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
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>MRTK 101: 기본 상호 작용을 위해 Mixed Reality Toolkit Unity를 사용 하는 방법 (HoloLens 2, HoloLens, Windows Mixed Reality, 오픈 VR)

![MRTK](images/MRTK101/MRTK101Cover.png)

MRTK를 사용 하 여 혼합 현실에서 가장 널리 사용 되는 일반적인 상호 작용 패턴을 구현 하는 방법에 대해 알아봅니다.

- Unity 편집기에서 입력 상호 작용을 시뮬레이트하는 방법
- 개체를 잡아 이동 하는 방법
- 개체 크기를 조정 하는 방법
- 정밀도를 사용 하 여 개체를 이동 하거나 회전 하는 방법
- 개체를 입력 이벤트에 응답 하도록 설정 하는 방법
- 시각적 피드백을 추가 하는 방법
- 오디오 피드백을 추가 하는 방법
- HoloLens 2 스타일 단추 prefabs를 사용 하는 방법
- 개체를 팔 로우 하도록 설정 하는 방법
- 개체의 얼굴을 만드는 방법

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>Unity 편집기에서 입력 상호 작용을 시뮬레이트하는 방법
MRTK는 편집기에서 입력 시뮬레이션을 지원 합니다. Unity의 재생 단추를 클릭 하 여 장면을 실행 하기만 하면 됩니다. 이러한 키를 사용 하 여 입력을 시뮬레이트합니다.
W, A, S, D 키를 눌러 카메라를 이동 합니다.
마우스 오른쪽 단추를 누른 상태에서 위로 마우스를 이동 합니다.
시뮬레이션 된 손을 가져오려면 스페이스바 (오른쪽) 또는 왼쪽 Shift 키 (왼쪽)를 눌러 시뮬레이션 된 손을 보기에 유지 하 고, T 또는 Y 키를 눌러 시뮬레이션 된 손을 회전 하거나, Q 또는 E (가로)/R 또는 F (수직)를 누릅니다.

- [MRTK 설명서의 입력 시뮬레이션에 대 한 자세한 정보](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>개체를 잡아 이동 하는 방법
개체를 grabbable 하려면 다음 두 스크립트를 할당 합니다. ManipulationHandler.cs 및 NearInteractionGrabbable (두 부분으로 된 직접 잡기의 경우) ManipulationHandler는 근거리 및 원거리 상호 작용을 모두 지원 합니다. HoloLens 2의 두 부분으로 구분 된 손 모양 추적 입력 (근거리), 손 모양 (far), 움직이는 컨트롤러의 빔 (far), HoloLens 응시 커서 & (far)를 사용 하 여 개체를 잡아 이동할 수 있습니다.

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>개체 크기를 조정 하는 방법
ManipulationHandler.cs는 2 방향 배율/회전을 지원 합니다. 이는 HoloLens 2의 트레일러 식 입력, HoloLens 1의 응시 + 제스처 입력 및 Windows Mixed Reality 모던 헤드셋의 동작 컨트롤러 입력과 같은 다양 한 입력 형식에서 작동 합니다.

- [MRTK 설명서의 조작 처리기에 대 한 자세한 정보](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>정밀도를 사용 하 여 개체를 이동 하거나 회전 하는 방법
개체의 크기를 조정 하 고 회전 하는 인터페이스인 경계 상자를 사용할 개체에 BoundingBox.cs를 할당 합니다. 기본적으로 HoloLens 1 스타일 파란색 핸들 및 와이어를 표시 합니다. HoloLens 2 스타일 근접 애니메이션 핸들을 사용 하려면 prefabs 및 자료를 할당 해야 합니다. 구성 세부 정보는 [경계 상자 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 및 BoundingBoxExamples 장면을 참조 하세요.

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [MRTK 설명서의 경계 상자에 대 한 자세한 정보](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>개체를 입력 이벤트에 응답 하도록 설정 하는 방법
PointerHandler.cs을 개체에 할당 합니다. 검사기에는 이벤트 OnPointerDown (), Onpointerdown (), Onpointerdown (), Onpointerdown ()를 사용 하 여 스크립트에서 이러한 이벤트를 사용할 수 있습니다. IMixedRealityPointerHandler을 구현 합니다.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [MRTK 설명서의 입력 시스템에 대 한 자세한 정보](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>시각적 피드백을 추가 하는 방법
Interactable.cs을 개체에 할당 합니다. 검사기에서 새 테마를 만듭니다. Interactable의 테마 프로필을 사용 하 여 사용 가능한 모든 입력 상호 작용 상태에 시각적 피드백을 쉽게 추가할 수 있습니다.

<img alt="PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactable는 셰이더 테마를 비롯 한 다양 한 형식의 테마를 제공 하 여 상호 작용 상태별로 셰이더의 속성을 제어할 수 있습니다.

- [MRTK 설명서의 Interactable에 대 한 자세한 정보](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

시각적 피드백에 대 한 또 다른 중요 한 빌딩 블록은 MRTK 표준 셰이더입니다. MRTK 표준 셰이더를 사용 하 여 호버 조명 및 근접 조명 같은 시각적 피드백 효과를 쉽게 추가할 수 있습니다. MRTK 표준 셰이더는 Unity 표준 셰이더 보다 훨씬 더 많은 계산을 수행 하므로 성능이 뛰어난 환경을 만들 수 있습니다.

새 자료를 만들고 셰이더 ' Mixed Reality Toolkit > Standard '를 선택 합니다. 또는 MRTK 표준 셰이더를 사용 하는 기존 자료 중 하나를 선택할 수 있습니다.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [MRTK 설명서의 MRTK 표준 셰이더에 대해 자세히 알아보기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>오디오 피드백을 추가 하는 방법
개체에 오디오 소스를 추가 합니다. 그런 다음 입력 이벤트를 노출 하는 스크립트 (예: Interactable.cs 또는 PointerHandler.cs)에서 개체를 이벤트에 할당 하 고 PlayOneShot ()를 선택 합니다. 오디오 클립을 사용 하거나 MRTK의 오디오 자산 중 하나를 선택할 수 있습니다.

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>HoloLens 2 스타일 단추 prefabs를 사용 하는 방법
MRTK는 다양 한 유형의 HoloLens 2 shell (OS) 스타일 단추를 제공 합니다. 근접 조명, 압축 상자 및 단추 표면의 ripple 효과와 같은 정교한 시각적 피드백 제공 합니다.

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_Button.gif">

HoloLens 2 스타일 pressable button prefab 중 하나를 장면으로 끌어다 놓기만 하면 됩니다. Prefab는 위에 도입 된 Interactable.cs을 사용 합니다. Interactable에서 OnClick ()과 같은 노출 된 이벤트를 사용 하 여 작업을 트리거할 수 있습니다.

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [MRTK 설명서의 단추 prefabs에 대 한 자세한 정보](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>개체를 팔 로우 하도록 설정 하는 방법
RadialView.cs 스크립트를 개체에 할당 합니다. 3D 공간에서 다양 한 유형의 개체 위치를 달성할 수 있는 해 찾기 스크립트 시리즈의 일부입니다. SolverHandler.cs가 자동으로 추가 됩니다.
다음은 HoloLens 셸에서 시작 메뉴와 마찬가지로 ' 지연 팔 로우 ' 태그를 활용 하는 RadialView 구성의 예입니다. 최소/최대 거리와 최소/최대 보기 각도를 지정할 수 있습니다. 아래 예제에서는 15 ° 내에서 0.4 m과 0.8 m 사이에서 개체의 위치를 지정 하는 방법을 보여 줍니다. Lerp 시간 값을 조정 하 여 위치를 더 빠르거나 더 느리게 업데이트 합니다.

<img alt="MRTK Standard Shader" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [MRTK 설명서의 Solvers에 대 한 자세한 정보](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>개체의 얼굴을 만드는 방법
Billboard.cs 스크립트를 개체에 할당 합니다. 사용자의 위치에 관계 없이 항상 직면 합니다. 피벗 축 옵션을 지정할 수 있습니다.

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


혼합 현실에서 놀라운 환경을 만들 준비가 되셨습니까? 아래 페이지를 방문 하 여 MRTK 및 mixed reality에 대해 자세히 알아보세요.

## <a name="about-the-author"></a>저자 소개

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>동 Yoon 공원</b><br>UX 디자이너 @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>참고 항목

* [Mixed Reality Toolkit-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [MRTK 시작](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [HoloToolkit to MRTK 포팅 지침](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
