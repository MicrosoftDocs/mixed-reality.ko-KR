---
title: 사례 연구-다양 한 성능으로 장치에서 고가는 크기 조정
description: 이 사례 연구는 다양 한 성능 기능을 갖춘 다양 한 장치에서 매력적인 환경을 제공 하기 위해 Microsoft 개발자가 어떻게 강화 카보베르데 앱을 최적화 하는 방법에 대 한 통찰력을 제공 합니다.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 모던 헤드셋, 성능 최적화, VR, 사례 연구
ms.openlocfilehash: 05f97188c81d85685540be998111ecfc47d9ef9c
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436508"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="4d78c-104">사례 연구-다양 한 성능으로 장치에서 고가는 크기 조정</span><span class="sxs-lookup"><span data-stu-id="4d78c-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="4d78c-105">가 중 카보베르데는 Microsoft에서 내부적으로 개발 된 Windows Mixed Reality 응용 프로그램으로,이를 통해 지형 데이터 위에 날씨 데이터를 표시 하는 데 중점을 두었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="4d78c-106">응용 프로그램은 사용자가 holographic 데이터 시각화를 사용 하 여 혼합 현실에서 데이터를 검색 하는 것을 얻을 수 있는 고유한 통찰력을 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="4d78c-107">뛰어난 카보베르데의 경우 Microsoft HoloLens에서 Windows Mixed Reality 몰입 형 헤드셋에 이르는 다양 한 하드웨어 기능을 갖춘 다양 한 플랫폼을 대상으로 하 고, 저전력 Pc에서 고성능 GPU를 사용 하는 최신 Pc로 다양 한 플랫폼을 대상으로 하고자 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="4d78c-108">주요 과제는 높은 프레임 속도로 실행 되는 동안 다른 그래픽 기능을 무분별 하는 장치에서 시각적으로 눈에 띄는 장면을 렌더링 하는 것 이었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="4d78c-109">이 사례 연구에서는 몇 가지 GPU 집약적 시스템을 만드는 데 사용 되는 프로세스와 기술을 단계별로 안내 하 여 발생 한 문제와 극복 했습니다 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="4d78c-110">투명도 및 과도 한 그리기</span><span class="sxs-lookup"><span data-stu-id="4d78c-110">Transparency and overdraw</span></span>

<span data-ttu-id="4d78c-111">투명도는 GPU에 비용이 많이 들 수 있으므로 주 렌더링 겪던 투명도를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="4d78c-112">깊이 버퍼에 쓰는 동안 단색 기 하 도형을 뒤로 렌더링 하 여 해당 픽셀 뒤에 있는 이후의 픽셀을 모두 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="4d78c-113">이렇게 하면 숨겨진 픽셀이 픽셀 셰이더를 실행 하는 것을 방지 하 여 프로세스 속도를 크게 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="4d78c-114">기 하 도형이 최적으로 정렬 된 경우 화면에서 각 픽셀은 한 번만 그려집니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="4d78c-115">투명 한 기 하 도형을 앞으로 다시 정렬 하 고 픽셀 셰이더의 출력을 화면에 있는 현재 픽셀에 혼합 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="4d78c-116">이로 인해 화면에 각 픽셀이 프레임 당 여러 번 그려집니다 (과다 그리기 라고 함).</span><span class="sxs-lookup"><span data-stu-id="4d78c-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="4d78c-117">HoloLens 및 메인스트림 Pc의 경우 화면을 몇 번만 채울 수 있으므로 투명 하 게 렌더링 하는 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="4d78c-118">이상 카보베르데 구성 요소 소개</span><span class="sxs-lookup"><span data-stu-id="4d78c-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="4d78c-119">장면에는 세 가지 주요 구성 요소가 있습니다. **UI, 지도**및 **날씨**입니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-119">We had three major components to our scene; **the UI, the map**, and **the weather**.</span></span> <span data-ttu-id="4d78c-120">날씨 효과에는 얻을 수 있는 모든 GPU 시간이 필요 하기 때문에, 과도 한 그리기를 줄이는 방식으로 UI 및 지형을 의도적으로 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="4d78c-121">UI를 여러 번 다시 작성 하 여 생성 되는 오버 그리기의 양을 최소화 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="4d78c-122">빛나는 단추 및 지도 개요와 같은 구성 요소를 위해 투명 한 아트를 서로 겹치지 않고 보다 복잡 한 기 하 도형의 측면에서 erred.</span><span class="sxs-lookup"><span data-stu-id="4d78c-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="4d78c-123">Map의 경우 그림자 및 복잡 한 조명과 같은 표준 Unity 기능을 제거 하 여 간단한 단일 sun 조명 모델과 사용자 지정 안개 계산으로 대체 하는 사용자 지정 셰이더를 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="4d78c-124">이로 인해 간단한 픽셀 셰이더가 생성 되 고 GPU 사이클이 해제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="4d78c-125">하드웨어에 따라 변경 내용이 필요 하지 않은 예산으로 렌더링 하기 위해 UI와 지도를 모두 얻기 위해 관리 했습니다. 그러나 특히 클라우드 렌더링에서 날씨 시각화는 더 많은 과제를 증명 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="4d78c-126">클라우드 데이터의 배경</span><span class="sxs-lookup"><span data-stu-id="4d78c-126">Background on cloud data</span></span>

<span data-ttu-id="4d78c-127">클라우드 데이터는 NOAA 서버 (https://nomads.ncep.noaa.gov/) 에서 다운로드 되었으며, 각각 클라우드의 위쪽 및 아래쪽 높이와 표의 각 셀에 대 한 클라우드의 밀도를 포함 하는 세 개의 고유한 2D 계층으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-127">Our cloud data was downloaded from NOAA servers (https://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="4d78c-128">데이터는 각 구성 요소가 질감의 빨강, 녹색 및 파랑 구성 요소에 저장 된 클라우드 정보 질감으로 처리 되어 GPU에 쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="4d78c-129">기 하 도형 클라우드</span><span class="sxs-lookup"><span data-stu-id="4d78c-129">Geometry clouds</span></span>

<span data-ttu-id="4d78c-130">더 적은 수의 컴퓨터에서 클라우드를 렌더링할 수 있도록 하려면 솔리드 geometry를 사용 하 여 과도 한 그리기를 최소화 하는 방법으로 시작 하기로 결정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="4d78c-131">먼저 꼭지점 마다 클라우드 정보 질감의 반지름을 사용 하 여 각 계층에 대해 solid heightmap 메시를 생성 하 고 셰이프를 생성 하 여 클라우드를 생성 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="4d78c-132">기 하 도형 셰이더를 사용 하 여 클라우드를 생성 하는 클라우드의 위쪽과 아래쪽에서 꼭 짓 점을 생성 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="4d78c-133">질감에서 밀도 값을 사용 하 여 더 많은 조밀한 클라우드의 경우 더 진한 색으로 클라우드를 색으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="4d78c-134">**꼭 짓 점 만들기에 대 한 셰이더:**</span><span class="sxs-lookup"><span data-stu-id="4d78c-134">**Shader for creating the vertices:**</span></span>

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

<span data-ttu-id="4d78c-135">실제 데이터에 대 한 자세한 정보를 얻기 위해 작은 소음 패턴이 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="4d78c-136">라운드 클라우드 가장자리를 생성 하기 위해 보간된 반지름 값이 0에 가까운 값을 삭제 하는 임계값에 도달할 때 픽셀 셰이더의 픽셀을 클리핑 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![기 하 도형 클라우드](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="4d78c-138">클라우드는 솔리드 기 하 도형 이므로 더 높은 속도의 지도 픽셀을 숨겨 프레임 속도를 높이는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="4d78c-139">이 솔루션은 견고한 기 하 도형 렌더링 방식 때문에 HoloLens 뿐만 아니라 최소 사양에서 하이엔드 그래픽 카드로 모든 그래픽 카드에서 효과적으로 실행 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="4d78c-140">단색 파티클 클라우드</span><span class="sxs-lookup"><span data-stu-id="4d78c-140">Solid particle clouds</span></span>

<span data-ttu-id="4d78c-141">이제 클라우드 데이터를 적절 하 게 표현 하는 백업 솔루션이 있지만,이는 "wow" 요소에 대 한 비트 lackluster, 고급 컴퓨터에 대 한 대규모 느낌이 전달 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="4d78c-142">다음 단계는 약 10만 파티클을 사용 하 여 클라우드를 만들어 더 유기적 및 대규모 모양을 생성 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="4d78c-143">파티클을 계속 해 서 오름차순으로 정렬 하는 경우 이전에 렌더링 된 입자 뒤의 픽셀에 대 한 깊이 버퍼 고르기을 활용 하 여 오버 그리기를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="4d78c-144">또한 파티클 기반 솔루션을 사용 하 여 다른 하드웨어를 대상으로 하는 데 사용 되는 파티클의 양을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="4d78c-145">그러나 모든 픽셀은 여전히 깊이 테스트를 거쳐야 하므로 약간의 추가 오버 헤드가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="4d78c-146">첫 번째는 시작 시 경험 중심 지점을 중심으로 파티클 위치를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="4d78c-147">입자를 중심 주위에 더 조밀 거리에 분산 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="4d78c-148">가장 가까운 입자가 가장 먼저 렌더링 되도록 모든 입자를 중심에서 뒤로 미리 정렬 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="4d78c-149">계산 셰이더는 각 파티클을 올바른 높이로 배치 하 고 밀도에 따라 색을 조정 하는 클라우드 정보 질감을 샘플링 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="4d78c-150">이 경우에는 모든 파티클에서 파티클 데이터를 유지할 수 있도록 각 파티클을 렌더링 하기 위해 *Drawprocedural* 을 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="4d78c-151">각 파티클에는 높이와 반지름이 모두 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="4d78c-152">높이는 클라우드 정보 질감에서 샘플링 된 클라우드 데이터를 기반으로 하며, 반지름은 가장 가까운 인접 항목에 가로 거리를 저장 하도록 계산 되는 초기 분포를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="4d78c-153">Quads는이 데이터를 사용 하 여 높이를 기준으로 하 여 사용자가 가로 방향으로 표시 하 고, 높이가 표시 되 고, 사용자가 하향식으로 볼 때 이웃 영역 사이에 영역이 적용 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![파티클 모양](images/particle-shape-700px.png)

<span data-ttu-id="4d78c-155">**분포를 보여 주는 셰이더 코드:**</span><span class="sxs-lookup"><span data-stu-id="4d78c-155">**Shader code showing the distribution:**</span></span>

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

<span data-ttu-id="4d78c-156">파티클을 front로 정렬 하 고 단색 스타일 셰이더를 사용 하 여 투명 픽셀을 클리핑 하기 때문에이 기술은 놀라운 양의 파티클을 처리 하 여 더 높은 수준의 시스템 에서도 과도 한 오버 그리기를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="4d78c-157">투명 파티클 클라우드</span><span class="sxs-lookup"><span data-stu-id="4d78c-157">Transparent particle clouds</span></span>

<span data-ttu-id="4d78c-158">솔리드 파티클은 클라우드의 셰이프에 좋은 유기적 느낌을 제공 하지만 클라우드의 fluffiness을 판매 하는 데 필요한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="4d78c-159">투명도를 도입할 수 있는 고급 그래픽 카드에 대 한 사용자 지정 솔루션을 사용해 보았습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="4d78c-160">이렇게 하려면 파티클의 초기 정렬 순서를 전환 하 고 질감 알파를 사용 하도록 셰이더를 변경 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Fluffy 클라우드](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="4d78c-162">수백 번의 화면에서 각 픽셀을 렌더링 하므로 가장 어려운 컴퓨터에도 너무 많은 것으로 판명 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="4d78c-163">해상도가 낮은 화면에서 렌더링</span><span class="sxs-lookup"><span data-stu-id="4d78c-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="4d78c-164">클라우드에서 렌더링 되는 픽셀 수를 줄이기 위해 화면에 비해 사분기 해상도 버퍼로 렌더링 하기 시작 하 고 모든 파티클이 그려진 후 최종 결과를 화면에 다시 스트레치 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="4d78c-165">약 4 배 속도를 제공 했지만 몇 가지 주의 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="4d78c-166">**화면 밖에 렌더링 하기 위한 코드:**</span><span class="sxs-lookup"><span data-stu-id="4d78c-166">**Code for rendering off-screen:**</span></span>

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

<span data-ttu-id="4d78c-167">첫째, 화면 외부 버퍼로 렌더링할 때 주 장면에서 모든 깊이 정보를 손실 하 여 산악 산 위에서의 파티클 렌더링을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="4d78c-168">두 번째로, 버퍼를 스트레치 하는 것은 해결 방법이 눈에 띄는 클라우드의 가장자리에도 아티팩트를 도입 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="4d78c-169">다음 두 섹션에서는 이러한 문제를 해결 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="4d78c-170">파티클 깊이 버퍼</span><span class="sxs-lookup"><span data-stu-id="4d78c-170">Particle depth buffer</span></span>

<span data-ttu-id="4d78c-171">산 또는 개체가 산의 입자를 다룰 수 있는 세계 기 하 도형에 입자를 공존할 수 있도록 하기 위해 화면 외부 버퍼를 주 장면의 기 하 도형을 포함 하는 깊이 버퍼로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="4d78c-172">이러한 깊이 있는 버퍼를 생성 하기 위해 두 번째 카메라를 만들었으므로 솔리드 기 하 도형 및 장면의 깊이가 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="4d78c-173">그런 다음 클라우드의 픽셀 셰이더에 새 텍스처를 사용 하 여 픽셀을 려 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="4d78c-174">동일한 질감을 사용 하 여 클라우드 픽셀 뒤의 기 하 도형에 대 한 거리를 계산 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="4d78c-175">이제이 거리를 사용 하 여 픽셀의 알파에 적용 하는 경우, 이제는 지역에 근접 하 고 파티클 및 지형을 만족 하는 하드 컷을 제거 하 여 클라우드의 효과를 줄일 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![지형으로 혼합 되는 클라우드](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="4d78c-177">가장자리를 선명 하 게</span><span class="sxs-lookup"><span data-stu-id="4d78c-177">Sharpening the edges</span></span>

<span data-ttu-id="4d78c-178">확장 된 클라우드는 파티클의 중앙에서 일반적인 크기의 클라우드와 거의 동일 하 게 보이지만, 겹쳐진 위치는 클라우드 가장자리에서 일부 아티팩트를 보여 주었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="4d78c-179">그렇지 않으면 선명한 가장자리가 흐리게 표시 되 고 카메라를 이동할 때 별칭 효과가 도입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="4d78c-180">이는 화면 밖의 버퍼에서 간단한 셰이더를 실행 하 여 대비에 큰 변화가 발생 한 위치 (1)를 확인 하 여이를 해결 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="4d78c-181">큰 변화를 가진 픽셀을 새 스텐실 버퍼 (2)에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="4d78c-182">그런 다음 스텐실 버퍼를 사용 하 여 화면에 오프 화면 버퍼를 다시 적용할 때 이러한 높은 대비 영역을 마스크 하 여 클라우드 (3)의 구멍이 발생 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="4d78c-183">그런 다음 전체 화면 모드에서 모든 파티클을 다시 렌더링 했지만 이번에는 스텐실 버퍼를 사용 하 여 가장자리를 제외한 모든 항목을 마스크 하 여 최소한의 픽셀 집합 (4)을 사용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="4d78c-184">파티클에 대해 명령 버퍼를 이미 만들었기 때문에 새 카메라로 다시 렌더링 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![클라우드 가장자리 렌더링 진행](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="4d78c-186">최종 결과는 클라우드의 저렴 한 센터 섹션과 선명한 가장자리가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="4d78c-187">이는 전체 화면에서 모든 입자를 렌더링 하는 것 보다 훨씬 빠르기는 하지만 스텐실 버퍼에 대 한 픽셀 테스트와 관련 된 비용이 여전히 남아 있으므로 엄청난 양의 과도 한 그리기는 여전히 비용으로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="4d78c-188">고르기 파티클</span><span class="sxs-lookup"><span data-stu-id="4d78c-188">Culling particles</span></span>

<span data-ttu-id="4d78c-189">바람 효과를 위해 계산 셰이더에 긴 삼각형 스트립을 생성 하 여 전 세계에서 많은 바람의 wisps을 생성 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="4d78c-190">Skinny 스트립으로 인해 윈드 효과가 가득 차서 채우기 비율이 크게 지는 않지만 수많은 꼭 짓 점 셰이더를 생성 하 여 꼭 짓 점 셰이더를 많이 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="4d78c-191">그릴 바람 스트립의 하위 집합을 제공 하기 위해 계산 셰이더에 추가 버퍼를 도입 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="4d78c-192">계산 셰이더의 몇 가지 간단한 뷰 고르기 논리를 사용 하 여 스트립이 카메라 보기 외부에 있는지 확인 하 고 푸시 버퍼에 추가 되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="4d78c-193">이렇게 하면 스트립의 양이 현저 하 게 감소 하 여 GPU에서 필요한 주기가 확보 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="4d78c-194">**추가 버퍼를 보여 주는 코드:**</span><span class="sxs-lookup"><span data-stu-id="4d78c-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="4d78c-195">*셰이더 계산:*</span><span class="sxs-lookup"><span data-stu-id="4d78c-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="4d78c-196">*C#code*</span><span class="sxs-lookup"><span data-stu-id="4d78c-196">*C# code:*</span></span>

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

<span data-ttu-id="4d78c-197">클라우드 파티클에서 동일한 기법을 사용 하려고 했습니다. 여기서는 계산 셰이더에 추려내 표시 되는 파티클만 푸시합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="4d78c-198">이 기법은 가장 큰 병목 현상이 화면에 렌더링 되는 픽셀 크기이 고 꼭 짓 점을 계산 하는 비용이 아니라 GPU에 거의 저장 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="4d78c-199">이 방법의 다른 문제는 파티클을 계산 하 여 병렬 처리 된 특성으로 인해 추가 버퍼가 임의의 순서로 채워지기 때문에 정렬 된 입자가 정렬 되지 않아 클라우드 파티클이 깜박거리는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="4d78c-200">푸시 버퍼를 정렬 하는 기술이 있지만 고르기 파티클에서 제공 되는 제한 된 양은 추가 정렬을 사용 하 여 상쇄 될 가능성이 높기 때문에 이러한 최적화를 활용 하지 않기로 결정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="4d78c-201">적응 렌더링</span><span class="sxs-lookup"><span data-stu-id="4d78c-201">Adaptive rendering</span></span>

<span data-ttu-id="4d78c-202">Cloudy vs와 같이 다양 한 렌더링 조건이 있는 앱에서 안정적인 프레임 속도를 보장 하기 위해 앱에 적응 렌더링을 도입 했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="4d78c-203">적응 렌더링의 첫 번째 단계는 GPU를 측정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="4d78c-204">이를 위해 사용자 지정 코드를 렌더링 된 프레임의 시작과 끝에 있는 GPU 명령 버퍼에 삽입 하 여 왼쪽 및 오른쪽 시각 화면 시간을 모두 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="4d78c-205">렌더링 하는 데 걸린 시간을 측정 하 여 원하는 새로 고침 비율과 비교 하면 얼마나 가까이 프레임을 삭제 하는 것이 합리적입니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="4d78c-206">프레임을 놓을 때 보다 빠르게 보이도록 렌더링을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="4d78c-207">한 가지 간단한 방법은 화면에서 뷰포트 크기를 변경 하는 것입니다. 렌더링 되는 데 필요한 픽셀 수를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="4d78c-208">*XR* 를 사용 하 여 시스템에서 대상 뷰포트를 축소 하 고 결과를 화면에 맞게 자동으로 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="4d78c-209">세계 기 하 도형에서는 규모의 작은 변화가 거의 눈에 띄지 않으며, 배율 인수 0.7에는 렌더링 해야 하는 픽셀의 절반이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70% 배율, 1/2 픽셀](images/datascape-scaling-700px.jpg)

<span data-ttu-id="4d78c-211">프레임을 삭제 하려고 하는 것을 감지 하면 크기를 고정 된 수 만큼 줄이고 빠르게 다시 실행 하는 경우 다시 증가 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="4d78c-212">시작할 때 하드웨어의 그래픽 기능을 기반으로 사용할 클라우드 기술을 결정 했지만, 시스템에서 오랜 시간 동안 해상도를 유지 하지 못하도록 GPU 측정의 데이터를 기반으로 할 수 있습니다. 그러나이는 시간이 없는 것입니다.  을 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="4d78c-213">최종 생각</span><span class="sxs-lookup"><span data-stu-id="4d78c-213">Final thoughts</span></span>

<span data-ttu-id="4d78c-214">다양 한 하드웨어를 대상으로 하는 것은 어려운 일 이며 몇 가지 계획이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="4d78c-215">낮은 수준의 컴퓨터를 대상으로 지정 하 여 문제 공간을 파악 하 고 모든 컴퓨터에서 실행 되는 백업 솔루션을 개발 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="4d78c-216">픽셀은 가장 귀중 한 리소스 이기 때문에 채우기 빈도를 염두에 두면 솔루션을 디자인 하세요.</span><span class="sxs-lookup"><span data-stu-id="4d78c-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="4d78c-217">투명도에 대 한 대상 솔리드 기 하 도형입니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="4d78c-218">그러면 백업 솔루션을 사용 하 여 높은 수준의 컴퓨터에 대해 더 복잡 하 게 계층화를 시작 하거나 백업 솔루션의 해상도를 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="4d78c-219">최악의 시나리오에 맞게 디자인 하 고 많은 상황에서 적응 렌더링을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4d78c-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="4d78c-220">작성자 정보</span><span class="sxs-lookup"><span data-stu-id="4d78c-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="4d78c-221"><b>Robert Ferrese</b></span><span class="sxs-lookup"><span data-stu-id="4d78c-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="4d78c-222">소프트웨어 엔지니어 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="4d78c-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="4d78c-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="4d78c-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="4d78c-224">소프트웨어 엔지니어 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="4d78c-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="4d78c-225">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d78c-225">See also</span></span>
* [<span data-ttu-id="4d78c-226">혼합 현실 성능 이해</span><span class="sxs-lookup"><span data-stu-id="4d78c-226">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="4d78c-227">Unity에 대 한 성능 권장 사항</span><span class="sxs-lookup"><span data-stu-id="4d78c-227">Performance Recommendations for Unity</span></span>](performance-recommendations-for-unity.md)

 
