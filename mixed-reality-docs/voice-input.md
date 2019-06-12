---
title: 음성 입력
description: 음성 입력이 HoloLens 및 Windows Mixed Reality 몰입 형 헤드셋에 대 한 핵심 입력 합니다. 음성 명령, 받아쓰기, Cortana, 등에 대 한 사용할 수 있습니다.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv, 음성, cortana 음성 입력
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829952"
---
# <a name="voice-input"></a>음성 입력

음성에 대 한 의견도 HoloLens의 세 가지 키 형식 중 하나입니다. 직접 사용 하지 않고도 홀로그램 명령 할 수 있습니다 [제스처](gestures.md)합니다. 있습니다 단순히 [gaze](gaze.md) 를 홀로그램에서 말하고 명령입니다. 음성 입력 의도인 통신 하는 자연 스러운 방법이 될 수 있습니다. 음성은 사용자가 하나의 명령 사용 하 여 중첩 된 메뉴가 줄이는 수 있기 때문에 복잡 한 인터페이스를 트래버스에 특히 적합 합니다.

음성 입력으로 구동 되며 합니다 [같은 엔진](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) 다른 모든 유니버설 Windows 앱에서 지 원하는 음성.

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (첫 번째 범용)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></td>
    </tr>
     <tr>
        <td>음성 입력</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>(사용 하 여 마이크) ✔️</td>
    </tr>
</table>

## <a name="the-select-command"></a>"Select" 명령

음성 지원 앱에 구체적으로 추가 하지 않고도 사용자가 "select" 라는 하면 홀로그램을 활성화할 수 있습니다. 이 동일 하 게 동작을 [어 탭](gestures.md#air-tap) HoloLens에서 선택 단추를 누르고 합니다 [HoloLens clicker](hardware-accessories.md#hololens-clicker), 트리거를 누르거나는 [Windows Mixed Reality 동작 컨트롤러](motion-controllers.md). 소리를 듣고 되며 확인 표시 "선택"을 사용 하 여 도구 설명을 참조 하세요. "Select" 항상 쪽에는 손이 최소 배터리 수명에 영향을 줍니다 서 언제 든 지 말할 수는 사용할 수 있도록 절전 키워드 검색 알고리즘으로 사용 됩니다.

> [!NOTE]
> HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.

!["Select" 명령을 사용 하 여 음성 선택](images/kma-voice-select-00170-800px.png)<br>
*"Select" 명령을 사용 하 여 음성 선택*

## <a name="hey-cortana"></a>안녕 코타나

또한 언제 든 지 Cortana를 불러오려면 "Hey Cortana"를 말할 수 있습니다. 그녀에 질문 만듭니다 계속 하거나 라는 예를 들어, 명령-만듭니다 제공에 게 표시 될 때까지 기다리는 필요가 "Hey Cortana 날씨 란?" 와 문장 하나입니다. Cortana 및 수행할 수 있는 작업에 대 한 자세한 내용은 단순히 요청할 만듭니다! "Hey Cortana 어떻게 말할" 예를 들어합니다 자신이 작업 및 제안 된 명령의 목록을 잡아당깁니다 됩니다. Cortana 앱에서 이미 있는 경우 클릭할 수도 있습니다는 **?** 이 동일한 메뉴를 세로 막대에서 아이콘입니다.

**HoloLens 관련 명령**
* "이렇게 말 하세요~"
* "Go home" 또는 "시작"-of [블 룸](gestures.md#bloom) 페이지로 이동 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)
* "Launch <app>"
* "이동 <app> 여기"
* "사진을 찍은"
* "기록 시작"
* "기록을 중지"
* "밝게"
* "밝기 decrease"
* "볼륨 increase"
* "볼륨 decrease"
* "Mute" 또는 "음소거 해제"
* "장치 종료"
* "장치를 다시 시작"
* "절전 모드로 이동"
* "언제 입니까"?
* "남은 양을 배터리 do?"
* "호출 <contact>" (HoloLens에 대 한 Skype 필요)

## <a name="see-it-say-it"></a>"표시, 말"

HoloLens에 음성 입력에 대 한 "표시, 말" 모델이 있는 단추에서 레이블을 사용자에 게 알려주기 어떤 음성 명령으로 말할 수 있습니다. 예를 들어, 2D 앱을 보면 사용자 환경에서 앱의 위치를 조정 하려면 앱 바에서 보는 "조정" 명령을 말할 수 있습니다.

![사용자 환경에서 앱의 위치를 조정 하려면 앱 바에서 보는 "조정" 명령 말할 수는 2D 앱 또는 홀로그램에 원하는 경우](images/microphone-600px.png)

앱이이 규칙에 따라, 시스템을 제어 하에 사용자가 쉽게 파악할 수 있습니다. 단추에서 gazing 하는 동안이 보완을 하려면 단추 음성 지원 및 "누름"에 게 문의 하는 명령을 표시 하는 경우 잠시 후 표시 되는 "음성 지속" 도구 설명이 표시 됩니다.

![표시, 말 명령 단추 아래에 나타납니다.](images/voice-seeitsayit-600px.png)<br>
*단추 아래에 표시 되는 명령 "말이 참조 하세요."*

## <a name="voice-commands-for-fast-hologram-manipulation"></a>빠른 홀로그램 조작에 대 한 음성 명령

이 밖에도 다양 한 음성 명령에 신속 하 게 조작 작업을 수행 하는 홀로그램 gazing 하는 동안 말할 수 있습니다. 이러한 음성 명령은 2D 앱 뿐 아니라 전 세계에서 3D 개체에서 작동 합니다.

**홀로그램 조작 명령**
* Me 얼굴
* 더 큰 | 강화
* 더 작은

## <a name="dictation"></a>받아쓰기

사용 하 여 입력 하지 않고도 [탭을 어](gestures.md#air-tap), 음성 받아쓰기를 앱에 텍스트를 입력 하는 것이 효율적일 수 있습니다. 매우 적은 노력으로 사용자를 사용 하 여 입력을 가속화할 수 있습니다이.

![음성 받아쓰기 마이크 단추를 선택 하 여 시작](images/micbuttonfordictation.png)<br>
*음성 받아쓰기 키보드에서 마이크 단추를 선택 하 여 시작*

Holographic 키보드가 활성 상태인 경우 언제 든 지를 입력 하는 대신 받아쓰기 모드로 전환할 수 있습니다. 시작 하려면 텍스트 입력된 상자 측면의 마이크를 선택 합니다.

## <a name="communication"></a>통신

사용자 지정된 오디오 입력 처리 HoloLens에서 제공 하는 옵션을 활용 하고자 하는 응용 프로그램에 대 한 다양 한 알아야 할 것 [오디오 스트림 범주](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) 앱에서 사용할 수 있습니다. 여러 개의 다른 스트림으로 범주 및 HoloLens를 사용 하면 Windows 10 지원을 사용 하 여 이러한 세 가지 음성, 통신 및 오디오 주변 환경에 대 한 사용할 수 있는 다른 맞게 마이크 오디오 품질을 최적화 하기 위해 사용자 지정 처리를 사용 하도록 설정 캡처 (즉, "camcorder") 시나리오입니다.
* AudioCategory_Communications stream 범주 호출 품질 및 내레이션 시나리오에 대 한 사용자 지정 된 고 사용자의 음성의 16, 24 비트 kHz 모노 오디오 스트림을 사용 하 여 클라이언트에 제공
* AudioCategory_Speech stream 범주 HoloLens (Windows) 음성 엔진에 대 한 사용자 지정 된와 사용자의 음성의 16, 24 비트 kHz mono 스트림을 사용 하 여 제공 합니다. 필요한 경우 타사 파티 음성 엔진에서이 범주를 사용할 수 있습니다.
* AudioCategory_Other stream 범주 오디오 녹음 주변 환경에 대 한 사용자 지정 된 고 48 kHz 24 비트 스테레오 오디오 스트림을 사용 하 여 클라이언트를 제공 합니다.

이 모든 오디오 처리가 하드웨어 가속 기능 드레이닝 HoloLens CPU에서 동일한 처리가 완료 된 경우 보다 훨씬 적습니다. power를 의미 하는 중입니다. 다른 오디오 입력 시스템 배터리 수명을 최대화 하 여 기본 제공된을 활용 하기 위해 CPU에서 처리를 실행 하지 않습니다, 오디오 입력된 처리를 오프 로드 합니다.

## <a name="troubleshooting"></a>문제 해결

그래도 모든 "선택"을 사용 하 여 문제 및 "Hey Cortana" 방문해봅니다 노이즈를 더 크게 통화 하 여 원본에서 설정, 조용한 공간으로 이동 합니다. 이때 HoloLens에 모든 음성 인식 조정 이며의 미국 영어를 모국어에 맞게 최적화 합니다.

Windows Mixed Reality Developer Edition 2017 릴리스의 경우 오디오 끝점 관리 논리 작동 제대로 (영원히) HMD 한 초기 연결 후 PC 바탕 화면에서 로그 아웃 후 다시 로그인 한 후 합니다. Out/WMR OOBE 통해 이동 후 이벤트에 해당 첫 번째 기호 하기 전에 사용자 오디오 없음에서 오디오를 HMD 처음으로 연결 하기 전에 시스템 설정 된 방식에 따라 전환 없는에 이르기까지 다양 한 오디오 기능 문제를 발생할 수 있습니다.

## <a name="see-also"></a>참조
* [DirectX의 음성 입력](voice-input-in-directx.md)
* [Unity의 음성 입력](voice-input-in-unity.md)
* [MR 입력 212: 음성](holograms-212.md)
