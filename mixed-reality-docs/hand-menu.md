---
title: 손 메뉴
description: 사용자는 직접 메뉴를 사용 하 여 자주 사용 하는 함수에 대 한 직접 연결 된 UI를 빠르게 가져올 수 있습니다. 다음은 직접 메뉴에 대 한 모범 사례 및 권장 사항입니다.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: 손, 메뉴, 단추, 빠른 액세스, 레이아웃
ms.openlocfilehash: d1d15b36bab2ca2082ca4ba91b9c64862893f80c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061173"
---
# <a name="hand-menu"></a>손 메뉴

![Ulnar 사이드 위치](images/UX/UX_Hero_HandMenu.jpg)

손 메뉴는 HoloLens 2에서 가장 고유한 UX 패턴 중 하나입니다. 이를 통해 직접 연결 된 UI를 신속 하 게 가져올 수 있습니다. 언제 든 지 액세스할 수 있으며 쉽게 표시 하 고 숨길 수 있으므로 빠른 작업에 유용 합니다.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

아래 목록에서 직접 메뉴를 사용 하는 방법에 대 한 권장 모범 사례를 찾을 수 있습니다. [Mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)의 손 메뉴를 보여 주는 예제 장면을 찾을 수도 있습니다.

<br>


---

## <a name="best-practices"></a>모범 사례
**단추 수를 작게 유지 합니다.** 

언제 든 지 잠긴 메뉴와 눈동자 간의 거리와 상대적으로 작은 시각적 영역에 초점을 맞춘 사용자의 추세 때문에 (시각의 attentional 원뿔 약 10도), 단추 수를 작게 유지 하는 것이 좋습니다. 탐색을 기반으로 세 개의 단추가 있는 한 열은 사용자가 시계를 FOV의 중심으로 이동 하는 경우에도 뷰 (FOV)의 모든 콘텐츠를 유지 하 여 잘 작동 합니다. 

**빠른 작업을 위한 손 메뉴 활용** 

Arm을 발생 시키고 위치를 유지 하면 arm 피로이 쉽게 발생할 수 있습니다. 짧은 상호 작용을 필요로 하는 메뉴에 대해 직접 잠긴 메서드를 사용 합니다. 메뉴가 복잡 하 고 확장 된 상호 작용 시간이 필요한 경우에는 대신 세계 잠금 또는 본문 잠금을 사용 하는 것이 좋습니다. 

**단추/패널 각도**

메뉴는 head의 반대 어깨와 중간 방향으로 빌보드를 수행 해야 합니다. 이렇게 하면 자연스럽 게 왼쪽 이동이 반대 방향으로 메뉴와 상호 작용 하 고 단추를 터치 하는 경우에는 불쾌 하거나 불편 한 위치를 방지할 수 있습니다. 

**단일 전달 또는 실습 작업 지원 고려**

사용자의 손을 항상 사용할 수 있다고 가정 하지 마세요. 하나 또는 둘 다를 사용할 수 없는 경우 광범위 한 컨텍스트를 고려 하 고 해당 상황에 대 한 설계 계정이 있는지 확인 합니다. 단방향 메뉴를 지원 하기 위해 손을 대칭 이동 하면 (팜 아래로 이동) 메뉴 배치를 왼쪽에서 잠김으로 전환 해 볼 수 있습니다. 직접 사용 하지 않는 시나리오의 경우 음성 명령을 사용 하 여 손 메뉴를 호출 하는 것이 좋습니다.

**손목 (시스템 홈 단추) 근처에 단추를 추가 하지 않습니다.**

손 메뉴 단추가 홈 단추 가까이에 배치 되 면 손 메뉴와 상호 작용 하는 동안 실수로 트리거될 수 있습니다.

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>크고 복잡 한 UI 컨트롤이 포함 된 손 모양 메뉴
<img src="images/UX/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
직접 연결 된 메뉴에서 단추나 UI 컨트롤의 수를 제한 하는 것이 좋습니다. 이는 많은 수의 UI 요소와의 확장 된 상호 작용이 arm 피로을 일으킬 수 있기 때문입니다. 환경에 많은 메뉴가 필요한 경우 사용자가 메뉴를 쉽게 잠글 수 있는 방법을 제공 합니다. 사용자가 손을 벗어나거나 대칭 이동 하는 경우에는 세계 잠금을 해제 한 다음 메뉴를 사용 하는 것이 좋습니다. 두 번째 방법은 사용자가 메뉴를 직접 가져올 수 있도록 하는 것입니다. 사용자가 메뉴를 놓으면 메뉴는 전 세계 잠금을 사용 해야 합니다. 이러한 방식으로 사용자는 오랜 시간 동안 편안 하 고 안전 하 게 다양 한 UI 요소를 조작할 수 있습니다. 

메뉴가 세계에서 잠긴 경우 메뉴를 이동 하는 방법을 제공 하 고 더 이상 필요 하지 않은 경우 메뉴를 닫습니다. 메뉴의 측면 또는 위쪽에 핸들을 제공 하 여 메뉴를 이동 가능 하 게 합니다. 닫기 단추를 추가 하 여 메뉴를 닫을 수 있습니다. 사용자가 사용자에 게 손을 면 메뉴를 다시 연결할 수 있습니다. 또한 거짓 활성화를 방지 하기 위해 사용자가 손을 gazes 하는 것이 좋습니다 (아래 참조).

**유용성 문제를 보여 주는 커다란 메뉴**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**직접 삭제 시 전 세계 잠긴 메뉴**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**수동으로 가져오기 & 전 세계로 가져오기-메뉴 잠금**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a>False 활성화를 방지 하는 방법

손 메뉴를 트리거하는 이벤트로 palm을 사용 하는 경우 사용자가 의도적으로 (통신 및 개체 조작을 위해) 손을 이동 하 고 실수로 해당 손을 이동 하기 때문에 필요 하지 않은 경우 실수로 나타날 수 있습니다 (가양성). False 활성화를 줄이려면 손 모양 메뉴를 호출 하는 추가 단계 (예: 완전히 열린 손가락 또는 사용자가 의도적으로 의도적으로 gazing)를 추가 합니다.

**평면 팜 필요**

평면을 사용 하면 사용자가 환경 내에서 통신 하는 동안 개체 또는 제스처를 조작 하는 경우에 발생할 수 있는 거짓 활성화를 방지할 수 있습니다. 

**응시 필요**

사용자가 직접 응시 하도록 요구 하면 (눈에 띄게 또는 head 응시 사용) 사용자가 자신에 게 사용자 편안을 허용 하는 데 사용 되는 조정 가능한 거리 임계값을 사용 하 여 사용자가 직접 직접 주의를 기울여야 하는 것으로 인해 거짓 활성화가 수행 되지 않습니다.  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>손 메뉴 배치 모범 사례

인간 분석에서 ulnar nerve은 ulna 뼈 근처에서 실행 되는 nerve입니다. Ulna는 엘보우에서 가장 작은 손가락으로 확장 되는 긴 뼈가 있습니다.

다음은 탐색를 기반으로 하는 두 가지 권장 위치입니다.


:::row:::
    :::column:::
        ![Ulnar 사이드 위치](images/UlnarSideHandMenu.gif)<br>
        **야자수 내부에 있는 Ulnar**<br>
        이 위치는 서로 겹치지 않으므로 안정적입니다. 정확한 직접 검색 및 추적에 중요 합니다.
    :::column-end:::
    :::column:::
        ![Ulnar 사이드 위치](images/UlnarAboveHandMenu.gif)<br>
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
        ![Arm 위](images/AboveArm.gif)<br>
        **Arm 위**<br>
        1-좋은 수동 추적을 유지 하기 어렵게 합니다.<br>
        2-비 자연 위치로 인해 사용자 피로 발생
    :::column-end:::
    :::column:::
        ![손가락 위](images/AboveFingers.gif)<br>
        **손가락 위**<br>
        피로 오랫동안 보유 하기 때문에 1 손을.<br>
        2-인덱스 및 가운데 손가락에 대 한 추적 문제
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![센터 팜 위](images/handCenter.gif)<br>
        **위쪽-가운데 palm**<br>
        겹친 실습으로 인 한 1 손을 추적 하는 문제<br>
        피로 메뉴와 상호 작용 하는 데 오랜 시간이 소요 되기 때문에 2 손
    :::column-end:::
    :::column:::
        ![Top Fingertip ](images/TopFingerTip.gif) **top Fingertip**<br>
        1 손을 추적 하는 문제<br>
        2 손을 피로 정상 상태를 유지 하 고 있습니다.<br>
        3-손가락 사이의 제한 된 공간으로 인해 실수로 다른 손가락으로 단추를 누르는 문제
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Arm의 후면](images/BackOfTheArm.gif)<br>
        **Arm의 후면**<br>
        1-실수로 홈 단추를 트리거할 수 있습니다.<br>
        2-자연 또는 편안한 위치가 아닙니다.
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 용 MRTK (Mixed Reality Toolkit)의 손 모양 메뉴
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 손 메뉴에 대 한 스크립트와 예제 장면을 제공 합니다. HandConstraintPalmUp 해결 프로그램 스크립트를 사용 하면 다양 한 구성 가능한 옵션을 통해 개체를 직접 연결할 수 있습니다. MRTK의 손 메뉴 예제에는 거짓 활성화를 방지 하기 위한 flat palm 및 응시 요구 사항과 같은 유용한 옵션이 포함 되어 있습니다.

* [손 메뉴 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [손 모양 메뉴 예제 장면](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

MRTK 예제 허브 앱을 사용 하 여 HoloLens 2에서 직접 메뉴 예제를 사용해 볼 수 있습니다. 
* [MRTK 예제 허브의 손 메뉴 장면](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a>참조

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
* [셰이더](shader.md)
* [빌보딩 및 태그얼롱](billboarding-and-tag-along.md)
* [진행률 표시](progress.md)
* [표면 자성](surface-magnetism.md)
