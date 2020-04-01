---
title: 시작 자습서 - 5. 3D 개체와 상호 작용
description: 3D 개체 구성, 기본 조작을 위한 경계 상자와 같은 기본 3D 콘텐츠 및 사용자 환경에 대해 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 65bcef6a7c10450816d7a928302b0b266b132f0f
ms.sourcegitcommit: 536fd45b48a70bbeca1454cef517ae007225e533
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80362067"
---
# <a name="5-interacting-with-3d-objects"></a>5. 3D 개체와 상호 작용

이 자습서에서는 컬렉션의 일부로 3D 개체 구성, 기본 조작을 위한 경계 상자, 근거리 및 원거리 상호 작용, 손 추적을 사용하는 터치 및 잡기 제스처 등의 기본 3D 콘텐츠 및 사용자 환경에 대해 알아봅니다.

## <a name="objectives"></a>목표

* 다른 학습 목표에 사용되는 3D 개체 패널 만들기
* 경계 상자 구현
* 이동, 회전, 크기 조정 등의 기본 조작을 위한 3D 개체 구성
* 근거리 및 원거리 조작 살펴보기
* 잡기 및 터치와 같은 추가적인 손 추적 제스처 알아보기

## <a name="importing-the-tutorial-assets"></a>자습서 자산 가져오기

다음 Unity 사용자 지정 패키지를 다운로드하여 가져옵니다.

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.

## <a name="decluttering-the-scene-view"></a>장면 보기 정리

장면을 좀 더 쉽게 작업할 수 있도록 개체 왼쪽의 **눈** 아이콘을 클릭하여 **큐브** 및 **ButtonCollection** 개체의 **장면 표시 유형**을 끄기로 설정합니다. 이렇게 하면 다음과 같이 게임 내 표시 유형을 변경하지 않고 [장면] 창에서 개체를 숨깁니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> 장면 표시 유형 컨트롤에 대한 내용 및 이 컨트롤을 사용하여 장면 보기와 워크플로를 최적화하는 방법에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">장면 표시 유형</a> 설명서를 참조하세요.

## <a name="organizing-3d-objects-in-a-collection"></a>컬렉션에서 3D 개체 구성

이 섹션에서는 이 자습서의 다음 섹션에서 3D 개체와 상호 작용하는 다양한 방법을 살펴볼 때 사용할 3D 개체 패널을 만듭니다. 특히 3 x 3 그리드에 배치되도록 3D 개체를 구성합니다.

[단추 패널을 만들 때](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)와 마찬가지로, 여기서 수행할 주요 단계는 다음과 같습니다.

1. 3D 개체를 부모 개체의 부모로 지정
2. Grid Object Collection(스크립트) 구성 요소 추가 및 구성

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. 3D 개체를 부모 개체의 부모로 지정

[계층 구조] 창에서 **빈 개체를 만들고**, 적절한 이름(예: **3DObjectCollection**)을 지정하고, 적절한 위치(예: X = 0, Y =-0.2, Z = 2)에 배치합니다.

[프로젝트] 창에서 **자산** > **MRTK.Tutorials.GettingStarted** > **프리팹**으로 이동하여 다음 프리팹을 **3DObjectCollection**의 **부모로 지정**합니다.

* Cheese
* CoffeeCup
* EarthCore
* Octa
* Platonic
* TheModule

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

다음과 같이 [계층 구조] 창에서 **3DObjectCollection** 개체의 자식 개체로 **3개 큐브를 만들고** 변환 **배율**을 X = 0.15, Y = 0.15, Z = 0.15로 설정합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> 위에 나열된 단계를 수행하는 방법은 [사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성](mrlearning-base-ch2.md) 자습서를 참조 하세요.

각 큐브를 볼 수 있도록 다음과 같이 큐브 위치를 변경합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

[프로젝트] 창에서 **자산** > **MixedRealityToolkit.SDK** > **StandardAssets** > **재질**로 이동하여 MRTK와 함께 제공된 재질을 확인합니다.

다음과 같은 적절한 재질을 **클릭**하여 각 큐브의 메시 렌더러 **재질** 요소 0 속성으로 끌어 놓습니다.

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Grid Object Collection(스크립트) 구성 요소 추가 및 구성

**3DObjectCollection** 개체에 **Grid Object Collection(스크립트)** 구성 요소를 추가하고 다음과 같이 구성합니다.

* 자식 개체가 부모 개체 아래에 배치된 순서대로 정렬되도록 **정렬 형식**을 **자식 개체**로 변경합니다.

그런 다음, 다음과 같이 **컬렉션 업데이트** 단추를 클릭하여 새 구성을 적용합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>3D 개체 조작

이 섹션에서는 이전 섹션에서 만든 패널의 모든 3D 개체를 조작하는 기능을 추가합니다. 그리고 프리팹 개체의 경우 사용자가 추적 손으로 이러한 개체에 손을 뻗어 잡을 수 있도록 설정할 것입니다. 그런 다음, 개체에 적용할 수 있는 몇 가지 조작 동작을 살펴보겠습니다.

이를 위해 수행할 주요 단계는 다음과 같습니다.

1. 모든 개체에 조작 처리기(스크립트) 구성 요소 추가
2. 프리팹 개체에 근거리 잡기형 상호 작용(스크립트) 구성 요소 추가
3. 조작 처리기(스크립트) 구성 요소 구성

> [!IMPORTANT]
> **개체를 조작**하려면 개체에 다음 구성 요소가 있어야 합니다.
>
> * **충돌체** 구성 요소(예: 상자 충돌체)
> * **조작 처리기(스크립트)** 구성 요소
>
> 추적 손으로 개체에 대한 **조작** 및 **잡기**를 수행하려면 개체에 다음 구성 요소가 있어야 합니다.
>
> * **충돌체** 구성 요소(예: 상자 충돌체)
> * **조작 처리기(스크립트)** 구성 요소
> * **근거리 잡기형 상호 작용(스크립트) 구성 요소**

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. 모든 개체에 조작 처리기(스크립트) 구성 요소 추가

[계층 구조] 창에서 **Cheese** 개체를 선택하고, **Shift** 키를 누른 채 **Cube () 2** 개체를 선택하고, 모든 개체에 **조작 처리기(스크립트)** 구성 요소를 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> 이 자습서의 학습 목표를 달성하기 위해 이미 프리팹에 충돌체가 추가되어 있습니다. 큐브 개체와 같은 Unity 기본 형식의 경우 개체를 만들 때 충돌체 구성 요소가 자동으로 추가됩니다. 위의 이미지에서 충돌체는 녹색 윤곽선으로 표시됩니다. 충돌체에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">충돌체</a> 설명서를 참조하세요.

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. 프리팹 개체에 근거리 잡기형 상호 작용(스크립트) 구성 요소 추가

[계층 구조] 창에서 **Cheese** 개체를 선택하고, **Shift** 키를 누른 채 **TheModule** 개체를 선택하고, 모든 개체에 **근거리 잡기형 상호 작용(스크립트)** 구성 요소를 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. 조작 처리기(스크립트) 구성 요소 구성

#### <a name="default-manipulation"></a>기본 조작

**Cube** 개체의 경우 기본 조작 동작을 경험하도록 다음과 같이 모든 속성을 기본값으로 둡니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> 구성 요소를 기본값으로 초기화하려면 구성 요소의 [설정] 아이콘을 선택하고 [초기화]를 선택하면 됩니다.

#### <a name="restrict-manipulation-to-scale-only"></a>조작을 배율 전용으로 제한

**Cube (1)** 개체의 경우 사용자가 개체의 크기를 변경할 수 있도록 **양손 조작 유형**을 **배율**로 변경합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>사용자로부터 고정된 거리로 이동 제한

**Cube (2)** 개체의 경우 이동된 개체가 사용자로부터 동일한 거리를 유지하도록 **이동에 대한 제약 조건**을 **Fix Distance From Head(헤드로부터의 거리 고정)** 로 변경합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>기본 잡기형 조작

**Cheese**, **CoffeCup** 및 **EarthCore** 개체의 경우 기본 잡기형 조작 동작을 경험하도록 다음과 같이 모든 속성을 기본값으로 둡니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>원거리 조작 기능 제거

**Octa** 개체의 경우 사용자가 추적 손을 사용하여 개체와 직접 상호 작용하는 것만 가능하도록 **원거리 조작 허용** 확인란을 선택 취소합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>개체가 중심을 축으로 회전하도록 설정

**Platonic** 개체의 경우 사용자가 한 손으로 개체를 돌리면 개체가 중심을 축으로 회전하도록 **한 손 회전 모드 근거리** 및 **한 손 회전 모드 원거리**를 **개체 중심을 축으로 회전**으로 변경합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a>개체가 릴리스된 후 이동 유지

**TheModule** 개체의 경우 물리학을 사용하도록 **Rigidbody** 구성 요소를 추가한 다음, 개체가 중력의 영향을 받지 않도록 **중력 사용** 확인란을 선택 취소합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

다시 조작 처리기(스크립트) 구성 요소에서, 개체가 사용자의 손에서 떨어지면 계속 움직이도록 **릴리스 동작**이 **속도 유지** 및 **각속도 유지**로 설정되었는지 확인합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

조작 처리기 구성 요소 및 관련 속성에 대한 자세한 내용을 보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [조작 처리기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) 가이드를 참조하세요.

## <a name="adding-bounding-boxes"></a>경계 상자 추가

경계 상자를 사용하면 크기 조정 및 회전에 사용할 수 있는 핸들을 제공하여 근거리 및 원거리 상호 작용 모두에서 한 손으로 개체를 보다 쉽고 직관적으로 조작할 수 있습니다.

이 예제에서는 EarthCore 개체에 경계 상자를 추가할 것입니다. 그러면 이전 섹션에서 구성한 개체 조작을 사용하여 이 개체와 상호 작용하고, 경계 상자 핸들을 사용하여 크기를 조정하고 회전할 수 있습니다.

> [!IMPORTANT]
> **경계 상자**를 사용하려면 개체에 다음 구성 요소가 있어야 합니다.
>
> * **충돌체** 구성 요소(예: 상자 충돌체)
> * **경계 상자(스크립트)** 구성 요소

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. EarthCore 개체에 경계 상자(스크립트) 구성 요소 추가

[검사기] 창에서 **EarthCore** 개체를 선택하고 EarthCore 개체에 **경계 상자(스크립트)** 구성 요소를 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> 런타임에 경계 상자 시각화가 생성되므로 게임 모드로 전환하기 전에는 보이지 않습니다.

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. 편집기 내 시뮬레이션을 사용하여 경계 상자 시각화 및 테스트

[재생] 단추를 눌러 게임 모드로 전환합니다. 그리고 다음과 같이 스페이스바를 길게 눌러 손을 호출하고 마우스를 사용하여 경계 상자와 상호 작용합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

경계 상자 구성 요소 및 관련 속성에 대한 자세한 내용을 보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [조작 처리기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 가이드를 참조하세요.

## <a name="adding-touch-effects"></a>터치 효과 추가

이 예제에서는 손으로 개체를 터치할 때 이벤트를 트리거하도록 설정할 것입니다. 특히 사용자가 Octa 개체를 터치하면 소리 효과를 재생하도록 구성하겠습니다.

이를 위해 수행할 주요 단계는 다음과 같습니다.

1. 개체에 오디오 원본 구성 요소 추가
2. 개체에 근거리 터치형 상호 작용(스크립트) 구성 요소 추가
3. 개체에 손 상호 작용 터치(스크립트) 구성 요소 추가
4. On Touch Started 이벤트 구현
5. 편집기 내 시뮬레이션을 사용하여 터치 상호 작용 테스트

> [!IMPORTANT]
> **터치 이벤트를 트리거**하려면 개체에 다음 구성 요소가 있어야 합니다.
>
> * **충돌체** 구성 요소. 가급적이면 상자 충돌체
> * **근거리 터치형 상호 작용(스크립트) 구성 요소**
> * **손 상호 작용 터치(스크립트)** 구성 요소

> [!NOTE]
> 손 상호 작용 터치(스크립트) 구성 요소는 MRTK에 포함되지 않습니다. 이 자습서의 자산과 함께 가져왔으며 원래는 MixedReality Toolkit Unity 예제에 포함되어 있습니다.

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. 개체에 오디오 원본 구성 요소 추가

다음과 같이 [계층 구조] 창에서 **Octa** 개체를 선택하고 **오디오 원본** 구성 요소를 Octa 개체에 추가한 다음, 공간 오디오를 사용하도록 **공간 블렌드**를 1로 변경합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. 개체에 근거리 터치형 상호 작용(스크립트) 구성 요소 추가

다음과 같이 **Octa** 개체를 선택한 상태에서 **근거리 터치형 상호 작용(스크립트)** 구성 요소를 Octa 개체에 추가한 다음, **경계 고정** 및 **중심 고정** 단추를 클릭하여 근거리 터치형 상호 작용(스크립트)의 로컬 중심 및 경계 속성을 BoxCollider에 맞게 업데이트합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. 개체에 손 상호 작용 터치(스크립트) 구성 요소 추가

다음과 같이 **Octa** 개체를 선택한 상태에서 **손 상호 작용 터치(스크립트)** 구성 요소를 Octa 개체에 추가합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. On Touch Started 이벤트 구현

**손 상호 작용 터치(스크립트)** 구성 요소에서 작은 **+** 아이콘을 클릭하여 새 **On Touch Started ()** 이벤트를 만듭니다. 다음과 같이 이벤트를 수신하도록 **Octa** 개체를 구성하고 트리거할 동작으로 **AudioSource.PlayOneShot**을 정의합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

**자산** > **MixedRealityToolkit.SDK** > **StandardAssets** > **오디오**로 이동하여 MRTK와 함께 제공된 오디오 클립을 살펴본 다음, **오디오 클립** 필드에 적절한 오디오 클립(예: MRTK_Gem 오디오 클립)을 할당합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> 이벤트를 구현하는 방법에 대한 내용은 [손 추적 제스처 및 상호 작용 가능 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 지침을 참조하세요.

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. 편집기 내 시뮬레이션을 사용하여 터치 상호 작용 테스트

[재생] 단추를 눌러 게임 모드로 전환합니다. 다음과 같이 스페이스바를 길게 눌러 손을 호출하고 마우스로 Octa 개체를 터치하여 소리 효과를 트리거합니다.

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> 터치 상호 작용을 테스트할 때, 그리고 위의 이미지에서 본 것처럼, Octa 개체를 터치할 때 색이 맥동합니다. 이 효과는 손 상호 작용 터치(스크립트) 구성 요소에 하드 코딩되며 위의 단계에서 완료한 이벤트 구성의 결과물이 아닙니다.
>
> 이 효과를 사용하지 않도록 설정하려면 줄 32 'TargetRenderer = GetComponentInChildren<Renderer>();'를 주석 처리하면 됩니다. 그러면 TargetRenderer가 null로 유지되고 색이 맥동하지 않습니다.

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 그리드 컬렉션에서 3D 개체를 구성하는 방법과 근거리 상호 작용(추적 손으로 직접 잡기) 및 원거리 상호 작용(응시 레이 또는 손 레이 사용)을 사용하여 이러한 개체를 조작(크기 조정, 회전 및 이동)하는 방법을 알아보았습니다. 또한 3D 개체 주위에 경계 상자를 배치하는 방법과 경계 상자에서 핸들을 사용하고 사용자 지정하는 방법을 배웠습니다. 마지막으로 개체를 터치할 때 이벤트를 트리거하는 방법을 알아보았습니다.

[다음 단원: 6. 고급 입력 옵션 탐색](mrlearning-base-ch5.md)
