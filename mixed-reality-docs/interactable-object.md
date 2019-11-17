---
title: Interactable 개체
description: 단추는 긴 2D 추상 세계에서 이벤트를 트리거하는 데 사용 되는 비유입니다. 3 차원 혼합 현실 세계에서는 이러한 추상화의 목표로 더 이상 국한 되지 않습니다.
author: cre8ivepark
ms.author: jennyk
ms.date: 06/06/2019
ms.topic: article
keywords: 혼합 현실, 컨트롤, 상호 작용, ui, ux
ms.openlocfilehash: 73c8a3ce9e01f580ecbae23f2178871642c4540e
ms.sourcegitcommit: 17427d4d8c3723d53540f1b7f5bc061bba08c1d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2019
ms.locfileid: "74143261"
---
# <a name="interactable-object"></a>Interactable 개체

![Interactible 개체](images/UX/UX_Hero_Interactable.jpg)

단추는 긴 2D 추상 세계에서 이벤트를 트리거하는 데 사용 되는 비유입니다. 3 차원 혼합 현실 세계에서는 이러한 추상화의 목표로 더 이상 국한 되지 않습니다. 모든 항목은 이벤트를 트리거하는 **interactable 개체** 일 수 있습니다. Interactable 개체는 테이블의 커피에서 공기의 풍선 부동으로 표시할 수 있습니다. 대화 상자 UI에서와 같은 특정 상황에서는 여전히 기존 단추를 사용 합니다. 단추의 시각적 표시는 컨텍스트에 따라 달라 집니다.

<br>

---


## <a name="important-properties-of-the-interactable-object"></a>Interactable 개체의 중요 한 속성

### <a name="visual-cues"></a>시각적 신호

시각적 신호는 시각적 개체를 시각적으로 인식 하면서 시각적 시스템에서 처리 하 고 밝은 형태로 받은 토대로 된 큐입니다. 시각적 시스템은 다양 한 정보, 특히 사람에 게 중요 한 것 이므로 시각적 신호는 전 세계의 정보에 대 한 많은 정보를 표시 합니다.

Holographic 개체는 혼합 현실에서 실제 환경과 혼합 되므로 상호 작용할 수 있는 개체를 이해 하기 어려울 수 있습니다. 사용자 환경에서 모든 interactable 개체의 경우 각 입력 상태에 대해 차별화 된 시각적 신호를 제공 하는 것이 중요 합니다. 이렇게 하면 사용자가 interactable 하는 환경 부분을 이해 하 고 일관 된 상호 작용 방법을 사용 하 여 사용자를 신뢰할 수 있습니다.

<br>

---

### <a name="far-interactions"></a>먼 상호 작용

사용자가 응시, 손 모양 및 모션 컨트롤러의 광선과 상호 작용할 수 있는 개체의 경우 다음과 같은 세 가지 입력 상태에 대해 서로 다른 시각적 표시를 사용 하는 것이 좋습니다.

:::row:::
    :::column:::
       ![interactibleobject-기본](images/interactibleobject-states-default.jpg)<br>
       **기본 (관찰) 상태**<br>
        개체의 기본 유휴 상태입니다.
    커서가 개체에 없습니다. 손으로 검색 되지 않았습니다.
    :::column-end:::
    :::column:::
       ![interactibleobject-대상](images/interactibleobject-states-targeted.jpg)<br>
        **대상 (가리키기) 상태**<br>
        개체가 응시 커서, 손가락 근접 또는 동작 컨트롤러의 포인터를 대상으로 하는 경우
    커서가 개체에 있습니다. 준비가 완료 되었습니다.
    :::column-end:::
    :::column:::
       ![interactibleobject-누름](images/interactibleobject-states-pressed.jpg)<br>
       **누름 상태**<br>
        공기 탭 제스처를 사용 하 여 개체를 누르면 손가락을 누르거나 동작 컨트롤러의 선택 단추를 선택 합니다.
    커서가 개체에 있습니다. 손으로 검색 되었습니다.
    :::column-end:::
:::row-end:::

<br>

---

강조 표시 또는 크기 조정과 같은 기술을 사용 하 여 사용자의 입력 상태를 시각적으로 파악할 수 있습니다. 혼합 현실에서는 시작 메뉴와 앱 바 단추를 사용 하 여 다양 한 입력 상태를 시각화 하는 예제를 찾을 수 있습니다. 

**Holographic 단추**에서 이러한 상태는 다음과 같습니다.

:::row:::
    :::column:::
       ![interactibleobject-기본](images/MRTK_InteractableState-default.jpg)<br>
       **기본 (관찰) 상태**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-대상](images/MRTK_InteractableState-targeted.jpg)<br>
        **대상 (가리키기) 상태**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-누름](images/MRTK_InteractableState-pressed.jpg)<br>
       **누름 상태**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>거의 상호 작용 (직접) 

HoloLens 2는 개체와 상호 작용할 수 있도록 하는 트레일러 추적 입력을 지원 합니다. 사용자 의견을 햅 하 고 완벽 하 게 인식 하지 못하는 경우에도 개체에서 얼마나 멀리 떨어져 있는지 또는 사용자가 이야기 하 고 있는지를 확인 하는 것이 어려울 수 있습니다. 개체 상태를 전달 하는 데 충분 한 시각적 신호를 제공 하 고 해당 개체와 관련 된 사용자의 상태를 제공 하는 것이 중요 합니다.

시각적 피드백을 사용 하 여 다음을 전달 합니다.
* **Default (관찰)** : 개체의 기본 유휴 상태입니다.
* **가리키기**: 손을 홀로그램 근처에 있으면 시각적 개체를 대상으로 하 여 홀로그램을 대상으로 하는 통신으로 변경 합니다. 
* **거리 및 상호 작용 지점**: 홀로그램은 홀로그램에 근접 하 고, 예상 되는 상호 작용 지점을 전달 하기 위한 디자인 피드백을 비롯 하 여 개체의 거리와
* **연락처 시작**: 터치가 발생 했음을 알리기 위해 시각적 개체 (광원, 색)를 변경 합니다.
* **Grasped**: 개체가 Grasped 경우 시각적 개체 (광원, 색)를 변경 합니다.
* **연락처 끝**: 터치가 종료 되 면 시각적 개체 (밝은 색)를 변경 합니다.

<br>

---

:::row:::
    :::column:::
        ![가리키기 (Far)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **가리키기 (Far)**<br>
        손 모양에 따라 강조 표시 합니다.
    :::column-end:::
    :::column:::
        ![가리키기 (근처)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **가리키기 (근처)**<br>
        강조 표시 크기는 손 거리에 따라 변경 됩니다.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![Touch/press](images/640px-interactibleobject-states-near-press.jpg)<br>
        **터치/누르기**<br>
        시각적 개체와 오디오 피드백
    :::column-end:::
    :::column:::
        ![](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **잡습니다**<br>
        시각적 개체와 오디오 피드백
    :::column-end:::
:::row-end:::

<br>

<br>

---

[HoloLens 2의 단추](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) 는 서로 다른 입력 상호 작용 상태를 시각화 하는 방법의 예입니다.

:::row:::
    :::column:::
        ![기본](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **기본**<br>
    :::column-end:::
    :::column:::
        ![가리키기](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **오도록**<br>
        근접 기반 조명 효과를 표시 합니다.
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![터치](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **터치**<br>
        Ripple 효과를 표시 합니다.
    :::column-end:::
    :::column:::
        ](images/640px-interactibleobject-pressablebutton-press.jpg) ![누르기<br>
        **누르면**<br>
        프런트 판을 이동 합니다.
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>HoloLens 2의 "링" 시각 신호<br>
        HoloLens 2에는 사용자가 깊이를 인식 하는 데 도움이 될 수 있는 추가 시각적 표시가 있습니다. Fingertip 근처의 링은 개체에 가까울수록 fingertip가 위쪽으로 표시 되 고 축소 됩니다. 누름 상태에 도달 하면 링이 결국 점으로 수렴. 이 시각적 affordance는 사용자가 개체에서 얼마나 떨어져 있는지 이해 하는 데 도움이 됩니다.<br>
        <br>
        *비디오 루프: 경계 상자에 근접 한 시각적 피드백의 예*
    :::column-end:::
        :::column:::
        ![공간](images/spacer-20x582.png)<br>
       직접 근접 한 시각적 피드백을 ![](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>오디오 신호

직접 상호 작용을 위해 적절 한 오디오 피드백을 통해 사용자 환경을 크게 향상 시킬 수 있습니다. 오디오 피드백을 사용 하 여 다음을 전달 합니다.
* **연락처 시작**: 터치 시작 시 소리 재생
* **연락처 끝**: 터치 엔드에서 소리 재생
* **시작**: 잡기 시작 시 소리 재생
* **잡기 종료**: 잡기 종료 시 소리 재생

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>음성 명령<br>
        Interactable 개체의 경우 대체 상호 작용 옵션을 지 원하는 것이 중요 합니다. 기본적으로 interactable 되는 모든 개체에 대해 [음성 명령](voice-design.md) 지원을 권장 합니다. 검색 가능성을 향상 시키기 위해 가리키기 상태에서 도구 설명을 제공할 수도 있습니다.<br>
        <br>
        *Image: 음성 명령에 대 한 도구 설명*
    :::column-end:::
        :::column:::
       ![음성 명령](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a>크기 조정 권장 사항 

사용자가 모든 interactable 개체를 쉽게 사용할 수 있도록 하려면 사용자의 거리를 기준으로 interactable이 최소 크기 (시각적 원호의 각도로 측정 되는 시각적 각도)를 충족 하는지 확인 하는 것이 좋습니다. 시각적 각도는 사용자의 눈동자와 개체 간의 거리를 기준으로 하며 일정 하 게 유지 되 고, 대상의 실제 크기는 사용자의 거리가 변경 될 때 변경 될 수 있습니다. 사용자의 거리를 기준으로 개체의 필요한 실제 크기를 확인 하려면 [다음과 같은 시각적](https://elvers.us/perception/visualAngle/)각도 계산기를 사용해 보세요.

다음은 interactable 콘텐츠의 최소 크기에 대 한 권장 사항입니다.


### <a name="target-size-for-direct-hand-interaction"></a>직접 상호 작용의 대상 크기

| 거리 | 시야각 | 사이즈 |
|---------|---------|---------|
| 45cm  | 2 ° 미만 | 1.6 x 1.6 cm |

직접 상호 작용에 대 한 대상 크기를 ![](images/TargetSizingNear.jpg)<br>
*직접 상호 작용의 대상 크기*

<br>

### <a name="target-size-for-buttons"></a>단추의 대상 크기

직접 상호 작용에 대 한 단추를 만들 때 아이콘 및 잠재적으로 일부 텍스트를 포함할 수 있는 충분 한 공간이 있도록 최소 크기인 3.2 x 3.2 cm을 권장 합니다.

| 거리 | 최소 크기 |
|---------|---------|
| 45cm  | 3.2 x 3.2 cm |

단추에 대 한 대상 크기를 ![](images/TargetSizingButtons.png)<br>
*단추의 대상 크기*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>핸드 레이 또는 응시 상호 작용의 대상 크기
| 거리 | 시야각 | 사이즈 |
|---------|---------|---------|
| 2m  | 1 ° 보다 작음 | 3.5 x 3.5 cm |

손으로 광선 또는 응시 상호 작용에 대 한 대상 크기를 ![](images/TargetSizingFar.jpg)<br>
*핸드 레이 또는 응시 상호 작용의 대상 크기*


<br>

---


## <a name="interactable-object-in-mrtkmixed-reality-toolkit-for-unit"></a>단위에 대 한 MRTK (Mixed Reality Toolkit)의 Interactable 개체

**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 에서는 [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) 스크립트를 사용 하 여 개체를 다양 한 유형의 입력 상호 작용 상태에 응답할 수 있습니다. 색, 크기, 재질, 셰이더 등의 개체 속성을 제어 하 여 시각적 상태를 정의할 수 있도록 하는 다양 한 형식의 테마를 지원 합니다.

* [Interactable](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [직접 상호 작용 예제 장면](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit의 표준 셰이더는 시각적 및 오디오 큐를 만드는 데 도움이 되는 **근접 조명** 과 같은 다양 한 옵션을 제공 합니다.
* [MRTK 표준 셰이더](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


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
