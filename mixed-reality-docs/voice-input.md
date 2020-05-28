---
title: 음성 입력
description: 음성 입력은 HoloLens 및 Windows Mixed Reality 모던 헤드셋의 핵심 입력입니다. 음성은 명령, 받아쓰기, Cortana 등에 사용할 수 있습니다.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, 음성, cortana, 음성, 입력
ms.openlocfilehash: a5411c338a854660652cfc89aa2d48d85ee89778
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866923"
---
# <a name="voice-input"></a>음성 입력

![음성 입력](images/UX/UX_Hero_VoiceCommand.jpg)

음성은 HoloLens의 주요 입력 형태 중 하나입니다. 직접 [제스처](gaze-and-commit.md#composite-gestures)를 사용 하지 않고도 홀로그램을 직접 명령을 수행할 수 있습니다. 음성 입력은 의도를 전달하는 자연스러운 방법일 수 있습니다. 음성은 복잡 한 인터페이스를 트래버스하는 데 특히 유용 합니다 .이를 통해 사용자는 단일 명령을 사용 하 여 중첩 된 메뉴를 잘라낼 수 있습니다.

음성 입력은 다른 모든 _유니버설 Windows 앱_의 음성을 지 원하는 [동일한 엔진](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) 에 의해 구동 됩니다. HoloLens에서 음성 인식은 항상 설정에 구성 된 Windows 표시 언어로 작동 합니다. 

<br>

## <a name="voice-and-gaze"></a>음성 및 응시

음성 명령을 사용 하는 경우 (head 또는 눈) 응시는 일반적으로 커서 ("select")를 사용 하 여 대상 메커니즘으로 사용 되거나 원하는 응용 프로그램에 명령을 암시적으로 채널 합니다. 이 경우에는 모든 응시 커서를 표시 하는 데 필요 하지 않을 수 있습니다 _("참조)_. 물론 일부 음성 명령에는 "시작으로 이동" 또는 "안녕하세요 Cortana"와 같은 대상이 전혀 필요 하지 않습니다.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a>디바이스 지원

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
        <td>음성 입력</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (마이크 포함)</td>
    </tr>
</table>

## <a name="the-select-command"></a>"Select" 명령

**HoloLens(1세대)**

앱에 음성 지원을 특별히 추가 하지 않은 경우에도 사용자는 시스템 음성 명령 "select"를 통해 holograms을 활성화할 수 있습니다. 이는 HoloLens의 [공기 탭](gaze-and-commit.md#composite-gestures) , [hololens clicker](https://docs.microsoft.com/hololens/hololens1-clicker)의 선택 단추 누르기 또는 [Windows Mixed Reality 동작 컨트롤러](motion-controllers.md)에서 트리거 누르기와 동일 하 게 작동 합니다. 소리가 들리고 "선택"이 확인으로 표시 된 도구 설명이 표시 됩니다. "선택"은 낮은 파워 키워드 검색 알고리즘에서 사용 하도록 설정 되므로 사용자가 손을 사용 하더라도 배터리 수명에 영향을 최소화 하면서 언제 든 지 항상 사용할 수 있습니다.

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        HoloLens 2에서 "select" 음성 명령을 사용 하려면 먼저 응시 커서를 사용 하 여 포인터로 사용 해야 합니다. 이를 가져오는 명령은 쉽게 기억할 수 있습니다. 예를 들어 "선택" 합니다.<br><br>
        모드를 종료 하려면 마우스를 사용 하 여 손가락을 다시 사용 하거나 손가락으로 단추에 근접 하거나 시스템 제스처를 사용 하면 됩니다.<br>
        <br>
        *이미지: 선택 영역에 음성 명령을 사용 하려면 "선택"*
    :::column-end:::
        :::column:::
       ![사용자는 선택에 대해 음성 명령을 사용 하기 위해 "선택" 이라고 말할 수 있습니다.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a>안녕하세요. Cortana

또한 언제 든 지 Cortana를 표시 하는 "안녕하세요" Cortana를 사용할 수 있습니다. 사용자의 질문을 계속 하거나 명령을 제공 하기 위해 사용자가 표시 될 때까지 기다릴 필요가 없습니다. 예를 들어 "안녕하세요? 단일 문장으로 Cortana 및 수행할 수 있는 작업에 대 한 자세한 내용은 사용자에 게 문의 하세요. "안녕하세요?" 라고 표시 됩니다. 그리고 작업 및 제안 된 명령 목록을 가져옵니다. Cortana 앱에 이미 있는 경우 **다음을 클릭 하면 됩니다** . 동일한 메뉴를 끌어올 수 있는 아이콘입니다.

**HoloLens 관련 명령**
* "무엇을 할 수 있나요?"
* [시작 메뉴로](navigating-the-windows-mixed-reality-home.md#start-menu) 이동 하려면 [블 룸](system-gesture.md#bloom) 대신 "시작으로 이동"을 참조 하세요.
* "Launch <app> "
* " <app> 여기로 이동"
* "사진 찍기"
* "기록 시작"
* "기록 중지"
* "밝기 늘리기"
* "밝기 낮추기"
* "볼륨 증가"
* "볼륨 낮추기"
* "음소거" 또는 "음소거 해제"
* "장치 종료"
* "장치 다시 시작"
* "절전 모드로 전환"
* "시간 이란?"
* "얼마나 많은 배터리가 남아 있나요?"



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>"이 항목을 참조 하세요."<br>
        HoloLens에는 음성 입력에 대 한 "이를 확인 하는 것이 있습니다. 예를 들어 HoloLens (첫 번째 gen)에서 앱 창을 볼 때 사용자는 앱 바에 표시 되는 "조정" 명령을 사용 하 여 전 세계의 앱 위치를 조정할 수 있습니다.<br>
        <br>
        *이미지: 사용자가 앱 바에 표시 되는 "조정" 명령을 사용 하 여 앱의 위치를 조정할 수 있습니다.*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![앱 창이 나 홀로그램을 볼 때 사용자가 앱 바에 표시 되는 "조정" 명령을 사용 하 여 전 세계의 앱 위치를 조정할 수 있습니다.](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        앱이이 규칙을 준수 하는 경우 사용자는 시스템을 제어 하는 내용을 쉽게 파악할 수 있습니다. 이를 강화 하기 위해 HoloLens (첫 번째 gen)의 단추를 gazing 하는 동안 "음성 유지" 도구 설명이 표시 됩니다. 단추가 음성으로 사용 되는 경우 두 번째는 "음성 유지" 도구 설명이 표시 되 고이를 통해 "누르기"를 말하는 명령이 표시 됩니다. HoloLens 2에서 음성 도구 설명을 표시 하려면 "선택" 또는 "설명 가능한 내용" (이미지 참조)을 설명 하 여 음성 커서를 표시 합니다. <br>
        <br>
        *이미지: 단추 아래에 "표시 됩니다." 라고 표시 됩니다.*
    :::column-end:::
        :::column:::
       ![단추 아래에 표시 되는 것을 확인 하세요.](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a>빠른 홀로그램 조작을 위한 음성 명령

한 번에 조작 작업을 빠르게 수행 하기 위해 홀로그램에서 gazing 하는 동안 많은 음성 명령을 사용할 수 있습니다. 이러한 음성 명령은 응용 프로그램 창 뿐만 아니라 전 세계에 배치한 3D 개체에도 적용 됩니다.

**홀로그램 조작 명령**
* 얼굴 얼굴
* 크게 | 보강
* 짧은

HoloLens 2에서는 참조 하는 내용에 대 한 컨텍스트 정보를 암시적으로 제공 하는 눈에 잘 맞는 상호 작용을 만들 수도 있습니다. 예를 들어, 홀로그램을 확인 하 고 "배치" 라고 표시 한 다음 배치 하려는 위치를 확인 하 고 " _여기_ _에"를_표시할 수 있습니다.
또는 복잡 한 컴퓨터에서 holographic 파트를 살펴볼 수 있습니다. " _이_에 대 한 자세한 정보를 제공 합니다." 라고 표시 합니다.



## <a name="discovering-voice-commands"></a>음성 명령 검색

위의 빠른 조작을 위한 명령과 같은 일부 명령은 숨길 수 있습니다. 사용할 수 있는 명령에 대 한 자세한 내용은 개체를 응시 하 고 "무엇을 할 수 있나요?" 라고 표시 합니다. 가능한 명령 목록이 표시 됩니다. 헤드 응시 커서를 사용 하 여 앞의 각 단추에 대 한 음성 도구 설명을 볼 수도 있습니다. 

전체 목록을 원하는 경우 언제 든 지 "모든 명령 표시" 라고 합니다. 


## <a name="dictation"></a>받아쓰기

음성 받아쓰기는 [공기 탭](gaze-and-commit.md#composite-gestures)을 사용 하 여 입력 하는 대신 앱에 텍스트를 입력 하는 것이 더 효율적일 수 있습니다. 이렇게 하면 사용자에 대해 더 짧은 노력으로 입력 속도를 크게 높일 수 있습니다.

![음성 받아쓰기는 마이크 단추를 선택 하 여 시작 합니다.](images/micbuttonfordictation.png)<br>
*음성 받아쓰기는 키보드에서 마이크 단추를 선택 하 여 시작 합니다.*

Holographic 키보드가 활성화 될 때마다 입력 하는 대신 받아쓰기 모드로 전환할 수 있습니다. 텍스트 입력 상자의 측면에서 마이크를 선택 하 여 시작 합니다.


## <a name="adding-voice-commands-to-your-app"></a>앱에 음성 명령 추가

빌드하는 모든 환경에 음성 명령을 추가하는 것이 좋습니다. 음성은 강력하고 편리한 방식으로 시스템 및 앱을 제어할 수 있는 방법입니다. 사용자는 다양한 언어 및 악센트를 사용하기 때문에 음성 키워드를 적절히 선택하면 사용자의 명령이 명확하게 해석될 수 있습니다.

### <a name="best-practices"></a>모범 사례

다음은 매끄러운 음성 인식에 도움이 될 수 있는 몇 가지 사례입니다.
* **간결한 명령 사용** - 가능한 경우 두 개 이상의 음절로 이루어진 키워드를 선택합니다. 1음절 단어는 악센트가 다른 사람이 말할 경우 다른 모음 소리를 사용할 수 있습니다. 예: "비디오 재생"은 "현재 선택한 비디오 재생" 보다 좋습니다.
* **간단한 어휘 사용** -예: "show note"는 "show 카드" 보다 좋습니다.
* **비파괴적인 명령 사용** - 음성 명령으로 수행할 수 있는 모든 작업은 비파괴적이어야 하며, 사용자 근처에서 말하는 다른 사람이 실수로 명령을 트리거하는 경우 쉽게 실행 취소할 수 있어야 합니다.
* **유사하게 들리는 명령 사용 금지** - 매우 비슷하게 들리는 여러 음성 명령을 등록하지 않도록 합니다. 예: "자세히 표시" 및 "저장소 표시"는 매우 유사 하 게 표시 될 수 있습니다.
* **사용하지 않을 경우 앱 등록 취소** - 앱에서 특정 음성 명령이 유효한 상태가 아닐 경우에는 다른 명령과 혼동되지 않도록 등록을 취소하는 것이 좋습니다.
* **다른 악센트로 테스트** - 다른 악센트의 사용자와 앱을 테스트합니다.
* **음성 명령 일관성 유지** - "Go back"이라고 말할 경우 이전 페이지로 이동되면 애플리케이션에서 이 동작을 유지합니다.
* **시스템 명령 사용 방지** - 다음 음성 명령은 시스템용으로 예약되어 있습니다. 따라서 애플리케이션에서 사용하지 않아야 합니다.
   * "Hey Cortana"
   * "Select"
   * "시작으로 이동"

### <a name="advantages-of-voice-input"></a>음성 입력의 장점

음성 입력은 의도를 전달하는 자연스러운 방법입니다. 음성 **은 인터페이스 탐색** 에 특히 유용 합니다. 사용자는 인터페이스의 여러 단계를 쉽게 수행할 수 있습니다 (사용자가 웹 페이지를 볼 때 응용 프로그램에서 뒤로 단추를 누르는 대신 "뒤로 이동" 이라고 말할 수 있음). 이러한 시간 절약은 사용자의 경험에 대 한 강력한 **감정적 효과** 를 제공 하 고 작은 양의 슈퍼 능력을 제공 합니다. 팔에 무언가를 잔뜩 들고 있거나 **멀티태스킹** 중일 때도 음성을 사용하는 것이 편리한 입력 방법입니다. 키보드에 입력 하는 것이 어려운 장치에서 **음성 받아쓰기** 는 텍스트를 입력 하는 효율적인 대체 방법이 될 수 있습니다. 마지막으로, 응시 및 제스처에 대 한 **정확도 범위가** 제한 되는 경우 음성은 사용자의 의도를 명확 하 게 구분 하는 데 도움이 될 수 있습니다. 

**사용자에게 도움이 될 수 있는 음성 사용 방법**
* 시간 단축 - 보다 효율적으로 최종 목표에 도달할 수 있어야 합니다.
* 최소의 노력 - 보다 유연하고 편리하게 작업할 수 있도록 해야 합니다.
* 인지 부담 감소 - 직관적이며 배우고 기억하기 쉽습니다.
* 사회적으로 용인 가능 - 사회 규범을 벗어나지 않는 행동을 사용해야 합니다.
* 일상적임 - 음성이 습관적인 동작이 될 수 있습니다.

### <a name="challenges-for-voice-input"></a>음성 입력에 대 한 문제

음성 입력은 다양 한 응용 프로그램에 적합 하지만 몇 가지 과제가 직면 합니다. 음성 입력의 장점과 문제를 모두 이해 하면 앱 개발자가 음성 입력을 사용 하는 방법 및 시기를 보다 효율적으로 선택 하 고 사용자에 게 훌륭한 환경을 만들 수 있습니다.

**연속 입력 컨트롤에 대 한 음성 입력** 세밀 한 제어가 그 중 하나입니다. 예를 들어 사용자가 음악 앱에서 볼륨을 변경할 수 있습니다. 단지 "큰" 라고 말할 수 있지만 시스템에서 볼륨을 만드는 것이 얼마나 큰 지는 확실 하지 않습니다. 사용자는 "약간 더 크게 만들기" 라고 말할 수 있지만 "약간의"는 수량화 하기 어렵습니다. 음성으로 holograms을 이동 하거나 크기를 조정 하는 것은 비슷하게 어렵습니다. 

**음성 입력 검색의 안정성** 음성 입력 시스템은 더 효과적이 고 더 나은 반면 음성 명령을 잘못 듣고 해석 하는 경우도 있습니다.
핵심은 시스템이 수신 대기 하는 경우 사용자에 게 피드백을 제공 하 여 응용 프로그램에서이 문제를 해결 하는 것이 고, 사용자를 올바르게 이해 하기 위해 잠재적인 문제를 명확 하 게 이해 하기 위해 시스템이 이해 하는 것입니다.  

**공유 공간의 음성 입력** 음성은 다른 사용자와 공유 하는 공간에서 사회 공학적 허용 되지 않을 수 있습니다.
다음은 몇 가지 예입니다.
* 사용자가 다른 사용자의 방해를 원하지 않을 수 있습니다 (예: 자동 라이브러리나 공유 사무실).
* 사용자가 공개를 통해 자신에 게 표시 되지 않을 수 있습니다.
* 사용자가 암호를 포함 하 여 개인 또는 기밀 메시지를 수신 하는 불편을 느낄 수 있습니다.

**고유 하거나 알 수 없는 단어의 음성 입력** 음성 입력의 어려움은 사용자가 시스템에서 알 수 없는 단어 (예: 애칭, 특정은 어 단어 또는 약어)를 받아쓰게 하는 경우에도 제공 됩니다. 

**음성 명령 학습** 최종 목표는 시스템에서 자연스럽 게 자주 사용 되지만 앱이 미리 정의 된 특정 음성 명령을 계속 사용 하는 경우도 있습니다.
큰 음성 명령 집합과 관련 된 과제는 사용자를 오버 로드 하지 않고 사용자를 유지 하는 데 도움이 되는 방법을 설명 하는 방법입니다. 

<br>

---

### <a name="voice-feedback-states"></a>음성 피드백 상태

음성이 제대로 적용되면 사용자는 **말할 수 있는 사항**을 이해하고 시스템이 **올바르게 알아 들었다는 명확한 피드백을 받게 됩니다**. 이러한 두 신호를 통해 사용자는 음성을 기본 입력으로 사용할 때 안심할 수 있습니다. 다음은 음성 입력이 인식될 때 커서에 나타나는 결과와 사용자에게 이러한 사실을 전달하는 방법을 보여 주는 다이어그램입니다.


:::row:::
    :::column:::
       ![1. 일반 커서 상태](images/voicefeedbackstates-regular.jpg)<br>
       **1. 일반 커서 상태**<br>
    :::column-end:::
    :::column:::
       ![2. 음성 피드백을 전달 하 고 사라집니다.](images/voicefeedbackstates-voice.jpg)<br>
        **2. 음성 피드백을 전달 하 고 사라집니다.**<br>
    :::column-end:::
    :::column:::
       ![3. 일반 커서 상태](images/voicefeedbackstates-regular.jpg)<br>
       **3. 일반 커서 상태로 돌아갑니다.**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>혼합 현실에서 "음성"에 대해 알아야 할 주요 사항
* 단추를 타기팅할 때 **"Select"** 라고 말합니다(단추를 클릭하기 위해 어디에서나 사용할 수 있음).
* 일부 앱에서는 작업을 수행하기 위해 **label name of an app bar button**이라고 말할 수 있습니다. 예를 들어, 앱을 바라보면서 명령 "Remove"라고 말하여 작업 환경에서 해당 앱을 제거할 수 있습니다(손으로 클릭할 때모다 시간이 절감됨).
* **"Hey Cortana"** 라고 말하여 Cortana가 청취를 시작하도록 할 수 있습니다. 질문을 하거나("Hey Cortana, how tall is the Eiffel tower"), 앱을 열도록 말하거나("Hey Cortana, open Netflix"), 시작 메뉴를 불러오도록 말할 수 있습니다("Hey Cortana, take me home").

## <a name="common-questions-and-concerns-users-have-about-voice"></a>음성에 대한 사용자의 일반적인 질문 및 어려움
* 무엇을 말할 수 있나요?
* 시스템이 내 말을 제대로 알아듣는지 어떻게 알 수 있나요?
   * 시스템이 내 음성 명령을 계속 잘못 알아듣습니다.
   * 음성 명령을 받아도 반응하지 않습니다.
* 음성 명령을 제공할 때 잘못된 방식으로 반응합니다.
* 특정 앱이나 앱 명령을 대상으로 음성 명령을 내리려면 어떻게 하나요?
* 음성을 사용해서 항목을 HoloLens의 홀로그래픽 프레임 밖으로 보낼 수 있나요?

## <a name="communication"></a>통신

HoloLens에서 제공 하는 사용자 지정 된 오디오 입력 처리 옵션을 활용 하려는 응용 프로그램의 경우 앱에서 사용할 수 있는 다양 한 [오디오 스트림 범주](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) 를 이해 하는 것이 중요 합니다. Windows 10은 다양 한 스트림 범주를 지원 하 고, HoloLens는 이러한 세 가지를 사용 하 여 음성, 통신 및 주변 환경 오디오 캡처 (예: "캠코더") 시나리오에 사용할 수 있는 마이크 오디오 품질을 최적화 하기 위해 사용자 지정 처리를 사용 하도록 설정 합니다.
* AudioCategory_Communications stream 범주는 통화 품질 및 내레이션 시나리오에 맞게 사용자 지정 되며 클라이언트에 사용자 음성의 16kHz 24bit mono 오디오 스트림을 제공 합니다.
* AudioCategory_Speech stream 범주는 HoloLens (Windows) 음성 엔진에 맞게 사용자 지정 되며 사용자 음성의 16kHz 24bit mono 스트림을 제공 합니다. 이 범주는 필요한 경우 타사 음성 엔진에서 사용할 수 있습니다.
* AudioCategory_Other stream 범주는 주변 환경 오디오 녹음에 맞게 사용자 지정 되며 클라이언트에 48kHz 24 비트 스테레오 오디오 스트림을 제공 합니다.

이러한 오디오 처리는 모두 하드웨어 가속입니다. 즉, HoloLens CPU에서 동일한 처리가 수행 된 경우 보다 기능이 훨씬 더 많은 전력을 소모 하 게 됩니다. 시스템 배터리 수명을 최대화 하 고 오프 로드 된 기본 제공 오디오 입력 처리 기능을 활용 하기 위해 CPU에서 기타 오디오 입력 처리를 실행 하지 않도록 합니다.

## <a name="languages"></a>언어

HoloLens 2는 추가 언어도 지원 합니다. 음성 명령은 여러 키보드가 설치 되어 있거나 앱이 다른 언어로 음성 인식기를 만들려고 하는 경우에도 항상 시스템의 표시 언어로 실행 됩니다.

## <a name="troubleshooting"></a>문제 해결

"Select" 및 "안녕하세요 Cortana"를 사용 하는 데 문제가 있는 경우 더 조용한 공간으로 이동 하거나, 소음의 원본에서 떨어진 곳으로 이동 하거나, 더 크게 말해 보세요. 지금은 HoloLens의 모든 음성 인식이 특별히 미국 영어의 기본 스피커로 조정 되 고 최적화 됩니다.

Windows Mixed Reality Developer Edition 릴리스 2017에서는 초기 HMD 연결 후 PC 데스크톱에 로그 아웃 했다가 다시 로그인 한 후 오디오 끝점 관리 논리가 정상적으로 작동 합니다 (계속). WMR OOBE를 통과 한 후 첫 번째 로그 아웃 이벤트 이전에는 사용자가 HMD를 처음으로 연결 하기 전에 설정 된 방법에 따라 오디오 없음에서 오디오 전환 없이 다양 한 오디오 기능 문제가 발생할 수 있습니다.

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 용 MRTK (Mixed Reality Toolkit)의 음성 입력
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 를 사용 하면 개체에 음성 명령을 쉽게 할당할 수 있습니다. MRTK의 **음성 입력 프로필** 을 사용 하 여 키워드를 정의 합니다. **SpeechInputHandler** 스크립트를 할당 하 여 음성 입력 프로필에 정의 된 키워드에 대 한 모든 개체 응답을 만들 수 있습니다. 또한 SpeechInputHandler는 사용자의 신뢰도를 높이기 위해 음성 확인 레이블을 제공 합니다.

* [MRTK-음성 명령](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a>참고 항목
* [응시 및 커밋](gaze-and-commit.md)
* [Instinctual 상호 작용](interaction-fundamentals.md)
* [MR 입력 212: 음성](holograms-212.md)
* [DirectX의 음성 입력](voice-input-in-directx.md)
* [Unity의 음성 입력](voice-input-in-unity.md)
