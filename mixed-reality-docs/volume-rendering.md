---
title: 볼륨 렌더링
description: 대규모 이미지 불투명도 및 전체 화면으로 쉽게 표현할 수 없는 볼륨에 색을 사용 하 여 다양 한 정보를 포함 합니다. Windows Mixed Reality 내에서 대규모 이미지를 효율적으로 렌더링 하는 방법을 알아봅니다.
author: KevinKennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: 대규모 이미지, 볼륨 렌더링, 성능, 혼합된 현실
ms.openlocfilehash: dc0e75b916ab7cc96be1eccb4ad32ac71f5b75ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604097"
---
# <a name="volume-rendering"></a>볼륨 렌더링

의료 MRI 볼륨 엔지니어링 참조 하십시오 [wikipedia 볼륨 렌더링](https://en.wikipedia.org/wiki/Volume_rendering)합니다. 이러한 '대규모 이미지' 불투명도 및 전체 볼륨을 쉽게으로 표현할 수 없는 화면 같은 색을 사용 하 여 다양 한 정보를 포함 [다각형 메시](https://en.wikipedia.org/wiki/Polygon_mesh)합니다.

성능 향상을 위해 핵심 솔루션
1. BAD: 순 진하게: 전체 볼륨을 표시, 일반적으로 너무 늦게 실행
2. 좋은: Cutting 평면: 볼륨의 단일 조각만 표시
3. 좋은: Cutting 하위 볼륨: 볼륨의 몇 가지 레이어만 표시
4. 좋은: 볼륨 렌더링의 해상도 낮은 (' 혼합 해상도 장면 렌더링 ' 참조)

특정 프레임에서 화면으로 응용 프로그램에서 전송 될 수 있는 정보의 특정 메모리만 총 메모리 대역폭입니다. 또한 프레젠테이션에 대 한 데이터를 변환 하는 데 필요한 모든 처리 (또는 '음영') 시간도 필요 합니다. 볼륨 렌더링을 수행할 때 주요 고려 사항은 아래와 같이:
* 화면 너비 * 화면 높이 * 화면 수 * 볼륨 계층-에-는-픽셀 별 총-볼륨-샘플-프레임당 =
* 1028 * 720 * 2 * 256 = 378961920 (100%) (전체 res 볼륨: 너무 많은 샘플)
* 1028 * 720 * 2 * 1 = 1480320 (전체 %0.3) (씬 조각: 픽셀당 1 샘플 원활 하 게 실행 됨)
* 1028 * 720 * 2 * 10 = 14803200 (전체 3.9%) (하위 볼륨 조각: 픽셀 당 10 개 샘플 매우 원활 하 게 실행, 3d 표시)
* 200 * 200 * 2 * 256 = 20480000 (전체의 5%) (res 볼륨 낮춤: 적은 픽셀 전체 볼륨은 3d 하지만 약간 blury)

## <a name="representing-3d-textures"></a>3D 텍스처를 나타내는

Cpu:

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

Gpu:

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

한 볼륨에서 MRI, 같은 유용한 시각화를 위해 음영 처리 하는 방법입니다. 기본 방법은 '강도 창이' 하도록 (min 및 max), 강도 보고 단순히 흑백 강도 확인 하려면 해당 공간으로 확장 하려는 합니다. '색 진입' 해당 범위 내의 값에 적용 및 강도 스펙트럼의 다른 부분에는 서로 다른 색 음영 처리 된 수 있도록 질감으로 저장 될 수 있습니다.

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

대부분의 원시 강도 값과 '구분 인덱스'는 볼륨에 저장 하는 것이 응용 프로그램 (다른 파트를 같은 분할 스킨 및 뼈 이러한 세그먼트는 일반적으로 생성의 전용된 도구 전문가가). 다른 색 이나 각 세그먼트는 인덱스에 대 한 다른 색 진입 삽입할 위 방법을 함께 사용할 수 있습니다.

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>셰이더에서 조각화 하는 볼륨

훌륭한 첫 번째 단계에서 "조각화 평면"를 만들 때 볼륨에서 이동할 수는 ' 해당 '와 각 지점에서 값을 검색 하는 방법. 이 요소를 배치에 대 한 참조로 사용할 수 있는 세계 좌표 공간에서 볼륨이 있는 나타내는 'VolumeSpace' 큐브에 있다고 가정 합니다.

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

GPU를 사용 하 여 하위 볼륨 추적 (거닐거나 소수의 voxels 심층 다음 계층 데이터 뒤에서 앞으로)를 수행 하는 방법:

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

위의 하위 볼륨 코드 수정 가져옵니다.

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>혼합 된 확인 장면 렌더링

낮은 해상도 사용 하 여 장면의 일부를 렌더링 하 고 현재 위치에 배치 하는 방법:
1. 각 프레임을 업데이트 하는 각 눈을 수행 하려면 하나 두 화면 밖에 카메라 설정
2. 이 카메라를 렌더링 하는 저해상도 두 설치 렌더링 대상 (예: 200x200 각),
3. 사용자 앞에 이동 하는 쿼드를 설정 합니다.

각 프레임:
1. 저해상도에 눈 마다 렌더링 대상 그리기 (예: 볼륨 데이터, 비용이 많이 드는 셰이더)
2. 일반적으로 전체 해상도로 장면을 그리는 (메시, UI 등.)
3. 사용자가 앞에 쿼드 장면 위에 그리고는 저해상도 렌더링 프로젝션 합니다.
4. 결과: 저해상도 이지만 고밀도 볼륨 데이터를 사용 하 여 고해상도 요소의 시각적 조합입니다.
