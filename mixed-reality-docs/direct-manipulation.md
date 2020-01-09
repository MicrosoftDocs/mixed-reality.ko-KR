---
title: 수동으로 직접 조작
description: 직접 조작 입력 모델의 개요
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Gaze, gaze targeting, interaction, design, hands near, HoloLens
ms.openlocfilehash: d263c84d306a2ece3783c2e7fb0e3f599dec49eb
ms.sourcegitcommit: 270ca09ec61e1153a83cf44942d7ba3783ef1805
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694177"
---
# <a name="direct-manipulation-with-hands"></a>수동으로 직접 조작

![단추](images/UX/UX_Hero_Manipulation.jpg)

직접 조작은 홀로그램을 손으로 직접 터치하게 되는 입력 모델입니다. 이 개념의 기본 아이디어는 개체가 실제 세계에서처럼 작동하는 것입니다. 단추는 간단히 눌러서 활성화하고, 개체는 잡아서 선택할 수 있으며, 2D 콘텐츠는 가상의 터치 스크린처럼 동작합니다. 이렇게 하면 사용자가 직접 조작하면서 쉽고 재미있게 학습할 수 있습니다. 팔을 뻗어 닿을 수 있는 콘텐츠와 상호 작용하는 데 가장 적합하다는 점에서 “근거리” 입력 모델로 간주됩니다.

직접 조작은 어포던스를 기준으로 합니다. 즉, 사용자 친화적입니다. 사용자를 교육하기 위한 기호화된 제스처는 없습니다. 모든 상호 작용은 사용자가 터치하거나 잡을 수 있는 시각적 요소를 중심으로 구축됩니다.

## <a name="device-support"></a>디바이스 지원

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>입력 모델</strong></td>
     <td><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
</tr>
<tr>
     <td>수동으로 직접 조작</td>
     <td>❌ 지원 안 됨</td>
     <td>✔️ 권장</td>
     <td>➕ 대안으로 <a href="point-and-commit.md">손으로 가리키고 커밋</a>이 권장됩니다.</td>
    
</tr>
</table>


직접 조작은 HoloLens 2의 기본 입력 모델이며, 새로운 연결형 손 추적 시스템을 사용합니다. 이 입력 모델은 모션 컨트롤러를 사용하여 몰입형 헤드셋에서도 사용할 수 있지만 개체 조작 이외의 상호 작용을 위한 기본 수단으로는 권장되지 않습니다. HoloLens(1세대)에는 직접 조작을 사용할 수 없습니다.

<br>

---

## <a name="collidable-fingertip"></a>충돌 가능한 손끝

HoloLens 2에서 사용자의 실제 손은 왼손 및 오른손 골격 모델로 인식 및 해석됩니다. 손으로 홀로그램을 직접 터치한다는 개념을 적절히 구현하기 위해 각 손 골격 모델의 5개 손끝에 5개의 충돌체(collider)를 연결할 수 있습니다. 그러나 촉각 피드백이 부족하기 때문에 10개의 충돌 가능한 손끝이 홀로그램과 예기치 않은 충돌을 유발할 수 있습니다. 

따라서 각 집게 손가락에만 충돌체(collider)를 놓는 것이 좋습니다. 아래 이미지와 같이, 충돌 가능한 집게 손끝은 여전히 다른 손가락과 관련된 다양한 터치 제스처(예: 한 손가락으로 누르기, 한 손가락으로 탭하기, 두 손가락으로 누르기, 다섯 손가락으로 누르기)를 위한 활성 터치 포인트 역할을 할 수 있습니다.

:::row:::
    :::column:::
       ![충돌 가능한 손끝](images/Collidable-Fingertip.jpg)<br>
       **충돌 가능한 손끝**<br>
    :::column-end:::
    :::column:::
       ![한 손가락으로 누르기](images/Collidable-Fingertip-1-finger-press.jpg)<br>
        **한 손가락으로 누르기**<br>
    :::column-end:::
    :::column:::
       ![한 손가락으로 탭하기](images/Collidable-Fingertip-1-finger-tap.jpg)<br>
       **한 손가락으로 탭하기**<br>
    :::column-end:::
    :::column:::
       ![다섯 손가락으로 누르기](images/Collidable-Fingertip-5-finger-press.jpg)<br>
       **다섯 손가락으로 누르기**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a>구형 충돌체(collider)

임의의 일반 셰이프를 사용하는 대신, 구형 충돌체(collider)를 사용하는 것이 좋습니다. 그러면, 시각적 렌더링을 통해 근거리 대상 지정에 더 나은 단서를 제공할 수 있습니다. 터치 정확도를 높이려면 구의 지름이 집게 손가락의 두께와 일치해야 합니다. 손 API를 호출하여 손가락 두께 변수를 쉽게 검색할 수 있습니다.

### <a name="fingertip-cursor"></a>손끝 커서

집게 손끝에 충돌 가능한 구형을 렌더링하는 것 외에, 더 나은 근거리 대상 지정 환경을 얻기 위해 고급 손끝 커서를 만들었습니다. 집게 손끝에 연결된 도넛형 커서입니다. 아래에 설명된 것처럼, 근접성에 따라 대상의 방향 및 크기 변화에 동적으로 반응합니다.

* 집게 손가락을 홀로그램 쪽으로 움직이면 커서는 항상 홀로그램 표면에 평행하게 움직이며 크기가 서서히 축소됩니다.
* 손가락으로 표면을 터치하는 즉시, 커서가 점으로 축소되고 터치 이벤트를 내보냅니다.

대화형 피드백을 사용하면 사용자는 아래와 같이 하이퍼링크 트리거 또는 단추 누르기와 같은 높은 정확도의 근거리 대상 지정 작업을 달성할 수 있습니다. 

:::row:::
    :::column:::
       ![손끝 커서 멀리](images/Fingertip-cursor-far.jpg)<br>
       **손끝 커서 멀리**<br>
    :::column-end:::
    :::column:::
       ![손끝 커서 가까이](images/Fingertip-cursor-near.jpg)<br>
        **손끝 커서 가까이**<br>
    :::column-end:::
    :::column:::
       ![손끝 커서 접촉](images/Fingertip-cursor-contact.jpg)<br>
       **손끝 커서 접촉**<br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a>근접 셰이더가 있는 경계 상자

홀로그램 자체에는 촉각 피드백 부족을 보정하기 위해 시각적 및 청각적 피드백을 둘 다 제공하는 기능도 필요합니다. 이를 위해 근접 셰이더를 포함하는 경계 상자 개념을 생성합니다. 경계 상자는 3D 개체를 둘러싸는 최소 체적 영역입니다. 경계 상자에는 근접 셰이더라는 대화형 렌더링 메커니즘이 포함되어 있습니다. 근접 셰이더는 다음과 같이 동작합니다.

:::row:::
    :::column:::
       ![시각적 피드백이 있는 가리키기(멀리)](images/bounding-box-with-proximity-shader-hover-far.jpg)<br>
       **가리키기(멀리)**<br>
       집게 손가락이 범위 내에 있는 경우 손끝 스포트라이트가 경계 상자 표면에 캐스팅됩니다.
    :::column-end:::
    :::column:::
       ![시각적 피드백이 있는 가리키기(가까이)](images/bounding-box-with-proximity-shader-hover-near.jpg)<br>
        **가리키기(가까이)**<br>
        손끝이 화면에 가까워질수록, 스포트라이트도 그에 따라 축소됩니다.
    :::column-end:::
    :::column:::
       ![접촉 시작](images/bounding-box-with-proximity-shader-begin-contact.jpg)<br>
       **접촉 시작**<br>
       손끝이 표면을 터치하는 즉시, 전체 경계 상자의 색상이 바뀌거나 터치 상태를 반영하는 시각적 효과가 생성됩니다.
    :::column-end:::
    :::column:::
       ![접촉 끝](images/bounding-box-with-proximity-shader-end-contact.jpg)<br>
       **접촉 끝**<br>
       또한 시각적 터치 피드백을 향상시키기 위해 음향 효과를 활성화할 수 있습니다.
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a>누를 수 있는 단추

충돌 가능한 손끝을 사용하면 사용자가 기본적인 홀로그래픽 UI 구성 요소(예: 누를 수 있는 단추)와 상호 작용할 수 있습니다. 누를 수 있는 단추는 직접적인 손가락 누르기에 맞게 조정된 홀로그래픽 단추입니다. 다시 말하지만, 촉각 피드백이 부족하기 때문에 누를 수 있는 단추에는 촉각 피드백 관련 이슈를 해결하기 위한 몇 가지 메커니즘이 포함되어 있습니다.

* 첫 번째 메커니즘은 근접 셰이더가 있는 경계 상자이며, 이전 섹션에 자세히 설명되어 있습니다. 이 메커니즘은 사용자가 단추에 접근하여 접촉할 때 더 근접한 느낌을 줍니다.
* 두 번째 메커니즘은 누르기입니다. 누르기는 손끝이 단추에 닿은 후 아래쪽을 누르는 감각을 만듭니다. 이 메커니즘은 단추가 손끝에 맞춰 깊이 축을 따라 움직이도록 합니다. 단추는 지정된 깊이(누를 때)에 도달하거나 해당 깊이를 통과한 후 떠나면(뗄 때) 트리거될 수 있습니다.
* 단추가 트리거될 때 피드백을 향상시키기 위해 음향 효과를 추가해야 합니다.

:::row:::
    :::column:::
       ![누를 수 있는 단추 멀리](images/pressable-button-far.jpg)<br>
       **멀리 있는 손가락**<br>
    :::column-end:::
    :::column:::
       ![누를 수 있는 단추 가까이](images/pressable-button-approach.jpg)<br>
        **접근하는 손가락**<br>
    :::column-end:::
    :::column:::
       ![누를 수 있는 단추 접촉 시작](images/pressable-button-contact.jpg)<br>
       **접촉 시작**<br>
    :::column-end:::
    :::column:::
       ![누를 수 있는 단추 누르기](images/pressable-button-press.jpg)<br>
       **아래로 누르기**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>2D 슬레이트 상호 작용

2D [슬레이트](slate.md)는 웹 브라우저와 같은 2D 앱 콘텐츠를 호스트하는 데 사용되는 홀로그램 컨테이너입니다. 직접 조작을 통해 2D 슬레이트와 상호 작용하기 위한 디자인 개념은 실제 터치 스크린과 상호 작용하는 상상 모델을 활용하는 것입니다.

### <a name="to-interact-with-the-slate-contact"></a>슬레이트 접촉 부분과 상호 작용하려면

:::row:::
    :::column:::
       ![터치](images/2d-slate-interaction-touch.jpg)<br>
       **터치**<br>
       집게 손가락으로 하이퍼링크 또는 단추를 누릅니다.
    :::column-end:::
    :::column:::
       ![스크롤](images/2d-slate-interaction-scroll2.jpg)<br>
        **스크롤**<br>
        집게 손가락으로 슬레이트 콘텐츠 위/아래로 스크롤합니다.
    :::column-end:::
    :::column:::
       ![확대/축소](images/2d-slate-interaction-zoom2.jpg)<br>
       **확대/축소**<br>
       사용자는 2개의 집게 손가락을 사용하여 손가락의 상대적 모션에 따라 슬레이트 콘텐츠를 확대 및 축소합니다.
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a>2D 슬레이트 자체를 조작하려면

:::row:::
    :::column:::
       ![이동](images/manipulate-2d-slate-move.jpg)<br>
       **이동**<br>
       손을 모서리와 가장자리 쪽으로 이동하여 가장 가까운 조작 어포던스를 드러냅니다. 2D 슬레이트의 맨 위에 있는 홀로바를 잡으면, 슬레이트 전체를 옮길 수 있습니다.
    :::column-end:::
    :::column:::
       ![크기 조정](images/manipulate-2d-slate-scale.jpg)<br>
        **크기 조정**<br>
        조작 어포던스를 잡고, 모서리 어포던스를 통해 균일하게 크기를 조정합니다.
    :::column-end:::
    :::column:::
       ![재배치](images/manipulate-2d-slate-reflow.jpg)<br>
       **재배치**<br>
       조작 어포던스를 잡고, 모서리 어포던스를 통해 재배치를 수행합니다.
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a>3D 개체 조작

HoloLens 2에서는 사용자가 3D 개체마다 경계 상자를 적용하여 손으로 3D 홀로그래픽 개체를 겨냥하고 조작할 수 잇습니다. 경계 상자는 근접 셰이더를 통해 더 나은 깊이 인식을 제공합니다. 경계 상자를 사용하면 3D 개체 조작을 위해 두 가지 디자인 방식을 사용할 수 있습니다.

### <a name="affordance-based-manipulation"></a>어포던스 기반 조작

어포던스 기반 조작에서는 경계 상자와 주변의 조작 어포던스를 통해 3D 개체를 조작할 수 있습니다. 

:::row:::
    :::column:::
       ![이동](images/3d-object-manipulation-move.jpg)<br>
       **이동**<br>
       사용자의 손이 3D 개체에 가까워지는 즉시, 경계 상자와 가장 가까운 어포던스가 표시됩니다. 사용자가 경계 상자를 잡고 전체 개체를 옮길 수 있습니다.
    :::column-end:::
    :::column:::
       ![회전](images/3d-object-manipulation-rotate.jpg)<br>
        **회전**<br>
        사용자가 가장자리 어포던스를 잡아서 회전할 수 있습니다.
    :::column-end:::
    :::column:::
       ![크기 조정](images/3d-object-manipulation-scale.jpg)<br>
       **크기 조정**<br>
       사용자가 모서리 어포던스를 잡아서 균일하게 크기를 조정할 수 있습니다.
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a>비어포던스 기반 조작

비어포던스 기반 조작은 경계 상자에 어포던스를 연결하지 않습니다. 사용자는 경계 상자만 표시한 후 직접 상호 작용할 수 있습니다. 한 손으로 경계 상자를 잡을 경우 개체의 변환 및 회전은 손의 동작 및 방향과 연결됩니다. 두 손으로 경계 상자를 잡을 경우 두 손의 상대적 동작에 따라 변환, 크기 조정 및 회전할 수 있습니다.

특정 조작에는 정밀도가 요구됩니다. 따라서 더 높은 세분성을 제공하는 **어포던스 기반 조작**을 사용하는 것이 좋습니다. 유연한 조작을 위해서는 즉각적이면서 유용한 환경을 지원하는 **비어포던스 조작**을 사용하는 것이 좋습니다.

<br>

---


## <a name="instinctual-gestures"></a>직관적 제스처

HoloLens(1세대)에서는 미리 정의된 몇 가지 제스처(예: 블룸 및 에어 탭)를 사용자에게 학습시켰습니다. HoloLens 2에서는 사용자에게 기호화된 제스처를 기억하도록 요구하지 않습니다. 사용자가 홀로그램 및 콘텐츠와 상호 작용하는 데 필요한 모든 제스처는 직관적입니다. 직관적 제스처를 달성하는 방법은 사용자가 UI 어포던스의 디자인을 통해 제스처를 수행하도록 돕는 것입니다.

예를 들어, 사용자가 두 손가락 모으기로 개체나 제어점을 잡도록 하려면 개체나 제어점이 작아야 합니다. 사용자가 5개 손가락으로 잡기를 수행하도록 하려면 개체 또는 제어점이 비교적 커야 합니다. 단추의 경우도 마찬가지로, 단추 크기가 작으면 사용자는 한 손가락으로 누르게 되지만, 단추 크기가 크면 손바닥으로 누르게 됩니다.


:::row:::
    :::column:::
       ![이동](images/instinctual-gestures-smallobject.jpg)<br>
       **소형 개체**<br>
    :::column-end:::
    :::column:::
       ![회전](images/instinctual-gestures-mediumobject.jpg)<br>
        **중형 개체**<br>
    :::column-end:::
    :::column:::
       ![크기 조정](images/instinctual-gestures-largeobject.jpg)<br>
       **대형 개체**<br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>손과 6 DoF 컨트롤러 간의 대칭 디자인

AR의 손과 VR의 모션 컨트롤러 간에는 상호 작용 평행 이론이 작용한다는 것을 알 수 있습니다. 두 입력은 모두 해당 환경에서 직접 조작을 트리거하는 데 사용할 수 있습니다. HoloLens 2의 근거리에서 손으로 잡아 끄는 동작은 WMR 모션 컨트롤러에 있는 잡기 단추로 작동하는 것과 같습니다. 따라서 사용자는 두 플랫폼에서 유사하게 조작할 수 있기 때문에, 애플리케이션을 한 플랫폼에서 다른 플랫폼으로 이식하는 경우 유용할 수 있습니다.

<br>

---

## <a name="optimize-with-eye-tracking"></a>시선 추적으로 최적화

직접 조작은 의도한 대로 작동한다면 마법과 같이 느껴질 수 있습니다. 하지만 손을 움직일 때마다 홀로그램이 의도와 다르게 트리거되면 당황할 수 있습니다. 시선 추적은 사용자의 의도를 더 잘 식별하는 데 유용할 수 있습니다.

* **사용할 때**: 조작 대응을 잘못 트리거하는 경우를 줄입니다. 시선 추적은 사용자가 현재 진행 중인 작업을 더 잘 이해할 수 있도록 합니다.
예를 들어, 실제 작업 공구를 잡기 위해 팔을 뻗으면서 홀로그래픽(지침) 텍스트를 읽는 경우를 가정해 봅니다.

이렇게 하여 이전에 알아채지 못했던(예: 사용자의 FoV(시야각) 밖에 있을 수도 있음) 일부 대화형 홀로그래픽 단추 사이에서 실수로 손을 움직이게 됩니다.

  요약: 사용자가 한참 동안 홀로그램을 보지 않았는데도 터치 또는 잡기 이벤트가 감지된 경우, 사용자가 해당 홀로그램과 상호 작용하려는 의도가 실제로 없었을 가능성이 높습니다.

* **선택한 대상**:  또 다른 예로 가양성 활성화를 처리하는 것 외에, 여러 개의 홀로그램이 서로 가깝게 배치된 경우 특히, 사용자 관점에서 정확한 교차점을 알 수 없으므로 잡거나 찌를 홀로그램을 더 잘 식별하는 경우를 들 수 있습니다.

  HoloLens 2의 시선 추적은 시선 응시를 정확하게 확인할 수 있는 정도에 따라 제한이 있지만, 손 입력으로 조작할 때는 깊이 차이가 있으므로 근거리 조작에 매우 유용할 수 있습니다. 즉, 경우에 따라 조작 위젯을 정확히 잡기 위해 손을 홀로그램 뒤에 둘지 아니면 앞에 둘지를 결정하는 것이 어려울 수 있습니다.

* **대상 위치**: 빨리 던지기 제스처에서 사용자가 바라보는 대상에 대한 정보를 사용합니다. 홀로그램을 잡은 후 의도한 대상 쪽으로 대충 던집니다.  

    이러한 조작은 일반적으로 잘 작동하지만, 손 제스처를 빠르게 수행할 경우 대상이 부정확할 수 있습니다. 하지만 시선 추적은 제스처의 정확도를 향상시킬 수 있습니다.

<br>

---

## <a name="manipulation-in-mrtkmixed-reality-toolkit-for-unity"></a>Unity용 MRTK(Mixed Reality Toolkit)의 조작
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 를 사용하면 **ManipulationHandler** 스크립트를 사용하여 일반적인 조작 동작을 쉽게 수행할 수 있습니다. ManipulationHandler를 사용하면 직접 손이나 손 광선으로 직접 개체를 잡아 이동할 수 있습니다. 또한 개체의 크기 조정 및 회전을 위해 양손 조작도 지원합니다.

* [MRTK - 조작](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)


---

## <a name="see-also"></a>참고 항목

* [헤드 게이즈 및 커밋](gaze-and-commit.md)
* [수동으로 가리키고 커밋](point-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
