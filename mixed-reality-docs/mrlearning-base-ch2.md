---
title: 시작 자습서 - 3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376140"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

이전 자습서에서는 HoloLens 2의 첫 번째 애플리케이션을 시작으로 MRTK(Mixed Reality Toolkit)에 제공되는 몇 가지 기능을 알아보았습니다. 이 자습서에서는 UI 텍스트 패널에서 단추를 만들고 구성하는 방법과 기본 상호 작용(터치)을 사용하여 각 단추와 상호 작용하는 방법을 알아봅니다. 개체의 크기, 사운드 및 색상 변경과 같은 간단한 작업과 효과도 추가로 살펴봅니다. 이 모듈에서는 [공간 매핑](spatial-mapping.md) 메시 시각화를 해제하는 것으로 시작하여 MRTK 프로필을 수정하는 방법에 대한 기본 개념을 소개합니다.

## <a name="objectives"></a>목표

* Mixed Reality Toolkit 프로필 사용자 지정 및 구성
* UI 요소 및 단추를 사용하여 홀로그램과 상호 작용
* 기본적인 손 추적 입력 및 상호 작용

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Mixed-Reality Toolkit 프로필을 구성하는 방법(공간 인식 변경 표시 옵션)
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

이 섹션에서는 기본 MRTK 프로필을 사용자 지정하고 구성하는 방법을 알아봅니다.

이 예제에서는 공간 메시 관찰자의 설정을 변경하여 공간 인식 메시를 숨기는 방법을 보여줍니다. 그러나 MRTK 프로필의 설정 또는 값을 사용자 지정할 때 이러한 원칙을 그대로 적용해도 됩니다.

공간 인식 메시를 숨기기 위해 수행하는 주요 단계는 다음과 같습니다.

1. 기본 구성 프로필 복제
2. 공간 인식 시스템 사용
3. 기본 공간 인식 시스템 프로필 복제
4. 기본 공간 인식 메시 관찰자 프로필 복제
5. 공간 인식 메시의 표시 유형 변경

> [!NOTE]
> 기본적으로 MRTK 프로필은 편집할 수 없습니다. 이러한 기본 프로필 템플릿을 편집하려면 먼저 복제해야 합니다. 중첩된 여러 프로필 레이어가 있습니다. 따라서 하나 이상의 설정을 구성할 때 여러 프로필을 복제하여 편집하는 것이 일반적입니다.

### <a name="1-clone-the-default-configuration-profile"></a>1. 기본 구성 프로필 복제

> [!NOTE]
> 구성 프로필은 최상위 수준 프로필입니다. 따라서 다른 프로필을 편집하려면 먼저 구성 프로필을 복제해야 합니다.

다음과 같이 [계층 구조] 창에서 **MixedRealityToolkit** 개체를 선택한 상태로, [검사기] 창에서 Mixed Reality Toolkit **구성 프로필**을 **DefaultHoloLens2ConfigurationProfile**로 변경합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

다음과 같이 **MixedRealityToolkit** 개체를 선택한 상태로, [검사기] 창에서 **복제 및 사용자 지정** 단추를 클릭하여 [프로필 복제] 창을 엽니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

다음과 같이 [프로필 복제] 창에서 **복제** 단추를 클릭하여 **DefaultHololens2ConfigurationProfile**의 편집 가능한 복사본을 만듭니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

이제 새로 만든 구성 프로필이 다음과 같이 장면의 구성 프로필로 할당됩니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

Unity 메뉴에서 **파일** > **저장**을 선택하여 장면을 저장합니다.

> [!TIP]
> 자습서를 진행하는 동안 항상 작업을 저장해야 합니다.

### <a name="2-enable-the-spatial-awareness-system"></a>2. 공간 인식 시스템 사용

다음과 같이 [계층 구조] 창에서 **MixedRealityToolkit** 개체를 선택한 상태로, [검사기] 창에서 **공간 인식** 탭을 선택한 다음, **공간 인식 시스템 사용** 확인란을 선택합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. 기본 공간 인식 시스템 프로필 복제

다음과 같이 **공간 인식** 탭에서 **복제** 단추를 클릭하여 [프로필 복제] 창을 엽니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

다음과 같이 [프로필 복제] 창에서 **복제** 단추를 클릭하여 **DefaultMixedRealitySpatialAwarenessSystemProfile**의 편집 가능한 복사본을 만듭니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

이제 새로 만든 공간 인식 시스템 프로필이 다음과 같이 구성 프로필에 자동으로 할당됩니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. 기본 공간 인식 메시 관찰자 프로필 복제

다음과 같이 **공간 인식** 탭을 선택한 상태로 **Windows Mixed Reality 공간 메시 관찰자** 섹션을 확장한 다음, **복제** 단추를 클릭하여 [프로필 복제] 창을 엽니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

다음과 같이 [프로필 복제] 창에서 **복제** 단추를 클릭하여 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**의 편집 가능한 복사본을 만듭니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

이제 새로 만든 공간 인식 메시 관찰자 프로필이 다음과 같이 공간 인식 시스템 프로필에 자동으로 할당됩니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. 공간 인식 메시의 표시 유형 변경

다음과 같이 **공간 메시 관찰자 설정**에서 **표시 옵션**을 **폐색**으로 변경하여 공간 매핑 메시가 계속 작동하는 동안에도 보이지 않도록 설정합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> 공간 매핑 메시가 보이지 않더라도 여전히 존재하며 작동 중입니다. 예를 들어 실제 벽 뒤의 홀로그램처럼 공간 매핑 메시 뒤의 홀로그램은 보이지 않습니다.

MRTK 프로필에서 설정을 수정하는 방법을 알아보았습니다. 보시는 것처럼, MRTK 설정을 사용자 지정하려면 먼저 기본 프로필의 복사본을 만들어야 합니다. 기본 프로필은 편집이 불가능하므로, 기본 설정으로 되돌리고 싶을 때 항상 기본 프로필을 참조로 사용할 수 있습니다. MRTK 프로필 및 해당 아키텍처에 대한 자세한 내용은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [Mixed Reality Toolkit 프로필 구성 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)를 참조하세요.

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>손 추적 제스처 및 상호 작용 가능 단추

이 섹션에서는 손 추적을 사용하여 단추를 누르고 단추가 눌리면 동작을 발생시키는 이벤트를 트리거하는 방법을 알아봅니다.

이 예제에서는 단추가 눌리면 큐브의 색을 변경하고 단추 누르기가 해제되면 원래 색으로 되돌리는 방법을 보여줍니다. 다른 이벤트를 만들 때 이 원칙을 그대로 적용해도 됩니다.

큐브의 색을 변경하기 위해 수행하는 주요 단계는 다음과 같습니다.

1. 장면에 누를 수 있는 단추 프리팹 추가
2. 장면에 큐브 추가
3. InteractableOnPressReceiver 이벤트 형식 구성
4. On Press 이벤트를 수신하는 큐브 구성
5. On Press 이벤트에 의해 트리거되는 동작 정의
6. On Release 이벤트를 수신하는 큐브 구성
7. On Release 이벤트에 의해 트리거되는 동작 정의
8. 편집기 내 시뮬레이션을 사용하여 단추 테스트

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. 장면에 누를 수 있는 단추 프리팹 추가

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">프리팹</a>은 Unity로 저장된 미리 구성된 GameObject이며 프로젝트 전체에서 재사용할 수 있습니다.

다음과 같이 **프로젝트 창**에서 **PressableButtonHoloLens2**를 검색하여 이 예제에 사용할 프리팹을 찾습니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

다음과 같이 **검색** 결과에서 **PressableButtonHoloLens2** 프리팹을 선택하고 **계층 구조** 창으로 **끌어** 장면에 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> 아래 이미지처럼 장면을 표시하려면 [계층 구조] 창에서 PressableButtonHoloLens2 개체를 두 번 클릭하여 포커스를 가져온 다음, 장면 창의 오른쪽 위 모서리에 있는 <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">장면 Gizmo</a>를 사용하여 시야각이 전방 Z 축을 따라 이동하도록 조정합니다.

**PressableButtonHoloLens2** 개체를 선택한 상태로 **검사기** 창에서 다음을 수행합니다.

* 카메라 앞에 배치되도록, 즉, 원점에 배치되도록 변환 **위치**를 변경합니다(예: x = 0, y = 0, z = 0.5).

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> 일반적으로 Unity의 1 위치 단위는 실제 세계의 1미터와 같습니다. 하지만 여기에는 예외가 있습니다. 예를 들어 개체가 크기 조정된 개체의 자식인 경우입니다.

### <a name="2-add-a-cube-to-the-scene"></a>2. 장면에 큐브 추가

다음과 같이 [계층 구조] 창 내부의 빈 지점을 마우스 오른쪽 단추로 클릭하고 **3D 개체** > **큐브**를 선택하여 장면에 큐브를 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

**Cube** 개체를 선택한 상태로 **검사기** 창에서 다음을 수행합니다.

* 누를 수 있는 단추 근처에 있지만 겹치지는 않도록 **변환** 위치를 변경합니다(예: x = 0, y = 0.04, z = 0.5).
* 변환 **배율**을 적절한 크기로 변경합니다(예: x = 0.02, y = 0.02, z = 0.02).

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. InteractableOnPressReceiver 이벤트 형식 구성

다음과 같이 [계층 구조] 창에서 **PressableButtonHoloLens2** 개체를 선택하고, **검사기** 창 **햄버거 메뉴**에서 **모든 구성 요소 축소**를 선택하여 이 개체의 모든 구성 요소에 대한 개요를 가져옵니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

다음과 같이 **Interactable(스크립트)** 구성 요소를 확장하고, **이벤트** > **수신기** 섹션을 찾아 확장합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

다음과 같이 **이벤트 추가** 단추를 클릭하여 이벤트 수신기 형식 **InteractableOnPressReceiver**의 새 이벤트 수신기를 만듭니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> InteractableOnPressReceiver라는 이벤트 수신기 형식을 사용하면 추적 손이 단추를 누를 때 누름 이벤트에 대해 단추가 응답할 수 있습니다.

새로 만든 이벤트 수신기의 **상호 작용 필터**를 **근거리 및 원거리**로 변경합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. On Press 이벤트를 수신하는 큐브 구성

다음과 같이 [계층 구조] 창에서 **큐브**를 **클릭**하여 **On Press ()** 이벤트의 **이벤트 속성** 개체 필드로 끌어 놓아 큐브를 On Press () 이벤트의 수신기로 할당합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. On Press 이벤트에 의해 트리거되는 동작 정의

다음과 같이 동작 드롭다운을 클릭합니다. 현재는 **함수 없음**이 할당되었습니다. 그리고 **MeshRenderer** > **재질 재질**을 선택하여 On Press () 이벤트가 트리거될 때 큐브의 재질 속성을 변경하도록 설정합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

다음과 같이 재질 필드 옆에 있는 작은 **원** 아이콘을 클릭하여 [재질 선택] 창을 엽니다. 현재 이 필드는 **없음(재질)** 으로 채워져 있습니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

다음과 같이 [재질 선택] 창에서 **MRTK_Standard**를 **검색**하여 적절한 재질을 선택합니다. 예를 들어 **MRTK_Standard_Cyan**을 선택할 경우 단추를 누르면 큐브의 색이 녹청으로 변합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. On Release 이벤트를 수신하는 큐브 구성

On Release 이벤트에 대해 4단계를 **반복**하여 **큐브**를 **On Release ()** 이벤트의 수신자로 할당합니다.

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. On Release 이벤트에 의해 트리거되는 동작 정의

다음과 같이 On Release 이벤트에 대해 5단계를 **반복**하되, 단추 누르기가 해제되면 큐브의 색이 원래의 밝은 회색으로 돌아가도록 **MRTK_Standard_LightGray** 재질을 선택합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. 편집기 내 시뮬레이션을 사용하여 단추 테스트

**재생** 단추를 눌러 게임 모드로 전환한 다음, 편집기 내 입력 시뮬레이션을 사용하여 새로 구성된 단추를 테스트합니다.

단추를 누르지 않음(스페이스바 + 마우스 스크롤 휠 뒤로):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

단추를 누름(스페이스바 + 마우스 스크롤 휠 앞으로):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> 편집기 내 입력 시뮬레이션을 사용하는 방법은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [편집기 내 손 입력 시뮬레이션을 사용하여 장면 테스트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) 가이드를 참조하세요.

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>MRTK의 Grid Object Collection을 사용하여 단추 패널 만들기

이 섹션에서는 MRTK의 Grid Object Collection 도구를 사용하여 여러 단추를 깔끔한 사용자 인터페이스로 자동 정렬하는 방법을 알아봅니다.

이 예제에서는 단추 5개가 가로로 정렬된 패널을 만드는 방법을 보여줍니다. 다른 레이아웃을 만들 때 이 원칙을 그대로 적용해도 됩니다.

이를 위해 수행할 주요 단계는 다음과 같습니다.

1. 단추 개체를 부모 개체의 부모로 지정
2. Grid Object Collection(스크립트) 구성 요소 추가 및 구성
3. 편집기 내 시뮬레이션을 사용하여 단추 테스트

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. 단추 개체를 부모 개체의 부모로 지정

다음과 같이 [계층 구조] 창 내부의 빈 지점을 마우스 오른쪽 단추로 클릭하고 **빈 항목 만들기**를 선택합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

다음과 같이 새로 만든 개체를 마우스 오른쪽 단추로 클릭하고, **이름 바꾸기**를 선택하여 적절한 이름(예: **ButtonCollection**)을 지정합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

다음과 같이 **PressableButtonHoloLens2** 개체를 선택하고 **ButtonCollection** 개체 위로 **끌어 놓아** ButtonCollection 개체의 자식으로 만듭니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

다음과 같이 **PressableButtonHoloLens2** 개체를 마우스 오른쪽 단추로 클릭하고 **복제**를 선택하여 복사본을 만듭니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

총 5개의 PressableButtonHoloLens2 개체가 생길 때까지 이 단계를 4회 더 **반복**합니다.

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Grid Object Collection(스크립트) 구성 요소 추가 및 구성

다음과 같이 [계층 구조] 창에서 ButtonCollection 개체를 선택하고 [검사기] 창에서 **구성 요소 추가** 단추를 클릭한 다음, **Grid Object Collection**을 검색하고 선택하여 ButtonCollection 개체에 Grid Object Collection(스크립트) 구성 요소를 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

다음과 같이 Grid Object Collection(스크립트)을 구성합니다.

* 모든 단추가 단일 행에 정렬되도록 **숫자 행**을 1로 변경합니다.
* 단추가 행 내부에 있도록 **셀 너비**를 0.05로 변경합니다.

그런 다음, 다음과 같이 **컬렉션 업데이트** 단추를 클릭하여 새 구성을 적용합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> 방금 적용한 구성 변경 내용은 단추를 단일 행에 배치하려는 목표를 달성하는 데 필요한 최소한의 변경 내용을 나타냅니다. 그러나 이후 프로젝트에서 부모 개체와 자식 개체의 방향 등의 요소에 따라 방향 유형과 같은 다른 설정을 조정해야 할 수도 있습니다. MRTK의 Grid Object Collection에 대한 자세한 내용은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [개체 컬렉션 스크립트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) 가이드를 참조하세요.

[계층 구조] 창에서 ButtonCollection 개체를 선택한 상태로, 자식 단추 개체가 카메라 앞에 배치되도록, 즉, 원점에 배치되도록 [검사기] 창에서 ButtonCollection 개체의 변환 **위치**를 변경합니다(예: x = 0, y = 0, z = 0.5).

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> 위의 [손 추적 제스처 및 상호 작용 가능 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 섹션에서 장면에 PressableButtonHoloLens2 프리팹을 처음 추가할 때 프리팹을 카메라 앞에 배치한 것입니다. 그러나 Grid Object Collection은 직계 자식 개체의 위치를 제어하기 때문에 PressableButtonHoloLens2 자식 개체의 Z 위치는 부모 값이 0일 때 Grid Object Collection의 기본 거리에 따라 0으로 다시 설정됩니다. 이러한 이유로, 그리고 부모/자식 위치 관계를 체계적으로 관리하기 위해, PressableButtonHoloLens2 자식 개체를 앞으로 이동하도록 부모 값으로부터의 거리를 구성하는 대신 부모 ButtonCollection 개체의 위치를 앞으로 이동했습니다.

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. 편집기 내 시뮬레이션을 사용하여 단추 테스트

다음과 같이 [재생] 단추를 눌러 게임 모드로 전환한 다음, 편집기 내 입력 시뮬레이션을 사용하여 새로 만든 단추 패널에서 각 단추를 테스트합니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> 현재는 5개 단추 중 하나를 누르면 큐브 색이 녹청으로 변합니다. 보다 흥미로운 환경을 만들려면 방금 배운 내용을 사용하여 큐브를 다른 색으로 변경하도록 각 단추를 구성해 보세요.

## <a name="adding-text-into-your-scene"></a>장면에 텍스트 추가

이 섹션에서는 이전 자습서의 [TextMesh Pro 필수 리소스 가져오기](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) 섹션에서 준비한 Unity의 TextMesh Pro를 사용하여 혼합 현실 환경에 텍스트를 추가하는 방법을 알아봅니다.

이 예제에서는 이전 섹션에서 만든 단추 컬렉션 아래에 간단한 레이블을 추가할 것입니다.

다음과 같이 ButtonCollection 개체를 마우스 오른쪽 단추로 클릭하고 **3D 개체** > **텍스트 - TextMeshPro**를 선택하여 TextMeshPro 개체를 ButtonCollection 개체의 자식으로 만듭니다.

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

새로 만든 텍스트(TMP)라는 TextMeshPro 개체를 선택한 상태로, 레이블이 깔끔하게 단추 컬렉션 아래에 배치되도록 다음 예제처럼 [검사기] 창에서 위치와 크기를 변경합니다.

* 사각형 변환 **세로 위치**를 -0.0425로 변경
* 사각형 변환 **너비**를 0.24로 변경
* 사각형 변환 **높이**를 0.024로 변경

그리고 다음 예제처럼 레이블의 내용을 반영하도록 텍스트를 업데이트하고, 텍스트가 레이블 내에서 잘 어울리도록 글꼴 속성을 선택합니다.

* Text Mesh Pro(스크립트) **텍스트**를 단추 컬렉션으로 변경
* Text Mesh Pro(스크립트) **글꼴 스타일**을 [굵게]로 변경
* Text Mesh Pro(스크립트) **글꼴 크기**를 0.2로 변경
* Text Mesh Pro(스크립트) **맞춤**을 [가운데] 및 [중간]으로 변경

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 MRTK 프로필 설정을 복제, 사용자 지정 및 구성하는 방법을 배웠습니다. HoloLens 2에서 추적 손을 사용하여 단추와 상호 작용하여 이벤트를 트리거하는 방법도 알아보았습니다. 마지막으로 MRTK의 Grid Object Collection 구성 요소와 Unity의 Text Mesh Pro를 사용하여 간단한 UI 인터페이스를 만드는 방법을 알아보았습니다.

[다음 자습서: 4. 동적 콘텐츠 배치 및 해결기 사용](mrlearning-base-ch3.md)
