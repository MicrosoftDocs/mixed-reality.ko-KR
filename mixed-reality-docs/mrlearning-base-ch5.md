---
title: 시작 자습서 - 6. 고급 입력 옵션 탐색
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 9a19ad59e520a2743aafd954910f43c6f51d6c8a
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441860"
---
# <a name="6-exploring-advanced-input-options"></a>6. 고급 입력 옵션 탐색

이 자습서에서는 음성 명령, 이동 제스처 및 시선 추적을 비롯한 HoloLens 2의 몇 가지 고급 입력 옵션을 살펴봅니다.

## <a name="objectives"></a>목표

* 음성 명령 및 키워드를 사용하여 이벤트 트리거
* 추적 손을 사용하여 추적 손으로 텍스처 및 3D 개체 이동
* HoloLens 2 시선 추적 기능을 활용하여 개체 선택

## <a name="enabling-voice-commands"></a>음성 명령 사용
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

이 섹션에서는 사용자가 Octa 개체에서 소리를 재생할 수 있도록 음성 명령을 실행합니다. 이를 위해 새 음성 명령을 생성한 다음, 음성 명령 키워드가 사용될 때 원하는 동작을 트리거하도록 이벤트를 구성합니다.

이를 위해 수행할 주요 단계는 다음과 같습니다.

1. 기본 입력 시스템 프로필 복제
2. 기본 음성 명령 프로필 복제
3. 새 음성 명령 만들기
4. 음성 입력 처리기(스크립트) 구성 요소 추가 및 구성
5. 음성 명령에 대한 응답 이벤트 구현

### <a name="1-clone-the-default-input-system-profile"></a>1. 기본 입력 시스템 프로필 복제
[계층 구조] 창에서 **MixedRealityToolkit** 개체를 선택하고 [검사기] 창에서 **입력** 탭을 선택한 다음, **DefaultHoloLens2InputSystemProfile**을 복제하여 개발자의 사용자 지정 가능한 **입력 시스템 프로필**로 바꿉니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!NOTE]
> MRTK 2.4.0 이상을 사용하는 경우 다음을 수행합니다.
> * [계층 구조] 탭에서 **MixedRealityToolkit** 개체를 선택한 다음, [검사기] 창에서 **입력** 탭을 클릭하여 **포인터** 섹션을 펼칩니다. 
> * **DefaultMixedRealityInputPointerProfile**을 복제하고, 사용자 지정 가능한 **입력 포인터 프로필**로 바꿉니다.
> * **응시 설정** 섹션에서 **시선 추적 사용**이 true인지 확인합니다. 

> [!TIP]
> MRTK 프로필을 복제하는 방법에 대한 자세한 내용은 [Mixed Reality Toolkit 프로필을 구성하는 방법](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 지침을 참조하세요.

### <a name="2-clone-the-default-speech-commands-profile"></a>2. 기본 음성 명령 프로필 복제

**음성** 섹션을 확장하고, **DefaultMixedRealitySpeechCommandsProfile**을 복제하여 개발자의 사용자 지정 가능한 **음성 명령 프로필**로 바꿉니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. 새 음성 명령 만들기

**음성 명령** 섹션에서 **+새 음성 명령 추가** 단추를 클릭하여 기존 음성 명령 목록의 맨 아래에 새 음성 명령을 추가한 다음, **키워드** 필드에 적절한 단어 또는 구(예: **음악 재생**)를 입력합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> 컴퓨터에 마이크가 없고 편집기 내 시뮬레이션을 사용하여 음성 명령을 테스트하려는 경우 해당 키를 누를 때 트리거할 수 있는 음성 명령에 KeyCode를 할당할 수 있습니다.

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. 음성 입력 처리기(스크립트) 구성 요소 추가 및 구성

[계층 구조] 창에서 **Octa** 개체를 선택하고 **음성 입력 처리기(스크립트)** 구성 요소를 Octa 개체에 추가합니다. 그런 다음, 사용자가 음성 명령을 트리거하기 위해 Octa 개체를 볼 필요가 없도록 **Is Focus Required** 확인란의 선택을 취소합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. 음성 명령에 대한 응답 이벤트 구현

음성 입력 처리기(스크립트) 구성 요소에서 작은 **+** 단추를 클릭하여 키워드 목록에 키워드 요소를 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

새로 생성한 **요소 0**을 클릭하여 확장한 다음, **키워드** 드롭다운에서 이전에 만든 **음악 재생** 키워드를 선택합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> 키워드 드롭다운의 키워드는 음성 명령 프로필의 음성 명령 목록에 정의된 키워드에 따라 채워집니다.

새 **Response ()** 이벤트를 만들고, 이벤트를 수신하도록 **Octa** 개체를 구성하고, **AudioSource.PlayOneShot**를 트리거할 작업으로 정의하고, 적절한 오디오 클립(예: MRTK_Gem 오디오 클립)을 **오디오 클립** 필드에 할당합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> 이벤트를 구현하고 오디오 클립을 할당하는 방법에 대한 자세한 내용은 [On Touch Started 이벤트 구현](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) 지침을 참조하세요.

## <a name="the-pan-gesture"></a>이동 제스처

이동 제스처는 손가락이나 손을 사용하여 내용을 스크롤하는 데 유용합니다. 이 예제에서는 먼저 2D UI를 스크롤한 다음, 이 UI를 확장하여 3D 개체 컬렉션을 스크롤하는 방법을 알아봅니다.

이를 위해 수행할 주요 단계는 다음과 같습니다.

1. 상하좌우 이동에 사용할 수 있는 쿼드 개체 만들기
2. 근거리 터치형 상호 작용(스크립트) 구성 요소 추가
3. 직접 상호 작용 팬 확대/축소(스크립트) 구성 요소 추가
4. 스크롤할 2D 콘텐츠 추가
5. 스크롤할 3D 콘텐츠 추가
6. 팬으로 이동(스크립트) 구성 요소 추가

> [!NOTE]
> 팬을 사용하여 이동(스크립트) 구성 요소는 MRTK에 포함되지 않습니다. 이 자습서의 자산과 함께 제공되었습니다.

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. 상하좌우 이동에 사용할 수 있는 쿼드 개체 만들기

[계층 구조] 창에서 마우스 오른쪽 단추로 빈 영역을 클릭하고, **3D 개체** > **쿼드**를 선택하여 장면에 쿼드를 추가합니다. 적절한 이름(예: **PanGesture**)을 지정하고, 적절한 위치(예: X = 0, Y = -0.2, Z = 2)에 배치합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> 3D 쿼드와 같은 유니티 기본값을 장면에 추가하는 방법에 대한 자세한 내용은 [장면에 큐브 추가](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) 지침을 참조하세요.

다른 모든 상호 작용과 마찬가지로, 팬 제스처에도 충돌체가 필요합니다. 기본적으로 쿼드에는 메시 충돌체가 있습니다. 그러나 메시 충돌체는 너무 얇아서 적합하지 않습니다. 사용자가 충돌체와 보다 쉽게 상호작용할 수 있도록 메시 충돌체를 박스 충돌체로 교체하겠습니다.

다음과 같이 PanGesture 개체를 선택한 상태에서 **메시 충돌체** 구성 요소의 **설정** 아이콘을 클릭하고, **구성 요소 제거**를 선택하여 메시 충돌체를 제거합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

다음과 같이 [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **상자 충돌체**를 추가한 다음, 상자 충돌체 **크기** Z를 0.15로 변경하여 상자 충돌체의 두께를 늘립니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. 근거리 터치형 상호 작용(스크립트) 구성 요소 추가

다음과 같이 **PanGesture** 개체를 선택한 상태에서 **근거리 터치형 상호 작용(스크립트)** 구성 요소를 PanGesture 개체에 추가한 다음, **경계 고정** 및 **중심 고정** 단추를 클릭하여 근거리 터치형 상호 작용(스크립트)의 로컬 중심 및 경계 속성을 BoxCollider에 맞게 업데이트합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. 직접 상호 작용 팬 확대/축소(스크립트) 구성 요소 추가

다음과 같이 **PanGesture** 개체를 선택한 상태에서 **직접 상호 작용 팬 확대/축소(스크립트)** 구성 요소를 PanGesture 개체에 추가한 다음, **가로 잠금** 확인란을 선택하여 세로 스크롤만 허용합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. 스크롤할 2D 콘텐츠 추가

다음과 같이 [프로젝트] 패널에서 **PanContent** 자료를 검색한 다음, 클릭하여 **PanGesture** 개체의 메시 렌더러 **재질** 요소 0 속성으로 끌어 놓습니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

다음과 같이 [검사기] 창에서 새로 추가된 **PanContent** 재질 구성 요소를 확장한 다음, X 값과 일치하고 타일이 사각형으로 표시되도록 **바둑판식 배열** Y 값을 0.5로 변경합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

이제 다음과 같이 게임 모드로 전환하면 편집기 내 시뮬레이션의 이동 제스처를 사용하여 2D 콘텐츠 스크롤을 테스트할 수 있습니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. 스크롤할 3D 콘텐츠 추가

다음과 같이 [계층 구조] 창에서 **PanGesture** 개체의 자식 개체로 **4개 큐브를 만들고** 변환 **배율**을 X = 0.15, Y = 0.15, Z = 0.15로 설정합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

큐브를 균등하게 분할하고 일정 시간을 절약하려면 다음과 같이 큐브의 부모 개체(즉, **PanGesture** 개체)에 **Grid 개체 컬렉션(스크립트)** 구성 요소를 추가하고 Grid Object Collection(스크립트)을 구성합니다.

* 모든 큐브가 단일 행에 정렬되도록 **숫자 행**을 1로 변경합니다.
* 큐브가 행 내부에 있도록 **셀 너비**를 0.25로 변경합니다.

그런 다음, 다음과 같이 **컬렉션 업데이트** 단추를 클릭하여 새 구성을 적용합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. 팬으로 이동(스크립트) 구성 요소 추가

다음과 같이 [계층 구조] 창에서 모든 **큐브 자식 개체**을 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 모든 큐브에 **팬으로 이동(스크립트)** 구성 요소를 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> [계층 구조] 창에서 여러 개체를 선택하는 방법에 대한 내용은 [모든 개체에 조작 처리기(스크립트) 구성 요소 추가](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)를 참조하세요.

다음과 같이 모든 큐브를 선택한 상태에서 **PanGesture** 개체를 클릭하여 **팬 입력 원본** 필드로 끌어 놓습니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> 각 큐브의 팬으로 이동(스크립트) 구성 요소는 위의 단계에서 팬 입력 원본으로 할당한 PanGesture 개체의 HandInteractionPanZoom(스크립트) 구성 요소에서 보낸 팬 업데이트 이벤트를 수신 대기하다가 각 큐브의 위치를 적절하게 업데이트합니다.

다음과 같이 [계층 구조] 창에서 **PanGesture** 개체를 선택한 다음, [검사기] 창에서 **메시 렌더러** 확인란을 **선택 취소**하여 메시 렌더러 구성 요소를 사용하지 않도록 설정합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

이제 다음과 같이 게임 모드로 전환하면 편집기 내 시뮬레이션의 이동 제스처를 사용하여 3D 콘텐츠 스크롤을 테스트할 수 있습니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>시선 추적

이 섹션에서는 프로젝트에서 시선 추적을 사용하도록 설정하는 방법을 살펴봅니다. 이 예에서는 사용자가 응시하는 동안 3DObjectCollection의 각 개체를 천천히 회전하고, 응시 중인 개체를 에어 탭 또는 음성 명령으로 선택하면 블립 효과를 트리거하는 기능을 구현하겠습니다.

이를 위해 수행할 주요 단계는 다음과 같습니다.

1. 모든 대상 개체에 시선 추적 대상(스크립트) 구성 요소 추가
2. 모든 대상 개체에 시선 추적 자습서 데모(스크립트) 구성 요소 추가
3. While Looking At Target 이벤트 구현
4. On Selected 이벤트 구현
5. 편집기 내 시뮬레이션에 시뮬레이션된 눈 추적 사용
6. Visual Studio 프로젝트의 앱 기능에서 응시 입력 사용

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. 모든 대상 개체에 시선 추적 대상(스크립트) 구성 요소 추가

다음과 같이 [계층 구조] 창에서 **3DObjectCollection**을 확장하고 모든 **자식 개체**를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 모든 자식 개체에 **시선 추적 대상(스크립트)** 구성 요소를 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

다음과 같이 모든 **자식 개체**를 선택한 상태에서 **시선 추적 대상(스크립트)** 구성 요소를 구성합니다.

* **동작 선택**을 **선택**으로 변경하여 이 개체의 에어 탭 동작을 [선택]으로 정의합니다.
* **음성 선택**을 확장하고 음성 명령 목록 **크기**를 1로 설정한 다음, 나타나는 새 요소 목록에서 **요소 0**을 **선택**으로 변경하여 이 개체의 음성 명령 동작을 [선택]으로 정의합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. 모든 대상 개체에 시선 추적 자습서 데모(스크립트) 구성 요소 추가

다음과 같이 모든 **자식 개체**를 선택한 상태에서 **구성 요소 추가** 단추를 사용하여 모든 자식 개체에 **시선 추적 자습서 데모(스크립트)** 구성 요소를 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> 시선 추적 대상(스크립트) 구성 요소는 MRTK의 일부가 아닙니다. 이 자습서의 자산과 함께 제공되었습니다.

### <a name="3-implement-the-while-looking-at-target-event"></a>3. While Looking At Target 이벤트 구현

[계층 구조] 창에서 **Cheese** 개체를 선택한 다음, 새 **While Looking At Target ()** 이벤트를 만들고, 이벤트를 수신하도록 **Cheese** 개체를 구성하고, 트리거할 동작으로 **EyeTrackingTutorialDemo.RotateTarget**을 정의합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

3DObjectCollection의 자식 개체마다 이 과정을 **반복**합니다.

> [!TIP]
> 이벤트를 구현하는 방법에 대한 내용은 [손 추적 제스처 및 상호 작용 가능 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 지침을 참조하세요.

### <a name="4-implement-the-on-selected-event"></a>4. On Selected 이벤트 구현

다음과 같이 [계층 구조] 창에서 **Cheese** 개체를 선택한 다음, 새 **On Selected ()** 이벤트를 만들고, 이벤트를 수신하도록 **Cheese** 개체를 구성하고, 트리거할 동작으로 **EyeTrackingTutorialDemo.BlipTarget**을 정의합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

3DObjectCollection의 자식 개체마다 이 과정을 **반복**합니다.

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. 편집기 내 시뮬레이션에 시뮬레이션된 눈 추적 사용

다음과 같이 [계층 구조] 창에서 **MixedRealityToolkit** 개체를 선택한 다음, [검사기] 창에서 **입력** 탭을 선택하고, **입력 데이터 공급자** 섹션을 확장하고, **입력 시뮬레이션 서비스** 섹션을 확장하고, **DefaultMixedRealityInputSimulationProfile**을 복제하여 개발자의 사용자 지정 가능한 **입력 시뮬레이션 프로필**로 바꿉니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> MRTK 프로필을 복제하는 방법에 대한 자세한 내용은 [Mixed Reality Toolkit 프로필을 구성하는 방법](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 지침을 참조하세요.

**시선 시뮬레이션** 섹션에서 **시선 위치 시뮬레이션** 확인란을 선택하여 시선 추적 시뮬레이션을 사용하도록 설정합니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

게임 모드로 전환하면 다음과 같이 커서가 개체 중 하나를 가리키도록 조정하고 손 상호 작용 또는 음성 명령으로 개체를 선택하여 앞에서 구현한 회전 및 블립 효과를 테스트할 수 있습니다.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> [Mixed Reality Toolkit 구성](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) 지침에 설명된 대로 DefaultHoloLens2ConfigurationProfile을 사용하여 사용자 지정 가능 MRTK 구성 프로필을 복제하지 않은 경우 프로젝트에서 시선 추적을 사용하도록 설정되지 않았을 수 있으며, 이 경우 사용하도록 설정해야 합니다. 설정 방법은 [MRTK에서 시선 추적 시작](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) 지침을 참조하세요.

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. Visual Studio 프로젝트의 앱 기능에서 응시 입력 사용

Visual Studio에서 앱을 빌드하여 디바이스에 배포하기 전에, 프로젝트의 앱 기능에서 응시 입력을 사용하도록 설정해야 합니다. 이렇게 하려면 [HoloLens 2에서 Unity 앱 테스트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) 지침을 따르세요.

## <a name="congratulations"></a>축하합니다.

애플리케이션에 기본적인 시선 추적 기능을 추가했습니다. 이러한 작업은 시선 추적 기능 활용의 시작에 불과합니다. 이 자습서에서는 음성 명령 및 이동 제스처와 같은 기타 고급 입력 기능에 대해서도 알아보았습니다.

[다음 단원: 7. 달착륙선 샘플 애플리케이션 만들기](mrlearning-base-ch6.md)
