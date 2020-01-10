---
title: 경계 상자 및 앱 바
description: 앱 바는 홀로그램 범위의 아래쪽 가장자리에 표시 되는 일련의 단추를 포함 하는 개체 수준 메뉴입니다.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, 앱 바, 경계 상자
ms.openlocfilehash: dab41207c2558fe8bb3fe07fca666cb2668f4e45
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723202"
---
# <a name="bounding-box-and-app-bar"></a>경계 상자 및 앱 바
![경계는 혼합 현실에서 개체 조작을 위한 표준 인터페이스입니다.](images/UX/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>경계 상자는 무엇 인가요?

경계는 혼합 현실에서 개체 조작을 위한 표준 인터페이스입니다. 사용자에 게 개체를 현재 조정할 수 있는 affordance 제공 합니다. HoloLens 2에서 경계 상자는 직접 조작을 사용 하 여 작동 하며 사용자의 finger's 근접에 응답 합니다. 사용자가 개체의 거리를 파악 하는 데 도움이 되는 시각적 피드백을 표시 합니다.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>개체 크기 조정<br>
        경계 상자의 모퉁이는 개체의 크기를 조정할 수 있음을 사용자에 게 알려줍니다. 핸들은 크기 조정을 조정 하기 위해 널리 이해 되는 패턴을 따릅니다. 이 시각적 개체는 조정 모드 외부에 표시 되지 않는 경우에도 사용자에 게 개체의 전체 영역을 affordance 표시 합니다. 이는 해당 개체가 없는 경우 다른 개체 또는 표면에 맞춰진 개체가 거기에 있어서는 안 되는 것 처럼 동작 하는 것 처럼 보일 수 있으므로 특히 중요 합니다.<br>
        <br>
        *비디오 루프: 경계 상자를 통해 개체 크기 조정*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       경계 상자를 통해 개체 크기를 조정 하는 ![HoloLens 관점](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>개체 회전<br>
        경계 상자 가장자리의 세로 사각형 affordances 회전 표시기입니다. 이렇게 하면 사용자가 배치 된 holograms을 보다 세부적으로 조정할 수 있습니다. 조정 하 고 크기를 조정할 수 있을 뿐만 아니라 이제 회전도 가능 합니다.<br>
        <br>
        *비디오 루프: 경계 상자를 통해 개체 회전*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       경계 상자를 통해 개체를 회전 하는 ![HoloLens 관점](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>HoloLens에서 근접 한 시각적 피드백 2<br>
        HoloLens 2에는 사용자가 깊이를 인식 하는 데 도움이 될 수 있는 추가 시각적 표시가 있습니다. Fingertip 근처의 링은 개체에 가까울수록 fingertip가 위쪽으로 표시 되 고 축소 됩니다. 누름 상태에 도달 하면 링이 결국 점으로 수렴. 이 시각적 affordance는 사용자가 개체에서 얼마나 떨어져 있는지 이해 하는 데 도움이 됩니다.<br>
        <br>
        *비디오 루프: 경계 상자에 근접 한 시각적 피드백의 예*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       직접 근접 한 시각적 피드백을 ![](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Unity 앱 개발의 경우 [혼합 현실 도구 키트-Unity에서 경계 상자](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 를 참조 하세요.**

<br>

---

## <a name="what-is-the-app-bar"></a>앱 바 란?

앱 바는 홀로그램 범위의 아래쪽 가장자리에 표시 되는 일련의 단추를 포함 하는 개체 수준 메뉴입니다. 이 패턴은 사용자에 게 holograms를 제거 하 고 조정 하는 기능을 제공 하는 데 일반적으로 사용 됩니다. 앱 바는 주로 사용자 환경에서 배치 된 개체를 관리 하는 방법으로 설계 되었습니다. 경계 상자와 함께 사용 하는 경우 사용자는 혼합 현실에서 개체의 방향 및 위치를 완전히 제어할 수 있습니다.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>앱 바는 사용자를 따릅니다.<br>
        이 패턴은 세계에서 잠긴 개체와 함께 사용 되므로 사용자가 개체를 이동할 때 앱 바는 항상 사용자에 게 가장 가까운 개체 쪽에 표시 됩니다. 이는 billboarding 되지 않지만 실제로 동일한 결과를 얻는 것입니다. 사용자의 위치를 려 하거나 환경의 다른 위치에서 사용할 수 있는 기능을 차단 합니다. <br>
        <br>
        *비디오 루프: 홀로그램 둘러보기, 앱 바는 다음과 같습니다.*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       홀로그램을 탐색 하는 ![. 앱 바는 다음과 같습니다.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 용 MRTK (Mixed Reality Toolkit)의 경계 상자
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 는 경계 상자와 앱 바에 대 한 스크립트 및 prefabs을 제공 합니다. BoundingBox.cs 스크립트를 개체에 할당 하기만 하면 경계 상자를 추가할 수 있습니다.

* [MRTK-경계 상자](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)


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
* [셰이더](shader.md)
* [빌보딩 및 태그얼롱](billboarding-and-tag-along.md)
* [진행률 표시](progress.md)
* [표면 자성](surface-magnetism.md)
