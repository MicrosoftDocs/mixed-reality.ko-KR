---
title: HoloLens 에뮬레이터를 사용 하 여
description: HoloLens 에뮬레이터를 사용 하면 실제 HoloLens 하지 않고 PC에서 혼합된 현실 앱을 테스트할 수 있습니다.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: HoloLens, 에뮬레이터
ms.openlocfilehash: 0a8fa6bb7c7c5bb846604b7a1878911f028d8cba
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580650"
---
# <a name="using-the-hololens-emulator"></a>HoloLens 에뮬레이터를 사용 하 여

HoloLens 에뮬레이터 실제 HoloLens 하지 않고 PC에서 holographic 앱을 테스트할 수 있습니다 및 HoloLens 개발 도구 집합과 함께 제공 됩니다. 에뮬레이터는 Hyper-v 가상 컴퓨터를 사용합니다. 일반적으로 HoloLens에 센서에서 읽을 수 있는 사람과 환경 입력 키보드, 마우스, 또는 Xbox 컨트롤러를 사용 하 여 시뮬레이션 대신 됩니다. 에뮬레이터에서 실행을 수정할 필요가 없습니다 프로그램과 알지 들 실제 HoloLens에서 실행 되지 않습니다.

데스크톱 Pc에 대 한 Windows Mixed Reality 몰입 형 (VR) 헤드셋 앱 또는 게임을 개발 하려는 경우 체크 아웃 합니다 [Windows Mixed Reality 시뮬레이터](using-the-windows-mixed-reality-simulator.md), 대신 데스크톱 헤드셋을 시뮬레이션할 수 있습니다.


## <a name="installing-the-hololens-emulator"></a>HoloLens 에뮬레이터 설치
HoloLens 에뮬레이터 및 holographic 프로젝트 템플릿을 다운로드 합니다.

버전: 
* [HoloLens 2 에뮬레이터 및 holographic 프로젝트 템플릿](https://go.microsoft.com/fwlink/?linkid=2087187)합니다.
* [HoloLens 에뮬레이터 (첫 번째 Gen) 및 holographic 프로젝트 템플릿](https://go.microsoft.com/fwlink/?linkid=2065980)합니다.

HoloLens 에뮬레이터의 이전 빌드를 찾을 수 있습니다 합니다 [HoloLens 에뮬레이터 아카이브](hololens-emulator-archive.md) 페이지입니다.

### <a name="hololens-emulator-system-requirements"></a>HoloLens 에뮬레이터 시스템 요구 사항

HoloLens 에뮬레이터에서 Hyper-v를 사용 하 여 RemoteFx를 사용 하 여 (첫 번째 Gen 에뮬레이터) 또는 GPU-PV (HoloLens 2 에뮬레이터) 하드웨어 가속 그래픽입니다. 에뮬레이터를 사용 하려면 PC에 이러한 하드웨어 요구 사항을 충족 하는지 확인 합니다.
* 64 비트 Windows 10 Pro, Enterprise 또는 교육 
    >[!NOTE]
    >Windows 10 Home edition에는 Hyper-v 또는 HoloLens 에뮬레이터를 지원 하지 않습니다.  
    >HoloLens 2 에뮬레이터는 Windows 10 년 10 월 2018 update 필요 이상.
* 64비트 CPU
* CPU 코어 4 개 (또는 총 코어 수 4 개를 사용 하 여 여러 Cpu)
* 8GB RAM 이상
* BIOS에서 다음 기능 이어야 합니다 [지원 하 고 사용 하도록 설정](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * 하드웨어 지원 가상화
   * SLAT(Second Level Address Translation)
   * 하드웨어 기반 DEP(데이터 실행 방지)
* GPU 요구 사항
   * DirectX 11.0 이상
   * WDDM 1.2 그래픽 드라이버 또는 이후 (Gen 1 일)
   * WDDM 2.5 그래픽 드라이버 (HoloLens 2 에뮬레이터)
   * 에뮬레이터는 지원 되지 않는 GPU에서 작동 하지만 성능이 크게 저하 됩니다.

시스템에는 위의 요구 사항을 충족 하는 경우 **시스템에서 "하이퍼-V" 기능이 설정 되어 있는지를 확인 하세요** 제어판을 통해-> 프로그램-> 프로그램 및 기능에서-> Windows 기능 설정 또는 해제-> 확인 찾기가 성공 하려면 에뮬레이터 설치에 대 한 해당 "하이퍼-V" 선택 됩니다.

## <a name="deploying-apps-to-the-hololens-emulator"></a>HoloLens 에뮬레이터에 앱 배포

1. Visual Studio에서 앱 솔루션을 로드 합니다.
    >[!NOTE]
    >Unity를 사용 하면 Unity에서 프로젝트를 빌드할 한 다음 빌드된 솔루션이 Visual Studio를 정상적으로 로드 합니다.
2. HoloLens 에뮬레이터 (첫 번째 Gen) 플랫폼으로 설정 되었는지 확인 **x86**합니다. HoloLens 2 에뮬레이터 확인 플랫폼에 대 한로 설정 되어 **x86** 하거나 **x64**합니다.
3. 원하는 **HoloLens 에뮬레이터** 디버깅에 대 한 대상 장치로 버전입니다.
4. 로 이동 **디버그 > 디버깅 시작** 누르거나 **F5** 에뮬레이터를 시작 하 여 디버깅을 위해 앱을 배포 합니다.

에뮬레이터는 1 분 이상 처음 시작할 때 부팅 걸릴 수 있습니다. 열어 에뮬레이터 디버깅 세션 중 실행 중인 에뮬레이터에 앱을 신속 하 게 배포할 수 있습니다 있도록 하는 것이 좋습니다.

## <a name="basic-emulator-input"></a>기본 에뮬레이터 입력

에뮬레이터를 제어 하는 것은 많은 일반적인 3D 비디오 게임 매우 비슷합니다. 키보드, 마우스 또는 Xbox 컨트롤러를 사용 하 여 사용할 수는 입력된 옵션이 있습니다. HoloLens 착용 시뮬레이션된 된 사용자의 동작을 지시 하 여 에뮬레이터를 제어 합니다. 작업 관련 시뮬레이션 된 사용자와 에뮬레이터에서 실행 되는 앱이 실제 장치에서 하 듯는 응답을 이동 합니다.

HoloLens에 커서를 헤드 이동 및 회전 (첫 번째 범용)을 따릅니다.  HoloLens 2 에뮬레이터에서 커서에 손 모양 이동 및 방향을 따릅니다.

* **앞으로, 다시을 유지 하 고 마우스 오른쪽 단추로** -W, 사용 하 여 키보드 또는 Xbox 컨트롤러에 왼쪽된 메모리에서 A, S, D 키입니다.
* **조회할 아래, 왼쪽 및 오른쪽** -클릭 하 고 마우스를 끌어 키보드 또는 Xbox 컨트롤러에 올바른 메모리에서 화살표 키를 사용 합니다.
* **어 탭 제스처** -마우스, 키보드에서 Enter 키를 눌러 또는 Xbox 컨트롤러에는 단추를 사용 합니다.
* **블 룸/시스템 제스처** -키보드에서 Windows 키나 F2 키를 눌러 또는 Xbox 컨트롤러 B 단추를 누릅니다.
* **스크롤 하는 것에 대 한 이동을 제공할** -Alt 키를 누른 채로 마우스 오른쪽 단추 및 위쪽 / 아래쪽에 마우스를 끌어 또는 Xbox 컨트롤러를에서 오른쪽 트리거와 단추 누른 오른쪽 스틱을 위아래로 이동 합니다.
* **이동 및 방향 전달** Alt 키를 누른 채로 및 위쪽 / 아래쪽 / 왼쪽 / 오른쪽 손 모양으로 이동 하려면 마우스를 끌기 또는 화살표 키와 질문 및 답변 사용 (HoloLens 2 에뮬레이터만 해당)-/ 회전 및 기울기 손 모양 아이콘이 E입니다.  Xbox 컨트롤러에 대 한 왼쪽 또는 오른쪽 범퍼 보유 하 고, 회전 및 위쪽 / 아래쪽를 손 모양 아이콘이 올리거나 Dpad에는 왼쪽된 엄지 스틱 왼쪽 / 오른쪽 / 전달 / 백, 손 모양 아이콘이 이동 하려면 오른쪽 엄지 사용 합니다.

## <a name="anatomy-of-the-hololens-2-emulator"></a>HoloLens 2 에뮬레이터의 분석 

### <a name="main-window"></a>주 창

![HoloLens 2 에뮬레이터 주 창](images/emulator2-900px.png)

### <a name="toolbar"></a>도구 모음

주 창의 오른쪽에는 에뮬레이터 도구 모음을 찾을 수 있습니다. 도구 모음에 다음 단추가 포함 됩니다.
* ![닫기 아이콘](images/emulator-close.png) **닫기**: 에뮬레이터를 닫습니다.
* ![최소화 아이콘](images/emulator-minimize.png) **최소화**: 에뮬레이터 창을 최소화합니다.
* ![Simulation_icon](images/emulator-simulation-panel.png) **시뮬레이션 제어판**: 표시 하거나 숨길 합니다 [시뮬레이션 Control panel](#simulation-control-panel) 구성 및 제어에 대 한 [에뮬레이터에 대 한 입력](#basic-emulator-input).
* ![화면에 맞춤 아이콘](images/emulator-fit.png) **화면에 맞추기**: 에뮬레이터를 화면에 맞춥니다.
* ![확대/축소 아이콘](images/emulator-zoom.png) **확대/축소**: 크고 작은 에뮬레이터를 확인 합니다.
* ![도움말 아이콘](images/emulator-help.png) **도움말**: 에뮬레이터 도움말을 엽니다.
* ![열린 장치 포털 아이콘](images/emulator-deviceportal.png) **장치 포털 열기**: 에뮬레이터에서 HoloLens OS에 대 한 Windows Device Portal 엽니다.
* ![도구 아이콘](images/emulator-tools.png) **도구**: 엽니다는 **추가 도구** 창입니다.

### <a name="simulation-control-panel"></a>시뮬레이션 제어판

시뮬레이션 제어판을 사용 하면 현재 위치와 방향을 사람과 시뮬레이션 입력 시뮬레이션 된 장치를 볼 수 있습니다.  또한 표시 또는 숨기기 손, 및 PC의 키보드, 마우스 및 gamepad 같은 시뮬레이션 된 입력 제어에 사용 되는 장치를 하나 또는 둘 다 같은 시뮬레이션 된 두 입력을 구성할 수 있습니다.

![시뮬레이션 제어판](images/emulator-simulation-control-panel.png)

* 시뮬레이션 패널을 표시 하거나 숨길, 도구 모음 단추를 클릭 또는 키보드에서 F7 키를 누릅니다.
* 컨트롤 또는 해당 키보드, 마우스 및 gamepad 컨트롤을 포함 하는 도구 설명을 표시할 필드 위로 마우스를 이동 합니다.
* 을 표시 하거나 숨기려면 손 모양 왼쪽 또는 오른쪽 아래에서 적절 한 스위치를 전환 합니다.
* 손 모양 아이콘이 제어 하려면 키보드를 gamepad에 왼쪽 또는 오른쪽 범퍼에서 왼쪽 또는 오른쪽 Alt 키를 사용 합니다.
* 하나 또는 둘 다 실습에 대 한 모든 입력을 보내기 위해 토글 스위치 아래에 있는 압정 단추를 클릭 합니다.  손 모양 아이콘이 대 한 Alt 키를 누른 채 것과 같습니다.
* 눈 게이즈 방향을 제어 하려면 "사람의 눈" 섹션에서 압정을 클릭 합니다.  키보드에서 'Y' 키를 누른 것과 같습니다.
* 기록 대화방을 로드 하려면 "기록" 섹션에서 "로드" 단추를 클릭 합니다.  참조 [방 시뮬레이션](#simulated-rooms) 자세한 내용은 합니다.
* 시뮬레이션 된 사용자 또는 시뮬레이션 된 입력된 장치 이동 하거나 회전 키보드에 대 한 응답에서 속도 조정 하려면 마우스 또는 gamepad 입력 "입력 설정" 옆에 있는 기어 아이콘을 클릭 하며 슬라이더를 조정 합니다.
* 기본적으로 키보드 입력 시뮬레이션 된 사람과 시뮬레이션 된 입력을 제어합니다.  PC의 키보드 입력을 HoloLens를 통해 전송 하도록 "시뮬레이션을 위해 사용 하 여 키보드." 선택을 취소 하십시오.  F4는이 설정에 대 한 바로 가기 키입니다.
* 시뮬레이션 패널에 표시 되어, 경우 F8을 누르면에 키보드 포커스를 이동 합니다.
* 에뮬레이터 창에서 시뮬레이션 패널의 도킹을 해제 하려면 패널의 맨 아래에 있는 단추를 클릭 하거나 키보드에서 F9 키를 누릅니다.  창 닫기 또는 다시 F9 키를 눌러 에뮬레이터에 창을 반환 합니다.
* 연결 하 고 PerceptionSimulationInput.exe %Programfiles(x86)%에서 실행 하 여 HoloLens 2 에뮬레이터, HoloLens 2 장치 또는 Windows Mixed Reality 시뮬레이션을 제어할 수 있도록 별도 응용 프로그램을 시작할 수 있습니다 시뮬레이션 제어판 \ Windows Kits\10\Microsoft XDE\10.0.18362.0\ 합니다.

### <a name="account-tab"></a>계정 탭

계정 탭을 사용 하면 Microsoft 계정으로 로그인 하도록 에뮬레이터를 구성할 수 있습니다. 사용자 계정으로 로그인 해야 하는 Api를 테스트에 유용 합니다.  이 옵션을 설정/해제는 완전히 닫고 적용 되려면 설정에 대해 HoloLens 에뮬레이터를 다시 시작 해야 합니다.  이 옵션을 사용 하는 경우 에뮬레이터의 후속 실행 묻습니다 할 로그인, 사용자 처럼 처음은 HoloLens 시작 될 것입니다.  PC의 키보드를 사용 하 여 자격 증명을 신속 하 게 입력을 시뮬레이션 제어판에서 "시뮬레이션에 대 한 키보드 사용"을 해제 하거나 F4 키를 눌러 키보드 설정 또는 해제를 전환 하려면 키보드에서 합니다.

### <a name="optional-settings-tab"></a>선택적 설정 탭

선택적 설정 탭을 사용 하도록 설정 하거나 하드웨어 가속된 그래픽을 사용 하지 않도록 컨트롤을 표시 됩니다.  하드웨어 가속된 그래픽 PC의 그래픽 어댑터 드라이버에서 지 원하는 경우 기본적으로 사용 됩니다.  그래픽 어댑터 드라이버 GPU PV을 지원 하지 않으면이 옵션이 표시 됩니다.

### <a name="diagnostics-tab"></a>진단 탭

진단 탭 에뮬레이터의 IP 주소를 링크의 형태로 Windows Device Portal 가상 GPU의 상태와 함께 표시 됩니다.


## <a name="anatomy-of-the-hololens-1st-gen-emulator"></a>HoloLens 분석 (첫 번째 Gen) 에뮬레이터

### <a name="main-window"></a>주 창

에뮬레이터를 시작, HoloLens OS를 표시 하는 창이 표시 됩니다.

![HoloLens 에뮬레이터 주 창](images/emulator-890px.png)

### <a name="toolbar"></a>도구 모음

주 창의 오른쪽에는 에뮬레이터 도구 모음을 찾을 수 있습니다. 도구 모음에 다음 단추가 포함 됩니다.
* ![닫기 아이콘](images/emulator-close.png) **닫기**: 에뮬레이터를 닫습니다.
* ![최소화 아이콘](images/emulator-minimize.png) **최소화**: 에뮬레이터 창을 최소화합니다.
* ![사용자 입력된 아이콘](images/emulator-control.png) **휴먼 입력**: 마우스 및 키보드 사용을 시뮬레이션할 휴먼 [에뮬레이터에 대 한 입력](#basic-emulator-input)합니다.
* ![키보드 및 마우스 입력된 아이콘](images/emulator-input.png) **키보드 및 마우스 입력**: 키보드 및 마우스 입력에 직접 전달 되는 HoloLens OS 키보드 및 마우스 이벤트로 Bluetooth 키보드와 마우스를 연결 하는 경우.
* ![화면에 맞춤 아이콘](images/emulator-fit.png) **화면에 맞추기**: 에뮬레이터를 화면에 맞춥니다.
* ![확대/축소 아이콘](images/emulator-zoom.png) **확대/축소**: 크고 작은 에뮬레이터를 확인 합니다.
* ![도움말 아이콘](images/emulator-help.png) **도움말**: 에뮬레이터 도움말을 엽니다.
* ![열린 장치 포털 아이콘](images/emulator-deviceportal.png) **장치 포털 열기**: 에뮬레이터에서 HoloLens OS에 대 한 Windows Device Portal 엽니다.
* ![도구 아이콘](images/emulator-tools.png) **도구**: 엽니다는 **추가 도구** 창입니다.

### <a name="simulation-tab"></a>시뮬레이션 탭

내에서 기본 탭의 **추가 도구** 창은 합니다 **시뮬레이션** 탭 합니다.

![HoloLens 에뮬레이터 ' 추가 ' 도구 창](images/emulator-simulation-500px.png)

시뮬레이션 탭 에뮬레이터 내에서 HoloLens OS 드라이브를 사용 하 고 시뮬레이트된 센서의 현재 상태를 보여 줍니다. 시뮬레이션 탭에 있는 값을 마우스로 가리키면 해당 값을 제어 하는 방법을 설명 하는 도구 설명을 제공 합니다.

### <a name="room-tab"></a>공간 탭

에뮬레이터에서 시뮬레이트된 "방" 공간 매핑 메시의 형태로 world 입력을 시뮬레이션합니다. 이 탭에는 기본 단체 실 대신 로드 하는 대화방을 선택할 수 있습니다.

![HoloLens 에뮬레이터 '대화방' 탭](images/emulator-room-500px.png)

참조 [방 시뮬레이션](#simulated-rooms) 자세한 내용은 합니다.

### <a name="account-tab"></a>계정 탭

계정 탭을 사용 하면 Microsoft 계정으로 로그인 하도록 에뮬레이터를 구성할 수 있습니다. API의 사용자 계정으로 로그인 해야 하는 테스트에 유용 합니다. 이 페이지에서 확인란을 선택 후 에뮬레이터의 후속 실행에서 로그인을 묻는는 HoloLens 시작 되는 사용자가 처음 처럼 합니다.

## <a name="simulated-rooms"></a>시뮬레이션 된 대화방

시뮬레이션 된 대화방 앱 테스트를 위해 여러 환경에서 유용 합니다. 여러 방 에뮬레이터와 함께 제공 되 고 찾을 수 %ProgramFiles (x86) %\Windows Kits\10\Microsoft XDE의에서 에뮬레이션을 설치한\\\Plugins\Rooms (버전). HoloLens를 사용 하 여 실제 환경에서 이러한 대화방의 모든 캡처된:
* **DefaultRoom.xef** -TV, 커피 테이블과 두 sofas를 사용 하 여 작은 거실 합니다. 에뮬레이터를 시작할 때 기본적으로 로드 합니다.
* **Bedroom1.xef** -책상을 사용 하 여 작은 침실 합니다.
* **Bedroom2.xef** -퀸 크기 평판, 장, nightstands, 및 walk-in 벽장 침실 합니다.
* **GreatRoom.xef** -거실, 식탁, 및 주방을 사용 하 여 열려 있는 대규모 공간 훌륭한 객실을 합니다.
* **LivingRoom.xef** 를 벽난로, 소파, armchairs, 거실 및 coffee 테이블과 꽃병-합니다.

고유한 공간과의 시뮬레이션 페이지를 사용 하 여 에뮬레이터에서 사용 하 여 기록할 수도 있습니다는 [Windows Device Portal](using-the-windows-device-portal.md) 에 HoloLens에 (첫 번째 Gen).

에뮬레이터에만 표시 됩니다 홀로그램 렌더링 하 여 홀로그램 뒤 시뮬레이션 된 대화방 표시 되지 것입니다. 이 둘 다 표시 되는 실제 HoloLens 달리 혼합 합니다. HoloLens 에뮬레이터에서 시뮬레이트된 대화방 표시 하려는 경우에 장면에서 공간 매핑 메시 렌더링 하도록 앱을 업데이트 해야 합니다.

## <a name="troubleshooting"></a>문제 해결

해야 하는 에뮬레이터를 설치 하는 동안 오류가 표시 될 수 있습니다 *"Visual Studio 2015 업데이트 1 및 UWP 도구 버전 1.2"* 합니다. 이 오류의 원인은 3 가지가 있습니다.
* 최신 버전의 Visual Studio (Visual Studio 2019, Visual Studio 2017 또는 Visual Studio 2015 업데이트 1 이상)는 없습니다. 이 해결 하려면 Visual Studio의 최신 릴리스를 설치 합니다.
* Visual Studio의 최신 버전의 유니버설 Windows 플랫폼 (UWP) 도구가 설치 되어 있지 않은 있지만 이것이 Visual Studio에 대 한 선택적 기능입니다.

에뮬레이터에는 비-Pro/Enterprise/교육 SKU의 Windows를 설치 하는 오류가 나타날 수도 있습니다 또는 Hyper-v 기능이 없는 경우 사용할 수 있습니다.
* 읽어보세요 합니다 [시스템 요구 사항](#hololens-emulator-system-requirements) 전체 요구 사항 집합에 대 한 위 섹션입니다.
* 하세요 시스템에서 Hyper-v 기능이 설정 되어 있는지 확인도 합니다.

설치를 완료 했지만 HoloLens 에뮬레이터 배포 및 디버깅에 대 한 옵션으로 표시 되지 않으면, 경우 다음 사항을 확인 하세요.
* Visual Studio 프로젝트 구성 (HoloLens 첫 번째 Gen) x86 또는 x86 또는 x64 (HoloLens 2 에뮬레이터)으로 설정 됩니다.
* Visual Studio 2019를 사용 하는 경우 프로젝트 구성이 플랫폼 도구 집합 v142로 설정 됩니다.

설치를 완료 했지만 Visual Studio에는 HoloLens 에뮬레이터를 시작 하는 동안 오류가 표시 됩니다, 경우 다음을 시도 하세요.
* 관리자 권한으로 Visual Studio를 실행 합니다.
* 만 설치 하는 Visual Studio 2019 했을 경우 HKEY_LOCAL_MACHINE\Software\Microsoft\Windows Kits\Installed 루트에 있는 레지스트리 값 "KitsRoot10" 32 비트 Program Files 폴더를 가리키는지 확인 하십시오 (예: "C:\Program Files (x86) \Windows 키트 \10 ").  표시 되지 않는 경우 HoloLens 에뮬레이터, 레지스트리 값을 변경 합니다 32 비트 Program Files 폴더를 제거한 다음 HoloLens 에뮬레이터.  이 문제는 Visual Studio 2019 16.0.3에서에서 해결 됩니다.

에뮬레이터 시작 시 "잘못 된 바이트 인코딩" 오류 대화 상자가 표시:
* %Localappdata%\Microsoft\XDE\HCS의 모든 파일을 삭제 하 고 다시 시도 하세요.

Visual Studio에서 디버그 대상 목록이 비어 있으면 (예를 들어, "Start"는 유일한 옵션) 위의 모든 문제 해결 단계를 수행 했다면 및:
* %Localappdata%\Microsoft\VisualStudio에서 'ConfigurationCache' 폴더를 삭제할\\<*설치 id*> \CoreCon 고 다시 시도 하세요.

시스템에서 에뮬레이터를 시작 하는 경우에 중지 되 면 에뮬레이터 그래픽 하드웨어 가속을 사용 하지 않도록 설정 합니다.
* HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\XDE\10.0에서 "DisableGPU" 라는 레지스트리 DWORD 값을 만들고 해당 값을 1로 설정 합니다.

## <a name="see-also"></a>참조
* [고급 HoloLens 에뮬레이터 및 Mixed Reality 시뮬레이터 입력](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens 에뮬레이터 소프트웨어 기록](hololens-emulator-archive.md)
* [Unity의 공간 매핑](spatial-mapping-in-unity.md)
* [DirectX의 공간 매핑](spatial-mapping-in-directx.md)
