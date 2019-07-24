---
title: 음성 입력
description: 음성 입력은 HoloLens 및 Windows Mixed Reality 모던 헤드셋의 핵심 입력입니다. 음성은 명령, 받아쓰기, Cortana 등에 사용할 수 있습니다.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv, 음성, cortana, 음성, 입력
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829952"
---
# <a name="voice-input"></a>음성 입력

음성은 HoloLens에서 입력 하는 세 가지 주요 형태 중 하나입니다. [제스처](gestures.md)를 사용 하지 않고도 홀로그램을 직접 명령을 수행할 수 있습니다. 홀로그램을 [응시](gaze.md) 하 고 명령을 말하기만 하면 됩니다. 음성 입력은 의도를 전달 하는 자연 스러운 방법이 될 수 있습니다. 음성은 사용자가 하나의 명령을 사용 하 여 중첩 된 메뉴를 잘라낼 수 있으므로 특히 복잡 한 인터페이스를 트래버스하는 데 유용 합니다.

음성 입력은 다른 모든 유니버설 Windows 앱의 음성을 지 원하는 [동일한 엔진](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) 에 의해 구동 됩니다.

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

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
        <td><strong>HoloLens 2</strong></td>
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

앱에 음성 지원을 특별히 추가 하지 않은 경우에도 사용자는 "선택" 이라는 간단한 방법으로 holograms을 활성화할 수 있습니다. 이는 HoloLens의 [공기 탭](gestures.md#air-tap) , [hololens clicker](hardware-accessories.md#hololens-clicker)의 선택 단추 누르기 또는 [Windows Mixed Reality 동작 컨트롤러](motion-controllers.md)에서 트리거 누르기와 동일 하 게 작동 합니다. 소리가 들리고 "선택"이 확인으로 표시 된 도구 설명이 표시 됩니다. "선택"은 낮은 파워 키워드 검색 알고리즘에서 사용 하도록 설정 되므로 사용자가 손을 사용 하더라도 배터리 수명에 영향을 최소화 하면서 언제 든 지 항상 사용할 수 있습니다.

> [!NOTE]
> HoloLens 2에 대 한 추가 지침은 [곧](index.md#news-and-notes)제공 될 예정입니다.

![선택 영역에 음성 명령을 사용 하려면 "선택" 이라고 표시 합니다.](images/kma-voice-select-00170-800px.png)<br>
*선택 영역에 음성 명령을 사용 하려면 "선택" 이라고 표시 합니다.*

## <a name="hey-cortana"></a>안녕 코타나

또한 언제 든 지 Cortana를 표시 하는 "안녕하세요" Cortana를 사용할 수 있습니다. 사용자의 질문을 계속 하거나 명령을 제공 하기 위해 사용자가 표시 될 때까지 기다릴 필요가 없습니다. 예를 들어 "안녕하세요? 단일 문장으로 Cortana 및 수행할 수 있는 작업에 대 한 자세한 내용은 사용자에 게 문의 하세요. "Cortana는 어떻게 해야 하나요?" 라고 표시 합니다. 그리고 작업 및 제안 된 명령 목록을 가져옵니다. Cortana 앱에 이미 있는 경우 **다음을 클릭** 하면 됩니다. 동일한 메뉴를 끌어올 수 있는 아이콘입니다.

**HoloLens 관련 명령**
* "이렇게 말 하세요~"
* [시작 메뉴로](navigating-the-windows-mixed-reality-home.md#start-menu) 이동 하려면 "홈으로 이동" 또는 "시작으로 이동"을 [블 룸](gestures.md#bloom) .
* "Launch <app>"
* "여기 <app> 로 이동"
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
* "Call <contact>" (HoloLens를 위한 Skype 필요)

## <a name="see-it-say-it"></a>"이 항목을 참조 하세요."

HoloLens에는 음성 입력에 대 한 "이를 확인 하는 것이 있습니다. 예를 들어 2D 앱을 볼 때 사용자는 앱 바에 표시 되는 "조정" 명령을 사용 하 여 전 세계의 앱 위치를 조정할 수 있습니다.

![2D 앱 또는 홀로그램을 볼 때 사용자는 앱 바에 표시 되는 "조정" 명령을 사용 하 여 전 세계의 앱 위치를 조정할 수 있습니다.](images/microphone-600px.png)

앱이이 규칙을 준수 하는 경우 사용자는 시스템을 제어 하는 내용을 쉽게 파악할 수 있습니다. 이를 강화 하기 위해 단추를 gazing 하는 동안 단추를 음성으로 사용할 수 있는 경우 두 번째 "음성 유지" 도구 설명이 표시 되 고이를 통해 "press"로 말하는 명령이 표시 됩니다.

![단추 아래에 표시 되는 것을 확인 하세요.](images/voice-seeitsayit-600px.png)<br>
*단추 아래에 "표시 됩니다." 라고 표시 되는 명령*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>빠른 홀로그램 조작을 위한 음성 명령

또한 한 번에 조작 작업을 빠르게 수행 하기 위해 홀로그램에서 gazing 하는 동안 많은 음성 명령을 사용할 수 있습니다. 이러한 음성 명령은 전 세계에 배치한 3D 개체 뿐만 아니라 2D 앱 에서도 작동 합니다.

**홀로그램 조작 명령**
* 얼굴 얼굴
* 크게 | 보강
* 짧은

## <a name="dictation"></a>받아쓰기

음성 받아쓰기는 [공기 탭](gestures.md#air-tap)을 사용 하 여 입력 하는 대신 앱에 텍스트를 입력 하는 것이 더 효율적일 수 있습니다. 이렇게 하면 사용자에 대해 더 짧은 노력으로 입력 속도를 크게 높일 수 있습니다.

![음성 받아쓰기는 마이크 단추를 선택 하 여 시작 합니다.](images/micbuttonfordictation.png)<br>
*음성 받아쓰기는 키보드에서 마이크 단추를 선택 하 여 시작 합니다.*

Holographic 키보드가 활성화 될 때마다 입력 하는 대신 받아쓰기 모드로 전환할 수 있습니다. 텍스트 입력 상자의 측면에서 마이크를 선택 하 여 시작 합니다.

## <a name="communication"></a>통신

HoloLens에서 제공 하는 사용자 지정 된 오디오 입력 처리 옵션을 활용 하려는 응용 프로그램의 경우 앱에서 사용할 수 있는 다양 한 [오디오 스트림 범주](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) 를 이해 하는 것이 중요 합니다. Windows 10은 몇 가지 다른 스트림 범주를 지원 하 고, HoloLens는 이러한 세 가지를 사용 하 여 음성, 통신 및 주변 환경 오디오에 사용 될 수 있는 마이크 오디오 품질을 최적화 하기 위해 사용자 지정 처리를 사용 하도록 설정 합니다. (즉, "캠코더") 시나리오를 캡처합니다.
* AudioCategory_Communications stream 범주는 통화 품질 및 내레이션 시나리오에 맞게 사용자 지정 되며 클라이언트에 사용자 음성의 16kHz 24bit mono 오디오 스트림을 제공 합니다.
* AudioCategory_Speech stream 범주는 HoloLens (Windows) 음성 엔진에 맞게 사용자 지정 되며 사용자 음성의 16kHz 24bit mono 스트림을 제공 합니다. 이 범주는 필요한 경우 타사 음성 엔진에서 사용할 수 있습니다.
* AudioCategory_Other stream 범주는 주변 환경 오디오 녹음에 맞게 사용자 지정 되며 클라이언트에 48kHz 24 비트 스테레오 오디오 스트림을 제공 합니다.

이러한 오디오 처리는 모두 하드웨어 가속입니다. 즉, HoloLens CPU에서 동일한 처리가 수행 된 경우 보다 기능이 훨씬 더 많은 전력을 소모 하 게 됩니다. 시스템 배터리 수명을 최대화 하 고 오프 로드 된 기본 제공 오디오 입력 처리 기능을 활용 하기 위해 CPU에서 기타 오디오 입력 처리를 실행 하지 않도록 합니다.

## <a name="troubleshooting"></a>문제 해결

"Select" 및 "안녕하세요 Cortana"를 사용 하는 데 문제가 있는 경우 더 조용한 공간으로 이동 하거나, 소음의 원본에서 떨어진 곳으로 이동 하거나, 더 크게 말해 보세요. 지금은 HoloLens의 모든 음성 인식이 특별히 미국 영어의 기본 스피커로 조정 되 고 최적화 됩니다.

Windows Mixed Reality Developer Edition 릴리스 2017에서는 초기 HMD 연결 후 PC 데스크톱에 로그 아웃 했다가 다시 로그인 한 후 오디오 끝점 관리 논리가 정상적으로 작동 합니다 (계속). WMR OOBE를 통과 한 후 첫 번째 로그 아웃 이벤트 이전에는 사용자가 HMD를 처음으로 연결 하기 전에 설정 된 방법에 따라 오디오 없음에서 오디오 전환 없이 다양 한 오디오 기능 문제가 발생할 수 있습니다.

## <a name="see-also"></a>참조
* [DirectX의 음성 입력](voice-input-in-directx.md)
* [Unity의 음성 입력](voice-input-in-unity.md)
* [MR 입력 212: 음성](holograms-212.md)
