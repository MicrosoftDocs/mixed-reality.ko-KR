---
title: 릴리스 정보-2016 년 8 월
description: HoloLens 릴리스는 Windows 10 1 주년 릴리스 (2016 년)에 대 한 정보
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 릴리스 정보, os, 플랫폼, 기능, 상용 도구 모음
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603665"
---
# <a name="release-notes---august-2016"></a>릴리스 정보-2016 년 8 월

HoloLens 팀이 작업 우선 순위를 지정 하려면 Windows 참가자 프로그램에는 개발자가 피드백을 수신 합니다. 읽어보세요 [의견을 보내 주십시오](give-us-feedback.md) 피드백 허브를 통해 합니다 [개발자 포럼](https://forums.hololens.com) 및 [를 통해 Twitter @HoloLens ](https://twitter.com/hololens)합니다. Windows 10으로 포옹 1 주년 업데이트, HoloLens 팀 전달할 정상 이라는 것을 추가로 홀로그램 환경으로 개선 합니다. 이 업데이트의 주요 수정, 향상 및 기업에서 Microsoft HoloLens Commercial Suite에서 사용할 수 있는 요청 소개 기능에 집중 했습니다.

**최신 릴리스:** Windows Holographic 2016 년 8 월 업데이트 (**10.0.14393.0**, Windows 10 1 주년 릴리스)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

[최신 릴리스로 업데이트](updating-hololens.md)엽니다는 *설정* 앱으로 이동 *업데이트 및 보안*를 선택 하 고는 *업데이트를 확인* 단추입니다.

## <a name="new-features"></a>새로운 기능

**연결 프로세스 디버깅 중에** HoloLens 이제 프로세스에 디버깅을 지원 합니다. Visual Studio 2015 업데이트 3을 사용 하 여는 HoloLens에서 실행 중인 앱에 연결할 수 있습니다 하 고 [디버깅 시작](using-visual-studio.md#debugging-an-installed-or-running-app)합니다. Visual Studio 프로젝트에서 배포 하지 않아도 작동 합니다.

**HoloLens 에뮬레이터 업데이트** HoloLens 에뮬레이터의 업데이트 된 버전도 릴리스 했습니다.

**Gamepad 지원** 이제 페어링 하 고 HoloLens를 사용 하 여 Bluetooth 게임 패드를 사용할 수 있습니다. 새로 출시 된 Xbox 무선 컨트롤러 S Bluetooth 기능을 기능 및 좋아하는 gamepad 지원 게임과 앱을 재생 하는 데 사용할 수 있습니다. A [컨트롤러 업데이트](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) Xbox 무선 컨트롤러 S HoloLens를 사용 하 여 연결 하려면 먼저 적용 해야 합니다. Xbox 무선 컨트롤러 S 지 [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) 하 고 [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) Api. Bluetooth 컨트롤러의 추가 모델을 통해 액세스할 수 합니다 [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API.

## <a name="improvements-and-fixes"></a>향상 된 기능 및 수정

에서는 되므로 Windows 10 1 주년 업데이트의 나머지 부분과 동기화 Hololens 특정 수정 하는 것 외에도 또한에서 받을 때는 모든 적합성 플랫폼 안정성과 성능을 향상 시키는 Windows 업데이트 합니다. 항상 사용자 의견 반환 이며 릴리스에서 수정에 대 한 우선 순위를 지정 합니다.

다음과 같은 환경을 개선 했습니다.
* 환경에 로그인 합니다.
* 작업 공간 연결 합니다.
* 장치의 전원 상태 전환에 대 한 전원 효율성입니다.
* 혼합 현실 캡처합니다 안정성.
* Bluetooth 연결에 대 한 안정성
* 다중 앱 시나리오에서 홀로그램 지 속성

다음과 같은 문제를 해결 했습니다.
* Visual Studio 프로파일러 및 그래픽 디버거를 연결할 수 없습니다.
* 사진 및 문서 장치 포털에서 파일 탐색기에서 표시 하지 않습니다.
* 앱 바 조정 모드에 있는 동안 위에 커서를 배치 하면 플래시 수 있습니다.
* 조정 모드에 있을 때 눈 게이즈 점 커서 바뀌어 4 화살표 커서를 잠시 느리게 합니다.
* "Hey Cortana 음악을 재생" Groove은 실행 되지 않습니다.
* 이전 업데이트 후 "Go Home" 라는 올바르게 표시 되지 않습니다 [pin] 패널입니다.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Microsoft HoloLens 상용 Suite 소개

Microsoft HoloLens Commercial Suite enterprise 배포 준비가 되었습니다. 많이 요청 되는 몇 가지 추가 했습니다 [상용 기능](commercial-features.md) 초기 비즈니스 파트너의 합니다.

Microsoft HoloLens Commercial Suite를 구입 하려면 해당 지역의 Microsoft 영업 담당자에 문의 하세요.

### <a name="key-commercial-features"></a>주요 상용 기능 

* **키오스크 모드입니다.** HoloLens 키오스크 모드를 사용 하 여 앱 데모 또는 쇼케이스 환경을 사용할 수 있도록 실행을 제한할 수 있습니다.<br>
  ![키오스크 모드를 사용 하 여 HoloLens 선택한 앱에 직접 시작합니다.](images/201608-kioskmode-400px.png)
* **HoloLens에 대 한 모바일 장치 관리 (MDM)입니다.** IT 부서는 동시에 Microsoft Intune과 같은 솔루션을 사용 하 여 여러 HoloLens 장치를 관리할 수 있습니다. 설정을 관리하고 앱을 선택해서 설치하며 조직의 요구에 부합하는 보안 구성을 설정할 수 있습니다.<br>
  ![HoloLens에 모바일 장치 관리는 여러 장치에서 엔터프라이즈 등급 장치 관리를 제공합니다.](images/201608-enterprisemanagement-400px.png)
* **비즈니스용 Windows 업데이트 합니다.** 장치 및 장기 서비스 분기에 대 한 지원에 대 한 운영 체제 업데이트를 제어 합니다.
* **데이터 보안입니다.** HoloLens에 BitLocker 데이터 암호화를 사용 하는 동일한 수준의 다른 Windows 장치로 보안 보호를 제공 합니다.
* **회사 액세스 합니다.** 조직의 모든 사용자가 가상 개인 네트워크에는 HoloLens 통해 회사 네트워크에 원격으로 연결할 수 있습니다. HoloLens 자격 증명을 필요로 하는 Wi-fi 네트워크 액세스할 수도 있습니다.
* **비즈니스용 Microsoft Store.** IT 부서 설정할 수도 엔터프라이즈 사설 저장소 특정 HoloLens 사용량에 대 한 회사의 앱만을 포함 합니다. 안전 하 게 선택한 사용자 그룹에 enterprise 엔터프라이즈 소프트웨어를 배포 합니다.

### <a name="development-edition-vs-commercial-suite"></a>Development Edition 및 Commercial Suite

<table>
<tr>
<th>기능</th><th>Development Edition</th><th>Commercial Suite</th>
</tr><tr>
<td>장치 암호화 (Bitlocker)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>VPN(가상 사설망)</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="using-the-windows-device-portal.md#kiosk-mode">키오스크 모드</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 관리 및 배포</th>
</tr><tr>
<td>MDM(모바일 장치 관리)</td><td style="text-align: center;"></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>등록 취소를 차단 하는 기능</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>인증서 기반 회사 Wi-fi 액세스</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (소비자)</td><td style="text-align: center;">소비자</td><td style="text-align: center;">MDM을 통해 필터링</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">업무용 스토어 포털</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 보안 및 ID</th>
</tr><tr>
<td>Azure Active Directory (AAD)를 사용 하 여 로그인</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft 계정 (MSA)으로 로그인</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>PIN 사용 하 여 다음 세대 자격 증명 잠금 해제</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">보안 부팅</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 서비스 및 지원</th>
</tr><tr>
<td>도착 했을 때 자동 시스템 업데이트</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">비즈니스용 Windows 업데이트</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>장기 서비스 분기</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>이전 릴리스 정보
* [릴리스 정보-2016 년 5 월](release-notes-may-2016.md)
* [릴리스 정보-2016 년 3 월](release-notes-march-2016.md)

## <a name="see-also"></a>참조
* [HoloLens 알려진 문제](hololens-known-issues.md)
* [고급 기능](commercial-features.md)
* [도구 설치](install-the-tools.md)
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
