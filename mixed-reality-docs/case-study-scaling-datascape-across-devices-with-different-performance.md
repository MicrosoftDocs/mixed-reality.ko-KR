---
title: 사례 연구-성능이 각기 다른 장치의 Datascape 크기 조정
description: 이 사례 연구에서는 Microsoft 개발자 Datascape 응용 프로그램에서 다양 한 성능 기능을 사용 하 여 장치에서 뛰어난 환경을 제공을 최적화 하는 방법에 대 한 정보를 제공 합니다.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 몰입 형 헤드셋을 성능 최적화, VR, 사례 연구
ms.openlocfilehash: 990a5ee6de07b6416e3150a7885220409a9c8d93
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604872"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="a98a5-104">사례 연구-성능이 각기 다른 장치의 Datascape 크기 조정</span><span class="sxs-lookup"><span data-stu-id="a98a5-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="a98a5-105">Datascape는 Windows Mixed Reality 응용 프로그램 내부에서 개발한 microsoft 지형 데이터를 기반으로 날씨 데이터를 표시 하는 방법을 집중 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="a98a5-106">Holographic 데이터 시각화를 사용 하 여 사용자와 관련 하 여 혼합된 현실에서 검색 데이터에서 사용자에 대 한 고유 정보를 탐색 하는 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="a98a5-107">Datascape에 이르기까지 Windows Mixed Reality 몰입 형 헤드셋을 Microsoft HoloLens 최고급 GPU 사용 하 여 최신 Pc-Pc에서 다른 하드웨어 기능을 사용 하 여 다양 한 플랫폼을 대상 하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="a98a5-108">가장 큰 문제를 높은 framerate에서 실행 하는 동안 상당히 다른 그래픽 기능을 사용 하 여 장치에서 시각적으로 뛰어난 몇에서이 장면을 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="a98a5-109">이 사례 연구 일부 어떻게 문제와 그 해결 및 발생 했습니다. 문제를 설명 하는 자세한 GPU 사용량이 많은 시스템을 만드는 데 기술과 프로세스를 단계별로 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="a98a5-110">투명도 overdraw 및</span><span class="sxs-lookup"><span data-stu-id="a98a5-110">Transparency and overdraw</span></span>

<span data-ttu-id="a98a5-111">이 기본 렌더링 좌충우돌 투명도 GPU에 부담이 클 수 있으므로 투명도 사용 하 여 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="a98a5-112">단색 기 하 도형에 해당 픽셀에서 삭제 되 고 뒤에 있는 모든 향후 픽셀 중지 깊이 버퍼에 쓰는 동안를 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="a98a5-113">이 숨겨진된 픽셀 프로세스 속도 크게 높이기 픽셀 셰이더를 실행할 수 없도록 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="a98a5-114">기 하 도형 최적으로 정렬 하는 경우 화면의 각 픽셀 한 번만 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="a98a5-115">앞으로 다시 픽셀 셰이더에 화면에서 현재 픽셀의 출력을 혼합 의존 하는 투명 한 기 하 도형 정렬 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="a98a5-116">이 인해 그리고를 여러 번 라고 overdraw 프레임당 화면의 각 픽셀 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="a98a5-117">HoloLens와 일반 Pc에 대 한 화면만 채울 수 있습니다 몇 번의 렌더링 문제가 투명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="a98a5-118">Datascape 장면 구성 요소 소개</span><span class="sxs-lookup"><span data-stu-id="a98a5-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="a98a5-119">세 가지 주요 구성 요소는 장면; 했습니다. **UI 맵**, 및 **날씨**합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="a98a5-120">초기에 그건는 우리의 날씨 효과 필요 GPU 항상 것 전해주 하므로 UI 및 모든 overdraw을 줄일 수 있는 방식으로 지형 의도적으로 설계 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="a98a5-121">새롭게 바뀌었습니다 UI를 여러 번이 양을 overdraw을 최소화 하기 위해 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="a98a5-122">빛나는 단추와 맵 개요와 같은 구성 요소에 대 한 서로 위에 겹치기 투명 한 아트 보다는 더 복잡 한 기 하 도형 측면의 몇몇 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="a98a5-123">지도 대 한 사용자 지정 셰이더 복잡 한 조명 및 그림자와 같은 표준 Unity 기능을 제거 하는 간단한 단일 sun 조명 모델 및 사용자 지정 안개 계산이로 바꿔 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="a98a5-124">이 간단한 픽셀 셰이더를 생성 하 고 GPU 사이클을 확보 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="a98a5-125">우리는 UI와 렌더링 하는 맵 예산에서 위치에서는 필요 하지 않은; 하드웨어에 따라 이러한 변경 그러나 특히 클라우드 렌더링, 날씨 시각화 판명 되 었 더 어려워집니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="a98a5-126">클라우드 데이터에 대 한 배경</span><span class="sxs-lookup"><span data-stu-id="a98a5-126">Background on cloud data</span></span>

<span data-ttu-id="a98a5-127">클라우드 데이터 NOAA 서버에서 다운로드 된 (http://nomads.ncep.noaa.gov/) 되었으며를 별도 세 가지 2D 계층에서 클라우드로의 위쪽과 아래쪽 높이 뿐만 아니라 클라우드 그리드의 각 셀에 대 한 밀도 사용 하 여 각 상태로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-127">Our cloud data was downloaded from NOAA servers (http://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="a98a5-128">데이터를 쉽게 액세스할 수는 GPU에서 질감의 빨강, 녹색 및 파랑 구성 요소에 각 구성 요소 저장 된 클라우드 정보 질감 처리 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="a98a5-129">기 하 도형 클라우드</span><span class="sxs-lookup"><span data-stu-id="a98a5-129">Geometry clouds</span></span>

<span data-ttu-id="a98a5-130">-컴퓨터를 시작 하기로 하는 클라우드 렌더링 되도록 하는 견고한 기 하 도형 최소화 하는 데 사용할 방법을 overdraw 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="a98a5-131">꼭 짓 점 당 클라우드 정보 질감의 radius를 사용 하 여 도형을 생성 하는 각 계층에 대 한 단색 heightmap 메시를 생성 하 여 클라우드 생성을 먼저 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="a98a5-132">견고한 클라우드 셰이프를 생성 하는 클라우드 아래쪽과 위쪽에서 꼭 짓 점을 생성 하는 기 하 도형 셰이더를 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="a98a5-133">자세한 조밀한 클라우드에 대 한 색이 어두울수록를 사용 하 여 클라우드를 색 질감에서 밀도 값을 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="a98a5-134">**꼭 짓 점을 만드는 셰이더:**</span><span class="sxs-lookup"><span data-stu-id="a98a5-134">**Shader for creating the vertices:**</span></span>

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

<span data-ttu-id="a98a5-135">실제 데이터를 바탕으로 자세한 내용을 보려면 작은 노이즈 패턴을 도입 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="a98a5-136">Round 클라우드 가장자리를 생성 하려면에서는 잘린 픽셀 픽셀 셰이더의 보간된 반경 값을 0에 가까운 값을 삭제 하는 임계값에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![기 하 도형 클라우드](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="a98a5-138">클라우드 단색 기 하 도형 되므로 프레임 속도 개선 하기 위해 아래에 있는 모든 비용이 많이 드는 지도 픽셀을 숨기려면 지형 전에 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="a98a5-139">이 솔루션 단색 기 하 도형 렌더링 방식을 인해 잘 최고급 그래픽 카드에 최소 사양에서 모든 그래픽 카드 및 HoloLens에서 실행 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="a98a5-140">Solid 파티클 클라우드</span><span class="sxs-lookup"><span data-stu-id="a98a5-140">Solid particle clouds</span></span>

<span data-ttu-id="a98a5-141">이제을 클라우드 데이터의 훌륭한 표현 생성 하지만 "wow" 팩터의 약간 낮은 고성능 컴퓨터에 대 한 원했습니다는 대규모 느낌을 전달 하지 않은 백업 솔루션을 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="a98a5-142">다음 단계는 약 100,000 입자에 보다 유기적이 고 대규모 느낌을 생성 하기 위해 사용 하 여이 나타내는 여 클라우드를 만들기 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="a98a5-143">파티클 단색으로 유지 하 고 앞에서 뒤로 정렬 하는 경우 것을 활용할 수 있습니다에서 이전에 렌더링된 파티클 뒤 픽셀의 깊이 버퍼 선별는 overdraw 감소 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="a98a5-144">또한 파티클 기반 솔루션을 사용 했습니다 파티클 대상 다른 하드웨어로 사용 되는 양을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="a98a5-145">그러나 모든 픽셀은 여전히 일부 추가 오버 헤드가 발생 하는 깊이 테스트 되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="a98a5-146">시작 시 입자 환경의 중심점의 위치를 먼저 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="a98a5-147">중심 더 조밀 하 게 입자를 분산 하는 것 등 작은 거리에서입니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="a98a5-148">가장 가까운 파티클은 먼저 렌더링 되도록 뒤로 센터에서 모든 파티클 미리 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="a98a5-149">계산 셰이더 밀도 따라 색을 올바른 높이에서 각 입자 위치로 클라우드 정보 질감을 샘플 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="a98a5-150">사용 했습니다 *DrawProcedural* 전혀 GPU에 있으려면 파티클 데이터 파티클 당 쿼드 렌더링 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="a98a5-151">각 입자 높이 반지름 둘 다 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="a98a5-152">높이 된 클라우드 정보 질감에서 샘플링 된 클라우드 데이터를 기반으로 하며 반지름 초기 배포를 가장 가까운 인접 가로 거리를 저장할 계산 될 것을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="a98a5-153">quads이이 데이터를 사용 하는 경우 사용자가 볼 가로로 있도록 높이 따라 각 진 자체를 높이 표시 및 인접 사이의 영역을 다룰 수는 사용자는이 하향식으로 살펴보고, 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="a98a5-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![파티클 셰이프](images/particle-shape-700px.png)

<span data-ttu-id="a98a5-155">**분포를 보여 주는 셰이더 코드:**</span><span class="sxs-lookup"><span data-stu-id="a98a5-155">**Shader code showing the distribution:**</span></span>

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

<span data-ttu-id="a98a5-156">입자 앞에서 뒤로 정렬 이므로 클립 (blend) 투명 한 픽셀에 스타일 단색 셰이더를 여전히 사용이 기술을 상당히 낮은 기반 컴퓨터에도 비용이 많이 드는 과도 한 그리기 방지 파티클의 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="a98a5-157">투명 한 파티클 클라우드</span><span class="sxs-lookup"><span data-stu-id="a98a5-157">Transparent particle clouds</span></span>

<span data-ttu-id="a98a5-158">Solid 파티클 클라우드의 셰이프에 좋은 유기적 느낌을 제공 하지만 여전히 클라우드의 fluffiness 판매를 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="a98a5-159">투명도 수 도입할 최고급 그래픽 카드에 대 한 사용자 지정 솔루션을 시도 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="a98a5-160">이렇게 하려면 단순히 파티클의 초기 정렬 순서를 전환 하 고 질감 알파를 사용 하도록 셰이더를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Fluffy 클라우드](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="a98a5-162">이 확인할 유용한 하지만 판명 되도 가장 까다로운 컴퓨터용 너무 무 거 워 횟수 수백 화면의 각 픽셀을 렌더링 초래 하므로!</span><span class="sxs-lookup"><span data-stu-id="a98a5-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="a98a5-163">더 낮은 해상도 사용 하 여 오프 스크린 렌더링</span><span class="sxs-lookup"><span data-stu-id="a98a5-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="a98a5-164">클라우드에서 렌더링 된 픽셀 수를 줄이려면 렌더링 하는 분기 확인 버퍼 (화면)에서 시작 및 모든 파티클 했습니다 그려진 후 화면 백업 최종 결과 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="a98a5-165">이 있었습니다 약 4 x 속도 향상 폭 하지만 몇 가지 주의 사항이 함께 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="a98a5-166">**오프 스크린 렌더링에 대 한 코드:**</span><span class="sxs-lookup"><span data-stu-id="a98a5-166">**Code for rendering off-screen:**</span></span>

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

<span data-ttu-id="a98a5-167">먼저를 화면 밖에 있는 버퍼를 렌더링 하는 경우 문제가 생기면 모든 깊이 정보는 주 장면에서 산 위에 렌더링 파티클 산 뒤에서 결과.</span><span class="sxs-lookup"><span data-stu-id="a98a5-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="a98a5-168">둘째, 변경 된 해상도 눈에 띄는 클라우드의 가장자리에서 아티팩트를 도입도 버퍼를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="a98a5-169">다음 두 섹션에서는 이러한 문제점을 해결 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="a98a5-170">파티클 깊이 버퍼</span><span class="sxs-lookup"><span data-stu-id="a98a5-170">Particle depth buffer</span></span>

<span data-ttu-id="a98a5-171">월드 기 하 도형의 함께 파티클 mountain 또는 개체를 뒤 파티클 배울를 하도록 주 장면 기 하 도형을 포함 하는 깊이 버퍼를 사용 하 여 화면 밖에 있는 버퍼를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="a98a5-172">이러한 깊이 버퍼를 생성 하려면 만든 두 번째 카메라, 단색 기 하 도형 및 깊이 장면의 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="a98a5-173">클라우드의 픽셀 셰이더에 새 질감 채워집니다 (픽셀)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="a98a5-174">클라우드 픽셀 뒤 기 하 도형 거리를 계산 하 여 같은 텍스처를 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="a98a5-175">이제는 거리를 사용 하 여 픽셀의 알파에 적용 하는 여 파티클과 지형이 보이는 만나는 클라우드 지형에 접근할 때 페이드아웃, 모든 하드 컷 제거의 영향을 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![지형에 혼합 클라우드](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="a98a5-177">가장자리 선명 하 게 표시</span><span class="sxs-lookup"><span data-stu-id="a98a5-177">Sharpening the edges</span></span>

<span data-ttu-id="a98a5-178">확장 접속 클라우드 찾을 파티클의 가운데에 보통 크기 클라우드에 거의 동일 또는 overlapped, 여기서 하지만 살펴보았습니다 일부 아티팩트 클라우드 가장자리입니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="a98a5-179">날카로운 가장자리 흐리게 표시 되 고 별칭 효과 카메라를 이동할 때 도입 된 그렇지 않은 경우.</span><span class="sxs-lookup"><span data-stu-id="a98a5-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="a98a5-180">반면 큰 변화 (1)의 발생 위치를 확인 하는 화면 밖에 있는 버퍼에서 간단한 셰이더를 실행 하 여이 문제를 해결 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="a98a5-181">큰 변화를 사용 하 여 픽셀을 (2) 새 스텐실 버퍼에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="a98a5-182">그런 다음 사용 마스크 스텐실 버퍼 이러한 고대비 영역 화면 밖에 있는 버퍼를 화면에 다시 적용할 때 구멍에 (3) 클라우드 중심의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="a98a5-183">에서는 다음 모든 파티클 다시 렌더링 전체 화면 모드에서이 이번을 마스킹 하려는 모든 스텐실 버퍼를 사용 하지만 픽셀의 최소 집합의 결과 지 수 (4)입니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="a98a5-184">파티클에 대 한 명령 버퍼를 이미 만든, 이후에 단순히 새 카메라를 다시 렌더링 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![클라우드 가장자리 렌더링의 진행](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="a98a5-186">최종 결과 클라우드의 저렴 한 가운데 섹션 선명한 가장자리 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="a98a5-187">이 렌더링 보다 훨씬 빠르게 수행 되는 동안 전체 화면에 있는 모든 파티클, 막대 한 양의 overdraw 여전히 있으므로 스텐실 버퍼에 대 한 픽셀을 테스트와 관련 된 비용이 비용을 함께 제공 되는 여전히 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="a98a5-188">파티클 고르기</span><span class="sxs-lookup"><span data-stu-id="a98a5-188">Culling particles</span></span>

<span data-ttu-id="a98a5-189">우리의 wind 효과 대 한 계산 셰이더를 전 세계의 많은 wisp 바람 만들기에서 삼각형 줄무늬 장기 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="a98a5-190">Wind 효과 생성 하는 스키 니 줄무늬 인해 채우기 비율에 과도 한 동안에 많은 수백 수천 개의 꼭 짓 점 셰이더에 대 한 부하가 발생 하는 꼭 짓 점 생성.</span><span class="sxs-lookup"><span data-stu-id="a98a5-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="a98a5-191">했습니다 그릴 wind 줄무늬의 하위 집합을 피드로 계산 셰이더 버퍼를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="a98a5-192">간단한 뷰 꼭지점이 절 두 체 선별의 일부 논리 계산 셰이더를 사용 하 여 카메라 뷰 외부 스트립 했는지 확인 하 고 푸시 버퍼에 추가 되지 않도록 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="a98a5-193">이 양이 줄어들지만 줄무늬 크게 GPU에서 필요한 일부 사이클을 확보 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="a98a5-194">**추가 버퍼를 보여 주는 코드:**</span><span class="sxs-lookup"><span data-stu-id="a98a5-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="a98a5-195">*계산 셰이더:*</span><span class="sxs-lookup"><span data-stu-id="a98a5-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="a98a5-196">*C#코드:*</span><span class="sxs-lookup"><span data-stu-id="a98a5-196">*C# code:*</span></span>

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

<span data-ttu-id="a98a5-197">클라우드 파티클, 여기서는 계산 셰이더에서 추려내 하 하 고 렌더링할 표시 파티클만 푸시에 동일한 기법을 사용 하는 것이 보았습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="a98a5-198">이 기술을 실제로 저장 하지 않은 우리 GPU에 가장 큰 병목 꼭 짓 점 계산 비용 하지 화면에 렌더링 크기 픽셀 되었으므로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="a98a5-199">이 기술 사용 하 여 다른 문제가 발생 하지 않은 rted 깜박임 현상이 클라우드 파티클의 발생 되도록 정렬된 파티클 파티클, 컴퓨팅의 병렬화 된 해당 특성으로 인해 임의 순서로 추가 버퍼 채워져 있는지 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="a98a5-200">푸시 버퍼를 정렬 하는 기술을 있지만 없습니다이 최적화를 추진 하기로 결정 되므로 파티클 고르기 부족 했습니다 성능 향상의 제한 된 크기는 추가 정렬을 사용 하 여 오프셋 가능성이 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="a98a5-201">적응형 렌더링</span><span class="sxs-lookup"><span data-stu-id="a98a5-201">Adaptive rendering</span></span>

<span data-ttu-id="a98a5-202">을 보장 하기 위해 앱에 대해 안정적인 framerate cloudy vs 등의 조건은 일반 뷰를 렌더링 하는 다양 한 앱에 적응 렌더링을 도입 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="a98a5-203">적응형 렌더링의 첫 번째 단계 GPU를 측정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="a98a5-204">시작 및 렌더링 된 프레임의 끝에 GPU 명령 버퍼를 사용자 지정 코드를 삽입 하 여이 수행한 것, 왼쪽 및 오른쪽 화면 시간 시각 모두 캡처.</span><span class="sxs-lookup"><span data-stu-id="a98a5-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="a98a5-205">측정 하 여 소요 된 시간 렌더링과 얼마나 근접 한다고 프레임이 삭제의 의미 했습니다는 원하는 새로 고침 빈도를 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="a98a5-206">프레임이 삭제 가까운 더 빨라질 수는 렌더링을 조정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="a98a5-207">조정의 한 가지 간단한 방법은 덜 픽셀 렌더링 필요한 화면의 뷰포트 크기를 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="a98a5-208">사용 하 여 *UnityEngine.XR.XRSettings.renderViewportScale* 시스템 대상된 뷰포트를 축소 하 고 자동으로 조정 화면 백업 결과 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="a98a5-209">눈금에서 작은 변경 world 기 하 도형에 잘 보이지 않음 이며 0.7의 배율을 렌더링 되어야 하는 픽셀 양의 절반이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70% 배율을 절반 픽셀](images/datascape-scaling-700px.jpg)

<span data-ttu-id="a98a5-211">고정된 된 수 별 크기 조정에서는 줄이고 증가 프레임이 삭제 하려고 한다고 검색 되는 경우 충분히 빠르게 다시 실행 하는 경우 백업 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="a98a5-212">어떤 클라우드 기술을 사용 하 여 기능을 기반으로 그래픽 하드웨어 시작 하기로, 시스템, 오랜 시간 동안 낮은 해상도로 유지 하지 않도록 하려면이 GPU 측정 값 으로부터 데이터를 기반으로 하는 것이 가능 하지만이 우리가 없는 시간  Datascape에서 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="a98a5-213">최종 고려 사항</span><span class="sxs-lookup"><span data-stu-id="a98a5-213">Final thoughts</span></span>

<span data-ttu-id="a98a5-214">다양 한 하드웨어를 대상으로 하는 것은 어렵습니다 및 약간의 계획이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="a98a5-215">모든 컴퓨터에서 실행 되는 백업 솔루션을 개발 하 고 문제 영역에 알아보기-컴퓨터를 대상으로 시작 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="a98a5-216">픽셀 가장 귀중 한 리소스 되므로 염두에 채우기 비율을 사용 하 여 솔루션을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="a98a5-217">투명성을 통해 대상 단색 기 하 도형입니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="a98a5-218">백업 솔루션을 사용 하 여 고성능 컴퓨터에 대 한 자세한 복잡성에 레이어를 먼저 수도 있고 백업 솔루션의 해상도 향상만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="a98a5-219">최악의 시나리오를 디자인 하 고 아마도 많은 경우 적응 렌더링을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a98a5-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="a98a5-220">저자 소개</span><span class="sxs-lookup"><span data-stu-id="a98a5-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="a98a5-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="a98a5-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="a98a5-222">소프트웨어 엔지니어 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="a98a5-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="a98a5-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="a98a5-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="a98a5-224">소프트웨어 엔지니어 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="a98a5-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="a98a5-225">참조</span><span class="sxs-lookup"><span data-stu-id="a98a5-225">See also</span></span>
* [<span data-ttu-id="a98a5-226">혼합된 현실에 대 한 성능 이해</span><span class="sxs-lookup"><span data-stu-id="a98a5-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="a98a5-227">Unity에 대 한 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="a98a5-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 
