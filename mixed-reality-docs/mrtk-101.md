---
title: MRTK 101-기본 상호 작용을 위해 Mixed Reality Toolkit Unity를 사용 하는 방법 (HoloLens 2, HoloLens, Windows Mixed Reality, 열린 VR)
description: 기본 상호 작용을 위해 Mixed Reality Toolkit Unity를 사용 하는 방법 (HoloLens 2, HoloLens, Windows Mixed Reality, 열린 VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, 디자인, 샘플 앱, 컨트롤
ms.openlocfilehash: ad9d2755522c2610ae051fa61f96605e49404d2d
ms.sourcegitcommit: 5054f5c23965ce56599cb29ac9d9c6e48812dabd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75623503"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a><span data-ttu-id="d4743-104">MRTK 101: 기본 상호 작용을 위해 Mixed Reality Toolkit Unity를 사용 하는 방법 (HoloLens 2, HoloLens, Windows Mixed Reality, 오픈 VR)</span><span class="sxs-lookup"><span data-stu-id="d4743-104">MRTK 101: How to use Mixed Reality Toolkit Unity for Basic Interactions (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="d4743-106">MRTK를 사용 하 여 혼합 현실에서 가장 널리 사용 되는 일반적인 상호 작용 패턴을 구현 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="d4743-107">Unity 편집기에서 입력 상호 작용을 시뮬레이트하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="d4743-108">개체를 잡아 이동 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-108">How to grab and move an object?</span></span>
- <span data-ttu-id="d4743-109">개체 크기를 조정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-109">How to resize an object?</span></span>
- <span data-ttu-id="d4743-110">정밀도를 사용 하 여 개체를 이동 하거나 회전 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="d4743-111">개체를 입력 이벤트에 응답 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="d4743-112">시각적 피드백을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-112">How to add visual feedback?</span></span>
- <span data-ttu-id="d4743-113">오디오 피드백을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-113">How to add audio feedback?</span></span>
- <span data-ttu-id="d4743-114">HoloLens 2 스타일 단추 prefabs를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="d4743-115">개체를 팔 로우 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-115">How to make an object follow you?</span></span>
- <span data-ttu-id="d4743-116">개체의 얼굴을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-116">How to make an object face you?</span></span>

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a><span data-ttu-id="d4743-117">Unity 편집기에서 입력 상호 작용을 시뮬레이트하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-117">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="d4743-118">MRTK는 편집기에서 입력 시뮬레이션을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-118">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="d4743-119">Unity의 재생 단추를 클릭 하 여 장면을 실행 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-119">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="d4743-120">이러한 키를 사용 하 여 입력을 시뮬레이트합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-120">Use these keys to simulate input.</span></span>
<span data-ttu-id="d4743-121">W, A, S, D 키를 눌러 카메라를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-121">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="d4743-122">마우스 오른쪽 단추를 누른 상태에서 위로 마우스를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-122">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="d4743-123">시뮬레이션 된 손을 가져오려면 스페이스바 (오른쪽) 또는 왼쪽 Shift 키 (왼쪽)를 눌러 시뮬레이션 된 손을 보기에 유지 하 고, T 또는 Y 키를 눌러 시뮬레이션 된 손을 회전 하거나, Q 또는 E (가로)/R 또는 F (수직)를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-123">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="d4743-124">MRTK 설명서의 입력 시뮬레이션에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="d4743-124">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a><span data-ttu-id="d4743-125">개체를 잡아 이동 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-125">How to grab and move an object?</span></span>
<span data-ttu-id="d4743-126">개체를 grabbable 하려면 다음 두 스크립트를 할당 합니다. ManipulationHandler.cs 및 NearInteractionGrabbable (두 부분으로 된 직접 잡기의 경우) ManipulationHandler는 근거리 및 원거리 상호 작용을 모두 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-126">To make an object grabbable, assign these two scripts: ManipulationHandler.cs and NearInteractionGrabbable.cs(for direct grab with articulated hand tracking input) ManipulationHandler supports both near and far interactions.</span></span> <span data-ttu-id="d4743-127">HoloLens 2의 두 부분으로 구분 된 손 모양 추적 입력 (근거리), 손 모양 (far), 움직이는 컨트롤러의 빔 (far), HoloLens 응시 커서 & (far)를 사용 하 여 개체를 잡아 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-127">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a><span data-ttu-id="d4743-128">개체 크기를 조정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-128">How to resize an object?</span></span>
<span data-ttu-id="d4743-129">ManipulationHandler.cs는 2 방향 배율/회전을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-129">ManipulationHandler.cs supports two-handed scale/rotation.</span></span> <span data-ttu-id="d4743-130">이는 HoloLens 2의 트레일러 식 입력, HoloLens 1의 응시 + 제스처 입력 및 Windows Mixed Reality 모던 헤드셋의 동작 컨트롤러 입력과 같은 다양 한 입력 형식에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-130">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="d4743-131">MRTK 설명서의 조작 처리기에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="d4743-131">Learn more about Manipulation Handler in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="d4743-132">정밀도를 사용 하 여 개체를 이동 하거나 회전 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-132">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="d4743-133">개체의 크기를 조정 하 고 회전 하는 인터페이스인 경계 상자를 사용할 개체에 BoundingBox.cs를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-133">Assign BoundingBox.cs to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="d4743-134">기본적으로 HoloLens 1 스타일 파란색 핸들 및 와이어를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-134">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="d4743-135">HoloLens 2 스타일 근접 애니메이션 핸들을 사용 하려면 prefabs 및 자료를 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-135">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> <span data-ttu-id="d4743-136">구성 세부 정보는 [경계 상자 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 및 BoundingBoxExamples 장면을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4743-136">Please refer to [Bounding Box documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) and the BoundingBoxExamples.unity scene for the configuration details.</span></span>

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [<span data-ttu-id="d4743-137">MRTK 설명서의 경계 상자에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="d4743-137">Learn more about Bounding Box in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a><span data-ttu-id="d4743-138">개체를 입력 이벤트에 응답 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-138">How to make an object respond to input events?</span></span>
<span data-ttu-id="d4743-139">PointerHandler.cs을 개체에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-139">Assign PointerHandler.cs to an object.</span></span> <span data-ttu-id="d4743-140">검사기에는 이벤트 OnPointerDown (), Onpointerdown (), Onpointerdown (), Onpointerdown ()를 사용 하 여 스크립트에서 이러한 이벤트를 사용할 수 있습니다. IMixedRealityPointerHandler을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-140">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement IMixedRealityPointerHandler.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="d4743-141">MRTK 설명서의 입력 시스템에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="d4743-141">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="d4743-142">시각적 피드백을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-142">How to add visual feedback?</span></span>
<span data-ttu-id="d4743-143">Interactable.cs을 개체에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-143">Assign Interactable.cs to an object.</span></span> <span data-ttu-id="d4743-144">검사기에서 새 테마를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-144">In the inspector, create a new theme.</span></span> <span data-ttu-id="d4743-145">Interactable의 테마 프로필을 사용 하 여 사용 가능한 모든 입력 상호 작용 상태에 시각적 피드백을 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-145">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="d4743-146">Interactable는 셰이더 테마를 비롯 한 다양 한 형식의 테마를 제공 하 여 상호 작용 상태별로 셰이더의 속성을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-146">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="d4743-147">MRTK 설명서의 Interactable에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="d4743-147">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="d4743-148">시각적 피드백에 대 한 또 다른 중요 한 빌딩 블록은 MRTK 표준 셰이더입니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-148">Another important building block for visual feedback is the MRTK Standard Shader.</span></span> <span data-ttu-id="d4743-149">MRTK 표준 셰이더를 사용 하 여 호버 조명 및 근접 조명 같은 시각적 피드백 효과를 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-149">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="d4743-150">MRTK 표준 셰이더는 Unity 표준 셰이더 보다 훨씬 더 많은 계산을 수행 하므로 성능이 뛰어난 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-150">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="d4743-151">새 자료를 만들고 셰이더 ' Mixed Reality Toolkit > Standard '를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-151">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="d4743-152">또는 MRTK 표준 셰이더를 사용 하는 기존 자료 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-152">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="d4743-153">MRTK 설명서의 MRTK 표준 셰이더에 대해 자세히 알아보기</span><span class="sxs-lookup"><span data-stu-id="d4743-153">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="d4743-154">오디오 피드백을 추가 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-154">How to add audio feedback?</span></span>
<span data-ttu-id="d4743-155">개체에 오디오 소스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-155">Add AudioSource to an object.</span></span> <span data-ttu-id="d4743-156">그런 다음 입력 이벤트를 노출 하는 스크립트 (예: Interactable.cs 또는 PointerHandler.cs)에서 개체를 이벤트에 할당 하 고 PlayOneShot ()를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-156">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object to the event and select AudioSource.PlayOneShot().</span></span> <span data-ttu-id="d4743-157">오디오 클립을 사용 하거나 MRTK의 오디오 자산 중 하나를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-157">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a><span data-ttu-id="d4743-158">HoloLens 2 스타일 단추 prefabs를 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-158">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="d4743-159">MRTK는 다양 한 유형의 HoloLens 2 shell (OS) 스타일 단추를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-159">MRTK provides various types of HoloLens 2's shell(OS) style buttons.</span></span> <span data-ttu-id="d4743-160">근접 조명, 압축 상자 및 단추 표면의 ripple 효과와 같은 정교한 시각적 피드백 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-160">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface.</span></span>

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="d4743-161">HoloLens 2 스타일 pressable button prefab 중 하나를 장면으로 끌어다 놓기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-161">Simply drag and drop one of the HoloLens 2 style pressable button prefab into your scene.</span></span> <span data-ttu-id="d4743-162">Prefab는 위에 도입 된 Interactable.cs을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-162">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="d4743-163">Interactable에서 OnClick ()과 같은 노출 된 이벤트를 사용 하 여 작업을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-163">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="d4743-164">MRTK 설명서의 단추 prefabs에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="d4743-164">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a><span data-ttu-id="d4743-165">개체를 팔 로우 하도록 설정 하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-165">How to make an object follow you?</span></span>
<span data-ttu-id="d4743-166">RadialView.cs 스크립트를 개체에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-166">Assign RadialView.cs script to an object.</span></span> <span data-ttu-id="d4743-167">3D 공간에서 다양 한 유형의 개체 위치를 달성할 수 있는 해 찾기 스크립트 시리즈의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-167">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="d4743-168">SolverHandler.cs가 자동으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-168">SolverHandler.cs will be automatically added.</span></span>
<span data-ttu-id="d4743-169">다음은 HoloLens 셸에서 시작 메뉴와 마찬가지로 ' 지연 팔 로우 ' 태그를 활용 하는 RadialView 구성의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-169">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="d4743-170">최소/최대 거리와 최소/최대 보기 각도를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-170">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="d4743-171">아래 예제에서는 15 ° 내에서 0.4 m과 0.8 m 사이에서 개체의 위치를 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-171">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="d4743-172">Lerp 시간 값을 조정 하 여 위치를 더 빠르거나 더 느리게 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-172">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="d4743-173">MRTK 설명서의 Solvers에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="d4743-173">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a><span data-ttu-id="d4743-174">개체의 얼굴을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="d4743-174">How to make an object face you?</span></span>
<span data-ttu-id="d4743-175">Billboard.cs 스크립트를 개체에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-175">Assign Billboard.cs script to an object.</span></span> <span data-ttu-id="d4743-176">사용자의 위치에 관계 없이 항상 직면 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-176">It will always face you, regardless of your position.</span></span> <span data-ttu-id="d4743-177">피벗 축 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4743-177">You can specify the pivot axis option.</span></span>

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="d4743-178">혼합 현실에서 놀라운 환경을 만들 준비가 되셨습니까?</span><span class="sxs-lookup"><span data-stu-id="d4743-178">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="d4743-179">아래 페이지를 방문 하 여 MRTK 및 mixed reality에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="d4743-179">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="d4743-180">저자 소개</span><span class="sxs-lookup"><span data-stu-id="d4743-180">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="d4743-181"><b>동 Yoon 공원</b></span><span class="sxs-lookup"><span data-stu-id="d4743-181"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="d4743-182">UX 디자이너 @Microsoft</span><span class="sxs-lookup"><span data-stu-id="d4743-182">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="d4743-183">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4743-183">See also</span></span>

* [<span data-ttu-id="d4743-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span><span class="sxs-lookup"><span data-stu-id="d4743-184">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="d4743-185">MRTK 설명서 포털</span><span class="sxs-lookup"><span data-stu-id="d4743-185">MRTK Documentation Portal</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="d4743-186">MRTK 시작</span><span class="sxs-lookup"><span data-stu-id="d4743-186">Getting Started with MRTK</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="d4743-187">HoloToolkit to MRTK 포팅 지침</span><span class="sxs-lookup"><span data-stu-id="d4743-187">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
