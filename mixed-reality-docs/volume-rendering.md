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
# <a name="volume-rendering"></a><span data-ttu-id="20c39-105">볼륨 렌더링</span><span class="sxs-lookup"><span data-stu-id="20c39-105">Volume rendering</span></span>

<span data-ttu-id="20c39-106">의료 MRI 볼륨 엔지니어링 참조 하십시오 [wikipedia 볼륨 렌더링](https://en.wikipedia.org/wiki/Volume_rendering)합니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-106">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="20c39-107">이러한 '대규모 이미지' 불투명도 및 전체 볼륨을 쉽게으로 표현할 수 없는 화면 같은 색을 사용 하 여 다양 한 정보를 포함 [다각형 메시](https://en.wikipedia.org/wiki/Polygon_mesh)합니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-107">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="20c39-108">성능 향상을 위해 핵심 솔루션</span><span class="sxs-lookup"><span data-stu-id="20c39-108">Key solutions to improve performance</span></span>
1. <span data-ttu-id="20c39-109">BAD: 순 진하게: 전체 볼륨을 표시, 일반적으로 너무 늦게 실행</span><span class="sxs-lookup"><span data-stu-id="20c39-109">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="20c39-110">좋은: Cutting 평면: 볼륨의 단일 조각만 표시</span><span class="sxs-lookup"><span data-stu-id="20c39-110">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="20c39-111">좋은: Cutting 하위 볼륨: 볼륨의 몇 가지 레이어만 표시</span><span class="sxs-lookup"><span data-stu-id="20c39-111">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="20c39-112">좋은: 볼륨 렌더링의 해상도 낮은 (' 혼합 해상도 장면 렌더링 ' 참조)</span><span class="sxs-lookup"><span data-stu-id="20c39-112">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="20c39-113">특정 프레임에서 화면으로 응용 프로그램에서 전송 될 수 있는 정보의 특정 메모리만 총 메모리 대역폭입니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-113">There is only a certain amount of information that can be transferred from the application to the screen in any particular frame, this is the total memory bandwidth.</span></span> <span data-ttu-id="20c39-114">또한 프레젠테이션에 대 한 데이터를 변환 하는 데 필요한 모든 처리 (또는 '음영') 시간도 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-114">Also any processing (or 'shading') required to transform that data for presentation also requires time.</span></span> <span data-ttu-id="20c39-115">볼륨 렌더링을 수행할 때 주요 고려 사항은 아래와 같이:</span><span class="sxs-lookup"><span data-stu-id="20c39-115">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="20c39-116">화면 너비 \* 화면 높이 \* 화면 수 \* 볼륨 계층-에-는-픽셀 별 총-볼륨-샘플-프레임당 =</span><span class="sxs-lookup"><span data-stu-id="20c39-116">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="20c39-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (전체 res 볼륨: 너무 많은 샘플)</span><span class="sxs-lookup"><span data-stu-id="20c39-117">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="20c39-118">1028 \* 720 \* 2 \* 1 = 1480320 (전체 %0.3) (씬 조각: 픽셀당 1 샘플 원활 하 게 실행 됨)</span><span class="sxs-lookup"><span data-stu-id="20c39-118">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="20c39-119">1028 \* 720 \* 2 \* 10 = 14803200 (전체 3.9%) (하위 볼륨 조각: 픽셀 당 10 개 샘플 매우 원활 하 게 실행, 3d 표시)</span><span class="sxs-lookup"><span data-stu-id="20c39-119">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (sub-volume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="20c39-120">200 \* 200 \* 2 \* 256 = 20480000 (전체의 5%) (res 볼륨 낮춤: 적은 픽셀 전체 볼륨은 3d 하지만 약간 blury)</span><span class="sxs-lookup"><span data-stu-id="20c39-120">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blury)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="20c39-121">3D 텍스처를 나타내는</span><span class="sxs-lookup"><span data-stu-id="20c39-121">Representing 3D Textures</span></span>

<span data-ttu-id="20c39-122">Cpu:</span><span class="sxs-lookup"><span data-stu-id="20c39-122">On the CPU:</span></span>

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

<span data-ttu-id="20c39-123">Gpu:</span><span class="sxs-lookup"><span data-stu-id="20c39-123">On the GPU:</span></span>

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

## <a name="shading-and-gradients"></a><span data-ttu-id="20c39-124">음영 및 그라데이션</span><span class="sxs-lookup"><span data-stu-id="20c39-124">Shading and Gradients</span></span>

<span data-ttu-id="20c39-125">한 볼륨에서 MRI, 같은 유용한 시각화를 위해 음영 처리 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-125">How to shade an volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="20c39-126">기본 방법은 '강도 창이' 하도록 (min 및 max), 강도 보고 단순히 흑백 강도 확인 하려면 해당 공간으로 확장 하려는 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-126">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="20c39-127">'색 진입' 해당 범위 내의 값에 적용 및 강도 스펙트럼의 다른 부분에는 서로 다른 색 음영 처리 된 수 있도록 질감으로 저장 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-127">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="20c39-128">대부분의 원시 강도 값과 '구분 인덱스'는 볼륨에 저장 하는 것이 응용 프로그램 (다른 파트를 같은 분할 스킨 및 뼈 이러한 세그먼트는 일반적으로 생성의 전용된 도구 전문가가).</span><span class="sxs-lookup"><span data-stu-id="20c39-128">In many our applications we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone, these segments are generally created by experts in dedicated tools).</span></span> <span data-ttu-id="20c39-129">다른 색 이나 각 세그먼트는 인덱스에 대 한 다른 색 진입 삽입할 위 방법을 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-129">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="20c39-130">셰이더에서 조각화 하는 볼륨</span><span class="sxs-lookup"><span data-stu-id="20c39-130">Volume Slicing in a Shader</span></span>

<span data-ttu-id="20c39-131">훌륭한 첫 번째 단계에서 "조각화 평면"를 만들 때 볼륨에서 이동할 수는 ' 해당 '와 각 지점에서 값을 검색 하는 방법.</span><span class="sxs-lookup"><span data-stu-id="20c39-131">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="20c39-132">이 요소를 배치에 대 한 참조로 사용할 수 있는 세계 좌표 공간에서 볼륨이 있는 나타내는 'VolumeSpace' 큐브에 있다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-132">This assumes that there is a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="20c39-133">셰이더에서 볼륨 추적</span><span class="sxs-lookup"><span data-stu-id="20c39-133">Volume Tracing in Shaders</span></span>

<span data-ttu-id="20c39-134">GPU를 사용 하 여 하위 볼륨 추적 (거닐거나 소수의 voxels 심층 다음 계층 데이터 뒤에서 앞으로)를 수행 하는 방법:</span><span class="sxs-lookup"><span data-stu-id="20c39-134">How to use the GPU to do sub-volume tracing (walks a few voxels deep then layers on the data from back to front):</span></span>

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

## <a name="whole-volume-rendering"></a><span data-ttu-id="20c39-135">전체 볼륨 렌더링</span><span class="sxs-lookup"><span data-stu-id="20c39-135">Whole Volume Rendering</span></span>

<span data-ttu-id="20c39-136">위의 하위 볼륨 코드 수정 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-136">Modifying the sub-volume code above we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="20c39-137">혼합 된 확인 장면 렌더링</span><span class="sxs-lookup"><span data-stu-id="20c39-137">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="20c39-138">낮은 해상도 사용 하 여 장면의 일부를 렌더링 하 고 현재 위치에 배치 하는 방법:</span><span class="sxs-lookup"><span data-stu-id="20c39-138">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="20c39-139">각 프레임을 업데이트 하는 각 눈을 수행 하려면 하나 두 화면 밖에 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="20c39-139">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="20c39-140">이 카메라를 렌더링 하는 저해상도 두 설치 렌더링 대상 (예: 200x200 각),</span><span class="sxs-lookup"><span data-stu-id="20c39-140">Setup two low-resolution render targets (say 200x200 each), that the cameras render into</span></span>
3. <span data-ttu-id="20c39-141">사용자 앞에 이동 하는 쿼드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-141">Setup a quad that moves in front of the user</span></span>

<span data-ttu-id="20c39-142">각 프레임:</span><span class="sxs-lookup"><span data-stu-id="20c39-142">Each Frame:</span></span>
1. <span data-ttu-id="20c39-143">저해상도에 눈 마다 렌더링 대상 그리기 (예: 볼륨 데이터, 비용이 많이 드는 셰이더)</span><span class="sxs-lookup"><span data-stu-id="20c39-143">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, etc.)</span></span>
2. <span data-ttu-id="20c39-144">일반적으로 전체 해상도로 장면을 그리는 (메시, UI 등.)</span><span class="sxs-lookup"><span data-stu-id="20c39-144">Draw the scene normally as full resolution (meshes, UI, etc.)</span></span>
3. <span data-ttu-id="20c39-145">사용자가 앞에 쿼드 장면 위에 그리고는 저해상도 렌더링 프로젝션 합니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-145">Draw a quad in front of the user, over the scene, and project the low-res renders onto that.</span></span>
4. <span data-ttu-id="20c39-146">결과: 저해상도 이지만 고밀도 볼륨 데이터를 사용 하 여 고해상도 요소의 시각적 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="20c39-146">Result: visual combination of full-resolution elements with low-resolution but high-density volume data.</span></span>
