---
title: 시작 자습서 - 4. 장면에서 개체 위치 지정
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여 줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 71990db23b5154de916f0eda86a978885ab53547
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376635"
---
# <a name="4-positioning-objects-in-the-scene"></a>4. 장면에서 개체 위치 지정

## <a name="overview"></a>개요

이 자습서에서는 자습서 자산을 가져오고 제공된 개체를 장면에 배치합니다.

## <a name="objectives"></a>목표

* 장면에 개체를 배치하는 방법 알아보기
* MRTK의 그리드 개체 컬렉션 기능을 사용하는 방법 알아보기

## <a name="importing-the-tutorial-assets"></a>자습서 자산 가져오기

다음 Unity 사용자 지정 패키지를 다운로드하여 가져옵니다.

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.

![mr-learning-base](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [MRTK 가져오기](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.

## <a name="creating-the-parent-object"></a>부모 개체 만들기

Hierarchy 창에서 빈 영역을 마우스 오른쪽 단추로 클릭하고, **빈 항목 만들기**를 선택하여 빈 개체를 장면에 추가합니다.

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> 위의 이미지처럼 장면 및 게임 창을 나란히 표시하려면 게임 창을 장면 창의 오른쪽으로 끌어다 놓습니다. 작업 영역을 사용자 지정하는 방법에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조하세요.

새로 만든 개체를 마우스 오른쪽 단추로 클릭하고, **이름 바꾸기**를 선택하고, 이름을 **RoverExplorer**로 변경합니다.

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-2.png)

RoverExplorer 개체가 선택된 상태에서 Inspector 창에서 다음과 같이 **Transform** 구성 요소를 구성합니다.

* **위치**: X = 0, Y = -0.6, Z = 2
* **회전**: X = 0, Y = 0, Z = 0
* **크기 조정**: X = 1, Y = 1, Z = 1

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> 카메라는 사용자 헤드를 나타내며 원점, X = 0, Y = 0, Z = 0에 배치됩니다. 일반적으로 Unity의 1단위는 실제 세계의 약 1미터입니다. 하지만 여기에는 예외가 있습니다. 예를 들어 개체가 크기 조정된 개체의 자식인 경우입니다. 위의 시나리오에서 RoverExplorer는 2미터 앞에 배치되고 사용자 헤드보다 0.6 미터 아래에 배치됩니다.

## <a name="adding-the-tutorial-prefabs"></a>자습서 프리팹 추가

Project 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** 폴더로 이동합니다.

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">프리팹</a>은 Unity로 저장된 미리 구성된 GameObject이며 프로젝트 전체에서 재사용할 수 있습니다.

Project 창에서 **Table** 프리팹을 클릭하여 RoverExplorer 개체의 자식이 되도록 **RoverExplorer** 개체에 끌어 놓은 다음, Inspector 창에서 다음과 같이 **Transform** 구성 요소를 구성합니다.

* **위치**: X = 0, Y = -0.005, Z = 0
* **회전**: X = 0, Y = 0, Z = 0
* **크기 조정**: X = 1.2, Y = 0.01, Z = 1.2

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> 위의 이미지에 표시된 것처럼 장면을 표시하려면 장면 창의 오른쪽 위 모서리에 있는 <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">장면 Gizmo</a>를 사용하여 시야각이 전방 Z 축을 따라 이동하도록 조정하고, MixedRealityPlayspace 개체를 두 번 클릭하여 카메라에 포커스를 설정하고, 필요에 따라 확대합니다.

Project 창에서 **RoverAssembly** 프리팹을 클릭하여 RoverExplorer 개체의 자식으로 만들도록 **RoverExplorer** 개체로 끌어 놓은 다음, Inspector 창에서 다음과 같이 **Transform** 구성 요소를 구성합니다.

* **위치**: X = -0.1, Y = 0, Z = 0
* **회전**: X = 0, Y = -135, Z = 0
* **크기 조정**: X = 1, Y = 1, Z = 1

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a>컬렉션에서 개체 구성

Hierarchy 창에서 **RoverExplorer** 개체를 마우스 오른쪽 단추로 클릭하고 **빈 항목 만들기**를 선택하여 빈 개체를 RoverExplorer의 자식으로 추가하고, 개체 이름을 **RoverParts**로 설정하고 **Transform** 구성 요소를 다음과 같이 구성합니다.

* **위치**: X = 0, Y = 0.06, Z = 0
* **회전**: X = 0, Y = 90, Z = 0
* **크기 조정**: X = 1, Y = 1, Z = 1

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-1.png)

Hierarchy 창에서 모든 RoverExplorer > RoverAssembly > RoverModel > **Parts** 자식 개체를 선택하고, 마우스 오른쪽 단추로 클릭하고 **중복**을 선택하여 각 파트의 복사본을 만듭니다.

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> 인접 개체를 여러 개 선택하려면 SHIFT 키를 누른 채 마우스를 사용하여 첫 번째 및 마지막 개체를 선택합니다.

새로 중복된 Parts 자식 개체가 선택된 상태에서 이를 클릭하여 **RoverParts** 개체로 끌어 놓아 RoverParts 개체의 자식 개체로 만듭니다.

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-3.png)

장면 작업을 더 쉽게 수행할 수 있도록 Hierarchy 창에서 개체 왼쪽의 **눈** 아이콘을 클릭하여 **RoverExplorer** 개체에 대한 **장면 표시 유형**을 끄기로 전환합니다. 이렇게 하면 다음과 같이 게임 내 표시 유형을 변경하지 않고 장면 창에서 개체를 숨깁니다.

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> 장면 표시 유형 컨트롤에 대한 내용 및 이 컨트롤을 사용하여 장면 보기와 워크플로를 최적화하는 방법에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">장면 표시 유형</a> 설명서를 참조하세요.

Hierarchy 창에서 추가된 **(1)** 을 **_Part**로 바꿔 RoverParts 자식 개체의 이름을 정리합니다.

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-5.png)

Hierarchy 창에서 **RoverParts** 개체를 선택한 다음, Inspector 창에서 **구성 요소 추가** 단추를 클릭하고, **GridObjectCollection**을 검색하고 선택하여 GridObjectCollection 구성 요소를 RoverParts 개체에 추가합니다.

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-6.png)

다음과 같이 **GridObjectCollection** 구성 요소 값을 구성합니다.

* **정렬 유형**: 사전순
* **레이아웃**: 수평
* **셀 너비**: 0.25
* **부모에서의 거리**: 0.38

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-7.png)

그런 다음, **컬렉션 업데이트** 단추를 클릭하여 RoverParts 자식 개체의 위치를 업데이트합니다.

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 사용자를 기준으로 장면에 개체를 배치하고 MRTK의 그리드 개체 컬렉션 기능을 사용하여 컬렉션의 개체를 구성하는 방법을 배웠습니다.

[다음 자습서: 5. 해결기를 사용하여 동적 콘텐츠 만들기](mr-learning-base-05.md)
