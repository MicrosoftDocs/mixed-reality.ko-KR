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
# <a name="getting-started-with-mrtk-v2"></a>MRTK v2를 사용 하 여 시작

## <a name="mrtk-getting-started-guide"></a>MRTK Getting Started Guide
참조 된 [MRTK 시작 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) MRTK V2를 사용 하 여 시작에 대 한 정보에 대 한 합니다.

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>혼합 현실 도구 키트 (MRTK) 란?
MRTK가 처음 출시 되는 HoloLens 이므로 없습니다 경우 현재 해당 하는 개발자 커뮤니티의 어려운 작업 없이 관련 된 멋진 오픈 소스 도구 키트입니다. 지난 3 년 동안 개발자 커뮤니티의 피드백을 수신 하 고 가장 큰 관심사를 고려해 야 할 MRTK v2를 작성 합니다.  

Unity 사용 하 여 MRTK v2는 오픈 소스 플랫폼 간 개발 키트를 사용 하 여 응용 프로그램 혼합된 현실입니다.  Microsoft HoloLens, (VR) 헤드셋을 몰입 형 Windows Mixed Reality 및 OpenVR 플랫폼을 대상으로 하는 응용 프로그램의 개발을 가속화 MRTK 버전 2 것입니다. 프로젝트는 장벽이 혼합된 현실 응용 프로그램을 만들고 우리가 증가 함에 따라 커뮤니티에 다시 기여에 항목을 줄이는 목표로 합니다. 


참조를 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) 에 대해 자세히 알아보세요.

## <a name="feature-areas"></a>기능 영역

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="입력된 시스템" width="105"> 입력된 시스템 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="추적 (HoloLens 2)를 전달 합니다." width="105"> 추적 (HoloLens 2)를 전달 합니다.
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="시선 추적 (HoloLens 2)" width="105">
    시선 추적 (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="음성 명령 실행" width="105"> 음성 명령 실행
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="Gaze + 선택 (HoloLens (첫 번째 gen))" width="105">
    Gaze + 선택 (HoloLens (첫 번째 gen))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="텔레포트" width="105"> 텔레포트
    :::column-end:::
:::row-end:::


:::row:::
    :::column:::
    <img src="images/MRTK_Icon_UIControls.png" alt="UI Controls" title="UI 컨트롤" width="105"> UI 컨트롤
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_Solver.png" alt="Solver and Interactions" title="해 찾기 및 상호 작용" width="105"> 해 찾기 및 상호 작용
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_ControllerVisualization.png" alt="Controller Visualization" title="컨트롤러 시각화" width="105"> 컨트롤러 시각화
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_SpatialUnderstanding.png" alt="Spatial Understanding" title="공간 이해" width="105"> 공간 이해
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Diagnostics.png" alt="Diagnostic Tool" title="진단 도구" width="105"> 진단 도구
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_StandardShader.png" alt="MRTK Standard Shader" title="MRTK 표준 셰이더" width="105"> MRTK 표준 셰이더
    :::column-end:::
:::row-end:::

## <a name="ui-and-interaction-building-blocks"></a>UI와 상호 작용 구성 요소

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="단추" width="250"><br>
    **Button**<br>
    HoloLens 2의 명확 하 고 직접을 비롯 한 다양 한 입력된 메서드를 지 원하는 단추 컨트롤 <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="경계 상자" width="250"><br>
    **경계 상자**<br>
    3D 공간에서 개체를 조작 하기 위한 표준 UI <a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="조작 처리기" width="250"><br>
    **조작 처리기**<br>
    하나 또는 두 개의 실습을 사용 하 여 개체를 조작 하기 위한 스크립트 <a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="슬레이트" width="250"><br>
    **슬레이트** <br>
    명확 하 고 직접 입력을 사용 하 여 스크롤을 지 원하는 스타일 2D 평면 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="시스템 키보드" width="250"><br>
    **시스템 키보드**<br>
    Unity에서 시스템 키보드를 사용 하는 예제 스크립트 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="상호 작용할 수 없는" width="250"><br>
     **상호 작용할 수 없는** <br>
     시각적 상태 및 테마 지원을 사용 하 여 상호 작용할 수 없는 개체를 만들기 위한 스크립트 <a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="해 찾기" width="250"><br>
    **해 찾기** <br>
    다양 한 개체 tag-along, 본문 잠금, 상수 뷰 크기 및 화면 자기와 같은 위치 지정 동작 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="개체 컬렉션" width="250"><br>
    **개체 컬렉션**<br>
    레이아웃을 3 차원 도형에 있는 개체의 배열에 대 한 스크립트 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="Tooltip" width="250">  <br>
    **Tooltip**<br>
    컨트롤러 동작 및 개체에 레이블을 지정 하기 위해 사용할 수 있는 유연한 앵커/피벗 시스템을 사용 하 여 UI 주석 <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="앱 바" width="250"><br>
    **앱 바**<br>
    경계 상자 수동 정품 인증에 대 한 UI <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="포인터" width="250"><br>
    **포인터**<br>
    다양 한 유형의 포인터에 대해 알아봅니다 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="손끝 시각화" width="250"><br>
     **손끝 시각화**<br>
     직접 상호 작용에 대 한 신뢰도 개선 하는 손끝에서 visual 유도성 <a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="슬라이더" width="250"><br>
    **슬라이더**<br>
    슬라이더 UI 조정에 대 한 지원 직접 직접 상호 작용 추적 값 <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 표준 셰이더" width="250"><br>
    **MRTK 표준 셰이더**<br>
    MRTK의 표준 셰이더 성능을 사용 하 여 다양 한 Fluent 디자인 요소를 지원합니다. <a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="직접 공동 체이서" width="250"><br>
     **직접 공동 체이서**<br>
     개체를 직접이 음 연결할 해결 기를 사용 하는 방법을 보여 줍니다. <a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="시선 추적: 대상 선택" width="250"><br>
    **시선 추적: 대상 선택**<br>
    눈, 음성 및 빠르고 손쉽게 홀로그램 장면에서 선택 하려면 입력 직접 결합 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="시선 추적: 탐색" width="250"><br>
    **시선 추적: 탐색**<br>
    자동 스크롤 텍스트 또는에서 원하는 내용을 기준으로 포커스가 있는 콘텐츠를 신속 하 게 확대/축소 하는 방법을 알아봅니다 <a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="시선 추적: 열 지도" width="250"><br>
    **시선 추적: 열 지도**<br>
    로깅에 대 한 예제를 로드 하 고 어떤 사용자가 시각화 살펴 보았습니다 앱에서 <a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>MRTK v2에 대 한 최소 요구 사항
* Unity 2018.3.x
* Microsoft Visual Studio 2017 이상
* Windows SDK 18362+ 
* Windows 10 1803 이상

## <a name="new-with-mrtk-v2"></a>MRTK v2를 사용 하 여 새
노력의 일환으로 이러한 플랫폼 도구 스트레스 하고자 합니다.  사실, 받은 편지함 경험 설치 환경 (OOBE) 등이 혼합 현실 학습 응용 프로그램을 개발 하려면 MRTK 버전 2 활용 했습니다.  플랫폼에서 개발 하는 가장 좋은 방법은 것 때문에 먼저 MRTK를 통해서도 새 HoloLens 2 기능을 확인 하려면 예상할 수 있습니다. 

### <a name="modular"></a>모듈식
빌드 했습니다이 모듈식 방식으로 프로젝트에 도구 키트의 모든 비트를 수행할 필요가 없습니다.  이 실제로 몇 가지 이점이 있습니다.  또한 프로젝트 크기를 작게 유지 뿐만 관리 하기가 쉬워집니다.  위쪽에, 있기 때문에 스크립트 가능한 개체를 사용 하 여 빌드되어 인터페이스 제어 되 고도 포함 되어 있는 다른 서비스, 시스템 및 플랫폼을 지원 하기 위해 고유한 구성 요소를 대체할 수 있습니다.


### <a name="cross-platform"></a>플랫폼 간
다른 플랫폼의 설명 하자면이 플랫폼 간 지원 합니다.  및 다른 플랫폼 빌드 대상 전환할 때 중단 toolkit 코드 없음 확인 했 동안 모든 단일 플랫폼은 기본적으로 지원 되는 뜻입니다.  견고성 및 모듈식 디자인을 사용 하 여 확장성을 설정 합니다 ARCore, ARKit 및 OpenVR 같은 여러 플랫폼을 지원할 수에 대 한 적절 한 경로에 있습니다.


### <a name="performant"></a>고성능
모바일 플랫폼을 사용 했습니다 생성 성능을 염두에서를 사용 하 여 합니다.  이 매우 중요 하 고 도구는 수에 대해 작동 하도록 하지 확인 하려고 했습니다.


## <a name="see-also"></a>참조
* [MRTK 시작 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK 설명서 홈](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [도구 설치](install-the-tools.md)
* [HTK/MRTK에서 MRTK 버전 2로 이식](mrtk-porting-guide.md)
