---
title: 시작 자습서 - 5. Solver를 사용하여 동적 콘텐츠 만들기
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: cbeaa8b65b7aecc0600294b3739fedfb903e568e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306656"
---
# <a name="5-creating-dynamic-content-using-solvers"></a>5. Solver를 사용하여 동적 콘텐츠 만들기

## <a name="overview"></a>개요

이 자습서에서는 복잡한 공간 배치 시나리오를 해결하기 위해 MRTK의 사용 가능한 배치 도구인 Solver를 사용하여 홀로그램을 동적으로 배치하는 방법을 살펴봅니다. MRTK의 Solver는 개체가 사용자 또는 장면의 기타 게임 개체를 따르도록 만드는 데 사용되는 스크립트 및 동작 시스템입니다. 또한 특정 위치에 맞춰서 앱을 보다 직관적으로 만들 수도 있습니다.

## <a name="objectives"></a>목표

* MRTK 해결기 소개
* Solver를 사용하여 사용자를 개체로 안내하는 방법 알아보기
* Solver를 사용하여 개체의 위치를 변경하는 방법 알아보기

## <a name="location-of-solvers-in-the-mrtk"></a>MRTK에서 해결기의 위치

 MRTK의 해결기는 MRTK SDK 폴더에 있습니다. 프로젝트에서 사용할 수 있는 Solver를 보려면 프로젝트 창에서 **Assets** > **MRTK** > **SDK** > **Features** > **Utilities** > **Solvers**로 이동합니다.

![mr-learning-base](images/mr-learning-base/base-05-section1-step1-1.png)

이 자습서에서는 Directional Indicator(방향 표시) Solver 및 Tap To Place(탭하여 위치 지정) Solver 구현을 검토합니다. MRTK에서 사용할 수 있는 Solver의 전체 범위를 알아보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) 가이드를 참조하세요.

> [!NOTE]
> Directional Indicator(방향 표시) Solver는 실험적인 기능이 때문에 위에 언급된 Solver 폴더에 없지만 Assets > MRTK > SDK > Experimental > Features > Utilities 폴더에 있습니다.

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a>Directional Indicator(방향 표시) Solver를 사용하여 사용자를 개체로 안내

프로젝트 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** 폴더로 이동하여 **Chevron** 프리팹을 클릭하여 Hierarchy(계층 구조) 창으로 끌어서 놓은 후 Transform(변환) **위치**를 X = 0, Y = 0, Z = 2로 설정하여 RoverExplorer 개체 근처에 배치합니다.

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> 카메라 또는 장면의 다른 아이콘이 개체를 숨기거나 방해가 되면, 위 이미지와 같이 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos를 끄기 위치로 전환</a>하여 아이콘을 숨길 수 있습니다. Gizmo 메뉴에 대한 내용 및 이 메뉴를 사용하여 장면 보기를 최적화하는 방법에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmo 메뉴</a> 설명서를 참조하세요.

새로 추가된 Chevron 개체 **표시기**의 이름을 변경한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **DirectionalIndicator** 및 **Directional Indicator Controller(스크립트)** 구성 요소를 추가합니다.

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> Solver를 추가하면(이 경우, DirectionalIndicator 구성 요소) SolverHandler 구성 요소가 Solver에 필요하기 때문에 자동으로 추가됩니다.

> [!NOTE]
> Directional Indicator Controller(스크립트)는 MRTK의 일부는 아니지만 자습서 자산에 포함되어 있습니다.

DirectionalIndicator 및 SolverHandler 구성 요소를 다음과 같이 구성합니다.

* **SolverHandler** 구성 요소의 **Tracked Target Type**(추적 대상 유형)이 **Head**로 설정되어 있는지 확인
* **RoverExplorer**를 Hierarchy(계층 구조) 창에서 **None (Transform)** 필드로 끌어서 놓아 **DirectionalIndicator** 구성 요소의 **Directional Target**(방향성 대상)에 할당
* **View Offset**(보기 오프셋)을 0.2로 변경

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-3.png)

재생 단추를 눌러 게임 모드로 전환하고, 마우스 오른쪽 단추를 누른 상태에서 마우스를 왼쪽이나 오른쪽으로 움직여서 응시 방향을 회전하면서 다음 사항을 확인합니다.

* RoverExplorer 개체에서 눈길을 돌리면 표시기 개체가 나타나고 RoverExplorer 개체를 가리킵니다.

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> Scene(장면) 창에 카메라 광선이 보이지 않으면 위 이미지와 같이 Gizmo 메뉴가 활성화되어 있는지 확인합니다.

> [!TIP]
> 편집기 내 입력 시뮬레이션을 사용하는 방법은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [편집기 내 손 입력 시뮬레이션을 사용하여 장면 테스트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) 가이드를 참조하세요.

> [!TIP]
> 컴퓨터에 마이크가 있으면 음성 명령 "toggle diagnostics"를 사용하여 게임 창에 나타나는 Diagnostics(진단) 패널의 활성 상태를 쉽게 전환할 수 있습니다. 또는, MRTK Configuration Profile(MRTK 구성 프로필) > Diagnostics(진단) > Enable Diagnostics System(진단 시스템 활성화)에서 사용하지 않도록 설정할 수 있습니다. 하지만 일반적으로 개발 중에 Diagnostics System(진단 시스템)을 활성 상태로 유지하는 것이 좋습니다.

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a>Tap to Place(탭하여 위치 지정) Solver를 사용하여 개체 위치 변경

Hierarchy(계층 구조) 창에서 RoverExplorer > **RoverAssembly** 개체를 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **Tap To Place(스크립트)** 구성 요소를 추가하고 다음과 같이 구성합니다.

* **SolverHandler** 구성 요소의 **Tracked Target Type**(추적 대상 유형)이 **Head**로 설정되어 있는지 확인
* **Keep Orientation Vertical**(방향을 세로로 유지) 확인란 선택
* **Magnetic Surfaces**(자기 표면) > **Element 0**(요소 0) 드롭다운에서 **Spatial Awareness**(공간 인식)를 제외한 모든 옵션을 선택 취소

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> Magnetic Surfaces(자기 표면) 설정은 개체를 배치할 때 Tap To Place(스크립트) 구성 요소가 어떤 개체를 감지할 수 있는지 결정합니다. 이 설정을 Spatial Awareness(공간 인식) 전용으로 변경하면 Tap To Place(스크립트) 구성 요소는 Spatial Awareness라는 Unity 레이어의 개체에만 Rover를 배치할 수 있으며, 이것은 기본적으로 HoloLens에서 생성된 공간 인식 메시입니다.
>
>레이어에 대해 자세히 알아보려면 Unity의 <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">레이어</a> 설명서를 참조하세요.

> [!TIP]
> HoloLens에서 Tap To Place 기능을 테스트할 때 공간 인식 메시를 보려면 Spatial Mesh Observer의 표시 옵션을 임시로 Visible로 설정하면 됩니다. 표시 옵션을 변경하는 방법은 [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침을 참조하세요.

Hierarchy(계층 구조) 창에서 RoverAssembly 개체를 선택한 상태로 Inspector(인스펙터) 창에서 **On Placing Started ()** 이벤트를 찾아서 **+** 아이콘을 클릭하여 새 이벤트를 추가합니다.

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-2.png)

이벤트를 다음과 같이 구성합니다.

* **RoverAssembly** 개체를 Hierarchy(계층 구조) 창에서 **None (Object)** 필드로 끌어서 놓아 On Placing Started () 이벤트의 수신기로 지정
* **No Function**(함수 없음) 드롭다운에서 **TapToPlace** > **float SurfaceNormalOffset**을 선택하여 이벤트가 트리거될 때 SurfaceNormalOffset 속성 값을 업데이트
* 인수가 **0**으로 설정되어 있는지 확인

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-3.png)

Hierarchy(계층 구조) 창에서 빈 지점을 마우스 오른쪽 단추로 클릭하고 **3D 개체** > **큐브**를 선택하여 지면을 나타내는 임시 개체를 생성하고 **Transform**(변환) 구성 요소를 다음과 같이 구성합니다.

* **위치**: X = 0, Y = -1.65, Z = 6
* **회전**: X = 0, Y = 0, Z = 0
* **배율**: X = 10, Y = 0.2, Z = 10

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-4.png)

Hierarchy(계층 구조) 창에서 임시 큐브를 선택한 상태로 Inspector(인스펙터) 창에서 **레이어** 드롭다운을 사용하여 큐브의 레이어 설정에 **Spatial Awareness**(공간 인식) 레이어만 포함하도록 변경합니다.

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-5.png)

재생 단추를 눌러 게임 모드로 전환한 다음, 시선이 RoverAssembly 개체에 도달할 때까지 마우스 오른쪽 단추를 누른 상태로 마우스를 아래로 이동합니다.

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-6.png)

마우스 왼쪽 단추를 클릭하여 Tap To Place(탭하여 위치 지정) 프로세스를 시작합니다.

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-7.png)

마우스 오른쪽 단추를 누른 상태에서 마우스를 왼쪽이나 오른쪽으로 움직여서 응시 방향을 회전하고 배치에 만족하면 마우스 왼쪽 단추를 클릭합니다.

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-8.png)

게임 모드에서 기능 테스트를 마쳤으면 큐브 개체를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택하여 장면에서 제거합니다.

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 MRTK의 Directional Indicator(방향 표시) Solver를 사용하여 UI 요소가 직관적으로 사용자를 개체로 안내하는 방법을 알아보았습니다. Tap To Place(탭하여 위치 지정) Solver를 사용하여 개체의 위치를 쉽게 조정하는 방법도 알아보았습니다.

MRTK에 포함된 이러한 Solver와 다른 Solver에 대해 자세히 알아보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) 가이드를 참조하세요.

[다음 자습서: 6. 사용자 인터페이스 만들기](mr-learning-base-06.md)
