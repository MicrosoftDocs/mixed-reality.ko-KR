---
title: MRTK 101 - Mixed Reality Toolkit Unity를 기본 상호 작용에 사용하는 방법(HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Mixed Reality Toolkit Unity를 기본 상호 작용에 사용하는 방법(HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, 디자인, 샘플 앱, 컨트롤
ms.localizationpriority: high
ms.openlocfilehash: 4564e7a0c6a717452effacae2587461fe283cf0b
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79028308"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="a6f3b-104">MRTK 101: Mixed Reality Toolkit Unity를 기본 상호 작용에 사용하는 방법(HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span><span class="sxs-lookup"><span data-stu-id="a6f3b-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="a6f3b-106">MRTK를 사용하여 혼합 현실에서 가장 널리 사용되는 일반적인 상호 작용 패턴을 구현하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="a6f3b-107">Unity 편집기에서 입력 상호 작용을 시뮬레이션하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="a6f3b-108">개체를 잡고 움직이는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-108">How to grab and move an object?</span></span>
- <span data-ttu-id="a6f3b-109">개체 크기를 조정하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-109">How to resize an object?</span></span>
- <span data-ttu-id="a6f3b-110">정밀도를 사용하여 개체를 이동하거나 회전하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="a6f3b-111">개체에서 입력 이벤트에 응답하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="a6f3b-112">시각적 피드백을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-112">How to add visual feedback?</span></span>
- <span data-ttu-id="a6f3b-113">오디오 피드백을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-113">How to add audio feedback?</span></span>
- <span data-ttu-id="a6f3b-114">HoloLens 2 스타일 단추 프리팹을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="a6f3b-115">개체에서 사용자를 따르도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-115">How to make an object follow you?</span></span>
- <span data-ttu-id="a6f3b-116">개체에서 사용자를 향하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="a6f3b-117">Unity 편집기에서 입력 상호 작용을 시뮬레이션하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="a6f3b-118">MRTK는 편집기 내 입력 시뮬레이션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="a6f3b-119">Unity의 재생 단추를 클릭하여 장면을 실행하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="a6f3b-120">이러한 키를 사용하여 입력을 시뮬레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="a6f3b-121">W, A, S, D 키를 눌러 카메라를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="a6f3b-122">마우스 오른쪽 단추를 누른 채 마우스를 움직여 주위를 둘러봅니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="a6f3b-123">시뮬레이션된 손을 들어 가져오려면 스페이스 바(오른쪽 손) 또는 왼쪽 Shift 키(왼쪽 손)를 누릅니다. 보기에서 시뮬레이션된 손을 유지하려면 T 또는 Y 키를 누릅니다. 시뮬레이션된 손을 회전시키려면 Q 또는 E(수평)/R 또는 F(수직) 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="a6f3b-124">MRTK 문서에서 입력 시뮬레이션에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="a6f3b-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="a6f3b-125">개체를 잡고 움직이는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-125">How to grab and move an object?</span></span>
<span data-ttu-id="a6f3b-126">개체를 잡을 수 있게 하려면 다음 두 스크립트를 할당합니다. ManipulationHandler.cs 및 NearInteractionGrabbable.cs(관절 있는 손 추적 입력을 통한 직접 잡기의 경우)의 두 스크립트를 할당합니다. ManipulationHandler는 근거리 및 원거리 상호 작용을 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="a6f3b-127">HoloLens 2의 관절 있는 손 추적 입력(근거리), 손 광선(원거리), 모션 컨트롤러의 빔(원거리), HoloLens 응시 커서 및 에어 탭(원거리)을 사용하여 개체를 잡고 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="a6f3b-128">개체 크기를 조정하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-128">How to resize an object?</span></span>
<span data-ttu-id="a6f3b-129">ManipulationHandler.cs는 양손 크기 조정/회전을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="a6f3b-130">이는 HoloLens 2의 관절 있는 손 입력, HoloLens 1의 응시 + 제스처 입력, Windows Mixed Reality 몰입형 헤드셋의 모션 컨트롤러 입력과 같은 다양한 입력 유형에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="a6f3b-131">MRTK 설명서에서 조작 처리기에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="a6f3b-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="a6f3b-132">정밀도를 사용하여 개체를 이동하거나 회전하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="a6f3b-133">BoundingBox.cs를 개체에 할당하여 개체의 크기를 조정하고 회전하는 인터페이스인 경계 상자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="a6f3b-134">기본적으로 HoloLens 1 스타일 파란색 핸들 및 선이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="a6f3b-135">HoloLens 2 스타일 근접 기반 애니메이션 핸들을 사용하려면 프리팹과 재질을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="a6f3b-136">구성 세부 정보는 [경계 상자 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 및 BoundingBoxExamples.unity 장면을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="a6f3b-137">MRTK 설명서에서 경계 상자에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="a6f3b-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="a6f3b-138">개체에서 입력 이벤트에 응답하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="a6f3b-139">PointerHandler.cs를 개체에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="a6f3b-140">[검사기]에서 OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() 이벤트를 사용할 수 있습니다. 스크립트에서 이러한 이벤트를 사용하려면 IMixedRealityPointerHandler를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="a6f3b-141">MRTK 설명서에서 입력 시스템에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="a6f3b-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="a6f3b-142">시각적 피드백을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-142">How to add visual feedback?</span></span>
<span data-ttu-id="a6f3b-143">Interactable.cs를 개체에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="a6f3b-144">[검사기]에서 새 테마를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="a6f3b-145">Interactable의 테마 프로필을 사용하면 시각적 피드백을 사용 가능한 모든 입력 상호 작용 상태에 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="a6f3b-146">Interactable은 상호 작용 상태에 따라 셰이더의 속성을 제어할 수 있는 셰이더 테마를 포함하여 다양한 유형의 테마를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="a6f3b-147">MRTK 설명서에서 Interactable에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="a6f3b-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="a6f3b-148">시각적 피드백에 대한 또 다른 중요한 구성 요소는 MRTK 표준 셰이더입니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="a6f3b-149">MRTK 표준 셰이더를 사용하면 시각적 피드백 효과(예: 호버 조명, 근접 조명)를 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="a6f3b-150">MRTK 표준 셰이더는 Unity 표준 셰이더보다 훨씬 적은 계산을 수행하므로 성능이 뛰어난 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="a6f3b-151">새 재질을 만들고, 'Mixed Reality Toolkit > 표준' 셰이더를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="a6f3b-152">또는 MRTK 표준 셰이더를 사용하는 기존 재질 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="a6f3b-153">MRTK 문서에서 MRTK 표준 셰이더에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="a6f3b-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="a6f3b-154">오디오 피드백을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-154">How to add audio feedback?</span></span>
<span data-ttu-id="a6f3b-155">AudioSource를 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-155">Add AudioSource to an object.</span></span> <span data-ttu-id="a6f3b-156">그런 다음, 입력 이벤트를 공개하는 스크립트(예: Interactable.cs 또는 PointerHandler.cs)에서 개체를 이벤트에 할당하고, AudioSource.PlayOneShot()을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="a6f3b-157">오디오 클립을 사용하거나 MRTK의 오디오 자산 중에서 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="a6f3b-158">HoloLens 2 스타일 단추 프리팹을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="a6f3b-159">MRTK는 다양한 유형의 HoloLens 2 셸(OS) 스타일 단추를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="a6f3b-160">정교한 시각적 피드백(예: 근접 조명, 압축 상자 및 단추 표면의 잔물결 효과)을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="a6f3b-161">HoloLens 2 스타일 누름 가능한 단추 프리팹 중 하나를 장면에 끌어서 놓기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="a6f3b-162">프리팹은 위에서 소개한 Interactable.cs를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="a6f3b-163">Interactable의 OnClick()과 같은 공개된 이벤트를 사용하여 작업을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="a6f3b-164">MRTK 설명서에서 Button 프리팹에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="a6f3b-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="a6f3b-165">개체에서 사용자를 따르도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-165">How to make an object follow you?</span></span>
<span data-ttu-id="a6f3b-166">RadialView.cs 스크립트를 개체에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="a6f3b-167">3D 공간에서 다양한 유형의 개체 위치 지정을 구현할 수 있는 Solver 스크립트 시리즈의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="a6f3b-168">SolverHandler.cs가 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="a6f3b-169">다음은 HoloLens 셸의 [시작] 메뉴와 마찬가지로 '지연 팔로우(lazy follow)' tag-along 동작을 구현하기 위한 RadialView 구성의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="a6f3b-170">최소/최대 거리 및 최소/최대 보기 각도를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="a6f3b-171">아래 예에서는 개체의 위치를 15° 이내에서 0.4-0.8m 범위를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="a6f3b-172">위치를 더 빠르거나 더 느리게 업데이트하려면 선형 보간 시간(Lerp Time) 값을 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="a6f3b-173">MRTK 설명서에서 Solver에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="a6f3b-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="a6f3b-174">개체에서 사용자를 향하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="a6f3b-174">How to make an object face you?</span></span>
<span data-ttu-id="a6f3b-175">Billboard.cs 스크립트를 개체에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="a6f3b-176">사용자의 위치에 관계없이 항상 사용자를 향합니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="a6f3b-177">피벗 축 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="a6f3b-178">놀라운 혼합 현실 환경을 만들 준비가 되었나요?</span><span class="sxs-lookup"><span data-stu-id="a6f3b-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="a6f3b-179">아래 페이지를 방문하여 MRTK와 혼합 현실에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="a6f3b-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="a6f3b-180">작성자 정보</span><span class="sxs-lookup"><span data-stu-id="a6f3b-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="a6f3b-181"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="a6f3b-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="a6f3b-182">UX 디자이너 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="a6f3b-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="a6f3b-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a6f3b-183">See also</span></span>

* [<span data-ttu-id="a6f3b-184">MRTK(Mixed Reality Toolkit)-Unity GitHub</span><span class="sxs-lookup"><span data-stu-id="a6f3b-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="a6f3b-185">MRTK 설명서 포털</span><span class="sxs-lookup"><span data-stu-id="a6f3b-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="a6f3b-186">MRTK 시작</span><span class="sxs-lookup"><span data-stu-id="a6f3b-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="a6f3b-187">HoloToolkit에서 MRTK로 이식 지침</span><span class="sxs-lookup"><span data-stu-id="a6f3b-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
