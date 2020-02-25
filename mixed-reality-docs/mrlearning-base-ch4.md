---
title: 자습서 시작-5. 3D 개체와 상호 작용
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 7eb38e205237257e400550299fdeebb73ba746f1
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555498"
---
# <a name="5-interacting-with-3d-objects"></a>5.3D 개체와 상호 작용

이 자습서에서는 기본 3D 콘텐츠 및 사용자 환경에 대해 설명 합니다. 예를 들어, 3D 개체를 컬렉션의 일부로 구성 하 고, 기본 조작을 위한 경계 상자를 구성 하 고, 근거리 및 원거리 상호 작용을 제공 하 고, 터치 및 잡기 제스처를 사용 합니다.

## <a name="objectives"></a>목표

* 다른 학습 목표에 사용 되는 3D 개체의 패널을 만듭니다.
* 경계 상자 구현
* 이동, 회전, 크기 조정 등의 기본 조작을 위해 3D 개체를 구성 합니다.
* 근거리 및 원거리 조작 살펴보기
* 잡기, 터치 등의 추가 수동 추적 제스처에 대해 알아보기

## <a name="importing-the-tutorial-assets"></a>자습서 자산 가져오기

Unity 사용자 지정 패키지를 다운로드 하 고 가져옵니다.

* [MRTK. HoloLens2.2.3.0.2. unitypackage를 시작 합니다.](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

자습서 자산을 가져온 후 프로젝트 창이 다음과 같이 표시 됩니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> Unity 사용자 지정 패키지를 가져오는 방법에 대 한 미리 알림은 [혼합 현실 도구 키트 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 명령을 참조 하세요.

## <a name="decluttering-the-scene-view"></a>장면 보기 Decluttering

장면에서 작업을 더 쉽게 수행 하려면 개체 왼쪽의 **눈 모양** 아이콘을 클릭 하 여 **큐브** 및 **buttoncollection** 개체에 대 한 **장면 표시 유형을** off로 설정 합니다. 이렇게 하면 게임에서 표시 되지 않는 표시를 변경 하지 않고 장면 창에서 개체를 숨깁니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> 장면 표시 유형 컨트롤 및 장면 보기와 워크플로를 최적화 하는 데 사용할 수 있는 방법에 대 한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">장면 표시 유형</a> 설명서를 참조 하세요.

## <a name="organizing-3d-objects-in-a-collection"></a>컬렉션에서 3D 개체 구성

이 섹션에서는이 자습서의 다음 섹션에서 3D 개체와 상호 작용 하는 다양 한 방법을 살펴볼 때 사용할 3D 개체의 패널을 만듭니다. 특히 3D 개체가 3 x 3 모눈에 배치 되도록 구성 합니다.

[단추 패널을 만든](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)경우와 마찬가지로이를 위해 수행 해야 하는 주요 단계는 다음과 같습니다.

1. 부모 개체에 대 한 3D 개체의 부모
2. Grid 개체 컬렉션 (스크립트) 구성 요소 추가 및 구성

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. 부모 개체에 대 한 3D 개체의 부모

계층 창에서 **빈 개체를 만들고**적절 한 이름 (예: **3DObjectCollection**)을 지정한 다음 적절 한 위치에 배치 합니다 (예: X = 0, Y =-0.2, Z = 2).

프로젝트 창에서 **자산** > **mrtk로 이동 합니다. 자습서. GetPrefabs** 가 > 시작 **된 후 다음 Prefabs를** **3DObjectCollection**로.

* 치즈
* CoffeeCup
* EarthCore
* Octa
* Platonic
* TheModule

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

계층 창에서 **3 개의 큐브** 를 **3DObjectCollection** 의 자식 개체로 만들고 해당 변환 **배율을** X = 0.15, Y = 0.15, Z = 0.15로 설정 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> 위에 나열 된 단계를 수행 하는 방법에 대 한 미리 알림은 [사용자 인터페이스 만들기 및 혼합 현실 도구 키트 구성](mrlearning-base-ch2.md) 자습서를 참조할 수 있습니다.

각 큐브를 볼 수 있도록 큐브 위치를 변경 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

프로젝트 창에서 **자산** > **MixedRealityToolkit** > **standardassets** > **자료** 로 이동 하 여 mrtk와 함께 제공 되는 자료를 확인 합니다.

각 큐브의 메시 렌더러 **재질** 요소 0 속성에 적합 한 자료를 클릭 하 여 **끌어 놓습니다** . 예를 들면 다음과 같습니다.

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. 그리드 개체 컬렉션 (스크립트) 구성 요소 추가 및 구성

**3DObjectCollection** 개체에 **그리드 개체 컬렉션 (스크립트)** 구성 요소를 추가 하 고 다음과 같이 구성 합니다.

* **정렬 유형** 을 **자식 순서로** 변경 하 여 자식 개체가 부모 개체 아래에 배치 된 순서 대로 정렬 되도록 합니다.

그런 다음 **컬렉션 업데이트** 단추를 클릭 하 여 새 구성을 적용 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>3D 개체 조작

이 섹션에서는 이전 섹션에서 만든 패널의 모든 3D 개체를 조작 하는 기능을 추가 합니다. 또한 prefab 개체의 경우 사용자가 추적 된 손으로 이러한 개체를 연결 하 고 가져올 수 있습니다. 그런 다음 개체에 적용할 수 있는 몇 가지 조작 동작을 탐색 합니다.

이를 위해 수행 하는 주요 단계는 다음과 같습니다.

1. 모든 개체에 조작 처리기 (스크립트) 구성 요소 추가
2. Prefab 개체에 Near 인터랙션 Grabbable (스크립트) 구성 요소 추가
3. 조작 처리기 (스크립트) 구성 요소 구성

> [!IMPORTANT]
> 개체를 **조작할**수 있으려면 개체에 다음 구성 요소가 있어야 합니다.
>
> * **Collider** component (예: 상자 collider)
> * **조작 처리기 (스크립트)** 구성 요소
>
> **추적 된 손을 사용 하 여 개체**를 **조작** 하 고 잡기 위해서는 개체에 다음 구성 요소가 있어야 합니다.
>
> * **Collider** component (예: 상자 collider)
> * **조작 처리기 (스크립트)** 구성 요소
> * **Near 인터랙션 Grabbable (스크립트)** 구성 요소

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. 모든 개체에 조작 처리기 (스크립트) 구성 요소를 추가 합니다.

계층 창에서 **치즈** 개체를 선택 하 고 **shift** 키를 누른 채 **Cube () 2** 개체를 선택 하 고 모든 개체에 **조작 처리기 (스크립트)** 구성 요소를 추가 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> 이 자습서에서는 colliders가 이미 prefabs에 추가 되었습니다. 큐브 개체와 같은 Unity 기본 형식의 경우 개체를 만들 때 Collider 구성 요소가 자동으로 추가 됩니다. 위의 이미지에서 colliders는 녹색 윤곽선으로 표시 됩니다. Colliders에 대 한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> 설명서를 참조 하세요.

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. prefab 개체에 Near 인터랙션 Grabbable (스크립트) 구성 요소를 추가 합니다.

계층 창에서 **치즈** 개체를 선택 하 고 **shift** 키를 누른 상태에서 **TheModule** 개체를 선택 하 고 모든 개체에 **Near 인터랙션 Grabbable (스크립트)** 구성 요소를 추가 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. 조작 처리기 (스크립트) 구성 요소 구성

#### <a name="default-manipulation"></a>기본 조작

**큐브** 개체의 경우 기본 조작 동작을 수행 하려면 모든 속성을 기본적으로 그대로 둡니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> 구성 요소를 기본값으로 다시 설정 하려면 구성 요소의 설정 아이콘을 선택 하 고 다시 설정을 선택 하면 됩니다.

#### <a name="restrict-manipulation-to-scale-only"></a>조작을 확장 전용으로 제한

**Cube (1)** 개체의 경우 사용자가 개체의 크기를 변경할 수 있도록 **두 개의 전달 조작 유형을** **Scale** 으로 변경 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>사용자 로부터 고정 거리가 이동 하도록 제한

**Cube (2)** 개체의 경우 이동 **시** 의 거리를 변경 하 여 **Head에서의 거리를 수정** 합니다. 그러면 개체가 이동 될 때 사용자와 동일한 거리가 유지 됩니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>기본 grabbable 조작

**치즈**, **CoffeCup**및 **EarthCore** 개체의 경우 기본 grabbable 조작 동작을 수행 하려면 모든 속성을 기본적으로 그대로 둡니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>Far 조작 기능 제거

**Octa** 개체의 경우, 사용자가 추적 된 손을 사용 하 여 직접 개체와 상호 작용할 수 있도록이 작업을 수행 하는 데 **오래 된 조작 허용** 확인란을 선택 취소 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>개체의 중심을 기준으로 개체를 회전 하도록 설정

**Platonic** 개체의 경우에는 한 번 회전 **모드** 를 변경 하 여 **개체 중심을 회전할** 수 있습니다. 그러면 사용자가 개체를 한 손으로 회전할 때 개체의 중심을 기준으로 회전 하 게 됩니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a>개체를 릴리스한 후 이동 유지

**TheModule** 개체의 경우에는 **Rigidbody** 구성 요소를 추가 하 여 물리학을 사용 하도록 설정 하 고 **중력 사용** 확인란을 선택 취소 하 여 개체가 중력의 영향을 받지 않도록 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

조작 처리기 (스크립트) 구성 요소로 돌아가서, **릴리스 동작이** **속도 유지** 및 **각도 속도 유지** 로 설정 되어 있는지 확인 합니다. 그러면 개체가 사용자의 손을 해제 된 후 계속 이동 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

조작 처리기 구성 요소 및 관련 속성에 대해 자세히 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [조작 처리기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) 가이드를 참조 하세요.

## <a name="adding-bounding-boxes"></a>경계 상자 추가

경계 상자를 사용 하면 크기 조정 및 회전에 사용할 수 있는 핸들을 제공 하 여 거의 상호 작용 모두에 대 한 개체를 보다 쉽고 직관적으로 조작할 수 있습니다.

이 예제에서는 EarthCore 개체에 경계 상자를 추가 하 여이 개체를 이제 이전 섹션에서 구성한 개체 조작 및 경계 상자 핸들을 사용 하 여 크기 조정 및 회전을 사용 하 여 상호 작용할 수 있도록 합니다.

> [!IMPORTANT]
> **경계 상자**를 사용할 수 있으려면 개체에 다음 구성 요소가 있어야 합니다.
>
> * **Collider** component (예: 상자 collider)
> * **경계 상자 (스크립트)** 구성 요소

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. EarthCore 개체에 경계 상자 (스크립트) 구성 요소를 추가 합니다.

검사기 창에서 **EarthCore** 개체를 선택 하 고 EarthCore 개체에 **경계 상자 (스크립트)** 구성 요소를 추가 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> 경계 상자 시각화는 런타임에 생성 되므로 게임 모드를 시작 하기 전에 표시 되지 않습니다.

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. 편집기 내 시뮬레이션을 사용 하 여 경계 상자 시각화 및 테스트

게임 모드를 시작 하려면 재생 단추를 누릅니다. 그런 다음 스페이스바를 누르고 마우스를 사용 하 여 경계 상자와 상호 작용 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

경계 상자 구성 요소 및 관련 속성에 대 한 자세한 내용은 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [경계 상자](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 가이드를 참조 하세요.

## <a name="adding-touch-effects"></a>터치 효과 추가

이 예제에서는 개체를 손으로 이동할 때 이벤트를 트리거할 수 있도록 설정 합니다. 특히 Octa 개체가 사용자에 게 닿을 때 소리 효과를 재생 하도록 구성 합니다.

이를 위해 수행 하는 주요 단계는 다음과 같습니다.

1. 오디오 원본 구성 요소를 개체에 추가 합니다.
2. 개체에 Near 인터랙션 Touchable (스크립트) 구성 요소를 추가 합니다.
3. 개체에 손 모양 상호 작용 터치 (스크립트) 구성 요소 추가
4. 터치 시작 시 이벤트 구현
5. 편집기에서 시뮬레이션을 사용 하 여 터치 상호 작용 테스트

> [!IMPORTANT]
> **터치 이벤트를 트리거할**수 있으려면 개체에 다음 구성 요소가 있어야 합니다.
>
> * **Collider** component, 가급적 상자 Collider
> * **Near 인터랙션 Touchable (스크립트)** 구성 요소
> * **직접 상호 작용 터치 (스크립트)** 구성 요소

> [!NOTE]
> 핸드 상호 작용 터치 (스크립트) 구성 요소는 MRTK의 일부가 아닙니다. 이 자습서의 자산과 원래 MixedReality Toolkit Unity 예제의 일부로 가져왔습니다.

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. 오디오 원본 구성 요소를 개체에 추가 합니다.

계층 창에서 **Octa** 개체를 선택 하 고 **오디오 원본** 구성 요소를 Octa 개체에 추가한 다음 공간 **Blend** 를 1로 변경 하 여 공간 오디오를 사용 하도록 설정 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. Near 인터랙션 Touchable (스크립트) 구성 요소를 개체에 추가 합니다.

**Octa** 개체를 선택한 상태에서 **near 인터랙션 Touchable (스크립트)** 구성 요소를 Octa 개체에 추가한 다음, **범위 수정** 및 **수정 센터** 단추를 클릭 하 여와 일치 하는 근접 한 상호 작용 Touchable (스크립트)의 로컬 센터 및 범위 속성을 업데이트 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. 개체에 손 모양 상호 작용 터치 (스크립트) 구성 요소를 추가 합니다.

**Octa** 개체를 선택한 상태에서 Octa 개체에 **손 모양 상호 작용 터치 (스크립트)** 구성 요소를 추가 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. 터치 시작 시 이벤트 구현

**핸드 상호 작용 터치 (스크립트)** 구성 요소에서 small **+** 아이콘을 클릭 하 여 새 **터치 시작 ()** 이벤트를 만듭니다. 그런 다음 이벤트를 수신 하도록 **Octa** 개체를 구성 하 고 트리거할 동작으로 **PlayOneShot** 를 정의 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

**자산** > **MixedRealityToolkit** > **standardassets** > 자료로 이동 하 여 mrtk와 함께 제공 되는 오디오 클립을 확인 하 고 **오디오 클립** 필드 (예: MRTK_Gem 오디오 클립)에 적절 한 오디오 클립을 할당 합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> 이벤트를 구현 하는 방법에 대 한 미리 알림은 [손 추적 제스처 및 interactable 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 지침을 참조할 수 있습니다.

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. 편집기 내 시뮬레이션을 사용 하 여 터치 상호 작용 테스트

게임 모드를 시작 하려면 재생 단추를 누릅니다. 그런 다음 스페이스바를 누르고 마우스를 사용 하 여 Octa 개체를 터치 하 고 소리 효과를 트리거합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> 터치 상호 작용을 테스트할 때와 위의 이미지에 표시 된 것 처럼 Octa 개체 색은 작업을 수행 하는 동안 pulsated. 이 효과는 직접 상호 작용 터치 (스크립트) 구성 요소에 하드 코딩 되며 위 단계에서 완료 한 이벤트 구성의 결과가 아닙니다.
>
> 이 효과를 사용 하지 않도록 설정 하려면 예를 들어 주석 출력 또는 줄 32 ' TargetRenderer = GetComponentInChildren<Renderer>(); '를 사용할 수 있습니다. 그러면 TargetRenderer 남은 null과 색이 pulsating 되지 않습니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 그리드 컬렉션에서 3D 개체를 구성 하는 방법 및 거의 상호 작용 (추적 된 손으로 직접 이동) 및 먼 상호 작용 (응시 광선 또는 핸드 광선 사용)을 사용 하 여 이러한 개체를 조작 하는 방법 (크기 조정, 회전 및 이동)을 배웠습니다. 3D 개체 주위에 경계 상자를 배치 하는 방법 및 경계 상자에서 핸들을 사용 하 고 사용자 지정 하는 방법을 배웠습니다. 마지막으로 개체를 터치할 때 이벤트를 트리거하는 방법을 알아보았습니다.

[다음 단원: 6. 고급 입력 옵션 탐색](mrlearning-base-ch5.md)
