---
title: 사례 연구-혼합 현실에서 galaxy 만들기
description: Microsoft HoloLens를 제공 하기 전에 개발자 커뮤니티에서 새로운 장치에 대해 숙련 된 내부 팀 빌드를 확인 하려는 앱의 종류를 확인 했습니다. 5000 개 이상의 아이디어가 공유 되었으며 24 시간 Twitter 폴링 후에는 "Galaxy 탐색기" 라는 아이디어가 적용 되었습니다.
author: KarimLUCCIN
ms.author: kaluccin
ms.date: 03/21/2018
ms.topic: article
keywords: Galaxy 탐색기, HoloLens, Windows Mixed Reality, 아이디어 공유, 사례 연구
ms.openlocfilehash: a478eaa35144a8ee0fbeaeb43cec4b9f901890ab
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63523849"
---
# <a name="case-study---creating-a-galaxy-in-mixed-reality"></a><span data-ttu-id="230f4-105">사례 연구-혼합 현실에서 galaxy 만들기</span><span class="sxs-lookup"><span data-stu-id="230f4-105">Case study - Creating a galaxy in mixed reality</span></span>

<span data-ttu-id="230f4-106">Microsoft HoloLens를 제공 하기 전에 개발자 커뮤니티에서 새로운 장치에 대해 숙련 된 내부 팀 빌드를 확인 하려는 앱의 종류를 확인 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-106">Before Microsoft HoloLens shipped, we asked our developer community what kind of app they'd like to see an experienced internal team build for the new device.</span></span> <span data-ttu-id="230f4-107">5000 개 이상의 아이디어가 공유 되었고 24 시간 Twitter 폴링 후에는 [Galaxy 탐색기](galaxy-explorer.md)라는 아이디어가 적용 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-107">More than 5000 ideas were shared, and after a 24-hour Twitter poll, the winner was an idea called [Galaxy Explorer](galaxy-explorer.md).</span></span>

<span data-ttu-id="230f4-108">Andy Zibits, 프로젝트의 아트 리드 및 Karim Luccin (팀의 그래픽 엔지니어)는 Galaxy 탐색기의 Milky 방법 galaxy를 정확 하 고 대화형으로 표현 하는 art와 엔지니어링 간의 공동 노력에 대해 이야기 합니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-108">Andy Zibits, the art lead on the project, and Karim Luccin, the team's graphics engineer, talk about the collaborative effort between art and engineering that led to the creation of an accurate, interactive representation of the Milky Way galaxy in Galaxy Explorer.</span></span>

## <a name="the-tech"></a><span data-ttu-id="230f4-109">기술</span><span class="sxs-lookup"><span data-stu-id="230f4-109">The Tech</span></span>

<span data-ttu-id="230f4-110">[Microsoft의 팀](galaxy-explorer.md#meet-the-team) 은 3 명의 개발자, 4 개 음악가, 생산자 및 한 명의 테스터로 구성 되었으며, 모든 기능을 갖춘 앱을 빌드하는 데 6 주가 vastness,이는 사용자가 Milky 방식으로 Galaxy를 학습 하 고이를 탐색 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-110">[Our team](galaxy-explorer.md#meet-the-team) - made up of two designers, three developers, four artists, a producer, and one tester — had six weeks to build a fully functional app which would allow people to learn about and explore the vastness and beauty of our Milky Way Galaxy.</span></span>

<span data-ttu-id="230f4-111">Microsoft는 생생한 공간에서 3D 개체를 직접 렌더링 하는 데 HoloLens 기능을 최대한 활용 하고자 했습니다. 따라서 사람들이 가까운 곳에서 확대 하 고 개별의 개별 궤적을 볼 수 있는 현실적인 느낌의 galaxy를 만들려고 했습니다. .</span><span class="sxs-lookup"><span data-stu-id="230f4-111">We wanted to take full advantage of the ability of HoloLens to render 3D objects directly in your living space, so we decided we wanted to create a realistic looking galaxy where people would be able to zoom in close and see individual stars, each on their own trajectories.</span></span>

<span data-ttu-id="230f4-112">개발의 첫 번째 주에는 Milky 방식의 Galaxy를 표현 하기 위한 몇 가지 목표가 제공 됩니다. 여기에는 galaxy의 모양을 만드는 데 도움이 되는 깊이, 이동 및 느낌 대규모이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-112">In the first week of development, we came up with a few goals for our representation of the Milky Way Galaxy: It needed to have depth, movement, and feel volumetric—full of stars that would help create the shape of the galaxy.</span></span>

<span data-ttu-id="230f4-113">수십억 개의 별이 있는 애니메이션 된 galaxy를 만드는 경우의 문제는 업데이트 해야 하는 단일 요소 수가 HoloLens에서 CPU를 사용 하 여 애니메이션 효과를 줄 수 있을 정도로 크지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-113">The problem with creating an animated galaxy that had billions of stars was that the sheer number of single elements that need updating would be too big per frame for HoloLens to animate using the CPU.</span></span> <span data-ttu-id="230f4-114">이 솔루션에는 다양 한 아트와 과학이 함께 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-114">Our solution involved a complex mix of art and science.</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="230f4-115">백그라운드 작업</span><span class="sxs-lookup"><span data-stu-id="230f4-115">Behind the scenes</span></span>

<span data-ttu-id="230f4-116">사용자가 개별 별을 탐색할 수 있도록 하기 위해 첫 번째 단계는 한 번에 렌더링할 수 있는 파티클 수를 파악 하는 것 이었습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-116">To allow people to explore individual stars, our first step was to figure out how many particles we could render at once.</span></span>

### <a name="rendering-particles"></a><span data-ttu-id="230f4-117">렌더링 파티클</span><span class="sxs-lookup"><span data-stu-id="230f4-117">Rendering particles</span></span>

<span data-ttu-id="230f4-118">현재 Cpu는 일련의 작업을 수행 하는 데 매우 유용 하지만 많은 코어를 동시에 처리 하는 데는 많은 코어를 사용할 수 있지만, Gpu는 수천 개의 작업을 병렬로 처리 하는 데 훨씬 더 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-118">Current CPUs are great for processing serial tasks and up to a few parallel tasks at once (depending on how many cores they have), but GPUs are much more effective at processing thousands of operations in parallel.</span></span> <span data-ttu-id="230f4-119">그러나 일반적으로 CPU와 동일한 메모리를 공유 하지 않으므로 CPU < > GPU 간에 데이터를 교환 하는 것이 신속 하 게 병목 상태가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-119">However, because they don’t usually share the same memory as the CPU, exchanging data between CPU<>GPU can quickly become a bottleneck.</span></span> <span data-ttu-id="230f4-120">Microsoft의 해결책은 GPU에 galaxy를 설정 하는 것으로, GPU에 완전히 살고 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-120">Our solution was to make a galaxy on the GPU, and it had to live completely on the GPU.</span></span>

<span data-ttu-id="230f4-121">다양 한 패턴에서 수천 개의 점 입자를 사용 하 여 스트레스 테스트를 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-121">We started stress tests with thousands of point particles in various patterns.</span></span> <span data-ttu-id="230f4-122">이를 통해 galaxy에서 galaxy를 가져와 어떤 작업을 하는지 확인할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-122">This allowed us to get the galaxy on HoloLens to see what worked and what didn’t.</span></span>

### <a name="creating-the-position-of-the-stars"></a><span data-ttu-id="230f4-123">별 위치 만들기</span><span class="sxs-lookup"><span data-stu-id="230f4-123">Creating the position of the stars</span></span>

<span data-ttu-id="230f4-124">팀 멤버 중 한 명에 게 처음 위치 C# 에서 별을 생성 하는 코드를 이미 썼습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-124">One of our team members had already written the C# code that would generate stars at their initial position.</span></span> <span data-ttu-id="230f4-125">별은 타원에 있고 해당 위치는 (**curveOffset**, **ellipseSize**, **권한 상승**)로 설명할 수 있습니다. 여기서 **curveOffset** 는 타원을 따라 하는 별 각도이 고, **ellipseSize** 은 타원의 차원입니다. X 및 Z를 따라, galaxy 내에서 적절 한 별 권한 상승을 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-125">The stars are on an ellipse and their position can be described by (**curveOffset**, **ellipseSize**, **elevation**) where **curveOffset** is the angle of the star along the ellipse, **ellipseSize** is the dimension of the ellipse along X and Z, and elevation the proper elevation of the star within the galaxy.</span></span> <span data-ttu-id="230f4-126">따라서 각 별모양 특성을 사용 하 여 초기화 되는 버퍼 ([Unity의](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)경우)를 만들어 나머지 환경에 사용할 수 있는 GPU에 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-126">Thus, we can create a buffer ([Unity’s ComputeBuffer](http://docs.unity3d.com/ScriptReference/ComputeBuffer.html)) that would be initialized with each star attribute and send it on the GPU where it would live for the rest of the experience.</span></span> <span data-ttu-id="230f4-127">이 버퍼를 그리려면, galaxy를 나타내는 실제 메시 없이 임의의 요소 집합에서 셰이더 (GPU에서 코드)를 실행할 수 있는 [Unity의 DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-127">To draw this buffer, we use [Unity’s DrawProcedural](http://docs.unity3d.com/ScriptReference/Graphics.DrawProcedural.html) which allows running a shader (code on a GPU) on an arbitrary set of points without having an actual mesh that represents the galaxy:</span></span>

<span data-ttu-id="230f4-128">**CPU**</span><span class="sxs-lookup"><span data-stu-id="230f4-128">**CPU:**</span></span>




```
GraphicsDrawProcedural(MeshTopology.Points, starCount, 1);
```

<span data-ttu-id="230f4-129">**GPU**</span><span class="sxs-lookup"><span data-stu-id="230f4-129">**GPU:**</span></span>




```
v2g vert (uint index : SV_VertexID)
{

 // _Stars is the buffer we created that contains the initial state of the system
 StarDescriptor star = _Stars[index];
 …

}
```

<span data-ttu-id="230f4-130">수천 개의 입자가 있는 원시 순환 패턴으로 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-130">We started with raw circular patterns with thousands of particles.</span></span> <span data-ttu-id="230f4-131">이를 통해 많은 파티클을 관리 하 고 성능의 속도에서 실행할 수 있는 필요한 증거를 제공 했지만 galaxy의 전반적인 형태에는 만족 하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-131">This gave us the proof we needed that we could manage many particles AND run it at performant speeds, but we weren’t satisfied with the overall shape of the galaxy.</span></span> <span data-ttu-id="230f4-132">셰이프를 개선 하기 위해 회전을 사용 하는 다양 한 패턴 및 파티클 시스템을 시도 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-132">To improve the shape, we attempted various patterns and particle systems with rotation.</span></span> <span data-ttu-id="230f4-133">이러한 값은 파티클 및 성능 높게 유지 일치 하지만, 셰이프가 중심 근처에서 중단 되 고 나머지 유망한는 outwardly를 내보내는 동안 처음에는 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-133">These were initially promising because the number of particles and performance stayed consistent, but the shape broke down near the center and the stars were emitting outwardly which wasn't realistic.</span></span> <span data-ttu-id="230f4-134">시간을 조작 하 고 입자가 현실적으로 이동 하는 것을 허용 하는 내보내기가 필요 합니다 .이는 galaxy의 중심에 가깝게 반복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-134">We needed an emission that would allow us to manipulate time and have the particles move realistically, looping ever closer to the center of the galaxy.</span></span>

![이와 같이 회전 된 다양 한 패턴 및 파티클 시스템을 시도 했습니다.](images/galaxy-patterns-500px.png)

<span data-ttu-id="230f4-136">이와 같이 회전 된 다양 한 패턴 및 파티클 시스템을 시도 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-136">We attempted various patterns and particle systems that rotated, like these.</span></span>

<span data-ttu-id="230f4-137">우리 팀은 galaxies 함수에 대 한 몇 가지 연구를 수행 했으며 galaxy를 위해 특별히 사용자 지정 파티클 시스템을 만들었습니다 .이를 통해 galaxy의 theorizes는 "[밀도 wave 이론](https://en.wikipedia.org/wiki/Density_wave_theory)"을 기반으로 하는 타원에서 파티클을 이동할 수 있습니다. 더 높은 밀도 이지만 트래픽 걸림 같은 일관 된 flux.</span><span class="sxs-lookup"><span data-stu-id="230f4-137">Our team did some research about the way galaxies function and we made a custom particle system specifically for the galaxy so that we could move the particles on ellipses based on "[density wave theory](https://en.wikipedia.org/wiki/Density_wave_theory)," which theorizes that the arms of a galaxy are areas of higher density but in constant flux, like a traffic jam.</span></span> <span data-ttu-id="230f4-138">이는 안정적이 고 solid로 표시 되지만, 해당 하는 타원을 따라 이동 하는 동안에는 실제로는 arm에서 이동 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-138">It appears stable and solid, but the stars are actually moving in and out of the arms as they move along their respective ellipses.</span></span> <span data-ttu-id="230f4-139">시스템에서 파티클은 CPU에 존재 하지 않습니다. 즉, 카드를 생성 하 고 GPU에 모두 정위 하므로 전체 시스템은 단순히 초기 상태 + 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-139">In our system, the particles never exist on the CPU—we generate the cards and orient them all on the GPU, so the whole system is simply initial state + time.</span></span> <span data-ttu-id="230f4-140">다음과 같이 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-140">It progressed like this:</span></span>

![GPU 렌더링을 사용 하는 파티클 시스템 진행](images/spiral-galaxy-arms-500px.jpg)

<span data-ttu-id="230f4-142">GPU 렌더링을 사용 하는 파티클 시스템 진행</span><span class="sxs-lookup"><span data-stu-id="230f4-142">Progression of particle system with GPU rendering</span></span>


<span data-ttu-id="230f4-143">충분 한 타원이 추가 되 고 회전 되도록 설정 되 면 galaxies는 별 이동이 수렴 하는 "arm"을 형성 하기 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-143">Once enough ellipses are added and are set to rotate, the galaxies began to form “arms” where the movement of stars converge.</span></span> <span data-ttu-id="230f4-144">각 원형 경로를 따라 별의 간격에는 임의성이 지정 되 고 각 별 위치는 약간 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-144">The spacing of the stars along each elliptical path was given some randomness, and each star got a bit of positional randomness added.</span></span> <span data-ttu-id="230f4-145">이를 통해 별모양 이동 및 arm 모양의 보다 자연스럽 게 분포를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-145">This created a much more natural looking distribution of star movement and arm shape.</span></span> <span data-ttu-id="230f4-146">마지막으로, 중심 으로부터의 거리를 기준으로 색을 설정 하는 기능을 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-146">Finally, we added the ability to drive color based on distance from center.</span></span>

### <a name="creating-the-motion-of-the-stars"></a><span data-ttu-id="230f4-147">별 동작 만들기</span><span class="sxs-lookup"><span data-stu-id="230f4-147">Creating the motion of the stars</span></span>

<span data-ttu-id="230f4-148">일반적인 별모양 동작에 애니메이션 효과를 주려면 각 프레임에 대 한 상수 각도를 추가 하 고 일정 한 방사형 속도에서 줄임표를 따라 별 이동 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-148">To animate the general star motion, we needed to add a constant angle for each frame and to get stars moving along their ellipses at a constant radial velocity.</span></span> <span data-ttu-id="230f4-149">이는 **curveOffset**를 사용 하는 주된 이유입니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-149">This is the primary reason for using **curveOffset**.</span></span> <span data-ttu-id="230f4-150">이는 타원이 긴 측면에서 더 빠르게 이동 하지만 일반적인 동작이 양호 하다 고 판단 되기 때문에 기술적으로는 정확 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-150">This isn’t technically correct as stars will move faster along the long sides of the ellipses, but the general motion felt good.</span></span>

![별은 긴 호에서 더 빠르게 이동 하 여 가장자리에서 더 느리게 이동 합니다.](images/ellipse-movement.jpg)

<span data-ttu-id="230f4-152">별은 긴 호에서 더 빠르게 이동 하 여 가장자리에서 더 느리게 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-152">Stars move faster on the long arc, slower on the edges.</span></span>


<span data-ttu-id="230f4-153">이를 사용 하 여 각 별은 (**curveOffset**, **ellipseSize**, **권한 상승**, **age**)로 완전히 설명 됩니다. 여기서 **Age** 는 장면이 로드 된 이후 경과 된 총 시간의 누적입니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-153">With that, each star is fully described by (**curveOffset**, **ellipseSize**, **elevation**, **Age**) where **Age** is an accumulation of the total time that has passed since the scene was loaded.</span></span>




```
float3 ComputeStarPosition(StarDescriptor star)
{

  float curveOffset = star.curveOffset + Age;
  
  // this will be coded as a “sincos” on the hardware which will compute both sides
  float x = cos(curveOffset) * star.xRadii;
  float z = sin(curveOffset) * star.zRadii;
   
  return float3(x, star.elevation, z);
  
}
```

<span data-ttu-id="230f4-154">이를 통해 응용 프로그램 시작 시 수십 개의 별모양을 한 번 생성 한 후에는 설정 된 곡선을 따라 서명 된과의 별모양 집합에 애니메이션 효과를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-154">This allowed us to generate tens of thousands of stars once at the start of the application, then we animated a singled set of stars along the established curves.</span></span> <span data-ttu-id="230f4-155">모든 항목이 GPU에 있으므로 시스템은 CPU에 대 한 비용 없이 모든 별모양을 병렬로 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-155">Since everything is on the GPU, the system can animate all the stars in parallel at no cost to the CPU.</span></span>

![흰색 quads을 그릴 때의 모양은 다음과 같습니다.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="230f4-157">흰색 quads을 그릴 때의 모양은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-157">Here’s what it looks like when drawing white quads.</span></span>



<span data-ttu-id="230f4-158">각 쿼드 얼굴을 카메라에 배치 하기 위해 기 하 도형 셰이더를 사용 하 여 별 질감을 포함 하는 화면에서 각 별 위치를 2D 사각형으로 변환 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-158">To make each quad face the camera, we used a geometry shader to transform each star position to a 2D rectangle on the screen that will contain our star texture.</span></span>

![Quads 대신 다이아몬드입니다.](images/drawing-white-quads-300px.jpg)

<span data-ttu-id="230f4-160">Quads 대신 다이아몬드입니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-160">Diamonds instead of quads.</span></span>


<span data-ttu-id="230f4-161">과도 한 그리기 (픽셀이 처리 되는 횟수)를 최대한 제한 하려고 하기 때문에, 겹치는 부분을 줄일 수 있도록 quads 회전 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-161">Because we wanted to limit the overdraw (number of times a pixel will be processed) as much as possible, we rotated our quads so that they would have less overlap.</span></span>

### <a name="adding-clouds"></a><span data-ttu-id="230f4-162">클라우드 추가</span><span class="sxs-lookup"><span data-stu-id="230f4-162">Adding clouds</span></span>

<span data-ttu-id="230f4-163">여러 가지 방법으로 대규모 느낌을 얻을 수 있습니다 .이를 통해 볼륨 내 광선 행진를 사용 하 여 클라우드를 시뮬레이션 하기 위해 가능한 한 많은 수의 파티클을 그릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-163">There are many ways to get a volumetric feeling with particles—from ray marching inside of a volume to drawing as many particles as possible to simulate a cloud.</span></span> <span data-ttu-id="230f4-164">실시간 광선 행진 너무 비싸고 제작 하기 어렵습니다. 따라서 먼저 게임에서 포리스트를 렌더링 하기 위한 메서드를 사용 하 여 가짜 시스템을 빌드하고 카메라를 향하는 트리의 2D 이미지를 많이 사용해 보았습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-164">Real-time ray marching was going to be too expensive and hard to author, so we first tried building an imposter system using a method for rendering forests in games—with a lot of 2D images of trees facing the camera.</span></span> <span data-ttu-id="230f4-165">게임에서이 작업을 수행 하는 경우,이를 중심으로 회전 하는 카메라에서 렌더링 된 트리의 질감을 포함 하 고, 모든 이미지를 저장 하 고, 런타임에 각 빌보드 카드에 대해 뷰 방향과 일치 하는 이미지를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-165">When we do this in a game, we can have textures of trees rendered from a camera that rotates around, save all those images, and at runtime for each billboard card, select the image that matches the view direction.</span></span> <span data-ttu-id="230f4-166">이미지가 holograms 경우에도 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-166">This doesn't work as well when the images are holograms.</span></span> <span data-ttu-id="230f4-167">왼쪽 눈동자와 오른쪽 눈의 차이는이를 통해 훨씬 더 높은 해상도를 요구 하거나, 그렇지 않은 경우에만 플랫, 별칭 지정 또는 반복으로 보입니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-167">The difference between the left eye and the right eye make it so that we need a much higher resolution, or else it just looks flat, aliased, or repetitive.</span></span>

<span data-ttu-id="230f4-168">두 번째 시도에서는 가능한 한 많은 파티클을 사용해 보았습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-168">On our second attempt, we tried having as many particles as possible.</span></span> <span data-ttu-id="230f4-169">시각적 개체를 장면에 추가 하기 전에 추가로 업데이트할지 하 고 흐리게 표시 되는 경우 가장 적합 한 시각적 개체를 달성 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-169">The best visuals were achieved when we additively drew particles and blurred them before adding them to the scene.</span></span> <span data-ttu-id="230f4-170">이러한 접근 방식에 대 한 일반적인 문제는 한 번에 그릴 수 있는 파티클 수와 60 fps를 유지 하면서 적용 한 화면 영역의 크기와 관련이 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-170">The typical problems with that approach were related to how many particles we could draw at a single time and how much screen area they covered while still maintaining 60fps.</span></span> <span data-ttu-id="230f4-171">이 클라우드 느낌을 얻기 위해 결과 이미지를 흐리게 표시 하는 작업은 일반적으로 비용이 많이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-171">Blurring the resulting image to get this cloud feeling was usually a very costly operation.</span></span>

![질감이 없는 경우 클라우드는 2% 불투명도와 같이 표시 됩니다.](images/clouds-without-texture-300px.jpg)

<span data-ttu-id="230f4-173">질감이 없는 경우 클라우드는 2% 불투명도와 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-173">Without texture, this is what the clouds would look like with 2% opacity.</span></span>



<span data-ttu-id="230f4-174">추가 하 고 많은 것을 유지 하는 것은 서로에 게 여러 개의 quads 있고 동일한 픽셀을 반복 해 서 음영 처리 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-174">Being additive and having a lot of them means that we would have several quads on top of each other, repeatedly shading the same pixel.</span></span> <span data-ttu-id="230f4-175">Galaxy의 가운데에 있는 동일한 픽셀에는 수백 개의 quads가 있으며,이는 전체 화면을 완료할 때 상당한 비용이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-175">In the center of the galaxy, the same pixel has hundreds of quads on top of each other and this had a huge cost when being done full screen.</span></span>

<span data-ttu-id="230f4-176">전체 화면 클라우드를 수행 하 고이를 흐리게 하 려 시도 하는 것은 잘못 된 아이디어 이기 때문에 하드웨어에서 우리에 게 작업을 수행 하도록 결정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-176">Doing full screen clouds and trying to blur them would have been a bad idea, so instead we decided to let the hardware do the work for us.</span></span>

### <a name="a-bit-of-context-first"></a><span data-ttu-id="230f4-177">첫 번째 컨텍스트의 비트</span><span class="sxs-lookup"><span data-stu-id="230f4-177">A bit of context first</span></span>

<span data-ttu-id="230f4-178">게임에서 질감을 사용 하는 경우 질감 크기는 거의 사용 하려는 영역을 일치 하지만 다른 종류의 질감 필터링 질감의 픽셀에서 원하는 색을 보간 하는 그래픽 카드를 가져오고을 사용할 수 있습니다 ([질감 필터링<c3/>).](https://msdn.microsoft.com/library/dn642451.aspx)</span><span class="sxs-lookup"><span data-stu-id="230f4-178">When using textures in a game the texture size will rarely match the area we want to use it in, but we can use different kind of texture filtering to get the graphic card to interpolate the color we want from the pixels of the texture ([Texture Filtering](https://msdn.microsoft.com/library/dn642451.aspx)).</span></span> <span data-ttu-id="230f4-179">관심이 있는 필터링은 가장 인접 한 4 개를 사용 하 여 모든 픽셀의 값을 계산 하는 [이중 선형 필터링](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) 입니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-179">The filtering that interests us is [bilinear filtering](https://msdn.microsoft.com/library/windows/desktop/bb172357.aspx) which will compute the value of any pixel using the 4 nearest neighbors.</span></span>

![필터링 전 원래](images/texture-1.png)

![필터링 후 결과](images/texture-2.png)

<span data-ttu-id="230f4-182">이 속성을 사용 하면 질감을 한 영역에 두 번 그릴 때마다 결과가 흐리게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-182">Using this property, we see that each time we try to draw a texture into an area twice as big, it blurs the result.</span></span>

<span data-ttu-id="230f4-183">전체 화면으로 렌더링 하 고 이러한 귀중 한 시간 (밀리초)을 유지 하는 대신 약간의 화면으로 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-183">Instead of rendering to a full screen and losing those precious milliseconds we could be spending on something else, we render to a tiny version of the screen.</span></span> <span data-ttu-id="230f4-184">그런 다음이 질감을 복사 하 여 2의 계수를 여러 번 늘려서 프로세스의 콘텐츠를 흐리게 표시 하면서 전체 화면으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-184">Then, by copying this texture and stretching it by a factor of 2 several times, we get back to full screen while blurring the content in the process.</span></span>

![x3 upscale는 전체 해상도로 돌아갑니다.](images/galaxy-resolutions-300px.png)

<span data-ttu-id="230f4-186">x3 upscale는 전체 해상도로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-186">x3 upscale back to full resolution.</span></span>



<span data-ttu-id="230f4-187">이를 통해 클라우드 파트를 원래 비용의 일부분 으로만 가져올 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-187">This allowed us to get the cloud part with only a fraction of the original cost.</span></span> <span data-ttu-id="230f4-188">전체 해상도에서 클라우드를 추가 하는 대신 픽셀의 1/64th 칠하는 것 이며 전체 해상도로 텍스처를 다시 스트레치 합니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-188">Instead of adding clouds on the full resolution, we only paint 1/64th of the pixels and just stretch the texture back to full resolution.</span></span>

![왼쪽-1/8부터 전체 해상도로 upscale. 2를 사용 하 여 3 upscale 사용 합니다.](images/stars-upscaled-300px.jpg)

<span data-ttu-id="230f4-190">왼쪽-1/8부터 전체 해상도로 upscale. 2를 사용 하 여 3 upscale 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-190">Left, with an upscale from 1/8th to full resolution; and right, with 3 upscale using power of 2.</span></span>


<span data-ttu-id="230f4-191">그래픽 카드는 설정에서 4 픽셀을 사용 하 여 더 큰 영역과 아티팩트가 표시 되기 시작 하므로 크기의 1/64th에서 전체 크기로 이동 하려고 하면 완전히 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-191">Note that trying to go from 1/64th of the size to the full size in one go would look completely different, as the graphic card would still use 4 pixels in our setup to shade a bigger area and artifacts start to appear.</span></span>

<span data-ttu-id="230f4-192">그런 다음 더 작은 카드로 전체 해상도를 추가 하는 경우 전체 galaxy를 얻게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-192">Then, if we add full resolution stars with smaller cards, we get the full galaxy:</span></span>

![전체 해상도를 사용 하는 galaxy 렌더링의 거의 최종 결과](images/full-galaxy-500px.png)

<span data-ttu-id="230f4-194">셰이프를 사용 하 여 올바른 트랙을 만든 후에는 클라우드 계층을 추가 하 고, Photoshop에서 그린 것으로 임시 점을 교환 하 고, 몇 가지 추가 색을 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-194">Once we were on the right track with the shape, we added a layer of clouds, swapped out the temporary dots with ones we painted in Photoshop, and added some additional color.</span></span> <span data-ttu-id="230f4-195">그 결과, microsoft의 예술 및 엔지니어링 팀이 Milky 된 방식으로, CPU를 처리 시간이 소모 않고도 깊이, 볼륨 및 동작을 갖는 목표를 달성 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-195">The result was a Milky Way Galaxy our art and engineering teams both felt good about and it met our goals of having depth, volume, and motion—all without taxing the CPU.</span></span>

![3D의 최종 Milky 방법입니다.](images/final-galaxy-500px.jpg)

<span data-ttu-id="230f4-197">3D의 최종 Milky 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-197">Our final Milky Way Galaxy in 3D.</span></span>


### <a name="more-to-explore"></a><span data-ttu-id="230f4-198">자세히 살펴보기</span><span class="sxs-lookup"><span data-stu-id="230f4-198">More to explore</span></span>

<span data-ttu-id="230f4-199">Galaxy 탐색기 앱에 대 한 코드를 열고 개발자를 위해 [GitHub](https://github.com/Microsoft/GalaxyExplorer) 에서 사용할 수 있도록 했습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-199">We've open-sourced the code for the Galaxy Explorer app and made it available on [GitHub](https://github.com/Microsoft/GalaxyExplorer) for developers to build on.</span></span>

<span data-ttu-id="230f4-200">Galaxy 탐색기의 개발 프로세스에 대 한 자세한 정보를 확인 하는 데 관심이 있나요?</span><span class="sxs-lookup"><span data-stu-id="230f4-200">Interested in finding out more about the development process for Galaxy Explorer?</span></span> <span data-ttu-id="230f4-201">[Microsoft HoloLens YouTube 채널](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)의 모든 이전 프로젝트 업데이트를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="230f4-201">Check out all our past project updates on the [Microsoft HoloLens YouTube channel](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL).</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="230f4-202">작성자 정보</span><span class="sxs-lookup"><span data-stu-id="230f4-202">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="Picture of Karim Luccin at his desk" width="60" height="60" src="images/karim-thumb.jpg" /></td>
<td style="border:0"><span data-ttu-id="230f4-203"><b>Karim Luccin</b> 는 소프트웨어 엔지니어 및 팬시 시각적 개체 열성적인입니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-203"><b>Karim Luccin</b> is a Software Engineer and fancy visuals enthusiast.</span></span> <span data-ttu-id="230f4-204">Galaxy 탐색기의 그래픽 엔지니어 였습니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-204">He was the Graphics Engineer for Galaxy Explorer.</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Photo of art lead Andy Zibits" width="60" height="60" src="images/andy-avatar.png" /></td>
<td style="border:0"><span data-ttu-id="230f4-205"><b>Andy Zibits</b> 는 Galaxy 탐색기 및 fought에 대 한 3d 모델링 팀에서 더 많은 파티클을 관리 하는 아트 도선 및 공간 열성적인입니다.</span><span class="sxs-lookup"><span data-stu-id="230f4-205"><b>Andy Zibits</b> is an Art Lead and space enthusiast who managed the 3D modeling team for Galaxy Explorer and fought for even more particles.</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="230f4-206">참조</span><span class="sxs-lookup"><span data-stu-id="230f4-206">See also</span></span>
* [<span data-ttu-id="230f4-207">GitHub의 Galaxy 탐색기</span><span class="sxs-lookup"><span data-stu-id="230f4-207">Galaxy Explorer on GitHub</span></span>](https://github.com/Microsoft/GalaxyExplorer)
* [<span data-ttu-id="230f4-208">YouTube의 Galaxy 탐색기 프로젝트 업데이트</span><span class="sxs-lookup"><span data-stu-id="230f4-208">Galaxy Explorer project updates on YouTube</span></span>](https://www.youtube.com/playlist?list=PLZCHH_4VqpRj0Nl46J0LNRkMyBNU4knbL)
