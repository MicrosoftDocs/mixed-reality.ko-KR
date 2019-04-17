---
title: HoloLens 에뮬레이터를 사용 하 여
description: HoloLens 에뮬레이터를 사용 하면 실제 HoloLens 하지 않고 PC에서 혼합된 현실 앱을 테스트할 수 있습니다.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, 에뮬레이터
ms.openlocfilehash: 3551bf48037f0cb7e8d243f2d89d43664e7c3475
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604102"
---
# <a name="using-the-hololens-emulator"></a>HoloLens 에뮬레이터를 사용 하 여

HoloLens 에뮬레이터 실제 HoloLens 하지 않고 PC에서 holographic 앱을 테스트할 수 있습니다 및 HoloLens 개발 도구 집합과 함께 제공 됩니다. 에뮬레이터는 Hyper-v 가상 컴퓨터를 사용합니다. 일반적으로 HoloLens에 센서에서 읽을 수 있는 사람과 환경 입력 키보드, 마우스, 또는 Xbox 컨트롤러를 사용 하 여 시뮬레이션 대신 됩니다. 에뮬레이터에서 실행을 수정할 필요가 없습니다 프로그램과 알지 들 실제 HoloLens에서 실행 되지 않습니다.

데스크톱 Pc에 대 한 Windows Mixed Reality 몰입 형 (VR) 헤드셋 앱 또는 게임을 개발 하려는 경우 체크 아웃 합니다 [Windows Mixed Reality 시뮬레이터](using-the-windows-mixed-reality-simulator.md), 대신 데스크톱 헤드셋을 시뮬레이션할 수 있습니다.

> [!NOTE]
> HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.

## <a name="installing-the-hololens-emulator"></a>HoloLens 에뮬레이터 설치

다운로드 합니다 [HoloLens (첫 번째 gen) holographic 프로젝트 템플릿과 에뮬레이터](https://go.microsoft.com/fwlink/?linkid=2065980)합니다.

HoloLens 에뮬레이터의 이전 빌드를 찾을 수 있습니다 합니다 [HoloLens 에뮬레이터 아카이브](hololens-emulator-archive.md) 페이지입니다.

### <a name="hololens-emulator-system-requirements"></a>HoloLens 에뮬레이터 시스템 요구 사항

HoloLens 에뮬레이터에서 Hyper-v를 기반으로 하 고 하드웨어 가속된 그래픽에 대 한 RemoteFx를 사용 합니다. 에뮬레이터를 사용 하려면 PC에 이러한 하드웨어 요구 사항을 충족 하는지 확인 합니다.
* 64 비트 Windows 10 Pro, Enterprise 또는 교육 
    >[!NOTE]
    >Windows 10 Home edition에는 Hyper-v 또는 HoloLens 에뮬레이터를 지원 하지 않습니다.
* 64비트 CPU
* CPU 코어 4 개 (또는 총 코어 수 4 개를 사용 하 여 여러 Cpu)
* 8GB RAM 이상
* BIOS에서 다음 기능 이어야 합니다 [지원 하 고 사용 하도록 설정](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):
   * 하드웨어 지원 가상화
   * SLAT(Second Level Address Translation)
   * 하드웨어 기반 DEP(데이터 실행 방지)
* GPU 요구 사항 (에뮬레이터는 지원 되지 않는 GPU에서 작동 하지만 성능이 크게 저하 됩니다.)
   * DirectX 11.0 이상
   * WDDM 1.2 드라이버 이상

시스템에는 위의 요구 사항을 충족 하는 경우 **시스템에서 "하이퍼-V" 기능이 설정 되어 있는지를 확인 하세요** 제어판을 통해-> 프로그램-> 프로그램 및 기능에서-> Windows 기능 설정 또는 해제-> 확인 찾기가 성공 하려면 에뮬레이터 설치에 대 한 해당 "하이퍼-V" 선택 됩니다.

### <a name="installation-troubleshooting"></a>설치 문제 해결

해야 하는 에뮬레이터를 설치 하는 동안 오류가 표시 될 수 있습니다 *"Visual Studio 2015 업데이트 1 및 UWP 도구 버전 1.2"* 합니다. 이 오류의 원인은 3 가지가 있습니다.
* 최신 버전의 Visual Studio (Visual Studio 2017 또는 Visual Studio 2015 업데이트 1 이상)는 없습니다. 이 해결 하려면 Visual Studio의 최신 릴리스를 설치 합니다.
* Visual Studio의 최신 버전의 유니버설 Windows 플랫폼 (UWP) 도구가 설치 되어 있지 않은 있지만 이것이 Visual Studio에 대 한 선택적 기능입니다.

에뮬레이터에는 비-PRO/Enterprise/교육 SKU의 Windows를 설치 하는 오류가 나타날 수도 있습니다 또는 Hyper-v 기능이 없는 경우 사용할 수 있습니다.
* 읽어보세요 합니다 [시스템 요구 사항](#hololens-emulator-system-requirements) 전체 요구 사항 집합에 대 한 위 섹션입니다.
* 하세요 시스템에서 Hyper-v 기능이 설정 되어 있는지 확인도 합니다.

## <a name="deploying-apps-to-the-hololens-emulator"></a>HoloLens 에뮬레이터에 앱 배포

1. Visual Studio 2015에서 앱 솔루션을 로드 합니다.
    >[!NOTE]
    >Unity를 사용 하면 Unity에서 프로젝트를 빌드할 한 다음 빌드된 솔루션이 Visual Studio를 정상적으로 로드 합니다.
2. 플랫폼으로 설정 되었는지 확인 **x86**합니다.
3. 선택 된 **HoloLens 에뮬레이터** 디버깅에 대 한 대상 장치로 합니다.
4. 로 이동 **디버그 > 디버깅 시작** 누르거나 **F5** 에뮬레이터를 시작 하 여 디버깅을 위해 앱을 배포 합니다.

에뮬레이터는 1 분 이상 처음 시작할 때 부팅 걸릴 수 있습니다. 열어 에뮬레이터 디버깅 세션 중 실행 중인 에뮬레이터에 앱을 신속 하 게 배포할 수 있습니다 있도록 하는 것이 좋습니다.

## <a name="basic-emulator-input"></a>기본 에뮬레이터 입력

에뮬레이터를 제어 하는 것은 많은 일반적인 3D 비디오 게임 매우 비슷합니다. 키보드, 마우스 또는 Xbox 컨트롤러를 사용 하 여 사용할 수는 입력된 옵션이 있습니다. HoloLens 착용 시뮬레이션된 된 사용자의 동작을 지시 하 여 에뮬레이터를 제어 합니다. 작업 관련 시뮬레이션 된 사용자와 에뮬레이터에서 실행 되는 앱이 실제 장치에서 하 듯는 응답을 이동 합니다.
* **앞으로, 다시을 유지 하 고 마우스 오른쪽 단추로** -W, 사용 하 여 키보드 또는 Xbox 컨트롤러에 왼쪽된 메모리에서 A, S, D 키입니다.
* **조회할 아래, 왼쪽 및 오른쪽** -클릭 하 고 마우스를 끌어 키보드 또는 Xbox 컨트롤러에 올바른 메모리에서 화살표 키를 사용 합니다.
* **어 탭 제스처** -마우스, 키보드에서 Enter 키를 눌러 또는 Xbox 컨트롤러에는 단추를 사용 합니다.
* **제스처 피우는** -키보드에서 Windows 키나 F2 키를 눌러 또는 Xbox 컨트롤러 B 단추를 누릅니다.
* **스크롤 하는 것에 대 한 이동을 제공할** -Alt 키를 누른 채로 마우스 오른쪽 단추 및 위쪽 / 아래쪽에 마우스를 끌어 또는 Xbox 컨트롤러를에서 오른쪽 트리거와 단추 누른 오른쪽 스틱을 위아래로 이동 합니다.

## <a name="anatomy-of-the-hololens-emulator"></a>HoloLens 에뮬레이터의 분석

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

![HoloLens 에뮬레이터 '방' 탭](images/emulator-room-500px.png)

시뮬레이션 된 대화방 앱 테스트를 위해 여러 환경에서 유용 합니다. 여러 방 에뮬레이터와 함께 제공 됩니다 하 고 찾을 수 %Programfiles(x86)% %\Program 파일 (x86) \Microsoft XDE\10.0.11082.0\Plugins\Rooms 에뮬레이션을 설치한 경우. HoloLens를 사용 하 여 실제 환경에서 이러한 대화방의 모든 캡처된:
* **DefaultRoom.xef** -TV, 커피 테이블과 두 sofas를 사용 하 여 작은 거실 합니다. 에뮬레이터를 시작할 때 기본적으로 로드 합니다.
* **Bedroom1.xef** -책상을 사용 하 여 작은 침실 합니다.
* **Bedroom2.xef** -퀸 크기 평판, 장, nightstands, 및 walk-in 벽장 침실 합니다.
* **GreatRoom.xef** -거실, 식탁, 및 주방을 사용 하 여 열려 있는 대규모 공간 훌륭한 객실을 합니다.
* **LivingRoom.xef** 를 벽난로, 소파, armchairs, 거실 및 coffee 테이블과 꽃병-합니다.

고유한 공간과의 시뮬레이션 페이지를 사용 하 여 에뮬레이터에서 사용 하 여 기록할 수도 있습니다는 [Windows Device Portal](using-the-windows-device-portal.md) 에 HoloLens에 있습니다.

에뮬레이터에만 표시 됩니다 홀로그램 렌더링 하 여 홀로그램 뒤 시뮬레이션 된 대화방 표시 되지 것입니다. 이 둘 다 표시 되는 실제 HoloLens 달리 혼합 합니다. HoloLens 에뮬레이터에서 시뮬레이트된 대화방 표시 하려는 경우에 장면에서 공간 매핑 메시 렌더링 하도록 앱을 업데이트 해야 합니다.

### <a name="account-tab"></a>계정 탭

계정 탭을 사용 하면 Microsoft 계정으로 로그인 하도록 에뮬레이터를 구성할 수 있습니다. API의 사용자 계정으로 로그인 해야 하는 테스트에 유용 합니다. 이 페이지에서 확인란을 선택 후 에뮬레이터의 후속 실행에서 로그인을 묻는는 HoloLens 시작 되는 사용자가 처음 처럼 합니다.

## <a name="see-also"></a>참조
* [고급 HoloLens 에뮬레이터 및 혼합 현실 시뮬레이터 입력](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [HoloLens 에뮬레이터 소프트웨어 기록](hololens-emulator-archive.md)
* [Unity에서 공간 매핑](spatial-mapping-in-unity.md)
* [DirectX의 공간 매핑](spatial-mapping-in-directx.md)
