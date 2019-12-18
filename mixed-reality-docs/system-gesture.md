---
title: 시스템 제스처
description: 시작 메뉴를 호출 하는 시스템 제스처입니다.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: 혼합 현실, 제스처, 상호 작용, 디자인
ms.openlocfilehash: 9cfee1104cb9b8135dae51bea73850062fadd25c
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182003"
---
# <a name="system-gesture"></a>시스템 제스처

시스템 제스처는 시작 메뉴를 호출 하는 데 사용 되는 손 제스처입니다. 이는 키보드에서 Windows 키를 누르거나 Xbox 컨트롤러의 Xbox 단추를 누르거나 몰입 형 헤드셋 동작 컨트롤러의 Windows 단추를 누르는 것과 같습니다. 상호 작용을 디자인할 때 충돌을 방지 하기 위해 각 혼합 현실 장치에서 시스템용으로 예약 된 제스처를 이해 하는 것이 중요 합니다.

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
        <td>Bloom</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>손목 단추</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>아이 응시 및 야자수</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Bloom
HoloLens (첫 번째 gen)에서 시작 메뉴를 표시 하기 위해 꽃 벚꽃를 모방 기호화 된 제스처로 "블 룸"를 디자인 했습니다. 상호 작용 하 고, 쉽게 수행 하 고, 신속 하 게 회수할 수 있는 특수 한 방법입니다. HoloLens (첫 번째 gen)에서 블 룸 제스처를 수행 하려면 야자나무를 함께 사용 하 여 손을 놓고 손가락을 확산 시켜 손을 여세요.

:::row:::
    :::column:::
        ![블 룸 close](images/bloom-close.png)<br>
        **1 단계: 쉽게 함께 팜 강화**<br>
    :::column-end:::
    :::column:::
        ![블 룸 open](images/bloom-open.png)<br>
        **2 단계: 간편 하 게 확산 된 팜**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>시작 제스처
HoloLens 2에서 블 룸 제스처는 추가 교육을 필요로 하지 않는 더 많은 instinctual 상호 작용을 허용 하는 가상 손목 단추로 대체 되었습니다. 사용자가 손목 단추를 표시 하 여 쉽게 접근 하 고 다른 손으로 누를 수 있습니다.

:::row:::
    :::column:::
        ![손목 단추 준비](images/wrist-button-ready.png)<br>
        **1 단계: 손목 단추를 표시 합니다.**<br>
    :::column-end:::
    :::column:::
        ![손목 단추 누르기](images/wrist-button-press.png)<br>
        **2 단계: 손목 단추 누르기**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a>단방향 시작 제스처

> [!IMPORTANT]
> 한 번의 시작 제스처를 사용 하려면 다음을 수행 합니다.
>
> 1. 2019 년 11 월 업데이트 (빌드 18363.1039) 이상으로 업데이트 해야 합니다.
> 1. 눈동자 추적이 제대로 작동 하도록 장치에서 눈동자를 보정 해야 합니다. 표시 될 때 시작 아이콘 주위에 orbiting 점이 표시 되지 않는 경우 눈은 장치에서 보정 되지 않습니다.

또한 한 손으로만 시작 제스처를 수행할 수 있습니다. 이 작업을 수행 하려면 팜 연결을 잡고 내부 손목 **시작 아이콘** 을 확인 합니다. **아이콘을 눈에 유지 하면서**엄지 단추와 인덱스 손가락을 함께 손가락으로 합니다.<br>
:::row:::
    :::column:::
        ![손목 단추 준비](images/wrist-button-ready.png)<br>
        **1 단계: 손목 단추를 표시 합니다.**<br>
    :::column-end:::
    :::column:::
        ![손목 단추를 손가락으로](images/wrist-button-pinch.png)<br>
        **2 단계: 단추를 누른 후 손가락으로 이동**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>참고 항목

* [Instinctual 상호 작용](interaction-fundamentals.md)
* [눈 응시](eye-tracking.md)
* [음성 입력 ](voice-input.md)
