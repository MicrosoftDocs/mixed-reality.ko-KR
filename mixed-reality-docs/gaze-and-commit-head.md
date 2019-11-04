---
title: 헤드 게이즈(head-gaze) 및 커밋
description: 헤드 게이즈(head-gaze) 및 커밋 입력 모델 개요
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: 혼합 현실, 응시, 응시 타기팅, 상호 작용, 디자인
ms.openlocfilehash: 5fef778dde6852222e098aeb1cbb41fe04e0b744
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441098"
---
# <a name="head-gaze-and-commit"></a>헤드 게이즈(head-gaze) 및 커밋
_헤드-응시 및 커밋은_ 전방의 방향 (head 방향)으로 개체를 대상으로 지정 하 고, 손 모양 제스처와 같은 보조 입력으로 작업을 수행 하는 [응시 및 커밋](gaze-and-commit.md) 입력 모델의 특별 한 경우입니다. 또는 음성 명령 "선택"을 탭 합니다. 

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
        <td>헤드 게이즈(head-gaze) 및 커밋</td>
        <td>✔️ 권장</td>
        <td>✔️ 권장(세 번째 선택 - <a href="interaction-fundamentals.md">다른 옵션 보기</a>)</td>
        <td>➕ 대체 옵션</td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a>대상 크기 조정 및 피드백
헤드 응시 벡터는 세밀 하 게 대상 지정에 사용할 수 있도록 반복적으로 표시 되었지만, 일반적으로 더 큰 대상을 확보 하는 데 가장 적합 합니다. 최소 대상 크기인 1 ~ 1.5도를 사용 하면 대부분의 시나리오에서 성공적인 사용자 작업을 수행할 수 있지만, 3도의 대상은 속도가 더 빨라질 수 있습니다. 사용자가 타기팅하는 크기는 3D 요소인 경우에도 사실상 2D 영역입니다. 즉, 어떤 투영을 사용하든 타기킹이 가능한 영역이어야 합니다. 요소가 "활성" (사용자가 대상으로 하는) 인 두드러진 몇 가지 큐를 제공 하는 것은 매우 유용 합니다. 여기에는 표시 되는 "가리키기" 효과, 오디오 하이라이트 또는 클릭 또는 요소와 커서의 처리가 같은 내용이 포함 될 수 있습니다.

![2m 거리에서 최적 대상 크기](images/gazetargeting-size-1000px.jpg)<br>
*2m 거리에서 최적 대상 크기*

<br>

![응시 대상 개체를 강조 표시한 예](images/gazetargeting-highlighting-940px.jpg)<br>
*응시 대상 개체를 강조 표시한 예*

## <a name="target-placement"></a>대상 배치
사용자는 종종 보기의 해당 필드에서 매우 높은 또는 매우 낮은 UI 요소를 찾을 수 없기 때문에 주 포커스 주위의 영역에서 대부분의 주의를 기울일 수 있습니다. 대부분의 대상을 눈 높이 주변의 적당한 구간에 두면 도움이 됩니다. 사용자는 상대적으로 작은 시각 영역에 집중한다는 일반적인 경향을 감안하여(시력이 집중되는 원뿔 영역은 10도 정도임), UI 요소를 개념적으로 관련된 정도만큼 그룹화하면 사용자가 영역에서 응시 시선을 옮길 때 항목 간의 관심 연결 동작을 활용할 수 있습니다. UI를 디자인할 때는 HoloLens와 몰입형 헤드셋의 시야가 크게 달라질 수 있다는 점을 감안해야 합니다.

![Galaxy Explorer에서 응시 타기팅하기 편리하게 그룹화된 UI 요소의 예](images/gazetargeting-grouping-1000px.jpg)<br>
*Galaxy Explorer에서 응시 타기팅하기 편리하게 그룹화된 UI 요소의 예*

## <a name="improving-targeting-behaviors"></a>타기팅 동작 개선
특정 항목을 대상으로 지정 하는 사용자 의도를 결정 (또는 매우 근접 하 게) 할 수 있는 경우 올바르게 대상으로 지정 된 것 처럼 상호 작용 시 거의 누락 된 시도를 허용 하는 것이 유용할 수 있습니다 다음은 혼합 현실 환경에서 통합할 수 있는 성공적인 몇 가지 방법입니다.

### <a name="head-gaze-stabilization-gravity-wells"></a>헤드 게이즈(head-gaze) 안정화("중력 우물")
이는 대부분의 시간 동안 설정 해야 합니다. 이 기술은 사용자가 사용할 수 있는 자연 스런 head 및 목 jitter을 보고 동작으로 인해 이동 하는 것이 좋습니다.

### <a name="closest-link-algorithms"></a>가장 가까운 링크 알고리즘
이 기법은 상호 작용이 희소한 영역에 적합합니다. 사용자가 상호 작용 하려고 했던 항목을 결정할 수 있을 확률이 높은 경우 특정 수준의 의도를 가정 하 여 대상 기능을 보완할 수 있습니다.

### <a name="backdating-and-postdating-actions"></a>배경 및 postdating 작업
이 메커니즘은 속도가 필요한 작업에 유용합니다. 사용자가 고속 대상 지정 및 활성화 연습을 통해 이동 하는 경우에는 몇 가지 의도를 가정 하 고, 사용자가 탭 하기 전후에 약간의 초점을 두고 (50 ms 이전/이후 rly 테스트).

### <a name="smoothing"></a>다듬기
이 메커니즘은 자연 스러운 헤드 이동 특성으로 인해 약간의 지터와 wobble 감소 하는 pathing 이동에 유용 합니다. Pathing 동작을 매끄럽게 하는 경우 시간이 지남에 따라 부드러운 이동의 크기와 거리를 매끄럽게 합니다.

### <a name="magnetism"></a>자성
이 메커니즘은 가장 가까운 링크 알고리즘의 보다 일반적인 버전으로 간주할 수 있습니다. 즉, 사용자가 대화형 레이아웃에 대 한 몇 가지 정보를 사용 하 여 대상에 대 한 정보를 사용 하는 것이 가능 하기 때문에 사용자의 접근 방식이 hitboxes 수 있습니다. 사용자 의도에 접근 합니다. 특히 작은 대상에 강력한 수 있습니다.

### <a name="focus-stickiness"></a>포커스 고착
포커스를 제공할 근처 대화형 요소를 결정 하는 경우 포커스 유지는 현재 포커스가 있는 요소에 대 한 바이어스를 제공 합니다. 이렇게 하면 자연 노이즈가 있는 두 요소 간의 중간점에서 부동 상태에 있는 경우 비정상적인 포커스 전환 동작을 줄일 수 있습니다.


## <a name="see-also"></a>참고 항목
* [눈에 잘 맞는 상호 작용](eye-gaze-interaction.md)
* [응시 및 유지](gaze-and-dwell.md)
* [직접 조작](direct-manipulation.md)
* [손 제스처](gaze-and-commit.md#composite-gestures)
* [손 지점 및 커밋](point-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [음성 입력 ](voice-input.md)



