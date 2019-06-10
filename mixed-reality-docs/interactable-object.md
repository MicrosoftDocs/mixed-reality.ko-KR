---
title: 상호 작용할 수 없는 개체
description: 2D 추상 전 세계에서 이벤트를 트리거하는 데 사용 하는 비유를 오랫동안 단추입니다. 3 차원 혼합된 현실 세계에서 추상화를 더 이상이 환경으로 제한 될 필요가 없습니다.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 혼합된 현실 "," 컨트롤 "," 상호 작용 "," ui "," ux
ms.openlocfilehash: eea7eff6c591a9319b920936ce2be511cecb7496
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813828"
---
# <a name="interactable-object"></a><span data-ttu-id="0e2fd-105">상호 작용할 수 없는 개체</span><span class="sxs-lookup"><span data-stu-id="0e2fd-105">Interactable object</span></span>

<span data-ttu-id="0e2fd-106">2D 추상 전 세계에서 이벤트를 트리거하는 데 사용 하는 비유를 오랫동안 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="0e2fd-107">3 차원 혼합된 현실 세계에서 추상화를 더 이상이 환경으로 제한 될 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="0e2fd-108">항목 수를 **상호 작용할 수 없는 개체** 이벤트를 트리거하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="0e2fd-109">상호 작용할 수 없는 개체로 나타낼 수 있습니다 것과 테이블에는 커피 cup에서 공중에서 부동 풍선으로.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="0e2fd-110">여전히 확인 수행 대화 상자 UI와 같이 이러한 특정 상황에서 기존 단추를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="0e2fd-111">단추의 시각적 표시는 컨텍스트에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-111">The visual representation of the button depends on the context.</span></span>

![Interactible 개체](images/640px-interactibleobject-hero-640px.jpg)


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="0e2fd-113">상호 작용할 수 없는 개체의 중요 한 속성</span><span class="sxs-lookup"><span data-stu-id="0e2fd-113">Important properties of the interactable object</span></span>

### <a name="visual-cue"></a><span data-ttu-id="0e2fd-114">시각 신호</span><span class="sxs-lookup"><span data-stu-id="0e2fd-114">Visual cue</span></span>

<span data-ttu-id="0e2fd-115">시각 신호는 토대로 신호 light의 형태로 눈으로 수신 하 고 시각적 인식 하는 동안 visual 시스템에서 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="0e2fd-116">시각적 시스템에서 여러 종류, 특히 사용자 기준 이므로 시각 신호 것은 대규모 전 세계를 인식 하는 방법에 대 한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="0e2fd-117">혼합된 현실에서 실제 환경과 holographic 개체 혼합 되어 있으므로 수 있습니다 상호 작용할 수 없는 개체는 이해 하기가 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-117">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="0e2fd-118">환경에서 상호 작용할 수 없는 개체에 대 한 상태 각 입력에 대해 차별화 된 시각을 제공 하는 것이 반드시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-118">For any interactable objects in your experience, it is important to provide differentiated visual cue for each input state.</span></span> <span data-ttu-id="0e2fd-119">이렇게 하면 사용자 이해 사용자 경험의 어느 부분이 상호 작용할 수 없는 이며 일관성 있는 상호 작용 메서드를 사용 하 여 사용자를 확신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-119">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

#### <a name="far-interactions"></a><span data-ttu-id="0e2fd-120">먼 상호 작용</span><span class="sxs-lookup"><span data-stu-id="0e2fd-120">Far interactions</span></span>

<span data-ttu-id="0e2fd-121">모든 개체에 대 한 해당 사용자와 상호 작용할 수 게이즈를 직접 광선 동작 컨트롤러의 광선 것이 좋습니다 이러한 세 가지 입력된 상태에 대 한 다양 한 시각적 표시를 할:</span><span class="sxs-lookup"><span data-stu-id="0e2fd-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>
* <span data-ttu-id="0e2fd-122">**기본 (관찰)** : 개체의 기본 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-122">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="0e2fd-123">**대상된 (가리키기)** : 개체를 응시 커서를 사용 하 여 대상으로 하는 경우에 근접 또는 동영상 컨트롤러의 포인터 손가락으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-123">**Targeted (Hover)**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="0e2fd-124">**누른**: 어 탭 제스처, 손가락 누르거나 동작 컨트롤러의 선택 단추를 사용 하 여 개체를 누를 때 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="0e2fd-125">사용자의 입력된 상태에 시각 신호 제공 강조 표시 하거나 확장 하는 기법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-125">You can use techniques such as highlighting or scaling to provide visual cue to the user’s input states.</span></span> <span data-ttu-id="0e2fd-126">Windows Mixed Reality 시작 메뉴 및 앱 바 단추 입력된 상태를 다른 시각화의 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-126">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> 

<span data-ttu-id="0e2fd-127">![관찰 상태 시각화의 예제에서는 상태를 대상으로 하 고 누른 상태](images/640px-interactibleobject-states.png)</span><span class="sxs-lookup"><span data-stu-id="0e2fd-127">![Example of visualizing observation state, targeted state, and pressed state](images/640px-interactibleobject-states.png)</span></span><br>
<span data-ttu-id="0e2fd-128">*관찰 상태 시각화의 예제에서는 상태를 대상으로 하 고 누른 상태*</span><span class="sxs-lookup"><span data-stu-id="0e2fd-128">*Example of visualizing observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="0e2fd-129">![관찰 상태 대상 상태 및 상태 holographic 단추 누름](images/MRTK_InteractableState.png)</span><span class="sxs-lookup"><span data-stu-id="0e2fd-129">![Observation state, targeted state, and pressed state on holographic button](images/MRTK_InteractableState.png)</span></span><br>
<span data-ttu-id="0e2fd-130">*관찰 상태 대상 상태 및 상태 holographic 단추 누름*</span><span class="sxs-lookup"><span data-stu-id="0e2fd-130">*Observation state, targeted state, and pressed state on holographic button*</span></span>

#### <a name="neardirect-interactions"></a><span data-ttu-id="0e2fd-131">Near(direct) 상호 작용</span><span class="sxs-lookup"><span data-stu-id="0e2fd-131">Near(direct) interactions</span></span>

<span data-ttu-id="0e2fd-132">HoloLens 2 명확 하 고 직접 입력 개체와 상호 작용할 수 있는 추적을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-132">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="0e2fd-133">햅 틱 피드백 및 경우에 따라에서 완벽 한 깊이 인식 하지 않고 개체에서 직접은 얼마나 떨어져 하거나 터치 하는 여부를 확인 하기 어려운 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-133">Without haptic feedback and perfect depth perception sometimes it can be hard to tell how far away your hand is from an object, or whether you are touching.</span></span> <span data-ttu-id="0e2fd-134">에 제공 하는 관계에서는 손이의 특정 개체의 상태를 전달 하려면 충분 한 시각 신호를 제공 하는 것이 반드시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-134">It is important to provide enough visual cues to communicate the state of the object and in particular of your hands in relation to holograms.</span></span>

<span data-ttu-id="0e2fd-135">다음 전달할 시각적 피드백을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-135">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="0e2fd-136">**기본 (관찰)** : 개체의 기본 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-136">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="0e2fd-137">**가리킨**: 홀로그램, 변경 시각적 개체는 직접 통신 거의 직접 경우 홀로그램 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-137">**Hover**: When hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="0e2fd-138">**거리와 상호 작용 지점의**: 직접 홀로그램 다가오면 디자인 손가락은 개체 멀리 방법과 예상된 지점의 상호 작용도 통신 하는 피드백</span><span class="sxs-lookup"><span data-stu-id="0e2fd-138">**Distance and point of interaction**: As hand approaches hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="0e2fd-139">**문의 시작**: 변경 시각적 개체 (광원, 색)는 터치 전달할 발생</span><span class="sxs-lookup"><span data-stu-id="0e2fd-139">**Contact Begin**: Change visuals (light, color) to communicate that touch has occured</span></span>
* <span data-ttu-id="0e2fd-140">**잡았습니다**: 시각적 개체 (광원, 색)을 변경할 개체는 잡았습니다 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-140">**Grasped**: Change visuals (light, color) when the object is grasped.</span></span>
* <span data-ttu-id="0e2fd-141">**문의 끝**: 시각적 개체 (광원, 색)을 변경할 경우 터치를 마쳤습니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-141">**Contact End**: Change visuals (light, color) when touch has ended.</span></span>

<span data-ttu-id="0e2fd-142">![시각화 상호 작용 상태 근처의 예](images/640px-interactibleobject-states-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="0e2fd-142">![Example of visualizing near interaction states](images/640px-interactibleobject-states-near.jpg)</span></span><br>
<span data-ttu-id="0e2fd-143">*시각화 상호 작용 상태 근처의 예*</span><span class="sxs-lookup"><span data-stu-id="0e2fd-143">*Example of visualizing near interaction states*</span></span>

<span data-ttu-id="0e2fd-144">합니다 [HoloLens 2 단추](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) 다른 입력된 상호 작용 상태 시각화의 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-144">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows the example of visualizing different input interaction states.</span></span>

<span data-ttu-id="0e2fd-145">![HoloLens 2에서 pressable 단추 예제](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span><span class="sxs-lookup"><span data-stu-id="0e2fd-145">![Example of pressable button in HoloLens 2](images/640px-interactibleobject-pressablebutton-650px2.jpg)</span></span><br>
<span data-ttu-id="0e2fd-146">*HoloLens 2에서 pressable 단추 예제*</span><span class="sxs-lookup"><span data-stu-id="0e2fd-146">*Example of pressable button in HoloLens 2*</span></span>

<span data-ttu-id="0e2fd-147">HoloLens 2에서는 깊이 perception에서 사용자의 신뢰도 개선 하는 시각적 표시를 추가로 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-147">In HoloLens 2, there is an additional visual cue which improves the user's confidence on the depth perception.</span></span> <span data-ttu-id="0e2fd-148">링의 손끝에서 표시 하 고 끝 가까워질수록 개체 처럼 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-148">The ring on the fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="0e2fd-149">키를 눌러 상태에 점에 링 결국 수렴 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-149">The ring eventually converges into a dot on press state.</span></span> <span data-ttu-id="0e2fd-150">이 visual 유도성을 지 원하는 개체에서의 거리를 이해 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-150">This visual affordance helps the user understand the distance from the object.</span></span>

<span data-ttu-id="0e2fd-151">![손끝 링 시각화](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span><span class="sxs-lookup"><span data-stu-id="0e2fd-151">![Fingertip ring visualization](images/640px-interactibleobject-pressablebutton-650px3.jpg)</span></span><br>
<span data-ttu-id="0e2fd-152">*HoloLens 2의 손끝 링 시각화*</span><span class="sxs-lookup"><span data-stu-id="0e2fd-152">*Fingertip ring visualization in HoloLens 2*</span></span>

<span data-ttu-id="0e2fd-153">![직접 근접에 대 한 시각적 피드백](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="0e2fd-153">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="0e2fd-154">*-경계 상자 근접도에 따라 시각적 피드백의 예*</span><span class="sxs-lookup"><span data-stu-id="0e2fd-154">*Example of visual feedback based on the proximity - Bounding Box*</span></span>


### <a name="audio-cue"></a><span data-ttu-id="0e2fd-155">오디오 신호</span><span class="sxs-lookup"><span data-stu-id="0e2fd-155">Audio cue</span></span>
<span data-ttu-id="0e2fd-156">직접 직접 상호 작용에 대 한 적절 한 오디오 피드백 사용자 환경을 크게 향상할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-156">For the direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="0e2fd-157">다음 전달할 오디오 피드백을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-157">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="0e2fd-158">**문의 시작**: 터치가 시작 될 때 소리 재생</span><span class="sxs-lookup"><span data-stu-id="0e2fd-158">**Contact begin**: Play sound when touch begins</span></span>
* <span data-ttu-id="0e2fd-159">**연락처 최종**: 터치 끝에서 소리 재생</span><span class="sxs-lookup"><span data-stu-id="0e2fd-159">**Contact end**: Play sound on touch end</span></span>
* <span data-ttu-id="0e2fd-160">**잡기 시작**: 잡기 시작 될 때 소리 재생</span><span class="sxs-lookup"><span data-stu-id="0e2fd-160">**Grab begin**: Play sound when grab starts</span></span>
* <span data-ttu-id="0e2fd-161">**끝을 잡고**: 잡기 끝에서 소리 재생</span><span class="sxs-lookup"><span data-stu-id="0e2fd-161">**Grab end**: Play sound on grab end</span></span>

### <a name="voice-command"></a><span data-ttu-id="0e2fd-162">음성 명령</span><span class="sxs-lookup"><span data-stu-id="0e2fd-162">Voice command</span></span>
<span data-ttu-id="0e2fd-163">모든 상호 작용할 수 없는 개체에 대 한 대체 상호 작용 옵션을 지원 하도록 반드시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-163">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="0e2fd-164">기본, 것이 좋습니다 상호 작용할 수 없는 모든 개체에 대 한 음성 명령을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-164">In default, it is recommended to support voice command for any objects that are interactable.</span></span> <span data-ttu-id="0e2fd-165">검색 기능 향상을 위해 가리키기 상태에서 도구 설명을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-165">To improve the discoverability, you can provide tooltip on hover state.</span></span>

<img src="images/640px-interactibleobject-voicecommand.jpg" alt="Tooltip for the voice command" title="음성 명령에 대 한 도구 설명" width="350"><br/><span data-ttu-id="0e2fd-167">*음성 명령에 대 한 도구 설명*</span><span class="sxs-lookup"><span data-stu-id="0e2fd-167">*Tooltip for the voice command*</span></span>

## <a name="creating-interactable-object-with-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="0e2fd-168">혼합 현실 도구 키트 (MRTK)을 사용 하 여 상호 작용할 수 없는 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="0e2fd-168">Creating interactable object with Mixed Reality Toolkit (MRTK)</span></span>

<span data-ttu-id="0e2fd-169">에  **[혼합 현실 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , 일련의 Unity 스크립트를 찾을 수 있습니다 및 prefabs 도움이 되는 상호 작용할 수 없는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-169">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can find the series of Unity scripts and prefabs that will help you create interactable objects.</span></span> <span data-ttu-id="0e2fd-170">다양 한 유형의 입력된 상호 작용 상태에 응답 하는 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-170">You can use these to make objects respond to various types of input interaction states.</span></span>

* <span data-ttu-id="0e2fd-171">**[Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)**</span><span class="sxs-lookup"><span data-stu-id="0e2fd-171">**[Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)**</span></span>
* <span data-ttu-id="0e2fd-172">**[Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)**</span><span class="sxs-lookup"><span data-stu-id="0e2fd-172">**[Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)**</span></span>
* <span data-ttu-id="0e2fd-173">**[직접 상호 작용 예제 장면](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)**</span><span class="sxs-lookup"><span data-stu-id="0e2fd-173">**[Hand Interaction Examples Scene](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)**</span></span>

<span data-ttu-id="0e2fd-174">MixedRealityToolkit의 표준 셰이더와 같은 다양 한 옵션을 제공 **근접 light** 를 시각적 및 오디오 큐를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e2fd-174">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* <span data-ttu-id="0e2fd-175">**[MRTK 표준 셰이더](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)**</span><span class="sxs-lookup"><span data-stu-id="0e2fd-175">**[MRTK Standard Shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)**</span></span>


## <a name="see-also"></a><span data-ttu-id="0e2fd-176">참조</span><span class="sxs-lookup"><span data-stu-id="0e2fd-176">See also</span></span>

* <span data-ttu-id="0e2fd-177">**[경계 상자](app-bar-and-bounding-box.md)**</span><span class="sxs-lookup"><span data-stu-id="0e2fd-177">**[Bounding Box](app-bar-and-bounding-box.md)**</span></span>
* <span data-ttu-id="0e2fd-178">**[개체 컬렉션](object-collection.md)**</span><span class="sxs-lookup"><span data-stu-id="0e2fd-178">**[Object collection](object-collection.md)**</span></span>
* <span data-ttu-id="0e2fd-179">**[빌보드 및 tag-along](billboarding-and-tag-along.md)**</span><span class="sxs-lookup"><span data-stu-id="0e2fd-179">**[Billboarding and tag-along](billboarding-and-tag-along.md)**</span></span>
