---
title: 시작 자습서 - 4. 동적 콘텐츠 배치 및 해결기 사용
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 2825f99f49eca6fd7277d02828bfe1bc3c23291a
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031218"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. 동적 콘텐츠 배치 및 해결기 사용
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

HoloLens 2에서 홀로그램은 사용자를 직관적으로 따라다니며, 원활하고 세련된 상호 작용을 지원하는 방식으로 실제 환경에 배치됩니다. 이 자습서에서는 MRTK에서 제공하는 복잡한 공간 배치 시나리오를 해결할 수 있는 해결기라고 하는 배치 도구를 사용하여 홀로그램을 동적으로 배치하는 방법을 살펴봅니다. MRTK에서 해결기는 UI 요소가 장면에서 사용자 또는 다른 게임 개체를 따라다니도록 만드는 데 사용되는 스크립트 및 동작 시스템입니다. 특정 위치로 빠르게 스냅하여 애플리케이션을 보다 직관적인 만드는 데 사용할 수도 있습니다.

## <a name="objectives"></a>목표

* MRTK 해결기 소개
* 해결기를 사용하여 단추 컬렉션이 사용자를 따라다니게 만들기
* 해결기를 사용하여 게임 개체가 사용자의 추적 손을 따라다니게 만들기

## <a name="location-of-solvers-in-the-mrtk"></a>MRTK에서 해결기의 위치

 MRTK의 해결기는 MRTK SDK 폴더에 있습니다. 프로젝트에서 사용할 수 있는 해결기를 확인하려면 다음과 같이 프로젝트 창에서 **자산** > **MixedRealityToolkit.SDK** > **기능** > **유틸리티** > **해결기**로 이동합니다.

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

이 자습서에서는 궤도 해결기 및 방사형 보기 해결기가 어떻게 구현되는지 살펴봅니다. MRTK에서 사용할 수 있는 해결기의 전체 범위를 알아보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [해결기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) 가이드를 참조하세요.

## <a name="use-a-solver-to-follow-the-user"></a>해결기를 사용하여 사용자 따라다니기
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

이 섹션에서는 단추가 사용자의 응시 방향을 따라다니도록 이전 자습서에서 만든 단추 컬렉션을 개선합니다. 또한 단추 컬렉션이 항상 다음과 같이 표시되도록 해결기를 구성합니다.

* 자연스럽게 왼쪽에서 오른쪽으로 읽도록 사용자의 읽기 방향에 평행하게 회전
* 이 자습서의 뒷부분에서 추가할 다른 개체를 가리지 않도록 사용자 수평 응시 방향보다 살짝 아래에 배치
* 단추를 쉽게 누를 수 있도록 사용자로부터 팔 절반 길이쯤 되는 위치에 배치

이렇게 하기 위해, 개체를 참조 개체로부터 지정된 위치와 오프셋에 잠그는 **궤도 해결기**를 사용하겠습니다.

### <a name="1-add-the-orbital-solver"></a>1. 궤도 해결기 추가

[계층 구조] 창에서 **ButtonCollection** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **궤도(스크립트)** 구성 요소를 ButtonCollection 개체에 추가합니다.

> [!NOTE]
> 해결기를 추가하면(여기서는 궤도(스크립트) 구성 요소) 해결기에 필요한 해결기 처리기(스크립트) 구성 요소가 자동으로 추가됩니다.

### <a name="2-configure-the-orbital-solver"></a>2. 궤도 해결기 구성

다음과 같이 **해결기 처리기(스크립트)** 구성 요소를 구성합니다.

* **추적 대상 형식**이 **헤드**로 설정되었는지 확인

다음과 같이 **궤도(스크립트)** 구성 요소를 구성합니다.

* **방향 유형**이 **Follow Tracked Object(추적되는 개체 따라다니기)** 로 설정되었는지 확인
* **로컬 오프셋**을 X = 0, Y = 0, Z = 0으로 초기화
* **World Offset(월드 오프셋)** 을 X = 0, Y = -0.4, Z = 0.3으로 변경

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. 편집기 내 시뮬레이션을 사용하여 궤도 해결기 테스트

[재생] 단추를 눌러 게임 모드로 전환한 다음, 마우스 오른쪽 단추를 누른 채로 응시 방향을 회전하면서 다음 사항을 확인합니다.

* 이제 ButtonCollection의 변환 위치는 해결기 설정에 따라 결정됩니다.
* 해결기의 영향을 받지 않는 큐브는 동일한 위치에 유지됩니다.

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> [장면] 창에 카메라 광선이 보이지 않으면 Gizmo 메뉴가 활성화되어 있는지 확인합니다. Gizmo 메뉴에 대한 내용 및 이 메뉴를 사용하여 장면 보기를 최적화하는 방법에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmo 메뉴</a> 설명서를 참조하세요.
>
> 위의 이미지처럼 장면 및 게임 창을 나란히 표시하려면 간단하게 게임 창을 장면 창의 오른쪽으로 끌어다 놓으면 됩니다. 작업 영역을 사용자 지정하는 방법에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조하세요.

## <a name="enabling-objects-to-follow-tracked-hands"></a>개체가 추적 손을 따라다니도록 설정

이 섹션에서는 이전 자습서에서 만든 큐브 개체가 사용자의 추적 손, 특히 오른쪽 손목을 따라다니도록 구성합니다. 또한 큐브가 다음과 같이 되도록 해결기를 구성합니다.

* 사용자의 손이 회전하면 방향 변경
* 사용자의 손목에 배치

이렇게 하기 위해, 참조 개체가 캐스팅하는 보기 콘 내부에 개체를 유지 하는 **방사형 보기 해결기**를 사용합니다.

### <a name="1-add-the-radial-view-solver"></a>1. 방사형 보기 해결기 추가

[계층 구조] 창에서 **큐브** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 큐브 개체에 **방사형 보기(스크립트)** 구성 요소를 추가합니다.

### <a name="2-configure-the-radial-view-solver"></a>2. 방사형 보기 해결기 구성

다음과 같이 **해결기 처리기(스크립트)** 구성 요소를 구성합니다.

* **추적 대상 형식**을 **Hand Joint(손 관절)** 로 변경
* **Tracked Handness(추적 손)** 를 **오른쪽**으로 변경
* **Tracked Hand Joint(추적 손 관절)** 를 **손목**으로 변경

다음과 같이 **방사형 보기(스크립트)** 구성 요소를 구성합니다.

* **참조 방향**을 **개체 지향**으로 변경한 다음, **Orient To Reference Direction(참조 방향으로 회전)** 확인란 선택
* **최소 거리** 및 **최대 거리**를 0으로 변경

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. 편집기 내 시뮬레이션을 사용하여 방사형 보기 해결기 테스트

[재생] 단추를 눌러 게임 모드로 전환한 다음, 스페이스바를 길게 눌러 손을 호출합니다. 다음과 같이 마우스 커서를 이동하여 손을 움직이고, 마우스 왼쪽 단추를 누른 채로 손을 회전해 봅니다.

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 MRTK의 해결기를 사용하여 UI가 사용자를 직관적으로 따라다니게 만드는 방법을 알아보았습니다. 또한 해결기를 개체(예: 큐브)에 연결하여 사용자의 추적 손을 따라다니게 만드는 방법도 알아보았습니다. 이러한 해결기와 MRTK에 포함된 다른 해결기에 대한 자세한 내용은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [해결기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) 가이드를 참조하세요.

[다음 자습서: 5. 3D 개체와 상호 작용](mrlearning-base-ch4.md)
