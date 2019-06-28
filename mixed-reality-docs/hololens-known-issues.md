---
title: HoloLens 알려진 문제
description: HoloLens 개발자 영향을 줄 수 있는 알려진 문제 목록입니다.
author: mattzmsft
ms.author: mazeller
ms.date: 06/14/2019
ms.topic: article
keywords: 문제 해결, 알려진 문제, 도움말
ms.openlocfilehash: fd70171a908dab016b375e2207436dc11d625af9
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414347"
---
# <a name="hololens-known-issues"></a>HoloLens 알려진 문제

이것이 현재 HoloLens에 영향을 주는 개발자를 위한 알려진된 문제 목록입니다. 보려면 여기를 확인 한 부적절 한 동작 표시 되는 경우. 이 목록은 새로운 문제는 발견 되거나 보고 또는 이후 HoloLens 소프트웨어 업데이트 문제를 해결 하는 대로 업데이트 된 유지 됩니다.

## <a name="unable-to-connect-and-deploy-to-hololens-through-visual-studio"></a>연결을 Visual Studio를 통해 HoloLens에 배포할 수 없습니다.

>[!NOTE]
>마지막 업데이트 날짜: 6/14 오후 6 시-@ 문제 조사 중입니다.

HoloLens 및 Visual Studio 팀은 사용자가 Visual Studio를 통해 HoloLens 장치에 배포 하지 못하게 할 수 있는 문제를 조사 합니다.
 
배포 단계에서 사용자가 보고할 HoloLens 장치 나누고 개발자 컴퓨터에도 불구 하 고 다음 오류 메시지가 *개발자 모드* 사용 하도록 설정 합니다.

*DEP0100: 대상 장치에 개발자 모드가 사용 하도록 설정 해야 합니다. 개발자 라이선스를 얻지 못했습니다 <device IP> 80004005 오류로 인해 합니다.*
 
**해결 방법**: 
 
사용자가 해당 문제를 해결 하는 장치를 다시 설정 하는 모든 경우에 작동을 보장할 수 없습니다를 보고 합니다. 장치를 재설정 하는 방법을 찾을 수 있습니다 [여기](https://support.microsoft.com/en-us/help/13452/hololens-restart-reset-or-recover-hololens)합니다.
 
문제는 근본 원인인 즉시 업데이트로 제공 됩니다. 

## <a name="issues-launching-the-microsoft-store-and-apps-on-hololens"></a>Microsoft Store 및 HoloLens에 앱을 시작 하는 문제

>[!NOTE]
>마지막 업데이트 날짜: 4 월 2 @ 오전 10 시-문제를 해결 합니다. 

Microsoft Store 및 HoloLens에 앱을 시작 하려고 할 때 문제가 발생할 수 있습니다. 백그라운드 앱 업데이트 중 하나는 특정 시퀀스에서 프레임 워크 패키지의 최신 버전을 배포 또는 해당 종속 된 앱 중 계속 실행 하는 경우 문제가 발생 하 확인 했습니다. 이 경우 새 버전 (버전 10.0.25531를 10.0.27413)는.NET 네이티브 프레임 워크의 배달 자동 앱 업데이트 잘못 프레임 워크의 이전 버전을 사용 하는 모든 실행 중인 앱에 대 한 업데이트를 실행 하는 앱을 발생 합니다.  프레임 워크 업데이트에 대 한 흐름은 다음과 같습니다.-

1.  새 프레임 워크 패키지를 스토어에서 다운로드 및 설치
2.  이전 프레임 워크를 사용 하 여 모든 앱은 ' 업데이트 ' 최신 버전을 사용 하려면

2 단계 완료 되기 전에 중단 되는 경우 시작 메뉴에서 시작할 수 없는 최신 프레임 워크에 등록 되지 않은 모든 앱 실패 합니다.  HoloLens에 앱이이 문제로 인해 저하 될 수 있습니다 하는 것이 믿습니다.

그러나 일부 사용자에 게는 응답이 없는 앱을 닫기 피드백 허브 같은 다른 앱을 시작 하 고 3D 뷰어 또는 사진 확인 있으며 문제를 보고 합니다.이 작동 하지 않습니다 100%의 시간입니다.

했습니다 근본 원인인이 문제를 발생 시 키 지 버그 하지만 업데이트 자체를 올바르게 처리 되 고.NET 네이티브 프레임 워크 업데이트 발생 하는 OS에서. 수정 프로그램을 확인 하 고 업데이트 (OS 버전 17763.380) 릴리스를 발표할 기쁩니다 수정 사항을 포함 합니다. 

장치를 업데이트 하세요 걸릴 수 있습니다를 보려면:

1.  "설정" 앱으로 이동 하 고 "업데이트 및 보안"을 엽니다
2.  "업데이트 확인"을 클릭 합니다.
3.  17763.380 업데이트를 사용할 수 있는 경우 업데이트 하세요 앱 중단 버그 픽스를 받으려면이 빌드에
4.  운영 체제의이 버전으로 업데이트 되 면 앱은 예상 대로 작동 해야 합니다.

또한 모든 HoloLens OS 릴리스를 사용 하 여 마찬가지로에서는 게시 된 FFU 이미지는 Microsoft 다운로드 센터 https://aka.ms/hololensdownload/10.0.17763.380 합니다. 

업데이트 하려는 경우 3/29 일부 터 Microsoft Store UWP 앱의 새 버전을 릴리스 했습니다. 있다면 저장소의 업데이트 된 버전.

1) 스토어를 열고 로드 되는지 확인 합니다.
2) Bloom 제스처를 사용 하 여 메뉴를 엽니다.
3) 이전에 손상 된 앱을 열려고 시도
3) 여전히 시작할 수 없습니다, 하는 경우 탭 및 손상 된 앱의 아이콘을 보유 하 고 제거를 선택 합니다.
4) Resinstall 저장소에서 이러한 앱.

장치의 앱을 로드 하는 데 수 없는 경우 수행 하 여 다운로드 센터를 통해.NET 네이티브 프레임 워크 및 런타임 버전을 테스트용으로 로드를 수 있습니다.

1)  다운로드 하세요 [이 zip 파일](http://download.microsoft.com/download/8/5/C/85C23745-794C-419D-B8D7-115FBCCD6DA7/netfx_1.7.zip) Microsoft 다운로드 센터에서.  압축을 푸는 두 파일이 생성 됩니다.  Microsoft.NET.Native.Runtime.1.7.appx 및 Microsoft.NET.Native.Framework.1.7.appx
2)  장치가 개발자 잠금 해제 인지를 확인 하세요.  이렇게 하려면 지침은 전에 수행 하지 않았다면 [여기](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Fwindows%2Fmixed-reality%2Fusing-the-windows-device-portal&data=02%7C01%7Cjalynch%40microsoft.com%7C3622a462ebd04870fccb08d6ae94cad6%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636888351416725140&sdata=ZB6Zdx9GV95PcU6FAVgWaP3eQNMsyIc%2FbNDEby3Sb8A%3D&reserved=0)합니다.
3)  그런 다음 Windows Device Portal 하려고 합니다.  USB를 통해이 작업을 수행 하는 것이 좋습니다 및을 수행 하면 입력 하 여 http://127.0.0.1:10080 브라우저에 있습니다.  
4)  Windows Device Portal에서는 등록 해야 "테스트용 로드"를 만든 후 두 다운로드 하는 파일입니다.  작업을 수행 하는 "앱" 섹션을 가져와서 "앱"을 클릭할 때까지 왼쪽된 사이드 바 아래로 이동 해야 합니다.
5)  다음 화면이 표시 됩니다는 비슷한는 아래.  이러한 두 APPX 파일의 압축을 푼 찾아 "앱 설치" 라는 섹션으로 이동 하려고 합니다.  한 번에 하나씩만 수행을 하므로 첫 번째를 선택한 후 다음 "이동" 섹션에서 클릭 배포 합니다.  다음 두 번째 APPX 파일에 대 한이 작업을 수행 합니다. 
  ![테스트용 로드 앱을 설치 하려면 Windows Device Portal](images/20190322-DevicePortal.png)<br>
6)  이 시점에서 응용 프로그램 작업을 다시 시작 해야 하 고 저장소로 가져올 수도 있습니다는 것이 믿습니다.
7)  일부 경우에서는 필요한 영향을 받는 앱이 시작 되기 전에 3D 뷰어 앱을 시작 하는 추가 단계를 실행 합니다. 

이 문제를 해결 하는 프로세스를 통해 발전와 귀 환경을 혼합 현실 성공적으로 만들려면 커뮤니티를 사용 하 여 작업을 계속 하려면 기다려를 드립니다.

## <a name="connecting-to-wifi"></a>WiFi에 연결

OOBE 및 설정 하는 동안에 자격 증명 시간 제한은 2 분입니다. 사용자 이름/암호를 2 분이 고 그렇지 username 필드가 자동으로 지워집니다. 내에 입력 해야 합니다.

Bluetooth 키보드를 사용 하 여 긴 암호를 입력 하는 것이 좋습니다.

## <a name="device-update"></a>장치 업데이트
* 새 업데이트 후 30 초 셸은 한 번 사라질 수 있습니다. 수행 하십시오 합니다 **블 룸** 제스처에 세션을 다시 시작 합니다.

## <a name="visual-studio"></a>Visual Studio
* 참조 [도구를 설치](install-the-tools.md) HoloLens 개발에 권장 되는 Visual Studio의 최신 버전에 대 한 합니다.
* 에 HoloLens에 Visual Studio에서 앱을 배포할 때 오류가 표시 될 수 있습니다. **사용자 매핑 섹션 열려 있는 파일에서 요청된 된 작업을 수행할 수 없습니다. (예외가 발생한 HRESULT: 0x800704C8)** . 이 경우 다시 시도 및 배포는 일반적으로 성공 합니다.

## <a name="emulator"></a>에뮬레이터
* Microsoft Store 모든 앱을 에뮬레이터와 호환 됩니다. 예를 들어 Young Conker 및 조각이 없는 에뮬레이터에서 재생할 수 있습니다.
* 에뮬레이터에서 PC 웹캠을 사용할 수 없습니다.
* 에뮬레이터를 사용 하 여 Windows Device Portal 실시간 미리 보기 기능을 작동 하지 않습니다. 여전히 혼합 현실 비디오 및 이미지를 캡처할 수 있습니다.

## <a name="unity"></a>Unity
* 참조 [도구를 설치](install-the-tools.md) HoloLens 개발에 권장 되는 Unity의 최신 버전에 대 한 합니다.
* Unity HoloLens Technical Preview의 알려진된 문제에 설명 되어는 [HoloLens Unity 포럼](http://forum.unity3d.com/threads/known-issues.394627/)합니다.

## <a name="windows-device-portal"></a>Windows Device Portal
* 혼합 현실 캡처의 실시간 미리 보기 기능에는 몇 초 정도 대기 시간이 발생할 수 있습니다.
* 가상 입력 페이지에서 가상 제스처 섹션 제스처 및 스크롤 컨트롤 작동 하지 않습니다. 사용 하는 효과가 없습니다. 동일한 페이지의 가상 키보드 제대로 작동합니다.
* 설정에서 개발자 모드를 사용 하도록 설정한 후 장치 포털에는 스위치를 사용 하기 전에 몇 초 정도 걸립니다.

## <a name="api"></a>API
* 응용 프로그램을 설정 하는 경우는 [지점 집중](focus-point-in-unity.md) 사용자 또는 수직 camera.forward에 뒤 홀로그램 혼합 현실 캡처 사진 또는 비디오에 표시 되지 것입니다. 이 버그는 응용 프로그램에서 적극적으로 설정 하는 경우, Windows에서 해결 될 때까지 합니다 [지점 집중](focus-point-in-unity.md) 평면 보통 반대 카메라 정방향 설정 되도록 해야 (예: 일반 =-camera.forward).

## <a name="xbox-wireless-controller"></a>Xbox 무선 컨트롤러
* HoloLens를 사용 하 여 사용할 수 있습니다 Xbox 무선 컨트롤러 S는 업데이트 해야 합니다. 준수할 수 있도록 [최신](https://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) 는 HoloLens 사용 하 여 컨트롤러를 연결 하기 전에 합니다.
* Xbox 무선 컨트롤러 연결 되어 있는 동안에 HoloLens를 다시 부팅 하면 컨트롤러는 자동으로 다시 연결 되지 HoloLens에. 가이드 단추는 표시등이 느린 컨트롤러 꺼질 때까지 해제 3 분 후입니다. 컨트롤러 즉시 끄지 광원 해제 될 때까지 가이드 단추를 눌러 컨트롤러를 다시 연결 합니다. 켜면 컨트롤러 다시, HoloLens에 다시 연결 됩니다.
* Xbox 무선 컨트롤러 연결 되어 있는 동안 대기 모드로 전환에 HoloLens, 하는 경우 컨트롤러에 대 한 의견은 HoloLens 절전 모드 해제 됩니다. 완료 되 면 컨트롤러 해제 강화 하 여이 방지할 수 있습니다 사용 합니다.
