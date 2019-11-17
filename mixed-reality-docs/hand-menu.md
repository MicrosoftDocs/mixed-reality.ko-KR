---
title: 손 모양 메뉴
description: 사용자는 직접 메뉴를 사용 하 여 자주 사용 하는 함수에 대 한 직접 연결 된 UI를 빠르게 가져올 수 있습니다. 다음은 직접 메뉴에 대 한 모범 사례 및 권장 사항입니다.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 손, 메뉴, 단추, 빠른 액세스, 레이아웃
ms.openlocfilehash: c53fdc4ea6f3243cf906ee1916a9c234d0fce6ca
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143182"
---
# <a name="hand-menu"></a>손 모양 메뉴

![Ulnar 사이드 위치](images/UX/UX_Hero_HandMenu.jpg)

사용자는 직접 메뉴를 사용 하 여 자주 사용 하는 함수에 대 한 직접 연결 된 UI를 빠르게 가져올 수 있습니다. 

다음은 직접 메뉴에 대해 찾은 모범 사례입니다. [Mrtk](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)의 손 메뉴를 보여 주는 예제 장면을 찾을 수도 있습니다.

<br>

---

## <a name="behavior-best-practices"></a>동작 모범 사례
**A. 단추 수를 작게 유지 합니다.** 즉, 손 잠금 메뉴와 눈동자 간의 거리가 가까이 있고, 언제 든 지 상대적으로 작은 시각적 영역에 초점을 맞춘 사용자의 추세 (비전의 attentional 원뿔 약 10도)를 사용 하는 것이 좋습니다. 단추 수를 작게 유지 합니다. 탐색을 기반으로 3 개의 단추가 있는 한 열은 사용자가 시계 중심으로 이동 하는 경우에도 뷰 (FOV)의 모든 콘텐츠를 유지 하 여 잘 작동 합니다. 

**B. 빠른 작업을 위한 수동 메뉴 활용:** arm을 올리고 위치를 유지 관리 하면 arm 피로을 쉽게 유발할 수 있습니다. 짧은 상호 작용을 필요로 하는 메뉴에 대해 직접 잠긴 메서드를 사용 합니다. 메뉴가 복잡 하 고 확장 된 상호 작용 시간이 필요한 경우에는 대신 세계 잠금 또는 본문 잠금을 사용 하는 것이 좋습니다. 

**C. 단추/패널 각도:** 메뉴는 head의 반대 어깨와 중간 방향으로 빌보드를 수행 합니다 .이를 통해 자연 스런 이동이 반대 바늘을 사용 하 여 메뉴와 상호 작용 하 고, 터치 시 매우 불쾌 하거나 불편할 수 있습니다. 단추. 

**D. 단방향 또는 실습 작업 지원 고려:** 사용자의 손을 항상 사용할 수 있다고 가정 하지 마세요. 하나 또는 둘 다를 사용할 수 없는 경우 광범위 한 컨텍스트를 고려 하 고 해당 상황에 대 한 설계 계정이 있는지 확인 합니다. 단방향 메뉴를 지원 하기 위해 손을 대칭 이동 하면 (팜 아래로 이동) 메뉴 배치를 왼쪽에서 잠김으로 전환 해 볼 수 있습니다. 직접 사용 하지 않는 시나리오의 경우 음성 명령을 사용 하 여 직접 메뉴 단추를 호출 하는 것이 좋습니다.

**E. 2 단계 호출:** 손 메뉴를 트리거하는 이벤트로 palm을 사용 하는 경우 사용자가 의도적으로 둘 다 (통신 및 개체 조작을 위해)를 많이 이동 하기 때문에 필요 하지 않을 때 실수로 표시 될 수 있습니다 (가양성). 그리고 의도 하지 않은 경우 앱에서 가양성이 발생 하는 경우 팜 등록 이벤트 외에 추가 단계를 추가 하 여 완전히 열린 손가락 같은 손 메뉴를 호출 하는 것이 좋습니다.

**6. 손목 (시스템 홈 단추) 근처에 단추를 추가 하지 않습니다** . 손 메뉴 단추가 홈 단추에 너무 가까이 배치 된 경우에는 손 메뉴와 상호 작용 하는 동안 실수로 트리거될 수 있습니다.

**G. 테스트, 테스트, 테스트:** 사람들에 게 편안 하 고 discomfort 하는 다른 임계값과 함께 다른 본문이 있습니다. 디자인을 테스트 하 고 다양 한 사용자의 의견을 얻으세요.

<br>

---

## <a name="hand-menu-placement-best-practices"></a>손 메뉴 배치 모범 사례

인간 분석에서 ulnar nerve은 ulna 뼈 근처에서 실행 되는 nerve입니다. Ulna는 엘보우에서 가장 작은 손가락으로 확장 되는 긴 뼈가 있습니다.

다음은 탐색를 기반으로 하는 두 가지 권장 위치입니다.


:::row:::
    :::column:::
        ![Ulnar 측면 위치](images/UlnarSideHandMenu.gif)<br>
        **야자수 내부에 있는 Ulnar**<br>
        이 위치는 서로 겹치지 않으므로 안정적입니다. 정확한 직접 검색 및 추적에 중요 합니다.
    :::column-end:::
    :::column:::
        ![Ulnar 측면 위치](images/UlnarAboveHandMenu.gif)<br>
        **2. 전 사랑 Nar**<br>
        이 위치는 손 메뉴와 상호 작용 하는 데 너무 많은 arm을 발생 시킬 필요가 없기 때문에 사용자에 게 친숙 합니다. **메뉴를** palm 위에 배치 하 고 ulnar 팜 내에서 단추를 정렬 하는 것이 좋습니다. [최적의 단추 크기에 대해 자세히 알아보세요.](interactable-object.md)<br>
        <br>
        기술적인 이유로이 위치에는 하나의 필수 구현이 권장 됩니다. 개발자는 사용자의 반대 바늘이 가까이와 상호 작용할 때 메뉴를 고정 해야 합니다. 이렇게 하면 겹치는 jitteriness 방지 하 고 더 빠르게 단추를 대상으로 지정할 수 있습니다.<br>
        <br>
        HoloLens 2 카메라는 서로 분리 된 경우를 정확 하 게 식별 합니다. 모든 겹치는 손을 통해 고정 위치에서 바로 메뉴가 이동 될 수 있습니다.<br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a>권장 되지 않는 메뉴 위치
다른 메뉴 레이아웃 및 위치를 사용 하 여 사용자 연구를 완료 했습니다. 다음 메뉴 위치를 사용 **하지 않는 것이 좋습니다**. 아래 각 연구의 단점을 찾으십시오.


:::row:::
    :::column:::
        arm](images/AboveArm.gif) ![<br>
        **Arm 위**<br>
        1-좋은 수동 추적을 유지 하기 어렵게 합니다.<br>
        2-비 자연 위치로 인해 사용자 피로 발생
    :::column-end:::
    :::column:::
        손가락을 ![](images/AboveFingers.gif)<br>
        **손가락 위**<br>
        피로 오랜 시간 동안 보유 하 고 있으므로 손을<br>
        2-인덱스 및 가운데 손가락에 대 한 추적 문제
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![센터 팜](images/handCenter.gif)<br>
        **위쪽-가운데 palm**<br>
        겹친 실습으로 인 한 1 손을 추적 하는 문제<br>
        피로 메뉴와 상호 작용 하는 데 오랜 시간이 소요 되기 때문에 2 손
    :::column-end:::
    :::column:::
        ![Top Fingertip](images/TopFingerTip.gif) **top Fingertip**<br>
        1 손을 추적 하는 문제<br>
        2\. 정상 상태를 유지 하는 손을 피로<br>
        3-손가락 사이의 제한 된 공간으로 인해 실수로 다른 손가락으로 단추를 누르는 문제
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        Arm](images/BackOfTheArm.gif)의 ![돌아갑니다.<br>
        **Arm의 후면**<br>
        1-실수로 홈 단추를 트리거할 수 있습니다.<br>
        2-사용자에 게 친숙 하거나 친숙 하지 않은 위치
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtkmixed-reality-toolkit-for-unity"></a>Unity 용 MRTK (Mixed Reality Toolkit)의 손 모양 메뉴
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 손 메뉴에 대 한 스크립트와 예제 장면을 제공 합니다. HandConstraintPalmUp 해 찾기 스크립트를 사용 하면 다양 한 구성 가능한 옵션을 사용 하 여 개체를 쉽게 연결할 수 있습니다.

* [MRTK-수동 제약 조건 및 HandConstraintPalmUp를 사용 하는 메뉴](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


<br>

---


## <a name="see-also"></a>참고 항목

* [커서](cursors.md)
* [손 광선](point-and-commit.md)
* [Button](button.md)
* [상호 작용 가능한 개체](interactable-object.md)
* [경계 상자 및 앱 바](app-bar-and-bounding-box.md)
* [조작](direct-manipulation.md)
* [손 메뉴](hand-menu.md)
* [Near 메뉴](near-menu.md)
* [개체 컬렉션](object-collection.md)
* [음성 명령](voice-input.md)
* [키보드](keyboard.md)
* [Tooltip](tooltip.md)
* [슬레이트](slate.md)
* [슬라이더](slider.md)
* [셰이더가](shader.md)
* [빌보딩 및 태그얼롱](billboarding-and-tag-along.md)
* [진행률 표시](progress.md)
* [표면 자성](surface-magnetism.md)
