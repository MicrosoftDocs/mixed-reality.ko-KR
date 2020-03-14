---
title: 응시 및 커밋
description: 눈길 또는 head 입력을 사용 하는 "응시 및 커밋" 입력 모델의 일반 개요입니다.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 혼합 현실, 응시, 응시 대상 지정, 상호 작용, 디자인, 눈 추적, head 추적
ms.openlocfilehash: df152f6a3a6e4ae2d6c32a0c56fbb615bcfa7aa8
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375850"
---
# <a name="gaze-and-commit"></a>응시 및 커밋

_응시 및 commit_ 은 마우스를 사용 하 여 컴퓨터와 상호 작용 하는 방법과 밀접 하 게 관련 된 기본적인 입력 모델입니다. _& 클릭_합니다.
이 페이지에서는 두 가지 유형의 응시 입력 (헤드 및 눈에 해당)과 다양 한 커밋 작업 유형을 소개 합니다. 
_응시 및 commit_ 은 간접 조작이 있는 far 입력 모델로 간주 됩니다.
즉, 도달 하지 않은 holographic 콘텐츠와 상호 작용 하는 데 가장 적합 합니다.

혼합 현실 헤드셋은 사용자 헤드의 위치와 방향을 사용 하 여 헤드 벡터를 결정할 수 있습니다. 사용자의 눈 사이에서 앞을 똑바로 가리키는 레이저라고 생각할 수 있습니다. 이것은 사용자가 보고 있는 위치에 대한 대략적인 근사치입니다. 응용 프로그램은 가상 또는 실제 개체와이 광선을 교차 하 고 해당 위치에 커서를 그려 사용자에 게 현재 대상으로 지정 된 항목을 알 수 있도록 합니다.

헤드 응시 외에도 HoloLens 2와 같은 일부 혼합 현실 헤드셋은 눈에 잘 맞는 벡터를 생성 하는 눈 추적 시스템을 포함 합니다. 이를 통해 사용자가 보는 위치를 세밀하게 측정할 수 있습니다. 두 경우 모두, 응시는 사용자의 의도에 대 한 중요 한 신호를 나타냅니다. 시스템에서 사용자의 의도 된 작업을 해석 하 고 예측할 수 있으므로 사용자 만족도가 향상 되 고 성능이 향상 됩니다.

다음은 혼합 현실 개발자가 헤드 또는 눈에 잘 응시 할 수 있는 방법에 대 한 몇 가지 예제입니다.
* 앱은 장면의 holograms와 교차 하 여 사용자의 주의가 되는 위치를 확인할 수 있습니다 (눈에 띄게 더 정확 하 게).
* 앱은 사용자의 응시를 바탕으로 채널 제스처와 컨트롤러를 누르면 사용자가 원활 하 게 선택, 활성화, 잡기, 스크롤 또는 holograms과 상호 작용할 수 있습니다.
* 앱을 사용 하면 사용자가 holograms 표면에 해당 응시 광선과 공간 매핑 메시를 교차 하 여 실제 표면에 놓을 수 있습니다.
* 앱은 사용자가 중요 한 개체의 방향을 확인 *하지 않는* 경우를 알 수 있습니다. 그러면 응용 프로그램에서 시각적 개체와 오디오 신호를 제공 하 여 해당 개체를 가리킬 수 있습니다.

<br>


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
         <tr>
        <td>시선 응시 및 커밋</td>
        <td>❌ 사용할 수 없음</td>
        <td>✔️ 권장(세 번째 선택 - <a href="interaction-fundamentals.md">다른 옵션 보기</a>)</td>
        <td>❌ 사용할 수 없음</td>
    </tr>
</table>


## <a name="gaze"></a>응시

### <a name="eye--or-head-gaze"></a>눈 또는 헤드-응시?
"눈에 응시 하 고 커밋" 또는 "헤드-응시 및 커밋" 입력 모델을 사용 해야 하는지 여부와 관련 하 여 고려해 야 할 몇 가지 고려 사항이 있습니다. 몰입 형 헤드셋 또는 HoloLens 용으로 개발 하는 경우 (첫 번째 gen) 선택은 간단 합니다. 헤드-응시 및 커밋입니다. HoloLens 2 용으로 개발 하는 경우이를 선택 하는 것이 약간 더 어렵습니다. 이러한 이유로 각 항목에서 제공 하는 장점과 문제를 이해 하는 것이 중요 합니다.
아래 표에서 광범위 한 pro 및 con을 컴파일하여 헤드와 눈동자 대상 지정을 대조 합니다. 이것은 완료 된 것이 아니므로 여기에서 혼합 현실에서 눈에 잘 못 한 대상 지정에 대해 자세히 알아보는 것이 좋습니다.
* [Hololens의 눈동자 추적 2](eye-tracking.md): 몇 가지 개발자 지침을 포함 하 여 hololens 2에 대 한 새로운 눈 추적 기능을 소개 합니다. 
* [눈동자-응시 상호 작용](eye-gaze-interaction.md): 입력으로 눈동자 추적을 사용할 계획인 경우 디자인 고려 사항 및 권장 사항입니다.

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>눈동자-응시 대상 지정</strong></td>
        <td><strong>헤드-응시 대상 지정</strong></td>
    </tr>
    <tr>
        <td>빠르지!</td>
        <td>느리다는</td>
    </tr>
    <tr>
        <td>낮은 노력 (거의 모든 본문 이동 필요)</td>
        <td>Fatiguing 수 있습니다 (예: discomfort).</td>
    </tr>
    <tr>
        <td>에는 커서가 필요 하지 않지만 미묘한 피드백을 권장 합니다.</td>
        <td>커서를 표시 해야 함</td>
    </tr>
    <tr>
        <td>부드러운 눈 이동 없음 – 예: 그리기에 적합 하지 않음</td>
        <td>추가 제어 및 명시적</td>
    </tr>
    <tr>
        <td>매우 작은 대상 (예: 작은 단추 또는 weblinks)에 대해 어려움</td>
        <td>높고! 뛰어난 대체</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

사용자의 응시 [및 커밋 입력](gaze-and-commit-head.md) 모델에 대해 head-응시 또는 눈동자를 사용 하는 [것은 각각](gaze-and-commit-eyes.md) 다른 디자인 제약 조건 집합과 함께 제공 됩니다 .이 제약 조건은 다른 디자인 제약 조건으로 제공 됩니다

<br>

---

### <a name="cursor"></a>Cursor

:::row:::
    :::column:::
        헤드 응시의 경우 대부분의 앱은 [커서](cursors.md) (또는 기타 청각/시각적 표시)를 사용 하 여 사용자가 상호 작용 하려는 항목을 사용자에 게 확실 하 게 제공 해야 합니다. 일반적으로 헤드 응시 광선이 먼저 개체와 교차 하는 위치에이 커서를 배치 합니다 .이는 홀로그램 또는 실제 표면이 될 수 있습니다.<br>
        <br>
        아이 응시의 경우 일반적으로 사용자에 게 혼란을 줄 수 있으므로 커서를 표시 *하지 않는* 것이 좋습니다. 대신 시각적 대상을 미세 하 게 강조 표시 하거나 매우 희미 한 눈 커서를 사용 하 여 사용자가 상호 작용할 정보를 제공 합니다. 자세한 내용은 HoloLens 2의 [눈동자 기반 입력에 대 한 디자인 지침](eye-tracking.md) 을 확인 하세요.
    :::column-end:::
        :::column:::
       응시를 표시 하는 예제 시각적 커서 ![](images/cursor.jpg)<br>
       *이미지: 응시를 표시 하는 예제 시각적 커서*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>커밋
대상 _에 참여 하는_ 다양 한 방법에 대해 이야기 한 후에는 _응시 및 commit_의 _커밋_ 부분에 대해 좀 더 자세히 살펴보겠습니다.
개체 또는 UI 요소를 대상으로 지정한 후에는 사용자가 보조 입력을 사용 하 여 상호 작용 하거나 클릭할 수 있습니다. 이를 입력 모델의 커밋 단계 라고 합니다. 

지원되는 커밋 메서드는 다음과 같습니다.
- 공기 탭 제스처 (즉, 사용자의 앞에 손을 올리고 인덱스 손가락 및 엄지 단추를 통합)
- _"Select"_ 또는 대상 음성 명령 중 하나를 말합니다.
- [HoloLens Clicker](hardware-accessories.md#hololens-clicker) 에서 단일 단추를 누릅니다.
- Xbox 게임 패드에서 ' A ' 단추를 누릅니다.
- Xbox 적응 컨트롤러에서 ' A ' 단추를 누릅니다.

### <a name="gaze-and-air-tap-gesture"></a>응시 및 air 탭 제스처
에어 탭은 손을 똑바로 세워서 탭하는 동작입니다. 공중 탭을 수행 하려면 인덱스 손가락을 준비 위치로 올리고 엄지 단추를 누른 후 인덱스 손가락을 다시 릴리스로 올립니다. HoloLens (첫 번째 gen)에서 air 탭은 가장 일반적인 보조 입력입니다.


:::row:::
    :::column:::
       준비 위치에 손가락을 ![](images/readyandpress-ready.jpg)<br>
       **준비 위치의 핑거**<br>
    :::column-end:::
    :::column:::
       손가락 아래로 ![눌러 탭 하거나 클릭](images/readyandpress-press.jpg)<br>
        **손가락 아래로를 눌러 탭 하거나 클릭 합니다.**<br>
    :::column-end:::
:::row-end:::


항공기 탭은 HoloLens 2 에서도 사용할 수 있습니다. 원래 버전에서 완화 되었습니다. 이제는 손을 수직이 고 그대로 유지 되는 동안 거의 모든 유형의 pinches이 지원 됩니다. 따라서 사용자가 동작을 배우고 수행하기 훨씬 쉽습니다. 새 공중 탭은 동일한 API를 통해 이전 항목을 대체 하므로 HoloLens 2를 다시 컴파일한 후 기존 응용 프로그램에서 자동으로 새 동작을 갖게 됩니다.

<br>

---

### <a name="gaze-and-select-voice-command"></a>응시 및 "선택" 음성 명령
음성 명령은 혼합 현실에서 기본 상호 작용 방법 중 하나입니다. 시스템을 제어 하는 매우 강력한 수동 메커니즘을 제공 합니다. 음성 상호 작용 모델에는 다음과 같은 다양 한 유형이 있습니다.

- 클릭 actuation를 수행 하거나 보조 입력으로 커밋하는 일반 "Select" 명령입니다.
- 개체 명령 (예: "Close" 또는 "더 크게 설정")은 작업을 수행 하 고 보조 입력으로 작업을 커밋합니다.
- 전역 명령 (예: "시작으로 이동")은 대상이 필요 하지 않습니다.
- 대화 사용자 인터페이스 또는 Cortana와 같은 엔터티는 AI 자연어 기능을 포함 합니다.
- 사용자 지정 음성 명령

사용 가능한 음성 명령의 포괄적인 목록과 사용 방법에 대 한 자세한 내용을 보려면 [음성 명령](voice-design.md) 지침을 확인 하세요.

<br>

---


### <a name="gaze-and-hololens-clicker"></a>응시 및 HoloLens Clicker

:::row:::
    :::column:::
        HoloLens Clicker는 HoloLens 용으로 특별히 구축 된 첫 번째 주변 장치입니다. HoloLens (첫 번째 gen) 개발 버전에 포함 되어 있습니다. HoloLens Clicker를 사용 하면 사용자가 최소한의 손 동작을 클릭 하 고 보조 입력으로 커밋할 수 있습니다. HoloLens Clicker는 Bluetooth 저 에너지 (BTLE)를 사용 하 여 HoloLens (첫 번째 gen) 또는 HoloLens 2에 연결 합니다.<br>
        <br>
        [장치를 페어링 하는 방법에 대 한 자세한 내용 및 지침](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *이미지: HoloLens Clicker*
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>응시 및 Xbox 무선 컨트롤러

:::row:::
    :::column:::
        Xbox 무선 컨트롤러는 ' A ' 단추를 사용 하 여 클릭 actuation를 보조 입력으로 수행 합니다. 장치는 시스템을 탐색 하 고 제어 하는 데 도움이 되는 기본 작업 집합에 매핑됩니다. 컨트롤러를 사용자 지정 하려면 Xbox 액세서리 응용 프로그램을 사용 하 여 Xbox 무선 컨트롤러를 구성 합니다.<br>
        <br>
        [Xbox 컨트롤러와 PC를 페어링 하는 방법](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *이미지: Xbox 무선 컨트롤러*
    :::column-end:::
        :::column:::
       ![Xbox 무선 컨트롤러](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>응시 및 Xbox 적응 컨트롤러
주로 모바일 기능이 제한 된 게이머의 요구 사항을 충족 하기 위해 설계 된 Xbox 적응 컨트롤러는 혼합 현실에 더 쉽게 액세스할 수 있도록 지 원하는 장치에 대 한 통합 허브입니다.

Xbox 적응 컨트롤러는 ' A ' 단추를 사용 하 여 클릭 actuation를 보조 입력으로 수행 합니다. 장치는 시스템을 탐색 하 고 제어 하는 데 도움이 되는 기본 작업 집합에 매핑됩니다. 컨트롤러를 사용자 지정 하려면 Xbox 액세서리 응용 프로그램을 사용 하 여 Xbox 적응 컨트롤러를 구성 합니다.

![Xbox 적응형 컨트롤러](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox 적응형 컨트롤러*

스위치, 단추, 탈것, 조이스틱 등의 외부 장치를 연결 하 여 고유한 사용자 지정 컨트롤러 환경을 만듭니다. 단추, 엄지 스틱 및 트리거 입력은 3.5 mm 잭 및 USB 포트를 통해 연결 된 보조 장치를 사용 하 여 제어 됩니다.

![Xbox 적응형 컨트롤러 포트](images/xbox-adaptive-controller-ports.jpg)<br>
*Xbox 적응형 컨트롤러 포트*

[디바이스 페어링 지침](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Xbox 사이트의 더 많은 정보</a>

<br>

---

## <a name="composite-gestures"></a>복합 제스처

### <a name="air-tap"></a>에어 탭
아래에 있는 다른 제스처 뿐만 아니라 공기 탭 제스처는 특정 탭에만 반응 합니다. 메뉴 또는와 같은 다른 탭을 검색 하려면 응용 프로그램에서 위의 두 키 구성 요소 제스처 섹션에 설명 된 하위 수준 상호 작용을 직접 사용 해야 합니다.

### <a name="tap-and-hold"></a>길게 누르기
홀드(hold)는 에어 탭의 아래쪽 손가락 위치를 유지하는 것입니다. 공기 탭 및 유지의 조합을 사용 하면 개체를 활성화 하는 대신 개체를 선택 하거나 상황에 맞는 메뉴를 표시 하는 것과 같이 개체를 선택 하는 것과 같이 arm 이동과 결합 하 여 복잡 한 "클릭 및 끌기" 상호 작용을 수행할 수 있습니다.
단, 이러한 제스처를 디자인할 때는 주의가 필요합니다. 확장된 동작을 하는 동안 사용자가 손의 자세를 푸는 경향이 있기 때문입니다.

### <a name="manipulation"></a>조작
사용자의 손을 이동 하 여 홀로그램에서 1:1에 반응할 수 있도록 하려면 조작 제스처를 사용 하 여 홀로그램을 이동, 크기 조정 또는 회전할 수 있습니다. 이러한 1:1 움직임을 사용하는 한 가지 방식은 실제로 선을 긋거나 그릴 수 있도록 하는 것입니다.
조작 제스처에 대한 초기 타기팅은 응시 또는 포인팅을 통해 수행해야 합니다. 탭 하 여 보류가 시작 되 면 개체 조작을 직접 이동 하 여 조작 하는 동안 사용자가 쉽게 볼 수 있도록 합니다.

### <a name="navigation"></a>탐색
탐색 제스처는 가상 조이스틱처럼 작동하며 방사형 메뉴와 같은 UI 위젯을 탐색하는 데 사용할 수 있습니다. 길게 눌러서 제스처를 시작한 후 초기에 누른 부분을 중심으로 정규화된 3D 큐브 안에서 손을 움직입니다. X, Y, Z 축을 따라 -1에서 1로 손을 움직일 수 있고, 시작점은 0입니다.
탐색은 속도 기반 연속 스크롤 또는 확대/축소 제스처를 빌드하는 데 사용할 수 있으며, 마우스 가운데 단추를 클릭한 다음, 마우스를 위아래로 움직여서 2D UI를 스크롤하는 것과 유사합니다.

레일을 사용한 탐색은 특정 임계값에 도달할 때까지 특정 축의 움직임을 인식 하는 기능을 나타냅니다. 이는 응용 프로그램이 X, Y 축의 탐색 제스처를 인식 하도록 구성 되어 있지만 레일을 사용 하 여 X 축도 지정 하는 경우와 같이 개발자가 응용 프로그램에서 둘 이상의 축으로 이동 하는 경우에만 유용 합니다. 이 경우 Y 축에서 직접 이동이 발생 하는 경우 시스템은 x 축에서 허수 레일 (가이드) 내에 유지 되는 동안 X 축에서 직접 이동 하는 것을 인식 합니다.

2D 앱에서는 사용자가 세로 탐색 제스처를 사용하여 앱 내에서 스크롤, 확대/축소 또는 끌기를 수행할 수 있습니다. 그러면 앱에 가상 손가락 터치가 삽입되어 같은 유형의 터치 제스처가 시뮬레이션됩니다. 사용자는 단추를 선택 하거나 ' < 스크롤/끌기/확대/축소 > 도구 '를 사용 하 여 응용 프로그램 위에 있는 막대의 도구 사이를 전환 하 여 수행할 작업을 선택할 수 있습니다.

[복합 제스처에 대한 추가 정보](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>제스처 인식기

제스처 인식 기능을 사용 하는 경우의 한 가지 장점 중 하나는 현재 대상 홀로그램에서 수락할 수 있는 제스처에 대해서만 제스처 인식기를 구성할 수 있다는 것입니다. 플랫폼은 지원 되는 특정 제스처를 구분 하기 위해 필요에 따라 명확성을 갖습니다. 이러한 방식으로, 살짝 누르기를 지 원하는 홀로그램은 press와 release 사이에 모든 시간을 허용할 수 있는 반면, 탭 및 유지를 모두 지 원하는 홀로그램은 대기 시간 임계값 후에 탭을 보류 중으로 승격할 수 있습니다.

## <a name="hand-recognition"></a>손 인식
HoloLens는 디바이스에 보이는 한쪽 또는 양쪽 손의 위치를 추적하여 손 제스처를 인식합니다. HoloLens는 손이 준비 상태(집게손가락을 올리고 손등을 마주보고 있는 상태)이거나 눌린 상태(집게손가락을 내리고 손등을 마주보고 있는 상태)일 때 손을 봅니다. 손이 다른 포즈에 있는 경우 HoloLens는이를 무시 합니다.
HoloLens가 검색 하는 각 손으로는 방향 및 눌린 상태 없이 해당 위치에 액세스할 수 있습니다. 손이 제스처 프레임의 가장자리에 가까워지면, 방향 벡터가 제공됩니다. 이것을 사용자에게 표시하면, HoloLens에게 보이는 위치로 손을 다시 이동하려면 손을 어떻게 움직여야 하는지를 사용자가 알 수 있습니다.

## <a name="gesture-frame"></a>제스처 프레임
HoloLens의 제스처의 경우이 손을 제스처 프레임 내에 있어야 합니다. 제스처는 제스처-감지 카메라에서 적절 하 게 볼 수 있는 범위에서 접근 waist와 사이에 있어야 합니다. 사용자는 작업 성공 및 자신에 게 편안 하 게 사용할 수 있도록이 영역에 대 한 교육을 받아야 합니다. 대부분의 사용자는 처음에는 HoloLens를 통해 제스처 프레임이 보기 내에 있어야 하 고 상호 작용 하기 위해 편안 하 게 유지 하는 것으로 가정 합니다. HoloLens Clicker를 사용 하는 경우에는 손을 제스처 프레임 안에 포함 하지 않아도 됩니다.

특히 연속 제스처의 경우 holographic 개체를 이동 하는 경우 중간 제스처를 사용 하 고 의도 하지 않은 결과를 잃지 못하도록 제스처 프레임 외부에서 손을 이동할 위험이 있습니다.

다음 세 가지 사항을 고려해야 합니다.

- 제스처 프레임의 존재 및 근사치 범위에 대 한 사용자 교육입니다. HoloLens를 설정 하는 동안이를 배울 수 있습니다.

- 응용 프로그램 내의 제스처 프레임 경계에 도달 하거나 해당 제스처가 원치 않는 결과로 이어질 수 있는 수준까지 사용자에 게 알립니다. Research는 이러한 알림 시스템의 주요 품질을 보여 줍니다. HoloLens shell은 경계가 교차 하는 방향을 나타내는 중앙 커서에 이러한 유형의 알림 (시각적 개체)에 대 한 좋은 예를 제공 합니다.

- 제스처 프레임 경계를 벗어난 결과는 최소화되어야 합니다. 일반적으로이는 제스처의 결과가 경계에서 중지 되 고 반전 되지 않음을 의미 합니다. 예를 들어 사용자가 실내에서 일부 holographic 개체를 이동 하는 경우 제스처 프레임이 위반 되 면 이동이 중지 되 고 시작 지점으로 반환 되지 않습니다. 사용자에 게 몇 가지 문제가 발생할 수 있지만, 경계를 보다 신속 하 게 이해 하 고 매번 원하는 작업을 다시 시작 하지 않아도 됩니다.



## <a name="see-also"></a>참고 항목
* [시선 기반 상호 작용](eye-gaze-interaction.md)
* [HoloLens 2의 시선 추적](eye-tracking.md)
* [응시 및 유지](gaze-and-dwell.md)
* [손 - 직접 조작](direct-manipulation.md)
* [손 - 제스처](gaze-and-commit.md#composite-gestures)
* [손 - 가리키기 및 커밋](point-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [음성 입력 ](voice-input.md)

