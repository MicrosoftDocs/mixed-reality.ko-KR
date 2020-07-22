---
title: 시작 자습서 - 7. 3D 개체와 상호 작용
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 8920b35d1583777b86bc82868bb90338e25298e2
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305996"
---
# <a name="7-interacting-with-3d-objects"></a>7. 3D 개체와 상호 작용

이 자습서에서는 3D 개체의 근거리 및 원거리 조작을 사용하도록 설정하고 허용되는 조작 유형을 제한하는 방법을 알아봅니다. 개체 조작을 보다 쉽게 제어할 수 있도록 3D 개체 주위에 경계 상자를 추가하는 방법도 알아봅니다.

## <a name="objectives"></a>목표

* 3D 개체가 상호 작용할 수 있도록 구성하는 방법 알아보기
* 3D 개체에 경계 상자를 추가하는 방법 알아보기

## <a name="manipulating-3d-objects"></a>3D 개체 조작

이 섹션에서는 [장면에서 개체 위치 지정](mr-learning-base-04.md) 자습서를 진행하는 동안 테이블에서 구성한 모든 Rover 파트를 조작하는 기능을 추가합니다.

이를 위해 수행할 주요 단계는 다음과 같습니다.

1. 모든 파트 개체에 Object Manipulator(스크립트) 구성 요소 추가
2. 모든 파트 개체에 NearInteractionGrabbable 구성 요소 추가
3. Object Manipulator(스크립트) 구성 요소 구성

> [!NOTE]
> **개체를 조작**하려면 개체에 다음 구성 요소가 있어야 합니다.
>
> * **충돌체** 구성 요소(예: 상자 충돌체)
> * **Object Manipulator(스크립트)** 구성 요소
>
> 추적 손으로 개체에 대한 **조작** 및 **잡기**를 수행하려면 개체에 다음 구성 요소가 있어야 합니다.
>
> * **충돌체** 구성 요소(예: 상자 충돌체)
> * **Object Manipulator(스크립트)** 구성 요소
> * **NearInteractionGrabbable** 구성 요소

또한 Rover 파트를 Rover에 배치하여 완전한 Rover 어셈블리로 만들 수 있도록 Rover Explorer를 구성합니다.

Hierarchy(계층 구조) 창에서 RoverExplorer > **RoverParts** 개체를 펼치고, 자식 Rover 파트 개체와 **RoverAssembly** 개체를 모두 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 다음 구성 요소를 선택한 모든 개체에 추가합니다.

* **Object Manipulator(스크립트)** 구성 요소
* **NearInteractionGrabbable** 구성 요소
* **Part Assembly Controller(스크립트)** 구성 요소

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> 서로 인접하지 않은 여러 개체를 선택하려면 Ctrl 키를 누른 채 마우스를 사용하여 개체를 선택합니다.

> [!NOTE]
> 이 자습서의 학습 목표를 달성하기 위해 Rover 파트에 충돌체가 이미 추가되어 있습니다. 충돌체에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">충돌체</a> 설명서를 참조하세요.

> [!NOTE]
> Part Assembly Controller(스크립트)는 MRTK의 일부는 아니지만 자습서 자산에 포함되어 있습니다.

Rover 파트 개체와 RoverAssembly 개체를 선택한 상태로, Inspector(인스펙터) 창에서 **Object Manipulator(스크립트)** 구성 요소를 다음과 같이 구성합니다.

* **Two Handed Manipulation Type**(양손 조작 유형) 드롭다운에서 Scale(크기 조정) 선택을 취소하고 **Move**(이동) 및 **Rotate**(회전)만 가능하도록 설정

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> 이제 모든 Rover 파트 개체와 RoverAssembly 개체에 대해 개체 조작이 가능하도록 설정했습니다.

프로젝트 창에서 **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** 폴더로 이동하여 오디오 클립을 찾습니다.

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

Hierarchy(계층 구조) 창에서 **Rover 파트 개체**를 다시 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **Audio Sources**(오디오 소스) 구성 요소를 추가하고 다음과 같이 구성합니다.

* **MRTK_Scale_Start** 오디오 클립을 **AudioClip** 필드에 할당
* **Play On Awake**(활성 상태일 때 재생) 확인란의 선택을 취소
* **Spatial Blend**(공간 블렌드)를 1로 변경

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

Hierarchy(계층 구조) 창에서 RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** 개체를 펼쳐서 모든 배치 힌트 개체를 표시한 다음, 첫 번째 Rover 파트 RoverParts > **Camera_Part**를 선택하고 **Part Assembly Controller(스크립트)** 구성 요소를 다음과 같이 구성합니다.

* **Camera_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

나머지 Rover 파트 개체와 RoverAssembly 개체 각각에 대해 이 단계를 **반복**하여 **Part Assembly Controller(스크립트)** 구성 요소를 다음과 같이 구성합니다.

* **Generator_Part**의 경우 **Generator_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당
* **Lights_Part**의 경우 **Lights_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당
* **UHFAntenna_Part**의 경우 **UHFAntenna_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당
* **Spectrometer_Part**의 경우 **Spectrometer_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당
* **RoverAssembly**의 경우 개체 자체(즉, 동일한 **RoverAssembly** 개체)를 **Location To Place**(배치할 위치) 필드에 할당

Hierarchy(계층 구조) 창에서 RoverExplorer > Buttons > **Reset**(초기화) 단추 개체를 선택한 다음, Inspector(인스펙터) 창에서 상호작용 가능 **OnClick ()** 이벤트를 다음과 같이 구성합니다.

* **RoverAssembly** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **PartAssemblyController** > **ResetPlacement ()** 를 선택하여 이 함수를 이벤트가 트리거될 때 실행할 작업으로 설정

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

이제 게임 모드로 전환하면 근거리 또는 원거리 상호 작용을 사용하여 Rover 파트를 Rover에 놓을 수 있습니다. 파트가 해당하는 배치 힌트에 가까워지면 위치로 맞춰져서 Rover의 일부가 됩니다. 배치를 다시 설정하려면 Reset(초기화) 단추를 누르면 됩니다.

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

Object Manipulator 구성 요소 및 관련 속성에 대해 자세히 알아보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) 가이드를 참조하세요.

## <a name="adding-bounding-boxes"></a>경계 상자 추가

경계 상자를 사용하면 크기 조정 및 회전에 사용할 수 있는 핸들을 제공하여 근거리 및 원거리 상호 작용 모두에서 한 손으로 개체를 보다 쉽고 직관적으로 조작할 수 있습니다.

이 예제에서는 전체 환경을 쉽게 이동, 회전, 확장할 수 있도록 RoverExplorer 개체에 경계 상자를 추가합니다. 또한 경계 상자를 켜고 끌 수 있도록 메뉴를 구성합니다.

Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 다음 구성 요소를 추가합니다.

* **BoundingBox** 구성 요소
* **Object Manipulator(스크립트)** 구성 요소

그런 다음, 두 구성 요소 옆에 있는 확인란을 **선택 취소**하여 기본적으로 **사용하지 않도록 설정**합니다.

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> 경계 상자 시각화는 런타임에 생성되므로 게임 모드로 전환하기 전에는 보이지 않습니다.

> [!NOTE]
> BoundingBox 구성 요소는 런타임에 NearInteractionGrabbable 구성 요소를 자동으로 추가합니다. 따라서 추적 손으로 감싼 개체를 잡기 위해 이 구성 요소를 추가할 필요가 없습니다.

Hierarchy(계층 구조) 창에서 메뉴 > **ButtonCollection** 개체를 펼쳐서 단추 4개를 표시하고 3번째 단추의 이름을 **BoundingBox_Enable**로 변경한 다음, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소를 다음과 같이 구성합니다.

* **Main Label Text**(기본 레이블 텍스트)를 **Enable**(사용)로 변경
* **RoverExplorer** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **BoundingBox** > **bool Enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트
* 인수 확인란이 **선택**되어 있는지 확인
* 작은 **+** 아이콘을 클릭하여 또 다른 이벤트를 추가
* **RoverExplorer** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **ObjectManipulator** > **bool Enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트
* 인수 확인란이 **선택**되어 있는지 확인
* **아이콘**을 'cube with bounding box'(경계 상자와 큐브) 아이콘으로 유지

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

네 번째와 마지막 단추의 이름을 **BoundingBox_Disable**로 바꾼 다음, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소를 다음과 같이 구성합니다.

* **Main Label Text**(기본 레이블 텍스트)를 **Disable**(사용 안 함)로 변경
* **RoverExplorer** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **BoundingBox** > **bool Enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트
* 인수 확인란이 **선택 취소**되어 있는지 확인
* 작은 **+** 아이콘을 클릭하여 또 다른 이벤트를 추가
* **RoverExplorer** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **ObjectManipulator** > **bool Enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트
* 인수 확인란이 **선택 취소**되어 있는지 확인
* **아이콘**을 'cube with bounding box'(경계 상자와 큐브) 아이콘으로 변경

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

이제 게임 모드로 전환하여 Enable(사용) 단추를 클릭하여 경계 상자를 사용하도록 설정하면, 근거리나 원거리 상호 작용을 사용하여 경계 상자를 이동 및 회전하고 크기를 조정할 수 있으며 Disable(사용 안 함) 단추를 사용하여 경계 상자를 다시 사용하지 않도록 설정할 수 있습니다.

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

경계 상자 구성 요소 및 관련 속성에 대한 자세한 내용을 보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [조작 처리기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 가이드를 참조하세요.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 3D 개체에 대한 근거리 및 원거리 조작을 사용하도록 설정하는 방법과 허용되는 조작 유형을 제한하는 방법을 알아보았습니다. 개체 조작을 보다 쉽게 제어할 수 있도록 3D 개체 주위에 경계 상자를 추가하는 방법도 알아보았습니다.

[다음 자습서: 8. 시선 추적 사용](mr-learning-base-08.md)
