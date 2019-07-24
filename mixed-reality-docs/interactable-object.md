---
title: Interactable 개체
description: 단추는 긴 2D 추상 세계에서 이벤트를 트리거하는 데 사용 되는 비유입니다. 3 차원 혼합 현실 세계에서는 이러한 추상화의 목표로 더 이상 국한 되지 않습니다.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: 혼합 현실, 컨트롤, 상호 작용, ui, ux
ms.openlocfilehash: 57299cbb758a69603fc68ad5d43af8f2216e5104
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415367"
---
# <a name="interactable-object"></a><span data-ttu-id="7f473-105">Interactable 개체</span><span class="sxs-lookup"><span data-stu-id="7f473-105">Interactable object</span></span>

<span data-ttu-id="7f473-106">단추는 긴 2D 추상 세계에서 이벤트를 트리거하는 데 사용 되는 비유입니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="7f473-107">3 차원 혼합 현실 세계에서는 이러한 추상화의 목표로 더 이상 국한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="7f473-108">모든 항목은 이벤트를 트리거하는 **interactable 개체** 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="7f473-109">Interactable 개체는 테이블의 커피에서 공기의 풍선 부동으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="7f473-110">대화 상자 UI에서와 같은 특정 상황에서는 여전히 기존 단추를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="7f473-111">단추의 시각적 표시는 컨텍스트에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-111">The visual representation of the button depends on the context.</span></span>

![Interactible 개체](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="7f473-113">Interactable 개체의 중요 한 속성</span><span class="sxs-lookup"><span data-stu-id="7f473-113">Important properties of the interactable object</span></span>

### <a name="visual-cue"></a><span data-ttu-id="7f473-114">시각적 표시</span><span class="sxs-lookup"><span data-stu-id="7f473-114">Visual cue</span></span>

<span data-ttu-id="7f473-115">시각적 신호는 시각적 개체를 시각적으로 인식 하면서 시각적 시스템에서 처리 하 고 밝은 형태로 받은 토대로 된 큐입니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="7f473-116">시각적 시스템은 다양 한 정보, 특히 사람에 게 중요 한 것 이므로 시각적 신호는 전 세계의 정보에 대 한 많은 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="7f473-117">혼합 현실에서는 holographic 개체가 실제 환경과 혼합 되어 있으므로 interactable 개체를 이해 하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-117">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="7f473-118">사용자 환경에서 interactable 개체의 경우 각 입력 상태에 대해 차별화 된 시각적 표시를 제공 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-118">For any interactable objects in your experience, it is important to provide differentiated visual cue for each input state.</span></span> <span data-ttu-id="7f473-119">이렇게 하면 사용자가 interactable 하는 환경 부분을 이해 하 고 사용자에 게 일관 된 상호 작용 방법을 확신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-119">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

#### <a name="far-interactions"></a><span data-ttu-id="7f473-120">먼 상호 작용</span><span class="sxs-lookup"><span data-stu-id="7f473-120">Far interactions</span></span>

<span data-ttu-id="7f473-121">사용자가 응시, 손 모양 및 모션 컨트롤러의 광선과 상호 작용할 수 있는 개체의 경우 다음과 같은 세 가지 입력 상태에 대해 서로 다른 시각적 표시를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>
* <span data-ttu-id="7f473-122">**기본 (관찰)** : 개체의 기본 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-122">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="7f473-123">**대상 지정 (가리키기)** : 개체가 응시 커서, 손가락 근접 또는 동작 컨트롤러의 포인터를 대상으로 하는 경우</span><span class="sxs-lookup"><span data-stu-id="7f473-123">**Targeted (Hover)**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="7f473-124">**누름**: 공기 탭 제스처를 사용 하 여 개체를 누르면 손가락을 누르거나 동작 컨트롤러의 선택 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="7f473-125">강조 표시 또는 크기 조정과 같은 기술을 사용 하 여 사용자의 입력 상태에 시각적 신호를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-125">You can use techniques such as highlighting or scaling to provide visual cue to the user’s input states.</span></span> <span data-ttu-id="7f473-126">Windows Mixed Reality에서는 시작 메뉴와 앱 바 단추에서 다양 한 입력 상태를 시각화 하는 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-126">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> 

<span data-ttu-id="7f473-127">![관찰 상태, 대상 상태 및 누름 상태 시각화의 예](images/640px-interactibleobject-states.png)</span><span class="sxs-lookup"><span data-stu-id="7f473-127">![Example of visualizing observation state, targeted state, and pressed state](images/640px-interactibleobject-states.png)</span></span><br>
<span data-ttu-id="7f473-128">*관찰 상태, 대상 상태 및 누름 상태 시각화의 예*</span><span class="sxs-lookup"><span data-stu-id="7f473-128">*Example of visualizing observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="7f473-129">![Holographic 단추의 관찰 상태, 대상 상태 및 누름 상태](images/MRTK_InteractableState.png)</span><span class="sxs-lookup"><span data-stu-id="7f473-129">![Observation state, targeted state, and pressed state on holographic button](images/MRTK_InteractableState.png)</span></span><br>
<span data-ttu-id="7f473-130">*Holographic 단추의 관찰 상태, 대상 상태 및 누름 상태*</span><span class="sxs-lookup"><span data-stu-id="7f473-130">*Observation state, targeted state, and pressed state on holographic button*</span></span>

#### <a name="neardirect-interactions"></a><span data-ttu-id="7f473-131">근거리 (직접) 상호 작용</span><span class="sxs-lookup"><span data-stu-id="7f473-131">Near(direct) interactions</span></span>

<span data-ttu-id="7f473-132">HoloLens 2는 개체와 상호 작용할 수 있도록 하는 트레일러 추적 입력을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-132">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="7f473-133">햅 피드백 및 완벽 한 수준 인식 없이 개체에서 손 거리를 확인 하는 것이 어려울 수 있습니다. 또는 접촉 하 고 있는지 여부를 확인 하는 것은 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-133">Without haptic feedback and perfect depth perception sometimes it can be hard to tell how far away your hand is from an object, or whether you are touching.</span></span> <span data-ttu-id="7f473-134">개체의 상태를 전달 하는 데 충분 한 시각적 신호를 제공 하는 것은 holograms와 관련 된 개체의 상태를 전달 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-134">It is important to provide enough visual cues to communicate the state of the object and in particular of your hands in relation to holograms.</span></span>

<span data-ttu-id="7f473-135">시각적 피드백을 사용 하 여 다음을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-135">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="7f473-136">**기본 (관찰)** : 개체의 기본 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-136">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="7f473-137">**가리키기**: 손이 가장 가까이 있는 경우에는 시각적 개체를 대상으로 하 여 홀로그램을 대상으로 하는 통신으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-137">**Hover**: When hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="7f473-138">**상호 작용의 거리 및 지점**: 홀로그램 방법으로, 프로젝션 된 상호 작용 지점 뿐만 아니라 개체에서 손가락으로 떨어져 있는 정도를 전달 하도록 피드백을 디자인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-138">**Distance and point of interaction**: As hand approaches hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="7f473-139">**연락처 시작**: 시각적 개체 (광원, 색)를 변경 하 여 터치가 발생 했음을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-139">**Contact Begin**: Change visuals (light, color) to communicate that touch has occured</span></span>
* <span data-ttu-id="7f473-140">**Grasped**: 개체가 grasped 경우 시각적 개체 (광원, 색)를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-140">**Grasped**: Change visuals (light, color) when the object is grasped.</span></span>
* <span data-ttu-id="7f473-141">**연락처 끝**: 터치가 종료 되 면 시각적 개체 (밝은 색)를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-141">**Contact End**: Change visuals (light, color) when touch has ended.</span></span>

<span data-ttu-id="7f473-142">![거의 상호 작용 상태 시각화의 예제](images/640px-interactibleobject-states-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="7f473-142">![Example of visualizing near interaction states](images/640px-interactibleobject-states-near.jpg)</span></span><br>
<span data-ttu-id="7f473-143">*거의 상호 작용 상태 시각화의 예제*</span><span class="sxs-lookup"><span data-stu-id="7f473-143">*Example of visualizing near interaction states*</span></span>

<span data-ttu-id="7f473-144">[HoloLens 2의 단추](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) 는 다양 한 입력 상호 작용 상태를 시각화 하는 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-144">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows the example of visualizing different input interaction states.</span></span>

<span data-ttu-id="7f473-145">![HoloLens 2의 pressable 단추 예제](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span><span class="sxs-lookup"><span data-stu-id="7f473-145">![Example of pressable button in HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span></span><br>
<span data-ttu-id="7f473-146">*HoloLens 2의 pressable 단추 예제*</span><span class="sxs-lookup"><span data-stu-id="7f473-146">*Example of pressable button in HoloLens 2*</span></span>

<span data-ttu-id="7f473-147">HoloLens 2에는 깊이 인식에 대 한 사용자의 신뢰도를 개선 하는 추가적인 시각적 표시 큐가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-147">In HoloLens 2, there is an additional visual cue which improves the user's confidence on the depth perception.</span></span> <span data-ttu-id="7f473-148">Fingertip가 개체에 가까울수록 fingertip의 링이 표시 되 고 축소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-148">The ring on the fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="7f473-149">링은 결국 누름 상태에서 점으로 수렴.</span><span class="sxs-lookup"><span data-stu-id="7f473-149">The ring eventually converges into a dot on press state.</span></span> <span data-ttu-id="7f473-150">이 시각적 affordance는 사용자가 개체 로부터의 거리를 이해 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-150">This visual affordance helps the user understand the distance from the object.</span></span>

<span data-ttu-id="7f473-151">![Fingertip 링 시각화](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span><span class="sxs-lookup"><span data-stu-id="7f473-151">![Fingertip ring visualization](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span></span><br>
<span data-ttu-id="7f473-152">*HoloLens의 Fingertip 링 시각화 2*</span><span class="sxs-lookup"><span data-stu-id="7f473-152">*Fingertip ring visualization in HoloLens 2*</span></span>

<span data-ttu-id="7f473-153">![근접 한 시각적 피드백](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="7f473-153">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="7f473-154">*근접 경계 상자를 기준으로 하는 시각적 피드백의 예*</span><span class="sxs-lookup"><span data-stu-id="7f473-154">*Example of visual feedback based on the proximity - Bounding box*</span></span>


### <a name="audio-cue"></a><span data-ttu-id="7f473-155">오디오 큐</span><span class="sxs-lookup"><span data-stu-id="7f473-155">Audio cue</span></span>
<span data-ttu-id="7f473-156">직접 상호 작용을 위해 적절 한 오디오 피드백을 통해 사용자 환경을 크게 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-156">For the direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="7f473-157">오디오 피드백을 사용 하 여 다음을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-157">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="7f473-158">**연락처 시작**: 터치 시작 시 소리 재생</span><span class="sxs-lookup"><span data-stu-id="7f473-158">**Contact begin**: Play sound when touch begins</span></span>
* <span data-ttu-id="7f473-159">**연락처 끝**: 터치 엔드에서 소리 재생</span><span class="sxs-lookup"><span data-stu-id="7f473-159">**Contact end**: Play sound on touch end</span></span>
* <span data-ttu-id="7f473-160">**시작 하기**: 잡기 시작 시 소리 재생</span><span class="sxs-lookup"><span data-stu-id="7f473-160">**Grab begin**: Play sound when grab starts</span></span>
* <span data-ttu-id="7f473-161">**종료**: 잡기 쪽에서 소리 재생</span><span class="sxs-lookup"><span data-stu-id="7f473-161">**Grab end**: Play sound on grab end</span></span>

### <a name="voice-command"></a><span data-ttu-id="7f473-162">음성 명령</span><span class="sxs-lookup"><span data-stu-id="7f473-162">Voice command</span></span>
<span data-ttu-id="7f473-163">Interactable 개체의 경우 대체 상호 작용 옵션을 지 원하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-163">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="7f473-164">기본적으로 interactable 되는 모든 개체에 대해 음성 명령을 지 원하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-164">In default, it is recommended to support voice command for any objects that are interactable.</span></span> <span data-ttu-id="7f473-165">검색 가능성을 향상 시키기 위해 가리키기 상태에 도구 설명을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-165">To improve the discoverability, you can provide tooltip on hover state.</span></span>

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="음성 명령에 대 한 도구 설명" width="350"><br/><span data-ttu-id="7f473-167">*음성 명령에 대 한 도구 설명*</span><span class="sxs-lookup"><span data-stu-id="7f473-167">*Tooltip for the voice command*</span></span>

## <a name="sizing"></a><span data-ttu-id="7f473-168">크기 조정</span><span class="sxs-lookup"><span data-stu-id="7f473-168">Sizing</span></span>
<span data-ttu-id="7f473-169">사용자가 모든 interactable 개체를 쉽게 사용할 수 있도록 하려면 사용자의 거리를 기준으로 interactable이 최소 크기 (시각적 원호의 각도로 측정 되는 시각적 각도)를 충족 하는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-169">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="7f473-170">시각적 각도는 사용자의 눈동자와 개체 간의 거리를 기준으로 하며 일정 하 게 유지 되 고, 대상의 실제 크기는 사용자의 거리가 변경 될 때 변경 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-170">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="7f473-171">사용자의 거리를 기준으로 개체의 필요한 실제 크기를 확인 하려면 다음과 같은 시각적 각도 계산기를 사용해 [보세요.](http://elvers.us/perception/visualAngle/)</span><span class="sxs-lookup"><span data-stu-id="7f473-171">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](http://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="7f473-172">다음은 interactable 콘텐츠의 최소 크기에 대 한 권장 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-172">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="7f473-173">직접 상호 작용의 대상 크기</span><span class="sxs-lookup"><span data-stu-id="7f473-173">Target size for direct hand interaction</span></span>
| <span data-ttu-id="7f473-174">거리</span><span class="sxs-lookup"><span data-stu-id="7f473-174">Distance</span></span> | <span data-ttu-id="7f473-175">시야각</span><span class="sxs-lookup"><span data-stu-id="7f473-175">Viewing angle</span></span> | <span data-ttu-id="7f473-176">Size</span><span class="sxs-lookup"><span data-stu-id="7f473-176">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="7f473-177">45cm</span><span class="sxs-lookup"><span data-stu-id="7f473-177">45cm</span></span>  | <span data-ttu-id="7f473-178">2 ° 미만</span><span class="sxs-lookup"><span data-stu-id="7f473-178">no smaller than 2°</span></span> | <span data-ttu-id="7f473-179">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="7f473-179">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="7f473-180">![직접 상호 작용의 대상 크기](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="7f473-180">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="7f473-181">*직접 상호 작용의 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="7f473-181">*Target size for direct hand interaction*</span></span>

<span data-ttu-id="7f473-182">직접 상호 작용에 대 한 단추를 만들 때 아이콘 및 잠재적으로 일부 텍스트를 포함할 수 있는 충분 한 공간이 있는지 확인 하려면 최소 크기인 3.2 x 3.2 cm을 권장 합니다. \* \*</span><span class="sxs-lookup"><span data-stu-id="7f473-182">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text\*\*</span></span>

| <span data-ttu-id="7f473-183">거리</span><span class="sxs-lookup"><span data-stu-id="7f473-183">Distance</span></span> | <span data-ttu-id="7f473-184">최소 크기</span><span class="sxs-lookup"><span data-stu-id="7f473-184">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="7f473-185">45cm</span><span class="sxs-lookup"><span data-stu-id="7f473-185">45cm</span></span>  | <span data-ttu-id="7f473-186">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="7f473-186">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="7f473-187">![단추의 대상 크기](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="7f473-187">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="7f473-188">*단추의 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="7f473-188">*Target size for the buttons*</span></span>


### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="7f473-189">핸드 레이 또는 응시 상호 작용의 대상 크기</span><span class="sxs-lookup"><span data-stu-id="7f473-189">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="7f473-190">거리</span><span class="sxs-lookup"><span data-stu-id="7f473-190">Distance</span></span> | <span data-ttu-id="7f473-191">시야각</span><span class="sxs-lookup"><span data-stu-id="7f473-191">Viewing angle</span></span> | <span data-ttu-id="7f473-192">Size</span><span class="sxs-lookup"><span data-stu-id="7f473-192">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="7f473-193">2m</span><span class="sxs-lookup"><span data-stu-id="7f473-193">2m</span></span>  | <span data-ttu-id="7f473-194">1 ° 보다 작음</span><span class="sxs-lookup"><span data-stu-id="7f473-194">no smaller than 1°</span></span> | <span data-ttu-id="7f473-195">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="7f473-195">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="7f473-196">![핸드 레이 또는 응시 상호 작용의 대상 크기](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="7f473-196">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="7f473-197">*핸드 레이 또는 응시 상호 작용의 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="7f473-197">*Target size for hand ray or gaze interaction*</span></span>

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="7f473-198">혼합 현실 도구 키트를 사용 하 여 interactable 개체 만들기 (MRTK)</span><span class="sxs-lookup"><span data-stu-id="7f473-198">Creating interactable object with Mixed Reality Toolkit (MRTK)</span></span>

<span data-ttu-id="7f473-199">**[혼합 현실 도구 키트](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 에서 interactable 개체를 만드는 데 도움이 되는 일련의 Unity 스크립트 및 prefabs를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-199">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can find the series of Unity scripts and prefabs that will help you create interactable objects.</span></span> <span data-ttu-id="7f473-200">이러한 개체를 사용 하 여 다양 한 유형의 입력 상호 작용 상태에 대해 개체에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-200">You can use these to make objects respond to various types of input interaction states.</span></span>

* [<span data-ttu-id="7f473-201">Interactable</span><span class="sxs-lookup"><span data-stu-id="7f473-201">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="7f473-202">Button</span><span class="sxs-lookup"><span data-stu-id="7f473-202">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="7f473-203">직접 상호 작용 예제 장면</span><span class="sxs-lookup"><span data-stu-id="7f473-203">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="7f473-204">MixedRealityToolkit의 표준 셰이더는 시각적 및 오디오 큐를 만드는 데 도움이 되는 **근접 조명** 과 같은 다양 한 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f473-204">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="7f473-205">MRTK 표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="7f473-205">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


## <a name="see-also"></a><span data-ttu-id="7f473-206">참조</span><span class="sxs-lookup"><span data-stu-id="7f473-206">See also</span></span>

* [<span data-ttu-id="7f473-207">경계 상자</span><span class="sxs-lookup"><span data-stu-id="7f473-207">Bounding box</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="7f473-208">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="7f473-208">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="7f473-209">빌보딩 및 태그얼롱</span><span class="sxs-lookup"><span data-stu-id="7f473-209">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)