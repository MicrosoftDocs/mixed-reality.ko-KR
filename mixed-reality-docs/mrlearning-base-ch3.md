---
title: 자습서-4를 시작 합니다. 동적 콘텐츠 배치 및 solvers 사용
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 8275d5a97d7827d34ed3926cabe4032cc7f4cfac
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129339"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a>4. 동적 콘텐츠 배치 및 Solvers 사용
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

Holograms은 사용자가 직관적이 고 원활 하 게 상호 작용 하는 방식으로 실제 환경에 배치 되는 경우 HoloLens 2를 사용 합니다. 이 자습서에서는 Solvers 이라고 하는 MRTK의 사용 가능한 배치 도구를 사용 하 여 동적으로 holograms을 배치 하 여 복잡 한 공간 배치 시나리오를 해결 하는 방법을 알아봅니다. MRTK에서 Solvers는 UI 요소에서 사용자, 사용자 또는 장면의 기타 게임 개체를 팔 로우 하는 데 사용 되는 스크립트 및 동작의 시스템입니다. 특정 위치로 빠르게 스냅하여 애플리케이션을 보다 직관적인 만드는 데 사용할 수도 있습니다.

## <a name="objectives"></a>목표

* MRTK의 Solvers 소개
* Solvers를 사용 하 여 단추 컬렉션을 사용자에 게 따름
* Solvers를 사용 하 여 게임 개체가 사용자의 추적 된 손을 따름

## <a name="location-of-solvers-in-the-mrtk"></a>MRTK의 Solvers 위치

 MRTK의 Solvers는 MRTK SDK 폴더에 있습니다. 프로젝트에서 사용 가능한 Solvers를 보려면 프로젝트 창에서 **자산** > **MixedRealityToolkit** > **기능** > **유틸리티** > **Solvers**로 이동 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial3-section1-step1-1.png)

이 자습서에서는 궤도 해 찾기 및 방사형 보기 해 찾기의 구현을 검토 합니다. MRTK에서 사용할 수 있는 Solvers의 전체 범위에 대해 자세히 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) 가이드를 참조 하세요.

## <a name="use-a-solver-to-follow-the-user"></a>사용자를 팔 로우 하는 데 사용할 수 있는 해 찾기
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

이 섹션에서는 사용자의 응시 방향을 따라 이전 자습서에서 만든 단추 컬렉션을 개선 합니다. 또한 단추 컬렉션이 항상이 되도록 해 찾기를 구성 합니다.

* 왼쪽에서 오른쪽으로 읽도록 사용자의 읽기 방향에 평행 하 게 회전
* 사용자 수평 응시 방향 아래에 배치 되므로이 자습서의 뒷부분에서 추가 하는 다른 개체를 방해 하지 않는지 하지 않습니다.
* 사용자 로부터 약 1/2 arm의 길이에 배치 하므로 단추를 쉽게 누를 수 있습니다.

이 경우 개체를 참조 된 개체에서 지정 된 위치 및 오프셋으로 잠그는 **궤도 해** 를 사용 합니다.

### <a name="1-add-the-orbital-solver"></a>1. 궤도 해 찾기를 추가 합니다.

계층 창에서 **buttoncollection** 개체를 선택한 다음 검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 **궤도 (스크립트)** 구성 요소를 buttoncollection 개체에 추가 합니다.

> [!NOTE]
> 해 찾기를 추가 하는 경우 (이 경우에는 궤도 (스크립트) 구성 요소) 해 찾기에 필요 하기 때문에 해결 프로그램 처리기 (스크립트) 구성 요소가 자동으로 추가 됩니다.

### <a name="2-configure-the-orbital-solver"></a>2. 궤도 해 찾기를 구성 합니다.

**해 찾기 처리기 (스크립트)** 구성 요소를 구성 합니다.

* **추적 대상 형식이** **Head** 로 설정 되었는지 확인 합니다.

**궤도 (스크립트)** 구성 요소를 구성 합니다.

* 추적 된 개체를 **따르도록** **방향 유형** 변경
* **로컬 오프셋** 을 X = 0, Y = 0, Z = 0으로 다시 설정 합니다.
* **전역 오프셋** 을 X = 0, Y =-0.4, Z = 0.3로 변경 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a>3. 편집기 내 시뮬레이션을 사용 하 여 궤도 해 찾기 테스트

재생 단추를 눌러 게임 모드로 전환 하 고 마우스 오른쪽 단추를 누른 채 마우스 오른쪽 단추를 눌러 응시 방향을 회전 하 고 다음을 확인 합니다.

* 이제 ButtonCollection의 변환 위치는 해 찾기 설정에 따라 결정 됩니다.
* 해 찾기의 영향을 받지 않는 큐브는 동일한 위치에 유지 됩니다.

![mrlearning-기본](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> 장면 창에 카메라 광선이 표시 되지 않으면 Gizmo 그리려면 메뉴가 활성화 되어 있는지 확인 합니다. Gizmo 그리려면 메뉴와이 메뉴를 사용 하 여 장면 보기를 최적화 하는 방법에 대 한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">gizmo 그리려면 메뉴</a> 설명서를 참조 하세요.
>
> 위의 이미지에 표시 된 대로 장면 및 게임 창을 나란히 표시 하려면 게임 창을 장면 창의 오른쪽으로 끌기만 하면 됩니다. 작업 영역을 사용자 지정 하는 방법에 대해 자세히 알아보려면 Unity의 <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조 하세요.

## <a name="enabling-objects-to-follow-tracked-hands"></a>추적 된 손을 따르도록 개체 활성화

이 섹션에서는 이전 자습서에서 만든 큐브 개체를 구성 하 여 사용자의 추적 된 실습, 특히 오른쪽 손목를 따릅니다. 또한 다음과 같이 큐브를 구성 해 볼 수 있습니다.

* 사용자의 손을 회전 하 여 방향을 변경 합니다.
* 사용자의 손목 위치

이 경우 참조 된 개체에의 한 뷰 원추 내에서 개체를 유지 하는 **방사형 보기 해 찾기를** 사용 합니다.

### <a name="1-add-the-radial-view-solver"></a>1. 방사형 보기 해 찾기 추가

계층 창에서 **큐브** 개체를 선택한 다음, 검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 **방사형 보기 (스크립트)** 구성 요소 큐브 개체를 추가 합니다.

### <a name="2-configure-the-radial-view-solver"></a>2. 방사형 보기 해결 기 구성

**해 찾기 처리기 (스크립트)** 구성 요소를 구성 합니다.

* **추적 대상 유형을** **직접 조인트** 로 변경
* **추적** 을 **오른쪽** 으로 변경
* **추적 된 손을** **손목** 으로 변경

**방사형 보기 (스크립트)** 구성 요소를 구성 합니다.

* **참조 방향을** **개체 지향**으로 변경한 다음 방향 **참조 방향** 확인란을 선택 합니다.
* **최소 거리** 및 **최대 거리** 를 0으로 변경

![mrlearning-기본](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a>3. 편집기 내 시뮬레이션을 사용 하 여 방사형 보기 해 찾기를 테스트 합니다.

게임 모드로 전환 하려면 재생 단추를 누르고 스페이스바를 누르고 있으면 됩니다. 마우스 커서를 이동 하 여 손 모양으로 이동 하 고 마우스 왼쪽 단추를 클릭 하 여 손을 회전 합니다.

![mrlearning-기본](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a>축하합니다.

이 자습서에서는 MRTK의 solvers를 사용 하 여 UI가 사용자를 직관적으로 따르도록 하는 방법을 배웠습니다. 또한 사용자의 추적 된 작업을 수행 하기 위해 개체 (예: 큐브)에 해 찾기를 첨부 하는 방법을 배웠습니다. 이에 대 한 자세한 내용 및 MRTK에 포함 된 다른 solvers에 대 한 자세한 내용은 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) 가이드를 참조 하세요.

[다음 자습서: 5.3D 개체와 상호 작용](mrlearning-base-ch4.md)
