---
title: 자습서 시작-7. 음력 모듈 샘플 응용 프로그램 만들기
description: 이 단원에서는 이전 단원에서 배운 여러 개념을 결합 하 여 고유한 샘플 환경을 만듭니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: b5b1bd0115822449bd6098f78cfc94d909169737
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129453"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. 음력 모듈 샘플 응용 프로그램 만들기
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

이 자습서에서는 다양 한 개념을 이전 단원에서 결합 하 여 고유한 샘플 환경을 만듭니다. 사용자가 추적 된 손을 사용 하 여 파트를 선택 하 고 음력 모듈을 조합 하 여 구성 해야 하는 파트 어셈블리 응용 프로그램을 만드는 방법을 배웁니다. Pressable 단추를 사용 하 여 배치 힌트를 설정/해제 하 고, 환경을 다시 설정 하 고, 음력 모듈을 공간으로 시작 합니다.

이후 자습서에서는 공간 맞춤을 위해 Azure 공간 앵커를 활용 하는 강력한 다중 사용자 사용 사례를 포함 하 여이 환경을 계속 빌드할 수 있습니다.

## <a name="objectives"></a>목표

* 이전 단원의 여러 개념을 결합하여 고유한 환경 만들기
* 개체를 설정/해제하는 방법 알아보기
* 누를 수 있는 단추를 사용하여 복합 이벤트 트리거
* 강체 물리학 및 힘 사용
* 도구 설명 사용 살펴보기

## <a name="lunar-module-parts-overview"></a>음력 모듈 부분 개요
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

이 섹션에서는 간단한 파트 어셈블리 챌린지를 만듭니다. 여기서 사용자의 목표는 테이블에 분산 된 5 개의 파트를 음력 모듈의 올바른 위치에 배치 하는 것입니다.

이를 위해 수행 하는 주요 단계는 다음과 같습니다.

1. 장면에 로켓 시작 관리자 prefab 추가
2. 모든 파트에 대 한 개체 조작 사용
3. 파트 어셈블리 데모 (스크립트) 구성 요소 추가 및 구성

> [!NOTE]
> 파트 어셈블리 데모 (스크립트) 구성 요소는 MRTK의 일부가 아닙니다. 이 자습서의 자산과 함께 제공 되었습니다.

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. prefab에 로켓 시작 관리자를 추가 합니다.

프로젝트 창에서 **자산** > **mrtk로 이동 합니다. 자습서. Get > ** **Prefabs** 가 시작 > **RocketLauncher** 폴더에서 **RocketLauncher** prefab를 계층 창으로 끌어 장면에 추가 하 고 적절 한 위치에 배치 합니다. 예를 들면 다음과 같습니다.

* X = 1.5, Y =-0.4, Z = 0 위치를 변환 합니다. 그러면 waist height에서 사용자의 오른쪽에 배치 됩니다.
* 변환 회전 X = 0, Y = 180, Z = 0. 따라서 환경의 주요 기능은 사용자에 게 직면 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. 모든 파트에 대 한 개체 조작 사용

계층 구조 창에서 RocketLauncher > **LunarModuleParts** 개체를 찾고 모든 **자식 개체**를 선택한 다음 **조작 처리기 (스크립트)** 구성 요소 및 **Near 인터랙션 Grabbable (스크립트)** 구성 요소를 추가 하 고 조작 처리기 (스크립트)를 다음과 같이 구성 합니다.

* 크기 조정 기능을 사용 하지 않도록 회전을 이동 하도록 **두 손 조작 유형을** 변경 합니다.
* 거의 **조작** 가능 확인란의 선택을 취소 하 여 거의 상호 작용이 가능 하도록 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> 개체 조작을 구현 하는 방법에 대 한 단계별 지침이 포함 된 미리 알림은 [3D 개체 조작](mrlearning-base-ch4.md#manipulating-3d-objects) 지침을 참조할 수 있습니다.

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. 파트 어셈블리 데모 (스크립트) 구성 요소 추가 및 구성

LunarModuleParts 자식 개체가 모두 선택 된 상태에서 **오디오 원본** 구성 요소를 추가 하 고 다음과 같이 구성 합니다.

* 오디오 **클립** 필드에 적합 한 오디오 클립을 할당 합니다 (예: MRKT_Scale_Start
* **재생이 재생** 되 면 재생 확인란을 선택 취소 하 여 장면이 로드 될 때 오디오 클립을 자동으로 재생 하지 않습니다.
* 공간 **Blend** 를 1로 변경 하 여 공간 오디오 사용

![mrlearning-기본](images/mrlearning-base/tutorial6-section1-step2-1.png)

LunarModuleParts 자식 개체가 모두 선택 된 상태에서 **파트 어셈블리 데모 (스크립트)** 구성 요소를 추가 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section1-step2-2.png)

계층 창에서 **Roverenclosure** 개체를 선택 하 고 다음과 같이 **파트 어셈블리 데모 (스크립트)** 구성 요소를 구성 합니다.

* 개체를 **놓을 개체** 에 대해 개체 자체 (이 경우 **roverenclosure** 개체)를 할당 합니다.
* **배치 위치** 필드에 해당 PlacementHints 개체를 할당 합니다 .이 경우에는 **RoverEnclosure_PlacementHints** 개체입니다.
* **도구 설명 개체** 필드에 해당 하는 ToolTipObject (이 경우에는 **RoverEnclosure_ToolTip** 개체)를 할당 합니다.
* **오디오 원본** 필드에 개체 자체 (이 경우 **roverenclosure** 개체)를 할당 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section1-step2-3.png)

FuelTank, EnergyCell, DockingPortal 및 ExternalSensor와 같은 다른 LunarModuleParts 자식 개체 각각에 대해 **반복** 합니다.

이제 게임 모드를 입력 하 고 ' 개체를 ' 위치 '에 가깝게 이동 하려면 다음을 확인 합니다.

* 개체는 LunarModule 개체 아래에 위치 하 고 부모로 되어 있으므로 음력 모듈의 일부가 됩니다.
* 개체의 오디오 소스가 개체의 위치에서 할당 된 오디오 클립을 재생 합니다.
* 해당 하는 도구 설명 개체는 숨겨집니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> 편집기에서 입력 시뮬레이션을 사용 하는 방법에 대 한 미리 알림은 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [편집기 내 입력 시뮬레이션을 사용](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) 하 여 장면 가이드를 테스트 하는 방법을 참조할 수 있습니다.

## <a name="configuring-the-lunar-module"></a>달탐사선 구성

이 섹션에서는 사용자가 다음을 수행할 수 있도록 로켓 시작 관리자 응용 프로그램에 추가 기능을 추가 합니다.

* 음력 모듈과 상호 작용
* 공간으로 음력 모듈을 시작 하 고 시작 시 소리 재생
* 음력 모듈과 모든 파트가 원래 위치에 다시 배치 되도록 응용 프로그램을 다시 설정 합니다.
* 파트 어셈블리 챌린지를 더 어렵게 만들기 위해 배치 힌트를 숨깁니다.

이를 위해 수행 하는 주요 단계는 다음과 같습니다.

1. 개체 조작 사용
2. 물리 사용
3. 오디오 원본 구성 요소 추가
4. 시작 음력 모듈 (스크립트) 구성 요소 추가 및 구성
5. 배치 힌트 (스크립트) 구성 요소 추가 및 구성

> [!NOTE]
> 시작 음력 모듈 (스크립트) 구성 요소와 전환 배치 힌트 (스크립트) 구성 요소는 MRTK의 일부가 아닙니다. 이 자습서의 자산과 함께 제공 되었습니다.

### <a name="1-enable-object-manipulation"></a>1. 개체 조작 사용

계층 구조 창에서 RocketLauncher > **LunarModule** 개체를 선택 하 고 **조작 처리기 (스크립트)** 구성 요소 및 **Near 인터랙션 Grabbable (스크립트)** 구성 요소를 추가한 다음 조작 처리기 (스크립트)를 다음과 같이 구성 합니다.

* 크기 조정 기능을 사용 하지 않도록 회전을 이동 하도록 **두 손 조작 유형을** 변경 합니다.
* 거의 **조작** 가능 확인란의 선택을 취소 하 여 거의 상호 작용이 가능 하도록 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. 물리학 사용

RocketLauncher > **LunarModule** 개체가 선택 된 상태에서 Rigidbody 구성 요소를 추가 하 고 다음과 같이 구성 합니다.

* 음력의 영향을 받지 않도록 **중력 사용** 확인란을 선택 취소 합니다.
* 처음에는 음력 모듈이 physic의 영향을 받지 않도록 하려면 **기구학** 확인란을 선택 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. 오디오 원본 구성 요소 추가

RocketLauncher > **LunarModule** 개체가 선택 된 상태에서 **오디오 원본** 구성 요소를 추가 하 고 다음과 같이 구성 합니다.

* 공간 **Blend** 를 1로 변경 하 여 공간 오디오 사용

![mrlearning-기본](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. Launch 음력 모듈 (스크립트) 구성 요소를 추가 하 고 구성 합니다.

RocketLauncher > **LunarModule** 개체를 선택한 상태에서 **시작 음력 모듈 (스크립트)** 구성 요소를 추가 하 고 다음과 같이 구성 합니다.

* **위한 것** 값을 변경 하 여 음력 모듈이 시작 될 때 정상적으로 실행 되도록 합니다 (예: 0.01).

![mrlearning-기본](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. 배치 힌트 (스크립트) 구성 요소를 추가 하 고 구성 합니다.

RocketLauncher > **LunarModule** 개체가 선택 된 상태에서 **설정/해제 배치 힌트 (스크립트)** 구성 요소를 추가 하 고 다음과 같이 구성 합니다.

* Game 개체 배열 **크기** 속성을 5로 설정 합니다.
* 각 **PlacementHints** 개체의 **자식 개체** 를 Game 개체 배열의 **요소** 필드에 할당 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>시작 단추 구성

계층 창에서 RocketLauncher > 단추 > **launchbutton** 개체를 선택한 다음 **Pressable 단추 (스크립트)** 구성 요소에서 새 **단추 누름 ()** 이벤트를 만들고, 이벤트를 받도록 **LunarModule** 개체를 구성 하 고, 트리거할 작업으로 **LaunchLunarModule** 를 정의 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> 이벤트를 구현 하는 방법에 대 한 미리 알림은 [손 추적 제스처 및 interactable 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 지침을 참조할 수 있습니다.

RocketLauncher > 단추 > **launchbutton** 개체를 선택 하 고 **Pressable 단추 (스크립트)** 구성 요소에서 새 **단추 누름 ()** 이벤트를 만들고, 이벤트를 받도록 **LunarModule** 개체를 구성 하 고, 트리거할 작업으로 **PlayOneShot** 을 정의 하 고, 오디오 **클립** 필드 (예: MRTK_Gem 오디오 클립)에 적절 한 오디오 클립을 할당 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section3-step1-2.png)

RocketLauncher > 단추 > **launchbutton** 개체를 선택한 상태에서 **Pressable 단추 (스크립트)** 구성 요소에서 새 **Touch 종료 ()** 이벤트를 만들고, 이벤트를 받도록 **LunarModule** 개체를 구성 하 고, 트리거할 작업으로 **LaunchLunarModule** 를 정의 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section3-step1-3.png)

이제 게임 모드를 입력 하 고 시작 단추를 누르면 오디오 클립이 재생 되 고, 두 번째 이상에 대해 시작 단추를 누르고 있는 경우 음력 모듈이 다음 공간에 표시 됩니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>다시 설정 단추 구성

계층 창에서 RocketLauncher > 단추 > **resetbutton** 개체를 선택 하 고, **Pressable 단추 (스크립트)** 구성 요소에서 새 **단추 누름 ()** 이벤트를 만들고, 이벤트를 받도록 **LunarModule** 개체를 구성 하 고, 트리거할 작업으로 **LaunchLunarModule 모듈** 을 정의 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section4-step1-1.png)

RocketLauncher > 단추 > **resetbutton** 개체를 선택 하 고 **Pressable 단추 (스크립트)** 구성 요소에서 새 **단추 누름 ()** 이벤트를 만들고, 이벤트를 받도록 **RocketLauncher** 개체를 구성 하 고, 트리거할 작업으로 **GameObject** 를 정의 하 고, 메시지 필드에 **resetbutton** 를 입력 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> GameObject BroadcastMessage 작업은 RocketLauncher 개체에서 모든 자식 개체에 ResetPlacement 메시지를 보냅니다. 모든 LunarModuleParts 자식 개체에 추가한 파트 어셈블리 데모 (스크립트) 구성 요소에 정의 된 ResetPlacement 함수를 포함 하는 자식 개체는 자식 개체의 배치를 다시 설정 하는 ResetPlacement 함수를 호출 합니다.

이제 게임 모드를 입력 하 고 다시 설정 단추를 누르면 재생 중인 오디오 클립이 표시 되 고 공간에 시작 되는 음력 모듈이 표시 됩니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>배치 힌트 단추 구성
<!-- TODO: Rename to 'Configuring the Hints button'-->

계층 창에서 RocketLauncher > 단추 > **Hintsbutton** 개체를 선택한 다음 **Pressable 단추 (스크립트)** 구성 요소에서 새 **단추 누름 ()** 이벤트를 만들고 **LunarModule** 개체를 구성 하 여 이벤트를 수신 하 고, 트리거할 작업 **을 정의 합니다.**

![mrlearning-기본](images/mrlearning-base/tutorial6-section5-step1-1.png)

이제 게임 모드를 입력 하면 반투명 배치 힌트가 기본적으로 사용 하지 않도록 설정 되어 있지만 힌트 단추를 눌러 설정 및 해제할 수 있습니다.

![mrlearning-기본](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>축하합니다.

이 응용 프로그램을 완전히 구성 했습니다. 이제 응용 프로그램을 통해 사용자는 음력 모듈을 완전히 조합 하 고, 음력 모듈을 시작 하 고, 힌트를 설정/해제 하 고, 응용 프로그램을 다시 시작할 수 있습니다.
