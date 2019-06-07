---
title: MRTK 버전 2 사용 하 여 시작
description: 새 MRTK 활용 하려는 개발자를 위한
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality 테스트, 혼합 현실 도구 키트, MRTK 버전 2, MRTK, 도구, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 249a0ce0e608410983934b75e399d013e1ff1879
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750383"
---
# <a name="getting-started-with-mrtk-v2"></a><span data-ttu-id="98959-104">MRTK v2를 사용 하 여 시작</span><span class="sxs-lookup"><span data-stu-id="98959-104">Getting started with MRTK v2</span></span>

## <a name="mrtk-getting-started-guide"></a><span data-ttu-id="98959-105">MRTK Getting Started Guide</span><span class="sxs-lookup"><span data-stu-id="98959-105">MRTK Getting Started Guide</span></span>
<span data-ttu-id="98959-106">참조 된 [MRTK 시작 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) MRTK V2를 사용 하 여 시작에 대 한 정보에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="98959-106">See the [MRTK getting started guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) for information on getting started with MRTK V2.</span></span>

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="98959-107">혼합 현실 도구 키트 (MRTK) 란?</span><span class="sxs-lookup"><span data-stu-id="98959-107">What is Mixed Reality Toolkit (MRTK)?</span></span>
<span data-ttu-id="98959-108">MRTK가 처음 출시 되는 HoloLens 이므로 없습니다 경우 현재 해당 하는 개발자 커뮤니티의 어려운 작업 없이 관련 된 멋진 오픈 소스 도구 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="98959-108">The MRTK is an amazing open source toolkit that has been around since the HoloLens was first released, and would not be where it is today without the hard work of our developer community who have contributed to it.</span></span> <span data-ttu-id="98959-109">지난 3 년 동안 개발자 커뮤니티의 피드백을 수신 하 고 가장 큰 관심사를 고려해 야 할 MRTK v2를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="98959-109">Over the past 3 years, we have listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="98959-110">Unity 사용 하 여 MRTK v2는 오픈 소스 플랫폼 간 개발 키트를 사용 하 여 응용 프로그램 혼합된 현실입니다.</span><span class="sxs-lookup"><span data-stu-id="98959-110">The MRTK v2 with Unity is an open source cross-platform development kit for mixed reality applications.</span></span>  <span data-ttu-id="98959-111">Microsoft HoloLens, (VR) 헤드셋을 몰입 형 Windows Mixed Reality 및 OpenVR 플랫폼을 대상으로 하는 응용 프로그램의 개발을 가속화 MRTK 버전 2 것입니다.</span><span class="sxs-lookup"><span data-stu-id="98959-111">MRTK version 2 is intended to accelerate development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets and OpenVR platform.</span></span> <span data-ttu-id="98959-112">프로젝트는 장벽이 혼합된 현실 응용 프로그램을 만들고 우리가 증가 함에 따라 커뮤니티에 다시 기여에 항목을 줄이는 목표로 합니다.</span><span class="sxs-lookup"><span data-stu-id="98959-112">The project is aimed at reducing barriers to entry to create mixed reality applications and contribute back to the community as we all grow.</span></span> 


<span data-ttu-id="98959-113">참조를 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) 에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="98959-113">See the [MRTK documentation portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) to learn more.</span></span>

## <a name="feature-areas"></a><span data-ttu-id="98959-114">기능 영역</span><span class="sxs-lookup"><span data-stu-id="98959-114">Feature areas</span></span>

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="입력된 시스템" width="105"> <span data-ttu-id="98959-116">입력된 시스템</span><span class="sxs-lookup"><span data-stu-id="98959-116">Input System</span></span> 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="추적 (HoloLens 2)를 전달 합니다." width="105"> <span data-ttu-id="98959-118">추적 (HoloLens 2)를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="98959-118">Hand Tracking (HoloLens 2)</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="시선 추적 (HoloLens 2)" width="105">
    <span data-ttu-id="98959-120">시선 추적 (HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="98959-120">Eye Tracking (HoloLens 2)</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="음성 명령 실행" width="105"> <span data-ttu-id="98959-122">음성 명령 실행</span><span class="sxs-lookup"><span data-stu-id="98959-122">Voice Commanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Gaze + 선택 (HoloLens (첫 번째 gen))" width="105">
    <span data-ttu-id="98959-124">Gaze + 선택 (HoloLens (첫 번째 gen))</span><span class="sxs-lookup"><span data-stu-id="98959-124">Gaze + Select (HoloLens (1st gen))</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="텔레포트" width="105"> <span data-ttu-id="98959-126">텔레포트</span><span class="sxs-lookup"><span data-stu-id="98959-126">Teleportation</span></span>
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI 컨트롤" width="105"> <span data-ttu-id="98959-128">UI 컨트롤</span><span class="sxs-lookup"><span data-stu-id="98959-128">UI Controls</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="해 찾기 및 상호 작용" width="105"> <span data-ttu-id="98959-130">해 찾기 및 상호 작용</span><span class="sxs-lookup"><span data-stu-id="98959-130">Solver and Interactions</span></span>
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="컨트롤러 시각화" width="105"> <span data-ttu-id="98959-132">컨트롤러 시각화</span><span class="sxs-lookup"><span data-stu-id="98959-132">Controller Visualization</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="공간 이해" width="105"> <span data-ttu-id="98959-134">공간 이해</span><span class="sxs-lookup"><span data-stu-id="98959-134">Spatial Understanding</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="진단 도구" width="105"> <span data-ttu-id="98959-136">진단 도구</span><span class="sxs-lookup"><span data-stu-id="98959-136">Diagnostic Tool</span></span>
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK 표준 셰이더" width="105"> <span data-ttu-id="98959-138">MRTK 표준 셰이더</span><span class="sxs-lookup"><span data-stu-id="98959-138">MRTK Standard Shader</span></span>
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a><span data-ttu-id="98959-139">UI와 상호 작용 구성 요소</span><span class="sxs-lookup"><span data-stu-id="98959-139">UI and Interaction Building blocks</span></span>

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="단추" width="250"><br>
    <span data-ttu-id="98959-141">**Button**</span><span class="sxs-lookup"><span data-stu-id="98959-141">**Button**</span></span><br>
    <span data-ttu-id="98959-142">HoloLens 2의 명확 하 고 직접을 비롯 한 다양 한 입력된 메서드를 지 원하는 단추 컨트롤 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-142">A button control which supports various input methods including HoloLens 2's articulated hand <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="경계 상자" width="250"><br>
    <span data-ttu-id="98959-144">**경계 상자**</span><span class="sxs-lookup"><span data-stu-id="98959-144">**Bounding Box**</span></span><br>
    <span data-ttu-id="98959-145">3D 공간에서 개체를 조작 하기 위한 표준 UI <a/></span><span class="sxs-lookup"><span data-stu-id="98959-145">Standard UI for manipulating objects in 3D space <a/></span></span>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="조작 처리기" width="250"><br>
    <span data-ttu-id="98959-147">**조작 처리기**</span><span class="sxs-lookup"><span data-stu-id="98959-147">**Manipulation Handler**</span></span><br>
    <span data-ttu-id="98959-148">하나 또는 두 개의 실습을 사용 하 여 개체를 조작 하기 위한 스크립트 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-148">Script for manipulating objects with one or two hands <a/></span></span>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="슬레이트" width="250"><br>
    <span data-ttu-id="98959-150">**슬레이트**</span><span class="sxs-lookup"><span data-stu-id="98959-150">**Slate**</span></span> <br>
    <span data-ttu-id="98959-151">명확 하 고 직접 입력을 사용 하 여 스크롤을 지 원하는 스타일 2D 평면 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-151">2D style plane which supports scrolling with articulated hand input <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="시스템 키보드" width="250"><br>
    <span data-ttu-id="98959-153">**시스템 키보드**</span><span class="sxs-lookup"><span data-stu-id="98959-153">**System Keyboard**</span></span><br>
    <span data-ttu-id="98959-154">Unity에서 시스템 키보드를 사용 하는 예제 스크립트 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-154">Example script of using the system keyboard in Unity <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="상호 작용할 수 없는" width="250"><br>
     <span data-ttu-id="98959-156">**상호 작용할 수 없는**</span><span class="sxs-lookup"><span data-stu-id="98959-156">**Interactable**</span></span> <br>
     <span data-ttu-id="98959-157">시각적 상태 및 테마 지원을 사용 하 여 상호 작용할 수 없는 개체를 만들기 위한 스크립트 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-157">A script for making objects interactable with visual states and theme support <a/></span></span>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="해 찾기" width="250"><br>
    <span data-ttu-id="98959-159">**해 찾기**</span><span class="sxs-lookup"><span data-stu-id="98959-159">**Solver**</span></span> <br>
    <span data-ttu-id="98959-160">다양 한 개체 tag-along, 본문 잠금, 상수 뷰 크기 및 화면 자기와 같은 위치 지정 동작 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-160">Various object positioning behaviors such as tag-along, body-lock, constant view size and surface magnetism <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="개체 컬렉션" width="250"><br>
    <span data-ttu-id="98959-162">**개체 컬렉션**</span><span class="sxs-lookup"><span data-stu-id="98959-162">**Object Collection**</span></span><br>
    <span data-ttu-id="98959-163">레이아웃을 3 차원 도형에 있는 개체의 배열에 대 한 스크립트 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-163">Script for lay out an array of objects in a three-dimensional shape <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Tooltip" width="250">  <br>
    <span data-ttu-id="98959-165">**Tooltip**</span><span class="sxs-lookup"><span data-stu-id="98959-165">**Tooltip**</span></span><br>
    <span data-ttu-id="98959-166">컨트롤러 동작 및 개체에 레이블을 지정 하기 위해 사용할 수 있는 유연한 앵커/피벗 시스템을 사용 하 여 UI 주석 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-166">Annotation UI with flexible anchor/pivot system which can be used for labeling motion controllers and object <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="앱 바" width="250"><br>
    <span data-ttu-id="98959-168">**앱 바**</span><span class="sxs-lookup"><span data-stu-id="98959-168">**App Bar**</span></span><br>
    <span data-ttu-id="98959-169">경계 상자 수동 정품 인증에 대 한 UI <a/></span><span class="sxs-lookup"><span data-stu-id="98959-169">UI for Bounding Box's manual activation <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="포인터" width="250"><br>
    <span data-ttu-id="98959-171">**포인터**</span><span class="sxs-lookup"><span data-stu-id="98959-171">**Pointers**</span></span><br>
    <span data-ttu-id="98959-172">다양 한 유형의 포인터에 대해 알아봅니다 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-172">Learn about various types of pointers <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="손끝 시각화" width="250"><br>
     <span data-ttu-id="98959-174">**손끝 시각화**</span><span class="sxs-lookup"><span data-stu-id="98959-174">**Fingertip Visualization**</span></span><br>
     <span data-ttu-id="98959-175">직접 상호 작용에 대 한 신뢰도 개선 하는 손끝에서 visual 유도성 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-175">Visual affordance on the fingertip which improves the confidence for the direct interaction <a/></span></span>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="슬라이더" width="250"><br>
    <span data-ttu-id="98959-177">**슬라이더**</span><span class="sxs-lookup"><span data-stu-id="98959-177">**Slider**</span></span><br>
    <span data-ttu-id="98959-178">슬라이더 UI 조정에 대 한 지원 직접 직접 상호 작용 추적 값 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-178">Slider UI for adjusting values supporting direct hand tracking interaction <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 표준 셰이더" width="250"><br>
    <span data-ttu-id="98959-180">**MRTK 표준 셰이더**</span><span class="sxs-lookup"><span data-stu-id="98959-180">**MRTK Standard Shader**</span></span><br>
    <span data-ttu-id="98959-181">MRTK의 표준 셰이더 성능을 사용 하 여 다양 한 Fluent 디자인 요소를 지원합니다. <a/></span><span class="sxs-lookup"><span data-stu-id="98959-181">MRTK's Standard shader supports various Fluent design elements with performance <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="직접 공동 체이서" width="250"><br>
     <span data-ttu-id="98959-183">**직접 공동 체이서**</span><span class="sxs-lookup"><span data-stu-id="98959-183">**Hand Joint Chaser**</span></span><br>
     <span data-ttu-id="98959-184">개체를 직접이 음 연결할 해결 기를 사용 하는 방법을 보여 줍니다. <a/></span><span class="sxs-lookup"><span data-stu-id="98959-184">Demonstrates how to use Solver to attach objects to the hand joints <a/></span></span>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="시선 추적: 대상 선택" width="250"><br>
    <span data-ttu-id="98959-186">**시선 추적: 대상 선택**</span><span class="sxs-lookup"><span data-stu-id="98959-186">**Eye Tracking: Target Selection**</span></span><br>
    <span data-ttu-id="98959-187">눈, 음성 및 빠르고 손쉽게 홀로그램 장면에서 선택 하려면 입력 직접 결합 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-187">Combine eyes, voice and hand input to quickly and effortlessly select holograms across your scene <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="시선 추적: 탐색" width="250"><br>
    <span data-ttu-id="98959-189">**시선 추적: 탐색**</span><span class="sxs-lookup"><span data-stu-id="98959-189">**Eye Tracking: Navigation**</span></span><br>
    <span data-ttu-id="98959-190">자동 스크롤 텍스트 또는에서 원하는 내용을 기준으로 포커스가 있는 콘텐츠를 신속 하 게 확대/축소 하는 방법을 알아봅니다 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-190">Learn how to auto scroll text or fluently zoom into focused content based on what you are looking at <a/></span></span>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="시선 추적: 열 지도" width="250"><br>
    <span data-ttu-id="98959-192">**시선 추적: 열 지도**</span><span class="sxs-lookup"><span data-stu-id="98959-192">**Eye Tracking: Heat Map**</span></span><br>
    <span data-ttu-id="98959-193">로깅에 대 한 예제를 로드 하 고 어떤 사용자가 시각화 살펴 보았습니다 앱에서 <a/></span><span class="sxs-lookup"><span data-stu-id="98959-193">Examples for logging, loading and visualizing what users have been looking at in your app <a/></span></span>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a><span data-ttu-id="98959-194">MRTK v2에 대 한 최소 요구 사항</span><span class="sxs-lookup"><span data-stu-id="98959-194">Minimum Requirement for MRTK v2</span></span>
* <span data-ttu-id="98959-195">Unity 2018.3.x</span><span class="sxs-lookup"><span data-stu-id="98959-195">Unity 2018.3.x</span></span>
* <span data-ttu-id="98959-196">Microsoft Visual Studio 2017 이상</span><span class="sxs-lookup"><span data-stu-id="98959-196">Microsoft Visual Studio 2017 or later</span></span>
* <span data-ttu-id="98959-197">Windows SDK 18362+</span><span class="sxs-lookup"><span data-stu-id="98959-197">Windows SDK 18362+</span></span> 
* <span data-ttu-id="98959-198">Windows 10 1803 이상</span><span class="sxs-lookup"><span data-stu-id="98959-198">Windows 10 1803 or later</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="98959-199">MRTK v2를 사용 하 여 새</span><span class="sxs-lookup"><span data-stu-id="98959-199">New with MRTK v2</span></span>
<span data-ttu-id="98959-200">노력의 일환으로 이러한 플랫폼 도구 스트레스 하고자 합니다.</span><span class="sxs-lookup"><span data-stu-id="98959-200">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="98959-201">사실, 받은 편지함 경험 설치 환경 (OOBE) 등이 혼합 현실 학습 응용 프로그램을 개발 하려면 MRTK 버전 2 활용 했습니다.</span><span class="sxs-lookup"><span data-stu-id="98959-201">In fact, we leveraged MRTK version 2 to develop our inbox experiences, such as the setup experience (OOBE) and our Mixed Reality Learning application.</span></span>  <span data-ttu-id="98959-202">플랫폼에서 개발 하는 가장 좋은 방법은 것 때문에 먼저 MRTK를 통해서도 새 HoloLens 2 기능을 확인 하려면 예상할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98959-202">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="98959-203">모듈식</span><span class="sxs-lookup"><span data-stu-id="98959-203">Modular</span></span>
<span data-ttu-id="98959-204">빌드 했습니다이 모듈식 방식으로 프로젝트에 도구 키트의 모든 비트를 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="98959-204">We have built it in a modular way, so that you do not need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="98959-205">이 실제로 몇 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98959-205">There are actually a few benefits to this.</span></span>  <span data-ttu-id="98959-206">또한 프로젝트 크기를 작게 유지 뿐만 관리 하기가 쉬워집니다.</span><span class="sxs-lookup"><span data-stu-id="98959-206">It keeps your project size smaller, as well as makes it easier to manage.</span></span>  <span data-ttu-id="98959-207">위쪽에, 있기 때문에 스크립트 가능한 개체를 사용 하 여 빌드되어 인터페이스 제어 되 고도 포함 되어 있는 다른 서비스, 시스템 및 플랫폼을 지원 하기 위해 고유한 구성 요소를 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98959-207">On top of that, because it’s built with scriptable objects and is interface driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>


### <a name="cross-platform"></a><span data-ttu-id="98959-208">플랫폼 간</span><span class="sxs-lookup"><span data-stu-id="98959-208">Cross-platform</span></span>
<span data-ttu-id="98959-209">다른 플랫폼의 설명 하자면이 플랫폼 간 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="98959-209">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="98959-210">및 다른 플랫폼 빌드 대상 전환할 때 중단 toolkit 코드 없음 확인 했 동안 모든 단일 플랫폼은 기본적으로 지원 되는 뜻입니다.</span><span class="sxs-lookup"><span data-stu-id="98959-210">And while this doesn’t mean every single platform is supported out of the box, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="98959-211">견고성 및 모듈식 디자인을 사용 하 여 확장성을 설정 합니다 ARCore, ARKit 및 OpenVR 같은 여러 플랫폼을 지원할 수에 대 한 적절 한 경로에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98959-211">The robustness and extensibility with the modular design sets you up on a good path to be able to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>


### <a name="performant"></a><span data-ttu-id="98959-212">고성능</span><span class="sxs-lookup"><span data-stu-id="98959-212">Performant</span></span>
<span data-ttu-id="98959-213">모바일 플랫폼을 사용 했습니다 생성 성능을 염두에서를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="98959-213">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="98959-214">이 매우 중요 하 고 도구는 수에 대해 작동 하도록 하지 확인 하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="98959-214">This is super important, and we wanted to ensure that the tools are not going to work against you.</span></span>


## <a name="see-also"></a><span data-ttu-id="98959-215">참조</span><span class="sxs-lookup"><span data-stu-id="98959-215">See also</span></span>
* [<span data-ttu-id="98959-216">MRTK 시작 가이드</span><span class="sxs-lookup"><span data-stu-id="98959-216">MRTK getting started guide</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [<span data-ttu-id="98959-217">MRTK 설명서 홈</span><span class="sxs-lookup"><span data-stu-id="98959-217">MRTK documentation home</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="98959-218">도구 설치</span><span class="sxs-lookup"><span data-stu-id="98959-218">Install the tools</span></span>](install-the-tools.md)
* [<span data-ttu-id="98959-219">HTK/MRTK에서 MRTK 버전 2로 이식</span><span class="sxs-lookup"><span data-stu-id="98959-219">Porting from HTK/MRTK to MRTK version 2</span></span>](mrtk-porting-guide.md)
