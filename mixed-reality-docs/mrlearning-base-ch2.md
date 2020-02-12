---
title: 자습서를 시작 합니다. 3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 067832a130f130ffbaa8d455007b8e77e1b13671
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130535"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

이전 자습서에서는 HoloLens 2에 대 한 첫 번째 응용 프로그램을 시작 하 여 혼합 현실 도구 키트 (MRTK)가 제공 해야 하는 기능 중 일부에 대해 알아보았습니다. 이 자습서에서는 UI 텍스트 패널과 함께 단추를 만들고 구성 하 고, 터치 (기본 상호 작용)를 사용 하 여 각 단추와 상호 작용 하는 방법을 배웁니다. 개체의 크기, 사운드 및 색상 변경과 같은 간단한 작업과 효과도 추가로 살펴봅니다. 이 모듈에서는 [공간 매핑](spatial-mapping.md) 메시 시각화를 해제 하는 것부터 MRTK 프로필 수정에 대 한 기본 개념을 소개 합니다.

## <a name="objectives"></a>목표

* Mixed Reality Toolkit 프로필 사용자 지정 및 구성
* UI 요소 및 단추를 사용 하 여 holograms와 상호 작용
* 기본적인 손 추적 입력 및 상호 작용

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Mixed Reality Toolkit 프로필을 구성 하는 방법 (공간 인식 표시 옵션 변경)
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

이 섹션에서는 기본 MRTK 프로필을 사용자 지정 하 고 구성 하는 방법을 알아봅니다.

이 특정 예제에서는 공간 메시 관찰자의 설정을 변경 하 여 공간 인식 메시를 숨기는 방법을 보여 줍니다. 그러나이 동일한 원칙에 따라 MRTK 프로필의 설정 또는 값을 사용자 지정할 수 있습니다.

공간 인식 메시를 숨기기 위해 수행 하는 주요 단계는 다음과 같습니다.

1. 기본 구성 프로필 복제
2. 공간 인식 시스템 사용
3. 기본 공간 인식 시스템 프로필을 복제 합니다.
4. 기본 공간 인식 메시 관찰자 프로필 복제
5. 공간 인식 메시의 표시 유형 변경

> [!NOTE]
> 기본적으로 MRTK 프로필은 편집할 수 없습니다. 이러한 템플릿은 편집 하기 전에 복제 해야 하는 기본 프로필 템플릿입니다. 여러 개의 중첩 된 프로필 계층이 있습니다. 따라서 하나 이상의 설정을 구성할 때 여러 프로필을 복제 하 고 편집 하는 것이 일반적입니다.

### <a name="1-clone-the-default-configuration-profile"></a>1. 기본 구성 프로필을 복제 합니다.

> [!NOTE]
> 구성 프로필은 최상위 수준 프로필입니다. 따라서 다른 프로필을 편집할 수 있으려면 먼저 구성 프로필을 복제 해야 합니다.

계층 창에서 **MixedRealityToolkit** 개체를 선택한 상태에서 검사기 창에서 **복사 & 사용자 지정** 단추를 클릭 하 여 복제 프로필 창을 엽니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step1-1.png)

복제 프로필 창에서 **복제** 단추를 클릭 하 여 **DefaultHololens2ConfigurationProfile**의 편집 가능한 복사본을 만듭니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step1-2.png)

이제 새로 만든 구성 프로필이 장면의 구성 프로필로 할당 됩니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step1-3.png)

Unity 메뉴에서 **파일** > **저장** 을 선택 하 여 장면을 저장 합니다.

> [!TIP]
> 자습서 전체에서 작업을 저장 해야 합니다.

### <a name="2-enable-the-spatial-awareness-system"></a>2. 공간 인식 시스템 사용

계층 창에서 **MixedRealityToolkit** 개체를 선택 하 고 검사기 창에서 **공간 인식** 탭을 선택한 후 **공간 인식 시스템 사용** 확인란을 선택 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. 기본 공간 인식 시스템 프로필을 복제 합니다.

**공간 인식** 탭에서 **복제** 단추를 클릭 하 여 복제 프로필 창을 엽니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step3-1.png)

복제 프로필 창에서 **복제** 단추를 클릭 하 여 **DefaultMixedRealitySpatialAwarenessSystemProfile**의 편집 가능한 복사본을 만듭니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step3-2.png)

이제 새로 만든 공간 인식 시스템 프로필이 구성 프로필에 자동으로 할당 됩니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. 기본 공간 인식 메시 관찰자 프로필을 복제 합니다.

**공간 인식** 탭을 선택한 상태에서 **Windows Mixed Reality 공간 메시 관찰자** 섹션을 확장 한 다음 **복제** 단추를 클릭 하 여 복제 프로필 창을 엽니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step4-1.png)

복제 프로필 창에서 **복제** 단추를 클릭 하 여 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**의 편집 가능한 복사본을 만듭니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step4-2.png)

새로 만든 공간 인식 메시 관찰자 프로필은 이제 공간 인식 시스템 프로필에 자동으로 할당 됩니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. 공간 인식 메시의 표시 여부를 변경 합니다.

**공간 메시 관찰자 설정**에서 **표시 옵션** 을 **폐색** 로 변경 하 여 공간 매핑 메시를 계속 작동 하는 동안 표시 하지 않도록 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> 공간 매핑 메시는 표시 되지 않지만 여전히 존재 하 고 작동 합니다. 예를 들어 실제 벽 뒤의 홀로그램 처럼 공간 매핑 메시 뒤의 holograms은 표시 되지 않습니다.

MRTK 프로필에서 설정을 수정하는 방법을 알아보았습니다. 여기서 볼 수 있듯이 MRTK 설정을 사용자 지정 하려면 먼저 기본 프로필의 복사본을 만들어야 합니다. 기본 프로필을 편집할 수 없기 때문에 기본 설정으로 되돌리려면 항상 해당 프로필을 참조로 사용할 수 있습니다. MRTK 프로필 및 해당 아키텍처에 대해 자세히 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [Mixed Reality Toolkit 프로필 구성 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) 를 참조 하세요.

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>제스처 및 interactable 단추 수동 추적

이 섹션에서는 단추를 누를 때 작업을 발생 시키는 단추를 누르고 이벤트를 트리거하는 데 수동 추적을 사용 하는 방법을 배웁니다.

이 특정 예제에서는 단추를 누를 때 큐브의 색을 변경 하 고 단추가 해제 될 때 원래의 색으로 다시 변경 하는 방법을 보여 줍니다. 그러나 이러한 동일한 원칙에 따라 다른 이벤트를 만들 수 있습니다.

큐브의 색을 변경 하기 위해 수행 하는 주요 단계는 다음과 같습니다.

1. 장면에 pressable 단추 prefab 추가
2. 장면에 큐브 추가
3. InteractableOnPressReceiver 이벤트 유형 구성
4. On Press 이벤트를 받도록 큐브 구성
5. On Press 이벤트에서 트리거할 작업을 정의 합니다.
6. On Release 이벤트를 받도록 큐브 구성
7. On Release 이벤트에서 트리거할 작업을 정의 합니다.
8. 편집기 내 시뮬레이션을 사용 하 여 단추 테스트

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. 장면에 pressable 단추 prefab 추가

> [!TIP]
> <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> 는 Unity 자산으로 저장 되 고 프로젝트 전체에서 다시 사용할 수 있는 미리 구성 된 GameObject입니다.

**프로젝트 창**에서 **PressableButtonHoloLens2** 를 검색 하 여이 예제에 사용할 prefab를 찾습니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step1-1.png)

**검색** 결과에서 **PressableButtonHoloLens2** prefab를 선택 하 고 **계층** 창으로 **끌어** 장면에 추가 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> 아래 이미지에 표시 된 것 처럼 장면을 표시 하려면 계층 창에서 PressableButtonHoloLens2 개체를 두 번 클릭 하 여 포커스를 가져온 다음 장면 창의 오른쪽 위 모퉁이에 있는 <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Gizmo 장면을</a>사용 하 여 보기 각도를 앞으로 Z 축을 따라 조정 합니다.

PressableButtonHoloLens2 개체가 선택 된 상태에서 **검사기** 창에서 다음을 수행 합니다.

* 원본에 위치 하는 카메라 앞에 배치 되도록 변환 **위치** 를 변경 합니다 (예: x = 0, y = 0 및 z = 0.5).

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> 일반적으로 Unity에서 1 위치 단위는 물리적 세계에서 1 미터와 거의 동일 합니다. 그러나 개체가 크기 조정 된 개체의 자식인 경우와 같이이에 대 한 예외도 있습니다.

### <a name="2-add-a-cube-to-the-scene"></a>2. 장면에 큐브 추가

계층 창 내부의 빈 지점을 마우스 오른쪽 단추로 클릭 하 고 **3D 개체** > **큐브** 를 선택 하 여 큐브를 장면에 추가 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step2-1.png)

선택한 큐브 개체를 사용 하 여 **검사기** 창에서 다음을 수행 합니다.

* Pressable 단추 근처에 있지만 (예: x = 0, y = 0.04 및 z = 0.5)와 겹치지 않도록 변환 **위치** 를 변경 합니다.
* 변환 **배율을** 적절 한 크기로 변경 합니다 (예: x = 0.02, y = 0.02 및 z = 0.02).

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. Interactableon보도 Sreceiver 이벤트 유형 구성

계층 창에서 선택한 PressableButtonHoloLens2 개체를 사용 하 여 **검사기** 창 **햄버거 메뉴**에서 **Collaps 모든 구성 요소** 를 선택 하 여이 개체의 모든 구성 요소에 대 한 개요를 가져옵니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step3-1.png)

**Interactable (스크립트)** 구성 요소를 확장 한 다음 **이벤트** > **수신자** 섹션을 찾아 확장 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step3-2.png)

이벤트 수신기 유형 **Interactableonpressreceiver**에서 **상호 작용 필터** 를 **Near 및 Far**로 변경 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> Interactableon보도 Sreceiver 이라는 이벤트 수신기 유형을 사용 하면 추적 된 손을 단추를 누를 때 눌린 이벤트에 응답할 수 있습니다.

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. On Press 이벤트를 받도록 큐브 구성

계층 창에서 **큐브** 를 **클릭 하 고** **on press ()** 이벤트에 대 한 **이벤트 속성** 개체 필드로 끌어 큐브를 on press () 이벤트의 받는 사람으로 할당 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. On Press 이벤트에서 트리거할 작업을 정의 합니다.

작업 드롭다운 (현재 **함수 없음**)을 클릭 하 고 **MeshRenderer** > **자재 자료** 를 선택 하 여 On Press () 이벤트가 트리거될 때 변경할 큐브의 재질 속성을 설정 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step5-1.png)

재질 필드 옆에 있는 작은 **원** 아이콘 **(재질)** 을 클릭 하 여 재질 선택 창을 엽니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step5-2.png)

재질 선택 창에서 **MRTK_Standard** 을 **검색** 하 고 적절 한 재질을 선택 합니다. 예를 들어, 단추를 누르면 큐브의 색이 녹청으로 변경 되도록 **MRTK_Standard_Cyan** .

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. On Release 이벤트를 받도록 큐브 구성

**반복** On Release 이벤트의 경우 4 단계를 통해 릴리스 () 이벤트의 받는 사람으로 큐브를 할당 합니다.

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. On Release 이벤트에서 트리거할 작업을 정의 합니다.

**반복** On Release 이벤트에 대해 5 단계 이지만, 단추가 해제 될 때 큐브의 색이 원래의 밝은 회색 색으로 반환 되도록 **MRTK_Standard_LightGray** 재질을 선택 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. 편집기 내 시뮬레이션을 사용 하 여 단추 테스트

**재생** 단추를 눌러 게임 모드로 전환 하 고 편집기 내 입력 시뮬레이션을 사용 하 여 새로 구성 된 단추를 테스트 합니다.

단추를 누르지 않음 (스페이스바 + 마우스 스크롤 휠):

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step8-1.png)

단추 누름 (스페이스바 + 마우스 스크롤 휠을 앞으로):

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> 편집기에서 입력 시뮬레이션을 사용 하는 방법을 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [편집기 내 입력 시뮬레이션을 사용](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) 하 여 장면 가이드를 테스트 하는 방법을 참조할 수 있습니다.

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>MRTK의 Grid Object Collection을 사용하여 버튼 패널 만들기

이 섹션에서는 MRTK의 Grid 개체 수집 도구를 사용 하 여 자동으로 여러 단추를 깔끔한 사용자 인터페이스로 맞추는 방법에 대해 설명 합니다.

이 특정 예제에서는 5 개의 단추가 가로로 맞춰진 패널을 만드는 방법을 보여 줍니다. 그러나 이러한 동일한 원칙에 따라 다른 레이아웃을 만들 수 있습니다.

이를 위해 수행 하는 주요 단계는 다음과 같습니다.

1. 부모 개체에 대 한 단추 개체의 부모
2. Grid 개체 컬렉션 (스크립트) 구성 요소 추가 및 구성
3. 편집기에서 시뮬레이션을 사용 하 여 단추 테스트

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. 부모 개체에 대 한 단추 개체의 부모

계층 창 내부에서 빈 지점을 마우스 오른쪽 단추로 클릭 하 고 **빈 만들기**를 선택 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step1-1.png)

새로 만든 개체를 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 선택 하 여 적절 한 이름을 지정 합니다 (예: **buttoncollection**).

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step1-2.png)

**PressableButtonHoloLens2** 개체를 선택 하 고 **buttoncollection** 개체의 위쪽 **으로 끌어** buttoncollection 개체의 자식으로 만듭니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step1-3.png)

**PressableButtonHoloLens2** 개체를 마우스 오른쪽 단추로 클릭 하 고 **복제** 를 선택 하 여 복사본을 만듭니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step1-4.png)

총 5 개의 PressableButtonHoloLens2 개체가 나올 때까지이 단계를 4 번 더 **반복** 합니다.

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. 그리드 개체 컬렉션 (스크립트) 구성 요소 추가 및 구성

계층 창에서 ButtonCollection 개체를 선택 하 고 검사기 창에서 **구성 요소 추가** 단추를 클릭 한 다음 **표 개체 컬렉션** 을 검색 하 고 선택 하 여 Buttoncollection 개체에 그리드 개체 컬렉션 (스크립트) 구성 요소를 추가 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step2-1.png)

다음과 같이 그리드 개체 컬렉션 (스크립트)을 구성 합니다.

* 단일 행에 모든 단추가 정렬 되도록 **Num 행** 을 1로 변경 합니다.
* **셀 너비** 를 0.05으로 변경 하 여 행 내의 단추를 공백으로 이동 합니다.

그런 다음 **컬렉션 업데이트** 단추를 클릭 하 여 새 구성을 적용 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> 방금 적용 한 구성 변경 내용은 단추를 단일 행에 배치 하는 목표를 달성 하는 데 필요한 최소 변경 내용을 나타냅니다. 그러나 이후 프로젝트에서 부모 개체와 자식 개체의 방향 등의 요소에 따라 방향 유형과 같은 다른 설정을 조정 해야 할 수 있습니다. MRTK의 그리드 개체 컬렉션에 대해 자세히 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [개체 컬렉션 스크립트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) 가이드를 참조 하세요.

계층 창에서 ButtonCollection 개체를 선택한 상태에서 Inspector 창에서 ButtonCollection 개체의 변환 **위치** 를 변경 하 여 자식 단추 개체가 카메라 앞에 배치 되도록 합니다. 즉, x = 0, y = 0, z = 0.5과 같이 원점에 배치 됩니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> 위의 [손을 tracking 제스처 및 interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 섹션의 장면에 PressableButtonHoloLens2 prefab를 처음 추가 하면 카메라 앞에 배치 합니다. 그러나 Grid 개체 컬렉션은 직계 자식 개체의 위치를 제어 하기 때문에 PressableButtonHoloLens2 자식 개체의 Z 위치는 부모 값 0의 기본 거리에 따라 0으로 다시 설정 됩니다. 부모/자식 위치 관계를 구성 하기 위해 부모 값에서 거리를 구성 하는 대신 부모 ButtonCollection 개체의 위치를 앞으로 이동 하는 이유는 PressableButtonHoloLens2 자식 개체를 앞으로 이동 하는 것입니다.

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. 편집기 내 시뮬레이션을 사용 하 여 단추 테스트

재생 단추를 눌러 게임 모드로 전환 하 고 편집기 내 입력 시뮬레이션을 사용 하 여 새로 만든 단추 패널의 각 단추를 테스트 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> 현재 5 개 단추 중 하나를 누르면 큐브 색이 녹청로 바뀝니다. 더 흥미로운 환경을 만들려면 각 단추를 구성 하 여 큐브를 다른 색으로 변경 하는 방법에 대해 배운 내용을 사용 합니다.

## <a name="adding-text-into-your-scene"></a>장면에 텍스트 추가

이 섹션에서는 이전 자습서의 [Textmesh Pro 필수 리소스 가져오기](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) 섹션에서 준비한 Unity의 Textmesh pro를 사용 하 여 혼합 현실 환경에 텍스트를 추가 하는 방법을 알아봅니다.

이 특정 예제에서는 이전 섹션에서 만든 단추 컬렉션 아래에 간단한 레이블을 추가 합니다.

ButtonCollection 개체를 마우스 오른쪽 단추로 클릭 하 고 **3D 개체** > **선택 하 여 TextMeshPro** 개체를 buttoncollection 개체의 자식으로 만듭니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section4-step1-1.png)

검사기 창에서 새로 만든 TextMeshPro 개체 (TMP) 라는 텍스트 (TMP)를 사용 하 여 해당 위치와 크기를 변경 하면 레이블이 단추 컬렉션 아래에 깔끔하게 배치 됩니다. 예를 들면 다음과 같습니다.

* Rect Transform **Pos Y** 를-0.0425로 변경 합니다.
* Rect 변환 **너비** 를 0.24으로 변경
* Rect 변환 **높이** 를 0.024으로 변경

그런 다음 레이블을 반영 하도록 텍스트를 업데이트 하 고 텍스트를 레이블 내에 맞추기 위해 글꼴 속성을 선택 합니다. 예를 들면 다음과 같습니다.

* 텍스트 메시 Pro (스크립트) **텍스트** 를 단추 컬렉션으로 변경
* 텍스트 메시 Pro (스크립트) **글꼴 스타일** 을 굵게 변경
* 텍스트 메시 Pro (스크립트) **글꼴 크기** 를 0.2으로 변경 합니다.
* 텍스트 메시 Pro (스크립트) **맞춤** 을 가운데 및 중간으로 변경 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 MRTK 프로필 설정을 복제, 사용자 지정 및 구성 하는 방법을 배웠습니다. 또한 HoloLens 2에서 추적 된 실습을 사용 하 여 이벤트를 트리거하는 단추와 상호 작용 하는 방법도 배웠습니다. 마지막으로, MRTK의 그리드 개체 컬렉션 구성 요소 및 Unity의 텍스트 메시 Pro를 사용 하 여 간단한 UI 인터페이스를 만드는 방법을 알아보았습니다.

[다음 자습서: 4. 동적 콘텐츠 배치 및 solvers 사용](mrlearning-base-ch3.md)
