---
title: 응시 및 지속
description: (눈/헤드) 응시 및 지속 입력 모델의 일반적인 개요
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 혼합 현실, 응시, 지속, 상호 작용, 디자인, 눈 추적, head 추적
ms.openlocfilehash: d87406d0b2695cd86c40f27cb132af54ed525b25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435360"
---
# <a name="gaze-and-dwell"></a>응시 및 지속

손에 도구와 파트가 있으면 제스처가 어렵거나 불가능할 수 있습니다. 예를 들어 과도 하 게 큰 조건에서 음성 명령은 특정 컨텍스트에서 안정적이 아닐 수도 있습니다. 응시 및 유지는 HoloLens에서 실습 작업을 수행할 수 있는 친숙 하 고 간편한 마스터 메커니즘을 제공 합니다. 또한 응시 및 유지는 운영 환경에서 노이즈 간섭 또는 대기 제약 조건과 무관 한 좋은 대체 방법입니다.
여기서는 두 가지 변형 _,_ 즉 [헤드-응시 및](gaze-and-dwell-head.md) 유지와 [눈에 잘](gaze-and-dwell-eyes.md)해 서 유지를 구분 합니다.

## <a name="scenarios"></a>시나리오

사용자가 다른 작업을 사용 중이 고, 환경 또는 소셜 제약 조건으로 인해 음성이 100% 안정적이 지 않거나 사용 가능 하지 않은 시나리오에서 뛰어나지만을 응시 하 고 유지 합니다. HoloLens를 착용하고 자동차 엔진을 수리하는 동안 참조 정보를 오버레이하는 경우가 좋은 예입니다. 엔진 칸에 기대고 있는 몸을 지탱하거나 도구를 다루느라 손을 사용할 수 없습니다. 차고 공간에서는 연장이 계속 윙윙거리면서 소리를 내기 때문에 시끄러워서 음성 명령을 실행하기 어렵습니다. 응시 및 유지를 사용 하면 HoloLens를 사용 하는 사용자가 워크플로를 중단 하지 않고 자신에 게 해당 참조 자료를 쉽게 탐색할 수 있습니다. 

## <a name="device-support"></a>장치 지원

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>입력 모델</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>헤드 게이즈(head-gaze) 및 드웰(dwell)</td>
        <td>✔️ 권장</td>
        <td>✔️ 권장</td>
        <td>✔️ 권장</td>
    </tr>
     <tr>
        <td>눈에 응시 및 지속</td>
        <td>❌ 사용할 수 없음</td>
        <td>✔️ 권장</td>
        <td>❌ 사용할 수 없음</td>
    </tr>
</table>


<br>

---
 
 ## <a name="see-also"></a>참고 항목
* [눈에 잘 맞는 상호 작용](eye-gaze-interaction.md)
* [HoloLens의 눈동자 추적 2](eye-tracking.md)
* [응시 및 커밋](gaze-and-commit.md)
* [직접 조작](direct-manipulation.md)
* [손 제스처](gaze-and-commit.md#composite-gestures)
* [손 지점 및 커밋](point-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [음성 입력 ](voice-input.md)
