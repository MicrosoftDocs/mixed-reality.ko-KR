---
title: HoloLens 알려진 문제
description: HoloLens 개발자에 게 영향을 줄 수 있는 알려진 문제의 목록입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 07/10/2019
ms.topic: article
keywords: 문제 해결, 알려진 문제, 도움말
ms.openlocfilehash: 9ec15957b75ca3ec51dd01f5b9b4bc7371912c5a
ms.sourcegitcommit: a11999e92e4e87516a6dcceabc2c5ed7642f1fd9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68887265"
---
# <a name="hololens-known-issues"></a>HoloLens 알려진 문제

이 목록은 개발자에 게 영향을 주는 HoloLens의 알려진 문제에 대 한 현재 목록입니다. 이상한 동작이 표시 되는 경우 먼저 여기를 확인 하세요. 이 목록은 새로운 문제가 검색 되거나 보고 되거나 이후 HoloLens 소프트웨어 업데이트에서 문제가 해결 될 때 업데이트 됩니다.

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>Visual Studio를 통해 HoloLens에 연결 하 고 배포할 수 없습니다.

>[!NOTE]
>마지막 업데이트: 8/8 @ 5:11PM-이 문제에 대 한 수정 사항이 포함 된 Visual Studio에서 VS 2019 버전 16.2을 릴리스 했습니다. 이 오류가 발생 하지 않도록 최신 버전으로 업데이트 하는 것이 좋습니다.

Visual Studio에는이 문제에 대 한 수정 사항이 포함 된 VS 2019 버전 16.2이 릴리스 되었습니다. 이 오류가 발생 하지 않도록 최신 버전으로 업데이트 하는 것이 좋습니다.

문제 근본 원인: Visual studio 2015 또는 Visual Studio 2017의 초기 릴리스를 사용 하 여 HoloLens에 응용 프로그램을 배포 하 고 디버그 한 다음, 나중에 동일한 HoloLens로 최신 버전의 Visual Studio 2017 또는 Visual Studio 2019를 사용 하는 사용자는 영향을 받게 됩니다. 최신 버전의 Visual Studio에서는 새 버전의 구성 요소를 배포 하지만 이전 버전의 파일은 장치에 남아 있으므로 최신 버전이 실패 합니다.  이로 인해 다음과 같은 오류 메시지가 나타납니다. DEP0100: 대상 장치에서 개발자 모드를 사용 하도록 설정 했는지 확인 하세요. 80004005 오류로 인해에서 <ip> 개발자 라이선스를 가져올 수 없습니다.
 
**해결 방법**: 

팀이 현재 수정 작업을 진행 중입니다. 그 동안에는 다음 단계를 사용 하 여 문제를 해결 하 고 배포 및 디버깅을 차단 해제 하는 데 도움이 될 수 있습니다.  
1. Visual Studio를 엽니다.
2. 파일 > 새로 만들기-> 프로젝트
3. Visual C# > Windows 데스크톱-> 콘솔 앱 (.NET Framework)
4. 프로젝트에 이름 (예: HoloLensDeploymentFix)을 지정 하 고 프레임 워크가 .NET Framework 4.5 이상으로 설정 되었는지 확인 한 다음 확인을 클릭 합니다.
5. 솔루션 탐색기에서 참조 노드를 마우스 오른쪽 단추로 클릭 하 고 다음 참조를 추가 합니다. ' 찾아보기 ' 섹션을 클릭 하 고 ' 찾아보기 ... '를 클릭 합니다. 단추):
    ```
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Deploy.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\Microsoft.Tools.Connectivity.dll
    C:\Program Files (x86)\Windows Kits\10\bin\10.0.18362.0\x86\SirepInterop.dll
    ```
    >[!NOTE]
    >10.0.18362.0가 설치 되어 있지 않은 경우에는 최신 버전을 사용 합니다.
 
6. 솔루션 탐색기에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 > 기존 항목 추가를 선택 합니다.
 
7. C:\Program Files (x86) \Windows Kits\10\bin\10.0.18362.0\x86로 이동 하 고 필터를 "모든 파일 (\*.)"로 변경 합니다.\*
 
8. SirepClient 및 SshClient를 둘 다 선택 하 고 "추가"를 클릭 합니다.
 
9. 솔루션 탐색기에서 두 파일을 찾아서 선택 하 고 (파일 목록의 맨 아래에 있어야 함) "속성 창 출력 디렉터리로 복사"를 "항상 복사"로 변경 합니다.
 
10. 파일 맨 위에 있는 ' using ' 문의 기존 목록에 다음을 추가 합니다. 
    ```
    using Microsoft.Tools.Deploy;
    using System.Net;
    ```
 
11. "Static void Main (...)" 내부에 다음 코드를 추가 합니다.
    ```
    RemoteDeployClient client = RemoteDeployClient.CreateRemoteDeployClient();
    client.Connect(new ConnectionOptions()
    {
        Credentials = new NetworkCredential("DevToolsUser", string.Empty),
        IPAddress = IPAddress.Parse(args[0])
    });
    client.RemoteDevice.DeleteFile(@"C:\Data\Users\DefaultAccount\AppData\Local\DevelopmentFiles\VSRemoteTools\x86\CoreCLR\mscorlib.ni.dll");
    ```
12. 빌드 > 솔루션 빌드
 
13. 컴파일된 .exe를 포함 하는 폴더 (예: C:\MyProjects\HoloLensDeploymentFix\bin\Debug)에 대 한 명령 프롬프트를 엽니다.
 
14. 실행 파일을 실행 하 고 장치의 IP 주소를 명령줄 인수로 제공 합니다.  (USB를 통해 연결 된 경우 127.0.0.1을 사용할 수 있습니다. 그렇지 않으면 장치의 WiFi IP 주소를 사용 합니다.)  예: "HoloLensDeploymentFix 127.0.0.1"
 
15. 도구가 메시지 없이 종료 된 경우 (몇 초 밖에 걸리지 않음) 이제 Visual Studio 2017 이상에서 배포 하 고 디버그할 수 있습니다.  계속 해 서 도구를 사용 해야 하는 것은 아닙니다.

사용할 수 있게 되 면 추가 업데이트를 제공 합니다.

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>HoloLens에서 Microsoft Store 및 앱을 시작 하는 문제

>[!NOTE]
>마지막 업데이트: 4/2 @ 10 AM-문제가 해결 되었습니다. 

HoloLens에서 Microsoft Store 및 앱을 시작 하려고 하면 문제가 발생할 수 있습니다. 백그라운드 앱 업데이트가 특정 시퀀스에서 최신 버전의 프레임 워크 패키지를 배포 하는 동안 해당 종속 앱 중 하나 이상이 실행 중일 때 문제가 발생 함을 확인 했습니다. 이 경우 자동 앱 업데이트는 이전 버전의 프레임 워크를 사용 하는 실행 중인 모든 앱에 대해 올바르게 업데이트 되지 않는 .NET 네이티브 Framework (version 10.0.25531 to 10.0.27413)의 새 버전을 제공 했습니다.  프레임 워크 업데이트에 대 한 흐름은 다음과 같습니다.

1.  새 프레임 워크 패키지가 저장소에서 다운로드 되 고 설치 됩니다.
2.  이전 프레임 워크를 사용 하는 모든 앱은 최신 버전을 사용 하도록 ' 업데이트 ' 됩니다.

완료 전에 2 단계가 중단 되 면 최신 프레임 워크가 등록 되지 않은 모든 앱이 시작 메뉴에서 시작 되지 않습니다.  HoloLens의 모든 앱이이 문제의 영향을 받을 수 있다고 생각 합니다.

일부 사용자가 중지 된 앱을 닫고 피드백 허브, 3D 뷰어 또는 사진과 같은 기타 앱을 시작 하 여 문제를 해결 하는 것을 보고 했습니다. 그러나이 문제는 100%의 시간 동안 작동 하지 않습니다.

이 문제로 인해 업데이트 자체가 발생 하지 않았지만, .NET 네이티브 framework 업데이트를 잘못 처리 하는 OS의 버그가 발생 하 여 근본 원인이 되었습니다. 수정 사항을 확인 하 고 픽스를 포함 하는 업데이트 (OS 버전 17763.380)를 릴리스 했습니다. 

장치에서 업데이트를 사용할 수 있는지 확인 하려면 다음을 수행 하십시오.

1.  "설정" 앱으로 이동 하 여 "& 보안 업데이트"를 엽니다.
2.  "업데이트 확인"을 클릭 합니다.
3.  17763.380에 대 한 업데이트를 사용할 수 있는 경우이 빌드로 업데이트 하 여 앱 중단 버그에 대 한 픽스를 수신 하세요.
4.  이 버전의 OS를 업데이트할 때 앱이 예상 대로 작동 해야 합니다.

또한 모든 HoloLens OS 릴리스와 마찬가지로의 Microsoft 다운로드 센터 https://aka.ms/hololensdownload/10.0.17763.380 에 ffu 이미지를 게시 했습니다. 

업데이트를 수행 하지 않으려는 경우 3/29 Microsoft Store UWP 앱의 새 버전을 릴리스 했습니다. 스토어의 업데이트 된 버전이 있으면 다음을 수행 합니다.

1) 저장소를 열고 로드 되는지 확인 합니다.
2) 블 룸 제스처를 사용 하 여 메뉴를 엽니다.
3) 이전에 중단 된 앱을 열려고 시도 합니다.
3) 여전히 시작할 수 없는 경우 손상 된 앱의 아이콘을 탭 하 고 누른 채 제거를 선택 합니다.
4) 스토어에서 이러한 앱을 설치 합니다.

장치에서 여전히 앱을 로드할 수 없는 경우 다음을 수행 하 여 다운로드 센터를 통해 .NET 네이티브 Framework 및 런타임 버전을 테스트용으로 로드 수 있습니다.

1)  Microsoft 다운로드 센터에서 [이 zip 파일](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) 을 다운로드 하세요.  압축을 푸는 경우 두 개의 파일이 생성 됩니다.  Microsoft .NET 네이티브. m a. m. m. m a.
2)  장치가 dev의 잠금 해제 상태 인지 확인 하세요.  [여기](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)에서 이러한 작업을 수행 하기 위한 지침을 수행 하기 전에 수행 하지 않은 경우에는이 작업을 수행 합니다.
3)  그런 다음 Windows 장치 포털로 이동 하려고 합니다.  USB를 통해이 작업을 수행 하 고 브라우저에를 입력 http://127.0.0.1:10080 하 여이 작업을 수행 하는 것이 좋습니다.  
4)  Windows 장치 포털을 설치한 후 다운로드 한 두 파일을 "로드" 해야 합니다.  이렇게 하려면 "앱" 섹션에 도달할 때까지 왼쪽 막대를 아래로 이동 하 여 "앱"을 클릭 해야 합니다.
5)  그러면 아래와 비슷한 화면이 표시 됩니다.  "응용 프로그램 설치" 섹션으로 이동 하 여 해당 두 APPX 파일의 압축을 푼 위치를 찾습니다.  한 번에 하나씩만 수행할 수 있으므로 첫 번째 항목을 선택한 후 배포 섹션에서 "이동"을 클릭 합니다.  그런 다음 두 번째 APPX 파일에 대해이 작업을 수행 합니다. 
  ![테스트용으로 로드 된 앱을 설치 하는 Windows 장치 포털](images/20190322-DevicePortal.png)<br>
6)  이 시점에서 응용 프로그램이 다시 작업을 시작 하 고 스토어에도 액세스할 수 있다고 생각 합니다.
7)  일부 경우에는 영향을 받는 앱이 시작 되기 전에 3D 뷰어 앱을 시작 하는 추가 단계를 실행 해야 합니다. 

이 문제를 해결 하기 위해 프로세스를 완료 한 후에 감사 드립니다. 그러면 커뮤니티와 함께 계속 작업 하 여 성공적인 혼합 현실 환경을 만들 수 있습니다.

## <a name="connecting-to-wifi"></a>WiFi에 연결

OOBE & 설정 중에는 2 분의 자격 증명 제한 시간이 있습니다. 2 분 이내에 사용자 이름/암호를 입력 해야 합니다. 그렇지 않으면 사용자 이름 필드는 자동으로 지워집니다.

긴 암호를 입력할 때는 Bluetooth 키보드를 사용 하는 것이 좋습니다.

## <a name="device-update"></a>장치 업데이트
* 새 업데이트 후 30 초 후 셸이 한 번 사라질 수 있습니다. **블 룸** 제스처를 수행 하 여 세션을 다시 시작 하세요.

## <a name="visual-studio"></a>Visual Studio
* 최신 버전의 Visual Studio 용 [도구 설치](install-the-tools.md) 를 참조 하 여 HoloLens 개발에 권장 합니다.
* Visual Studio에서 HoloLens에 앱을 배포할 때 다음 오류가 표시 될 수 있습니다. **사용자 매핑 섹션이 열려 있는 파일에 대해서는 요청한 작업을 수행할 수 없습니다. (예외가 발생한 HRESULT: 0x800704C8)** . 이 문제가 발생 하는 경우 다시 시도 하면 배포가 일반적으로 성공 합니다.

## <a name="emulator"></a>에뮬레이터
* Microsoft Store의 모든 앱은 에뮬레이터와 호환 되지 않습니다. 예를 들어, 에뮬레이터에서 젊은 Conker 및 조각은 재생할 수 없습니다.
* 에뮬레이터에서는 PC 웹캠를 사용할 수 없습니다.
* Windows 장치 포털의 실시간 미리 보기 기능은 에뮬레이터에서 작동 하지 않습니다. 여전히 혼합 현실 비디오 및 이미지를 캡처할 수 있습니다.

## <a name="unity"></a>Unity
* HoloLens 개발에 권장 되는 최신 버전의 Unity 용 [도구 설치](install-the-tools.md) 를 참조 하세요.
* Unity HoloLens Technical Preview의 알려진 문제는 [HoloLens Unity 포럼](http://forum.unity3d.com/threads/known-issues.394627/)에 설명 되어 있습니다.

## <a name="windows-device-portal"></a>Windows Device Portal
* 혼합 현실 캡처의 실시간 미리 보기 기능은 몇 초 동안 대기 시간을 나타낼 수 있습니다.
* 가상 입력 페이지에서 가상 제스처 섹션 아래의 제스처 및 스크롤 컨트롤이 작동 하지 않습니다. 이를 사용 하면 아무런 영향을 주지 않습니다. 동일한 페이지의 가상 키보드가 제대로 작동 합니다.
* 설정에서 개발자 모드를 사용 하도록 설정한 후 장치 포털을 켜는 스위치를 사용 하도록 설정 하는 데 몇 초 정도 걸릴 수 있습니다.

## <a name="api"></a>API
* 응용 프로그램에서 사용자의 [포커스 지점을](focus-point-in-unity.md) 설정 하거나, 정상에서 카메라로 이동 하는 경우 Holograms는 혼합 현실 사진 또는 비디오 캡처에 표시 되지 않습니다. Windows에서이 버그가 수정 될 때까지 응용 프로그램에서 [포커스 지점을](focus-point-in-unity.md) 적극적으로 설정 하는 경우 평면을 반대 방향 카메라 앞으로 설정 합니다 (예: normal =-camera).

## <a name="xbox-wireless-controller"></a>Xbox 무선 컨트롤러
* Xbox 무선 컨트롤러를 HoloLens와 함께 사용 하려면 먼저 업데이트 해야 합니다. 컨트롤러를 HoloLens와 페어링 하기 전에 [최신 상태](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) 인지 확인 합니다.
* Xbox 무선 컨트롤러를 연결 하는 동안 HoloLens를 다시 부팅 하면 컨트롤러가 HoloLens에 자동으로 다시 연결 되지 않습니다. 3 분 후에 컨트롤러의 전원이 꺼질 때까지 가이드 단추 표시등이 느리게 깜박입니다. 컨트롤러를 즉시 다시 연결 하려면 표시등이 꺼질 때까지 가이드 단추를 눌러 컨트롤러의 전원을 끕니다. 컨트롤러의 전원을 다시 켤 때 HoloLens에 다시 연결 됩니다.
* Xbox 무선 컨트롤러를 연결 하는 동안 HoloLens가 대기 모드로 전환 되 면 컨트롤러의 모든 입력은 HoloLens를 절전 모드에서 해제 합니다. 이 작업을 사용 하는 경우 컨트롤러의 전원을 꺼서이를 방지할 수 있습니다.
