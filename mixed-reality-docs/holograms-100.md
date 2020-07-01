---
title: MR 기본 사항 100-Unity 시작
description: 첫 번째 기본 혼합 현실 "hello 세계" 응용 프로그램을 만드는 방법에 대해 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 혼합 현실, Windows Mixed Reality, HoloLens, 몰입 형, vr, mr, 시작, 홀로그램, 아카데미, 자습서
ms.openlocfilehash: 58a1785ef74872c633cf65d6a32e24d517367359
ms.sourcegitcommit: f523b74a549721b6bec69cb5d2eca5b7673a793c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85570302"
---
# <a name="mr-basics-100-getting-started-with-unity"></a>MR 기본 100: Unity 시작

>[!IMPORTANT]
>Mixed Reality 아카데미 자습서는 HoloLens(1세대) 및 Mixed Reality 몰입형 헤드셋을 염두에 두고 설계되었습니다.  따라서 이러한 디바이스 개발에 대한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요합니다.  이러한 자습서는 HoloLens 2에 사용되는 최신 도구 집합 또는 상호 작용으로 업데이트되지 **_않습니다_**.  대신 지원되는 디바이스에서 계속 작동하도록 유지 관리됩니다. HoloLens 2에 대한 [새로운 자습서 시리즈](mrlearning-base.md)가 게시되었습니다.

이 자습서에서는 Unity로 빌드된 기본 혼합 현실 앱을 만드는 과정을 안내 합니다.

## <a name="device-support"></a>디바이스 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td>MR 기본 100: Unity 시작</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>필수 구성 요소

* 올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.

## <a name="chapter-1---create-a-new-project"></a>1 장-새 프로젝트 만들기

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Unity를 사용 하 여 앱을 빌드하려면 먼저 프로젝트를 만들어야 합니다. 이 프로젝트는 몇 개의 폴더로 구성 되며 가장 중요 한 것은 자산 폴더입니다. 이 폴더는 Maya, Max 시네마, Photoshop 등의 디지털 콘텐츠 생성 도구에서 가져온 모든 자산, Visual Studio 또는 즐겨 찾는 코드 편집기를 사용 하 여 만든 모든 코드 및 편집기에서 장면, 애니메이션 및 기타 Unity 자산 형식을 작성할 때 Unity에서 만드는 모든 콘텐츠 파일을 포함 하는 폴더입니다.

UWP 앱을 빌드 및 배포 하기 위해 Unity는 필요한 모든 자산과 코드 파일을 포함 하는 Visual Studio 솔루션으로 프로젝트를 내보낼 수 있습니다.

1. Unity 시작
2. **새로 만들기** 선택
3. 프로젝트 이름 (예: "MixedRealityIntroduction")을 입력 합니다.
4. 프로젝트를 저장할 위치를 입력 하십시오.
5. **3d** 토글이 선택 되어 있는지 확인 합니다.
6. **프로젝트 만들기** 선택

이제 혼합 현실 사용자 지정을 시작 하기 위한 모든 설정이 축 하 합니다.

## <a name="chapter-2---setup-the-camera"></a>2 장-카메라 설정

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Unity 기본 카메라는 헤드 추적 및 stereoscopic 렌더링을 처리 합니다. 혼합 현실에서 사용할 수 있도록 기본 카메라에 몇 가지 변경 사항이 있습니다.

1. 파일 > 새 장면 선택

첫째, 사용자의 시작 위치 (**X**: 0, **Y**: 0, **Z**: 0)를 생각해 보면 앱을 레이아웃 하는 것이 더 쉽습니다. 주 카메라가 사용자 헤드의 이동을 추적 하므로 기본 카메라의 시작 위치를 설정 하 여 사용자의 시작 위치를 설정할 수 있습니다.

1. **계층** 패널에서 **주 카메라** 를 선택 합니다.
2. **검사기** 패널에서 **변형** 구성 요소를 찾아 **위치** 를 (**x**: 0, **y**: 1, **z**:-10)에서 (**x**: 0, **y**: 0, **z**: 0)로 변경 합니다.

둘째, 기본 카메라 배경을 고려해 야 합니다.

**HoloLens 응용 프로그램의**경우 실제 세계는 Skybox 질감이 아닌 카메라에서 렌더링 하는 모든 항목 뒤에 표시 되어야 합니다.

1. **계층** 패널 **에서 주 카메라** 를 선택 하 고, **검사기** 패널에서 **카메라** 구성 요소를 찾고, **Clear Flags** 드롭다운에서 **Skybox** 에서 **Solid 색**으로 변경 합니다.
2. **배경색** 선택을 선택 하 고 **RGBA** 값을 (0, 0, 0, 0)으로 변경 합니다.

**모던 헤드셋을 대상으로 하는 혼합 현실 응용 프로그램의**경우 Unity에서 제공 하는 기본 Skybox 텍스처를 사용할 수 있습니다.

1. **계층** 패널 **에서 주 카메라** 를 선택 하 고, **검사기** 패널에서 **카메라** 구성 요소를 찾고, **Clear Flags** 드롭다운을 **Skybox**으로 유지 합니다.

셋째, Unity에서 가까운 클립 평면을 고려 하 고 사용자가 개체 또는 개체에 접근 하기 때문에 개체가 사용자 눈에 너무 가깝게 렌더링 되지 않도록 할 수 있습니다.

**Hololens 응용 프로그램의**경우 가까운 클립 평면을 [hololens 권장](camera-in-unity.md#clip-planes) 0.85 미터로 설정할 수 있습니다.

1. **계층** 패널 **에서 주 카메라** 를 선택 하 고, **검사기** 패널에서 **카메라** 구성 요소를 찾아 **가까운 클립 평면** 필드를 기본 **0.3** 에서 HoloLens 권장 **0.85**로 변경 합니다.

**모던 헤드셋을 대상으로 하는 혼합 현실 응용 프로그램의**경우 Unity에서 제공 하는 기본 설정을 사용할 수 있습니다.

1. **계층** 패널에서 **주 카메라** 를 선택 하 고, **검사기** 패널에서 **카메라** 구성 요소를 찾아 **가까운 클립 평면** 필드를 기본 **0.3**으로 유지 합니다.

마지막으로 지금까지 진행 상황을 저장 해 주세요. 장면 변경 내용을 저장 하려면 > 파일을 선택 하 고 **다른 이름으로 장면 저장**을 **선택한 다음**, **저장**을 선택 합니다.

## <a name="chapter-3---setup-the-project-settings"></a>3 장-프로젝트 설정 설치

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

이 장에서는 개발을 위해 Windows Holographic SDK를 대상으로 하는 데 도움이 되는 몇 가지 Unity 프로젝트 설정을 설정 합니다. 응용 프로그램에 대 한 몇 가지 품질 설정도 설정 됩니다. 마지막으로 빌드 대상이 유니버설 Windows 플랫폼로 설정 되었는지 확인 합니다.

### <a name="unity-performance-and-quality-settings"></a>Unity 성능 및 품질 설정

**HoloLens 용 Unity 품질 설정**

![HoloLens 용 Unity 품질 설정](images/qualitysettings.png)

HoloLens에서 높은 프레임 속도를 유지 하는 것이 매우 중요 하기 때문에 최상의 성능을 위해 품질 설정을 조정 하려고 합니다. 자세한 성능 정보는 [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)을 제공 합니다.

1. **편집 > 프로젝트 설정 > 품질** 을 선택 합니다.
2. **유니버설 Windows 플랫폼** 로고 아래에 있는 **드롭다운** 을 선택 하 고 **매우 낮음**을 선택 합니다. 유니버설 Windows 플랫폼 열의 상자와 **매우 낮은** 행이 녹색 이면 설정이 올바르게 적용 됩니다.

**폐색를 대상으로 하는 혼합 현실 응용 프로그램의 경우**품질 설정을 기본값으로 그대로 둘 수 있습니다.

### <a name="target-windows-10-sdk"></a>Windows 10 SDK를 대상으로 합니다.

**Windows Holographic SDK 대상**

![Windows Holographic SDK 대상](images/xrsettings.png)

내보내려는 앱이 2D 보기 대신 [몰입 형 보기](app-views.md) 를 만들어야 한다고 Unity에 알려야 합니다. Windows 10 SDK를 대상으로 하는 Unity에서 가상 현실 지원을 사용 하도록 설정 하 여이 작업을 수행 합니다.

1. **편집 > 프로젝트 설정 > 플레이어**로 이동 합니다.
2. 플레이어 설정에 대 한 **검사기 패널** 에서 **유니버설 Windows 플랫폼** 아이콘을 선택 합니다.
3. **XR 설정** 그룹을 확장합니다.
4. **렌더링** 섹션에서 **가상 현실 지원 됨** 확인란을 선택 하 여 새 **가상 현실 sdk** 목록을 추가 합니다.
5. 목록에 **Windows Mixed Reality**가 나타나는지 확인합니다. 그렇지 않은 경우 목록 아래쪽에서 **+** 단추를 선택하고 **Windows Mixed Reality**를 선택합니다.

>[!NOTE]
>**유니버설 Windows 플랫폼** 아이콘이 표시 되지 않는 경우 설치 중에 빌드 지원 유니버설 Windows 플랫폼 선택 했는지 확인 합니다. 이 항목을 선택하지 않은 경우 올바른 Windows 설치를 사용하여 Unity를 다시 설치해야 할 수 있습니다.

모든 프로젝트 설정을 적용 하기 위한 놀라운 작업입니다. 다음으로, 홀로그램을 추가 해 보겠습니다.

## <a name="chapter-4---create-a-cube"></a>4 장-큐브 만들기

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Unity 프로젝트에서 큐브를 만드는 것은 Unity에서 다른 개체를 만드는 것과 같습니다. Unity의 좌표계가 실제 세계에 매핑되므로 unity의 좌표계가 실제 환경에서 약 1 미터의 약 1 미터에 매핑되므로 사용자 앞에 큐브를 배치 하는 것이 쉽습니다.

1. **계층** 패널의 왼쪽 위 모서리에서 **만들기** 드롭다운을 선택 하 고 **3d 개체 > 큐브**를 선택 합니다.
2. **계층** 패널에서 새로 만든 **큐브** 를 선택 합니다.
3. **검사기** 에서 **변형** 구성 요소를 찾고 **위치** 를 (**X**: 0, **Y**: 0, **Z**: 2)로 변경 합니다. *이는 큐브 2 미터를 사용자의 시작 위치 앞에 배치 합니다.*
4. **변환** 구성 요소에서 **회전** 을 (**x**: 45, **y**: 45, **z**: 45)로 변경 하 고 **Scale** 을 (**x**: 0.25, **Y**: 0.25, **z**: 0.25)로 변경 합니다. *그러면 큐브의 크기가 0.25 미터가 됩니다.*
5. 장면 변경 내용을 저장 하려면 **파일 > 장면 저장**을 선택 합니다.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>5 장-Unity 편집기에서 장치 확인

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

이제 큐브를 만들었으므로 장치를 빠르게 확인할 수 있습니다. Unity 편집기 내에서이 작업을 직접 수행할 수 있습니다.

### <a name="initial-setup"></a>초기 설정

1. 개발 PC의 Unity에서 **파일 > 빌드 설정** 창을 엽니다.
2. **플랫폼** 을 **유니버설 Windows 플랫폼** 로 변경 하 고 **플랫폼 전환** 을 클릭 합니다.

### <a name="for-hololens-use-unity-remoting"></a>HoloLens의 경우 Unity 원격 기능 사용

1. HoloLens에서 Windows 스토어에서 사용할 수 있는 [Holographic Remoting 플레이어](holographic-remoting-player.md)를 설치 하 고 실행 합니다. 장치에서 응용 프로그램을 시작 하면 대기 중 상태로 전환 되 고 장치의 IP 주소가 표시 됩니다. IP를 적어둡니다.
2. **창 > XR > Holographic 에뮬레이션**을 엽니다.
3. **에뮬레이션 모드** 를 **없음** 에서 **원격에서 장치로**변경 합니다.
4. **원격 컴퓨터**에 앞에서 적어둔 HOLOLENS의 IP 주소를 입력 합니다.
5. **연결**을 클릭합니다.
6. **연결 상태가** **녹색으로**변경 되었는지 확인 합니다.
7. 이제 Unity 편집기에서 **Play** 를 클릭할 수 있습니다.

이제 장치 및 편집기에서 큐브를 볼 수 있습니다. 편집기에서 응용 프로그램을 실행 하는 것 처럼 편집기에서 응용 프로그램을 실행 하는 것 처럼 응용 프로그램을 일시 중지 하 고 검사 하 고 디버그할 수 있습니다. 단, 비디오, 오디오 및 장치 입력은 네트워크를 통해 호스트 컴퓨터와 장치 간에 전송 됩니다.

### <a name="for-other-mixed-reality-supported-headsets"></a>다른 혼합 현실 지원 헤드셋의 경우

1. USB 케이블과 HDMI 또는 디스플레이 포트 케이블을 사용 하 여 개발 PC에 헤드셋을 연결 합니다.
2. **혼합 현실 포털** 을 시작 하 고 첫 실행 환경을 완료 했는지 확인 합니다.
3. 이제 Unity에서 재생 단추를 누를 수 있습니다.

이제 혼합 현실 헤드셋 및 편집기에서 큐브 렌더링을 볼 수 있습니다.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>6 장-Visual Studio에서 장치 빌드 및 배포

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

이제 프로젝트를 Visual Studio로 컴파일하고 대상 장치에 배포할 준비가 되었습니다.

### <a name="export-to-the-visual-studio-solution"></a>Visual Studio 솔루션으로 내보내기

1. **파일 > 빌드 설정** 창을 엽니다.
1. 열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.
1. **플랫폼** 을 **유니버설 Windows 플랫폼** 로 변경 하 고 **플랫폼 전환**을 클릭 합니다.
1. **유니버설 Windows 플랫폼** 설정에서 **SDK** 가 **유니버설 10**인지 확인 합니다.
1. 대상 장치에 대해 폐색를 표시 하거나 **HoloLens**로 전환 하는 **모든 장치** 를 그대로 둡니다.
1. **UWP 빌드 형식은** **D3D**이어야 합니다.
1. **UWP SDK** 는 **설치 된 최신 버전**으로 유지할 수 있습니다.
1. **빌드**를 클릭한 다음
1. 파일 탐색기에서 **새 폴더** 를 클릭 하 고 폴더 이름을 **"App"** 으로 선택 합니다.
1. **앱** 폴더가 선택 된 상태에서 **폴더 선택** 단추를 클릭 합니다.
1. Unity가 빌드를 완료 하면 Windows 파일 탐색기 창이 표시 됩니다.
1. 파일 탐색기에서 **앱** 폴더를 엽니다.
1. 생성 된 Visual Studio 솔루션 (이 예제에서는 MixedRealityIntroduction)을 엽니다.

### <a name="compile-the-visual-studio-solution"></a>Visual Studio 솔루션 컴파일

마지막으로, 내보낸 Visual Studio 솔루션을 컴파일하여 배포 하 고 장치에서 사용해 보세요.

1. Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 **디버그** 에서 **릴리스** 로, **ARM** 에서 **x 86**으로 변경 합니다.

지침은 장치 및 에뮬레이터에 배포 하는 경우와 다릅니다. 설치와 일치 하는 지침을 따르세요.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Wi-fi를 통해 혼합 현실 장치에 배포

1. **로컬 컴퓨터** 단추 옆의 화살표를 클릭 하 고 배포 대상을 **원격 컴퓨터로**변경 합니다.
2. 혼합 현실 장치의 IP 주소를 입력 하 고 다른 장치의 HoloLens 및 **Windows** 에 대 한 **인증 모드** 를 유니버설 (암호화 되지 않은 프로토콜)으로 변경 합니다.
3. **디버그 > 디버깅 하지 않고 시작**을 클릭 합니다.

**HoloLens의**경우 장치에 처음 배포 하는 경우 [Visual Studio를 사용 하 여](using-visual-studio.md)페어링 해야 합니다.

### <a name="deploy-to-mixed-reality-device-over-usb"></a>USB를 통해 혼합 현실 장치에 배포

USB 케이블을 통해 장치가 연결 되어 있는지 확인 합니다.

1. **HoloLens의**경우 **로컬 컴퓨터** 단추 옆에 있는 화살표를 클릭 하 고 배포 대상을 **장치**로 변경 합니다.
2. **PC에 연결 된 폐색 장치를 대상으로 지정**하려면 설정을 로컬 컴퓨터에 유지 합니다. **혼합 현실 포털이** 실행 중인지 확인 합니다.
3. **디버그 > 디버깅 하지 않고 시작**을 클릭 합니다.

### <a name="deploy-to-emulator"></a>에뮬레이터에 배포

1. **장치** 단추 옆의 화살표를 클릭 하 고 드롭다운에서 **HoloLens 에뮬레이터**를 선택 합니다.
2. **디버그 > 디버깅 하지 않고 시작**을 클릭 합니다.

### <a name="try-out-your-app"></a>앱 사용해 보기

이제 앱이 배포 되었으므로 큐브를 모두 이동 하 여 전 세계에 유지 되는지 확인 하세요.

## <a name="see-also"></a>참고 항목

* [Unity 개발 개요](unity-development-overview.md)
* [Unity 및 Visual Studio 사용 모범 사례](best-practices-for-working-with-unity-and-visual-studio.md)
* [MR 기본 101](holograms-101.md)
* [MR 기본 101E](holograms-101e.md)
