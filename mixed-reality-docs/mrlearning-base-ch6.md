---
title: 시작 자습서 - 7. 달착륙선 샘플 애플리케이션 만들기
description: 이 단원에서는 이전 단원에서 학습한 여러 개념을 결합하여 고유한 샘플 환경을 만듭니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031554"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. 달착륙선 샘플 애플리케이션 만들기
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

이 자습서에서는 이전 단원에서 학습한 여러 개념을 결합하여 고유한 샘플 환경을 만듭니다. 사용자가 추적 손을 사용하여 달착륙선 부품을 선택하고 조립을 시도하는 데 사용할 부품 어셈블리 애플리케이션을 만드는 방법을 알아봅니다. 누를 수 있는 단추를 사용하여 배치 힌트를 설정/해제하고, 환경을 다시 설정하고, 달착륙선을 우주로 발사합니다.

향후 자습서에서는 공간 맞춤을 위해 Azure Spatial Anchors를 사용하는 강력한 다중 사용자 사용 사례를 포함하여 이 환경을 지속적으로 구축해 나갈 것입니다.

## <a name="objectives"></a>목표

* 이전 단원의 여러 개념을 결합하여 고유한 환경 만들기
* 개체를 설정/해제하는 방법 알아보기
* 누를 수 있는 단추를 사용하여 복합 이벤트 트리거
* 강체 물리학 및 힘 사용
* 도구 설명 사용 살펴보기

## <a name="lunar-module-parts-overview"></a>달착륙선 부품 개요
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

이 섹션에서는 간단한 부품 어셈블리 챌린지를 만듭니다. 여기서 사용자의 목표는 테이블 위에 흩어져 있는 부품 5개를 달착륙선의 올바른 위치에 배치하는 것입니다.

이를 위해 수행할 주요 단계는 다음과 같습니다.

1. 장면에 로켓 발사대 프리팹 추가
2. 모든 부품에 개체 조작 사용
3. 부품 어셈블리 데모(스크립트) 구성 요소 추가 및 구성

> [!NOTE]
> 부품 어셈블리 데모(스크립트) 구성 요소는 MRTK에 포함되지 않습니다. 이 자습서의 자산과 함께 제공되었습니다.

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. 장면에 로켓 발사대 프리팹 추가

[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** 폴더로 이동하여 **RocketLauncher** 프리팹을 [계층 구조] 창으로 끌어 장면에 추가한 다음, 적절한 위치에 배치합니다. 예를 들어 다음 위치에 배치합니다.

* 변환 위치 X = 1.5, Y =-0.4, Z = 0. 사용자의 오른쪽에 허리 높이로 배치됩니다.
* 변환 회전 X = 0, Y = 180, Z = 0. 환경의 주요 부분이 사용자를 향합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. 모든 부품에 개체 조작 사용

다음과 같이 [계층 구조] 창에서 RocketLauncher > **LunarModuleParts** 개체를 찾아 모든 **하위 개체**를 선택하고, **조작 처리기(스크립트)** 구성 요소와 **근거리 잡기형 상호 작용(스크립트)** 구성 요소를 추가한 다음, 조작 처리기(스크립트)를 구성합니다.

* 근거리 상호 작용만 허용하도록 **원거리 조작 허용** 확인란을 선택 취소합니다.
* 크기 조정을 사용하지 않도록 **양손 조작 유형**을 **이동 회전**으로 변경합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> 다시 말씀드리지만, 개체 조작을 구현하는 방법에 대한 단계별 지침은 [3D 개체 조작](mrlearning-base-ch4.md#manipulating-3d-objects) 지침을 참조하세요.

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. 부품 어셈블리 데모(스크립트) 구성 요소 추가 및 구성

모든 LunarModuleParts 자식 개체를 선택한 상태에서 **오디오 원본** 구성 요소를 추가하고 다음과 같이 구성합니다.

* **오디오 클립** 필드에 적절한 오디오 클립(예: MRKT_Scale_Start)을 할당합니다
* 장면이 로드될 때 오디오 클립이 자동으로 재생되지 않도록 **Play On Awake(절전 모드 해제 시 재생)** 확인란을 선택 취소합니다.
* **공간 블렌드**를 1로 변경하여 공간 오디오를 사용하도록 설정합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

다음과 같이 모든 LunarModuleParts 자식 개체를 선택한 상태에서 **부품 어셈블리 데모(스크립트)** 구성 요소를 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

다음과 같이 [계층 구조] 창에서 **RoverEnclosure** 개체를 선택하고 해당 **부품 어셈블리 데모(스크립트)** 구성 요소를 구성합니다.

* **Object To Place(배치할 개체)** 필드에 개체 **자체**를 할당합니다. 여기서는 RoverEnclosure 개체입니다.
* **Location To Place(배치할 위치)** 필드에 해당하는 **PlacementHints** 개체를 할당합니다. 여기서는 RoverEnclosure_PlacementHint 개체입니다.
* **Tool Tip Object(도구 설명 개체)** 필드에 해당하는 **도구 설명**을 할당합니다. 여기서는 RoverEnclosure_ToolTip 개체입니다.
* **오디오 원본** 필드에 개체 **자체**를 할당합니다. 여기서는 RoverEnclosure 개체입니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

FuelTank, EnergyCell, DockingPortal, ExternalSensor 등의 다른 LunarModuleParts 자식 개체에도 같은 과정을 **반복**합니다.

이제 게임 모드로 전환하여 '배치할 개체'를 해당하는 '배치할 위치'에 가깝게 이동하면 다음과 같은 현상을 볼 수 있습니다.

* 개체가 제 위치에 배치되고 LunarModule 개체 아래에 부모 개체로 지정되므로 달착륙선의 부품이 됩니다.
* 개체의 오디오 원본이 개체의 위치에서 할당된 오디오 클립을 재생합니다.
* 해당하는 도구 설명 개체는 숨겨집니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> 편집기 내 입력 시뮬레이션을 사용하는 방법을 다시 보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [편집기 내 손 입력 시뮬레이션을 사용하여 장면 테스트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) 가이드를 참조하세요.

## <a name="configuring-the-lunar-module"></a>달탐사선 구성

이 섹션에서는 사용자가 다음을 수행할 수 있도록 로켓 발사대 애플리케이션에 기능을 추가합니다.

* 달착륙선과 상호 작용
* 달착륙선을 우주로 발사하고, 발사할 때 소리 재생
* 달착륙선과 모든 부품이 다시 원래 위치에 배치되도록 애플리케이션을 초기화합니다.
* 부품 어셈블리 챌린지의 난이도를 높이기 위해 배치 힌트를 숨깁니다.

이를 위해 수행할 주요 단계는 다음과 같습니다.

1. 개체 조작 사용
2. 물리학 사용
3. 오디오 원본 구성 요소 추가
4. 달착륙선 발사(스크립트) 구성 요소 추가 및 구성
5. 배치 힌트 설정/해제(스크립트) 구성 요소 추가 및 구성

> [!NOTE]
> 달착륙선 발사(스크립트) 구성 요소와 배치 힌트 설정/해제(스크립트) 구성 요소는 MRTK에 포함되지 않습니다. 이 자습서의 자산과 함께 제공되었습니다.

### <a name="1-enable-object-manipulation"></a>1. 개체 조작 사용

다음과 같이 [계층 구조] 창에서 RocketLauncher > **LunarModule** 개체를 선택하고, **조작 처리기(스크립트)** 구성 요소 및 **근거리 잡기형 상호 작용(스크립트)** 구성 요소를 추가한 다음, 조작 처리기(스크립트)를 구성합니다.

* 근거리 상호 작용만 허용하도록 **원거리 조작 허용** 확인란을 선택 취소합니다.
* 크기 조정을 사용하지 않도록 **양손 조작 유형**을 [이동 회전]으로 변경합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. 물리학 사용

RocketLauncher > **LunarModule** 개체를 선택한 상태에서 **Rigidbody** 구성 요소를 추가하고 다음과 같이 구성합니다.

* 달착륙선이 중력의 영향을 받지 않도록 **중력 사용** 확인란을 선택 취소합니다.
* 달착륙선이 처음에는 물리력의 영향을 받지 않도록 **Is Kinematic(운동학 적용)** 확인란을 선택합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. 오디오 원본 구성 요소 추가

RocketLauncher > **LunarModule** 개체를 선택한 상태에서 **오디오 원본** 구성 요소를 추가하고 다음과 같이 구성합니다.

* **공간 블렌드**를 1로 변경하여 공간 오디오를 사용하도록 설정합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. 달착륙선 발사(스크립트) 구성 요소 추가 및 구성

RocketLauncher > **LunarModule** 개체를 선택한 상태에서 **달착륙선 발사(스크립트)** 구성 요소를 추가하고 다음과 같이 구성합니다.

* 발사된 달 착륙선이 정상적으로 비행하도록 **Thrust(추진력)** 값을 변경합니다(예: 0.01로 변경).

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. 배치 힌트 설정/해제(스크립트) 구성 요소 추가 및 구성

RocketLauncher > **LunarModule** 개체를 선택한 상태에서 **배치 힌트 설정/해제(스크립트)** 구성 요소를 추가하고 다음과 같이 구성합니다.

* 게임 개체 배열 **크기** 속성을 5로 설정합니다.
* 다음과 같이 각 RocketLauncher > LunarModule > **PlacementHints** 개체의 **자식 개체**를 게임 개체 배열의 **요소** 필드에 할당합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>발사 단추 구성

다음과 같이 [계층 구조] 창에서 RocketLauncher > 단추 > **LaunchButton** 개체를 선택하고, **누를 수 있는 단추(스크립트)** 구성 요소에서 새 **Button Pressed ()** 이벤트를 만들고, 이벤트를 수신하도록 **LunarModule** 개체를 구성하고, 트리거할 동작으로 **LaunchLunarModule. StartThruster**를 정의합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> 이벤트를 구현하는 방법에 대한 내용은 [손 추적 제스처 및 상호 작용 가능 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 지침을 참조하세요.

다음과 같이 RocketLauncher > 단추 > **LaunchButton** 개체를 선택한 상태로 **누를 수 있는 단추(스크립트)** 구성 요소에서 새 **Button Pressed ()** 이벤트를 만들고, 이벤트를 수신하도록 **LunarModule** 개체를 구성하고, 트리거할 동작으로 **AudioSource.PlayOneShot**을 정의하고, **오디오 클립** 필드에 적절한 오디오 클립(예: MRTK_Gem 오디오 클립)을 할당합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

다음과 같이 RocketLauncher > 단추 > **LaunchButton** 개체를 선택한 상태로 **누를 수 있는 단추(스크립트)** 구성 요소에서 새 **Touch End ()** 이벤트를 만들고, 이벤트를 수신하도록 **LunarModule** 개체를 구성하고, 트리거할 동작으로 **LaunchLunarModule.StopThruster**를 정의합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

이제 게임 모드로 전환하여 [발사] 단추를 누르면 오디오 클립이 재생되며, [발사] 단추를 1초 이상 누르고 있으면 달착륙선이 우주로 발사됩니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>[초기화] 단추 구성

다음과 같이 [계층 구조] 창에서 RocketLauncher > 단추 > **ResetButton** 개체를 선택하고, **누를 수 있는 단추(스크립트)** 구성 요소에서 새 **Button Pressed ()** 이벤트를 만들고, 이벤트를 수신하도록 **LunarModule** 개체를 구성하고, 트리거할 동작으로 **LaunchLunarModule.ResetModule**을 정의합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

다음과 같이 RocketLauncher > 단추 > **ResetButton** 개체를 선택한 상태로 **누를 수 있는 단추(스크립트)** 구성 요소에서 새 **Button Pressed ()** 이벤트를 만들고, 이벤트를 수신하도록 **RocketLauncher** 개체를 구성하고, 트리거할 동작으로 **GameObject.BroadcastMessage**를 정의하고, 메시지 필드에 **ResetPlacement**를 입력합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> GameObject BroadcastMessage 동작은 RocketLauncher 개체의 ResetPlacement 메시지를 모든 자식 개체에게 보냅니다. 모든 LunarModuleParts 자식 개체에 추가한 부품 어셈블리 데모(스크립트) 구성 요소에 정의된 ResetPlacement 함수를 포함하고 있는 자식 개체는 자식 개체의 배치를 초기화하는 ResetPlacement 함수를 호출합니다.

이제 게임 모드로 전환하여 일부 부품을 이동하고/이동하거나 [초기화] 단추를 누르면 부품 및/또는 달착륙선이 원래 위치로 초기화되는 것을 볼 수 있습니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>배치 힌트 단추 구성
<!-- TODO: Rename to 'Configuring the Hints button'-->

다음과 같이 [계층 구조] 창에서 RocketLauncher > 단추 > **HintsButton** 개체를 선택하고, **누를 수 있는 단추(스크립트)** 구성 요소에서 새 **Button Pressed ()** 이벤트를 만들고, 이벤트를 수신하도록 **LunarModule** 개체를 구성하고, 트리거할 동작으로 **TogglePlacementHints.ToggleGameObjects**를 정의합니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

이제 게임 모드로 전환하면 반투명 배치 힌트가 기본적으로 사용되지 않습니다. 하지만 다음과 같이 [힌트] 단추를 눌러 켜고 끌 수 있습니다.

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>축하합니다.

이 애플리케이션의 구성을 마쳤습니다. 이제 사용자들이 이 애플리케이션을 사용하여 달착륙선을 완전히 조립하고, 달착륙선을 발사하고, 힌트를 설정/해제하고, 애플리케이션을 초기화하여 다시 시작할 수 있습니다.
