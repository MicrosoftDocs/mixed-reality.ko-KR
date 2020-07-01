---
title: Windows 장치 포털 사용
description: HoloLens용 Windows 장치 포털을 사용하면 Wi-Fi 또는 USB를 통해 원격으로 디바이스를 구성하고 관리할 수 있습니다. Device Portal은 PC의 웹 브라우저에서 연결 가능한 HoloLens에 있는 웹 서버입니다. 장치 포털에는 HoloLens를 관리하고 앱을 디버깅 및 최적화하는 데 도움이 되는 많은 도구가 포함되어 있습니다.
author: hamalawi
ms.author: moelhama
ms.date: 02/24/2019
ms.topic: article
keywords: Windows 장치 포털, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 234f8a5f2550c4437445ec3ac2726a3588f8bdbe
ms.sourcegitcommit: 5612e8bfb9c548eac42182702cec87b160efbbfe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85441847"
---
# <a name="using-the-windows-device-portal"></a>Windows 장치 포털 사용

<table>
<tr>
<th>기능</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens(1세대)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> Windows Device Portal</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

HoloLens용 Windows 장치 포털을 사용하면 Wi-Fi 또는 USB를 통해 원격으로 디바이스를 구성하고 관리할 수 있습니다. Device Portal은 PC의 웹 브라우저에서 연결 가능한 HoloLens에 있는 웹 서버입니다. 장치 포털에는 HoloLens를 관리하고 앱을 디버깅 및 최적화하는 데 도움이 되는 많은 도구가 포함되어 있습니다.

이 설명서에서는 HoloLens용 Windows 장치 포털을 중점적으로 설명합니다. Windows Mixed Reality를 포함한 데스크톱용 Windows 장치 포털을 사용하려면 [Windows 장치 포털 개요](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)를 참조하세요.

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Windows 장치 포털을 사용하도록 HoloLens 설정

1. HoloLens의 전원을 켜고 디바이스에 배치합니다.
2. [시작 제스처](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture)(HoloLens 2) 또는 [블룸](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)(HoloLens 1세대)으로 주 메뉴를 실행합니다. 
3. **설정** 타일을 응시하고 HoloLens 1세대에서 [에어 탭](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) 제스처를 수행하거나 HoloLens 2에서 [터치하거나 손 광선을 사용](https://docs.microsoft.com/hololens/hololens2-basic-usage)하여 선택합니다. 
4. **업데이트** 메뉴 항목을 선택합니다.
5. **개발자용** 메뉴 항목을 선택합니다.
6. **개발자 모드**를 사용하도록 설정합니다.
7. [아래로 스크롤](gaze-and-commit.md#composite-gestures)하여 **장치 포털**을 사용하도록 설정합니다.
8. USB 또는 Wi-Fi를 통해 이 HoloLens에 앱을 배포할 수 있도록 Windows 장치 포털을 설정하려면 **연결**을 클릭하여 [연결 PIN을 생성](using-visual-studio.md)합니다. 첫 번째 배포 시에는 Visual Studio에 PIN을 입력할 때까지 PIN 팝업에서 설정 앱을 그대로 둡니다.

   ![Windows Holographic 설정 앱에서 개발자 모드 사용](images/deviceportalsettings.png)

## <a name="connecting-over-wi-fi"></a>Wi-Fi를 통한 연결

1. [HoloLens를 Wi-Fi에 연결합니다](connecting-to-wi-fi-on-hololens.md).
2. 다음 중 하나를 수행하여 디바이스의 IP 주소를 조회합니다.
   * **설정 > 네트워크 및 인터넷 > Wi-Fi > 고급 옵션**으로 차례로 이동합니다.
   * **설정 > 네트워크 및 인터넷**으로 차례로 이동하고, **하드웨어 속성**을 선택합니다.

![HoloLens 2 설정](images/windows-device-portal-img-16.png)

3. PC의 웹 브라우저에서 https://<YOUR_HOLOLENS_IP_ADDRESS>로 이동합니다.
   * 브라우저에 다음 메시지가 표시됩니다. "이 웹 사이트의 보안 인증서에 문제가 있습니다." 이 오류는 디바이스 포털에 발행된 인증서가 테스트 인증서이기 때문에 발생합니다. 지금은 이 인증서 오류를 무시하고 계속 진행할 수 있습니다.

## <a name="connecting-over-usb"></a>USB를 통한 연결

1. PC에 Windows 10 개발자 도구와 Visual Studio 업데이트 1이 설치되도록 [도구를 설치](install-the-tools.md)합니다. 이렇게 하면 USB 연결을 사용할 수 있습니다.
2. 마이크로 USB 케이블(HoloLens 1세대) 또는 USB-C(HoloLens 2)를 사용하여 HoloLens를 PC에 연결합니다.
3. PC의 웹 브라우저에서 [https://127.0.0.1:10080](https://127.0.0.1:10080)으로 이동합니다.

## <a name="connecting-to-an-emulator"></a>에뮬레이터에 연결

에뮬레이터로 디바이스 포털을 사용할 수도 있습니다. 장치 포털에 연결하려면 [도구 모음](using-the-hololens-emulator.md)을 사용합니다. 다음 아이콘을 클릭합니다. ![장치 포털 열기 아이콘](images/emulator-deviceportal.png) **장치 포털 열기**: 에뮬레이터에서 HoloLens OS용 Windows 디바이스 포털을 엽니다.

## <a name="creating-a-username-and-password"></a>사용자 이름 및 암호 만들기

![Windows 장치 포털에 대한 액세스 설정](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Windows 장치 포털에 대한 액세스 설정*

HoloLens에서 디바이스 포털에 처음 연결하면 사용자 이름 및 암호를 만들어야 합니다.
1. PC의 웹 브라우저에서 HoloLens의 IP 주소를 입력합니다. 액세스 설정 페이지가 열립니다.
2. **PIN 요청**을 클릭 또는 탭하고 HoloLens 디스플레이를 확인하여 생성된 PIN을 가져옵니다.
3. **디바이스에 표시된 PIN** 텍스트 상자에 PIN을 입력합니다.
4. 디바이스 포털 연결에 사용할 사용자 이름을 입력합니다. MSA(Microsoft 계정) 이름 또는 도메인 이름일 필요는 없습니다.
5. 암호를 입력하고 확인합니다. 암호는 7자 이상이어야 합니다. MSA 또는 도메인 암호일 필요는 없습니다.
6. **연결**을 클릭하여 HoloLens의 Windows 장치 포털에 연결합니다.

이 사용자 이름 또는 암호를 변경하려는 경우 언제든지 https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm으로 이동하여 디바이스 보안 페이지를 방문하면 이 프로세스를 반복할 수 있습니다.

## <a name="security-certificate"></a>보안 인증서

브라우저에 "인증서 오류"가 표시되는 경우 디바이스와 트러스트 관계를 만들어 수정할 수 있습니다.

각 HoloLens는 해당 SSL 연결에 대한 고유의 자체 서명된 인증서를 생성합니다. 기본적으로 이 인증서는 PC의 웹 브라우저에서 신뢰하지 않아 "인증서 오류"가 발생할 수 있습니다. 신뢰하는 Wi-Fi 네트워크 또는 USB를 통해 HoloLens에서 이 인증서를 다운로드하고 PC에서 신뢰할 수 있도록 만들어 안전하게 디바이스에 연결할 수 있습니다.
1. **보안된 네트워크(신뢰하는 Wi-Fi 네트워크 또는 USB)에 있는지 확인합니다.**
2. 장치 포털의 "보안" 페이지에서 이 디바이스의 인증서를 다운로드합니다.
   * https://<YOUR_HOLOLENS_IP_ADDRESS>/devicepair.htm으로 이동합니다.
   * 시스템 > 기본 설정에 대한 노드를 엽니다. 
   * "디바이스 보안"이 나올 때까지 아래로 스크롤하고 "이 디바이스의 인증서 다운로드" 단추를 클릭합니다.
3. PC의 "신뢰할 수 있는 루트 인증 기관" 저장소에 인증서를 설치합니다.
   * Windows 메뉴에서 컴퓨터 인증서 관리를 입력하고 애플릿을 시작합니다.
   * **신뢰할 수 있는 루트 인증 기관** 폴더를 확장합니다.
   * **인증서** 폴더를 클릭합니다.
   * 작업 메뉴에서 모든 작업 > 가져오기...를 선택합니다.
   * 디바이스 포털에서 다운로드한 인증서 파일을 사용하여 인증서 가져오기 마법사를 완료합니다.
4. 브라우저를 다시 시작합니다.

>[!NOTE]
> 이 인증서는 디바이스에서만 신뢰할 수 있으며, 디바이스가 플래시되면 사용자가 프로세스를 다시 진행해야 합니다.


## <a name="device-portal-pages"></a>디바이스 포털 페이지

### <a name="home"></a>홈

![Microsoft HoloLens에 대한 Windows 장치 포털의 홈 페이지](images/windows-device-portal-home-page-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 홈 페이지*

홈페이지에서 디바이스 포털 세션을 시작합니다. 홈페이지의 왼쪽 탐색 모음에서 다른 페이지에 액세스합니다.

페이지 맨 위에 있는 도구 모음에서 자주 사용하는 상태 및 기능에 대한 액세스를 제공합니다.
* **온라인**: 디바이스가 Wi-Fi에 연결되어 있는지 여부를 나타냅니다.
* **종료**: 디바이스를 끕니다.
* **다시 시작**: 디바이스를 하드 부팅합니다.
* **보안**: 디바이스 보안 페이지를 엽니다.
* **냉각**: 디바이스의 온도를 나타냅니다.
* **A/C**: 디바이스가 연결되어 있고 충전 중인지 여부를 나타냅니다.
* **도움말**: REST 인터페이스 설명서 페이지를 엽니다.

홈페이지에는 다음 정보가 표시됩니다.
* **디바이스 상태:** 디바이스의 상태를 모니터링하고 중요한 오류를 보고합니다.
* **Windows 정보:** HoloLens 이름과 현재 설치된 Windows 버전을 보여줍니다.
* **기본 설정** 섹션에는 다음 설정이 포함되어 있습니다.
   * **IPD**: 앞을 똑바로 바라볼 때 사용자의 동공 중심 사이의 거리인 IPD(동공 간 거리)를 밀리미터 단위로 설정합니다. 설정은 즉시 적용됩니다. 기본값은 디바이스를 설정할 때 자동으로 계산되었습니다.
   * **디바이스 이름**: HoloLens에 이름을 할당합니다. 이 값을 변경 후에는 디바이스를 다시 부팅해야 적용됩니다. **저장**을 클릭한 후 디바이스를 즉시 다시 부팅할 것인지 또는 나중에 다시 부팅할 것인지를 묻는 대화 상자가 나타납니다.
   * **절전 설정**: 디바이스가 전원에 연결된 경우 및 배터리에 연결된 경우에 각각 절전 모드로 전환되기 전에 대기할 시간을 설정합니다.

### <a name="3d-view"></a>3D 뷰

![Microsoft HoloLens에 대한 Windows 장치 포털의 3D 뷰 페이지](images/3dview-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 3D 뷰 페이지*

3D 뷰 페이지를 사용하여 HoloLens가 사용자의 주변을 해석하는 방법을 확인합니다. 마우스를 사용하여 뷰를 탐색합니다.
* 회전: 왼쪽 단추 클릭 + 마우스
* 이동: 오른쪽 단추 클릭 + 마우스
* 확대/축소: 마우스 스크롤
* **추적 옵션**
   * **강제 시각적 추적**을 선택하여 연속 시각적 추적을 켭니다. 
   * **일시 중지**는 시각적 추적을 중지합니다.
* **보기 옵션**: 3D 뷰의 옵션을 설정합니다.
  * **추적**: 시각적 추적이 활성 상태인지 여부를 나타냅니다.
  * **바닥 표시**: 체크무늬 바닥 평면을 표시합니다.
  * **절두체 표시**: 절두체 보기를 표시합니다.
  * **보정 평면 표시**: HoloLens가 동작을 안정화하는 데 사용하는 평면을 표시합니다.
  * **메시 표시**: 사용자의 주변을 나타내는 공간 매핑 메시를 표시합니다.
  * **공간 앵커 표시**: 활성 앱의 공간 앵커를 표시합니다. 업데이트 단추를 클릭하여 앵커를 가져오고 새로 고쳐야 합니다.
  * **자세한 정보 표시**: 실시간으로 바뀌는 손 위치, 머리 회전 사원수 및 디바이스 원점 벡터를 표시합니다.
  * **전체 화면 단추**: 3D 뷰를 전체 화면 모드로 표시합니다. 전체 화면 보기를 종료하려면 ESC 키를 누릅니다.
* **표면 재구성**: **업데이트**를 클릭 또는 탭하여 디바이스에서 최신 공간 매핑 메시를 표시합니다. 전체 단계를 완료하는 데 시간이 최대 몇 초 걸릴 수 있습니다. 메시는 3D 뷰에서 자동으로 업데이트되지 않으며, 디바이스에서 수동으로 **업데이트**를 클릭해야만 최신 메시를 얻을 수 있습니다. **저장**을 클릭하여 현재 공간 매핑 메시를 PC에서 obj 파일로 저장합니다.
* **공간 앵커**: 업데이트를 클릭하여 활성 앱의 공간 앵커를 표시하거나 업데이트합니다.

### <a name="mixed-reality-capture"></a>혼합 현실 캡처

![Microsoft HoloLens에 대한 Windows 장치 포털의 혼합 현실 캡처 페이지](images/windows-device-portal-mixed-reality-capture-page-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 혼합 현실 캡처 페이지*

혼합 현실 캡처 페이지를 사용하여 HoloLens에서 미디어 스트림을 저장합니다.
* **캡처 설정**: 다음 설정을 확인하여 캡처할 미디어 스트림을 제어합니다.
  * **홀로그램**: 비디오 스트림에서 홀로그램 콘텐츠를 캡처합니다. 홀로그램은 스테레오가 아닌 모노로 렌더링됩니다.
  * **PV 카메라**: 사진/비디오 카메라에서 비디오 스트림을 캡처합니다.
  * **마이크 오디오**: 마이크 배열에서 오디오를 캡처합니다.
  * **앱 오디오**: 현재 실행 중인 앱에서 오디오를 캡처합니다.
  * **카메라에서 렌더링**: [실행 중인 앱에서 지원](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)할 경우 캡처본을 사진/비디오 카메라 관점이 되도록 조정합니다(HoloLens 2만 해당).
  * **실시간 미리 보기 품질**: 실시간 미리 보기의 화면 해상도, 프레임 속도 및 스트리밍 속도를 선택합니다.
* **오디오 설정**(HoloLens 2만 해당):
  * **오디오 미디어 범주**: 마이크를 처리할 때 사용되는 범주를 선택합니다. **기본**에는 일부 환경이 포함되지만 **통신**은 백그라운드 노이즈 취소를 적용합니다.
  * **앱 오디오 게인**: 앱 오디오의 볼륨에 적용되는 게인입니다.
  * **마이크 오디오 게인**: 마이크 오디오의 볼륨에 적용되는 게인입니다.
* **사진 및 비디오 설정**(HoloLens 2, 버전 2004 이상):
  * **캡처 프로필**: 사진과 비디오를 촬영할 때 사용할 프로필을 선택합니다. 프로필은 사용할 수 있는 해상도와 프레임 비율을 결정합니다.
  * **사진 해상도**: 사진을 촬영하는 해상도입니다.
  * **비디오 해상도 및 프레임 비율**: 촬영하는 비디오의 해상도와 프레임 비율입니다.
  * **비디오 안정화 버퍼**: 비디오를 촬영할 때 사용되는 버퍼 크기입니다. 값이 클수록 빠른 움직임에 맞게 보정할 수 있습니다.
* **실시간 미리 보기** 단추를 클릭 또는 탭하여 캡처 스트림을 표시합니다. **실시간 미리 보기 중지**는 캡처 스트림을 중지합니다.
* **녹화**를 클릭 또는 탭하여 지정된 설정을 사용해 혼합 현실 스트림의 녹화를 시작합니다. **녹화 정지**는 녹화를 끝내고 저장합니다.
* **사진 촬영**을 클릭 또는 탭하여 캡처 스트림에서 정지 이미지를 촬영합니다.
* **기본 설정 복원**을 클릭하거나 탭하여 오디오, 사진 및 비디오 설정에 기본 설정을 복원합니다.
* **비디오 및 사진**: 디바이스에서 촬영한 비디오 및 사진 캡처 목록을 표시합니다.

이 페이지의 모든 설정은 Windows 장치 포털을 사용하는 캡처에 적용되지만 일부는 추가적으로 시스템 MRC(시작 메뉴, 하드웨어 단추, 글로벌 음성 명령, Miracast) 및 사용자 지정 MRC 레코더에 적용됩니다.

|  설정  |  시스템 MRC에 적용  |  사용자 지정 MRC 레코더에 적용 |
|----------|----------|----------|
|  홀로그램  |  아니요  |  아니요 |
|  PV 카메라  |  아니요  |  아니요 |
|  마이크 오디오  |  아니요  |  아니요 |
|  앱 오디오  |  아니요  |  아니요 |
|  카메라에서 렌더링  |  예    |  예(재정의할 수 있음) |
|  실시간 미리 보기 품질  |  아니요  |  아니요 |
|  오디오 미디어 범주  |  예  |  아니요 |
|  앱 오디오 게인  |  예  |  예(재정의할 수 있음) |
|  마이크 오디오 게인  |  예  |  예(재정의할 수 있음) |
|  캡처 프로필  |  예  |  아니요 |
|  사진 해상도  |  예  |  아니요 |
|  비디오 해상도 및 프레임 비율  |  예  |  아니요 |
|  비디오 안정화 버퍼  |  예  |  예(재정의할 수 있음) |

> [!NOTE]
> [동시 MRC에 대한 제한 사항](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)이 있습니다.
> * Windows 장치 포털이 비디오를 녹화하는 동안 앱에서 사진/비디오 카메라에 액세스하려고 하면 비디오 녹화가 중지됩니다.
>   * 앱이 SharedReadOnly 모드를 사용하여 사진/비디오 카메라에 액세스하는 경우 HoloLens 2는 비디오 녹화를 중지하지 않습니다.
> * 앱이 현재 사진/비디오 카메라를 사용하는 경우 Windows 장치 포털에서 사진을 촬영하거나 비디오를 녹화할 수 있습니다.
> * 라이브 스트리밍:
>   * HoloLens(1세대)는 Windows 장치 포털에서 라이브 스트리밍 중에 앱이 사진/비디오 카메라에 액세스하지 못하도록 합니다.
>   * HoloLens(1세대)는 앱이 현재 사진/비디오 카메라를 사용하는 경우 라이브 스트리밍에 실패합니다.
>   * HoloLens 2는 앱이 ExclusiveControl 모드에서 사진/비디오 카메라에 액세스하려고 하면 라이브 스트리밍을 자동으로 중지합니다.
>   * HoloLens 2는 앱이 현재 PV 카메라를 사용 중인 경우 라이브 스트림을 시작할 수 있습니다.

### <a name="performance-tracing"></a>성능 추적

![Microsoft HoloLens에 대한 Windows 장치 포털의 성능 추적 페이지](images/windows-device-portal-performance-tracing-page-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 성능 추적 페이지*

HoloLens에서 [WPR(Windows Performance Recorder)](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) 추적을 캡처합니다.
* **사용 가능한 프로필**: 드롭다운 목록에서 WPR 프로필을 선택하고 **시작**을 클릭 또는 탭하여 추적을 시작합니다.
* **사용자 지정 프로필**: PC에서 WPR 프로필을 선택하려면 **찾아보기**를 클릭 또는 탭합니다. 추적을 시작하려면 **업로드 및 시작**을 클릭 또는 탭합니다.

추적을 중지하려면 중지 링크를 클릭합니다. 추적 파일이 다운로드를 완료할 때까지 이 페이지에 계속 있습니다.

캡처된 ETL 파일은 [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx)에서 분석을 위해 열 수 있습니다.

### <a name="processes"></a>프로세스

![Microsoft HoloLens에 대한 Windows 장치 포털의 프로세스 페이지](images/windows-device-portal-running-processes-page-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 프로세스 페이지*

현재 실행 중인 프로세스에 대한 세부 정보를 보여 줍니다. 앱 및 시스템 프로세스 모두 포함합니다.

### <a name="system-performance"></a>시스템 성능

![Microsoft HoloLens에 대한 Windows 장치 포털의 시스템 성능 페이지](images/windows-device-portal-system-performance-page-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 시스템 성능 페이지*

전력 사용량, 프레임 속도 및 CPU 로드와 같은 시스템 진단 정보를 실시간 그래프로 보여 줍니다.

사용 가능한 메트릭은 다음과 같습니다.
* **SoC 전원**: 1분 평균 순간 시스템 온칩 전력 사용률
* **시스템 전원**: 1분 평균 순간 시스템 전력 사용률
* **프레임 속도**: 초당 프레임, 초당 누락 VBlank 및 연속 누락 VBlank
* **GPU**: GPU 엔진 사용률(사용 가능한 총 전원 대비 백분율)
* **CPU**: 사용 가능한 총 전원 대비 백분율
* **I/O**: 읽기 및 쓰기
* **네트워크**: 수신 및 전송
* **메모리**: 전체, 사용 중, 약정, 페이징 및 비페이징 메모리

### <a name="apps"></a>앱

![Microsoft HoloLens에 대한 Windows 장치 포털의 앱 페이지](images/windows-device-portal-apps-page-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 앱 페이지*

HoloLens에 설치된 앱을 관리합니다.
* **설치된 앱**: 앱을 제거하고 시작합니다.
* **실행 중인 앱**: 현재 실행 중인 앱을 나열합니다.
* **앱 설치**: 컴퓨터/네트워크 폴더에서 설치할 앱 패키지를 선택합니다.
* **종속성**: 설치하려는 앱에 대한 종속성을 추가합니다.
* **배포**: 선택한 앱 + 종속성을 HoloLens에 배포합니다.

### <a name="app-crash-dumps"></a>앱 크래시 덤프

![Microsoft HoloLens에 대한 Windows 장치 포털의 앱 크래시 덤프 페이지](images/windows-device-portal-dev-apps-crash-dumps-page-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 앱 크래시 덤프 페이지*

이 페이지에서는 테스트용으로 로드된 앱에 대한 크래시 덤프를 수집할 수 있습니다. 크래시 덤프를 수집하려는 각 앱에 대해 **크래시 덤프 사용** 확인란을 선택합니다. 이 페이지로 돌아와서 크래시 덤프를 수집합니다. 덤프 파일은 [디버깅을 위해 Visual Studio에서 열릴 수 있습니다](https://msdn.microsoft.com/library/d5zhxt22.aspx).

### <a name="file-explorer"></a>파일 탐색기

![Microsoft HoloLens에 대한 Windows 장치 포털의 파일 탐색기 페이지](images/fileexplorer-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 파일 탐색기 페이지*

파일 탐색기를 사용하여 파일을 찾아보고, 업로드하고, 다운로드합니다. 문서 폴더, 그림 폴더 및 Visual Studio 또는 장치 포털에서 배포한 앱에 대한 로컬 스토리지 폴더의 파일을 사용할 수 있습니다.

### <a name="kiosk-mode"></a>키오스크 모드

>[!NOTE]
>키오스크 모드는 [Microsoft HoloLens Commercial Suite](commercial-features.md)에서만 사용할 수 있습니다.

Windows 장치 포털을 통해 키오스크 모드를 사용하도록 설정하는 방법에 대한 최신 지침은 Windows IT 전문가 센터의 [키오스크 모드로 HoloLens 설정 ](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) 문서를 확인하세요.

### <a name="logging"></a>로깅

![Microsoft HoloLens에 대한 Windows 장치 포털의 로깅 페이지](images/windows-device-portal-logging-page-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 로깅 페이지*

HoloLens에서 실시간 ETW(Windows용 이벤트 추적)를 관리합니다.

**이벤트 목록**만 표시하려면 **공급자 숨기기**를 선택합니다.
* **등록된 공급자**: ETW 공급자와 추적 수준을 선택합니다. 추적 수준은 다음 값 중 하나입니다.
   1. 비정상적인 끝내기 또는 종료
   2. 심각한 오류
   3. 경고
   4. 오류가 아닌 경고

추적을 시작하려면 **사용**을 클릭 또는 탭합니다. 공급자가 **활성화된 공급자** 드롭다운에 추가됩니다.
* **사용자 지정 공급자**: 사용자 지정 ETW 공급자와 추적 수준을 선택합니다. 공급자를 GUID로 식별합니다. GUID에 대괄호를 포함하지 마세요.
* **활성화된 공급자**: 활성화된 공급자를 나열합니다. 추적을 중지하려면 드롭다운에서 공급자를 선택하고 **사용 안 함**을 클릭 또는 탭합니다. 모든 추적을 일시 중단하려면 **모두 중지**를 클릭 또는 탭합니다.
* **공급자 기록**: 현재 세션 중 활성화된 ETW 공급자를 보여줍니다. 비활성화된 공급자를 활성화하려면 **사용**을 클릭 또는 탭합니다. 기록을 지우려면 **지우기**를 클릭 또는 탭합니다.
* **이벤트**: 선택된 공급자의 ETW 이벤트를 표 형식으로 나열합니다. 이 표는 실시간으로 업데이트됩니다. 모든 ETW 이벤트를 표에서 삭제하려면 표 아래에 있는 **지우기** 단추를 클릭합니다. 이렇게 해도 공급자는 비활성화되지 않습니다. **파일로 저장**을 클릭하여 현재 수집된 ETW 이벤트를 CSV 파일에 로컬로 내보낼 수 있습니다.
* **필터**: 수집된 ETW 이벤트를 ID, 키워드, 수준, 공급자 이름, 작업 이름 또는 텍스트로 필터링할 수 있습니다. 여러 조건을 함께 결합할 수 있습니다.
   1. 동일한 속성에 적용되는 조건의 경우 이러한 조건 중 하나라도 만족하는 이벤트가 표시됩니다.
   2. 다른 속성에 적용되는 조건의 경우 이벤트가 모든 조건을 충족해야 합니다.

예를 들어 *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')* 기준을 지정할 수 있습니다.

### <a name="simulation"></a>Simulation

![Microsoft HoloLens에 대한 Windows 장치 포털의 시뮬레이션 페이지](images/windows-device-portal-simulation-page-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 시뮬레이션 페이지*

테스트를 위해 입력 데이터를 기록 및 재생할 수 있습니다.
* **공간 캡처**: 사용자의 주변에 대한 공간 매핑 메시를 포함하는 시뮬레이트된 공간 파일을 다운로드하는 데 사용됩니다. 공간의 이름을 지정한 다음, **캡처**를 클릭하여 PC에 .xef 파일로 데이터를 저장합니다. 이 공간 파일을 HoloLens 에뮬레이터에 로드할 수 있습니다.
* **녹화**: 녹화할 스트림을 선택하고 녹화본의 이름을 지정하고 **녹화**를 클릭 또는 탭하여 녹화를 시작합니다. HoloLens를 사용하여 작업을 수행한 다음, **중지**를 클릭하여 PC에 .xef 파일로 데이터를 저장합니다. 이 파일을 HoloLens 에뮬레이터 또는 디바이스에 로드할 수 있습니다.
* **재생**: **녹화본 업로드**를 클릭 또는 탭하여 PC에서 xef 파일을 선택하고 HoloLens에 데이터를 보냅니다.
* **제어 모드**: 드롭다운 목록에서 **기본** 또는 **시뮬레이션**을 선택하고 **설정** 단추를 클릭 또는 탭하여 HoloLens의 모드를 선택합니다. "시뮬레이션"을 선택하면 HoloLens의 실제 센서를 사용할 수 없고 대신 업로드한 시뮬레이트된 데이터를 사용합니다. "시뮬레이션"으로 전환하면 HoloLens가 "기본"으로 다시 전환될 때까지 실제 사용자에게 응답하지 않습니다.

### <a name="networking"></a>네트워킹

![Microsoft HoloLens에 대한 Windows 장치 포털의 네트워킹 페이지](images/windows-device-portal-networking-page-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 네트워킹 페이지*

HoloLens에서 Wi-Fi 연결을 관리합니다.
* **WiFi 어댑터**: 드롭다운 컨트롤을 사용하여 Wi-Fi 어댑터 및 프로필을 선택합니다. **연결**을 클릭하거나 탭하여 선택한 어댑터를 사용합니다.
* **사용 가능한 네트워크**: HoloLens가 연결할 수 있는 Wi-Fi 네트워크를 나열합니다. 목록을 업데이트하려면 **새로 고침**을 클릭하거나 탭합니다.
* **IP 구성**: 네트워크 연결의 IP 주소 및 기타 세부 정보를 표시합니다.

### <a name="virtual-input"></a>가상 입력

![Microsoft HoloLens에 대한 Windows 장치 포털의 가상 입력 페이지](images/windows-device-portal-virtual-input-page-1000px.png)<br>
*Microsoft HoloLens에 대한 Windows 장치 포털의 가상 입력 페이지*

원격 컴퓨터에서 HoloLens에 키보드 입력을 보냅니다.

**가상 키보드** 아래 영역을 클릭 또는 탭하여 HoloLens에 키 입력 전송을 사용합니다. **입력 텍스트** 텍스트 상자에 입력하고 **보내기**를 클릭 또는 탭하여 활성 앱에 키 입력을 보냅니다.

## <a name="device-portal-rest-apis"></a>장치 포털 REST API

장치 포털의 모든 작업은 데이터에 액세스하고 디바이스를 프로그래밍 방식으로 제어할 때 선택적으로 사용할 수 있는 [REST API](device-portal-api-reference.md)를 기반으로 합니다.
