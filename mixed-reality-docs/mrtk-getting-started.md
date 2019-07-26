---
title: MRTK 버전 2 시작
description: MRTK를 활용 하려는 새로운 개발자
author: Yoyoz
ms.author: Yoyoz
ms.date: 05/15/19
ms.topic: article
keywords: Windows Mixed Reality, 테스트, 혼합 현실 도구 키트, MRTK 버전 2, MRTK, 도구, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 7eded2c766765a5ccebf741eed2f8b7fe8f65a93
ms.sourcegitcommit: 76a7aa6e64e114b63ace058dd6d6d662b3c9f09e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68507926"
---
# <a name="getting-started-with-mrtk-v2"></a>MRTK v2 시작

## <a name="mrtk-getting-started-guide"></a>MRTK 시작 가이드
MRTK V2 시작에 대 한 자세한 내용은 [mrtk 시작 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) 를 참조 하세요.

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>혼합 현실 도구 키트 (MRTK) 란?
MRTK는 HoloLens가 처음 출시 된 후에 발생 하는 놀라운 오픈 소스 도구 키트 이며, 오늘날 개발자 커뮤니티의 하드 작업 없이는 오늘날 어디에서 나 사용할 수 없습니다. 지난 3 년간 개발자 커뮤니티의 피드백을 수신 하 고 MRTK v 2를 구축 하 여 가장 중요 한 문제를 고려 했습니다.  

MRTK v2 Unity는 혼합 현실 응용 프로그램을 위한 오픈 소스 플랫폼 간 개발 키트입니다.  MRTK 버전 2는 Microsoft HoloLens를 대상으로 하는 응용 프로그램의 개발을 가속화 하기 위한 것입니다 (Windows Mixed Reality 몰입 (VR) 헤드셋 및 OpenVR 플랫폼). 이 프로젝트는 혼합 현실 애플리케이션을 만들기 위한 진입 장벽을 낮추고 커뮤니티에 다시 기여하는 것을 목표로 합니다. 


자세히 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) 을 참조 하세요.

## <a name="feature-areas"></a>기능 영역

:::row:::
    :::column:::
    <img src="images/MRTK_Icon_InputSystem.png" alt="Input system" title="입력 시스템" width="105"> 입력 시스템 
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_HandTracking.png" alt="Hand Tracking (HoloLens 2)" title="손으로 추적 (HoloLens 2)" width="105"> 손으로 추적 (HoloLens 2)
    :::column-end:::
    :::column:::
    <img src="images/MRTK_Icon_EyeTracking.png" alt="Eye Tracking (HoloLens 2)" title="아이 추적 (HoloLens 2)" width="105">
    아이 추적 (HoloLens 2)
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_VoiceCommand.png" alt="Voice Commanding" title="음성 명령" width="105"> 음성 명령
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_GazeSelect.png" alt="Gaze + Select (HoloLens (1st gen))" title="응시 + Select (HoloLens (첫 번째 gen))" width="105">
    응시 + Select (HoloLens (첫 번째 gen))
    :::column-end:::
        :::column:::
    <img src="images/MRTK_Icon_Teleportation.png" alt="Teleportation" title="Teleportation" width="105"> Teleportation
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

## <a name="ui-and-interaction-building-blocks"></a>UI 및 상호 작용 구성 요소

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html"><img src="images/MRTK_Button_Main.png" alt="Button" title="단추" width="250"><br>
    **Button**<br>
    HoloLens 2의 트레일러를 포함 하는 다양 한 입력 메서드를 지 원하는 button 컨트롤입니다.<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html"><img src="images/MRTK_BoundingBox_Main.png" alt="Bounding Box" title="경계 상자" width="250"><br>
    **경계 상자**<br>
    3D 공간에서 개체 조작을 위한 표준 UI<a/>
    :::column-end:::
    :::column:::
<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html"><img src="images/MRTK_Manipulation_Main.png" alt="Manipulation Handler" title="조작 처리기" width="250"><br>
    **조작 처리기**<br>
    하나 또는 두 개의 손을 사용 하 여 개체를 조작 하는 스크립트<a/>
    :::column-end:::
:::row-end:::    
    
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Slate.html"><img src="images/MRTK_Slate_Main.png" alt="Slate" title="찬" width="250"><br>
    **찬** <br>
    트레일러 식 입력으로 스크롤을 지 원하는 2D 스타일 평면<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_SystemKeyboard.html"><img src="images/MRTK_SystemKeyboard_Main.png" alt="System Keyboard" title="시스템 키보드" width="250"><br>
    **시스템 키보드**<br>
    Unity에서 시스템 키보드를 사용 하는 예제 스크립트<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html"><img src="images/InteractableExamples.png" alt="Interactable" title="Interactable" width="250"><br>
     **Interactable** <br>
     시각적 상태 및 테마 지원과 함께 개체를 interactable 하는 스크립트<a/>
    :::column-end:::
:::row-end:::       

:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html"><img src="images/MRTK_Solver_Main.png" alt="Solver" title="찾기에서" width="250"><br>
    **찾기에서** <br>
    태그 동반, 본문 잠금, 상수 보기 크기 및 표면 자기와 같은 다양 한 개체 위치 지정 동작<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html"><img src="images/MRTK_ObjectCollection_Main.png" alt="Object Collection" title="개체 컬렉션" width="250"><br>
    **개체 컬렉션**<br>
    3 차원 모양의 개체 배열을 레이아웃 하는 스크립트<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Tooltip.html"><img src="images/MRTK_Tooltip_Main.png" alt="Tooltip" title="도구 설명" width="250">  <br>
    **놓으면**<br>
    동작 컨트롤러 및 개체에 레이블을 지정 하는 데 사용할 수 있는 유연한 앵커/피벗 시스템을 포함 하는 주석 UI<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html"><img src="images/MRTK_AppBar_Main.png" alt="App Bar" title="앱 바" width="250"><br>
    **앱 바**<br>
    경계 상자의 수동 활성화를 위한 UI<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Pointers.html"><img src="images/MRTK_Pointer_Main.png" alt="Pointers" title="포인터" width="250"><br>
    **포인터**<br>
    다양 한 종류의 포인터에 대해 알아보기<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_FingertipVisualization.html"><img src="images/MRTK_FingertipVisualization_Main.png" alt="Fingertip Visualization" title="Fingertip 시각화" width="250"><br>
     **Fingertip 시각화**<br>
     직접 상호 작용에 대 한 신뢰도를 향상 시키는 fingertip의 시각적 affordance<a/>
    :::column-end:::
:::row-end:::   

:::row:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_Sliders.md"><img src="images/MRTK_UX_Slider_Main.jpg" alt="Slider" title="슬라이더" width="250"><br>
    **슬라이더**<br>
    직접 추적 상호 작용을 지 원하는 값을 조정 하기 위한 슬라이더 UI<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md"><img src="images/MRTK_StandardShader.jpg" alt="MRTK Standard Shader" title="MRTK 표준 셰이더" width="250"><br>
    **MRTK 표준 셰이더**<br>
    MRTK의 표준 셰이더는 성능으로 다양 한 흐름 디자인 요소를 지원 합니다.<a/>
    :::column-end:::
    :::column:::
    <a href="https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_HandJointChaser.md"><img src="images/MRTK_HandJointChaser_Main.jpg" alt="Hand Joint Chaser" title="핸드 조인트 체이서" width="250"><br>
     **핸드 조인트 체이서**<br>
     해 찾기를 사용 하 여 개체를 직접 조인트에 연결 하는 방법을 보여 줍니다.<a/>
    :::column-end:::
:::row-end:::   
        
:::row:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_TargetSelection.html"><img src="images/mrtk_et_targetselect.png" alt="Eye Tracking: Target Selection" title="눈 추적: 대상 선택" width="250"><br>
    **눈 추적: 대상 선택**<br>
    눈, 음성 및 손 입력을 결합 하 여 장면 전체의 holograms을 빠르고 간편 하 게 선택<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Navigation.html"><img src="images/mrtk_et_navigation.png" alt="Eye Tracking: Navigation" title="눈 추적: 탐색" width="250"><br>
    **눈 추적: 내비게이션**<br>
    표시 되는 내용에 따라 텍스트를 자동으로 운용 확대/축소 하는 방법에 대해 알아봅니다.<a/>
    :::column-end:::
    :::column:::
    <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Visualization.html"><img src="images/mrtk_et_heatmaps.png" alt="Eye Tracking: Heat Map" title="눈 추적: 열 지도" width="250"><br>
    **눈 추적: 열 지도**<br>
    사용자의 앱에서 보고 있는 사용자를 기록, 로드 및 시각화 하는 예제<a/>
    :::column-end:::
:::row-end:::           


## <a name="minimum-requirement-for-mrtk-v2"></a>MRTK v 2의 최소 요구 사항
* Unity 2018.3.x
* Microsoft Visual Studio 2017 이상
* Windows SDK 18362 + 
* Windows 10 1803 이상

## <a name="new-with-mrtk-v2"></a>MRTK v2에서 새로 만들기
이러한 플랫폼 도구에 대 한 약속을 스트레스 하고자 합니다.  실제로는 MRTK 버전 2를 활용 하 여 설치 환경 (OOBE) 및 혼합 현실 학습 응용 프로그램 등의 수신함 환경을 개발 했습니다.  플랫폼에서 개발 하는 것이 가장 좋은 방법 이라고 생각 하기 때문에 MRTK를 통해 처음에 제공 되는 새로운 HoloLens 2 기능이 표시 될 수도 있습니다. 

### <a name="modular"></a>방식
이를 모듈식 방식으로 빌드하여 프로젝트에 도구 키트의 모든 비트를 사용할 필요가 없습니다.  실제로 몇 가지 이점이 있습니다.  이를 통해 프로젝트 크기를 더 작게 유지 하 고 쉽게 관리할 수 있습니다.  그 위에는 스크립트 가능한 개체를 사용 하 여 빌드되고 인터페이스를 기반으로 하기 때문에 사용자 고유의 구성 요소를 대체 하 여 다른 서비스, 시스템 및 플랫폼을 지원할 수도 있습니다.


### <a name="cross-platform"></a>플랫폼 간
다른 플랫폼의 경우 플랫폼 간 지원이 제공 됩니다.  이는 모든 단일 플랫폼이 기본적으로 지원 되는 것을 의미 하지는 않지만 빌드 대상을 다른 플랫폼으로 전환 하면 도구 키트 코드가 중단 되지 않도록 합니다.  모듈식 디자인을 사용한 견고성과 확장성은 ARCore, Arcore 및 OpenVR와 같은 여러 플랫폼을 지원할 수 있는 좋은 경로를 설정 합니다.


### <a name="performant"></a>성능과
모바일 플랫폼을 사용 하 여 작업 하는 경우 성능을 염두에 두어야 합니다.  이는 매우 중요 하며, 도구가 사용자에 대해 작동 하지 않도록 하는 데 필요 합니다.


## <a name="see-also"></a>참조
* [MRTK 시작 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [MRTK 설명서 홈](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [도구 설치](install-the-tools.md)
* [HTK/MRTK에서 MRTK 버전 2로 포팅](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
