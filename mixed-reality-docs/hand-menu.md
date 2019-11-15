---
title: 손 모양 메뉴
description: 사용자는 직접 메뉴를 사용 하 여 자주 사용 하는 함수에 대 한 직접 연결 된 UI를 빠르게 가져올 수 있습니다. 다음은 직접 메뉴에 대 한 모범 사례 및 권장 사항입니다.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 손, 메뉴, 단추, 빠른 액세스, 레이아웃
ms.openlocfilehash: b4ea7411be22633e82a88d1c91b6b2b1edbea735
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105636"
---
# <a name="hand-menu"></a><span data-ttu-id="d7cb4-105">손 모양 메뉴</span><span class="sxs-lookup"><span data-stu-id="d7cb4-105">Hand menu</span></span>

![Ulnar 사이드 위치](images/UX/UX_Hero_HandMenu.jpg)

<span data-ttu-id="d7cb4-107">사용자는 직접 메뉴를 사용 하 여 자주 사용 하는 함수에 대 한 직접 연결 된 UI를 빠르게 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-107">Hand menus allow users to quickly bring up hand-attached UI for frequently used functions.</span></span> 

<span data-ttu-id="d7cb4-108">다음은 직접 메뉴에 대해 찾은 모범 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-108">Below are the best practices we have found for hand menus.</span></span> <span data-ttu-id="d7cb4-109">[Mrtk](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)의 손 메뉴를 보여 주는 예제 장면을 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-109">You can also find an example scene demonstrating the hand menu in [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).</span></span>

<br>

---

## <a name="behavior-best-practices"></a><span data-ttu-id="d7cb4-110">동작 모범 사례</span><span class="sxs-lookup"><span data-stu-id="d7cb4-110">Behavior best practices</span></span>
<span data-ttu-id="d7cb4-111">**A. 단추 수를 작게 유지 합니다.** 즉, 손 잠금 메뉴와 눈동자 간의 거리가 가까이 있고, 언제 든 지 상대적으로 작은 시각적 영역에 초점을 맞춘 사용자의 추세 (비전의 attentional 원뿔 약 10도)를 사용 하는 것이 좋습니다. 단추 수를 작게 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-111">**A. Keep the number of buttons small:** Due to the close distance between a hand-locked menu and the eyes and also the user's tendency to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="d7cb4-112">탐색을 기반으로 3 개의 단추가 있는 한 열은 사용자가 시계 중심으로 이동 하는 경우에도 뷰 (FOV)의 모든 콘텐츠를 유지 하 여 잘 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-112">Based on our exploration, one column with three buttons work well by keeping all the content within the field of view (FOV) even when users move their hands to the center of the FOV.</span></span> 

<span data-ttu-id="d7cb4-113">**B. 빠른 작업을 위한 수동 메뉴 활용:** arm을 올리고 위치를 유지 관리 하면 arm 피로을 쉽게 유발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-113">**B. Utilize hand menu for quick action:** Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="d7cb4-114">짧은 상호 작용을 필요로 하는 메뉴에 대해 직접 잠긴 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-114">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="d7cb4-115">메뉴가 복잡 하 고 확장 된 상호 작용 시간이 필요한 경우에는 대신 세계 잠금 또는 본문 잠금을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-115">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="d7cb4-116">**C. 단추/패널 각도:** 메뉴는 head의 반대 어깨와 중간 방향으로 빌보드를 수행 합니다 .이를 통해 자연 스런 이동이 반대 바늘을 사용 하 여 메뉴와 상호 작용 하 고, 터치 시 매우 불쾌 하거나 불편할 수 있습니다. 단추.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-116">**C. Button / Panel angle:** Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="d7cb4-117">**D. 단방향 또는 실습 작업 지원 고려:** 사용자의 손을 항상 사용할 수 있다고 가정 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-117">**D. Consider supporting one-handed or hands-free operation:** Do not assume both of the user's hands are always available.</span></span> <span data-ttu-id="d7cb4-118">하나 또는 둘 다를 사용할 수 없는 경우 광범위 한 컨텍스트를 고려 하 고 해당 상황에 대 한 설계 계정이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-118">Consider a wide range of contexts when one or both hands are not available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="d7cb4-119">단방향 메뉴를 지원 하기 위해 손을 대칭 이동 하면 (팜 아래로 이동) 메뉴 배치를 왼쪽에서 잠김으로 전환 해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-119">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="d7cb4-120">직접 사용 하지 않는 시나리오의 경우 음성 명령을 사용 하 여 직접 메뉴 단추를 호출 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-120">For hands-free scenarios, consider using a voice command to invoke the hand menu buttons.</span></span>

<span data-ttu-id="d7cb4-121">**E. 2 단계 호출:** 손 메뉴를 트리거하는 이벤트로 palm을 사용 하는 경우 사용자가 의도적으로 둘 다 (통신 및 개체 조작을 위해)를 많이 이동 하기 때문에 필요 하지 않을 때 실수로 표시 될 수 있습니다 (가양성). 그리고 의도 하지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="d7cb4-121">**E. Two-step invocation:** If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands a lot both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="d7cb4-122">앱에서 가양성이 발생 하는 경우 팜 등록 이벤트 외에 추가 단계를 추가 하 여 완전히 열린 손가락 같은 손 메뉴를 호출 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-122">If you experience false-positives in your app, consider adding an additional step besides the palm-up event to invoke the hand menu such as fully opened fingers.</span></span>

<span data-ttu-id="d7cb4-123">**6. 손목 (시스템 홈 단추) 근처에 단추를 추가 하지 않습니다** . 손 메뉴 단추가 홈 단추에 너무 가까이 배치 된 경우에는 손 메뉴와 상호 작용 하는 동안 실수로 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-123">**F. Avoid adding buttons near the wrist (system home button):** If the hand menu buttons are placed too close to the home button, it may get accidentally triggered while interacting with the hand menu.</span></span>

<span data-ttu-id="d7cb4-124">**G. 테스트, 테스트, 테스트:** 사람들에 게 편안 하 고 discomfort 하는 다른 임계값과 함께 다른 본문이 있습니다. 디자인을 테스트 하 고 다양 한 사용자의 의견을 얻으세요.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-124">**G. Test, test, test:** People have different bodies, with different thresholds for comfort and discomfort, etc. Be sure to test out your design on and get feedback from a variety of people.</span></span>

<br>

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="d7cb4-125">손 메뉴 배치 모범 사례</span><span class="sxs-lookup"><span data-stu-id="d7cb4-125">Hand menu placement best practices</span></span>

<span data-ttu-id="d7cb4-126">인간 분석에서 ulnar nerve은 ulna 뼈 근처에서 실행 되는 nerve입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-126">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="d7cb4-127">Ulna는 엘보우에서 가장 작은 손가락으로 확장 되는 긴 뼈가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-127">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="d7cb4-128">다음은 탐색를 기반으로 하는 두 가지 권장 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-128">Below are 2 recommended placements based on our explorations:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="d7cb4-129">![Ulnar 측면 위치](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="d7cb4-129">![Ulnar side hand location](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="d7cb4-130">**야자수 내부에 있는 Ulnar**</span><span class="sxs-lookup"><span data-stu-id="d7cb4-130">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="d7cb4-131">이 위치는 서로 겹치지 않으므로 안정적입니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-131">This position is reliable because the hands do not overlap each other.</span></span> <span data-ttu-id="d7cb4-132">정확한 직접 검색 및 추적에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-132">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d7cb4-133">![Ulnar 측면 위치](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="d7cb4-133">![Ulnar side hand location](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="d7cb4-134">**2. 전 사랑 Nar**</span><span class="sxs-lookup"><span data-stu-id="d7cb4-134">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="d7cb4-135">이 위치는 손 메뉴와 상호 작용 하는 데 너무 많은 arm을 발생 시킬 필요가 없기 때문에 사용자에 게 친숙 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-135">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="d7cb4-136">**메뉴를** palm 위에 배치 하 고 ulnar 팜 내에서 단추를 정렬 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-136">We recommend placing menus **13cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="d7cb4-137">최적의 단추 크기에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-137">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="d7cb4-138">기술적인 이유로이 위치에는 하나의 필수 구현이 권장 됩니다. 개발자는 사용자의 반대 바늘이 가까이와 상호 작용할 때 메뉴를 고정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-138">For technical reasons we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="d7cb4-139">이렇게 하면 겹치는 jitteriness 방지 하 고 더 빠르게 단추를 대상으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-139">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="d7cb4-140">HoloLens 2 카메라는 서로 분리 된 경우를 정확 하 게 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-140">HoloLens 2 cameras identify hands accurately when they are separate from each other.</span></span> <span data-ttu-id="d7cb4-141">모든 겹치는 손을 통해 고정 위치에서 바로 메뉴가 이동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-141">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a><span data-ttu-id="d7cb4-142">권장 되지 않는 메뉴 위치</span><span class="sxs-lookup"><span data-stu-id="d7cb4-142">Menu positions that are not recommended</span></span>
<span data-ttu-id="d7cb4-143">다른 메뉴 레이아웃 및 위치를 사용 하 여 사용자 연구를 완료 했습니다. 다음 메뉴 위치를 사용 **하지 않는 것이 좋습니다**. 아래 각 연구의 단점을 찾으십시오.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-143">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>


:::row:::
    :::column:::
        <span data-ttu-id="d7cb4-144">arm](images/AboveArm.gif) ![</span><span class="sxs-lookup"><span data-stu-id="d7cb4-144">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="d7cb4-145">**Arm 위**</span><span class="sxs-lookup"><span data-stu-id="d7cb4-145">**Above the arm**</span></span><br>
        <span data-ttu-id="d7cb4-146">1-좋은 수동 추적을 유지 하기 어렵게 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-146">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="d7cb4-147">2-비 자연 위치로 인해 사용자 피로 발생</span><span class="sxs-lookup"><span data-stu-id="d7cb4-147">2 - Causes user fatigue due to unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d7cb4-148">손가락을 ![](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="d7cb4-148">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="d7cb4-149">**손가락 위**</span><span class="sxs-lookup"><span data-stu-id="d7cb4-149">**Above fingers**</span></span><br>
        <span data-ttu-id="d7cb4-150">피로 오랜 시간 동안 보유 하 고 있으므로 손을</span><span class="sxs-lookup"><span data-stu-id="d7cb4-150">1 - Hand fatigue due to holding hand for long time</span></span><br>
        <span data-ttu-id="d7cb4-151">2-인덱스 및 가운데 손가락에 대 한 추적 문제</span><span class="sxs-lookup"><span data-stu-id="d7cb4-151">2 - Hand tracking issues on index and middle finger</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="d7cb4-152">![센터 팜](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="d7cb4-152">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="d7cb4-153">**위쪽-가운데 palm**</span><span class="sxs-lookup"><span data-stu-id="d7cb4-153">**Above-center palm**</span></span><br>
        <span data-ttu-id="d7cb4-154">겹친 실습으로 인 한 1 손을 추적 하는 문제</span><span class="sxs-lookup"><span data-stu-id="d7cb4-154">1 - Hand tracking issues due to overlapping hands</span></span><br>
        <span data-ttu-id="d7cb4-155">피로 메뉴와 상호 작용 하는 데 오랜 시간이 소요 되기 때문에 2 손</span><span class="sxs-lookup"><span data-stu-id="d7cb4-155">2 - Hand fatigue due to holding hands for long time in order to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="d7cb4-156">![Top Fingertip](images/TopFingerTip.gif) **top Fingertip**</span><span class="sxs-lookup"><span data-stu-id="d7cb4-156">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="d7cb4-157">1 손을 추적 하는 문제</span><span class="sxs-lookup"><span data-stu-id="d7cb4-157">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="d7cb4-158">2\. 정상 상태를 유지 하는 손을 피로</span><span class="sxs-lookup"><span data-stu-id="d7cb4-158">2 - Hand fatigue holding hand above normal posture</span></span><br>
        <span data-ttu-id="d7cb4-159">3-손가락 사이의 제한 된 공간으로 인해 실수로 다른 손가락으로 단추를 누르는 문제</span><span class="sxs-lookup"><span data-stu-id="d7cb4-159">3 - Issues pressing buttons with other fingers by accident due to limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="d7cb4-160">Arm](images/BackOfTheArm.gif)의 ![돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-160">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="d7cb4-161">**Arm의 후면**</span><span class="sxs-lookup"><span data-stu-id="d7cb4-161">**Back of the arm**</span></span><br>
        <span data-ttu-id="d7cb4-162">1-실수로 홈 단추를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-162">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="d7cb4-163">2-사용자에 게 친숙 하거나 친숙 하지 않은 위치</span><span class="sxs-lookup"><span data-stu-id="d7cb4-163">2 - Not a natural or comfortable position for users</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="d7cb4-164">Unity 용 MRTK (Mixed Reality Toolkit)의 손 모양 메뉴</span><span class="sxs-lookup"><span data-stu-id="d7cb4-164">Hand menu in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="d7cb4-165">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 손 메뉴에 대 한 스크립트와 예제 장면을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-165">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="d7cb4-166">HandConstraintPalmUp 해 찾기 스크립트를 사용 하면 다양 한 구성 가능한 옵션을 사용 하 여 개체를 쉽게 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7cb4-166">HandConstraintPalmUp solver script allows you easily attach any objects to the hands with various configurable options.</span></span>

* [<span data-ttu-id="d7cb4-167">MRTK-수동 제약 조건 및 HandConstraintPalmUp를 사용 하는 메뉴</span><span class="sxs-lookup"><span data-stu-id="d7cb4-167">MRTK - Hand Menu with HandConstraint and HandConstraintPalmUp </span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


<br>

---


## <a name="see-also"></a><span data-ttu-id="d7cb4-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d7cb4-168">See also</span></span>

* [<span data-ttu-id="d7cb4-169">커서</span><span class="sxs-lookup"><span data-stu-id="d7cb4-169">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d7cb4-170">손 모양</span><span class="sxs-lookup"><span data-stu-id="d7cb4-170">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="d7cb4-171">Button</span><span class="sxs-lookup"><span data-stu-id="d7cb4-171">Button</span></span>](button.md)
* [<span data-ttu-id="d7cb4-172">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="d7cb4-172">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d7cb4-173">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="d7cb4-173">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d7cb4-174">조작은</span><span class="sxs-lookup"><span data-stu-id="d7cb4-174">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d7cb4-175">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="d7cb4-175">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="d7cb4-176">메뉴 근처</span><span class="sxs-lookup"><span data-stu-id="d7cb4-176">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="d7cb4-177">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="d7cb4-177">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d7cb4-178">음성 명령</span><span class="sxs-lookup"><span data-stu-id="d7cb4-178">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="d7cb4-179">키보드</span><span class="sxs-lookup"><span data-stu-id="d7cb4-179">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="d7cb4-180">놓으면</span><span class="sxs-lookup"><span data-stu-id="d7cb4-180">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="d7cb4-181">찬</span><span class="sxs-lookup"><span data-stu-id="d7cb4-181">Slate</span></span>](slate.md)
* [<span data-ttu-id="d7cb4-182">슬라이더</span><span class="sxs-lookup"><span data-stu-id="d7cb4-182">Slider</span></span>](slider.md)
* [<span data-ttu-id="d7cb4-183">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="d7cb4-183">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d7cb4-184">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="d7cb4-184">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="d7cb4-185">표면 자기</span><span class="sxs-lookup"><span data-stu-id="d7cb4-185">Surface magnetism</span></span>](surface-magnetism.md)