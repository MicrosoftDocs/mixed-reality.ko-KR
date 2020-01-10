---
title: 커서
description: 대상 벡터의 커서 또는 표시기는 사용자에 대 한 지속적인 피드백을 제공 하 여 HoloLens의 용도에 대 한 정보를 파악할 수 있습니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (첫 번째 gen), HoloLens 2, 혼합 현실, 커서, 대상 지정, 응시, 제스처
ms.openlocfilehash: 969906cb09e100dbdd289d78baba722a4bd32537
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723242"
---
# <a name="cursors"></a>커서

![커서](images/UX/UX_Hero_Cursor.jpg)

현재 대상 벡터의 커서 또는 표시기는 헤드셋에서 현재 포커스가 있는 위치를 파악할 수 있도록 사용자에 게 지속적인 피드백을 제공 합니다. 사용자는 커서를 사용 하 여 현재 대상 지정 지점을 이해 하 고 사용자가 입력에 응답 하는 영역, 홀로그램 또는 점을 나타내는 피드백 역할을 할 수 있습니다. 장치에서 사용자의 주의가 인식 되는 위치를 디지털로 표현한 것입니다. 단,이는 의도에 대 한 모든 사항을 결정 하는 것과 다를 수 있습니다.

커서에서 제공 하는 피드백은 사용자가 시스템에 응답 하는 방법을 예상할 수 있는 기능을 제공 하 고, 해당 신호를 피드백으로 사용 하 여 장치에 대 한 의도를 더 잘 전달 하 고, 궁극적으로 상호 작용 하는 것이 더 확실

**손가락, 광선**및 **헤드-응시**의 세 가지 종류의 커서가 있습니다. 이러한 포인팅 커서는 HoloLens, HoloLens 2 및 모던 헤드셋에서 다른 입력 소프트웨어나 사용 됩니다. 다음은 각 유형의 헤드셋 및 상호 작용 모델에 사용할 커서 유형에 대 한 지침입니다. Mixed Reality Toolkit (MRTK)에서 끌어서 놓기 커서 모듈을 만들어 올바른 포인팅 환경을 구축할 수 있습니다.


## <a name="device-support"></a>장치 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>기능</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>손가락 커서</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>레이 커서</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>헤드-응시 커서</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>손가락 커서
핑거 커서는 "[손으로 직접 조작](direct-manipulation.md)" 상호 작용 모드를 향상 시키기 위해 HoloLens 2 에서만 사용할 수 있습니다. 손가락이 가리키는 위치를 더 잘 이해 하기 위해 두 인덱스 손가락의 팁에 링을 연결 했습니다. 링 크기는 손가락의 근접성 (손가락 가까이, 링의 작은 쪽)을 기반으로 하며, 손가락이 UI와 접촉 하면 점 모양으로 축소 됩니다. <br>

![손가락 커서](images/finger-cursor.png)<br>
**손가락 커서 1의 시각적 피드백 상태** : 링이 점으로 축소 됩니다. 2: 링이 표면과 맞춰집니다. 3: 링이 손가락 벡터에 수직 합니다. 4: 링 없음

## <a name="ray-cursor"></a>레이 커서
광선 커서는 먼 곳의 끝에 연결 하 여 손을 벗어난 개체를 조작할 수 있도록 합니다. 몰입 형 헤드셋에서 광선은 동작 컨트롤러에서 시작 하 여 점 커서에서 종료 됩니다. HoloLens 2에서는 이러한 동작 컨트롤러 광선의 멘 탈 모델을 활용 하 고 직접 조작에 사용 되는 손가락 커서와 일치 하는 고리 모양의 커서에서 시작 하 여 palms에서 시작 하는 핸드 광선을 설계 했습니다. <br>
:::row:::
    :::column:::
        ![레이 커서 컨트롤러](images/ray-cursor-controller.png)<br>
        **동작 컨트롤러의 레이 커서**<br>
    :::column-end:::
    :::column:::
        ![레이 커서 손](images/ray-cursor-hand.png)<br>
        **바늘의 레이 커서**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a>헤드-응시 커서
헤드-응시 커서는 헤드의 위치와 회전을 사용 하는 보이지 않는 헤드 응시 벡터의 끝에 연결 되는 점입니다. 작업을 실행 하기 위해이 포인팅 커서는 공중 탭, 음성 명령, 지속 및 단추 누름과 같은 다양 한 커밋 입력과 쌍을 이룹니다. HoloLens 2에서 헤드-응시는 공기 탭과 far 광선 간의 상호 작용 충돌을 발생 시킬 수 있기 때문에 공중 탭이 아닌 커밋 입력에 가장 적합 합니다. <br>
:::row:::
    :::column:::
        ![헤드 응시 커서 손](images/head-gaze-cursor-hand.png)<br>
        **헤드-손 모양 제스처를 사용 하 여 커서 이동**<br>
    :::column-end:::
    :::column:::
        ![헤드 응시 커서 음성](images/head-gaze-cursor-voice.png)<br>
        **헤드-음성 명령으로 커서를 응시 합니다.**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a>커서 사용자 지정 권장 사항
커서 피드백 동작 및 모양을 사용자 지정 하려는 경우 다음 몇 가지 디자인 권장 사항을 참조 하세요.

### <a name="cursor-scale"></a>커서 배율
* 사용자가 쉽게 콘텐츠를 조작 하 고 볼 수 있도록 커서는 사용 가능한 대상 보다 크지 않아야 합니다.
* 사용자가 만드는 환경에 따라 사용자가 볼 때 커서의 크기를 조정 하는 것도 중요 한 고려 사항입니다. 예를 들어 사용자가 더 이상 사용자의 경험을 볼 수 없게 되 면 커서는 너무 작아서 손실 될 수 있습니다.
* 커서의 크기를 조정 하는 경우 유기적 느낌을 제공 하기 위해 크기가 조정 될 때 소프트 애니메이션을 적용 하는 것이 좋습니다.
* 방해 하지 않는지 콘텐츠를 방지 합니다. Holograms는 환경을 기억 하 고 커서를 사용 하지 않아야 합니다.

### <a name="directionless-cursor-shape"></a>Directionless cursor 셰이프
* 하나의 오른쪽 커서 셰이프도 있지만 torus와 같은 directionless 셰이프를 사용 하는 것이 좋습니다. 특정 방향 (예: 기존 화살표 커서)을 가리키는 커서는 사용자에 게 항상 표시 되는 것으로 혼동 될 수 있습니다.
* 이에 대 한 예외는 커서를 사용 하 여 사용자에 게 상호 작용 명령을 전달 하는 경우입니다. 예를 들어 혼합 현실 OS에서 holograms 크기를 조정 하는 경우 커서는 손을 이동 하 여 홀로그램 크기를 조정 하는 방법을 사용자에 게 지시 하는 화살표를 일시적으로 포함 합니다.

### <a name="look-and-feel"></a>모양 및 느낌
* 도넛형 또는 torus 모양의 커서는 많은 응용 프로그램에 대해 작동 합니다.
* 사용자가 만드는 환경을 가장 잘 나타내는 색과 모양을 선택 합니다.
* 커서는 특히 [색 구분](hologram-stability.md#color-separation)이 쉽습니다.
* 분산 된 불투명도가 있는 작은 커서는 시각적 계층 구조를 dominating 않고 정보를 유지 합니다.
* 콘텐츠를 액세스가 방해 하 고 작업에서 방해 수 있으므로 커서 뒤에 그림자 또는 하이라이트를 사용 하는 것이 cognizant 합니다.
* 커서는 앱의 표면에 맞추고 hug 합니다. 이렇게 하면 시스템에서 원하는 위치를 볼 수 있을 뿐만 아니라 시스템에서 주변을 인식 하 게 됩니다. 예를 들어 혼합 현실 OS에서는 사용자가 홀로그램에서 직접 확인 하지 않는 경우에도 커서를 사용자 세계의 표면에 맞추고 전 세계의 인식 느낌을 만듭니다.
* 자기적으로가 근접 한 영역 내에 있을 때 대화형 요소로 커서를 잠그면 사용자가 선택 작업을 수행할 때 해당 요소와 상호 작용 하는 확신을 향상 시킬 수 있습니다.

### <a name="visual-cues"></a>시각적 신호
* 환경을 단일 홀로그램에 집중 하는 경우 해당 홀로그램에서 볼 때 커서는 홀로그램 및 변경 셰이프만 정렬 하 고 hug 합니다. 이는 사용자에 게 홀로그램 작업을 수행할 수 있고 사용자가이를 조작할 수 있음을 알릴 수 있습니다.
* 응용 프로그램에서 공간 매핑을 사용 하는 경우 커서가 표시 하는 모든 표면에 커서를 맞추고 hug 수 있습니다. 그러면 HoloLens를 사용 하는 사용자에 게 피드백을 제공 하 고 응용 프로그램에서 해당 공간을 볼 수 있습니다. 이를 통해 강화는 진정한 세계 이며 실제 및 가상 간의 차이를 쉽게 파악할 수 있습니다.
* 보기에 holograms 또는 표면이 없을 때 커서에서 수행 해야 하는 작업을 파악 합니다. 사용자 앞의 미리 정해진 거리에 배치 하는 것은 한 가지 옵션입니다.

### <a name="possible-actions"></a>가능한 작업
* 커서는 여러 아이콘으로 표시 되어 홀로그램에서 크기 조정 또는 회전과 같이 수행할 수 있는 작업을 전달할 수 있습니다.
* 사용자에 게 무언가가 있음을 의미 하는 경우에만 커서에 추가 정보를 추가 합니다. 그렇지 않으면 사용자가 상태를 변경 하거나 커서를 혼동 하지 않을 수 있습니다.

### <a name="input-state"></a>입력 상태
* 커서를 사용 하 여 사용자의 입력 상태나 의도를 표시할 수 있습니다. 예를 들어 사용자에 게 시스템 상태를 확인 하 고 응용 프로그램에서 사용자에 게 조치를 취할 준비가 되었음을 알리는 아이콘을 표시할 수 있습니다.
* 또한 일시적 색을 통해 시스템에서 음성 명령을 파일과 사용자를 표시 하는 데 커서를 사용할 수 있습니다.

* 다음 커서 상태를 다양 한 방법으로 구현할 수 있습니다. 상태 시스템 처럼 커서를 모델링 하 여 이러한 다양 한 상태를 구현할 수 있습니다. 예를 들어 다음과 같은 가치를 제공해야 합니다.
    * 유휴 상태는 기본 커서를 표시 하는 위치입니다.
    * 준비 상태는 준비 위치에서 사용자의 손을 검색 한 경우입니다.
    * 상호 작용 상태는 사용자가 특정 상호 작용을 수행 하는 경우입니다.
    * 가능한 작업 상태 또는 가리키기 상태는 홀로그램에서 수행할 수 있는 가능한 작업을 전달 하는 경우입니다.

다양 한 상태가 검색 되 면 다양 한 아트 자산을 표시할 수 있도록 이러한 상태를 스킨 가능 방식으로 구현할 수도 있습니다.

<br>

---


## <a name="going-cursor-free"></a>"커서를 사용 하지 않음"으로 이동
집중 교육의 의미는 환경의 주요 구성 요소이 고 (응시 및 제스처를 통해)에는 상당한 정밀도가 필요 하지 않은 경우 커서를 사용 하지 않고 디자인 하는 것이 좋습니다. 시스템은 시스템에 대 한 지속적인 피드백을 사용자에 게 제공 하 고 사용자가 자신의 의도를 시스템에 안전 하 게 전달할 수 있도록 하 여 커서가 일반적으로 충족 하는 요구 사항을 충족 해야 합니다. 이는 다른 눈에 띄는 상태를 변경 하 여 달성할 수 있습니다.

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 용 MRTK (Mixed Reality Toolkit)의 커서
기본적으로 [Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity) 는 셸 시스템 커서와 동일한 시각적 상태를 가진 커서 Prefab ([defaultcursor. prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors))를 제공 합니다. MRTK의 입력 프로필의 포인터 아래에 할당됩니다. 사용자 환경에 맞게이 커서를 바꾸거나 사용자 지정할 수 있습니다. 아이 추적 입력 환경에서 MRTK는 혼란을 최소화 하기 위해 미묘한 시각적 개체를 포함 하는 EyeGazeCursor 제공 합니다.

* [MRTK - 포인터 프로필](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [MRTK - 입력 시스템](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [MRTK - 포인터](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a>참고 항목
* [제스처](gaze-and-commit.md#composite-gestures)
* [헤드 게이즈 및 커밋](gaze-and-commit.md)
