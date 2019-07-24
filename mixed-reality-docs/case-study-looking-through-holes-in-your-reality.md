---
title: 사례 연구-현실에서의 구멍 검색
description: 이 사례 연구에서는 HoloLens에 "자동 창" 효과를 구현 하 여 사용자가 실제 환경 내에서 옆면을 볼 수 있도록 하는 방법을 설명 합니다.
author: EricRehmeyer
ms.author: ericrehm
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 마법 창, 시차
ms.openlocfilehash: 945a09614fbc77400825b524f4e0b591bf7b1f6b
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873932"
---
# <a name="case-study---looking-through-holes-in-your-reality"></a><span data-ttu-id="8ed31-104">사례 연구-현실에서의 구멍 검색</span><span class="sxs-lookup"><span data-stu-id="8ed31-104">Case study - Looking through holes in your reality</span></span>

<span data-ttu-id="8ed31-105">사용자가 혼합 현실 및 Microsoft HoloLens로 수행할 수 있는 작업에 대해 생각 하는 경우 일반적으로 "대화방에 추가할 수 있는 개체는 무엇 인가요?"와 같은 질문에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-105">When people think about mixed reality and what they can do with Microsoft HoloLens, they usually stick to questions like "What objects can I add to my room?"</span></span> <span data-ttu-id="8ed31-106">또는 "공간 위에 계층화 할 수 있는 것은 무엇입니까?"</span><span class="sxs-lookup"><span data-stu-id="8ed31-106">or “What can I layer on top of my space?"</span></span> <span data-ttu-id="8ed31-107">고려할 수 있는 다른 영역을 강조 하 고 싶습니다. 기본적으로 동일한 기술을 사용 하 여 사용자를 대상으로 하는 실제 개체를 조회 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-107">I’d like to highlight another area you can consider—essentially a magic trick—using the same technology to look into or through real physical objects around you.</span></span>

## <a name="the-tech"></a><span data-ttu-id="8ed31-108">기술</span><span class="sxs-lookup"><span data-stu-id="8ed31-108">The tech</span></span>

<span data-ttu-id="8ed31-109">**[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)** 의 벽을 fought 하 고, **[조각](case-study-creating-an-immersive-experience-in-fragments.md)** 에서 벽을 안전 하 게 잠금 해제 하거나, **[2015의 E3에 있는 HALO 5 환경](https://www.youtube.com/watch?v=QDw5QjDtFy8)** 에서 unsc Infinity hangar를 볼 만큼 충분 하다 고 생각 하는 경우, 제가 이야기 하 고 있는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-109">If you've fought aliens as they break through your walls in **[RoboRaid](https://www.youtube.com/watch?v=Hf9qkURqtbM)**, unlocked a wall safe in **[Fragments](case-study-creating-an-immersive-experience-in-fragments.md)**, or were lucky enough to see the UNSC Infinity hangar in the **[Halo 5 experience at E3 in 2015](https://www.youtube.com/watch?v=QDw5QjDtFy8)**, then you've seen what I'm talking about.</span></span> <span data-ttu-id="8ed31-110">상상력에 따라이 시각적 트릭을 사용 하 여 drywall에 임시 구멍을 배치 하거나 느슨한 floorboard에서 환경을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-110">Depending on your imagination, this visual trick can be used to put temporary holes in your drywall or to hide worlds under a loose floorboard.</span></span>

![RoboRaid은 3 차원 파이프와 벽 뒤에 있는 다른 구조를 추가 하 여 invaders break로 생성 된 구멍을 통해서만 표시 됩니다.](images/roboraid-640px.png)

<span data-ttu-id="8ed31-112">RoboRaid은 3 차원 파이프와 벽 뒤에 있는 다른 구조를 추가 하 여 invaders break로 생성 된 구멍을 통해서만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-112">RoboRaid adds three-dimensional pipes and other structure behind your walls, visible only through holes created as the invaders break through.</span></span>

<span data-ttu-id="8ed31-113">앱은 HoloLens의 이러한 고유 holograms 중 하나를 사용 하 여 실제 창을 통해 자신을 나타내는 것과 같은 방식으로 벽 뒤에 있는 콘텐츠의 효과를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-113">Using one of these unique holograms on HoloLens, an app can provide the illusion of content behind your walls or through your floor in the same way that reality presents itself through an actual window.</span></span> <span data-ttu-id="8ed31-114">왼쪽으로 이동 하 고 오른쪽에 있는 모든 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-114">Move yourself left, and you can see whatever is on the right side.</span></span> <span data-ttu-id="8ed31-115">좀 더 자세히 알아보겠습니다. 모든 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-115">Get closer, and you can see a bit more of everything.</span></span> <span data-ttu-id="8ed31-116">주요 차이점은 실제 구멍에서를 사용 하는 것 이지만, 바닥 stubbornly는 해당 마법 holographic 콘텐츠를 통과할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-116">The major difference is that real holes allow you through, while your floor stubbornly won't let you climb through to that magical holographic content.</span></span> <span data-ttu-id="8ed31-117">(백로그에 작업을 추가 합니다.)</span><span class="sxs-lookup"><span data-stu-id="8ed31-117">(I'll add a task to the backlog.)</span></span>

## <a name="behind-the-scenes"></a><span data-ttu-id="8ed31-118">백그라운드 작업</span><span class="sxs-lookup"><span data-stu-id="8ed31-118">Behind the scenes</span></span>

<span data-ttu-id="8ed31-119">이 트릭은 두 가지 효과의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-119">This trick is a combination of two effects.</span></span> <span data-ttu-id="8ed31-120">첫째, holographic 콘텐츠는 "공간 앵커"를 사용 하 여 전 세계에 고정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-120">First, holographic content is pinned to the world using "spatial anchors."</span></span> <span data-ttu-id="8ed31-121">앵커를 사용 하 여 "세계에서 잠김" 콘텐츠를 사용 하면 이동 하는 경우 또는 기본 공간 매핑 시스템에서 해당 공간의 3D 모델을 업데이트 하는 경우에도 원하는 내용이 근처의 물리적 개체에서 시각적으로 사라지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-121">Using anchors to make that content "world-locked" means that what you're looking at doesn't visually drift away from the physical objects near it, even as you move or the underlying spatial mapping system updates its 3D model of your room.</span></span>

<span data-ttu-id="8ed31-122">둘째, holographic 내용이 매우 특정 공간으로 시각적으로 제한 되므로 현실에서 구멍을 통해서만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-122">Secondly, that holographic content is visually limited to a very specific space, so you can only see through the hole in your reality.</span></span> <span data-ttu-id="8ed31-123">이 폐색는 트릭을 판매 하는 논리 구멍, 창 또는 이르는 길을 살펴보는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-123">That occlusion is necessary to require looking through a logical hole, window, or doorway, which sells the trick.</span></span> <span data-ttu-id="8ed31-124">대부분의 뷰를 차단 하지 않으면 비밀 Jurassic 차원에 대 한 공간을 해독 하는 것은 잘못 배치 된 공룡 처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-124">Without something blocking most of the view, a crack in space to a secret Jurassic dimension might just look like a poorly placed dinosaur.</span></span>

![이는 실제 스크린샷은 아니지만, MR 기본 사항 101의 비밀 지 여부에 대 한 설명은 HoloLens를 확인 하는 방법에 대 한 설명입니다.](images/origamiholecomposited-640px.png)

<span data-ttu-id="8ed31-128">실제 스크린샷은 아니지만, [MR 기본 사항 101](holograms-101.md) 의 비밀 지가 HoloLens를 어떻게 볼 수 있는 지에 대 한 예시를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-128">This is not an actual screenshot, but an illustration of how the secret underworld from the [MR Basics 101](holograms-101.md) looks on HoloLens.</span></span> <span data-ttu-id="8ed31-129">검은색 인클로저는 표시 되지 않지만 가상 구멍을 통해 콘텐츠를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-129">The black enclosure doesn’t show up, but you can see content through a virtual hole.</span></span> <span data-ttu-id="8ed31-130">(실제 장치를 살펴볼 때 눈이 없는 것 처럼 더 많은 거리에 집중 하는 것 처럼 보일 수도 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="8ed31-130">(When looking through an actual device, the floor would seem to disappear even more because your eyes focus at a further distance as if it’s not even there.)</span></span>

### <a name="world-locking-holographic-content"></a><span data-ttu-id="8ed31-131">세계 holographic 콘텐츠 잠금</span><span class="sxs-lookup"><span data-stu-id="8ed31-131">World-locking holographic content</span></span>

<span data-ttu-id="8ed31-132">Unity에서 holographic 콘텐츠가 세계에서 잠긴 상태로 유지 되도록 하는 것은 WorldAnchor 구성 요소를 추가 하는 것 만큼 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-132">In Unity, causing holographic content to stay world-locked is as easy as adding a WorldAnchor component:</span></span>

```
myObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="8ed31-133">WorldAnchor 구성 요소는 해당 GameObject의 위치와 회전을 지속적으로 조정 하 여 주변 물리적 개체에 상대적으로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-133">The WorldAnchor component will constantly adjust the position and rotation of its GameObject (and thus anything else under that object in the hierarchy) to keep it stable relative to nearby physical objects.</span></span> <span data-ttu-id="8ed31-134">콘텐츠를 제작할 때 개체의 루트 피벗이이 가상 구멍 가운데에 오도록 하 여 해당 콘텐츠를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-134">When authoring your content, create it in such a way that the root pivot of your object is centered at this virtual hole.</span></span> <span data-ttu-id="8ed31-135">(개체의 피벗이 벽에 있는 경우에는 위치 및 회전이 약간 조정 되는 것이 훨씬 더 눈에 띄지 않으며 구멍이 안정적이 지 않은 것 처럼 보일 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="8ed31-135">(If your object's pivot is deep in the wall, its slight tweaks in position and rotation will be much more noticeable, and the hole may not look very stable.)</span></span>

### <a name="occluding-everything-but-the-virtual-hole"></a><span data-ttu-id="8ed31-136">가상 구멍이 아닌 모든 항목 Occluding</span><span class="sxs-lookup"><span data-stu-id="8ed31-136">Occluding everything but the virtual hole</span></span>

<span data-ttu-id="8ed31-137">벽에서 숨겨진 항목에 대 한 보기를 선택적으로 차단 하는 다양 한 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-137">There are a variety of ways to selectively block the view to what is hidden in your walls.</span></span> <span data-ttu-id="8ed31-138">가장 간단한 방법은 HoloLens가 추가 표시를 사용 한다는 사실을 활용 하는 것입니다. 즉, 완전히 검정색 개체가 보이지 않는 것으로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-138">The simplest one takes advantage of the fact that HoloLens uses an additive display, which means that fully black objects appear invisible.</span></span> <span data-ttu-id="8ed31-139">특별 한 셰이더 나 재질을 사용 하지 않고 Unity에서이 작업을 수행할 수 있습니다. 검정 재질을 만들어 콘텐츠의 상자를 지정 하는 개체에 할당 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-139">You can do this in Unity without doing any special shader or material tricks— just create a black material and assign it to an object that boxes in your content.</span></span> <span data-ttu-id="8ed31-140">3D 모델링을 수행 하는 것이 마음에 들지 않으면 몇 개의 기본 쿼드 개체를 사용 하 고 약간 겹치게 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-140">If you don't feel like doing 3D modeling, just use a handful of default Quad objects and overlap them slightly.</span></span> <span data-ttu-id="8ed31-141">이 접근 방식에는 몇 가지 단점이 있지만, 작업을 수행 하는 가장 빠른 방법은 나중에 리팩터링할 수 있는 것으로 의심 되는 경우에도 중요 한 개념 증명을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-141">There are a number of drawbacks to this approach, but it is the fastest way to get something working, and getting a low-fidelity proof of concept working is great, even if you suspect you might want to refactor it later.</span></span>

<span data-ttu-id="8ed31-142">위의 "검은색 상자" 접근 방법의 주요 단점 중 하나는 사진이 제대로 작동 하지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-142">One major drawback to the above "black box" approach is that it doesn't photograph well.</span></span> <span data-ttu-id="8ed31-143">HoloLens 표시를 통해 효과가 완벽 하 게 보일 수 있지만, 사용 하는 모든 스크린샷은 벽 또는 층이 아니라 긴 검은색 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-143">While your effect might look perfect through the display of HoloLens, any screenshots you take will show a large black object instead of what remains of your wall or floor.</span></span> <span data-ttu-id="8ed31-144">그 이유는 물리적 하드웨어와 스크린샷 복합 holograms 및 현실가 다르게 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-144">The reason for this is that the physical hardware and screenshots composite holograms and reality differently.</span></span> <span data-ttu-id="8ed31-145">약간의 가짜를 잠시 우회.</span><span class="sxs-lookup"><span data-stu-id="8ed31-145">Let's detour for a moment into some fake math...</span></span>

<span data-ttu-id="8ed31-146">*가짜 수학 경고! 이러한 숫자와 수식은 정확한 메트릭이 아닌 점을 보여 주기 위해 작성 되었습니다.*</span><span class="sxs-lookup"><span data-stu-id="8ed31-146">*Fake math alert! These numbers and formulas are meant to illustrate a point, not to be any sort of accurate metric!*</span></span>

<span data-ttu-id="8ed31-147">HoloLens를 통해 표시 되는 내용:</span><span class="sxs-lookup"><span data-stu-id="8ed31-147">What you see through HoloLens:</span></span>

```
( Reality * darkening_amount ) + Holograms
```

<span data-ttu-id="8ed31-148">스크린샷 및 비디오에 표시 되는 내용:</span><span class="sxs-lookup"><span data-stu-id="8ed31-148">What you see in screenshots and video:</span></span>

```
( Reality * ( 1 - hologram_alpha ) ) + Holograms * hologram_alpha
```

<span data-ttu-id="8ed31-149">영어: HoloLens를 통해 표시 되는 항목은 어두운 현실 (예: 선글라스) 및 앱이 표시 하고자 하는 모든 holograms의 간단한 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-149">In English: What you see through HoloLens is a simple combination of darkened reality (like through sunglasses) and whatever holograms the app wants to show.</span></span> <span data-ttu-id="8ed31-150">하지만 스크린샷을 만들 때 카메라 이미지는 픽셀 별 투명도 값에 따라 앱의 holograms 혼합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-150">But when you take a screenshot, the camera's image is blended with the app's holograms according to the per-pixel transparency value.</span></span>

<span data-ttu-id="8ed31-151">이 문제를 해결 하는 한 가지 방법은 "검은색 상자" 자료를 깊이 버퍼에만 쓰도록 변경 하 고 다른 모든 불투명 자료를 정렬 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-151">One way to get around this is to change the "black box" material to only write to the depth buffer, and sort with all the other opaque materials.</span></span> <span data-ttu-id="8ed31-152">이에 대 한 예제를 보려면 GitHub의 [MixedRealityToolkit에서 WindowOcclusion 파일](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader)을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="8ed31-152">For an example of this, check out the [WindowOcclusion.shader file in the MixedRealityToolkit on GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Common/Shaders/WindowOcclusion.shader).</span></span> <span data-ttu-id="8ed31-153">관련 줄이 여기에 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-153">The relevant lines are copied here:</span></span>

```
"RenderType" = "Opaque"
"Queue" = "Geometry"
ColorMask 0
```

<span data-ttu-id="8ed31-154">("오프셋 50, 100" 줄은 관련 되지 않은 문제를 처리 하는 것 이므로이를 그대로 유지 하는 것이 좋습니다.)</span><span class="sxs-lookup"><span data-stu-id="8ed31-154">(Note the "Offset 50, 100" line is to deal with unrelated issues, so it'd probably make sense to leave that out.)</span></span>

<span data-ttu-id="8ed31-155">표시 되는 것과 같은 보이지 않는 폐색 재질을 구현 하 여 앱이 디스플레이 및 혼합 현실 스크린샷에서 올바른 모양의 상자를 그릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-155">Implementing an invisible occlusion material like that will let your app draw a box that looks correct in the display and in mixed-reality screenshots.</span></span> <span data-ttu-id="8ed31-156">보너스 점수를 얻기 위해 더 작은 수의 보이지 않는 픽셀을 그리기 위해 더 많은 작업을 수행 하 여 해당 상자의 성능을 향상 시킬 수 있지만,이는 일반적으로 weeds에 포함 될 수 있으며 일반적으로 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-156">For bonus points, you can try to improve the performance of that box even further by doing clever things to draw even fewer invisible pixels, but that can really get into the weeds and usually won't be necessary.</span></span>

![다음은 occluding 상자의 외부 파트를 제외 하 고 Unity가 그릴 때 MR 기본 101의 비밀 지 수입니다.](images/underworld-occluded-640px.png)

<span data-ttu-id="8ed31-159">다음은 occluding 상자의 외부 파트를 제외 하 고 Unity가 그릴 때 [MR 기본 101](holograms-101.md) 의 비밀 지 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-159">Here is the secret underworld from [MR Basics 101](holograms-101.md) as Unity draws it, except for the outer parts of the occluding box.</span></span> <span data-ttu-id="8ed31-160">지 수에 대 한 피벗은 상자 중심에 있으므로 실제 바닥을 기준으로 가능한 한 안정적으로 구멍을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-160">Note that the pivot for the underworld is at the center of the box, which helps keep the hole as stable as possible relative to your actual floor.</span></span>

## <a name="do-it-yourself"></a><span data-ttu-id="8ed31-161">직접</span><span class="sxs-lookup"><span data-stu-id="8ed31-161">Do it yourself</span></span>

<span data-ttu-id="8ed31-162">HoloLens가 있고 그에 대 한 효과를 시험해 보 시겠습니까?</span><span class="sxs-lookup"><span data-stu-id="8ed31-162">Have a HoloLens and want to try out the effect for yourself?</span></span> <span data-ttu-id="8ed31-163">가장 쉬운 작업 (코딩 필요 없음)은 무료 3D 뷰어 앱을 설치한 다음, [GitHub에 제공 된 fbx 파일 다운로드](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) 를 로드 하 여 대화방에서 꽃 .pot 모델을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-163">The easiest thing you can do (no coding required) is to install the free 3D Viewer app and then load the [download the.fbx file I've provided on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/CaseStudy-MagicWindow/MagicWindow) to view a flower pot model in your room.</span></span> <span data-ttu-id="8ed31-164">HoloLens에 로드 하 고 작업에 대 한 환상 효과를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-164">Load it on HoloLens, and you can see the illusion at work.</span></span> <span data-ttu-id="8ed31-165">모델 앞에 있는 경우 작은 구멍만 볼 수 있으며, 다른 모든 항목은 보이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-165">When you're in front of the model, you can only see into the small hole—everything else is invisible.</span></span> <span data-ttu-id="8ed31-166">다른 쪽에서 모델을 살펴보면 완전히 사라집니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-166">Look at the model from any other side and it disappears entirely.</span></span> <span data-ttu-id="8ed31-167">3D 뷰어의 이동, 회전 및 크기 조정 컨트롤을 사용 하 여 몇 가지 아이디어를 생성 하는 것으로 간주할 수 있는 수직 표면의 가상 구멍을 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-167">Use the movement, rotation, and scale controls of 3D Viewer to position the virtual hole against any vertical surface you can think of to generate some ideas!</span></span>

![Unity 편집기에서이 모델을 보면 flowerpot 주위에 긴 검은색 상자가 표시 됩니다.](images/magicwindowflowerpotineditor.png)

<span data-ttu-id="8ed31-170">Unity 편집기에서이 모델을 보면 flowerpot 주위에 긴 검은색 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-170">Viewing this model in your Unity editor will show a large black box around the flowerpot.</span></span> <span data-ttu-id="8ed31-171">HoloLens에서 상자가 사라지고 매직 창 효과를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-171">On HoloLens, the box disappears, giving way to a magic window effect.</span></span>

<span data-ttu-id="8ed31-172">이 기법을 사용 하는 앱을 빌드 하려는 경우 [Mixed Reality 자습서](tutorials.md)의 [MR 기본 사항 101 자습서](holograms-101.md) 를 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="8ed31-172">If you want to build an app that uses this technique, check out the [MR Basics 101 tutorial](holograms-101.md) in the [Mixed Reality tutorials](tutorials.md).</span></span> <span data-ttu-id="8ed31-173">7 장은 위에서 설명한 대로 숨겨진 지 각 지를 보여 주는 폭발으로 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-173">Chapter 7 ends with an explosion in your floor that reveals a hidden underworld (as pictured above).</span></span> <span data-ttu-id="8ed31-174">자습서는 지루한 일이 있나요?</span><span class="sxs-lookup"><span data-stu-id="8ed31-174">Who said tutorials had to be boring?</span></span>

<span data-ttu-id="8ed31-175">다음은이 아이디어를 수행할 수 있는 몇 가지 아이디어입니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-175">Here are some ideas of where you can take this idea next:</span></span>
* <span data-ttu-id="8ed31-176">가상 구멍 내에서 콘텐츠를 대화형으로 만드는 방법을 생각해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-176">Think of ways to make the content inside the virtual hole interactive.</span></span> <span data-ttu-id="8ed31-177">사용자가 자신의 벽을 넘어 약간의 영향을 줄 수 있도록 하면이 트릭에서 제공할 수 있는 불가사의의 의미를 크게 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-177">Letting your users have some impact beyond their walls can really improve the sense of wonder that this trick can provide.</span></span>
* <span data-ttu-id="8ed31-178">개체를 통해 알려진 영역으로 다시 확인 하는 방법을 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ed31-178">Think of ways to see through objects back to known areas.</span></span> <span data-ttu-id="8ed31-179">예를 들어 커피 테이블에 holographic를 추가 하 고 그 아래에 있는 바닥을 확인 하려면 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="8ed31-179">For example, how can you put a holographic hole in your coffee table and see your floor beneath it?</span></span>

## <a name="about-the-author"></a><span data-ttu-id="8ed31-180">작성자 정보</span><span class="sxs-lookup"><span data-stu-id="8ed31-180">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Eric Rehmeyer" width="60" height="60" src="images/genericusertile.jpg"></td>
<td style="border-style: none"><span data-ttu-id="8ed31-181"><b>Eric Rehmeyer</b></span><span class="sxs-lookup"><span data-stu-id="8ed31-181"><b>Eric Rehmeyer</b></span></span><br><span data-ttu-id="8ed31-182">수석 소프트웨어 엔지니어@Microsoft</span><span class="sxs-lookup"><span data-stu-id="8ed31-182">Senior Software Engineer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="8ed31-183">참조</span><span class="sxs-lookup"><span data-stu-id="8ed31-183">See also</span></span>
* [<span data-ttu-id="8ed31-184">MR 기본 101: 디바이스를 사용하는 완전한 프로젝트</span><span class="sxs-lookup"><span data-stu-id="8ed31-184">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="8ed31-185">좌표계</span><span class="sxs-lookup"><span data-stu-id="8ed31-185">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="8ed31-186">공간 앵커</span><span class="sxs-lookup"><span data-stu-id="8ed31-186">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="8ed31-187">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="8ed31-187">Spatial mapping</span></span>](spatial-mapping.md)
