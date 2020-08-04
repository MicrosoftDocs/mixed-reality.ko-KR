---
title: 시작 자습서 - 8. 시선 추적 사용
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여 줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 31552cba9a68d1f1214395dbf4e4ed84ecd3f388
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376605"
---
# <a name="8-using-eye-tracking"></a>8. 시선 추적 사용

## <a name="overview"></a>개요

이 자습서에서는 HoloLens 2에 대해 시선 추적을 사용하도록 설정하고 개체에 시선 추적을 추가하여 사용자가 개체를 볼 때 작업을 트리거하는 방법을 배웁니다.

> [!NOTE]
> 이 프로젝트를 HoloLens(첫 번째 세대)에 배포하는 경우에는 HoloLens 2에서만 시선 추적이 지원됩니다.

## <a name="objectives"></a>목표

* HoleLens 2에 대한 시선 추적을 사용하도록 설정하는 방법 알아보기
* 시선 추적을 사용하여 작업을 트리거하는 방법 알아보기

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a>시선 응시 입력 기능이 활성화되었는지 확인

Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > **Unity 프로젝트 구성**을 선택하여 **MRTK Project Configurator** 창을 열고 **UWP 기능** 섹션에서 **시선 응시 입력 기능 사용**이 회색으로 표시되는지 확인합니다.

![mr-learning-base](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> 이 자습서 시리즈의 시작 부분에서 Unity 프로젝트를 구성한 경우 [MRTK Project Configurator 설정 적용](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) 동안에는 응시 입력 기능이 사용하도록 설정되어 있어야 합니다. 그러나 사용하도록 설정되지 않은 경우 지금 사용하도록 설정해야 합니다.

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a>응시 공급자에서 시선 기반 응시 사용

Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 MixedRealityToolkit > **입력** 탭을 선택하고 다음 단계를 수행합니다.

* **DefaultHoloLens2InputSystemProfile**을 복제하고 적절한 이름(예: _GettingStarted_HoloLens2InputSystemProfile_)을 설정합니다.
* **포인터** 섹션을 확장합니다.
* **DefaultMixedRealityPointerProfile**을 복제하고 적절한 이름(예: _GettingStarted_MixedRealityPointerProfile_)을 설정합니다.
* **응시 설정** 섹션을 찾고 **시선 추적 사용** 확인란을 선택합니다.

![mr-learning-base](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> MRTK 프로필을 복제하는 방법은 [MRTK 프로필 구성](mr-learning-base-03.md) 지침을 참조하세요.

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a>Unity 편집기에 대해 시뮬레이션된 시선 추적 사용

Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 **입력** 탭으로 이동한 다음, 다음을 수행합니다.

* **입력 데이터 공급자** > **입력 시뮬레이션 서비스** 섹션을 확장합니다.
* **DefaultMixedRealityInputSimulationProfile**을 복제하고 적절한 이름(예: _GettingStarted_MixedRealityInputSimulationProfile_)을 설정합니다.
* **시선 시뮬레이션** 섹션을 찾아 **시선 위치 시뮬레이션** 확인란을 선택합니다.

![mr-learning-base](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a>개체에 시선 추적 추가

Hierarchy 창에서 RoverExplorer > **Buttons** 개체를 확장한 다음, 세 개의 자식 단추 개체 각각에 대해 SeeItSayItLabel > **TextMeshPro** 개체를 확장하고 선택합니다.

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-1.png)

TextMeshPro 개체를 선택한 상태로 Inspector 창에서 **구성 요소 추가** 단추를 사용하여 다음 구성 요소를 선택한 모든 개체에 추가합니다.

* **Box Collider** 구성 요소
* **EyeTrackingTarget** 구성 요소

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-2.png)

Hierarchy 창에서 **Hints** > SeeItSayItLabel > **TextMeshPro** 개체를 선택한 다음, 다음과 같이 **EyeTrackingTarget** 구성 요소를 구성합니다.

* **On Look At Start ()** 이벤트 섹션에서
  * 작은 **+** 아이콘을 클릭하여 다른 이벤트를 추가합니다.
  * 개체 자체(즉, 동일한 **TextMeshPro** 개체)를 **없음(개체)** 필드에 할당합니다.
  * **함수 없음** 드롭다운에서 **TextMeshPro** > **float fontSize**를 차례로 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트합니다.
  * 인수를 **0.06**으로 설정하여 현재 글꼴 크기인 0.04 x 50%를 늘립니다.
* **On Look Away ()** 이벤트 섹션에서
  * 작은 **+** 아이콘을 클릭하여 다른 이벤트를 추가합니다.
  * 개체 자체(즉, 동일한 **TextMeshPro** 개체)를 **없음(개체)** 필드에 할당합니다.
  * **함수 없음** 드롭다운에서 **TextMeshPro** > **float fontSize**를 차례로 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트합니다.
  * 인수를 **0.04**로 설정하여 글꼴 크기를 0.04로 다시 설정합니다.

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-3.png)

**Explode** > SeeItSayItLabel > **TextMeshPro** 개체 및 **Reset** > SeeItSayItLabel > **TextMeshPro** 개체에 대해 이 단계를 **반복**합니다.

이제 게임 모드로 들어간 다음, 마우스 오른쪽 버튼을 누른 채로 마우스를 이동하면서 응시가 레이블 중 하나를 적중할 때까지 누르면 글꼴 크기가 50%씩 증가하고 시선을 돌렸을 때 원래 크기로 다시 설정됩니다.

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 HoloLens 2에 대해 시선 추적을 사용하도록 설정하고 개체에 시선 추적을 추가하여 사용자가 개체를 볼 때 작업을 트리거하는 방법을 알아보았습니다.

[다음 자습서: 9. 음성 명령 사용](mr-learning-base-09.md)