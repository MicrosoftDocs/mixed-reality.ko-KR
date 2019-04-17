---
title: MR Input 212 - Voice
description: Unity에서 Visual Studio 및 HoloLens를 사용 하 여 음성 개념의 세부 정보를 알아보려면이 코딩 연습을 수행 합니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit mixedrealitytoolkit, mixedrealitytoolkit unity, academy, 음성 자습서
ms.openlocfilehash: 7e792bf40c47d4e1d57898fbe75ad050a030b7e3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598925"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-input-212-voice"></a>MR 입력 212: 음성

[입력 음성](voice-input.md) 우리의 홀로그램 상호 작용 하는 또 다른 방법은 제공 합니다. 음성 명령은 매우 자연 스러운 쉽고 방식으로 작동합니다. 수 있도록 음성 명령을 디자인:

* 자연 스러운
* 기억 하기 쉬운
* 적절 한 컨텍스트
* 충분히 동일한 컨텍스트 내에서 다른 옵션 중에서 고유

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

[MR 기본 사항 101](holograms-101.md), 두 개의 간단한 음성 명령을 작성 하는 KeywordRecognizer를 사용 했습니다. MR 입력 212에서 심층 고 알아봅니다 드리겠습니다 방법:

* HoloLens 음성 엔진에 대 한 최적화 된 디자인 음성 명령입니다.
* 사용자를 인식 하도록 어떤 음성 명령을 사용할 수 있습니다.
* 사용자의 음성 명령 듣고 인정 합니다.
* 사용자 이해 받아쓰기 인식기를 사용 하 여 간다고 지정 합니다.
* SRGS, 또는 음성 인식 문법을 사양 파일을 기반으로 하는 명령에 대 한 수신 대기 하도록 문법 인식기를 사용 합니다.

이 과정에서 구축한 모델 탐색기를 다시 방문할 예정 [MR 입력 210](holograms-210.md) 하 고 [MR 입력 211](holograms-211.md)합니다.

>[!IMPORTANT]
>각 아래 단원에 포함 된 비디오는 이전 버전의 Unity 및 혼합 현실 도구 키트를 사용 하 여 기록 되었습니다. 단계별 지침을 정확 하 고 현재는, 스크립트 및 만료 된 해당 동영상의 시각적 개체를 볼 수 있습니다. 비디오는 두세요 포함 상태를 유지 및 개념 설명 하기 때문에 계속 적용 합니다.


## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td>MR 입력 212: 음성</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>시작하기 전 주의 사항

### <a name="prerequisites"></a>사전 요구 사항

* 올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md)입니다.
* 기본적인 C# 기능을 프로그래밍 합니다.
* 완료 해야 [MR 기본 사항 101](holograms-101.md)합니다.
* 완료 해야 [MR 입력 210](holograms-210.md)합니다.
* 완료 해야 [MR 입력 211](holograms-211.md)합니다.
* HoloLens 장치 [개발에 대해 구성 된](using-visual-studio.md#enabling-developer-mode)합니다.

### <a name="project-files"></a>프로젝트 파일

* 다운로드 합니다 [파일](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) 프로젝트에서 필요 합니다. Unity 2017.2 이상이 필요합니다.
* 취소 보관 파일을 데스크톱 또는 기타 쉽게 달성할 수 있습니다 위치 합니다.

>[!NOTE]
>을 다운로드 하기 전에 소스 코드를 확인 하려는 경우 있기 [GitHub에서 사용할 수 있는](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)합니다.

### <a name="errata-and-notes"></a>오류 및 정보

* 사용 하지 않도록 설정할 필요 "내 코드만 사용" (*unchecked*)-> 도구 아래에서 Visual Studio에서 코드에서 중단점을 적중 하려면-> 디버깅 옵션입니다.

## <a name="unity-setup"></a>Unity 설치

### <a name="instructions"></a>지침

1. Unity를 시작 합니다.
2. 선택 **열려**합니다.
3. 로 이동 합니다 **HolographicAcademy 홀로그램-212 음성** 폴더 되지 않은 보관 된 이전에 있습니다.
4. 찾기 및 선택 합니다 **터**/**모델 탐색기** 폴더입니다.
5. 클릭 합니다 **폴더 선택** 단추입니다.
6. 에 **프로젝트** 패널을 확장 합니다 **장면** 폴더.
7. 두 번 클릭 **ModelExplorer** 장면 Unity에 로드 합니다.

### <a name="building"></a>빌드

1. Unity에서 선택 **파일 > 빌드 설정**합니다.
2. 하는 경우 **장면/ModelExplorer** 에 나열 되지 **Scenes In Build**, 클릭 **열기 장면 추가** 장면에 추가할 합니다.
3. HoloLens에 대 한 구체적으로 개발 하는 경우 설정 **대상 장치** 하 **HoloLens**합니다. 그렇지 않으면 켜져 **모든 장치**합니다.
4. 확인 **빌드 형식** 로 설정 된 **D3D** 하 고 **SDK** 로 설정 되어 **가장 최근에 설치 된** (16299 또는 최신 SDK는 이어야 함).
5. **빌드**를 클릭합니다.
6. 만들기는 **새 폴더** 이름을 "App"입니다.
7. 한 번 클릭 합니다 **앱** 폴더입니다.
8. 키를 눌러 **폴더 선택** Unity for Visual Studio 프로젝트를 빌드하기 시작 됩니다.

Unity 완료 되 면 파일 탐색기 창이 나타납니다.

1. 엽니다는 **앱** 폴더입니다.
2. 엽니다는 **ModelExplorer Visual Studio 솔루션**합니다.

HoloLens 배포 하는 경우:

1. 에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **x86**합니다.
2. 드롭다운 로컬 컴퓨터 단추 옆의 화살표를 클릭 하 고 선택 **원격 컴퓨터**합니다.
3. 입력 **HoloLens 장치 IP 주소** 인증 모드를 설정 하 고 **유니버설 (암호화 되지 않은 프로토콜)** 합니다. 클릭 **선택**합니다. 장치 IP 주소를 모르는 경우 찾는 위치 **설정 > 네트워크 및 인터넷 > 고급 옵션**합니다.
4. 맨 위 메뉴 모음에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다. 처음으로 장치에 배포할 경우 해야 [Visual Studio를 사용 하 여 쌍](using-visual-studio.md#pairing-your-device-hololens)합니다.
5. 앱에 배포 하는 경우 해제 합니다 **Fitbox** 사용 하 여를 **제스처 선택**.

경우는 몰입 형 헤드셋에 배포 합니다.

1. 에 디버그 대상 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **릴리스** 들어오고를 ARM **x64**합니다.
2. 배포 대상 설정 되어 있는지 확인 **로컬 컴퓨터**합니다.
3. 맨 위 메뉴 모음에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.
4. 앱에 배포 하는 경우 해제 합니다 **Fitbox** 동작 컨트롤러에서 트리거를 풀링 하 여 합니다.

>[!NOTE]
>Visual Studio 오류 패널에서 빨간색 일부 오류를 확인할 수 있습니다. 무시 해도 됩니다. 스위치를 실제 보려면 출력 패널에 빌드 진행률입니다. 출력 패널에는 오류 (가장 일반적으로 스크립트를이 잘못 되어 발생)을 수정 해야 해야 합니다.

## <a name="chapter-1---awareness"></a>1 장-인식

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>목표

* 에 대해 알아봅니다 합니다 **일과** 음성 명령 디자인 합니다.
* 사용 하 여 **KeywordRecognizer** 게이즈 기반 음성 명령을 추가할 수 있습니다.
* 사용자가 커서를 사용 하 여 음성 명령을 인식 하도록 **피드백**합니다.

### <a name="voice-command-design"></a>음성 명령 디자인

이 챕터에서는 음성 명령 디자인에 대 한 알아봅니다. 음성 명령을 만들면:

#### <a name="do"></a>DO

* 간결한 명령을 만듭니다. 사용 하지 않으려는 *"현재 선택 된 비디오 재생"* 명령을 간결한 이며 사용자가 기억 하기가 것 때문입니다. 대신 사용 하면 됩니다. *"비디오 재생"* 이므로 간결 하며 여러 음절을 갖추고 있습니다.
* 간단한 어휘를 사용 합니다. 항상 일반적인 단어 및 구 검색 하 고 기억 하기 쉽게 사용 하려고 합니다. 예를 들어, 응용 프로그램에 표시 하거나 뷰에서 숨길 수 있는 참고를 있으면 하지는 명령을 사용 *"카드 표시"* 이므로 "카드" 드물게 사용 되는 용어입니다. 대신 명령을 사용 합니다. *"참고 표시"*, 응용 프로그램에서 메모를 표시 합니다.
* 일관성을 유지합니다. 음성 명령 해야 응용 프로그램에서 일관성 있게 유지할 수 있습니다. 두 장면 응용 프로그램에 둘 다 백그라운드에서 응용 프로그램에 대 한 단추를 포함 한다고 가정 합니다. 명령을 사용 하는 첫 번째 장면을 *"Exit"* 트리거할 단추 되지만 두 번째 장면 명령을 사용 하 *앱 "닫기"*, 생기게 하려는 사용자를 합니다. 여러 장면에서 동일한 기능을 계속 되 면 동일한 음성 명령은 트리거를 사용 해야 합니다.

#### <a name="dont"></a>안 함

* 단일 음절 명령을 사용 합니다. 예를 들어 비디오를 재생 하는 음성 명령을 만들 때 사용 하지 않아야 간단한 명령을 *"재생"* 처럼는 단일 음절만 되 고 시스템에서 쉽게 누락 될 수 있습니다. 대신 사용 하면 됩니다. *"비디오 재생"* 이므로 간결 하며 여러 음절을 갖추고 있습니다.
* 시스템 명령을 사용 합니다. 합니다 *"Select"* 명령 시스템 현재 포커스가 있는 개체에 대 한 탭 이벤트를 트리거하는 데 예약 됩니다. 다시 사용 하지 마십시오는 *"Select"* 명령을 키워드 또는 구에 예상한 대로 작동 하지 않으므로 수 있습니다. 예를 들어, 응용 프로그램에서 큐브를 선택 하는 것에 대 한 음성 명령이 되었으면 *"선택 큐브"*, 하지만 사용자가 구 명령을 재생 하는 경우 구체를 대신 선택할 수는 있습니다. 마찬가지로 앱 표시줄 명령 음성 지원 됩니다. CoreWindow 뷰에 다음 음성 명령을 사용 안 함:
    1. 돌아 가
    2. 스크롤 도구
    3. 확대/축소 도구
    4. 끌어서 도구
    5. 조정
    6. 제거
* 소리가 비슷한를 사용 합니다. 구절 음성 명령을 사용 하지 않도록 하려고 합니다. 지원 되는 쇼핑 응용 프로그램을 설치한 경우 *"표시 Store"* 및 *"자세히"* 으로 음성 명령, 다른 사용할 때 명령 중 하나를 사용 하지 않도록 할 것입니다. 예를 들어 사용할 수 있습니다는 *"표시 저장"* 저장소를 열려면 단추를 스토어에 표시 된 경우 다음 명령을 사용 하지 않도록 있도록를 *"자세히"* 명령을 검색에 사용할 수 있습니다.

### <a name="instructions"></a>지침

* Unity의 **계층** 패널에서 찾으려는 검색 도구를 사용 합니다 **holoComm_screen_mesh** 개체입니다.
* 두 번 클릭 합니다 **holoComm_screen_mesh** 에서 보려는 개체를 **장면**합니다. 이것이 우리의 음성 명령에 응답할 고상한의 watch,입니다.
* 에 **검사기** 패널에서 찾을 합니다 **음성 입력 원본 (스크립트)** 구성 요소.
* 확장 된 **키워드** 섹션을 참조 하는 지원 되는 음성 명령: **Communicator 엽니다**합니다.
* 왼쪽에서 오른쪽으로 코그를 클릭 한 다음 선택 **스크립트 편집**합니다.
* 탐색 **SpeechInputSource.cs** 사용 하는 방식을 이해 하는 **KeywordRecognizer** 음성 명령을 추가할 수 있습니다.

### <a name="build-and-deploy"></a>빌드 및 배포

* Unity를 사용 하 여 **파일 > 빌드 설정** 응용 프로그램을 다시 작성 해야 합니다.
* 엽니다는 **앱** 폴더입니다.
* 엽니다는 **ModelExplorer Visual Studio 솔루션**합니다.

(이미 빌드된/을 배포한 경우 Visual Studio에서이 프로젝트를 설정 하는 동안 다음 수 VS의 해당 인스턴스를 열고 ' 모두 다시 로드 ' 메시지가 표시 되 면 클릭).

* Visual Studio에서 클릭 **디버그-> 디버깅 없이 시작** 누르거나 **ctrl+f5**합니다.
* 응용 프로그램을 HoloLens를 배포한 후 사용 하 여 적합된 한 상자를 해제 합니다 [어 탭](gestures.md#air-tap) 제스처입니다.
* 고상한의 보기를 응시 합니다.
* 시계에 포커스가 있는지 확인 하는 경우 커서 마이크를 변경 합니다. 이 응용 프로그램 음성 명령을 수신 하는 피드백을 제공 합니다.
* 시계에 도구 설명 표시 되는지 확인 합니다. 이렇게 하면 사용자가 검색 합니다 *"Open Communicator"* 명령입니다.
* 시계에서 gazing, 하는 동안 가정해 *"엽니다 Communicator"* communicator 패널을 엽니다.

## <a name="chapter-2---acknowledgement"></a>2 장-승인

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>목표

* 마이크 입력을 사용 하 여 메시지를 기록 합니다.
* 응용 프로그램에서 해당 음성 수신 하는 사용자에 게 피드백을 제공 합니다.

>[!NOTE]
>합니다 **마이크** 마이크에서 녹음 하는 앱에 대 한 기능을 선언 해야 합니다. 이루어지는를 이미 MR 입력 212 하지만이 사용자의 프로젝트에 대 한 염두에 둡니다.
>
>1. Unity 편집기에서 "> 프로젝트 설정 > Player 편집"로 이동 하 여 플레이어 설정으로 이동 합니다.
>2. "유니버설 Windows 플랫폼" 탭을 클릭
>3. "게시 설정 > 기능" 섹션을 확인 합니다 **마이크** 기능

### <a name="instructions"></a>지침

* Unity의 **계층** 패널에서 확인 합니다 **holoComm_screen_mesh** 개체를 선택 합니다.
* 에 **검사기** 패널에서 찾을 합니다 **고상한 감시 (스크립트)** 구성 요소입니다.
* 값으로 설정 되어 있는 소규모의 파란색 큐브 클릭 합니다 **Communicator Prefab** 속성입니다.
* **프로젝트** 패널의 **Communicator** prefab 포커스가 있어야 합니다.
* 클릭 합니다 **Communicator** prefab의 **프로젝트** 패널의 해당 구성 요소를 볼 수는 **검사기**합니다.
* 확인 합니다 **마이크 관리자 (스크립트)** 구성 요소, 이렇게 하면 사용자의 음성을 녹음 하 합니다.
* 있음을 합니다 **Communicator** 개체에는 **음성 입력 처리기 (스크립트)** 에 응답 하기 위한 구성 요소를 **메시지 보내기** 명령입니다.
* 확인 합니다 **Communicator (스크립트)** 구성 요소 및 Visual Studio에서 열려는 스크립트를 두 번 클릭 합니다.

Communicator.cs는 communicator 장치의 적절 한 단추 상태를 설정 하는 일을 담당 합니다. 이렇게 하면 사용자 메시지를 기록 하 고를 재생할는 고상한 메시지 보내기에 있습니다. 또한 시작 하 고 중지 된 애니메이션된 웨이브 형식으로 음성 인식을 들어 본 적 된 사용자에 게 승인 합니다.

* **Communicator.cs**에서 다음 줄 (예: 81 및 82)을 삭제 합니다 **시작** 메서드. 이렇게 하면 '기록' 단추는 communicator에서 활성화 됩니다.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>빌드 및 배포

* Visual Studio에서 응용 프로그램을 다시 작성 하 고 장치에 배포 합니다.
* 그리고 고상한의 조사식 응시 *"Open Communicator"* 는 communicator 표시 합니다.
* 키를 눌러 합니다 **레코드** 구두 메시지는 고상한에 대 한 기록을 시작 하려면 단추 (마이크).
* 말하기를 시작 하 고 음성 인식을 들립니다 사용자에 게 피드백을 제공 하는 communicator에서 wave 애니메이션을 재생을 확인 합니다.
* 키를 눌러 합니다 **중지** (왼쪽된 사각형) 단추를 클릭 한 웨이브 애니메이션 실행을 중지를 확인 합니다.
* 키를 눌러 합니다 **재생** 기록 된 메시지를 다시 재생 하는 장치에서 재생 단추 (오른쪽 삼각형).
* 키를 눌러 합니다 **중지** 기록 된 메시지의 재생을 중지 하려면 단추 (오른쪽 사각형).
* 예를 들어 *"메시지 보내기"* 는 communicator 닫고는 고상한에서 메시지가 수신 응답을 수신 합니다.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>3 장-받아쓰기 인식기 및 이해

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>목표

* 받아쓰기 인식기를 사용 하 여 사용자의 음성을 텍스트로 변환 합니다.
* communicator에서 받아쓰기 인식기의 가설 및 최종 결과 보여 줍니다.

이 장에서 고상한에 대 한 메시지를 만들려면 받아쓰기 인식기 사용 하겠습니다. 받아쓰기 인식기를 사용 하는 경우에 유의 합니다.

* 받아쓰기 인식기가 작동 하는 WiFi에 연결 해야 합니다.
* 시간 제한 설정된 기간 후 발생합니다. 알아야 할 두 가지 시간 제한을 가지가 있습니다.
  * 인식기 시작 되 고 모든 오디오 첫 번째 5 초 동안 듣지 못합니다, 시간 초과 됩니다.
  * 인식기에 결과 지정 하지만 다음 20 초 동안 대기를 시도해볼 경우 시간 초과 됩니다.
* 한 번에 하나만 유형의 인식기 (키워드 또는 받아쓰기) 실행할 수 있습니다.

>[!NOTE]
>합니다 **마이크** 마이크에서 녹음 하는 앱에 대 한 기능을 선언 해야 합니다. 이루어지는를 이미 MR 입력 212 하지만이 사용자의 프로젝트에 대 한 염두에 둡니다.
>
>1. Unity 편집기에서 "> 프로젝트 설정 > Player 편집"로 이동 하 여 플레이어 설정으로 이동 합니다.
>2. "유니버설 Windows 플랫폼" 탭을 클릭
>3. "게시 설정 > 기능" 섹션을 확인 합니다 **마이크** 기능

### <a name="instructions"></a>지침

편집 하겠습니다 **MicrophoneManager.cs** 받아쓰기 인식기를 사용 하려면. 다음은 내용을 추가할 것입니다.

1. 경우는 **Record 단추** 는 우리가 누른 **는 DictationRecognizer 시작**.
2. 표시 된 **가설** DictationRecognizer를 이해 하는 항목의 합니다.
3. 잠금 합니다 **결과** DictationRecognizer를 이해 하는 항목의 합니다.
4. DictationRecognizer에서 시간 제한을 확인 합니다.
5. 경우는 **중지 단추** 누를 mic 세션 시간이 초과 또는 **는 DictationRecognizer 중지**합니다.
6. 다시 시작 합니다 **KeywordRecognizer**, 대기할 합니다 **메시지 보내기** 명령입니다.

그럼 시작해 보겠습니다. 3.a에 대 한 모든 코딩 연습을 완료 **MicrophoneManager.cs**, 복사한 나와 완성 된 코드를 붙여 넣습니다.

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

* Visual Studio에서 다시 작성 하 고 장치에 배포 합니다.
* 어 탭 제스처를 사용 하 여 적합된 한 상자를 닫습니다.
* 그리고 고상한의 조사식 응시 *"Open Communicator"* 합니다.
* 선택 합니다 **레코드** 단추 (마이크) 메시지를 기록 합니다.
* 말을 시작 합니다. 합니다 **받아쓰기 인식기** 음성이 해석 되며는 communicator 가설된 텍스트를 표시 합니다.
* 라는 시도 *"메시지 보내기"* 메시지를 기록 하는 동안. 있음을 합니다 **키워드 인식기** 때문에 응답 하지 않습니다는 **받아쓰기 인식기** 여전히 활성 상태입니다.
* 몇 초 동안 읽어주기 중지 합니다. 받아쓰기 인식기 해당 가설을 완료 하 고 최종 결과 표시 하는 대로 시청 하세요.
* 말하기를 시작 하 고 20 초 동안 일시 중지 합니다. 그러면 합니다 **받아쓰기 인식기** 시간이 초과 합니다.
* 다음에 유의 합니다 **키워드 인식기** 위의 제한 시간이 지난 후 다시 사용 하도록 설정 됩니다. 음성 명령에 이제는 communicator 응답할 수 있습니다.
* 예를 들어 *"메시지 보내기"* 는 고상한에 메시지를 보내려고 합니다.

## <a name="chapter-4---grammar-recognizer"></a>4 장-문법 인식기

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>목표

* SRGS, 또는 음성 인식 문법을 사양 파일을 따라 사용자의 음성 인식 문법 인식기를 사용 합니다.

>[!NOTE]
>합니다 **마이크** 마이크에서 녹음 하는 앱에 대 한 기능을 선언 해야 합니다. 이루어지는를 이미 MR 입력 212 하지만이 사용자의 프로젝트에 대 한 염두에 둡니다.
>
>1. Unity 편집기에서 "> 프로젝트 설정 > Player 편집"로 이동 하 여 플레이어 설정으로 이동 합니다.
>2. "유니버설 Windows 플랫폼" 탭을 클릭
>3. "게시 설정 > 기능" 섹션을 확인 합니다 **마이크** 기능

### <a name="instructions"></a>지침

1. 에 **계층 구조** 패널에서 검색할 **Jetpack_Center** 선택 합니다.
2. 검색할 합니다 **태그가 있는 작업** 스크립트를 **검사기** 패널입니다.
3. 오른쪽의 작은 원을 클릭 합니다 **개체에 태그를 따라** 필드입니다.
4. 에 팝업 창에서 검색할 **SRGSToolbox** 목록에서 선택 합니다.
5. 살펴봅니다 합니다 **SRGSColor.xml** 파일을 **StreamingAssets** 폴더입니다.
* SRGS 디자인 사양은 W3C 웹 사이트에서 확인할 수 있습니다 [여기](https://www.w3.org/TR/speech-grammar/)합니다.
* SRGS 파일의 세 가지 유형의 규칙이 있습니다.
  * 12 개 색 목록에서 한 가지 색의 예를 들어 있는 규칙입니다.
  * 색 규칙 및 세 가지 셰이프 중 하나는 조합에 대 한 수신 대기 하는 세 가지 규칙입니다.
  * 루트 규칙을 colorChooser 세 가지 "색 + 셰이프" 규칙을 조합에 대 한 수신 대기 하는 합니다. 셰이프는 세 가지 모두를 하나만에서 모든 크기에 순서에 관계 없이 한다고 할 수 있습니다. 초기 파일의 맨 위에 있는 루트 규칙으로 지정 된 것에 대 한 수신 대기 하는 유일한 규칙이 이것이 &lt;문법&gt; 태그입니다.

### <a name="build-and-deploy"></a>빌드 및 배포

* Unity에서 응용 프로그램을 다시 작성 하 고 빌드 HoloLens에 앱을 Visual Studio에서 배포 합니다.
* 어 탭 제스처를 사용 하 여 적합된 한 상자를 닫습니다.
* 고상한의 jetpack에서 gaze 및 어 탭 제스처를 수행 합니다.
* 말을 시작 합니다. 합니다 **문법 인식기** 음성이 해석 되며 인식에 따라 모양의 색을 변경 합니다. 명령 예제는 "파란색 원, 노란색 사각형"입니다.
* 도구 상자를 해제 하려면 다른 어 탭 제스처를 수행 합니다.

## <a name="the-end"></a>끝

축하합니다. 이제 완료 **MR 입력 212: 음성**합니다.

* 음성 명령 일과 알 수 있습니다.
* 도구 설명 된 사용자 음성 명령을 인식 하도록 하기 위해 사용 하는 방법을 알아보았습니다.
* 여러 유형의 사용자의 음성 들어 본 적가 승인 하는 데 사용 되는 피드백 살펴보았습니다.
* 받아쓰기 인식기 및 키워드 인식기를 전환 하는 방법 및 이러한 두 기능 이해 하 고 의견을 해석 하는 방법을 알 수 있습니다.
* 응용 프로그램에서 음성 인식 용 SRGS 파일과 문법 인식기를 사용 하는 방법을 알아보았습니다.
