---
title: Windows 장치 포털 사용
description: HoloLens 용 Windows 장치 포털을 사용 하면 Wi-fi 또는 USB를 통해 장치를 원격으로 구성 하 고 관리할 수 있습니다. Device Portal은 PC의 웹 브라우저에서 연결 가능한 HoloLens에 있는 웹 서버입니다. 장치 포털에는 HoloLens를 관리 하 고 앱을 디버그 및 최적화 하는 데 도움이 되는 많은 도구가 포함 되어 있습니다.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: Windows 장치 포털, HoloLens
ms.openlocfilehash: 9bb8116330d88c532b955ef497d29fe98c86fddb
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182023"
---
# <a name="using-the-windows-device-portal"></a>Windows 장치 포털 사용

<table>
<tr>
<th>기능</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens(1세대)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

HoloLens 용 Windows 장치 포털을 사용 하면 Wi-fi 또는 USB를 통해 장치를 원격으로 구성 하 고 관리할 수 있습니다. Device Portal은 PC의 웹 브라우저에서 연결 가능한 HoloLens에 있는 웹 서버입니다. 장치 포털에는 HoloLens를 관리 하 고 앱을 디버그 및 최적화 하는 데 도움이 되는 많은 도구가 포함 되어 있습니다.

이 설명서는 특별히 HoloLens 용 Windows 장치 포털에 대 한 것입니다. Windows Device portal for desktop (Windows Mixed Reality 포함)을 사용 하려면 [Windows 장치 포털 개요](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal) 를 참조 하세요.

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Windows 장치 포털을 사용 하도록 HoloLens 설정

1. HoloLens의 전원을 켜고 디바이스에 배치합니다.
2. HoloLens2 또는 [블 룸](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) on HoloLens (첫 번째 Gen)의 [시작 제스처](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) 를 수행 하 여 주 메뉴를 시작 합니다. 
3. **설정** 타일을 응시 하 고 hololens (첫 번째 Gen)에서 [공기 탭](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) 제스처를 수행 하거나 [손으로 터치 하거나 손으로를 사용 하](https://docs.microsoft.com/hololens/hololens2-basic-usage)여 hololens 2에서 선택 합니다. 
4. **업데이트** 메뉴 항목을 선택합니다.
5. **개발자용** 메뉴 항목을 선택합니다.
6. **개발자 모드**를 사용하도록 설정합니다.
7. [아래로 스크롤하여](gaze-and-commit.md#composite-gestures) **장치 포털**을 사용 하도록 설정 합니다.
8. Windows 장치 포털을 설정 하 여 USB 또는 Wi-fi를 통해이 HoloLens에 앱을 배포할 수 **있도록 하려면 페어링을 클릭 하** 여 [페어링 핀을 생성](using-visual-studio.md)합니다. 첫 번째 배포 중에 Visual Studio에 PIN을 입력할 때까지 PIN 팝업에서 설정 앱을 그대로 둡니다.

   ![Windows Holographic 설정 앱에서 개발자 모드를 사용 하도록 설정](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Wi-fi를 통한 연결

1. [HoloLens를 wi-fi에 연결](connecting-to-wi-fi-on-hololens.md)합니다.
2. 장치의 IP 주소를 조회 합니다.
   * **설정 > 네트워크 & 인터넷 > wi-fi > 고급 옵션**에서 장치에 대 한 IP 주소를 찾습니다.
3. PC의 웹 브라우저에서 https://< YOUR_HOLOLENS_IP_ADDRESS으로 이동 >
   * 브라우저에 "이 웹 사이트의 보안 인증서에 문제가 있습니다." 라는 메시지가 표시 됩니다. 이 오류는 디바이스 포털에 발행된 인증서가 테스트 인증서이기 때문에 발생합니다. 지금은 이 인증서 오류를 무시하고 계속 진행할 수 있습니다.

## <a name="connecting-over-usb"></a>USB를 통해 연결

1. PC에 설치 된 Windows 10 개발자 도구를 사용 하 여 Visual Studio 업데이트 1이 설치 되어 있는지 확인 하 [는 도구를 설치](install-the-tools.md) 합니다. 이렇게 하면 USB 연결을 사용할 수 있습니다.
2. HoloLens를 마이크로-USB 케이블로 PC에 연결합니다.
3. PC의 웹 브라우저에서 [https://127.0.0.1:10080](https://127.0.0.1:10080)로 이동 합니다.

## <a name="connecting-to-an-emulator"></a>에뮬레이터에 연결

에뮬레이터로 디바이스 포털을 사용할 수도 있습니다. 장치 포털에 연결 하려면 [도구 모음](using-the-hololens-emulator.md)을 사용 합니다. 이 아이콘을 클릭 하 ![장치 포털 열기 아이콘](images/emulator-deviceportal.png) **장치 포털**열기: 에뮬레이터에서 HoloLens OS에 대 한 Windows 장치 포털을 엽니다.

## <a name="creating-a-username-and-password"></a>사용자 이름 및 암호 만들기

Windows 장치 포털에 대 한 액세스를 설정 ![](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Windows 장치 포털에 대 한 액세스 설정*

HoloLens에서 디바이스 포털에 처음 연결하면 사용자 이름 및 암호를 만들어야 합니다.
1. PC의 웹 브라우저에서 HoloLens의 IP 주소를 입력합니다. 액세스 설정 페이지가 열립니다.
2. **Pin 요청** 을 클릭 하거나 탭 하 고 HoloLens 디스플레이를 확인 하 여 생성 된 pin을 가져옵니다.
3. 장치 텍스트 상자 **에 표시 된 pin** 에 pin을 입력 합니다.
4. 디바이스 포털 연결에 사용할 사용자 이름을 입력합니다. MSA(Microsoft 계정) 이름 또는 도메인 이름일 필요는 없습니다.
5. 암호를 입력하고 확인합니다. 암호는 7자 이상이어야 합니다. MSA 또는 도메인 암호일 필요는 없습니다.
6. **페어링** 을 클릭 하 여 HoloLens의 Windows 장치 포털에 연결 합니다.

언제 든 지이 사용자 이름 또는 암호를 변경 하려는 경우: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm.으로 이동 하 여 장치 보안 페이지를 방문 하 여이 프로세스를 반복할 수 있습니다.

## <a name="security-certificate"></a>보안 인증서

브라우저에 "인증서 오류"가 표시되는 경우 디바이스와 트러스트 관계를 만들어 수정할 수 있습니다.

각 HoloLens는 해당 SSL 연결에 대한 고유의 자체 서명된 인증서를 생성합니다. 기본적으로 이 인증서는 PC의 웹 브라우저에서 신뢰하지 않아 "인증서 오류"가 발생할 수 있습니다. 신뢰하는 Wi-Fi 네트워크 또는 USB를 통해 HoloLens에서 이 인증서를 다운로드하고 PC에서 신뢰할 수 있도록 만들어 안전하게 디바이스에 연결할 수 있습니다.
1. **보안 네트워크 (USB 또는 신뢰할 수 있는 Wi-fi 네트워크)에 있는지 확인 합니다.**
2. 장치 포털의 "보안" 페이지에서이 장치의 인증서를 다운로드 합니다.
   * 이동: https://< YOUR_HOLOLENS_IP_ADDRESS >/devicepair.htm
3. PC의 "신뢰할 수 있는 루트 인증 기관" 저장소에 인증서를 설치 합니다.
   * Windows 메뉴에서 컴퓨터 인증서 관리 및 애플릿 시작을 입력 합니다.
   * **신뢰할 수 있는 루트 인증 기관** 폴더를 확장 합니다.
   * **인증서** 폴더를 클릭 합니다.
   * 작업 메뉴에서 모든 작업 &gt; 가져오기...를 선택합니다.
   * 디바이스 포털에서 다운로드한 인증서 파일을 사용하여 인증서 가져오기 마법사를 완료합니다.
4. 브라우저를 다시 시작합니다.

## <a name="device-portal-pages"></a>디바이스 포털 페이지

### <a name="home"></a>Home

Microsoft HoloLens의 Windows 장치 포털 홈 페이지를 ![](images/windows-device-portal-home-page-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털 홈 페이지*

홈페이지에서 디바이스 포털 세션을 시작합니다. 홈페이지의 왼쪽 탐색 모음에서 다른 페이지에 액세스합니다.

페이지 맨 위에 있는 도구 모음에서 자주 사용하는 상태 및 기능에 대한 액세스를 제공합니다.
* **온라인**: 디바이스가 Wi-Fi에 연결되어 있는지 여부를 나타냅니다.
* **종료**: 디바이스를 끕니다.
* **다시 시작**: 디바이스의 전원을 하드 부팅합니다.
* **보안**: 디바이스 보안 페이지를 엽니다.
* **냉각**: 디바이스의 온도를 나타냅니다.
* **A/C**: 디바이스가 연결되어 있고 충전 중인지 여부를 나타냅니다.
* **도움말**: REST 인터페이스 설명서 페이지를 엽니다.

홈페이지에는 다음 정보가 표시됩니다.
* **장치 상태:** 장치의 상태를 모니터링 하 고 심각한 오류를 보고 합니다.
* **Windows 정보:** HoloLens의 이름과 현재 설치 되어 있는 windows 버전을 표시 합니다.
* **기본 설정** 섹션에는 다음 설정이 포함되어 있습니다.
   * **IPD**: 앞을 똑바로 바라볼 때 사용자의 동공 중심 사이의 거리인 IPD(동공 간 거리)를 밀리미터 단위로 설정합니다. 설정은 즉시 적용됩니다. 기본값은 디바이스를 설정할 때 자동으로 계산되었습니다.
   * **디바이스 이름**: HoloLens에 이름을 할당합니다. 이 값을 변경 후에는 디바이스를 다시 부팅해야 적용됩니다. **저장**을 클릭 한 후 장치를 즉시 다시 부팅 하거나 나중에 다시 부팅할 것인지 묻는 대화 상자가 나타납니다.
   * **절전 설정**: 디바이스가 전원에 연결된 경우 및 배터리에 연결된 경우에 대해 각각 절전 모드로 전환되기 전에 대기할 시간을 설정합니다.

### <a name="3d-view"></a>3D 뷰

Microsoft HoloLens의 Windows 장치 포털에서 3D 뷰 페이지 ![](images/3dview-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털의 3D 보기 페이지*

3D 뷰 페이지를 사용하여 HoloLens가 사용자의 주변을 해석하는 방법을 확인합니다. 마우스를 사용하여 뷰를 탐색합니다.
* 회전: 마우스 왼쪽 단추를 클릭 합니다.
* 이동: 마우스 오른쪽 단추 클릭 + 마우스
* Zoom: 마우스 스크롤입니다.
* **추적 옵션**
   * **시각적 개체 추적 적용**을 선택 하 여 연속 시각적 추적을 설정 합니다. 
   * **일시 중지** 는 시각적 추적을 중지 합니다.
* **보기 옵션**: 3d 보기에서 옵션을 설정 합니다.
  * **추적**: 시각적 추적이 활성 상태 인지 여부를 나타냅니다.
  * **바닥 표시**: 체크무늬 바닥 평면을 표시합니다.
  * **절두체 표시**: 절두체 보기를 표시합니다.
  * **보정 평면 표시**: HoloLens가 동작을 안정화하는 데 사용하는 평면을 표시합니다.
  * **메시 표시**: 주변을 나타내는 공간 매핑 메시를 표시 합니다.
  * **공간 앵커 표시**: 활성 앱에 대 한 공간 앵커를 표시 합니다. 업데이트 단추를 클릭 하 여 앵커를 가져오고 새로 고쳐야 합니다.
  * **자세한 정보 표시**: 실시간으로 바뀌는 손 위치, 머리 회전 사원수 및 디바이스 원점 벡터를 표시합니다.
  * **전체 화면 단추**: 3D 뷰를 전체 화면 모드로 표시합니다. 전체 화면 보기를 종료하려면 ESC 키를 누릅니다.
* **Surface 재구성**: **업데이트** 를 클릭 하거나 탭 하 여 장치에서 최신 공간 매핑 메시를 표시 합니다. 전체 단계를 완료하는 데 시간이 최대 몇 초 걸릴 수 있습니다. 메시는 3D 보기에서 자동으로 업데이트 되지 않으며 수동으로 **업데이트** 를 클릭 하 여 장치에서 최신 메시를 가져와야 합니다. **저장** 을 클릭 하 여 현재 공간 매핑 메시를 PC의 obj 파일로 저장 합니다.
* **공간 앵커**: 활성 앱에 대 한 공간 앵커를 표시 하거나 업데이트 하려면 업데이트를 클릭 합니다.

### <a name="mixed-reality-capture"></a>혼합 현실 캡처

Microsoft HoloLens의 Windows 장치 포털에서 혼합 현실 캡처 페이지 ![](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털에 있는 혼합 현실 캡처 페이지*

혼합 현실 캡처 페이지를 사용하여 HoloLens에서 미디어 스트림을 저장합니다.
* **설정**: 다음 설정을 확인 하 여 캡처할 미디어 스트림을 제어 합니다.
  * **Holograms**: 비디오 스트림에 holographic 콘텐츠를 캡처합니다. 홀로그램은 스테레오가 아닌 모노로 렌더링됩니다.
  * **PV 카메라**: 사진/비디오 카메라에서 비디오 스트림을 캡처합니다.
  * **마이크 오디오**: 마이크 배열에서 오디오를 캡처합니다.
  * **앱 오디오**: 현재 실행 중인 앱에서 오디오를 캡처합니다.
  * **카메라에서 렌더링**: [실행 중인 앱에서 지원 되](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) 는 경우 (HoloLens 2만 해당) 사진/비디오 카메라의 관점에서 캡처를 맞춥니다.
  * **실시간 미리 보기 품질**: 화면 해상도, 프레임 속도 및 실시간 미리 보기에 대한 스트리밍 속도를 선택합니다.
* **라이브 미리 보기** 단추를 클릭 하거나 탭 하 여 캡처 스트림을 표시 합니다. **라이브 미리 보기 중지** 는 캡처 스트림을 중지 합니다.
* 지정 된 설정을 사용 하 여 혼합 현실 스트림의 기록을 시작 하려면 **기록** 을 클릭 하거나 탭 합니다. **기록 중지** 는 기록을 종료 하 고 저장 합니다.
* **사진 촬영** 을 클릭 하거나 탭 하 여 캡처 스트림에서 계속 이미지를 가져옵니다.
* **동영상 및 사진**: 디바이스에서 촬영한 동영상 및 사진 캡처 목록을 표시합니다.

> [!NOTE]
> [동시 MRC에](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)는 다음과 같은 제한 사항이 있습니다.
> * Windows 장치 포털이 비디오를 기록 하는 동안 앱에서 사진/비디오 카메라에 액세스 하려고 하면 비디오 녹화가 중지 됩니다.
>   * 앱이 SharedReadOnly 모드를 사용 하 여 photo/video 카메라에 액세스 하는 경우 HoloLens 2는 비디오 녹화를 중지 하지 않습니다.
> * 앱에서 현재 photo/video 카메라를 사용 하는 경우 Windows 장치 포털에서 사진을 촬영 하거나 비디오를 녹음할 수 있습니다.
> * 라이브 스트리밍:
>   * HoloLens (첫 번째 gen)는 Windows 장치 포털에서 라이브 스트리밍 중에 앱이 사진/비디오 카메라에 액세스 하지 못하도록 합니다.
>   * 앱이 현재 photo/video 카메라를 사용 하 고 있는 경우 HoloLens (첫 번째 gen)는 라이브 스트림으로 실패 합니다.
>   * HoloLens 2는 앱이 ExclusiveControl 모드에서 photo/video 카메라에 액세스 하려고 할 때 라이브 스트리밍을 자동으로 중지 합니다.
>   * HoloLens 2는 앱이 현재 PV 카메라를 사용 하는 동안 라이브 스트림을 시작할 수 있습니다.

### <a name="performance-tracing"></a>성능 추적

Microsoft HoloLens의 Windows 장치 포털에서 성능 추적 페이지 ![](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털에서 성능 추적 페이지*

HoloLens에서 WPR ( [Windows 성능 레코더](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) ) 추적을 캡처합니다.
* **사용 가능한 프로필**: 드롭다운 목록에서 WPR 프로필을 선택하고, 추적을 시작하려면 **시작**을 클릭 또는 탭합니다.
* **사용자 지정 프로필**: PC에서 WPR 프로필을 선택하려면 **찾아보기**를 클릭 또는 탭합니다. 추적을 시작하려면 **업로드 및 시작**을 클릭 또는 탭합니다.

추적을 중지 하려면 중지 링크를 클릭 합니다. 추적 파일 다운로드가 완료 될 때까지이 페이지를 유지 합니다.

캡처된 ETL 파일은 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx)에서 분석을 위해 열 수 있습니다.

### <a name="processes"></a>Processes

Microsoft HoloLens의 Windows 장치 포털에서 ![프로세스 페이지](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털에 있는 프로세스 페이지*

현재 실행 중인 프로세스에 대한 세부 정보를 보여 줍니다. 앱 및 시스템 프로세스 모두 포함합니다.

### <a name="system-performance"></a>시스템 성능

Microsoft HoloLens의 Windows 장치 포털에서 ![시스템 성능 페이지](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털에서 시스템 성능 페이지*

전력 사용량, 프레임 속도 및 CPU 로드와 같은 시스템 진단 정보를 실시간 그래프로 보여 줍니다.

사용 가능한 메트릭은 다음과 같습니다.
* **SoC 전원**: 1분 평균 순간 system-on-chip 전력 사용율
* **시스템 전원**: 1분 평균 순간 시스템 전력 사용율
* **프레임 속도**: 초당 프레임, 초당 누락 VBlank 및 연속 누락 VBlank
* **GPU**: GPU 엔진 사용률, 총 사용 가능한 백분율
* **CPU**: 사용 가능한 총 백분율
* **I/O**: 읽기 및 쓰기
* **네트워크**: 수신 및 전송
* **메모리**: 총, 사용 중, 커밋된, 페이징 및 비페이징

### <a name="apps"></a>앱을 선택하고

Microsoft HoloLens의 Windows 장치 포털에서 ![Apps 페이지](images/windows-device-portal-apps-page-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털에 있는 앱 페이지*

HoloLens에 설치 된 앱을 관리 합니다.
* **설치된 앱**: 앱을 제거하고 시작합니다.
* **실행 중인 앱**: 현재 실행 중인 앱을 나열합니다.
* **앱 설치**: 컴퓨터/네트워크의 폴더에서 설치할 앱 패키지를 선택 합니다.
* **종속성**: 설치하려는 앱에 대한 종속성을 추가합니다.
* **배포**: 선택한 앱 + 종속성을 HoloLens에 배포 합니다.

### <a name="app-crash-dumps"></a>앱 크래시 덤프

Microsoft HoloLens의 Windows 장치 포털에서 앱 크래시 덤프 페이지를 ![](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털에 있는 앱 크래시 덤프 페이지*

이 페이지에서는 테스트용으로 로드된 앱에 대한 크래시 덤프를 수집할 수 있습니다. 크래시 덤프를 수집 하려는 각 앱에 대해 **크래시 덤프 사용** 확인란을 선택 합니다. 이 페이지로 돌아와서 크래시 덤프를 수집합니다. [디버깅을 위해 Visual Studio에서](https://msdn.microsoft.com/library/d5zhxt22.aspx)덤프 파일을 열 수 있습니다.

### <a name="file-explorer"></a>파일 탐색기

Microsoft HoloLens의 Windows 장치 포털에서 파일 탐색기 페이지 ![](images/fileexplorer-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털에 있는 파일 탐색기 페이지*

파일 탐색기를 사용 하 여 파일을 찾아보고, 업로드 하 고, 다운로드 합니다. 문서 폴더, 그림 폴더 및 Visual Studio 또는 장치 포털에서 배포한 앱에 대 한 로컬 저장소 폴더에서 파일을 사용할 수 있습니다.

### <a name="kiosk-mode"></a>키오스크 모드

>[!NOTE]
>키오스크 모드는 [Microsoft HoloLens 상용 제품군](commercial-features.md)에서만 사용할 수 있습니다.

Windows 장치 포털을 통해 키오스크 모드를 사용 하도록 설정 하는 방법에 대 한 최신 지침은 Windows IT 전문가 센터의 [키오스크 모드에서 HoloLens 설정](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 문서를 확인 하세요.

### <a name="logging"></a>Logging(로깅)

Microsoft HoloLens의 Windows 장치 포털 ![로깅 페이지](images/windows-device-portal-logging-page-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털에 있는 로깅 페이지*

HoloLens에서 실시간 ETW(Windows용 이벤트 추적) (ETW)를 관리 합니다.

**이벤트** 목록만 표시 하려면 **공급자 숨기기** 를 선택 합니다.
* **등록된 공급자**: ETW 공급자와 추적 수준을 선택합니다. 추적 수준은 다음 값 중 하나입니다.
   1. 비정상적인 끝내기 또는 종료
   2. 심각한 오류
   3. 경고
   4. 오류가 아닌 경고

추적을 시작하려면 **사용**을 클릭 또는 탭합니다. 공급자가 **활성화된 공급자** 드롭다운에 추가됩니다.
* **사용자 지정 공급자**: 사용자 지정 ETW 공급자 및 추적 수준을 선택합니다. 공급자를 GUID로 식별합니다. GUID에 대괄호를 포함하지 마세요.
* **활성화된 공급자**: 활성화된 공급자를 나열합니다. 추적을 중지하려면 드롭다운에서 공급자를 선택하고 **사용 안 함**을 클릭 또는 탭합니다. 모든 추적을 일시 중단하려면 **모두 중지**를 클릭 또는 탭합니다.
* **공급자 기록**: 현재 세션 중 활성화된 ETW 공급자를 보여 줍니다. 비활성화된 공급자를 활성화하려면 **사용**을 클릭 또는 탭합니다. 기록을 지우려면 **지우기**를 클릭 또는 탭합니다.
* **이벤트**: 선택된 공급자의 ETW 이벤트를 표 형식으로 나열합니다. 이 표는 실시간으로 업데이트됩니다. 테이블 아래에서 **지우기** 단추를 클릭 하 여 테이블에서 모든 ETW 이벤트를 삭제 합니다. 이렇게 해도 공급자는 비활성화되지 않습니다. **파일로 저장**을 클릭하여 현재 수집된 ETW 이벤트를 CSV 파일에 로컬로 내보낼 수 있습니다.
* **필터**: ID, 키워드, 수준, 공급자 이름, 작업 이름 또는 텍스트로 수집 된 ETW 이벤트를 필터링 할 수 있습니다. 여러 조건을 함께 결합할 수 있습니다.
   1. 동일한 속성에 적용 되는 조건에 대해 이벤트는 다음 조건 중 하나를 만족할 수 있습니다.
   2. 다른 속성에 적용 하는 조건의 경우-이벤트는 모든 조건을 충족 해야 합니다.

예를 들어, 조건 *(작업 이름에 ' Foo ' 또는 ' bar ' 포함)을 지정할 수 있으며, 텍스트에 ' 오류 ' 또는 ' 경고 '가 포함 됩니다* .

### <a name="simulation"></a>Simulation

Microsoft HoloLens의 Windows 장치 포털에서 ![시뮬레이션 페이지](images/windows-device-portal-simulation-page-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털에서 시뮬레이션 페이지*

테스트를 위해 입력 데이터를 기록 및 재생할 수 있습니다.
* **공간 캡처**: 사용자의 주변에 대한 공간 매핑 메시를 포함하는 시뮬레이트된 공간 파일을 다운로드하는 데 사용됩니다. 대화방의 이름을로 지정한 다음 **캡처** 를 클릭 하 여 PC에서 .xef 파일로 데이터를 저장 합니다. 이 공간 파일을 HoloLens 에뮬레이터에 로드할 수 있습니다.
* **기록**: 기록할 스트림을 확인 하 고 기록 이름을로 이름을 선택한 다음 **기록** 을 클릭 하거나 탭 하 여 기록을 시작 합니다. HoloLens를 사용 하 여 작업을 수행 하 고 **중지** 를 클릭 하 여 데이터를 PC에 .xef 파일로 저장 합니다. 이 파일을 HoloLens 에뮬레이터 또는 디바이스에 로드할 수 있습니다.
* **재생**: **녹화 업로드** 를 클릭 하거나 탭 하 여 PC에서 xef 파일을 선택 하 고 HoloLens로 데이터를 보냅니다.
* **컨트롤 모드**: 드롭다운에서 **기본값** 또는 **시뮬레이션** 을 선택 하 고 **설정** 단추를 클릭 하거나 탭 하 여 HoloLens에서 모드를 선택 합니다. "시뮬레이션"을 선택하면 HoloLens의 실제 센서를 사용할 수 없고 대신 업로드한 시뮬레이트된 데이터를 사용합니다. "시뮬레이션"으로 전환하면 HoloLens가 "기본"으로 다시 전환될 때까지 실제 사용자에게 응답하지 않습니다.

### <a name="networking"></a>네트워킹

Microsoft HoloLens의 Windows 장치 포털에서 ![네트워킹 페이지](images/windows-device-portal-networking-page-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털에 있는 네트워킹 페이지*

HoloLens에서 Wi-fi 연결을 관리 합니다.
* **WiFi 어댑터**: 드롭다운 컨트롤을 사용 하 여 wi-fi 어댑터 및 프로필을 선택 합니다. **연결** 을 클릭 하거나 탭 하 여 선택한 어댑터를 사용 합니다.
* **사용 가능한 네트워크**: HoloLens가 연결할 수 있는 wi-fi 네트워크를 나열 합니다. **새로 고침** 을 클릭 하거나 탭 하 여 목록을 업데이트 합니다.
* **Ip 구성**: 네트워크 연결의 ip 주소 및 기타 세부 정보를 표시 합니다.

### <a name="virtual-input"></a>가상 입력

Microsoft HoloLens의 Windows 장치 포털에서 ![가상 입력 페이지](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Microsoft HoloLens의 Windows 장치 포털에 있는 가상 입력 페이지*

원격 컴퓨터에서 HoloLens에 키보드 입력을 보냅니다.

**가상 키보드** 에서 영역을 클릭 하거나 탭 하 여 HoloLens로 키 입력을 보낼 수 있습니다. **입력 텍스트** 텍스트 상자에을 입력 하 고 **보내기** 를 클릭 하거나 탭 하 여 활성 앱에 키 입력을 보냅니다.

## <a name="device-portal-rest-apis"></a>장치 포털 REST API

장치 포털의 모든 항목은 선택적으로 데이터에 액세스 하 고 장치를 프로그래밍 방식으로 제어 하는 데 사용할 수 있는 [REST API](device-portal-api-reference.md) 의 맨 위에 빌드됩니다.
