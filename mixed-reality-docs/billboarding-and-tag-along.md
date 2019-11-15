---
title: Billboarding 및 태그 동반
description: Billboarding를 사용 하는 개체는 항상 사용자를 대상으로 합니다.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, billboarding, 태그 동반
ms.openlocfilehash: 06cd1c6f67f8aa2dd94173d4089adbdbd0765211
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105719"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="2efe1-104">Billboarding 및 태그 동반</span><span class="sxs-lookup"><span data-stu-id="2efe1-104">Billboarding and tag-along</span></span>

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="2efe1-105">Billboarding 란?</span><span class="sxs-lookup"><span data-stu-id="2efe1-105">What is billboarding?</span></span>

<span data-ttu-id="2efe1-106">Billboarding는 혼합 현실에서 개체에 적용할 수 있는 동작 개념입니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="2efe1-107">Billboarding를 사용 하는 개체는 항상 사용자를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="2efe1-108">이는 사용자의 환경에 배치 된 정적 개체 (세계에서 잠김)를 이동 해야 하는 경우에는 사용자의 환경에 배치 된 정적 개체를 숨기 거 나 읽을 수 없게 하는 텍스트 및 menuing 시스템에 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-108">This is especially helpful with text and menuing systems where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable if a user were to move around.</span></span>

<span data-ttu-id="2efe1-109">Billboarding를 사용 하는 개체는 사용자 환경에서 자유롭게 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="2efe1-110">디자인 고려 사항에 따라 단일 축으로 제한 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="2efe1-111">Billboarded 개체는 다른 개체에 너무 가까이 배치 되거나 HoloLens에 스캔 된 표면이 너무 가까이 배치 된 경우에는 클리핑 또는 려 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-111">Keep in mind, billboarded objects may clip or occlude themselves if they are placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="2efe1-112">이를 방지 하려면 billboarding에 대해 사용 하도록 설정 된 축에서 회전할 때 개체가 생성할 수 있는 총 공간을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="2efe1-113">태그의 정의</span><span class="sxs-lookup"><span data-stu-id="2efe1-113">What is a tag-along?</span></span>

<span data-ttu-id="2efe1-114">태그 동반은 holograms에 추가할 수 있는 동작 개념입니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="2efe1-115">태그 동반 개체는 사용자가 편안 하 게 상호 작용할 수 있도록 범위를 유지 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="2efe1-116">HoloLens 핀 패널 ![태그 동반 동작의 좋은 예](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="2efe1-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="2efe1-117">*HoloLens 시작 메뉴는 태그 동반 동작의 좋은 예입니다.*</span><span class="sxs-lookup"><span data-stu-id="2efe1-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="2efe1-118">태그를 포함 하는 개체에는 동작 방식을 세밀 하 게 조정할 수 있는 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-118">Tag-along objects have parameters which can fine-tune the way they behave.</span></span> <span data-ttu-id="2efe1-119">사용자가 환경 주위에서 이동할 때 원하는 대로 사용자의 시야에 콘텐츠를 배치 하거나 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-119">Content can be in or out of the user’s line of sight as desired while the user moves around their environment.</span></span> <span data-ttu-id="2efe1-120">사용자가 이동 하면 콘텐츠는 사용자가 이동 하는 속도에 따라 사용자의 주변 내에 유지 됩니다. 사용자가 이동 하면 콘텐츠가 일시적으로 표시 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-120">As the user moves, the content will attempt to stay within the user’s periphery by sliding towards the edge of the view, depending on how quickly a user moves may leave the content temporarily out of view.</span></span> <span data-ttu-id="2efe1-121">사용자가 태그를 따라 개체를 gazes 하는 경우에는 더 자세히 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-121">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="2efe1-122">콘텐츠를 항상 "한 눈에 파악" 하는 것은 사용자에 게 콘텐츠가 있는 방향을 잊지 않도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-122">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="2efe1-123">추가 매개 변수를 사용 하면 사용자의 헤드에 대 한 태그 동반 개체 느낌을 고무 띠로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-123">Additional parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="2efe1-124">완충 가속 또는 감속은 개체에 대 한 가중치를 제공 하 여 더 물리적으로 표시 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-124">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="2efe1-125">이 스프링 동작은 사용자가 태그를 사용 하는 방법에 대 한 정확한 멘 탈 모델을 빌드하는 데 도움이 되는 affordance입니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-125">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="2efe1-126">오디오는 사용자가 태그 동반 모드에서 개체를 사용할 때 추가 affordances을 제공 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-126">Audio helps provide additional affordances for when users have objects in tag-along mode.</span></span> <span data-ttu-id="2efe1-127">오디오는 이동 속도를 보강 해야 합니다. 고속 헤드 턴은 모든 효과가 있는 경우 자연 속도로 이동 하는 것이 최소 오디오를 포함 하는 동안 보다 눈에 띄는 음향 효과를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-127">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect while walking at a natural speed should have minimal audio if any effects at all.</span></span>

<span data-ttu-id="2efe1-128">진정한 헤드 잠금 콘텐츠와 마찬가지로 태그를 사용 하는 개체는 사용자의 뷰에서 무분별 또는 스프링을 너무 많이 이동 하는 경우 과도 하 게 또는 nauseating을 입증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-128">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="2efe1-129">사용자가이를 확인 하 고 신속 하 게 중지 하면 해당 사용자가 중지 된 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-129">As a user looks around and then quickly stop, their senses tell them they have stopped.</span></span> <span data-ttu-id="2efe1-130">이러한 잔액은 세계를 중지 하는 것을 알 수 있는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-130">Their balance informs them that their head has stopped turning as well as their vision sees the world stop turning.</span></span> <span data-ttu-id="2efe1-131">그러나 사용자가 중지 되었을 때 태그를 따라 이동 하는 경우에는 해당 사용자의 감지를 혼동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-131">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="2efe1-132">Billboarding 및 태그-Unity 용 MRTK (혼합 현실 도구 키트)</span><span class="sxs-lookup"><span data-stu-id="2efe1-132">Billboarding and Tag-along in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="2efe1-133">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 Billboarding 및 태그 동반 동작에 대 한 스크립트를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-133">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and Tag-along behavior.</span></span> <span data-ttu-id="2efe1-134">Billboard.cs 스크립트를 모든 개체에 할당 하 여 billboarding 동작을 추가 하 고 개체를 항상 사용자에 게 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-134">Simply assign Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="2efe1-135">태그 동반 동작을 추가 하려면 RadialView.cs 스크립트를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-135">To add tag-along behavior, use RadialView.cs script.</span></span> <span data-ttu-id="2efe1-136">Lerping 시간, 거리, 학위 등의 다양 한 옵션을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2efe1-136">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="2efe1-137">MRTK-방사형 보기 해 찾기</span><span class="sxs-lookup"><span data-stu-id="2efe1-137">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="2efe1-138">MRTK-빌보드 스크립트</span><span class="sxs-lookup"><span data-stu-id="2efe1-138">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="2efe1-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2efe1-139">See also</span></span>

* [<span data-ttu-id="2efe1-140">커서</span><span class="sxs-lookup"><span data-stu-id="2efe1-140">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="2efe1-141">손 모양</span><span class="sxs-lookup"><span data-stu-id="2efe1-141">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="2efe1-142">Button</span><span class="sxs-lookup"><span data-stu-id="2efe1-142">Button</span></span>](button.md)
* [<span data-ttu-id="2efe1-143">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="2efe1-143">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="2efe1-144">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="2efe1-144">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="2efe1-145">조작은</span><span class="sxs-lookup"><span data-stu-id="2efe1-145">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="2efe1-146">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="2efe1-146">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="2efe1-147">메뉴 근처</span><span class="sxs-lookup"><span data-stu-id="2efe1-147">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="2efe1-148">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="2efe1-148">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="2efe1-149">음성 명령</span><span class="sxs-lookup"><span data-stu-id="2efe1-149">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="2efe1-150">키보드</span><span class="sxs-lookup"><span data-stu-id="2efe1-150">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="2efe1-151">놓으면</span><span class="sxs-lookup"><span data-stu-id="2efe1-151">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="2efe1-152">찬</span><span class="sxs-lookup"><span data-stu-id="2efe1-152">Slate</span></span>](slate.md)
* [<span data-ttu-id="2efe1-153">슬라이더</span><span class="sxs-lookup"><span data-stu-id="2efe1-153">Slider</span></span>](slider.md)
* [<span data-ttu-id="2efe1-154">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="2efe1-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="2efe1-155">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="2efe1-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="2efe1-156">표면 자기</span><span class="sxs-lookup"><span data-stu-id="2efe1-156">Surface magnetism</span></span>](surface-magnetism.md)
