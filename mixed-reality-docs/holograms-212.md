---
title: MR 입력 212-음성
description: Unity, Visual Studio 및 HoloLens를 사용 하 여이 코딩 연습을 수행 하 여 음성 개념에 대 한 세부 정보를 알아보세요.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit, 아카데미, 자습서, 음성
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522357"
---
>[!NOTE]
>혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.  따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.  이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.  지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다. 향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.  이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-input-212-voice"></a>MR 입력 212: 음성

[음성 입력](voice-input.md) 은 holograms와 상호 작용 하는 또 다른 방법을 제공 합니다. 음성 명령은 매우 자연스럽 고 쉬운 방법으로 작동 합니다. 음성 명령은 다음과 같이 설계 합니다.

* 스런
* 쉽게 기억할 수 있습니다.
* 적절 한 컨텍스트
* 동일한 컨텍스트 내의 다른 옵션과 충분히 구분

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

[MR 기본 101](holograms-101.md)에서 KeywordRecognizer를 사용 하 여 간단한 음성 명령을 두 번 빌드 했습니다. MR 입력 212에서는 다음을 수행 하는 방법을 자세히 알아보고 알아보세요.

* HoloLens 음성 엔진에 최적화 된 음성 명령을 디자인 합니다.
* 사용자가 사용할 수 있는 음성 명령을 인식 하도록 합니다.
* 사용자의 음성 명령이 들리는지 인정 합니다.
* 받아쓰기 인식기를 사용 하 여 사용자의 의견을 이해 합니다.
* 문법 인식기를 사용 하 여 SRGS 또는 음성 인식 문법 사양 파일에 따라 명령을 수신 합니다.

이 과정에서는 [Mr 입력 210](holograms-210.md) 및 [mr 입력 211](holograms-211.md)에서 빌드된 모델 탐색기를 다시 방문 합니다.

>[!IMPORTANT]
>아래 각 장에 포함 된 비디오는 이전 버전의 Unity 및 혼합 현실 도구 키트를 사용 하 여 기록 되었습니다. 단계별 지침은 정확 하 고 최신 상태 이지만 최신의 비디오에서 스크립트 및 시각적 개체를 볼 수 있습니다. Posterity에 대 한 비디오는 포함 되어 있지만 적용 되는 개념은 그대로 유지 됩니다.


## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 입력 212: 음성</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 주의 사항

### <a name="prerequisites"></a>사전 요구 사항

* 올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.
* 몇 가지 C# 기본적인 프로그래밍 기능.
* [MR 기본 101](holograms-101.md)를 완료 해야 합니다.
* [MR 입력 210](holograms-210.md)을 완료 해야 합니다.
* [MR 입력 211](holograms-211.md)을 완료 해야 합니다.
* [개발용으로 구성 된](using-visual-studio.md#enabling-developer-mode)HoloLens 장치입니다.

### <a name="project-files"></a>프로젝트 파일

* 프로젝트에 필요한 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) 을 다운로드 합니다. Unity 2017.2 이상이 필요 합니다.
* 바탕 화면 또는 기타 쉬운 위치에 파일을 보관 하지 않습니다.

>[!NOTE]
>다운로드 하기 전에 소스 코드를 확인 하려는 경우 [GitHub에서 사용할 수](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)있습니다.

### <a name="errata-and-notes"></a>정오표 및 참고 사항

* 코드에서 중단점을 적중 하려면 Visual Studio의 도구-> 옵션-> 디버깅에서 "내 코드만 사용"을 사용 하지 않도록 설정 (*선택 취소*) 해야 합니다.

## <a name="unity-setup"></a>Unity 설치

### <a name="instructions"></a>지침

1. Unity를 시작합니다.
2. **열기**를 선택 합니다.
3. 이전에 보관 하지 않은 **HolographicAcademy-Holograms-212-Voice** 폴더로 이동 합니다.
4. **모델 탐색기** **시작**/폴더를 찾아 선택 합니다.
5. **폴더 선택** 단추를 클릭 합니다.
6. **프로젝트** 패널에서 **장면** 폴더를 확장 합니다.
7. **모델 탐색기** 장면을 두 번 클릭 하 여 Unity에서 로드 합니다.

### <a name="building"></a>빌드

1. Unity에서 **파일 > 빌드 설정**을 선택 합니다.
2. 백그라운드에서 장면 **/모델 탐색기** 가 **백그라운드**에서 표시 되지 않는 경우 **열린 장면 추가** 를 클릭 하 여 장면을 추가 합니다.
3. 특별히 HoloLens를 개발 하는 경우 **대상 장치** 를 **hololens**로 설정 합니다. 그렇지 않으면 **모든 장치**에 그대로 둡니다.
4. **빌드 형식이** **D3D** 로 설정 되 고 **sdk** 가 **최신 버전** 으로 설정 되어 있는지 확인 합니다 (sdk 16299 이상 이어야 함).
5. **빌드**를 클릭합니다.
6. "App" 이라는 **새 폴더** 를 만듭니다.
7. 단일 **앱** 폴더를 클릭 합니다.
8. **폴더 선택** 을 클릭 하면 Unity에서 Visual Studio 용 프로젝트 빌드를 시작 합니다.

Unity가 완료 되 면 파일 탐색기 창이 표시 됩니다.

1. **앱** 폴더를 엽니다.
2. **모델 탐색기 Visual Studio 솔루션**을 엽니다.

HoloLens에 배포 하는 경우:

1. Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 **x 86**으로 변경 합니다.
2. 로컬 컴퓨터 단추 옆에 있는 드롭다운 화살표를 클릭 하 고 **원격 컴퓨터**를 선택 합니다.
3. **HoloLens 장치 IP 주소** 를 입력 하 고 인증 모드를 **유니버설 (암호화 되지 않은 프로토콜)** 로 설정 합니다. **선택**을 클릭합니다. 장치 IP 주소를 모르는 경우 **네트워크 & 인터넷 > 고급 옵션 > 설정**을 참조 하세요.
4. 상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다. 처음으로 장치에 배포 하는 경우에는 [Visual Studio와 쌍](using-visual-studio.md#pairing-your-device-hololens)으로 연결 해야 합니다.
5. 앱이 배포 되 면 **선택 제스처로** **fitbox** 를 해제 합니다.

모던 헤드셋에 배포 하는 경우:

1. Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 디버그에서 **릴리스** 로, ARM에서 x **64**로 변경 합니다.
2. 배포 대상이 **로컬 컴퓨터**로 설정 되었는지 확인 합니다.
3. 상단 메뉴 모음에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.
4. 앱이 배포 되 면 동작 컨트롤러에서 트리거를 당겨 **Fitbox** 를 해제 합니다.

>[!NOTE]
>Visual Studio 오류 패널에 몇 가지 빨간색 오류가 표시 될 수 있습니다. 무시 해도 됩니다. 출력 패널로 전환 하 여 실제 빌드 진행률을 확인 합니다. 출력 패널에 오류가 발생 하면 문제를 해결 해야 합니다 (대부분 스크립트에서 실수로 인해 발생 하는 경우).

## <a name="chapter-1---awareness"></a>1 장-인식

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>목표

* 음성 명령 디자인의 **일과 및 Dos** 에 대해 알아봅니다.
* **KeywordRecognizer** 를 사용 하 여 응시 기반 음성 명령을 추가 합니다.
* 사용자가 커서 **피드백**을 사용 하 여 음성 명령을 인식 하도록 합니다.

### <a name="voice-command-design"></a>음성 명령 디자인

이 장에서는 음성 명령을 디자인 하는 방법에 대해 알아봅니다. 음성 명령을 만들 때:

#### <a name="do"></a>DO

* 간결한 명령을 만듭니다. *"현재 선택한 비디오 재생"* 을 사용 하지 않으려는 경우에는 해당 명령이 간결 하지 않으며 사용자가 쉽게 잊어버린 것입니다. 대신 다음을 사용 해야 합니다. *"Play Video"* 는 간결 하 고 여러 음절을 포함 하기 때문입니다.
* 간단한 어휘를 사용 합니다. 사용자가 쉽게 검색 하 고 기억할 수 있는 일반적인 단어와 구를 항상 사용 하세요. 예를 들어 응용 프로그램에 보기에서 표시 하거나 숨길 수 있는 note 개체가 있는 경우 "카드"는 거의 사용 되지 않는 용어 이므로 *"Show 카드"* 명령을 사용 하지 않습니다. 대신 명령을 사용 합니다. 응용 프로그램에서 메모를 표시 하는 *"메모 표시"*
* 일관성을 유지합니다. 음성 명령은 응용 프로그램 전체에서 일관 되 게 유지 되어야 합니다. 응용 프로그램에 두 가지 장면이 있고 두 장면 모두에 응용 프로그램을 닫는 단추가 포함 되어 있다고 가정 합니다. 첫 번째 장면에서 *"Exit"* 명령을 사용 하 여 단추를 트리거하고 두 번째 장면에서 *"응용 프로그램 닫기"* 명령을 사용 하는 경우 사용자는 혼동을 발생 시킬 수 있습니다. 동일한 기능이 여러 장면에서 지속 되는 경우이를 트리거하기 위해 동일한 음성 명령을 사용 해야 합니다.

#### <a name="dont"></a>안 함

* 단일 음절 명령을 사용 합니다. 예를 들어 비디오를 재생 하는 음성 명령을 만든 경우 간단한 명령 *"play"* 를 사용 하지 않는 것이 좋습니다 .이는 단일 음절 이며 시스템에서 쉽게 누락 될 수 있기 때문입니다. 대신 다음을 사용 해야 합니다. *"Play Video"* 는 간결 하 고 여러 음절을 포함 하기 때문입니다.
* 시스템 명령을 사용 합니다. *"Select"* 명령은 현재 포커스가 있는 개체에 대 한 탭 이벤트를 트리거하기 위해 시스템에 예약 되어 있습니다. 원하는 대로 작동 하지 않을 수 있으므로 키워드 또는 구에 *"Select"* 명령을 다시 사용 하지 마십시오. 예를 들어 응용 프로그램에서 큐브를 선택 하는 음성 명령이 *"Select cube"* 이지만 사용자가 명령을 재생 때 구를 확인 하는 경우 구가 대신 선택 됩니다. 비슷하게 앱 바 명령은 음성으로 사용 됩니다. CoreWindow 보기에서 다음 음성 명령을 사용 하지 마세요.
    1. 돌아 가
    2. 스크롤 도구
    3. 확대/축소 도구
    4. 끌기 도구
    5. 조정
    6. 제거
* 비슷한 소리를 사용 합니다. Rhyme 음성 명령을 사용 하지 않도록 하십시오. *"저장소 표시"* 및 *"자세히 표시"* 를 지 원하는 쇼핑 응용 프로그램이 있는 경우 다른 명령 중 하나를 사용 하 고 있는 동안에는 명령 중 하나를 사용 하지 않도록 설정 하는 것이 좋습니다. 예를 들어 *"저장소 표시"* 단추를 사용 하 여 저장소를 연 후 *"자세히 표시"* 명령을 사용 하 여 검색을 할 수 있도록 저장소가 표시 될 때 해당 명령을 사용 하지 않도록 설정할 수 있습니다.

### <a name="instructions"></a>지침

* Unity의 **계층** 패널에서 검색 도구를 사용 하 여 **holoComm_screen_mesh** 개체를 찾습니다.
* **HoloComm_screen_mesh** 개체를 두 번 클릭 하 여 **화면**에 표시 합니다. 음성 명령에 응답 하는 astronaut의 조사식입니다.
* **검사기** 패널에서 **음성 입력 원본 (스크립트)** 구성 요소를 찾습니다.
* **키워드** 섹션을 확장 하 여 지원 되는 음성 명령을 표시 합니다. **Communicator를 엽니다**.
* 오른쪽의 코그를 클릭 한 다음 **스크립트 편집**을 선택 합니다.
* **SpeechInputSource.cs** 를 탐색 하 여 **KeywordRecognizer** 를 사용 하 여 음성 명령을 추가 하는 방법을 이해 합니다.

### <a name="build-and-deploy"></a>빌드 및 배포

* Unity에서 **파일 > 빌드 설정을** 사용 하 여 응용 프로그램을 다시 빌드합니다.
* **앱** 폴더를 엽니다.
* **모델 탐색기 Visual Studio 솔루션**을 엽니다.

설정 하는 동안 Visual Studio에서이 프로젝트를 이미 빌드/배포한 경우 해당 인스턴스를 열고 메시지가 표시 되 면 다시 로드를 클릭할 수 있습니다.

* Visual Studio에서 **디버그-> 디버깅 하지 않고 시작** 을 클릭 하거나 **ctrl + F5**를 누릅니다.
* 응용 프로그램을 HoloLens에 배포한 후에는 마우스를 [탭](gestures.md#air-tap) 제스처를 사용 하 여 맞춤 상자를 해제 합니다.
* Astronaut의 조사식을 응시 합니다.
* Watch에 포커스가 있는 경우 커서가 마이크로로 변경 되는지 확인 합니다. 그러면 응용 프로그램이 음성 명령을 수신 대기 하는 것으로 피드백을 제공 합니다.
* 도구 설명이 조사식에 표시 되는지 확인 합니다. 그러면 사용자가 *"Communicator 열기"* 명령을 검색 하는 데 도움이 됩니다.
* Gazing 하는 동안 *"Communicator 열기"* 라고 communicator 패널을 엽니다.

## <a name="chapter-2---acknowledgement"></a>2 장-승인

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>목표

* 마이크 입력을 사용 하 여 메시지를 기록 합니다.
* 응용 프로그램이 자신의 음성을 수신 대기 하 고 있음을 사용자에 게 피드백을 제공 합니다.

>[!NOTE]
>마이크에서 녹음할 앱에 대해 **마이크** 기능을 선언 해야 합니다. 이러한 작업은 이미 MR 입력 212에 대해 수행 되지만 사용자 고유의 프로젝트에 대해서는이를 염두에 두어야 합니다.
>
>1. Unity 편집기에서 "편집 > 프로젝트 설정 > 플레이어"로 이동 하 여 플레이어 설정으로 이동 합니다.
>2. "유니버설 Windows 플랫폼" 탭을 클릭 합니다.
>3. "게시 설정 > 기능" 섹션에서 **마이크** 기능을 확인 합니다.

### <a name="instructions"></a>지침

* Unity의 **계층 구조** 패널에서 **holoComm_screen_mesh** 개체가 선택 되어 있는지 확인 합니다.
* **검사기** 패널에서 **Astronaut Watch (스크립트)** 구성 요소를 찾습니다.
* **Communicator Prefab** 속성의 값으로 설정 된 작은 파란색 큐브를 클릭 합니다.
* 이제 **프로젝트** 패널에서 **Communicator** prefab에 포커스가 있어야 합니다.
* **프로젝트** 패널에서 **Communicator** prefab를 클릭 하 여 **검사기**에서 해당 구성 요소를 확인 합니다.
* **마이크 관리자 (스크립트)** 구성 요소를 살펴보면 사용자의 음성을 기록 하는 데 사용할 수 있습니다.
* **Communicator** 개체에는 **메시지 보내기** 명령에 응답 하기 위한 **음성 입력 처리기 (스크립트)** 구성 요소가 있습니다.
* **Communicator (스크립트)** 구성 요소를 확인 하 고 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.

Communicator.cs는 communicator 장치에서 적절 한 단추 상태를 설정 하는 일을 담당 합니다. 이렇게 하면 사용자가 메시지를 기록 하 고, 다시 재생 하 고, 메시지를 astronaut으로 보낼 수 있습니다. 또한 애니메이션이 적용 된 웨이브 폼을 시작 하 고 중지 하 여 사용자에 게 음성이 들리는지를 승인 합니다.

* **Communicator.cs**에서 **Start** 메서드에서 다음 줄 (81 및 82)을 삭제 합니다. 그러면 communicator에서 ' 레코드 ' 단추가 활성화 됩니다.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>빌드 및 배포

* Visual Studio에서 응용 프로그램을 다시 빌드하고 장치에 배포 합니다.
* Astronaut의 감시를 응시 하 고 communicator를 표시 하는 *"Open communicator"* 라고 표시 합니다.
* Astronaut에 대 한 구두 메시지 기록을 시작 하려면 **녹음** 단추 (마이크)를 누릅니다.
* 말하기를 시작 하 고 사용자에 게 음성이 들리는지 사용자에 게 피드백을 제공 하는 웨이브 애니메이션이 communicator에서 재생 되는지 확인 합니다.
* **중지** 단추 (왼쪽 사각형)를 누르고 웨이브 애니메이션의 실행이 중지 되는지 확인 합니다.
* **재생** 단추 (오른쪽 삼각형)를 눌러 기록 된 메시지를 재생 하 고 장치에서이를 듣습니다.
* **중지** 단추 (오른쪽 사각형)를 눌러 기록 된 메시지의 재생을 중지 합니다.
* *"메시지 보내기"* 를 통해 communicator를 닫고 astronaut에서 ' message Received ' 응답을 받을 수 있습니다.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>3 장-및 받아쓰기 인식기 이해

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>목표

* 받아쓰기 인식기를 사용 하 여 사용자의 음성을 텍스트로 변환 합니다.
* Communicator에서 받아쓰기 인식기의 가설 및 최종 결과를 표시 합니다.

이 장에서는 받아쓰기 인식기를 사용 하 여 astronaut에 대 한 메시지를 만듭니다. 받아쓰기 인식기를 사용 하는 경우 다음을 염두에 두어야 합니다.

* 받아쓰기 인식기가 작동 하려면 WiFi에 연결 되어 있어야 합니다.
* 시간 제한은 설정 된 시간 후에 발생 합니다. 다음 두 가지 제한 시간을 인식 합니다.
  * 인식기가 시작 되 고 처음 5 초 동안 오디오가 들리지 않으면 시간이 초과 됩니다.
  * 인식기가 결과를 제공 했지만 20 초 동안 침묵 소음을 받은 경우 시간이 초과 됩니다.
* 한 번에 하나의 인식기 유형 (키워드 또는 받아쓰기)만 실행할 수 있습니다.

>[!NOTE]
>마이크에서 녹음할 앱에 대해 **마이크** 기능을 선언 해야 합니다. 이러한 작업은 이미 MR 입력 212에 대해 수행 되지만 사용자 고유의 프로젝트에 대해서는이를 염두에 두어야 합니다.
>
>1. Unity 편집기에서 "편집 > 프로젝트 설정 > 플레이어"로 이동 하 여 플레이어 설정으로 이동 합니다.
>2. "유니버설 Windows 플랫폼" 탭을 클릭 합니다.
>3. "게시 설정 > 기능" 섹션에서 **마이크** 기능을 확인 합니다.

### <a name="instructions"></a>지침

받아쓰기 인식기를 사용 하도록 **MicrophoneManager.cs** 를 편집 하겠습니다. 다음을 추가 합니다.

1. **기록 단추** 를 누르면 **DictationRecognizer이 시작**됩니다.
2. DictationRecognizer가 이해 하는 사항의 **가설** 을 표시 합니다.
3. DictationRecognizer가 이해 한 **결과** 를 잠급니다.
4. DictationRecognizer에서 시간 제한을 확인 합니다.
5. **중지 단추** 를 누르거나 mic 세션이 시간 초과 되 면 **DictationRecognizer를 중지**합니다.
6. **메시지 보내기** 명령을 수신 대기 하는 **KeywordRecognizer**를 다시 시작 합니다.

이제 시작하겠습니다. **MicrophoneManager.cs**에서 3. a에 대 한 모든 코딩 연습을 완료 하거나 아래에 있는 완성 된 코드를 복사 하 여 붙여넣습니다.

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone. 
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>빌드 및 배포

* Visual Studio에서 다시 빌드하고 장치에 배포 합니다.
* 공기 탭 제스처를 사용 하 여 맞춤 상자를 해제 합니다.
* Astronaut의 감시를 응시 하 고 *"Communicator Open"* 이라고 표시 합니다.
* **녹음** 단추 (마이크)를 선택 하 여 메시지를 기록 합니다.
* 말하기를 시작 합니다. **받아쓰기 인식기** 는 음성을 해석 하 고, communicator에 가설 텍스트를 표시 합니다.
* 메시지를 기록 하는 동안 *"메시지 보내기"* 를 사용해 보세요. **받아쓰기 인식기** 가 여전히 활성 상태 이므로 **키워드 인식기** 가 응답 하지 않습니다.
* 몇 초 동안 말하기를 중지 합니다. 받아쓰기 인식기가 가설을 완료 하 고 최종 결과를 표시 하는 것을 시청 하세요.
* 읽어주기를 시작한 후 20 초 동안 일시 중지 합니다. 이렇게 하면 **받아쓰기 인식기** 가 시간 초과 됩니다.
* 위의 제한 시간이 지나면 **키워드 인식기** 가 다시 활성화 됩니다. 이제 communicator가 음성 명령에 응답 합니다.
* Astronaut에 메시지를 보내기 위한 *"메시지 보내기"* 라고 표시 합니다.

## <a name="chapter-4---grammar-recognizer"></a>4 장-문법 인식기

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>목표

* 문법 인식기를 사용 하 여 SRGS 또는 음성 인식 문법 사양 파일에 따라 사용자 음성을 인식 합니다.

>[!NOTE]
>마이크에서 녹음할 앱에 대해 **마이크** 기능을 선언 해야 합니다. 이러한 작업은 이미 MR 입력 212에 대해 수행 되지만 사용자 고유의 프로젝트에 대해서는이를 염두에 두어야 합니다.
>
>1. Unity 편집기에서 "편집 > 프로젝트 설정 > 플레이어"로 이동 하 여 플레이어 설정으로 이동 합니다.
>2. "유니버설 Windows 플랫폼" 탭을 클릭 합니다.
>3. "게시 설정 > 기능" 섹션에서 **마이크** 기능을 확인 합니다.

### <a name="instructions"></a>지침

1. **계층** 패널에서 **Jetpack_Center** 를 검색 하 고 선택 합니다.
2. **검사기** 패널에서 **Tagalong Action** 스크립트를 찾습니다.
3. 개체의 오른쪽에 있는 작은 원을 클릭 하 여 필드 **에 태그를 추가할 수** 있습니다.
4. 팝업 창이 표시 되 면 **Srgstoolbox** 를 검색 하 고 목록에서 선택 합니다.
5. **Streamingassets** 폴더의 **Srgscolor .xml** 파일을 살펴봅니다.
* SRGS 디자인 사양은 [여기](https://www.w3.org/TR/speech-grammar/)의 W3C 웹 사이트에서 찾을 수 있습니다.
* SRGS 파일에는 다음과 같은 세 가지 유형의 규칙이 있습니다.
  * 12 색 목록에서 한 색을 표시할 수 있는 규칙입니다.
  * 색 규칙과 세 도형 중 하나를 조합 하 여 수신 대기 하는 세 가지 규칙입니다.
  * 3 가지 "color + shape" 규칙의 조합을 수신 하는 루트 규칙 colorChooser입니다. 도형은 임의의 순서로 정렬 하 고 1부터 모두 세까지 지정할 수 있습니다. 이 규칙은 초기 &lt;문법&gt; 태그에서 파일의 맨 위에 루트 규칙으로 지정 되므로에 대해 수신 됩니다.

### <a name="build-and-deploy"></a>빌드 및 배포

* Unity에서 응용 프로그램을 다시 빌드한 다음, Visual Studio에서 빌드 및 배포 하 여 HoloLens에서 앱을 경험해 보세요.
* 공기 탭 제스처를 사용 하 여 맞춤 상자를 해제 합니다.
* Astronaut의 jetpack을 응시 하 고 공중 탭 제스처를 수행 합니다.
* 말하기를 시작 합니다. **문법 인식기** 는 음성을 해석 하 고 인식에 따라 셰이프의 색을 변경 합니다. 예제 명령은 "파란색 원, 노란색 사각형"입니다.
* 다른 공기 탭 제스처를 수행 하 여 도구 상자를 해제 합니다.

## <a name="the-end"></a>끝

축하합니다. 이제 MR 입력 212 **을 완료 했습니다. 음성**.

* 음성 명령의 Dos 및 일과을 알고 있습니다.
* 사용자가 음성 명령을 인식 하도록 도구 설명을 사용 하는 방법을 살펴보았습니다.
* 사용자의 음성이 들리는지 확인 하는 데 사용 되는 다양 한 유형의 피드백이 표시 됩니다.
* 키워드 인식자와 받아쓰기 인식기 사이를 전환 하는 방법 및 이러한 두 기능이 음성을 이해 하 고 해석 하는 방법을 알고 있습니다.
* 응용 프로그램에서 음성 인식을 위해 SRGS 파일 및 문법 인식기를 사용 하는 방법을 배웠습니다.
