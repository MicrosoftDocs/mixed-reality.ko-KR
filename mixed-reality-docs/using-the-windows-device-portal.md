---
title: Windows Device Portal 사용 하 여
description: HoloLens에 대 한 Windows Device Portal 사용 하 여 구성 하 고 Wi-fi 또는 USB를 통해 장치를 원격으로 관리할 수 있습니다. Device Portal은 PC의 웹 브라우저에서 연결 가능한 HoloLens에 있는 웹 서버입니다. 장치 포털에는 HoloLens 및 디버그 관리 앱을 최적화 하는 데 도움이 되는 많은 도구가 포함 되어 있습니다.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows Device Portal, HoloLens
ms.openlocfilehash: f4319e1efa94d90bfb8cc4e5815ffa87fc865a7f
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829998"
---
# <a name="using-the-windows-device-portal"></a>Windows Device Portal 사용 하 여

<table>
<tr>
<th>기능</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (첫 번째 범용)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

HoloLens에 대 한 Windows Device Portal 사용 하 여 구성 하 고 Wi-fi 또는 USB를 통해 장치를 원격으로 관리할 수 있습니다. Device Portal은 PC의 웹 브라우저에서 연결 가능한 HoloLens에 있는 웹 서버입니다. 장치 포털에는 HoloLens 및 디버그 관리 앱을 최적화 하는 데 도움이 되는 많은 도구가 포함 되어 있습니다.

이 설명서는 HoloLens에 대 한 Windows Device Portal 관련 됩니다. 데스크톱 (Windows Mixed Reality 포함)에 대 한 Windows 장치 포털을 사용 하려면 참조 [Windows Device Portal 개요](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>HoloLens Windows Device Portal 사용 하도록 설정

1. HoloLens의 전원을 켜고 디바이스에 배치합니다.
2. [블룸](gestures.md#bloom) 제스처를 수행하여 주 메뉴를 시작합니다.
3. 응시 합니다 **설정** 타일을 수행 합니다 [어 탭](gestures.md#air-tap) 제스처입니다. 사용자 환경에서 앱을 추가할 두 번째 어 탭을 수행 합니다. 앱을 배치한 후 앱 설정이 시작됩니다.
4. **업데이트** 메뉴 항목을 선택합니다.
5. **개발자용** 메뉴 항목을 선택합니다.
6. **개발자 모드**를 사용하도록 설정합니다.
7. [아래로 스크롤하여](gestures.md#composite-gestures) 높이고 **장치 포털**합니다.
8. 설정 하는 Windows Device Portal USB 또는 Wifi를 통해이 HoloLens에 앱을 배포할 수 있도록, 클릭 **쌍** 하 [페어링 PIN을 생성](using-visual-studio.md)합니다. 첫 번째 배포 하는 동안 Visual Studio에 PIN을 입력할 때까지 설정 앱을 PIN 팝업 그대로 둡니다.

   ![Windows Holographic에 대 한 설정 앱에서 개발자 모드가 사용 하도록 설정](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Wi-fi 연결

1. [Wi-fi에 HoloLens 연결할](connecting-to-wi-fi-on-hololens.md)합니다.
2. 장치의 IP 주소를 조회 합니다.
   * 장치의 IP 주소를 찾으려면 **설정 > 네트워크 및 인터넷 > Wi-fi > 고급 옵션**합니다.
3. PC에서 웹 브라우저에서 https://<YOUR_HOLOLENS_IP_ADDRESS>로 이동
   * 브라우저는 다음과 같은 메시지가 표시 됩니다. "이 웹이 사이트의 보안 인증서에 문제가 있습니다". 이 오류는 디바이스 포털에 발행된 인증서가 테스트 인증서이기 때문에 발생합니다. 지금은 이 인증서 오류를 무시하고 계속 진행할 수 있습니다.

## <a name="connecting-over-usb"></a>USB를 통해 연결

1. [도구 설치](install-the-tools.md) PC에 설치 된 Windows 10 개발자 도구를 사용 하 여 Visual Studio 업데이트 1을에 있는지 확인 합니다. 이렇게 하면 USB 연결을 사용할 수 있습니다.
2. HoloLens를 마이크로-USB 케이블로 PC에 연결합니다.
3. PC의 웹 브라우저에서 http://127.0.0.1:10080로 이동합니다.

## <a name="connecting-to-an-emulator"></a>에뮬레이터에 연결

에뮬레이터로 디바이스 포털을 사용할 수도 있습니다. 장치 포털에 연결 하려면 사용 합니다 [도구 모음](using-the-hololens-emulator.md)합니다. 다음 아이콘을 클릭합니다. ![열기 장치 포털 아이콘](images/emulator-deviceportal.png) **장치 포털 열기**: 에뮬레이터에서 HoloLens OS에 대 한 Windows Device Portal 엽니다.

## <a name="creating-a-username-and-password"></a>사용자 이름 및 암호 만들기

![Windows Device Portal 대 한 액세스 설정](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Windows Device Portal 대 한 액세스 설정*

HoloLens에서 디바이스 포털에 처음 연결하면 사용자 이름 및 암호를 만들어야 합니다.
1. PC의 웹 브라우저에서 HoloLens의 IP 주소를 입력합니다. 액세스 설정 페이지가 열립니다.
2. 클릭 하거나 탭 **요청 pin** 생성 된 PIN을 가져오려면 HoloLens 표시를 확인 합니다.
3. PIN을 입력 합니다 **장치에 표시 된 PIN** 텍스트 상자에 붙여넣습니다.
4. 디바이스 포털 연결에 사용할 사용자 이름을 입력합니다. MSA(Microsoft 계정) 이름 또는 도메인 이름일 필요는 없습니다.
5. 암호를 입력하고 확인합니다. 암호는 7자 이상이어야 합니다. MSA 또는 도메인 암호일 필요는 없습니다.
6. 클릭 **쌍** Windows Device Portal HoloLens에 연결할 수 있습니다.

언제 든 지가 사용자 이름 또는 암호를 변경 하려는 경우으로 이동 하 여 장치 보안 페이지를 방문 하 여이 프로세스를 반복할 수 있습니다: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm 합니다.

## <a name="security-certificate"></a>보안 인증서

브라우저에 "인증서 오류"가 표시되는 경우 디바이스와 트러스트 관계를 만들어 수정할 수 있습니다.

각 HoloLens는 해당 SSL 연결에 대한 고유의 자체 서명된 인증서를 생성합니다. 기본적으로 이 인증서는 PC의 웹 브라우저에서 신뢰하지 않아 "인증서 오류"가 발생할 수 있습니다. 신뢰하는 Wi-Fi 네트워크 또는 USB를 통해 HoloLens에서 이 인증서를 다운로드하고 PC에서 신뢰할 수 있도록 만들어 안전하게 디바이스에 연결할 수 있습니다.
1. **보안 네트워크 (USB 또는 신뢰 하는 Wi-fi 네트워크)에 있는지 확인 합니다.**
2. 장치 포털에서 "보안" 페이지에서이 장치의 인증서를 다운로드 합니다.
   * 이동할: https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm
3. 에 "신뢰할 수 있는 루트 인증 기관" 저장소 PC에서 인증서를 설치 합니다.
   * Windows 메뉴에서 다음을 입력 합니다. 컴퓨터 인증서를 관리 하 고 애플릿을 시작 합니다.
   * 확장 된 **신뢰할 수 있는 루트 인증 기관** 폴더입니다.
   * 클릭 합니다 **인증서** 폴더입니다.
   * 작업 메뉴에서 선택 합니다. 모든 작업 > 가져오기...
   * 디바이스 포털에서 다운로드한 인증서 파일을 사용하여 인증서 가져오기 마법사를 완료합니다.
4. 브라우저를 다시 시작합니다.

## <a name="device-portal-pages"></a>디바이스 포털 페이지

### <a name="home"></a>홈

![Microsoft HoloLens Windows Device Portal 홈페이지](images/windows-device-portal-home-page-1000px.png)<br>
*Microsoft HoloLens Windows Device Portal 홈페이지*

홈페이지에서 디바이스 포털 세션을 시작합니다. 홈페이지의 왼쪽 탐색 모음에서 다른 페이지에 액세스합니다.

페이지 맨 위에 있는 도구 모음에서 자주 사용하는 상태 및 기능에 대한 액세스를 제공합니다.
* **온라인**: 장치에서 Wi-fi에 연결 되어 있는지 여부를 나타냅니다.
* **Shutdown**: 장치를 해제합니다.
* **다시 시작**: 장치의 전원을 주기입니다.
* **보안**: 장치 보안 페이지를 엽니다.
* **쿨**: 장치의 온도 나타냅니다.
* **A/C**: 청구 및 장치 연결 되어 있는지 여부를 나타냅니다.
* **도움말**: REST 인터페이스 설명서 페이지를 엽니다.

홈페이지에는 다음 정보가 표시됩니다.
* **장치 상태:** 장치의 상태를 모니터링 하 고 오류를 보고 합니다.
* **Windows 정보:** 는 HoloLens의 이름 및 현재 설치 된 Windows 버전을 보여 줍니다.
* **기본 설정** 섹션에는 다음 설정이 포함되어 있습니다.
   * **IPD**: Interpupillary 거리 (IPD) 간격의 직접 미리 볼 때 사용자의 삼아 중심 간 밀리미터 단위로 설정 합니다. 설정은 즉시 적용됩니다. 기본값은 디바이스를 설정할 때 자동으로 계산되었습니다.
   * **장치 이름**: HoloLens에 이름을 할당 합니다. 이 값을 변경 후에는 디바이스를 다시 부팅해야 적용됩니다. 클릭 한 후 **저장할**, 장치를 즉시 다시 부팅 하거나 나중에 다시 시작 하려는 경우 대화 상자를 묻습니다.
   * **절전 모드 설정을**: 배터리 때 및 장치 연결 된 경우 절전 모드로 전환 하기 전에 대기할 시간 길이 설정 합니다.

### <a name="3d-view"></a>3D 뷰

![Microsoft HoloLens Windows Device Portal 3D 뷰 페이지](images/3dview-1000px.png)<br>
*Microsoft HoloLens Windows Device Portal 3D 뷰 페이지*

3D 뷰 페이지를 사용하여 HoloLens가 사용자의 주변을 해석하는 방법을 확인합니다. 마우스를 사용하여 뷰를 탐색합니다.
* 마우스 왼쪽 단추 클릭 + 마우스; 회전 합니다.
* 클릭 + 마우스 이동: 마우스 오른쪽 단추로
* 확대/축소: 마우스 스크롤입니다.
* **추적 옵션**
   * 확인 하 여 연속 visual 추적을 켜려면 **Force visual 추적**합니다. 
   * **일시 중지** visual 추적을 중지 합니다.
* **옵션을 보려면**: 3D 뷰에서 옵션을 설정 합니다.
  * **추적**: Visual 추적 활성 상태 인지 여부를 나타냅니다.
  * **Floor 표시**: 체크 무늬 floor 평면에 표시 됩니다.
  * **꼭지점이 절 두 체 표시**: 하면 보기 프러스텀을 표시합니다.
  * **안정화 평면 표시**: HoloLens 안정화 동작을 사용 하는 평면에 표시 됩니다.
  * **메시를 보여 줍니다.** : 사용자 환경을 나타내는 공간 매핑 메시를 표시 합니다.
  * **공간 앵커 표시**: 현재 앱에 대 한 공간 앵커를 표시합니다. 가져오고 앵커를 새로 고치려면 [업데이트] 단추를 클릭 해야 합니다.
  * **세부 정보 표시**: 표시를 실시간으로 변경 될 때 해당 위치, 헤드 회전 쿼터 니 및 장치 원본 벡터를 전달 합니다.
  * **전체 화면 단추**: 전체 화면 모드에서 3D 뷰를 보여 줍니다. 전체 화면 보기를 종료하려면 ESC 키를 누릅니다.
* **재구성 화면**: 클릭 하거나 탭 **업데이트** 장치에서 최신 공간 매핑 메시를 표시 합니다. 전체 단계를 완료하는 데 시간이 최대 몇 초 걸릴 수 있습니다. 메시 3D 보기에서 자동으로 업데이트 되지 않습니다 및 수동으로 눌러야 **업데이트** 장치에서 최신 메시를 가져오려고 합니다. 클릭 **저장할** 현재 공간 매핑 메시 PC에서 obj 파일로 저장 합니다.
* **공간 앵커**: 표시 또는 활성화 된 앱에 대 한 공간 앵커를 업데이트 하는 업데이트를 클릭 합니다.

### <a name="mixed-reality-capture"></a>혼합 현실 캡처

![Microsoft HoloLens Windows Device Portal 혼합된 현실 캡처 페이지](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Microsoft HoloLens Windows Device Portal 혼합된 현실 캡처 페이지*

사용 된 [혼합 현실 캡처](mixed-reality-capture.md) 는 HoloLens에서 미디어 스트림 저장 하려면 페이지입니다.
* **설정**: 다음 설정을 확인 하 여 캡처되는 미디어 스트림 제어 합니다.
  * **홀로그램**: 비디오 스트림의 holographic 콘텐츠를 캡처합니다. 홀로그램은 스테레오가 아닌 모노로 렌더링됩니다.
  * **PV 카메라**: 사진/비디오 카메라에서 비디오 스트림을 캡처합니다.
  * **Mic 오디오**: 마이크 배열에서 오디오를 캡처합니다.
  * **앱 오디오**: 현재 실행 중인 앱에서 오디오를 캡처합니다.
  * **미리 보기 품질 라이브**: 화면 해상도, 프레임 속도 및 스트리밍 속도 대 한 실시간 미리 보기를 선택 합니다.
* 클릭 하거나 탭 합니다 **실시간 미리 보기** 캡처 stream에 표시할 단추입니다. **실시간 미리 보기 중지** 캡처 스트림을 중지 합니다.
* 클릭 하거나 탭 **레코드** 혼합 현실 스트림에 기록, 지정 된 설정을 사용 하 여 시작 합니다. **기록을 중지** 녹음/녹화를 종료 하 고 저장 합니다.
* 클릭 하거나 탭 **Take 사진** 캡처 스트림에서 이미지를 계속 수행 합니다.
* **비디오 및 사진**: 장치에서 수행 하는 비디오 및 사진 캡처 목록이 표시 됩니다.

HoloLens 앱은 디바이스 포털에서 실시간 미리 보기를 기록 또는 스트리밍하는 동안 MRC 사진 또는 동영상을 캡처할 수 없습니다.

### <a name="performance-tracing"></a>성능 추적

![Microsoft HoloLens Windows Device Portal 페이지를 추적 하는 성능](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Microsoft HoloLens Windows Device Portal 페이지를 추적 하는 성능*

캡처 [Windows 성능 기록기](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) 에 HoloLens에서 (WPR) 추적 합니다.
* **사용 가능한 프로필**: WPR 프로필 드롭다운 목록 및 클릭 또는 탭에서 선택 **시작** 추적을 시작 합니다.
* **사용자 지정 프로필**: 클릭 하거나 탭 **찾아보기** PC에서 WPR 프로필을 선택 합니다. 추적을 시작하려면 **업로드 및 시작**을 클릭 또는 탭합니다.

중지 추적 중지 링크를 클릭 합니다. 추적 파일 다운로드가 완료 될 때까지이 페이지에 남아 있습니다.

캡처된 ETL 파일은 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx)에서 분석을 위해 열 수 있습니다.

### <a name="processes"></a>프로세스

![Microsoft HoloLens Windows Device Portal 페이지를 처리합니다.](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Microsoft HoloLens Windows Device Portal 페이지를 처리합니다.*

현재 실행 중인 프로세스에 대한 세부 정보를 보여 줍니다. 앱 및 시스템 프로세스 모두 포함합니다.

### <a name="system-performance"></a>시스템 성능

![Microsoft HoloLens Windows Device Portal 시스템 성능 페이지](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Microsoft HoloLens Windows Device Portal 시스템 성능 페이지*

전력 사용량, 프레임 속도 및 CPU 로드와 같은 시스템 진단 정보를 실시간 그래프로 보여 줍니다.

사용 가능한 메트릭은 다음과 같습니다.
* **SoC power**: 즉시 시스템-온칩 power 사용률을 평균 1 분 이상
* **시스템 전원**: 즉시 시스템 전원 사용률을 평균 1 분 이상
* **프레임 속도**: 초당 프레임 초당 VBlanks 및 연속 누락된 VBlanks 누락
* **GPU**: GPU 엔진 사용률, 사용 가능한 총 퍼센트
* **CPU**: 사용 가능한 총 퍼센트
* **I/O**: 읽기 및 쓰기
* **네트워크**: 수신 및 전송
* **메모리**: 사용, 커밋된 총 페이징 및 비페이징

### <a name="apps"></a>앱

![Microsoft HoloLens Windows Device Portal 앱 페이지](images/windows-device-portal-apps-page-1000px.png)<br>
*Microsoft HoloLens Windows Device Portal 앱 페이지*

HoloLens에 설치 된 앱을 관리 합니다.
* **설치 된 앱**: 제거 하 고 앱을 시작 합니다.
* **실행 중인 응용 프로그램**: 현재 실행 중인 앱을 나열 합니다.
* **앱을 설치**: 컴퓨터/네트워크 폴더에서 설치에 대 한 앱 패키지를 선택 합니다.
* **종속성**: 설치 하려는 앱에 대 한 종속성을 추가 합니다.
* **배포**: HoloLens에 선택한 앱 + 종속성을 배포 합니다.

### <a name="app-crash-dumps"></a>응용 프로그램 크래시 덤프

![Windows Device Portal Microsoft HoloLens 앱 크래시 덤프 페이지](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Windows Device Portal Microsoft HoloLens 앱 크래시 덤프 페이지*

이 페이지에서는 테스트용으로 로드된 앱에 대한 크래시 덤프를 수집할 수 있습니다. 확인 합니다 **크래시 덤프를 사용 하도록 설정** 크래시 덤프를 수집 하려는 각 앱에 대 한 확인란을 선택 합니다. 이 페이지로 돌아와서 크래시 덤프를 수집합니다. 덤프 파일 수 [디버깅을 위해 Visual Studio에서 열릴](https://msdn.microsoft.com/library/d5zhxt22.aspx)합니다.

### <a name="file-explorer"></a>파일 탐색기

![Microsoft HoloLens Windows Device Portal 파일 탐색기 페이지](images/fileexplorer-1000px.png)<br>
*Microsoft HoloLens Windows Device Portal 파일 탐색기 페이지*

찾아보기, 업로드 및 파일을 다운로드 하려면 파일 탐색기를 사용 합니다. Visual Studio 또는 장치 포털에서 배포 된 앱에 대 한 그림 폴더 문서 폴더에 로컬 저장소 폴더에 파일을 사용 하 여 작업할 수 있습니다.

### <a name="kiosk-mode"></a>키오스크 모드

>[!NOTE]
>키오스크 모드를 이용 합니다 [Microsoft HoloLens Commercial Suite](commercial-features.md)합니다.

확인 하십시오 합니다 [HoloLens 키오스크 모드로 설정](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) Windows IT Pro Center 문서에 대 한 최신 지침은 Windows Device Portal 통해 키오스크 모드를 사용 하도록 설정 합니다.

### <a name="logging"></a>로깅

![Microsoft HoloLens Windows Device Portal 로깅 페이지](images/windows-device-portal-logging-page-1000px.png)<br>
*Microsoft HoloLens Windows Device Portal 로깅 페이지*

실시간 이벤트 추적에 대 한 Windows (ETW)는 HoloLens에서 관리합니다.

확인 **공급자를 숨기려면** 표시할 합니다 **이벤트** 만 나열 합니다.
* **등록 된 공급자**: 추적 수준과 ETW 공급자를 선택 합니다. 추적 수준은 다음 값 중 하나입니다.
   1. 비정상적인 끝내기 또는 종료
   2. 심각한 오류
   3. 경고
   4. 오류가 아닌 경고

추적을 시작하려면 **사용**을 클릭 또는 탭합니다. 공급자가 **활성화된 공급자** 드롭다운에 추가됩니다.
* **사용자 지정 공급자**: 추적 수준 및 사용자 지정 ETW 공급자를 선택 합니다. 공급자를 GUID로 식별합니다. GUID에 대괄호를 포함하지 마세요.
* **사용 가능한 공급자**: 활성화 된 공급자를 나열합니다. 추적을 중지하려면 드롭다운에서 공급자를 선택하고 **사용 안 함**을 클릭 또는 탭합니다. 모든 추적을 일시 중단하려면 **모두 중지**를 클릭 또는 탭합니다.
* **공급자 기록**: 현재 세션에서 사용할 수 있는 ETW 공급자를 보여 줍니다. 비활성화된 공급자를 활성화하려면 **사용**을 클릭 또는 탭합니다. 기록을 지우려면 **지우기**를 클릭 또는 탭합니다.
* **이벤트**: 테이블 형식으로 선택한 공급자의 ETW 이벤트를 나열합니다. 이 표는 실시간으로 업데이트됩니다. 테이블 아래를 클릭 합니다 **명확한** 테이블에서 모든 ETW 이벤트를 삭제 하려면 단추입니다. 이렇게 해도 공급자는 비활성화되지 않습니다. **파일로 저장**을 클릭하여 현재 수집된 ETW 이벤트를 CSV 파일에 로컬로 내보낼 수 있습니다.
* **필터**: ID, 키워드, 수준, 공급자 이름, 작업 이름 또는 텍스트에 의해 수집 된 ETW 이벤트를 필터링 할 수 있습니다. 여러 조건을 함께 결합할 수 있습니다.
   1. 적용 조건에 대 한 동일한 속성-이벤트 만족 하는 이러한 조건 중 하나가 표시 됩니다.
   2. 조건에 대 한 이벤트의 모든 조건을 충족 해야 합니다-서로 다른 속성에 적용

예를 들어, 조건을 지정할 수 있습니다 *(작업 이름 'Foo' 또는 '막대'을 포함 하는 데 사용) 및 (텍스트 'error' 또는 '경고'을 포함 하는 데 사용)*

### <a name="simulation"></a>Simulation

![Microsoft HoloLens Windows Device Portal 시뮬레이션 페이지](images/windows-device-portal-simulation-page-1000px.png)<br>
*Microsoft HoloLens Windows Device Portal 시뮬레이션 페이지*

테스트를 위해 입력 데이터를 기록 및 재생할 수 있습니다.
* **대화방 캡처**: 사용자의 환경에 대 한 공간 매핑 메시를 포함 하는 시뮬레이션 된 공간 파일을 다운로드 하는 데 사용 합니다. 대화방 이름을 지정 하 고 클릭 **캡처** PC에서.xef 파일로 데이터를 저장 합니다. 이 공간 파일을 HoloLens 에뮬레이터에 로드할 수 있습니다.
* **기록**: 스트림을 기록, 기록, 이름 확인을 클릭 하거나 탭 **레코드** 다시 코딩을 시작 합니다. 에 HoloLens 사용 하 여 작업을 수행 하 고 클릭 **중지** PC에서.xef 파일로 데이터를 저장 합니다. 이 파일을 HoloLens 에뮬레이터 또는 디바이스에 로드할 수 있습니다.
* **재생**: 클릭 하거나 탭 **업로드 기록** PC에서 xef 파일을 선택 하는 HoloLens에 데이터를 보냅니다.
* **컨트롤 모드**: 선택 **기본** 또는 **시뮬레이션** 드롭다운 목록 및 클릭 또는 탭에서를 **설정** 단추는 HoloLens에서 모드를 선택 합니다. "시뮬레이션"을 선택하면 HoloLens의 실제 센서를 사용할 수 없고 대신 업로드한 시뮬레이트된 데이터를 사용합니다. "시뮬레이션"으로 전환하면 HoloLens가 "기본"으로 다시 전환될 때까지 실제 사용자에게 응답하지 않습니다.

### <a name="networking"></a>네트워킹

![Microsoft HoloLens Windows Device Portal 네트워킹 페이지](images/windows-device-portal-networking-page-1000px.png)<br>
*Microsoft HoloLens Windows Device Portal 네트워킹 페이지*

HoloLens에서 Wi-fi 연결을 관리합니다.
* **WiFi 어댑터**: 드롭다운 컨트롤을 사용 하 여 Wi-fi 어댑터 및 프로필을 선택 합니다. 클릭 하거나 탭 **Connect** 선택한 어댑터를 사용 합니다.
* **사용 가능한 네트워크**: HoloLens에 연결할 수 있는 Wi-fi 네트워크를 나열 합니다. 클릭 하거나 탭 **새로 고침** 목록을 업데이트 합니다.
* **IP 구성**: IP 주소 및 네트워크 연결의 다른 세부 정보를 보여 줍니다.

### <a name="virtual-input"></a>가상 입력

![Microsoft HoloLens Windows Device Portal 가상 입력 페이지](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Microsoft HoloLens Windows Device Portal 가상 입력 페이지*

원격 컴퓨터에서 HoloLens에 키보드 입력을 보냅니다.

클릭 하거나 탭 아래에 있는 지역 **가상 키보드** 는 HoloLens에 보낼 키 입력을 사용 하도록 설정 합니다. 입력 합니다 **텍스트 입력** 텍스트 상자에 붙여넣습니다를 클릭 하거나 탭 **보낼** 활성 앱에 키 입력을 보낼.

## <a name="device-portal-rest-apis"></a>장치 포털 REST API

맨 위에 빌드되는 장치 포털에서 모든 [REST API의](device-portal-api-reference.md) 필요에 따라 데이터를 액세스 하 고 장치를 프로그래밍 방식으로 제어를 사용할 수 있습니다.
