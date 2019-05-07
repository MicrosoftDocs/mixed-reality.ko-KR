---
title: 사례 연구-구멍에 실제로 탐색
description: 이 사례 연구에는 HoloLens, 벽, floor, 및에 실제 환경에서 가상 있는데 뒤 보려는 사용자에 대 한 "매직 창" 효과 구현 하는 방법을 설명 합니다.
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, magic 창, 시차
ms.openlocfilehash: 945a09614fbc77400825b524f4e0b591bf7b1f6b
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873932"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a><span data-ttu-id="0cd50-104">사례 연구-구멍에 실제로 탐색</span><span class="sxs-lookup"><span data-stu-id="0cd50-104">Case study - Looking through holes in your reality</span></span>

<span data-ttu-id="0cd50-105">혼합된 현실 및 Microsoft HoloLens 사용 하 여 수행할 수 있는 작업에 대 한 생각을 하는 경우는 일반적으로 맞도록 질문 "하는 개체 내 공간을 추가할 수 있습니까?"와 같은</span><span class="sxs-lookup"><span data-stu-id="0cd50-105">When people think about mixed reality and what they can do with Microsoft HoloLens, they usually stick to questions like "What objects can I add to my room?"</span></span> <span data-ttu-id="0cd50-106">"어떤 수 있습니까 계층 내 공간 위에?" 또는</span><span class="sxs-lookup"><span data-stu-id="0cd50-106">or “What can I layer on top of my space?"</span></span> <span data-ttu-id="0cd50-107">고려할 수 있습니다 다른 영역을 강조 표시 하려는-magic 트릭을 기본적으로-동일한 기술을 사용 하 여 들어오거나와 관련해 서 실제 개체를 통해 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-107">I’d like to highlight another area you can consider—essentially a magic trick—using the same technology to look into or through real physical objects around you.</span></span>

## <a name="the-tech"></a><span data-ttu-id="0cd50-108">기술 지원 담당자</span><span class="sxs-lookup"><span data-stu-id="0cd50-108">The tech</span></span>

<span data-ttu-id="0cd50-109">벽을 통해 중단 됩니다 대로 외계인 경우 느껴지거나 했습니다  **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, 안전 벽을 잠금 해제  **[조각](case-study-creating-an-immersive-experience-in-fragments.md)**, 이루어지는 했거나 UNSC 무한대 격납고에서 참조 하는  **[2015에서 E3 Halo 5 경험](https://www.youtube.com/watch?v=QDw5QjDtFy8)** 에 대 한 말하고자 보았을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-109">If you've fought aliens as they break through your walls in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, unlocked a wall safe in **[Fragments](case-study-creating-an-immersive-experience-in-fragments.md)**, or were lucky enough to see the UNSC Infinity hangar in the **[Halo 5 experience at E3 in 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, then you've seen what I'm talking about.</span></span> <span data-ttu-id="0cd50-110">상상력에 따라 임시 구멍에 건식에 배치 하거나 느슨한 floorboard 아래 세계를 숨기려면이 visual 트릭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-110">Depending on your imagination, this visual trick can be used to put temporary holes in your drywall or to hide worlds under a loose floorboard.</span></span>

![RoboRaid 3 차원 파이프 및 다른 구조 벽을 중단 된 침략자 만들 구멍을 통해서만 표시 뒤에 추가 합니다.](images/roboraid-640px.png)

<span data-ttu-id="0cd50-112">RoboRaid 3 차원 파이프 및 다른 구조 벽을 중단 된 침략자 만들 구멍을 통해서만 표시 뒤에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-112">RoboRaid adds three-dimensional pipes and other structure behind your walls, visible only through holes created as the invaders break through.</span></span>

<span data-ttu-id="0cd50-113">이러한 고유 홀로그램 중 하나를 사용 하 여 HoloLens에, 실제로 실제 창을 통해 자체를 표시 하는 동일한 방식 앱 사용자 층을 통해 또는 벽 뒤 콘텐츠의 효과 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-113">Using one of these unique holograms on HoloLens, an app can provide the illusion of content behind your walls or through your floor in the same way that reality presents itself through an actual window.</span></span> <span data-ttu-id="0cd50-114">왼쪽으로 직접 이동 하 고 오른쪽에 무엇이 든 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-114">Move yourself left, and you can see whatever is on the right side.</span></span> <span data-ttu-id="0cd50-115">좀 더 자세히를 가져오고 모든 좀 더 자세한를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-115">Get closer, and you can see a bit more of everything.</span></span> <span data-ttu-id="0cd50-116">주요한 차이점은는 실제 구멍 수 있으며, 사용자 층 함에도 수 없습니다 마법 holographic 콘텐츠를 통해 않았다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-116">The major difference is that real holes allow you through, while your floor stubbornly won't let you climb through to that magical holographic content.</span></span> <span data-ttu-id="0cd50-117">(태스크를 추가 백로그.)</span><span class="sxs-lookup"><span data-stu-id="0cd50-117">(I'll add a task to the backlog.)</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="0cd50-118">백그라운드 작업</span><span class="sxs-lookup"><span data-stu-id="0cd50-118">Behind the scenes</span></span>

<span data-ttu-id="0cd50-119">이 트릭은 두 가지 효과가의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-119">This trick is a combination of two effects.</span></span> <span data-ttu-id="0cd50-120">첫째, holographic 콘텐츠 "공간 앵커"를 사용 하 여 전 세계에 고정</span><span class="sxs-lookup"><span data-stu-id="0cd50-120">First, holographic content is pinned to the world using "spatial anchors."</span></span> <span data-ttu-id="0cd50-121">해당 콘텐츠를 "world 잠긴" 앵커를 사용 하 여는에서 원하는 항목 하지 시각적으로 드리프트를 거의 실제 개체에서 기본 공간 매핑 시스템에 여유 공간 해당 3D 모델을 업데이트 또는 이동할 때에 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-121">Using anchors to make that content "world-locked" means that what you're looking at doesn't visually drift away from the physical objects near it, even as you move or the underlying spatial mapping system updates its 3D model of your room.</span></span>

<span data-ttu-id="0cd50-122">둘째,만 표시 되도록 구멍을 통과 하 여 실제로 holographic 콘텐츠 매우 구체적인 공간을 시각적으로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-122">Secondly, that holographic content is visually limited to a very specific space, so you can only see through the hole in your reality.</span></span> <span data-ttu-id="0cd50-123">해당 폐색 탐색 논리 구멍, 창 또는 이르는 길 트릭을 판매 해야 하는 데 필요한 경우</span><span class="sxs-lookup"><span data-stu-id="0cd50-123">That occlusion is necessary to require looking through a logical hole, window, or doorway, which sells the trick.</span></span> <span data-ttu-id="0cd50-124">항목 보기의 대부분을 차단 하지 않고 비밀 봤다면 차원 공간에서 crack 방금 잘못 배치 공룡 처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-124">Without something blocking most of the view, a crack in space to a secret Jurassic dimension might just look like a poorly placed dinosaur.</span></span>

![이 변경은 실제 스크린 샷 아니라 HoloLens에서 MR 기본 사항 101에서 비밀 지 표시 되는 모양을 보여 줍니다.](images/origamiholecomposited-640px.png)

<span data-ttu-id="0cd50-128">이 변경은 실제 스크린샷에서 아니라는 방법의 예시에서 비밀의 지 하는 [MR 기본 사항 101](holograms-101.md) HoloLens에서.</span><span class="sxs-lookup"><span data-stu-id="0cd50-128">This is not an actual screenshot, but an illustration of how the secret underworld from the [MR Basics 101](holograms-101.md) looks on HoloLens.</span></span> <span data-ttu-id="0cd50-129">검은색 인클로저 나타나지 않지만 가상 구멍을 통해 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-129">The black enclosure doesn’t show up, but you can see content through a virtual hole.</span></span> <span data-ttu-id="0cd50-130">(실제 장치를 살펴보는 경우 바닥 넘어서 없는 처럼 눈 먼 거리에 집중 하기 때문에 훨씬 더 사라집니다.)</span><span class="sxs-lookup"><span data-stu-id="0cd50-130">(When looking through an actual device, the floor would seem to disappear even more because your eyes focus at a further distance as if it’s not even there.)</span></span>

### <a name="world-locking-holographic-content"></a><span data-ttu-id="0cd50-131">Holographic 콘텐츠 world 잠금</span><span class="sxs-lookup"><span data-stu-id="0cd50-131">World-locking holographic content</span></span>

<span data-ttu-id="0cd50-132">Unity에서 전 세계 잠긴 상태로 유지 하려면 holographic 콘텐츠를 일으키는 다음과 같습니다. WorldAnchor 구성 요소를 추가 하는 것 만큼 쉽습니다</span><span class="sxs-lookup"><span data-stu-id="0cd50-132">In Unity, causing holographic content to stay world-locked is as easy as adding a WorldAnchor component:</span></span>

```
myObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="0cd50-133">WorldAnchor 구성 요소는 위치 및 해당 GameObject (및 따라서 계층 구조에서 해당 개체에서 다른 작업)의 실제 개체 주변에 상대적으로 안정적인 되도록 회전에 지속적으로 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-133">The WorldAnchor component will constantly adjust the position and rotation of its GameObject (and thus anything else under that object in the hierarchy) to keep it stable relative to nearby physical objects.</span></span> <span data-ttu-id="0cd50-134">콘텐츠를 작성할 때이 가상 구멍 중심이 개체의 루트 피벗 하는 방식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-134">When authoring your content, create it in such a way that the root pivot of your object is centered at this virtual hole.</span></span> <span data-ttu-id="0cd50-135">(개체의 피벗 벽의 깊은 수준에 있으면 해당 약간 조정 위치 및 회전에 훨씬 더 눈에 띄는 되 고 구멍 빌드되며 같지 않을 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="0cd50-135">(If your object's pivot is deep in the wall, its slight tweaks in position and rotation will be much more noticeable, and the hole may not look very stable.)</span></span>

### <a name="occluding-everything-but-the-virtual-hole"></a><span data-ttu-id="0cd50-136">가상 구멍을 제외한 모든 occluding</span><span class="sxs-lookup"><span data-stu-id="0cd50-136">Occluding everything but the virtual hole</span></span>

<span data-ttu-id="0cd50-137">선택적으로 담 벼 락에서 숨겨진 항목에 보기를 차단 하는 방법의 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-137">There are a variety of ways to selectively block the view to what is hidden in your walls.</span></span> <span data-ttu-id="0cd50-138">가장 간단한 것 HoloLens 완전히 black 개체 보이지 않는 나타나는지 즉는 가산적 표시 되는 사실을 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-138">The simplest one takes advantage of the fact that HoloLens uses an additive display, which means that fully black objects appear invisible.</span></span> <span data-ttu-id="0cd50-139">모든 특수 셰이더 또는 자재 트릭을 수행 하지 않고 Unity에서 이렇게 하려면-을 black 자료를 만들고 콘텐츠에서 상자 하는 개체에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-139">You can do this in Unity without doing any special shader or material tricks— just create a black material and assign it to an object that boxes in your content.</span></span> <span data-ttu-id="0cd50-140">3D 모델링을 수행 하는 같은 생각 하지 않습니다, 경우에 많은 기본 쿼드 개체를 사용 하 여 고 약간 서로 겹치는 하기만 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-140">If you don't feel like doing 3D modeling, just use a handful of default Quad objects and overlap them slightly.</span></span> <span data-ttu-id="0cd50-141">이 방식의 단점은 많이 있지만 빠르게 작동 하는 것 이며 낮은 충실도 개념 작업 증명을 가져오는, 나중에 리팩터링 하려는 의심 되는 경우에 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-141">There are a number of drawbacks to this approach, but it is the fastest way to get something working, and getting a low-fidelity proof of concept working is great, even if you suspect you might want to refactor it later.</span></span>

<span data-ttu-id="0cd50-142">위의 "블랙 박스" 접근 방식에 큰 단점 하나는 잘 촬영 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-142">One major drawback to the above "black box" approach is that it doesn't photograph well.</span></span> <span data-ttu-id="0cd50-143">효과 HoloLens의 표시를 통해 완벽 하 게 보일 수, 있지만 수행한 모든 스크린샷 벽의 floor 남은 대신 큰 검은색 개체를 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-143">While your effect might look perfect through the display of HoloLens, any screenshots you take will show a large black object instead of what remains of your wall or floor.</span></span> <span data-ttu-id="0cd50-144">그 이유는 실제 하드웨어와 스크린 샷을 복합 홀로그램와 진실 다르게 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-144">The reason for this is that the physical hardware and screenshots composite holograms and reality differently.</span></span> <span data-ttu-id="0cd50-145">일부 가짜 수학에 잠시 우회 보겠습니다...</span><span class="sxs-lookup"><span data-stu-id="0cd50-145">Let's detour for a moment into some fake math...</span></span>

<span data-ttu-id="0cd50-146">*가짜 수학 경고! 이러한 번호 및 수식은 모든 종류의 정확한 메트릭 일 수 없습니다는 내용을 설명 하기 위한 것!*</span><span class="sxs-lookup"><span data-stu-id="0cd50-146">*Fake math alert! These numbers and formulas are meant to illustrate a point, not to be any sort of accurate metric!*</span></span>

<span data-ttu-id="0cd50-147">HoloLens를 통해 참조 항목:</span><span class="sxs-lookup"><span data-stu-id="0cd50-147">What you see through HoloLens:</span></span>

```
( Reality * darkening_amount ) + Holograms
```

<span data-ttu-id="0cd50-148">스크린샷 및 비디오에 표시 되는 내용:</span><span class="sxs-lookup"><span data-stu-id="0cd50-148">What you see in screenshots and video:</span></span>

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

<span data-ttu-id="0cd50-149">영어의 경우: HoloLens를 통해 표시 되는 간단한의 조합 어두운된 실제로 (선글라스 통해와 같이) 및 모든 홀로그램 앱 표시 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-149">In English: What you see through HoloLens is a simple combination of darkened reality (like through sunglasses) and whatever holograms the app wants to show.</span></span> <span data-ttu-id="0cd50-150">하지만 카메라의 이미지 픽셀 별 투명도 값에 따라 앱의 홀로그램 혼합 됩니다 스크린 샷을 사용 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="0cd50-150">But when you take a screenshot, the camera's image is blended with the app's holograms according to the per-pixel transparency value.</span></span>

<span data-ttu-id="0cd50-151">이 문제를 해결 하는 한 가지 방법은 깊이 버퍼에 쓸 및 기타 불투명 자료를 사용 하 여 정렬만 "블랙 박스" 자료를 변경 하기 위해서입니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-151">One way to get around this is to change the "black box" material to only write to the depth buffer, and sort with all the other opaque materials.</span></span> <span data-ttu-id="0cd50-152">이 예제를 확인 하세요 합니다 [GitHub의는 MixedRealityToolkit에 WindowOcclusion.shader 파일](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-152">For an example of this, check out the [WindowOcclusion.shader file in the MixedRealityToolkit on GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span></span> <span data-ttu-id="0cd50-153">여기에 관련 줄을 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-153">The relevant lines are copied here:</span></span>

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

<span data-ttu-id="0cd50-154">(오프셋에 유의 하세요 "50, 100" 줄 것 이기 때문 것을 생략 하는 것이 관련 되지 않은 문제를 해결 하는 것입니다.)</span><span class="sxs-lookup"><span data-stu-id="0cd50-154">(Note the "Offset 50, 100" line is to deal with unrelated issues, so it'd probably make sense to leave that out.)</span></span>

<span data-ttu-id="0cd50-155">보이지 않는 폐색 자료를 구현 하는 올바른 표시에서 및 혼합 현실 스크린샷에서 보이는 상자를 그리는 앱 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-155">Implementing an invisible occlusion material like that will let your app draw a box that looks correct in the display and in mixed-reality screenshots.</span></span> <span data-ttu-id="0cd50-156">보너스 점수에 대 한 이보다 적은 수의 보이지 않는 픽셀을 그릴 clever 수행 하 여 더욱 상자의 성능을 개선 하기 위해 시도할 수 있지만 근본 원인을 제거를 얻을 수 있습니다 하 고 일반적으로 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-156">For bonus points, you can try to improve the performance of that box even further by doing clever things to draw even fewer invisible pixels, but that can really get into the weeds and usually won't be necessary.</span></span>

![Unity 그립니다 외부 부분 occluding 상자 제외 하 고 해당 하는 대로 MR 기본 사항 101에서 비밀 지 하는 다음과 같습니다.](images/underworld-occluded-640px.png)

<span data-ttu-id="0cd50-159">비밀 지 하는 다음과 같습니다 [MR 기본 사항 101](holograms-101.md) 으로 Unity 외부 부분 occluding 상자 제외 하 고이 그립니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-159">Here is the secret underworld from [MR Basics 101](holograms-101.md) as Unity draws it, except for the outer parts of the occluding box.</span></span> <span data-ttu-id="0cd50-160">Note는 지 하의 피벗 임을 구멍을 유지 하는 데 도움이 되는 상자의 가운데에 실제 floor를 기준으로 최대한 안정적으로.</span><span class="sxs-lookup"><span data-stu-id="0cd50-160">Note that the pivot for the underworld is at the center of the box, which helps keep the hole as stable as possible relative to your actual floor.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="0cd50-161">사용자가 직접 수행</span><span class="sxs-lookup"><span data-stu-id="0cd50-161">Do it yourself</span></span>

<span data-ttu-id="0cd50-162">HoloLens 있고 직접 효과 사용 하 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="0cd50-162">Have a HoloLens and want to try out the effect for yourself?</span></span> <span data-ttu-id="0cd50-163">(코딩할 필요 없이) 할 수 없는 가장 간단한 방법은 로드 한 후 무료 3D 뷰어 앱을 설치 하는 것은 [GitHub에서 제공한 the.fbx 파일 다운로드](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) 방에 꽃 pot 모델을 볼 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-163">The easiest thing you can do (no coding required) is to install the free 3D Viewer app and then load the [download the.fbx file I've provided on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) to view a flower pot model in your room.</span></span> <span data-ttu-id="0cd50-164">HoloLens, 로드 및 직장 효과 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-164">Load it on HoloLens, and you can see the illusion at work.</span></span> <span data-ttu-id="0cd50-165">모델 앞에 있는 경우 볼 수 있습니다를 작은 구멍에-기타 등등 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-165">When you're in front of the model, you can only see into the small hole—everything else is invisible.</span></span> <span data-ttu-id="0cd50-166">다른 쪽에서 모델을 조회 하 고 완전히 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-166">Look at the model from any other side and it disappears entirely.</span></span> <span data-ttu-id="0cd50-167">상상할 수 있는 몇 가지 아이디어를 생성 하려면 세로 화면에 대 한 가상 구멍 위치로 이동, 회전 및 크기 조정 컨트롤의 3D 뷰어 사용!</span><span class="sxs-lookup"><span data-stu-id="0cd50-167">Use the movement, rotation, and scale controls of 3D Viewer to position the virtual hole against any vertical surface you can think of to generate some ideas!</span></span>

![Unity 편집기에서이 모델을 보기는 flowerpot 주위에 큰 검은색 상자 표시 됩니다.](images/magicwindowflowerpotineditor.png)

<span data-ttu-id="0cd50-170">Unity 편집기에서이 모델을 보기는 flowerpot 주위에 큰 검은색 상자 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-170">Viewing this model in your Unity editor will show a large black box around the flowerpot.</span></span> <span data-ttu-id="0cd50-171">상자가 사라집니다, HoloLens에서 매직 창 효과를 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-171">On HoloLens, the box disappears, giving way to a magic window effect.</span></span>

<span data-ttu-id="0cd50-172">이 기술을 사용 하는 앱을 빌드 하려는 경우 체크 아웃 합니다 [MR 기본 사항 101 자습서](holograms-101.md) 에 [혼합 현실 자습서](tutorials.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-172">If you want to build an app that uses this technique, check out the [MR Basics 101 tutorial](holograms-101.md) in the [Mixed Reality tutorials](tutorials.md).</span></span> <span data-ttu-id="0cd50-173">7 장 (위의 그림)로 숨겨진된 지 표시 하 여 층에 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-173">Chapter 7 ends with an explosion in your floor that reveals a hidden underworld (as pictured above).</span></span> <span data-ttu-id="0cd50-174">자습서가 지루한 라고?</span><span class="sxs-lookup"><span data-stu-id="0cd50-174">Who said tutorials had to be boring?</span></span>

<span data-ttu-id="0cd50-175">다음은 몇 가지 아이디어를 작성할 수 있는이 다음의:</span><span class="sxs-lookup"><span data-stu-id="0cd50-175">Here are some ideas of where you can take this idea next:</span></span>
* <span data-ttu-id="0cd50-176">대화형 가상 구멍 내부 콘텐츠를 확인 하는 방법을 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-176">Think of ways to make the content inside the virtual hole interactive.</span></span> <span data-ttu-id="0cd50-177">사용자가 해당 경계를 넘어 몇 가지 영향을 미칠 수 불가사의이 트릭을 제공할 수 있는의 의미 실제로 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-177">Letting your users have some impact beyond their walls can really improve the sense of wonder that this trick can provide.</span></span>
* <span data-ttu-id="0cd50-178">알려진된 영역에 다시 개체를 통해 참조 하는 방법을 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cd50-178">Think of ways to see through objects back to known areas.</span></span> <span data-ttu-id="0cd50-179">예를 들어 수 holographic 구멍 커피 테이블에 배치 하는 방법을 아래에 floor를 참조 하세요?</span><span class="sxs-lookup"><span data-stu-id="0cd50-179">For example, how can you put a holographic hole in your coffee table and see your floor beneath it?</span></span>

## <a name="about-the-author"></a><span data-ttu-id="0cd50-180">저자 소개</span><span class="sxs-lookup"><span data-stu-id="0cd50-180">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><span data-ttu-id="0cd50-181"><b>Eric Rehmeyer</b></span><span class="sxs-lookup"><span data-stu-id="0cd50-181"><b>Eric Rehmeyer</b></span></span><br><span data-ttu-id="0cd50-182">선임 소프트웨어 엔지니어 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="0cd50-182">Senior Software Engineer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="0cd50-183">참조</span><span class="sxs-lookup"><span data-stu-id="0cd50-183">See also</span></span>
* [<span data-ttu-id="0cd50-184">MR 기본 101: 디바이스를 사용하는 완전한 프로젝트</span><span class="sxs-lookup"><span data-stu-id="0cd50-184">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="0cd50-185">좌표계</span><span class="sxs-lookup"><span data-stu-id="0cd50-185">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="0cd50-186">공간 앵커</span><span class="sxs-lookup"><span data-stu-id="0cd50-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="0cd50-187">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="0cd50-187">Spatial mapping</span></span>](spatial-mapping.md)
