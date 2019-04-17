---
title: MR 기본 사항 100-Unity를 사용 하 여 시작
description: 첫 번째 기본 혼합된 현실 "hello world" 응용 프로그램을 만드는 방법에 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality 실제로 혼합 HoloLens, 몰입 형, vr, mr, 시작, 홀로그램 academy, 자습서
ms.openlocfilehash: 1f4a5490383671fba694b386015ff6742d37241b
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597560"
---
>[!NOTE]
>혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.  따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.  이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.  지원 되는 장치에서 작업을 계속 유지 됩니다. 새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.  게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a>MR 100의 기초: Unity를 사용 하 여 시작

이 자습서 Unity를 사용 하 여 빌드한 기본 혼합된 현실 앱을 만드는 과정을 안내 합니다.

## <a name="device-support"></a>장치 지원

<table>
<tr>
<th>과정</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td>MR 100의 기초: Unity를 사용 하 여 시작</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>사전 요구 사항

* 올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md)입니다.

## <a name="chapter-1---create-a-new-project"></a>장 1-새 프로젝트 만들기

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Unity 사용 하 여 앱을 빌드하려면 먼저 프로젝트를 만들려면 해야 합니다. 이 프로젝트는 가장 중요 한 자산 폴더에는 몇 가지 폴더로 구성 됩니다. Maya, 최대 시네마 4d 또는 Photoshop, Visual Studio 또는 즐겨 찾는 코드 편집기를 사용 하 여 만든 모든 코드와 같은 디지털 콘텐츠 작성 도구에서 가져와야 하는 모든 자산을 보유 하는 폴더 이며 Unity 때 만들어지는 콘텐츠 파일을 개수에 관계 없이 백그라운드에서 작성 애니메이션 및 편집기에서 다른 Unity 자산 형식입니다.

Unity를 빌드 및 UWP 앱을 배포 하려면 모든 필요한 자산 및 코드 파일에 포함 될 Visual Studio 솔루션으로 프로젝트를 내보낼 수 있습니다.

1. Unity를 시작 합니다.
2. 선택 **새**
3. 프로젝트 이름 (예: 입력 "MixedRealityIntroduction")
4. 프로젝트를 저장할 위치를 입력 합니다.
5. 확인 합니다 **3D** 토글 선택
6. 선택 **프로젝트 만들기**

축에 이제 혼합된 현실 사용자 지정을 사용 하 여 시작 하려면 모든 설치 합니다.

## <a name="chapter-2---setup-the-camera"></a>2 장-카메라 설정

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

Unity 주 카메라 헤드 추적 및 stereoscopic 렌더링을 처리 합니다. 혼합된 현실 함께 사용 하 여 주 카메라를 확인 하려면 몇 가지 변경 내용이.입니다.
1. 파일 선택 > 새 장면

첫째,이 더 쉽게 레이아웃 지정 앱으로 사용자의 시작 위치를 가정해 보겠습니다 (**X**: 0, **Y**: 0, **Z**: 0). 주 카메라 사용자의 헤드의 움직임 추적, 이후 주 카메라의 시작 위치를 설정 하 여 사용자의 시작 위치를 설정할 수 있습니다.
1. 선택 **주 카메라** 에 **계층** 패널
2. 에 **검사기** 패널에서 찾을 합니다 **변환** 구성 요소 및 변경 합니다 **위치** 에서 (**X**: 0, **Y**: 1 **Z**:-10)를 (**X**: 0 **Y**: 0, **Z**: 0)

둘째, 기본 카메라 배경을 약간의 고려를 해야합니다.

**HoloLens 응용 프로그램에 대 한**, 카메라 모든 개체의 뒤에 실제 표시 되어야 하지 Skybox 텍스처를 렌더링 합니다.
1. 사용 하 여는 **주 카메라** 선택 계속을 **계층** 패널에서 찾을 **카메라** 구성 요소를 **검사기** 패널 및 변경 합니다 **플래그 지우기** 드롭다운 **Skybox** 하 **단색**합니다.
2. 선택 된 **백그라운드** 색 선택기 및 변경 합니다 **RGBA** 값 (0, 0, 0, 0)을

**몰입 형 헤드셋을 대상으로 하는 혼합된 현실 응용 프로그램에 대 한**, Unity가 제공 하는 기본 Skybox 질감을 사용할 수 있습니다.
1. 사용 하 여는 **주 카메라** 선택 계속 합니다 **계층** 패널에서 찾을 **카메라** 구성 요소를 **검사기** 패널 및 유지를 **플래그 지우기** 드롭다운에서 **Skybox**합니다.

셋째, 보겠습니다 Unity의 가까운 클립 면과 고려 있으며 못하도록 개체 렌더링 너무 가깝게 사용자에 게 눈 사용자 개체에 도달 하거나 개체를 사용자에 도달 합니다.

**HoloLens 응용 프로그램에 대 한**, 가까운 클립 면과 카메라를 설정할 수 있는 합니다 [권장 HoloLens](camera-in-unity.md#clip-planes) 0.85 미터입니다.
1. 사용 하 여는 **주 카메라** 선택 계속을 **계층** 패널에서 찾을 **카메라** 구성 요소를 **검사기** 패널 및 변경 합니다 **가까운 클립 면과 카메라** 기본값과에서 필드 **0.3** 권장 HoloLens에 **0.85**합니다.

**몰입 형 헤드셋을 대상으로 하는 혼합된 현실 응용 프로그램에 대 한**, Unity가 제공 하는 기본 설정을 사용할 수 있습니다.
1. 사용 하 여는 **주 카메라** 선택 계속 합니다 **계층** 패널에서 찾을 **카메라** 구성 요소를 **검사기** 패널 및 유지를 **가까운 클립 면과 카메라** 기본 필드 **0.3**합니다.

마지막으로 진행 상황을 지금 저장 하겠습니다. 장면 변경 내용을 저장 하려면 선택 **파일 > 다른 이름으로 장면 저장**, 장면 이름을 **Main**를 선택 하 고 **저장**합니다.

## <a name="chapter-3---setup-the-project-settings"></a>3 장-설치 프로젝트 설정

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

이 챕터에 설정 데 도움이 되는 일부 Unity 프로젝트 설정은 Windows Holographic SDK 개발에 대 한 대상입니다. 또한 일부 품질 설정을 응용 프로그램에 대 한 설정입니다. 마지막으로, Windows 스토어에는 빌드 대상 설정이 되도록 합니다.

### <a name="unity-performance-and-quality-settings"></a>Unity 성능 및 품질 설정

**HoloLens에 대 한 unity 품질 설정**

![HoloLens에 대 한 unity 품질 설정](images/qualitysettings.png) 

HoloLens에 높은 프레임 속도 유지 관리 하므로 중요 한 이므로 가장 빠른 성능을 위해 조정 품질 설정 하려고 합니다. 성능 정보를 자세한 [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)합니다.
1. 선택 **편집 > 프로젝트 설정 > 품질**
2. 선택 합니다 **드롭다운** 아래를 **Windows 스토어** 로고 및 선택 **매우 낮음**합니다. Windows 스토어 열 및 빠른 행의 상자에 녹색 때 설정이 올바르게 적용 됩니다 것을 알 수 있습니다.

**폐색 표시를 대상으로 하는 혼합된 현실 응용 프로그램에 대 한**, 품질 설정을 기본값으로 두면 됩니다.

### <a name="target-windows-10-sdk"></a>대상 Windows 10 SDK

**대상 Windows Holographic SDK**

![대상 Windows Holographic SDK](images/xrsettings.png) 

Unity 내보내기 하려는 앱을 만들어야 알 수 있도록 해야는 [몰입 형 뷰](app-views.md) 2D 보기 대신 합니다. 이 작업을 수행 Unity에서 가상 현실 지원을 사용 하도록 설정 하 여 Windows 10 SDK를 대상으로 합니다.
1. 로 이동 **편집 > 프로젝트 설정 > 플레이어**합니다.
2. 에 **검사기 패널** 플레이어 설정에 대 한 선택 합니다 **Windows 스토어** 아이콘입니다.
3. 확장 된 **xr 하이 설정을** 그룹입니다.
4. 에 **렌더링** 섹션을 **가상 현실 지원** 새 추가 하려면이 확인란을 **가상 현실 Sdk** 목록.
5. 확인 **Windows Mixed Reality** 목록에 나타납니다. 그렇지 않은 경우 선택 합니다 **+** 목록의 맨 아래에 있는 단추를 선택 **Windows Mixed Reality**합니다.

>[!NOTE]
>표시 되지 않으면 합니다 **Windows 스토어** 아이콘을 Windows 스토어.NET 스크립팅 백 엔드를 설치 하기 전에 선택한 있는지 다시 확인 합니다. 그렇지 않은 경우 적절 한 Windows 설치를 사용 하 여 Unity를 다시 설치 해야 할 수 있습니다.

**.NET 구성 확인**

![.NET 구성 확인](images/configoptions-375px.png)

1. 로 이동 **편집 > 프로젝트 설정 > 플레이어** (될 수 있습니다이 이전 단계에서).
2. 에 **검사기 패널** 플레이어 설정에 대 한 선택 합니다 **Windows 스토어** 아이콘입니다.
3. 에 **기타 설정** 구성 섹션, 했는지 **스크립팅 백 엔드** 로 설정 된 **.NET**

적용 되는 모든 프로젝트 설정을 가져오는의 멋진 작업입니다. 다음으로, 추가 홀로그램 주세요!

## <a name="chapter-4---create-a-cube"></a>4-장을 큐브 만들기

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Unity 프로젝트에서 큐브를 만드는 Unity에서 다른 개체를 만들 때 처럼 됩니다. 큐브는 사용자 앞에 배치 하면 Unity의 좌표 시스템을 실제-Unity의 1 미터 인 실제 환경에서 약 1 미터에 매핑되므로 쉽습니다.
1. 왼쪽된 위 모퉁이에 **계층** 패널에서 합니다 **만들기** 드롭다운 선택 **3D 개체 > 큐브**합니다.
2. 새로 만든 선택 **큐브** 에 **계층** 패널
3. 에 **검사기** 찾을 합니다 **변환** 구성 요소 및 변경 **위치** 에 (**X**: 0, **Y**: 0, **Z**: 2). *이 배치 큐브 2m 사용자의 시작 위치 앞에 합니다.*
4. 에 **변환** 구성 요소 변경 **회전** 에 (**X**: 45, **Y**: 45, **Z**: 45) 및 변경 **크기 조정** 를 (**X**: 0.25, **Y**: 0.25, **Z**: 0.25). *0.25 미터제로 바뀌는 큐브 크기를 조정 합니다.*
5. 장면 변경 내용을 저장 하려면 선택 **파일 > 저장 장면**합니다.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Unity 편집기에서 장치의-5 장 확인

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

이제 큐브를 만든 장치에서 빠른 검사를 수행 하는 시간입니다. Unity 편집기 내에서 직접이 수행할 수 있습니다.

### <a name="initial-setup"></a>초기 설치
1. Unity에서 개발 PC에서 엽니다 **파일 > 빌드 설정** 창입니다.
2. 변경 **플랫폼** 하 **유니버설 Windows 플랫폼** 를 클릭 하 고 **스위치 플랫폼**

### <a name="for-hololens-use-unity-remoting"></a>HoloLens 원격 Unity를 사용 합니다.
1. 에 HoloLens에서 설치 하 고 실행 합니다 [Holographic 원격 플레이어](holographic-remoting-player.md), Windows 스토어에서 사용할 수 있습니다. 장치에서 응용 프로그램을 시작 하 고 대기 상태로 전환 하 고 장치의 IP 주소를 표시 합니다. IP 아래로 note 합니다.
2. 오픈 **창 > xr 하이 > Holographic 에뮬레이션**합니다.
3. 변경 **에뮬레이션 모드** 에서 **None** 하 **장치에 원격**합니다.
4. **원격 컴퓨터**, 앞서 언급 했 듯이 HoloLens의 IP 주소를 입력 합니다.
5. **연결**을 클릭합니다.
6. 확인 합니다 **연결 상태** 녹색으로 바뀝니다 **Connected**합니다.
7. 이제 클릭할 수 있습니다 **재생** Unity 편집기에서.

이제 장치에서 및 편집기에서 큐브를 볼 수 됩니다. 일시 중지 하 고, 개체를 검사 하 고, 상황을 기본적으로 이기 때문에 편집기에서 앱을 실행 된 것 처럼 하지만 비디오, 오디오 및 호스트 컴퓨터와 장치 간의 네트워크를 통해 앞뒤로 전송 장치 입력을 사용 하 여 디버깅할 수 있습니다.

### <a name="for-other-mixed-reality-supported-headsets"></a>다른 혼합된 현실 헤드셋을 지원합니다.

1. 헤드셋을 개발 PC에 USB 케이블 및 HDMI를 사용 하 여 연결 하거나 포트 케이블을 표시 합니다.
2. 시작 합니다 **혼합 현실 포털** 첫 실행된 경험 완료를 확인 합니다.
3. Unity에서 재생 단추를 눌러 지금 있습니다.

이제 편집기에서 혼합된 현실 헤드셋에 큐브 렌더링을 볼 수 됩니다.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>-6 장 빌드하고 Visual Studio에서 장치에 배포

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

Visual studio 프로젝트를 컴파일 및 대상 장치에 배포할 준비가 됩니다.

### <a name="export-to-the-visual-studio-solution"></a>Visual Studio 솔루션을 내보내려면
1.  오픈 **파일 > 빌드 설정** 창입니다.
2.  클릭 **열기 장면 추가** 장면에 추가 합니다.
3.  변경 **플랫폼** 하 **유니버설 Windows 플랫폼** 누릅니다 **플랫폼 전환**합니다.
4.  **Windows 스토어** 설정을 위해 **SDK** 됩니다 **유니버설 10**합니다.
5.  대상 장치를 둡니다 **모든 장치** 폐색 표시 또는 전환에 대 한 **HoloLens**합니다.
6.  **UWP 빌드 형식** 있어야 **D3D**합니다.
7.  **UWP SDK** 으로 유지할 수 없습니다 **가장 최근에 설치 된**합니다.
8.  확인할 **Unity C# 프로젝트** 디버깅에서 합니다.
9.  **빌드**를 클릭합니다.
10. 파일 탐색기에서 클릭 **새 폴더** 는 폴더의 이름을 **"App"** 합니다.
11. 사용 하 여는 **앱** 선택한 폴더를 클릭 합니다 **폴더 선택** 단추입니다.
12. Unity 완료 되 면을 빌드하는 Windows 파일 탐색기 창이 나타납니다.
13. 엽니다는 **앱** 파일 탐색기에서 폴더입니다.
14. 생성 된 Visual Studio 솔루션 (이 예제의 MixedRealityIntroduction.sln) 열기

### <a name="compile-the-visual-studio-solution"></a>Visual Studio 솔루션

마지막으로 내보낸된 Visual Studio 솔루션을 컴파일, 배포 하 고 장치에서이 사용해 보세요.
1. 대상을 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **디버그** 하 **릴리스** 들어오고 **ARM** 에 **X86**합니다.

에뮬레이터 및 장치에 배포 하기 위한 지침을 다릅니다. 설치와 일치 하는 지침을 따릅니다.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Wi-fi를 통해 혼합된 현실 장치에 배포
1. 옆에 화살표를 클릭 합니다 **로컬 컴퓨터** 단추를 선택한 하 고 배포 대상을 변경할 **원격 컴퓨터**합니다.
2. 혼합된 현실 장치의 IP 주소를 입력 하 고 변경할 **인증 모드** HoloLens에 대 한 유니버설 (암호화 되지 않은 프로토콜)를 하 고 **Windows** 다른 장치에 대 한 합니다.
3. 클릭 **디버그 > 디버깅 하지 않고 시작**합니다.

**HoloLens에 대 한**처음으로이 경우 장치에 배포 해야 쌍 [Visual Studio를 사용 하 여](using-visual-studio.md)입니다.

### <a name="deploy-to-mixed-reality-device-over-usb"></a>혼합된 현실 장치에 USB를 통해 배포

USB 케이블을 통해 장치 연결 되어 있는지 확인 합니다.
1. **HoloLens에 대 한**, 옆에 화살표를 클릭 합니다 **로컬 컴퓨터** 단추를 선택한 하 고 배포 대상을 변경할 **장치**합니다.
2. **사용자 PC에 연결 하는 폐색 장치를 대상으로 하는 것에 대 한**, 로컬 컴퓨터 설정을 유지 합니다. 했는지 확인 합니다 **혼합 현실 포털** 실행 합니다.
3. 클릭 **디버그 > 디버깅 하지 않고 시작**합니다.

### <a name="deploy-to-emulator"></a>에뮬레이터에 배포
1. 옆에 화살표를 클릭 합니다 **장치** 단추 및 드롭다운 선택 목록에서 **HoloLens 에뮬레이터**합니다.
2. 클릭 **디버그 > 디버깅 하지 않고 시작**합니다.

### <a name="try-out-your-app"></a>앱을 사용해

에 앱을 배포 했으므로 큐브 주위의 모든 이동 하 고는 사용자 앞에 전 세계에 유지 되는 관찰 합니다.

## <a name="see-also"></a>참조
* [Unity 개발 개요](unity-development-overview.md)
* [Unity 및 Visual Studio를 사용 하 여 작업에 대 한 모범 사례](best-practices-for-working-with-unity-and-visual-studio.md)
* [MR Basics 101](holograms-101.md)
* [MR Basics 101E](holograms-101e.md)
