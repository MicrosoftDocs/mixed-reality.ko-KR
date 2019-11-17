---
title: 경계 상자 및 앱 바
description: 앱 바는 홀로그램 범위의 아래쪽 가장자리에 표시 되는 일련의 단추를 포함 하는 개체 수준 메뉴입니다.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, 앱 바, 경계 상자
ms.openlocfilehash: e4f519cba459efac25f6c1370b07fcda4def30a1
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143167"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="6a781-104">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="6a781-104">Bounding box and App bar</span></span>
<span data-ttu-id="6a781-105">![경계는 혼합 현실에서 개체 조작을 위한 표준 인터페이스입니다.](images/UX/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="6a781-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="6a781-106">경계 상자는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="6a781-106">What is the Bounding box?</span></span>

<span data-ttu-id="6a781-107">경계는 혼합 현실에서 개체 조작을 위한 표준 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="6a781-108">사용자에 게 개체를 현재 조정할 수 있는 affordance 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="6a781-109">HoloLens 2에서 경계 상자는 직접 조작을 사용 하 여 작동 하며 사용자의 finger's 근접에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="6a781-110">사용자가 개체의 거리를 파악 하는 데 도움이 되는 시각적 피드백을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="6a781-111">개체 크기 조정</span><span class="sxs-lookup"><span data-stu-id="6a781-111">Scaling an object</span></span><br>
        <span data-ttu-id="6a781-112">경계 상자의 모퉁이는 개체의 크기를 조정할 수 있음을 사용자에 게 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="6a781-113">핸들은 크기 조정을 조정 하기 위해 널리 이해 되는 패턴을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="6a781-114">이 시각적 개체는 조정 모드 외부에 표시 되지 않는 경우에도 사용자에 게 개체의 전체 영역을 affordance 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-114">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="6a781-115">이는 해당 개체가 없는 경우 다른 개체 또는 표면에 맞춰진 개체가 거기에 있어서는 안 되는 것 처럼 동작 하는 것 처럼 보일 수 있으므로 특히 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-115">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="6a781-116">*비디오 루프: 경계 상자를 통해 개체 크기 조정*</span><span class="sxs-lookup"><span data-stu-id="6a781-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="6a781-117">![공간](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="6a781-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="6a781-118">경계 상자를 통해 개체 크기를 조정 하는 ![HoloLens 관점](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="6a781-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="6a781-119">개체 회전</span><span class="sxs-lookup"><span data-stu-id="6a781-119">Rotating an object</span></span><br>
        <span data-ttu-id="6a781-120">경계 상자 가장자리의 세로 사각형 affordances 회전 표시기입니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="6a781-121">이렇게 하면 사용자가 배치 된 holograms을 보다 세부적으로 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="6a781-122">조정 하 고 크기를 조정할 수 있을 뿐만 아니라 이제 회전도 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="6a781-123">*비디오 루프: 경계 상자를 통해 개체 회전*</span><span class="sxs-lookup"><span data-stu-id="6a781-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="6a781-124">![공간](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="6a781-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="6a781-125">경계 상자를 통해 개체를 회전 하는 ![HoloLens 관점](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="6a781-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="6a781-126">HoloLens에서 근접 한 시각적 피드백 2</span><span class="sxs-lookup"><span data-stu-id="6a781-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="6a781-127">HoloLens 2에는 사용자가 깊이를 인식 하는 데 도움이 될 수 있는 추가 시각적 표시가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-127">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="6a781-128">Fingertip 근처의 링은 개체에 가까울수록 fingertip가 위쪽으로 표시 되 고 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="6a781-129">누름 상태에 도달 하면 링이 결국 점으로 수렴.</span><span class="sxs-lookup"><span data-stu-id="6a781-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="6a781-130">이 시각적 affordance는 사용자가 개체에서 얼마나 떨어져 있는지 이해 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="6a781-131">*비디오 루프: 경계 상자에 근접 한 시각적 피드백의 예*</span><span class="sxs-lookup"><span data-stu-id="6a781-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="6a781-132">![공간](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="6a781-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="6a781-133">직접 근접 한 시각적 피드백을 ![](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="6a781-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="6a781-134">**Unity 앱 개발의 경우 [혼합 현실 도구 키트-Unity에서 경계 상자](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 를 참조 하세요.**</span><span class="sxs-lookup"><span data-stu-id="6a781-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="6a781-135">앱 바 란?</span><span class="sxs-lookup"><span data-stu-id="6a781-135">What is the App bar?</span></span>

<span data-ttu-id="6a781-136">앱 바는 홀로그램 범위의 아래쪽 가장자리에 표시 되는 일련의 단추를 포함 하는 개체 수준 메뉴입니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-136">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="6a781-137">이 패턴은 사용자에 게 holograms를 제거 하 고 조정 하는 기능을 제공 하는 데 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-137">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span> <span data-ttu-id="6a781-138">앱 바는 주로 사용자 환경에서 배치 된 개체를 관리 하는 방법으로 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="6a781-139">경계 상자와 함께 사용 하는 경우 사용자는 혼합 현실에서 개체의 방향 및 위치를 완전히 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="6a781-140">앱 바는 사용자를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="6a781-141">이 패턴은 세계에서 잠긴 개체와 함께 사용 되므로 사용자가 개체를 이동할 때 앱 바는 항상 사용자에 게 가장 가까운 개체 쪽에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="6a781-142">이는 billboarding 되지 않지만 실제로 동일한 결과를 얻는 것입니다. 사용자의 위치를 려 하거나 환경의 다른 위치에서 사용할 수 있는 기능을 차단 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-142">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="6a781-143">*비디오 루프: 홀로그램 둘러보기, 앱 바는 다음과 같습니다.*</span><span class="sxs-lookup"><span data-stu-id="6a781-143">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="6a781-144">![공간](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="6a781-144">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="6a781-145">홀로그램을 탐색 하는 ![.</span><span class="sxs-lookup"><span data-stu-id="6a781-145">![Walking around a hologram.</span></span> <span data-ttu-id="6a781-146">앱 바는 다음과 같습니다.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="6a781-146">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="6a781-147">Unity 용 MRTK (Mixed Reality Toolkit)의 경계 상자</span><span class="sxs-lookup"><span data-stu-id="6a781-147">Bounding box in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="6a781-148">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 경계 상자와 앱 바에 대 한 스크립트 및 prefabs을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-148">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="6a781-149">BoundingBox.cs 스크립트를 개체에 할당 하기만 하면 경계 상자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6a781-149">You can add a Bounding box by simply assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="6a781-150">MRTK-경계 상자</span><span class="sxs-lookup"><span data-stu-id="6a781-150">MRTK - Bounding Box</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="6a781-151">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6a781-151">See also</span></span>

* [<span data-ttu-id="6a781-152">커서</span><span class="sxs-lookup"><span data-stu-id="6a781-152">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="6a781-153">손 광선</span><span class="sxs-lookup"><span data-stu-id="6a781-153">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="6a781-154">Button</span><span class="sxs-lookup"><span data-stu-id="6a781-154">Button</span></span>](button.md)
* [<span data-ttu-id="6a781-155">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="6a781-155">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="6a781-156">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="6a781-156">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="6a781-157">조작</span><span class="sxs-lookup"><span data-stu-id="6a781-157">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6a781-158">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="6a781-158">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="6a781-159">Near 메뉴</span><span class="sxs-lookup"><span data-stu-id="6a781-159">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="6a781-160">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="6a781-160">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="6a781-161">음성 명령</span><span class="sxs-lookup"><span data-stu-id="6a781-161">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="6a781-162">키보드</span><span class="sxs-lookup"><span data-stu-id="6a781-162">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="6a781-163">Tooltip</span><span class="sxs-lookup"><span data-stu-id="6a781-163">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="6a781-164">슬레이트</span><span class="sxs-lookup"><span data-stu-id="6a781-164">Slate</span></span>](slate.md)
* [<span data-ttu-id="6a781-165">슬라이더</span><span class="sxs-lookup"><span data-stu-id="6a781-165">Slider</span></span>](slider.md)
* [<span data-ttu-id="6a781-166">셰이더가</span><span class="sxs-lookup"><span data-stu-id="6a781-166">Shader</span></span>](shader.md)
* [<span data-ttu-id="6a781-167">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="6a781-167">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="6a781-168">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="6a781-168">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="6a781-169">표면 자성</span><span class="sxs-lookup"><span data-stu-id="6a781-169">Surface magnetism</span></span>](surface-magnetism.md)
