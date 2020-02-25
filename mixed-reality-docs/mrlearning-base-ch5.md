---
title: 자습서 시작-6. 고급 입력 옵션 탐색
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: aaa02ce118fd051d94311e837b143affc96ff72b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554255"
---
# <a name="6-exploring-advanced-input-options"></a>6. 고급 입력 옵션 탐색

이 자습서에서는 음성 명령, 패닝 제스처 및 눈 추적 사용을 포함 하 여 HoloLens 2에 대 한 몇 가지 고급 입력 옵션을 탐색 합니다.

## <a name="objectives"></a>목표

* 음성 명령 및 키워드를 사용 하 여 이벤트 트리거
* 추적 된 손을 사용 하 여 추적 된 손으로 텍스처 및 3D 개체를 이동 합니다.
* HoloLens 2 눈동자 추적 기능을 활용 하 여 개체 선택

## <a name="enabling-voice-commands"></a>음성 명령 사용
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

이 섹션에서는 사용자가 Octa 개체에서 소리를 재생할 수 있도록 음성 명령을 구현 합니다. 이렇게 하려면 새 음성 명령을 만든 다음 speech command 키워드를 말할 때 원하는 작업을 트리거하기 위해 이벤트를 구성 합니다.

이를 위해 수행 하는 주요 단계는 다음과 같습니다.

1. 기본 입력 시스템 프로필을 복제 합니다.
2. 기본 음성 명령 프로필을 복제 합니다.
3. 새 음성 명령 만들기
4. 음성 입력 처리기 (스크립트) 구성 요소 추가 및 구성
5. Speech 명령에 대 한 응답 이벤트 구현

### <a name="1-clone-the-default-input-system-profile"></a>1. 기본 입력 시스템 프로필을 복제 합니다.

계층 구조 창에서 **MixedRealityToolkit** 개체를 선택한 다음, 검사기 창에서 **입력** 탭을 선택 하 고 **DefaultHoloLens2InputSystemProfile** 을 복제 하 여 사용자 지정 가능한 **입력 시스템 프로필로**바꿉니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> MRTK 프로필을 복제 하는 방법에 대 한 미리 알림은 [Mixed Reality Toolkit 프로필을 구성](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 하는 방법 지침을 참조할 수 있습니다.

### <a name="2-clone-the-default-speech-commands-profile"></a>2. 기본 음성 명령 프로필을 복제 합니다.

**음성** 섹션을 확장 하 고 **DefaultMixedRealitySpeechCommandsProfile** 를 복제 하 여 사용자 지정 가능한 **음성 명령 프로필로**바꿉니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. 새 음성 명령 만들기

**음성 명령** 섹션에서 **+ 새 음성 명령 추가** 단추를 클릭 하 여 기존 음성 명령 목록의 맨 아래에 새 음성 명령을 추가 하 고, **키워드** 필드에 적절 한 단어나 구를 입력 합니다 (예: **음악 재생**:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> 컴퓨터에 마이크가 없고 편집기에서 시뮬레이션을 사용 하 여 음성 명령을 테스트 하려는 경우 해당 키를 누를 때 트리거할 수 있도록 음성 명령에 KeyCode를 할당할 수 있습니다.

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. 음성 입력 처리기 (스크립트) 구성 요소 추가 및 구성

계층 창에서 **Octa** 개체를 선택 하 고 Octa 개체에 **음성 입력 처리기 (스크립트)** 구성 요소를 추가 합니다. 그런 다음 사용자가 Octa 개체를 확인 하 여 음성 명령을 트리거할 필요가 없도록 **포커스 필요** 확인란의 선택을 취소 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. 음성 명령에 대 한 응답 이벤트 구현

음성 입력 처리기 (스크립트) 구성 요소에서 작은 **+** 단추를 클릭 하 여 키워드 목록에 키워드 요소를 추가 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

새로 만든 **요소 0** 을 클릭 하 여 확장 한 다음 **키워드** 드롭다운에서 이전에 만든 **음악 재생** 키워드를 선택 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> 키워드 드롭다운의 키워드는 음성 명령 프로필의 음성 명령 목록에 정의 된 키워드를 기준으로 채워집니다.

새 **응답 ()** 이벤트를 만들고, 이벤트를 받도록 **Octa** 개체를 구성 하 고, 트리거할 작업으로 **PlayOneShot** 를 정의 하 고, 오디오 **클립** 필드에 적합 한 오디오 클립을 할당 합니다 (예: MRTK_Gem 오디오 클립).

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> 이벤트를 구현 하 고 오디오 클립을 할당 하는 방법에 대 한 미리 알림은 [터치 시작 시의 구현 이벤트](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) 지침을 참조할 수 있습니다.

## <a name="the-pan-gesture"></a>이동 제스처

이동 제스처는 손가락을 사용 하 여 스크롤 하거나 콘텐츠를 스크롤 하는 데 유용 합니다. 이 예제에서는 먼저 2D UI를 스크롤한 다음 3D 개체의 컬렉션을 스크롤할 수 있도록이를 확장 하는 방법을 알아봅니다.

이를 위해 수행 하는 주요 단계는 다음과 같습니다.

1. 패닝에 사용할 수 있는 쿼드 개체 만들기
2. Near 인터랙션 Touchable (스크립트) 구성 요소 추가
3. 직접 상호 작용 팬 확대/축소 (스크립트) 구성 요소 추가
4. 스크롤할 2D 콘텐츠 추가
5. 스크롤할 3D 콘텐츠 추가
6. 이동 (스크립트) 구성 요소를 사용 하 여 이동 추가

> [!NOTE]
> 이동 이동 (스크립트) 구성 요소가 MRTK의 일부가 아닙니다. 이 자습서의 자산과 함께 제공 되었습니다.

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. 패닝에 사용할 수 있는 쿼드 개체 만들기

계층 창에서 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 **3D 개체** > **4** 를 선택 하 여 장면에 쿼드를 추가 합니다. 적절 한 이름 (예: **Pangesture**)을 지정 하 고 적절 한 위치에 배치 합니다 (예: X = 0, Y =-0.2, Z = 2).

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> 3D 쿼드와 같은 Unity 기본 형식을 장면에 추가 하는 방법에 대 한 미리 알림은 [장면에 큐브 추가](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) 지침을 참조할 수 있습니다.

다른 모든 상호 작용 에서처럼 이동 제스처에는 collider도 필요 합니다. 기본적으로 쿼드에는 메시 collider가 있습니다. 그러나 메시 collider는 매우 씬 이기 때문에 이상적이 지 않습니다. 사용자가 collider와 쉽게 상호 작용할 수 있도록 메시 collider를 box collider로 바꿉니다.

PanGesture 개체를 선택한 상태에서 **메시 collider** Component의 **설정** 아이콘을 클릭 하 고 **구성 요소 제거** 를 선택 하 여 메시 collider를 제거 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 **상자 collider**를 추가한 다음 collider **Size** Z 상자를 0.15으로 변경 하 여 상자 collider의 두께를 늘립니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. Near 인터랙션 Touchable (스크립트) 구성 요소 추가

**Pangesture** 개체를 선택한 상태에서 **near 인터랙션 Touchable (스크립트)** 구성 요소를 pangestoutobject에 추가 하 고 **범위 수정** 및 **수정 센터** 단추를 클릭 하 여 near Touchable (스크립트)의 로컬 센터 및 범위 속성을 boxcollider와 일치 하도록 업데이트 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. 직접 상호 작용 팬 확대/축소 (스크립트) 구성 요소를 추가 합니다.

**Pangesture** 개체를 선택 하 고 나 서 **상호 작용 이동 확대/축소 (스크립트)** 구성 요소를 pangesture 개체에 추가한 다음 **가로 잠금** 확인란을 선택 하 여 세로 스크롤만 허용 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. 스크롤할 2D 콘텐츠를 추가 합니다.

프로젝트 패널에서 창 **콘텐츠** 자료를 검색 한 다음,이를 클릭 하 여 **pangesture** 의 메시 렌더러 **재질** 요소 0 속성으로 끌어 놓습니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

검사기 창에서 새로 추가 된 창 **콘텐츠** 재질 구성 요소를 확장 한 다음 X 값과 일치 하 고 타일이 사각형으로 표시 되도록 **바둑판식 배열** Y 값을 0.5로 변경 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

이제 게임 모드를 입력 하는 경우 편집기 내 시뮬레이션의 이동 제스처를 사용 하 여 2D 콘텐츠 스크롤을 테스트할 수 있습니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. 스크롤할 3D 콘텐츠를 추가 합니다.

계층 창에서 **4 개의 큐브** 를 **pangesture** 개체의 자식 개체로 만들고 해당 변환 **배율을** X = 0.15, Y = 0.15, Z = 0.15로 설정 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

큐브를 균등 하 게 공간을 절약 하 고 일정 시간을 절약 하려면 **표 개체 컬렉션 (스크립트)** 구성 요소를 큐브의 부모 개체 (예: **pangestlaobject** )에 추가 하 고 다음과 같이 그리드 개체 컬렉션 (스크립트)을 구성 합니다.

* **행** 수를 1로 변경 하 여 모든 큐브를 하나의 단일 행에 정렬 합니다.
* **셀 너비** 를 0.25으로 변경 하 여 행 내의 큐브 공간을 확보 합니다.

그런 다음 **컬렉션 업데이트** 단추를 클릭 하 여 새 구성을 적용 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. 패닝 (스크립트) 구성 요소를 사용 하 여 이동 추가

계층 창에서 모든 **큐브 자식 개체**를 선택한 다음, 검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 **위아래로 이동 (스크립트)** 구성 요소를 모든 큐브에 추가 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> 계층 창에서 여러 개체를 선택 하는 방법에 대 한 미리 알림은 [모든 개체에 조작 처리기 (스크립트) 구성 요소 추가](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) 명령을 참조할 수 있습니다.

모든 큐브를 선택 하 고 나 서 다음을 클릭 하 여 **Pangesture** 개체를 **이동 입력 원본** 필드에 놓습니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> 각 큐브의 이동 이동 (스크립트) 구성 요소는 HandInteractionPanZoom (스크립트) 구성 요소에서 보낸 팬 업데이트 이벤트를 위 단계에서 이동 입력 원본으로 할당 한 후 각 큐브의 위치를 업데이트 하는 것을 수신 합니다. 올바르게.

계층 창에서 **Pangestkeobject** 를 선택 하 고 검사기에서 메시 **렌더러** **확인 취소** 확인란을 선택 취소 하 여 메시 렌더러 구성 요소를 사용 하지 않도록 설정 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

이제 게임 모드를 입력 하는 경우 편집기 내 시뮬레이션의 이동 제스처를 사용 하 여 3D 콘텐츠 스크롤을 테스트할 수 있습니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>시선 추적

이 섹션에서는 프로젝트에서 눈 추적을 사용 하도록 설정 하는 방법을 설명 합니다. 이 예에서는 사용자의 눈 응시에서 확인 하는 동안 3DObjectCollection의 각 개체를 천천히 회전 하는 기능을 구현 하 고, 선택 하는 개체가 공중 탭 또는 음성 명령에 의해 선택 되는 경우에는 블 립 효과를 트리거합니다.

이를 위해 수행 하는 주요 단계는 다음과 같습니다.

1. 모든 대상 개체에 눈동자 추적 대상 (스크립트) 구성 요소 추가
2. 모든 대상 개체에 눈동자 추적 자습서 데모 (스크립트) 구성 요소 추가
3. 대상 이벤트를 찾는 동안을 구현 합니다.
4. 선택한 이벤트에 대해를 구현 합니다.
5. 편집기 내 시뮬레이션에 대해 시뮬레이션 된 눈 추적 사용
6. Visual Studio 프로젝트의 앱 기능에서 응시 입력 사용

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. 모든 대상 개체에 눈 추적 대상 (스크립트) 구성 요소를 추가 합니다.

계층 구조 창에서 **3DObjectCollection** 개체를 확장 하 고 모든 **자식 개체**를 선택한 다음, 검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 모든 자식 개체에 **눈 추적 대상 (스크립트)** 구성 요소를 추가 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

모든 **자식 개체가** 선택 된 상태에서 다음과 같이 **눈 추적 대상 (스크립트)** 구성 요소를 구성 합니다.

* 선택 **작업** **선택을 선택**하 여이 개체에 대 한 공기 탭 작업을 선택으로 정의 합니다.
* **음성 선택** 을 확장 하 고 음성 명령 목록 **크기** 를 1로 설정한 다음 나타나는 새 요소 목록에서 **요소 0** 을 **선택**으로 변경 하 여이 개체에 대 한 음성 명령 작업을 select로 정의 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. 모든 대상 개체에 눈동자 추적 자습서 데모 (스크립트) 구성 요소를 추가 합니다.

모든 **자식 개체** 를 선택 하 고 나 서 **구성 요소 추가** 단추를 사용 하 여 모든 자식 개체에 **눈동자 추적 자습서 데모 (스크립트)** 구성 요소를 추가 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> 아이 추적 대상 (스크립트) 구성 요소가 MRTK의 일부가 아닙니다. 이 자습서의 자산과 함께 제공 되었습니다.

### <a name="3-implement-the-while-looking-at-target-event"></a>3. 대상 이벤트를 찾는 동안을 구현 합니다.

계층 창에서 **치즈** 개체를 선택한 다음 **Target () 이벤트를 찾는 동안** 새를 만들고, 이벤트를 받도록 **치즈** 개체를 구성 하 고, 트리거할 작업으로 RotateTarget를 정의 **합니다** .

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

3DObjectCollection의 각 자식 개체에 대해 **반복** 합니다.

> [!TIP]
> 이벤트를 구현 하는 방법에 대 한 미리 알림은 [손 추적 제스처 및 interactable 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 지침을 참조할 수 있습니다.

### <a name="4-implement-the-on-selected-event"></a>4. 선택한 이벤트에 대해를 구현 합니다.

계층 구조 창에서 **치즈** 개체를 선택 하 고, **선택 된 () 이벤트에** 새 이벤트를 만들고, 이벤트를 받도록 **치즈** 개체를 구성 하 고, 트리거할 액션으로 BlipTarget를 정의 **합니다** .

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

3DObjectCollection의 각 자식 개체에 대해 **반복** 합니다.

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. 편집기 내 시뮬레이션에 대해 시뮬레이션 된 눈동자 추적 사용

계층 구조 창에서 **MixedRealityToolkit** 개체를 선택한 다음, 검사기 창에서 입력 탭을 선택 하 **고 입력** **데이터 공급자** 섹션을 확장 한 다음 입력 **시뮬레이션 서비스** 섹션을 확장 하 고 **DefaultMixedRealityInputSimulationProfile** 을 복제 하 여 사용자 지정 가능한 **입력 시뮬레이션 프로필로**바꿉니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> MRTK 프로필을 복제 하는 방법에 대 한 미리 알림은 [Mixed Reality Toolkit 프로필을 구성](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 하는 방법 지침을 참조할 수 있습니다.

눈 **시뮬레이션** 섹션에서 눈 **위치 시뮬레이트** 확인란을 선택 하 여 눈동자 추적 시뮬레이션을 사용 하도록 설정 합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

이제 게임 모드를 입력 하는 경우 커서가 개체 중 하나에 적중 하도록 뷰를 조정 하 고 직접 상호 작용 또는 음성 명령을 사용 하 여 개체를 선택 하 여 구현 된 회전 및 나선 효과를 테스트할 수 있습니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> [혼합 현실 도구 키트 구성](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) 에 설명 된 대로 DefaultHoloLens2ConfigurationProfile를 사용 하 여 사용자 지정 가능한 MRTK 구성 프로필을 복제 하지 않은 경우 프로젝트에서 눈 추적을 사용 하도록 설정할 수 없으며 사용 하도록 설정 해야 합니다. 이를 위해 [MRTK의 눈동자 추적 시작](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) 지침을 참조할 수 있습니다.

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. Visual Studio 프로젝트의 앱 기능에서 응시 입력 사용

Visual Studio에서 장치로 앱을 빌드하고 배포 하기 전에 프로젝트의 앱 기능에서 응시 입력을 사용 하도록 설정 해야 합니다. 이를 위해 [HoloLens 2 지침에서 Unity 앱 테스트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) 를 수행할 수 있습니다.

## <a name="congratulations"></a>축하합니다.

응용 프로그램에 기본 눈 추적 기능을 추가 했습니다. 이러한 작업은 시선 추적 기능 활용의 시작에 불과합니다. 이 자습서에서는 음성 명령 및 패닝 제스처와 같은 기타 고급 입력 기능에 대해서도 알아보았습니다.

[다음 단원: 7. 음력 모듈 샘플 응용 프로그램 만들기](mrlearning-base-ch6.md)
