---
title: Interactable 개체
description: 단추는 긴 2D 추상 세계에서 이벤트를 트리거하는 데 사용 되는 비유입니다. 3 차원 혼합 현실 세계에서는 이러한 추상화의 목표로 더 이상 국한 되지 않습니다.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: 혼합 현실, 컨트롤, 상호 작용, ui, ux
ms.openlocfilehash: 5305af97e9811134212fc6c730727962bb9e8353
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105807"
---
# <a name="interactable-object"></a><span data-ttu-id="68f55-105">Interactable 개체</span><span class="sxs-lookup"><span data-stu-id="68f55-105">Interactable object</span></span>

![Interactible 개체](images/UX/UX_Hero_Interactable.jpg)

<span data-ttu-id="68f55-107">단추는 긴 2D 추상 세계에서 이벤트를 트리거하는 데 사용 되는 비유입니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="68f55-108">3 차원 혼합 현실 세계에서는 이러한 추상화의 목표로 더 이상 국한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="68f55-109">모든 항목은 이벤트를 트리거하는 **interactable 개체** 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="68f55-110">Interactable 개체는 테이블의 커피에서 공기의 풍선 부동으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="68f55-111">대화 상자 UI에서와 같은 특정 상황에서는 여전히 기존 단추를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="68f55-112">단추의 시각적 표시는 컨텍스트에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-112">The visual representation of the button depends on the context.</span></span>

<br>

---


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="68f55-113">Interactable 개체의 중요 한 속성</span><span class="sxs-lookup"><span data-stu-id="68f55-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="68f55-114">시각적 신호</span><span class="sxs-lookup"><span data-stu-id="68f55-114">Visual cues</span></span>

<span data-ttu-id="68f55-115">시각적 신호는 시각적 개체를 시각적으로 인식 하면서 시각적 시스템에서 처리 하 고 밝은 형태로 받은 토대로 된 큐입니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="68f55-116">시각적 시스템은 다양 한 정보, 특히 사람에 게 중요 한 것 이므로 시각적 신호는 전 세계의 정보에 대 한 많은 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="68f55-117">Holographic 개체는 혼합 현실에서 실제 환경과 혼합 되므로 상호 작용할 수 있는 개체를 이해 하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="68f55-118">사용자 환경에서 모든 interactable 개체의 경우 각 입력 상태에 대해 차별화 된 시각적 신호를 제공 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="68f55-119">이렇게 하면 사용자가 interactable 하는 환경 부분을 이해 하 고 일관 된 상호 작용 방법을 사용 하 여 사용자를 신뢰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="68f55-120">먼 상호 작용</span><span class="sxs-lookup"><span data-stu-id="68f55-120">Far interactions</span></span>

<span data-ttu-id="68f55-121">사용자가 응시, 손 모양 및 모션 컨트롤러의 광선과 상호 작용할 수 있는 개체의 경우 다음과 같은 세 가지 입력 상태에 대해 서로 다른 시각적 표시를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="68f55-122">![interactibleobject-기본](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="68f55-123">**기본 (관찰) 상태**</span><span class="sxs-lookup"><span data-stu-id="68f55-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="68f55-124">개체의 기본 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-124">Default idle state of the object.</span></span>
    <span data-ttu-id="68f55-125">커서가 개체에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-125">The cursor is not on the object.</span></span> <span data-ttu-id="68f55-126">손으로 검색 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-126">Hand is not detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="68f55-127">![interactibleobject-대상](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="68f55-128">**대상 (가리키기) 상태**</span><span class="sxs-lookup"><span data-stu-id="68f55-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="68f55-129">개체가 응시 커서, 손가락 근접 또는 동작 컨트롤러의 포인터를 대상으로 하는 경우</span><span class="sxs-lookup"><span data-stu-id="68f55-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="68f55-130">커서가 개체에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-130">The cursor is on the object.</span></span> <span data-ttu-id="68f55-131">준비가 완료 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="68f55-132">![interactibleobject-누름](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="68f55-133">**누름 상태**</span><span class="sxs-lookup"><span data-stu-id="68f55-133">**Pressed state**</span></span><br>
        <span data-ttu-id="68f55-134">공기 탭 제스처를 사용 하 여 개체를 누르면 손가락을 누르거나 동작 컨트롤러의 선택 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="68f55-135">커서가 개체에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-135">The cursor is on the object.</span></span> <span data-ttu-id="68f55-136">손으로 검색 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="68f55-137">강조 표시 또는 크기 조정과 같은 기술을 사용 하 여 사용자의 입력 상태를 시각적으로 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="68f55-138">혼합 현실에서는 시작 메뉴와 앱 바 단추를 사용 하 여 다양 한 입력 상태를 시각화 하는 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="68f55-139">**Holographic 단추**에서 이러한 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-139">Here is what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="68f55-140">![interactibleobject-기본](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="68f55-141">**기본 (관찰) 상태**</span><span class="sxs-lookup"><span data-stu-id="68f55-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="68f55-142">![interactibleobject-대상](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="68f55-143">**대상 (가리키기) 상태**</span><span class="sxs-lookup"><span data-stu-id="68f55-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="68f55-144">![interactibleobject-누름](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="68f55-145">**누름 상태**</span><span class="sxs-lookup"><span data-stu-id="68f55-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="68f55-146">거의 상호 작용 (직접)</span><span class="sxs-lookup"><span data-stu-id="68f55-146">Near interactions (direct)</span></span> 

<span data-ttu-id="68f55-147">HoloLens 2는 개체와 상호 작용할 수 있도록 하는 트레일러 추적 입력을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="68f55-148">사용자 의견을 햅 하 고 완벽 하 게 인식 하지 못하는 경우에도 개체에서 얼마나 멀리 떨어져 있는지 또는 사용자가 이야기 하 고 있는지를 확인 하는 것이 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span></span> <span data-ttu-id="68f55-149">개체 상태를 전달 하는 데 충분 한 시각적 신호를 제공 하 고 해당 개체와 관련 된 사용자의 상태를 제공 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span></span>

<span data-ttu-id="68f55-150">시각적 피드백을 사용 하 여 다음을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-150">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="68f55-151">**Default (관찰)** : 개체의 기본 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-151">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="68f55-152">**가리키기**: 손을 홀로그램 근처에 있으면 시각적 개체를 대상으로 하 여 홀로그램을 대상으로 하는 통신으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-152">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="68f55-153">**거리 및 상호 작용 지점**: 홀로그램은 홀로그램에 근접 하 고, 예상 되는 상호 작용 지점을 전달 하기 위한 디자인 피드백을 비롯 하 여 개체의 거리와</span><span class="sxs-lookup"><span data-stu-id="68f55-153">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="68f55-154">**연락처 시작**: 터치가 발생 했음을 알리기 위해 시각적 개체 (광원, 색)를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-154">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="68f55-155">**Grasped**: 개체가 Grasped 경우 시각적 개체 (광원, 색)를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-155">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="68f55-156">**연락처 끝**: 터치가 종료 되 면 시각적 개체 (밝은 색)를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-156">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="68f55-157">![가리키기 (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="68f55-158">**가리키기 (Far)**</span><span class="sxs-lookup"><span data-stu-id="68f55-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="68f55-159">손 모양에 따라 강조 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="68f55-160">![가리키기 (근처)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="68f55-161">**가리키기 (근처)**</span><span class="sxs-lookup"><span data-stu-id="68f55-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="68f55-162">강조 표시 크기는 손 거리에 따라 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="68f55-163">![Touch/press](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="68f55-164">**터치/누르기**</span><span class="sxs-lookup"><span data-stu-id="68f55-164">**Touch / press**</span></span><br>
        <span data-ttu-id="68f55-165">시각적 개체와 오디오 피드백</span><span class="sxs-lookup"><span data-stu-id="68f55-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="68f55-166">![](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="68f55-167">**잡습니다**</span><span class="sxs-lookup"><span data-stu-id="68f55-167">**Grasp**</span></span><br>
        <span data-ttu-id="68f55-168">시각적 개체와 오디오 피드백</span><span class="sxs-lookup"><span data-stu-id="68f55-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="68f55-169">[HoloLens 2의 단추](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) 는 서로 다른 입력 상호 작용 상태를 시각화 하는 방법의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="68f55-170">![기본](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="68f55-171">**기본**</span><span class="sxs-lookup"><span data-stu-id="68f55-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="68f55-172">![가리키기](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="68f55-173">**오도록**</span><span class="sxs-lookup"><span data-stu-id="68f55-173">**Hover**</span></span><br>
        <span data-ttu-id="68f55-174">근접 기반 조명 효과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="68f55-175">![터치](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="68f55-176">**터치**</span><span class="sxs-lookup"><span data-stu-id="68f55-176">**Touch**</span></span><br>
        <span data-ttu-id="68f55-177">Ripple 효과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="68f55-178">](images/640px-interactibleobject-pressablebutton-press.jpg) ![누르기</span><span class="sxs-lookup"><span data-stu-id="68f55-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="68f55-179">**누르면**</span><span class="sxs-lookup"><span data-stu-id="68f55-179">**Press**</span></span><br>
        <span data-ttu-id="68f55-180">프런트 판을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="68f55-181">HoloLens 2의 "링" 시각 신호</span><span class="sxs-lookup"><span data-stu-id="68f55-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="68f55-182">HoloLens 2에는 사용자가 깊이를 인식 하는 데 도움이 될 수 있는 추가 시각적 표시가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-182">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="68f55-183">Fingertip 근처의 링은 개체에 가까울수록 fingertip가 위쪽으로 표시 되 고 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="68f55-184">누름 상태에 도달 하면 링이 결국 점으로 수렴.</span><span class="sxs-lookup"><span data-stu-id="68f55-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="68f55-185">이 시각적 affordance는 사용자가 개체에서 얼마나 떨어져 있는지 이해 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="68f55-186">*비디오 루프: 경계 상자에 근접 한 시각적 피드백의 예*</span><span class="sxs-lookup"><span data-stu-id="68f55-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="68f55-187">![공간](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="68f55-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="68f55-188">직접 근접 한 시각적 피드백을 ![](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="68f55-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="68f55-189">오디오 신호</span><span class="sxs-lookup"><span data-stu-id="68f55-189">Audio cues</span></span>

<span data-ttu-id="68f55-190">직접 상호 작용을 위해 적절 한 오디오 피드백을 통해 사용자 환경을 크게 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="68f55-191">오디오 피드백을 사용 하 여 다음을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-191">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="68f55-192">**연락처 시작**: 터치 시작 시 소리 재생</span><span class="sxs-lookup"><span data-stu-id="68f55-192">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="68f55-193">**연락처 끝**: 터치 엔드에서 소리 재생</span><span class="sxs-lookup"><span data-stu-id="68f55-193">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="68f55-194">**시작**: 잡기 시작 시 소리 재생</span><span class="sxs-lookup"><span data-stu-id="68f55-194">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="68f55-195">**잡기 종료**: 잡기 종료 시 소리 재생</span><span class="sxs-lookup"><span data-stu-id="68f55-195">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="68f55-196">음성 명령</span><span class="sxs-lookup"><span data-stu-id="68f55-196">Voice commanding</span></span><br>
        <span data-ttu-id="68f55-197">Interactable 개체의 경우 대체 상호 작용 옵션을 지 원하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-197">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="68f55-198">기본적으로 interactable 되는 모든 개체에 대해 [음성 명령](voice-design.md) 지원을 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-198">By default, we recommend that [voice commanding](voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="68f55-199">검색 가능성을 향상 시키기 위해 가리키기 상태에서 도구 설명을 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="68f55-200">*Image: 음성 명령에 대 한 도구 설명*</span><span class="sxs-lookup"><span data-stu-id="68f55-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![음성 명령](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="68f55-202">크기 조정 권장 사항</span><span class="sxs-lookup"><span data-stu-id="68f55-202">Sizing recommendations</span></span> 

<span data-ttu-id="68f55-203">사용자가 모든 interactable 개체를 쉽게 사용할 수 있도록 하려면 사용자의 거리를 기준으로 interactable이 최소 크기 (시각적 원호의 각도로 측정 되는 시각적 각도)를 충족 하는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-203">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="68f55-204">시각적 각도는 사용자의 눈동자와 개체 간의 거리를 기준으로 하며 일정 하 게 유지 되 고, 대상의 실제 크기는 사용자의 거리가 변경 될 때 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-204">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="68f55-205">사용자의 거리를 기준으로 개체의 필요한 실제 크기를 확인 하려면 [다음과 같은 시각적](https://elvers.us/perception/visualAngle/)각도 계산기를 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="68f55-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="68f55-206">다음은 interactable 콘텐츠의 최소 크기에 대 한 권장 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="68f55-207">직접 상호 작용의 대상 크기</span><span class="sxs-lookup"><span data-stu-id="68f55-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="68f55-208">거리</span><span class="sxs-lookup"><span data-stu-id="68f55-208">Distance</span></span> | <span data-ttu-id="68f55-209">시야각</span><span class="sxs-lookup"><span data-stu-id="68f55-209">Viewing angle</span></span> | <span data-ttu-id="68f55-210">사이즈</span><span class="sxs-lookup"><span data-stu-id="68f55-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="68f55-211">45cm</span><span class="sxs-lookup"><span data-stu-id="68f55-211">45cm</span></span>  | <span data-ttu-id="68f55-212">2 ° 미만</span><span class="sxs-lookup"><span data-stu-id="68f55-212">no smaller than 2°</span></span> | <span data-ttu-id="68f55-213">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="68f55-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="68f55-214">직접 상호 작용에 대 한 대상 크기를 ![](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="68f55-215">*직접 상호 작용의 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="68f55-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="68f55-216">단추의 대상 크기</span><span class="sxs-lookup"><span data-stu-id="68f55-216">Target size for buttons</span></span>

<span data-ttu-id="68f55-217">직접 상호 작용에 대 한 단추를 만들 때 아이콘 및 잠재적으로 일부 텍스트를 포함할 수 있는 충분 한 공간이 있도록 최소 크기인 3.2 x 3.2 cm을 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="68f55-218">거리</span><span class="sxs-lookup"><span data-stu-id="68f55-218">Distance</span></span> | <span data-ttu-id="68f55-219">최소 크기</span><span class="sxs-lookup"><span data-stu-id="68f55-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="68f55-220">45cm</span><span class="sxs-lookup"><span data-stu-id="68f55-220">45cm</span></span>  | <span data-ttu-id="68f55-221">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="68f55-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="68f55-222">단추에 대 한 대상 크기를 ![](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="68f55-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="68f55-223">*단추의 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="68f55-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="68f55-224">핸드 레이 또는 응시 상호 작용의 대상 크기</span><span class="sxs-lookup"><span data-stu-id="68f55-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="68f55-225">거리</span><span class="sxs-lookup"><span data-stu-id="68f55-225">Distance</span></span> | <span data-ttu-id="68f55-226">시야각</span><span class="sxs-lookup"><span data-stu-id="68f55-226">Viewing angle</span></span> | <span data-ttu-id="68f55-227">사이즈</span><span class="sxs-lookup"><span data-stu-id="68f55-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="68f55-228">2m</span><span class="sxs-lookup"><span data-stu-id="68f55-228">2m</span></span>  | <span data-ttu-id="68f55-229">1 ° 보다 작음</span><span class="sxs-lookup"><span data-stu-id="68f55-229">no smaller than 1°</span></span> | <span data-ttu-id="68f55-230">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="68f55-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="68f55-231">손으로 광선 또는 응시 상호 작용에 대 한 대상 크기를 ![](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="68f55-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="68f55-232">*핸드 레이 또는 응시 상호 작용의 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="68f55-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtkmixed-reality-toolkit-for-unit"></a><span data-ttu-id="68f55-233">단위에 대 한 MRTK (Mixed Reality Toolkit)의 Interactable 개체</span><span class="sxs-lookup"><span data-stu-id="68f55-233">Interactable object in MRTK(Mixed Reality Toolkit) for Unit</span></span>

<span data-ttu-id="68f55-234">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 에서는 [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) 스크립트를 사용 하 여 개체를 다양 한 유형의 입력 상호 작용 상태에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="68f55-235">색, 크기, 재질, 셰이더 등의 개체 속성을 제어 하 여 시각적 상태를 정의할 수 있도록 하는 다양 한 형식의 테마를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-235">It supports various types of themes that allows you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="68f55-236">Interactable</span><span class="sxs-lookup"><span data-stu-id="68f55-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="68f55-237">Button</span><span class="sxs-lookup"><span data-stu-id="68f55-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="68f55-238">직접 상호 작용 예제 장면</span><span class="sxs-lookup"><span data-stu-id="68f55-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="68f55-239">MixedRealityToolkit의 표준 셰이더는 시각적 및 오디오 큐를 만드는 데 도움이 되는 **근접 조명** 과 같은 다양 한 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="68f55-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="68f55-240">MRTK 표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="68f55-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="68f55-241">참고 항목</span><span class="sxs-lookup"><span data-stu-id="68f55-241">See also</span></span>

* [<span data-ttu-id="68f55-242">커서</span><span class="sxs-lookup"><span data-stu-id="68f55-242">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="68f55-243">손 모양</span><span class="sxs-lookup"><span data-stu-id="68f55-243">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="68f55-244">Button</span><span class="sxs-lookup"><span data-stu-id="68f55-244">Button</span></span>](button.md)
* [<span data-ttu-id="68f55-245">상호 작용 가능한 개체</span><span class="sxs-lookup"><span data-stu-id="68f55-245">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="68f55-246">경계 상자 및 앱 바</span><span class="sxs-lookup"><span data-stu-id="68f55-246">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="68f55-247">조작은</span><span class="sxs-lookup"><span data-stu-id="68f55-247">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="68f55-248">손 메뉴</span><span class="sxs-lookup"><span data-stu-id="68f55-248">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="68f55-249">메뉴 근처</span><span class="sxs-lookup"><span data-stu-id="68f55-249">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="68f55-250">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="68f55-250">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="68f55-251">음성 명령</span><span class="sxs-lookup"><span data-stu-id="68f55-251">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="68f55-252">키보드</span><span class="sxs-lookup"><span data-stu-id="68f55-252">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="68f55-253">놓으면</span><span class="sxs-lookup"><span data-stu-id="68f55-253">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="68f55-254">찬</span><span class="sxs-lookup"><span data-stu-id="68f55-254">Slate</span></span>](slate.md)
* [<span data-ttu-id="68f55-255">슬라이더</span><span class="sxs-lookup"><span data-stu-id="68f55-255">Slider</span></span>](slider.md)
* [<span data-ttu-id="68f55-256">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="68f55-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="68f55-257">진행률 표시</span><span class="sxs-lookup"><span data-stu-id="68f55-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="68f55-258">표면 자기</span><span class="sxs-lookup"><span data-stu-id="68f55-258">Surface magnetism</span></span>](surface-magnetism.md)