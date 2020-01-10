---
title: 진행률 표시
description: 진행률 컨트롤은 긴 작업을 진행 중인 사용자에게 피드백을 제공합니다.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 컨트롤, ui, ux
ms.openlocfilehash: d028b8717dae0e04a9a1104a8a4b7803023334ef
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723212"
---
# <a name="progress-indicator"></a>진행률 표시기

<br>

<img src="images/UX/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

진행률 컨트롤은 긴 작업을 진행 중인 사용자에게 피드백을 제공합니다. 이는 진행률 표시기가 표시될 때 사용자가 앱을 조작할 수 없다는 의미이며 사용되는 표시기에 따라 대기 시간을 예측할 수도 있다는 의미입니다.

<br>

---

## <a name="types-of-progress"></a>진행률 유형

발생 한 상황에 대 한 사용자 정보를 제공 하는 것이 중요 합니다. 혼합 현실에서는 앱이 좋은 시각적 피드백을 제공 하지 않는 경우 실제 환경 또는 개체에 의해 사용자가 쉽게 무시 수 있습니다. 데이터를 로드 하거나 장면을 업데이트 하는 경우와 같이 몇 초 정도 걸리는 상황에서는 시각적 표시기를 표시 하는 것이 좋습니다. 작업이 진행 중인 사용자를 표시 하는 두 가지 옵션은 **진행률 표시줄이** 나 **진행 링**입니다.

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>진행률 표시줄<br>
        진행률 표시줄에는 태스크의 완료율이 표시 됩니다. 기간이 알려진 작업 (활성화 상태의) 중에 사용 해야 하지만, 진행률은 사용자가 앱과의 상호 작용을 차단 하지 않아야 합니다.<br>
        <br>
        *이미지: HoloLens의 진행률 표시줄 예*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       HoloLens의 ![진행률 표시줄 예제](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>진행률 링<br>
        진행률 링은 확정 되지 않은 상태 이며 작업이 완료 될 때까지 추가 사용자 조작이 차단 되는 경우에만 사용 해야 합니다.<br>
        <br>
        *이미지: HoloLens의 진행 링 예*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       HoloLens의 ![진행률 링 예제](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>사용자 지정 개체의 진행률<br>
        사용자 지정 2D/3D 개체를 사용 하 여 진행률 컨트롤을 사용자 지정 하 여 앱의 개성 및 브랜드 id에 추가할 수 있습니다.<br>
        <br>
        *이미지: HoloLens의 사용자 지정 메시 예제를 사용 하 여 진행*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       HoloLens의 사용자 지정 메시 예제를 사용 하 여 진행 ![](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>최선의 구현 방법
* 사용자가 자신의 헤드를 빈 공간으로 쉽게 이동 하 고 컨텍스트를 손실할 수 있으므로 [billboarding 또는 태그](billboarding-and-tag-along.md) 를 진행률 표시와 긴밀 하 게 구분 합니다. 사용자가 아무것도 확인할 수 없는 경우 앱이 손상 된 것 처럼 보일 수 있습니다. Billboarding 및 태그 동반은 Progress prefab에 기본 제공 됩니다.
* 항상 사용자에 게 발생 하는 상황에 대 한 상태 정보를 제공 하는 것이 좋습니다. 진행률 prefab 상태를 제공 하기 위한 Windows 표준 링 유형 진행률을 비롯 한 다양 한 비주얼 스타일을 제공 합니다. 응용 프로그램의 브랜드에 맞게 진행률 스타일을 조정 하려는 경우 애니메이션으로 사용자 지정 메시를 사용할 수도 있습니다.

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 용 MRTK (Mixed Reality Toolkit)의 진행률 표시기

* [MRTK-진행률 표시기 prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK-장면 전환 서비스](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


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
