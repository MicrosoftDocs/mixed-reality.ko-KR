---
title: 시작 자습서 - 9. 음성 명령 사용
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: b0b9771d9569d100a354af96a34cd20ef2a3d7c4
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376595"
---
# <a name="9-using-speech-commands"></a>9. 음성 명령 사용

## <a name="overview"></a>개요

이 자습서에서는 음성 명령을 만드는 방법과 전역적으로 제어하는 방법을 알아봅니다. 음성 명령을 제어하는 개체를 사용자가 쳐다봐야 하는 로컬 음성 명령을 제어하는 방법에 대해서도 알아봅니다.

## <a name="objectives"></a>목표

* 음성 명령을 만드는 방법 알아보기
* 전역적으로 및 로컬에서 음성 명령을 제어하는 방법 알아보기

## <a name="ensuring-the-microphone-capability-is-enabled"></a>마이크 기능을 사용하도록 설정되어 있는지 확인

Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > **Unity 프로젝트 구성**을 선택하여 **MRTK Project Configurator** 창을 열고 **UWP 기능** 섹션에서 **Enable Microphone Capability**(마이크 기능 사용)가 회색으로 표시되는지 확인합니다.

![mr-learning-base](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> 이 자습서 시리즈의 시작 부분에서 Unity 프로젝트를 구성할 때 [MRTK Project Configurator 설정 적용](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) 지침을 진행하는 동안 마이크 기능을 사용하도록 설정되어 있어야 합니다. 하지만 사용하도록 설정되지 않으면 지금 사용하도록 설정해야 합니다.

## <a name="creating-speech-commands"></a>음성 명령 만들기

Hierarchy(계층 구조) 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector(인스펙터) 창에서 MixedRealityToolkit > **입력** 탭을 선택하고 다음 단계를 수행합니다.

* **Speech**(음성) 섹션 펼치기
* **DefaultMixedRealitySpeechCommandsProfile**을 복제하여 적절한 이름(예: _GettingStarted_MixedRealitySpeechCommandsProfile_)을 지정
* **Start Behaviour**(동작 시작)가 **Auto Start**(자동 시작)로 설정되어 있는지 확인

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> MRTK 프로필을 복제하는 방법은 [MRTK 프로필 구성](mr-learning-base-03.md) 지침을 참조하세요.

Speech(음성) > **Speech Commands**(음성 명령) 섹션에서 **+ Add a New Speech Command**(새 음성 명령 추가) 단추를 4번 클릭하여 새 음성 명령 4개를 기존 음성 명령 목록에 추가한 다음, **키워드** 필드에 다음 문구를 입력합니다.

* Enable Indicator(표시기 사용)
* Enable Tap to Place(탭하여 위치 지정 사용)
* Enable Bounding Box(경계 상자 사용)
* Disable Bounding Box(경계 상자 사용 안 함)

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> 컴퓨터에 마이크가 없는 경우 음성 명령에 KeyCode를 할당하면 해당 키를 누를 때 명령을 트리거할 수 있습니다.

## <a name="controlling-speech-commands"></a>음성 명령 제어

프로젝트 창에서 **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** 폴더로 이동하여 도구 설명 프리팹을 찾습니다.

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-1.png)

Hierarchy(계층 구조) 창에서 빈 지점을 마우스 오른쪽 단추로 클릭하고, **Create Empty**(빈 개체 생성)를 선택하여 빈 개체를 장면에 추가합니다.

개체 이름을 **SpeechInputHandler_Global**로 지정한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **SpeechInputHandler** 구성 요소를 추가하고 다음과 같이 구성합니다.

* 음성 명령을 트리거하기 위해 SpeechInputHandler 구성 요소가 있는 개체를 사용자가 쳐다보지 않아도 되도록, **Is Focus Required**(포커스 필요) 확인란을 **선택 취소**
* 음성 명령이 인식될 때 프리팹이 나타나도록, 프로젝트 창에서 **SpeechConfirmation Tooltip** 프리팹을 **Speech Confirmation Tooltip Prefab**(음성 확인 도구 설명 프리팹) 필드에 할당

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-2.png)

SpeechInputHandler 구성 요소에서 작은 **+** 아이콘을 3번 클릭하여 키워드 요소를 3개 추가합니다.

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-3.png)

**Element 0**(요소 0)을 펼치고 다음과 같이 구성합니다.

* 이전 섹션에서 만든 Enable Indicator(표시기 사용) 음성 명령을 참조하도록 **키워드** 필드에 **Enable Indicator**(표시기 사용)를 입력
* 작은 **+** 아이콘을 클릭하여 이벤트를 추가
* Hierarchy(계층 구조) 창에서 **Indicator**(표시기) 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **GameObject** > **SetActive (bool)** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정
* 인수 확인란이 **선택**되어 있는지 확인

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-4.png)

**Element 1**(요소 1)을 펼치고 다음과 같이 구성합니다.

* 이전 섹션에서 만든 Enable Bounding Box(경계 상자 사용) 명령을 참조하도록 **키워드** 필드에 **Enable Bounding Box**(경계 상자 사용)를 입력
* 작은 **+** 아이콘을 클릭하여 이벤트를 추가
* Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **BoundingBox** > **bool enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트
* 인수 확인란이 **선택**되어 있는지 확인
* 작은 **+** 아이콘을 클릭하여 또 다른 이벤트를 추가
* Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **ObjectManipulator** > **bool enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트
* 인수 확인란이 **선택**되어 있는지 확인

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-5.png)

**Element 2**(요소 2)를 펼치고 다음과 같이 구성합니다.

* 이전 섹션에서 만든 Disable Bounding Box(경계 상자 사용 안 함) 명령을 참조하도록 **키워드** 필드에 **Disable Bounding Box**(경계 상자 사용 안 함)를 입력
* 작은 **+** 아이콘을 클릭하여 이벤트를 추가
* Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **BoundingBox** > **bool enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트
* 인수 확인란이 **선택 취소**되어 있는지 확인
* 작은 **+** 아이콘을 클릭하여 또 다른 이벤트를 추가
* Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **ObjectManipulator** > **bool enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트
* 인수 확인란이 **선택 취소**되어 있는지 확인

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-6.png)

Hierarchy(계층 구조) 창에서 RoverExplorer > **RoverAssembly** 개체를 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **SpeechInputHandler** 구성 요소를 추가하고 다음과 같이 구성합니다.

* 음성 명령을 트리거하기 위해 SpeechInputHandler 구성 요소(예: RoverAssembly)가 있는 개체를 사용자가 쳐다봐야 하도록, **Is Focus Required**(포커스 필요) 확인란을 **선택**
* 음성 명령이 인식될 때 프리팹이 나타나도록, 프로젝트 창에서 **SpeechConfirmation Tooltip** 프리팹을 **Speech Confirmation Tooltip Prefab**(음성 확인 도구 설명 프리팹) 필드에 할당

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-7.png)

SpeechInputHandler 구성 요소에서 작은 **+** 아이콘을 클릭하여 키워드 요소를 추가하고 새로 만든 요소를 펼친 후, 다음과 같이 구성합니다.

* 이전 섹션에서 만든 Enable Tap to Place(탭하여 위치 지정 사용) 명령을 참조하도록 **키워드** 필드에 **Enable Tap to Place**(탭하여 위치 지정 사용)를 입력
* 작은 **+** 아이콘을 클릭하여 이벤트를 추가
* Hierarchy(계층 구조) 창에서 개체 자체(즉, 동일한 **RoverAssembly** 개체)를 **None (Object)** 필드에 할당
* **No Function**(함수 없음) 드롭다운에서 **TapToPlace** > **bool enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트
* 인수 확인란이 **선택**되어 있는지 확인

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 음성 명령을 만드는 방법과 전역적으로 제어하는 방법을 알아보았습니다. 음성 명령을 제어하는 개체를 사용자가 쳐다봐야 하는 로컬 음성 명령을 제어하는 방법에 대해서도 알아보았습니다.

이것으로 [시작 자습서](mr-learning-base-01.md) 시리즈를 마칩니다. 이 자습서를 통해 MRTK를 사용하여 처음부터 완전 혼합 현실 경험을 성공적으로 구축했습니다.

다음 두 가지 자습서 시리즈인 [Azure Spatial Anchors 자습서](mr-learning-asa-01.md) 및 [다중 사용자 기능 자습서](mr-learning-sharing-01.md)에서는 먼저 Azure Spatial Anchors를 프로젝트에 통합하여 직접 만든 Rover Explorer 경험을 실제 세계에서 고정하는 방법을 알아봅니다. 그런 다음, 다중 사용자 기능을 프로젝트에 추가하여 사용자와 개체 움직임을 실시간으로 공유하는 방법을 설명합니다.
