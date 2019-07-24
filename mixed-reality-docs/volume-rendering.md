---
title: 볼륨 렌더링
description: 대규모 이미지는 화면으로 쉽게 표현할 수 없는 볼륨 전체에서 불투명도 및 색이 포함 된 다양 한 정보를 포함 합니다. Windows Mixed Reality 내에서 대규모 이미지를 효율적으로 렌더링 하는 방법에 대해 알아봅니다.
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: 대규모 이미지, 볼륨 렌더링, 성능, 혼합 현실
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548636"
---
# <a name="volume-rendering"></a>볼륨 렌더링

의료 MRI 또는 엔지니어링 볼륨의 경우 [위키백과에서 볼륨 렌더링](https://en.wikipedia.org/wiki/Volume_rendering)을 참조 하세요. 이러한 ' 대규모 images '에는 [다각형 메시](https://en.wikipedia.org/wiki/Polygon_mesh)와 같이 표면으로 쉽게 표현 될 수 없는 볼륨 전체에서 불투명도 및 색을 사용 하는 다양 한 정보가 포함 되어 있습니다.

성능 향상을 위한 주요 솔루션
1. 올바르지 Naive 접근 방식: 일반적으로 너무 느리게 실행 되는 전체 볼륨 표시
2. 좋음 절삭 평면: 볼륨의 단일 조각만 표시
3. 좋음 하위 볼륨을 자르는 중: 볼륨의 일부 레이어만 표시
4. 좋음 볼륨 렌더링 해상도 낮추기 (' 혼합 해상도 장면 렌더링 ' 참조)

응용 프로그램에서 특정 프레임의 화면으로 전송 될 수 있는 정보에는 총 메모리 대역폭이 있습니다. 또한 프레젠테이션에 대 한 데이터를 변환 하는 데 필요한 모든 처리 (또는 ' 음영 ')도 시간이 필요 합니다. 볼륨 렌더링을 수행할 때 기본적인 고려 사항은 다음과 같습니다.
* 화면 너비 * 화면 높이 * 화면 수 * 볼륨-계층-픽셀 = 전체-볼륨-프레임 당 샘플 수
* 1028 * 720 * 2 * 256 = 378961920 (100%) (전체 res 볼륨: 샘플이 너무 많음)
* 1028 * 720 * 2 * 1 = 1480320 (전체의 0.3%) (씬 조각: 픽셀당 1 개 샘플, 부드럽게 실행 됨)
* 1028 * 720 * 2 * 10 = 14803200 (전체의 3.9%) (하위 볼륨 조각: 픽셀당 10 개 샘플, 매우 원활 하 게 실행, 3d 표시
* 200 * 200 * 2 * 256 = 2048만 (전체의 5%) (더 낮은 res 볼륨: 더 적은 픽셀, 전체 볼륨, 3d로 보이지만 비트 blury)

## <a name="representing-3d-textures"></a>3D 질감 표시

CPU:

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

GPU:

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>음영 및 그라데이션

유용한 시각화를 위해 MRI와 같은 볼륨을 음영 처리 하는 방법입니다. 기본 방법은 강도를 보려는 ' 강도 창 ' (최소 및 최대)을 보유 하는 것이 고, 해당 공간으로 크기를 조정 하 여 검정색과 백색 강도를 확인 하는 것입니다. 그러면 ' 색 램프 '가 해당 범위 내에 있는 값에 적용 되 고 질감으로 저장 될 수 있으므로 강도 스펙트럼의 각 부분이 서로 다른 색으로 음영 처리 될 수 있습니다.

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

많은 응용 프로그램에서 원시 강도 값과 ' 조각화 인덱스 '를 모두 볼륨에 저장 합니다 (스킨 및 뼈와 같은 여러 부분을 분할 하기 위해 이러한 세그먼트는 일반적으로 전용 도구의 전문가에 의해 만들어짐). 위의 방법으로 결합 하 여 다른 색 이나 각 세그먼트 인덱스 마다 다른 색 램프를 적용할 수 있습니다.

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>셰이더의 볼륨 조각화

첫 번째 단계는 볼륨을 이동 하 고, ' 조각화 ' 하 고, 각 지점에서 값을 검색 하는 방법을 "조각화 평면"을 만드는 것입니다. 여기서는 볼륨이 세계 공간에 있는 위치를 나타내는 ' VolumeSpace ' 큐브가 있다고 가정 합니다 .이는 요소를 배치 하기 위한 참조로 사용할 수 있습니다.

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>셰이더에서 볼륨 추적

GPU를 사용 하 여 하위 볼륨 추적을 수행 하는 방법 (voxels를 통해 데이터에 대 한 몇 가지 계층 구조를 차례로 이동):

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>전체 볼륨 렌더링

위의 하위 볼륨 코드를 수정 하면 다음을 얻게 됩니다.

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>혼합 해상도 장면 렌더링

낮은 해상도로 장면의 일부를 렌더링 하 고 다시 배치 하는 방법입니다.
1. 각 프레임을 업데이트 하는 각 눈에 따라 하나씩, 두 개의 오프 스크린 카메라를 설정 합니다.
2. 카메라에서 렌더링 하는 두 가지 저해상도 렌더링 대상 (각각 200 x 200)을 설정 합니다.
3. 사용자 앞으로 이동 하는 쿼드 설정

각 프레임:
1. 저해상도 (볼륨 데이터, 비용이 많이 드는 셰이더 등)에서 각 눈에 대 한 렌더링 대상을 그립니다.
2. 정상적으로 장면을 전체 해상도 (메시, UI 등)로 그리기
3. 장면에 대해 사용자 앞에 쿼드를 그리고이에 해당 하는 하위 res 렌더링을 프로젝션 합니다.
4. 결과: 저해상도 이지만 고밀도 볼륨 데이터로 전체 해상도 요소를 시각적으로 조합 합니다.
