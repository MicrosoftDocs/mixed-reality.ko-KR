---
title: HoloLens 에뮬레이터 사용
description: HoloLens 에뮬레이터를 사용하면 실제 HoloLens 없이 PC에서 혼합 현실 앱을 테스트할 수 있습니다.
author: pbarnettms
ms.author: pbarnett
ms.date: 1/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: HoloLens, 에뮬레이터
ms.openlocfilehash: 7cbddae7cc5088bc8be7187e8b2dff3249e9d265
ms.sourcegitcommit: 542a481b00b36d92633c64a6189ea989551bab3d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76036460"
---
# <a name="using-the-hololens-emulator"></a>HoloLens 에뮬레이터 사용

HoloLens 에뮬레이터를 사용하면 실제 HoloLens 없이 PC에서 홀로그램 애플리케이션을 테스트할 수 있습니다. 또한 HoloLens 개발 도구 세트가 포함됩니다. 에뮬레이터는 Hyper-V 가상 머신을 사용합니다. 일반적으로 HoloLens 센서가 판독하는 휴먼 입력과 환경적 입력이 키보드, 마우스 또는 Xbox 컨트롤러를 통해 시뮬레이션됩니다. 에뮬레이터에서 실행하기 위해 애플리케이션을 수정할 필요가 없으며, 애플리케이션은 실제 HoloLens에서 실행되지 않는다는 걸 알지 못합니다.

데스크톱 PC용 Windows Mixed Reality 몰입형(VR) 헤드셋 애플리케이션이나 게임을 개발하려는 경우 데스크톱 헤드셋을 시뮬레이션할 수 있는 [Windows Mixed Reality 시뮬레이터](using-the-windows-mixed-reality-simulator.md)를 확인하세요.


## <a name="installing-the-hololens-emulator"></a>HoloLens 에뮬레이터 설치
HoloLens 에뮬레이터를 다운로드합니다.

버전: 
* [HoloLens 2 에뮬레이터(2020년 1월 업데이트)](https://go.microsoft.com/fwlink/?linkid=2114824).
* [HoloLens 에뮬레이터(1세대) 및 홀로그램 프로젝트 템플릿](https://go.microsoft.com/fwlink/?linkid=2065980).

HoloLens 에뮬레이터의 릴리스 정보 및 이전 빌드는 [HoloLens 에뮬레이터 아카이브](hololens-emulator-archive.md) 페이지에서 찾을 수 있습니다.

### <a name="hololens-emulator-system-requirements"></a>HoloLens 에뮬레이터 시스템 요구 사항

HoloLens 에뮬레이터는 하드웨어 가속 그래픽에는 RemoteFx(1세대 에뮬레이터) 또는 GPU-PV(HoloLens 2 에뮬레이터)와 함께 Hyper-V를 사용합니다. 에뮬레이터를 사용하려면 PC가 다음과 같은 하드웨어 요구 사항을 충족하는지 확인합니다.
* 64비트 Windows 10 Pro, Enterprise 또는 Education 
    >[!NOTE]
    >Windows 10 Home 버전은 Hyper-V 또는 HoloLens 에뮬레이터를 지원하지 않습니다.  
    >HoloLens 2 에뮬레이터의 경우 Windows 10 2018년 10월 업데이트 이상이 필요합니다.
* 64비트 CPU
* 4코어의 CPU(또는 총 4코어를 사용하는 다중 CPU)
* RAM 8GB 이상
* BIOS에서 다음 기능이 [지원되어야 하며, 사용하도록 설정되어야 합니다](https://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx).
   * 하드웨어 지원 가상화
   * SLAT(Second Level Address Translation)
   * 하드웨어 기반 DEP(데이터 실행 방지)
* GPU 요구 사항
   * DirectX 11.0 이상
   * WDDM 1.2 그래픽 드라이버 이상(1세대)
   * WDDM 2.5 그래픽 드라이버(HoloLens 2 에뮬레이터)
   * 에뮬레이터는 지원되지 않는 GPU에서 작동할 수 있으나 성능이 크게 저하됩니다.

시스템이 위의 요구 사항을 충족하는 경우 제어판 -> 프로그램 -> 프로그램 및 기능 -> Windows 기능 켜기 또는 끄기에서 -> 에뮬레이터가 성공적으로 설치되도록 “Hyper-V”가 선택되어 있는지 확인하여 **“Hyper-V” 기능이 시스템에서 사용하도록 설정되어 있는지 확인합니다**.

## <a name="deploying-apps-to-the-hololens-emulator"></a>HoloLens 에뮬레이터에 앱 배포

1. Visual Studio에서 애플리케이션 솔루션을 로드합니다.
    >[!NOTE]
    >Unity를 사용하는 경우, 평소처럼 Unity에서 프로젝트를 빌드한 다음, 빌드된 솔루션을 Visual Studio에 로드합니다.
2. HoloLens 에뮬레이터(1세대)의 경우 플랫폼이 **x86**으로 설정되었는지 확인합니다. HoloLens 2 에뮬레이터의 경우 플랫폼이 **x86** 또는 **x64**로 설정되었는지 확인합니다.
3. 디버깅에 대한 대상 디바이스로 원하는 **HoloLens 에뮬레이터** 버전을 선택합니다.
4. **디버그 > 디버깅 시작**으로 이동하거나, **F5** 키를 눌러 에뮬레이터를 시작하고 디버깅을 위해 애플리케이션을 배포합니다.

에뮬레이터는 처음 시작할 때 부팅하는 데 1분 이상 걸릴 수 있습니다. 디버깅 세션 중에 에뮬레이터를 열어 두는 것이 좋습니다. 그래야 에뮬레이터에 애플리케이션을 신속하게 배포할 수 있습니다.

## <a name="basic-emulator-input"></a>기본 에뮬레이터 입력

에뮬레이터를 제어하는 것은 많은 일반적인 3D 비디오 게임과 매우 비슷합니다. 입력 옵션은 키보드, 마우스 또는 Xbox 컨트롤러 사용 시 이용할 수 있습니다. HoloLens를 착용한 시뮬레이션된 사용자의 작업을 지시하여 에뮬레이터를 제어합니다. 사용자의 작업은 시뮬레이트된 사용자를 환경 주위로 이동합니다. 에뮬레이터에서 실행되는 애플리케이션은 실제 디바이스에서와 같이 응답합니다.

HoloLens(1세대)의 커서는 헤드 이동 및 회전을 따릅니다. HoloLens 2 에뮬레이터에서는 커서가 손 이동 및 방향을 따릅니다.

* **앞으로, 뒤로, 왼쪽 및 오른쪽으로 걷기** - 키보드의 W, A, S 및 D 키 또는 Xbox 컨트롤러의 왼쪽 스틱을 사용합니다.
* **위, 아래, 왼쪽 및 오른쪽 보기** - 마우스를 클릭하여 끌거나, 키보드의 화살표 키 또는 Xbox 컨트롤러의 오른쪽 스틱을 사용합니다.
* **에어 탭 동작** - 마우스 오른쪽 단추를 클릭하거나, 키보드에서 Enter 키를 누르거나, Xbox 컨트롤러의 A 단추를 사용합니다.
* **블룸/시스템 동작** - 키보드에서 Windows 키나 F2 키를 누르거나 Xbox 컨트롤러의 B 단추를 누릅니다.
* **스크롤하기 위한 손 동작** - Alt 키를 누른 채로 마우스 오른쪽 단추를 누르면서 위쪽/아래쪽으로 마우스를 끌거나, Xbox 컨트롤러에서 오른쪽 트리거 및 A 단추를 아래로 유지하고 오른쪽 스틱을 위아래로 이동합니다.
* **손 이동 및 방향**(HoloLens 2 에뮬레이터만 해당) - Alt 키를 누른 채 마우스를 위나 아래, 왼쪽이나 오른쪽으로 끌어 손을 이동하거나, 화살표 키 및 Q 또는 E를 사용하여 손을 회전하고 기울입니다. Xbox 컨트롤러의 경우 왼쪽 또는 오른쪽 범퍼를 누른 채로 왼쪽 엄지스틱을 사용하여 손을 왼쪽, 오른쪽, 앞으로, 뒤로 움직입니다. 오른쪽 엄지스틱을 사용하여 회전시키고 Dpad에서 위쪽 또는 아래쪽으로 움직여 손을 들거나 내립니다.

## <a name="anatomy-of-the-hololens-2-emulator"></a>HoloLens 2 에뮬레이터의 구조 

### <a name="main-window"></a>기본 창

![HoloLens 2 에뮬레이터 기본 창](images/emulator2-900px.png)

### <a name="toolbar"></a>도구 모음

기본 창의 오른쪽에는 에뮬레이터 도구 모음이 있습니다. 도구 모음에는 다음과 같은 단추가 포함됩니다.
* ![닫기 아이콘](images/emulator-close.png) **닫기**: 에뮬레이터를 닫습니다.
* ![최소화 아이콘](images/emulator-minimize.png) **최소화**: 에뮬레이터 창을 최소화합니다.
* ![시뮬레이션 아이콘](images/emulator-simulation-panel.png) **시뮬레이션 제어판**: [에뮬레이터에 대한 입력](#basic-emulator-input)을 구성하거나 제어하기 위해 [시뮬레이션 제어판](#simulation-control-panel)을 표시하거나 숨깁니다.
* ![화면에 맞추기 아이콘](images/emulator-fit.png) **화면에 맞추기**: 에뮬레이터를 화면에 맞춥니다.
* ![확대/축소 아이콘](images/emulator-zoom.png) **확대/축소**: 에뮬레이터를 크거나 작게 합니다.
* ![도움말 아이콘](images/emulator-help.png) **도움말**: 에뮬레이터 도움말을 엽니다.
* ![디바이스 포털 열기 아이콘](images/emulator-deviceportal.png) **디바이스 포털 열기**: 에뮬레이터에서 HoloLens OS용 Windows 디바이스 포털을 엽니다.
* ![도구 아이콘](images/emulator-tools.png) **도구**: **추가 도구** 창을 엽니다.

### <a name="simulation-control-panel"></a>시뮬레이션 제어판

시뮬레이션 제어판을 사용하면 시뮬레이션된 휴먼 및 입력 디바이스의 현재 위치와 방향을 볼 수 있습니다. 또한 한 손이나 두 손을 표시하거나 숨기는 것과 같은 시뮬레이션된 입력과 PC의 키보드, 마우스, 게임 패드와 같은 시뮬레이션된 입력을 제어하는 데 사용되는 디바이스 모두를 구성할 수 있습니다.

![시뮬레이션 제어판](images/emulator-simulation-control-panel.png)

* 시뮬레이션 패널을 표시하거나 숨기려면 도구 모음 단추를 클릭하거나 키보드에서 F7 키를 누릅니다.
* 컨트롤 또는 필드 위에 마우스 커서를 올리면 키보드, 마우스 및 게임 패드 컨트롤이 포함된 도구 설명이 표시됩니다.
* 손을 표시하거나 숨기려면 왼손 또는 오른손 아래에 있는 적절한 스위치를 전환합니다.
* 손을 제어하려면 키보드의 왼쪽 또는 오른쪽 Alt 키나 게임 패드의 왼쪽 또는 오른쪽 범퍼를 사용합니다.
* 모든 입력을 한 손 또는 두 손 모두에 연결하려면 토글 스위치 아래의 고정핀 단추를 클릭합니다. 이것은 해당 손에 대해 Alt 키를 누른 것과 같습니다.
* 응시 방향을 제어하려면 눈 섹션의 고정핀을 클릭합니다. 이것은 키보드에서 ‘Y’ 키를 누른 것과 같습니다.
* 공간 기록을 로드하려면 기록 섹션의 로드 단추를 클릭합니다. 자세한 내용은 [시뮬레이션된 공간](#simulated-rooms)을 참조하세요.
* 키보드, 마우스 또는 게임 패드 입력에 따라 시뮬레이션된 휴먼 또는 입력 디바이스가 이동하거나 회전하는 속도를 조정하려면 입력 설정 옆의 기어 아이콘을 클릭하고 슬라이더를 조정합니다.
* 기본적으로 키보드 입력은 시뮬레이션된 휴먼과 시뮬레이션된 입력을 제어합니다. PC의 키보드 입력이 HoloLens를 통해 전송되도록 하려면 시뮬레이션에 키보드 사용 선택을 취소합니다. F4 키는 이 설정에 대한 바로 가기 키입니다.
* 시뮬레이션 패널이 이미 표시되어 있는 경우 F8 키를 누르면 키보드 포커스가 이동합니다.
* 에뮬레이터 창에서 시뮬레이션 패널의 도킹을 해제하려면 패널의 맨 아래에 있는 단추를 클릭하거나 키보드에서 F9 키를 누릅니다.  창을 닫거나 F9 키를 다시 누르면 창이 에뮬레이터로 돌아갑니다.
* 시뮬레이션 제어판은 별도의 애플리케이션으로 시작할 수 있으므로 %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\10.0.18362.0\에서 PerceptionSimulationInput.exe를 실행하여 HoloLens 2 에뮬레이터, HoloLens 2 디바이스 또는 Windows Mixed Reality 시뮬레이션을 연결하고 제어할 수 있습니다.

### <a name="account-tab"></a>계정 탭

계정 탭을 사용하면 Microsoft 계정으로 로그인하도록 에뮬레이터를 구성할 수 있습니다. 이것은 사용자가 계정에 로그인해야 하는 API를 테스트할 때 유용합니다. 이 옵션을 설정/해제하려면 설정이 적용되도록 HoloLens 에뮬레이터를 완전히 닫고 다시 시작해야 합니다. 이 옵션을 사용하도록 설정하면 사용자가 HoloLens를 처음 시작할 때와 마찬가지로 이후에 에뮬레이터를 시작할 때 로그인할지 묻는 메시지가 나타납니다. PC의 키보드를 사용하여 자격 증명을 입력하려면 먼저 시뮬레이션 제어판에서 시뮬레이션에 키보드 사용을 끄거나, 키보드에서 F4 키를 눌러 키보드 설정을 켜거나 끄도록 전환합니다.

### <a name="optional-settings-tab"></a>선택적 설정 탭

선택적 설정 탭에는 하드웨어 가속 그래픽을 사용하거나 사용하지 않도록 설정하는 컨트롤이 표시됩니다. 하드웨어 가속 그래픽은 PC의 그래픽 어댑터 드라이버에서 지원되는 경우 기본적으로 사용됩니다. 그래픽 어댑터의 드라이버가 GPU-PV를 지원하지 않으면 이 옵션은 표시되지 않습니다.

### <a name="diagnostics-tab"></a>진단 탭

진단 탭에는 가상 GPU의 상태와 함께 에뮬레이터의 IP 주소가 Windows 디바이스 포털에 대한 링크 형태로 표시됩니다.

### <a name="network-tab"></a>네트워크 탭

네트워크 탭에는 에뮬레이터의 네트워크 어댑터 세부 정보는 물론 호스트 머신의 네트워크 어댑터 세부 정보가 표시됩니다. HoloLens 2 에뮬레이터의 경우, Windows 10 2019년 5월 업데이트 이상에서 에뮬레이터를 실행하는 경우에만 이 탭이 표시됩니다.

### <a name="nat-configuration-tab"></a>NAT 구성 탭

Windows 10 2019년 5월 업데이트 이상에서 에뮬레이터를 실행하는 경우에만 이 탭이 표시됩니다.

에뮬레이터는 PC의 네트워크 연결을 사용하고 NAT 뒤에 위치합니다.  이 탭을 사용하면 호스트 PC의 포트를 에뮬레이터에 매핑할 수 있습니다. 그러면 원격 디바이스가 에뮬레이터에서 실행되는 애플리케이션과 서비스에 연결될 수 있습니다.

예를 들어 원격 PC의 에뮬레이터에서 디바이스 포털에 액세스하려면 다음을 수행합니다.

1. 테이블에서 빈 행을 두 번 클릭하여 내부 포트 80(디바이스 포털이 수신 대기하는 포트)에 대한 항목을 추가합니다.  다른 애플리케이션의 경우 해당 애플리케이션이 수신 대기하는 포트 번호를 입력합니다.
2. 사용 가능한 외부 포트를 선택합니다.  이 예제에서는 포트 8080을 외부 포트로 사용합니다.
3. 프로토콜을 선택합니다.  기본값은 TCP입니다.  디바이스 포털은 TCP를 사용하므로 기본값을 그대로 둡니다.
4. "변경 내용 적용"을 클릭하여 매핑을 활성화합니다.  '상태'가 '보류'에서 '활성'으로 변경됩니다.
5. 원격 PC에서 브라우저를 열고 (IP-of-the-PC-running-the-emulator):8080으로 이동합니다.  디바이스 포털 인터페이스가 표시됩니다.  원격 PC에서 사용하는 IP 주소는 에뮬레이터 자체가 아닌 에뮬레이터를 실행하는 PC의 IP 주소여야 합니다.  IP는 다양한 방법으로 검색할 수 있습니다. 예를 들어, '네트워크 및 인터넷' 범주에 있는 PC의 설정 앱, 명령 프롬프트의 'ipconfig', 데스크톱 어댑터 항목을 찾아서 에뮬레이터 도구 대화 상자의 네트워크 탭과 같은 다양한 방법이 있습니다.

디바이스 포털에 대한 포트 매핑을 추가하는 경우, 에뮬레이터 설치에 포함된 인식 시뮬레이션 컨트롤 도구를 사용하거나, 호스트 PC의 IP 주소 및 디바이스 포털 외부 포트(위 예시의 경우 8080)에 연결하여 인식 시뮬레이션 API를 통해 에뮬레이터를 원격으로 제어할 수도 있습니다.  인식 시뮬레이션 컨트롤을 사용하여 에뮬레이터에 원격으로 연결하고 제어하는 경우에는, PC의 IP 주소와 구성된 포트만 지정합니다.  'https://'는 포함하지 마십시오.

기본적으로 포트 매핑이 없습니다.  매핑을 구성하면 HoloLens 2 에뮬레이터를 시작해도 계속 유지되며 에뮬레이터가 완전히 부팅되면 자동으로 활성화됩니다.

'내보내기' 단추를 사용하여 매핑을 파일에 저장합니다.  그러면, '가져오기' 단추를 사용하여 동일한 매핑을 자동으로 구성할 수 있는 다른 팀 구성원과 이 파일을 공유 할 수 있습니다.

![HoloLens 에뮬레이터 'NAT 구성' 탭](images/emulator-natconfig-500px.png)

### <a name="updates-tab"></a>업데이트 탭

Windows 10 2019년 5월 업데이트 이상에서 에뮬레이터를 실행하는 경우에만 이 탭이 표시됩니다.

시작 시 에뮬레이터는 새 버전을 확인합니다.  새 버전을 사용할 수 있는 경우, 에뮬레이터에 사용 중인 버전과 사용 가능한 버전이 보이고 업데이트 여부를 묻는 메시지가 표시됩니다.  '예'를 선택하면 새 버전의 설치 관리자가 다운로드됩니다.

업데이트 탭에서는 에뮬레이터가 새 버전을 확인할지 여부를 제어할 수 있습니다. "자동으로 업데이트 확인" 확인란을 선택/해제하면 됩니다.  사용 가능한 다른 에뮬레이터 버전(2019년 9월 업데이트부터)을 살펴보고 다운로드할 수도 있습니다.  현재 실행하는 버전이 아닌 다른 버전에는 다운로드 링크가 제공됩니다.  이 링크를 클릭하면 해당 버전의 설치 관리자가 다운로드됩니다.

![HoloLens 에뮬레이터 ‘업데이트’ 탭](images/emulator-updates-500px.png)


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>HoloLens(1세대) 에뮬레이터의 구조

### <a name="main-window"></a>기본 창

에뮬레이터를 시작하면 HoloLens OS를 표시하는 창이 나타납니다.

![HoloLens 에뮬레이터 기본 창](images/emulator-890px.png)

### <a name="toolbar"></a>도구 모음

기본 창의 오른쪽에는 에뮬레이터 도구 모음이 있습니다. 도구 모음에는 다음과 같은 단추가 포함됩니다.
* ![닫기 아이콘](images/emulator-close.png) **닫기**: 에뮬레이터를 닫습니다.
* ![최소화 아이콘](images/emulator-minimize.png) **최소화**: 에뮬레이터 창을 최소화합니다.
* ![휴먼 입력 아이콘](images/emulator-control.png) **휴먼 입력**: [에뮬레이터에 대한 휴먼 입력](#basic-emulator-input)을 시뮬레이션하는 데 마우스 및 키보드가 사용됩니다.
* ![키보드 및 마우스 입력 아이콘](images/emulator-input.png) **키보드 및 마우스 입력**: Bluetooth 키보드와 마우스를 연결했을 때와 동일하게 키보드 및 마우스 입력이 키보드 및 마우스 이벤트로 HoloLens OS에 직접 전달됩니다.
* ![화면에 맞추기 아이콘](images/emulator-fit.png) **화면에 맞추기**: 에뮬레이터를 화면에 맞춥니다.
* ![확대/축소 아이콘](images/emulator-zoom.png) **확대/축소**: 에뮬레이터를 크거나 작게 합니다.
* ![도움말 아이콘](images/emulator-help.png) **도움말**: 에뮬레이터 도움말을 엽니다.
* ![디바이스 포털 열기 아이콘](images/emulator-deviceportal.png) **디바이스 포털 열기**: 에뮬레이터에서 HoloLens OS용 Windows 디바이스 포털을 엽니다.
* ![도구 아이콘](images/emulator-tools.png) **도구**: **추가 도구** 창을 엽니다.

### <a name="simulation-tab"></a>시뮬레이션 탭

**추가 도구** 창 내 기본 탭은 **시뮬레이션** 탭입니다.

![HoloLens 에뮬레이터 ‘추가 도구’ 창](images/emulator-simulation-500px.png)

시뮬레이션 탭에는 에뮬레이터 내에서 HoloLens OS를 구동하는 데 사용된 시뮬레이트된 센서의 현재 상태가 표시됩니다. 시뮬레이션 탭에 있는 아무 값에나 마우스 커서를 올리면 해당 값을 제어하는 방법을 설명하는 도구 설명이 제공됩니다.

### <a name="room-tab"></a>공간 탭

에뮬레이터는 시뮬레이트된 공간에서 공간적 매핑 메시의 형태로 세계 입력을 시뮬레이션합니다. 이 탭에서는 기본 공간을 대신하여 로드할 공간을 선택할 수 있습니다.

![HoloLens 에뮬레이터 ‘공간’ 탭](images/emulator-room-500px.png)

자세한 내용은 [시뮬레이션된 공간](#simulated-rooms)을 참조하세요.

### <a name="account-tab"></a>계정 탭

계정 탭을 사용하면 Microsoft 계정으로 로그인하도록 에뮬레이터를 구성할 수 있습니다. 이것은 사용자가 계정에 로그인해야 하는 API를 테스트할 때 유용합니다. 이 페이지의 상자를 선택하면 사용자가 HoloLens를 처음 시작할 때와 마찬가지로 이후에 에뮬레이터를 시작할 때 로그인할지 묻는 메시지가 나타납니다.

## <a name="simulated-rooms"></a>시뮬레이션된 공간

시뮬레이션된 공간은 여러 환경에서 애플리케이션을 테스트하는 데 유용합니다. 에뮬레이터와 함께 여러 공간이 제공됩니다. 에뮬레이션을 설치한 후 %ProgramFiles(x86)%\Windows Kits\10\Microsoft XDE\\(version)\Plugins\Rooms에서 찾을 수 있습니다. 이러한 모든 공간은 HoloLens를 사용하여 실제 환경에서 캡처되었습니다.
* **DefaultRoom.xef** - TV, 커피 테이블과 두 개의 소파가 있는 작은 거실. 에뮬레이터를 시작할 때 기본적으로 로드됩니다.
* **Bedroom1.xef** - 책상이 있는 작은 침실.
* **Bedroom2.xef** - 퀸 크기 침대, 장농, 협탁 및 벽장이 있는 침실.
* **GreatRoom.xef** - 거실, 식탁 및 주방이 있는 대규모 공간.
* **LivingRoom.xef** - 벽난로, 소파, 안락의자 및 꽃병이 놓인 커피 테이블이 있는 거실.

또한 HoloLens(1세대)에서 [Windows 디바이스 포털](using-the-windows-device-portal.md)의 시뮬레이션 페이지를 사용하여 에뮬레이터에서 사용할 자신의 공간을 기록할 수 있습니다.

에뮬레이터에서 렌더링하는 홀로그램만 표시됩니다. 그러나 시뮬레이션된 공간은 홀로그램 뒤에 표시 되지 않습니다. 이것은 두 가지가 함께 혼합되어 보이는 실제 HoloLens와는 대조적입니다. HoloLens 에뮬레이터에서 시뮬레이트된 공간을 보려면 장면에서 공간적 매핑 메시를 렌더링하도록 애플리케이션을 업데이트해야 합니다.

## <a name="troubleshooting"></a>문제 해결

에뮬레이터를 설치하는 동안 *“Visual Studio 2015 업데이트 1 및 UWP 도구 버전 1.2”* 가 필요하다고 알리는 오류 메시지가 표시될 수 있습니다. 이 오류의 가능한 세 가지 원인은 다음과 같습니다.
* Visual Studio 버전이 최신이 아닙니다(Visual Studio 2019, Visual Studio 2017 또는 Visual Studio 2015 업데이트 1 이상). 이를 해결하려면 Visual Studio의 최신 릴리스를 설치합니다.
* Visual Studio의 최신 버전이 있지만, UWP(유니버설 Windows 플랫폼) 도구가 설치되어 있지 않습니다. 이것은 Visual Studio에 대한 선택적 기능입니다.

또한 Windows Pro/Enterprise/Education SKU 외에 에뮬레이터를 설치할 때 또는 Hyper-V 기능을 사용하도록 설정하지 않은 경우에도 오류가 나타날 수 있습니다.
* 전체 요구 사항 세트에 대해 위에 나온 [시스템 요구 사항](#hololens-emulator-system-requirements) 섹션을 읽어보세요.
* 또한 시스템에서 Hyper-V 기능이 사용하도록 설정되어 있는지 확인하세요.

설치를 성공적으로 완료했지만 HoloLens 에뮬레이터가 배포 및 디버깅에 대한 옵션으로 표시되지 않으면 다음 사항을 확인하세요.
* Visual Studio 프로젝트 구성이 x86(HoloLens 1세대), x86 또는 x64(HoloLens 2 에뮬레이터)로 설정되어 있습니다.
* Visual Studio 2019를 사용하는 경우 프로젝트 구성의 플랫폼 도구 집합이 v142로 설정되어 있습니다.

설치를 성공적으로 완료했지만 Visual Studio에서 HoloLens 에뮬레이터를 시작하는 동안 오류가 표시되는 경우 다음을 시도하세요.
* 관리자 권한으로 Visual Studio 실행
* Visual Studio 2019만 설치한 경우 HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed Roots의 “KitsRoot10” 레지스트리 값이 사용자의 32비트 프로그램 파일 폴더(예: “C:\Program Files(x86)\Windows Kits\10”)를 가리키는지 확인합니다.  그렇지 않은 경우, HoloLens 에뮬레이터를 제거하고, 레지스트리 값을 32비트 프로그램 파일 폴더로 변경한 다음, HoloLens 에뮬레이터를 다시 설치합니다.  이 문제는 Visual Studio 2019 16.0.3에서 해결되었습니다.

에뮬레이터에서 시작 시 “잘못된 바이트 인코딩” 오류 대화 상자가 표시되는 경우 다음을 수행합니다.
* %localappdata%\Microsoft\XDE\HCS의 모든 파일을 삭제하고 다시 시도합니다.

Visual Studio의 디버그 대상 목록이 비어 있고(예를 들어, 시작이 유일한 옵션) 위의 모든 문제 해결 단계를 수행한 경우 다음을 수행합니다.
* %localappdata%\Microsoft\VisualStudio\\<*installation id*>\CoreCon에서 ConfigurationCache 폴더를 삭제하고 다시 시도합니다.

에뮬레이터가 시작될 때 시스템이 중지되면 에뮬레이터 그래픽에 대한 하드웨어 가속을 사용하지 않도록 설정합니다.
* HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0에서 “DisableGPU”라는 레지스트리 DWORD 값을 만들고 해당 값을 1로 설정합니다.

## <a name="see-also"></a>참고 항목
* [고급 HoloLens 에뮬레이터 및 Mixed Reality 시뮬레이터 입력](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens 에뮬레이터 소프트웨어 기록](hololens-emulator-archive.md)
* [Unity의 공간 매핑](spatial-mapping-in-unity.md)
* [DirectX의 공간 매핑](spatial-mapping-in-directx.md)
