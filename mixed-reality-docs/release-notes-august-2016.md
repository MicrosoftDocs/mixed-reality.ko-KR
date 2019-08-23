---
title: 릴리스 정보-8 월 2016
description: Windows 10 기념일 릴리스에 대 한 HoloLens 릴리스 정보 (낙하 2016)
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 릴리스 정보, os, 플랫폼, 기능, 상용 제품군
ms.openlocfilehash: 2fde8665f3572589abd3dcdfb3747ca487b66afb
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524299"
---
# <a name="release-notes---august-2016"></a>릴리스 정보-8 월 2016

HoloLens 팀은 Windows 참가자 프로그램의 개발자가 작업의 우선 순위를 지정 하는 피드백을 수신 대기 합니다. 피드백 허브, [개발자 포럼](https://forums.hololens.com) [ @HoloLens및 Twitter ](https://twitter.com/hololens)를 통해 피드백을 계속 해 서 [보내](give-us-feedback.md) 주세요. Windows 10에서 기념일 업데이트를 수용 하는 경우 HoloLens 팀은 holographic 환경에 대 한 향상 된 기능을 제공 합니다. 이 업데이트에서는 중요 한 수정 사항, 개선 사항 및 비즈니스에서 요청 하 고 Microsoft HoloLens 상용 제품군에서 사용 가능한 기능 소개에 초점을 맞추고 있습니다.

**최신 릴리스:** Windows Holographic 8 월 2016 업데이트 (**10.0.14393.0**, Windows 10 기념일 릴리스)

>[!VIDEO https://www.youtube.com/embed/tNd0e2CiAkE]

[현재 릴리스로 업데이트](updating-hololens.md)하려면 *설정* 앱을 열고 *업데이트 & 보안*으로 이동한 후 *업데이트 확인* 단추를 선택 합니다.

## <a name="new-features"></a>새로운 기능

**프로세스 디버깅에 연결** 이제 HoloLens에서 프로세스에 대 한 디버깅을 지원 합니다. Visual Studio 2015 업데이트 3을 사용 하 여 HoloLens에서 실행 중인 앱에 연결 하 고 [디버깅을 시작할](using-visual-studio.md#debugging-an-installed-or-running-app)수 있습니다. Visual Studio 프로젝트에서 배포할 필요 없이 작동 합니다.

**업데이트 된 HoloLens 에뮬레이터** 또한 업데이트 된 버전의 HoloLens 에뮬레이터를 출시 했습니다.

**게임 패드 지원** 이제 HoloLens를 사용 하 여 Bluetooth gamepads를 페어링 하 고 사용할 수 있습니다. 새로 릴리스된 Xbox 무선 컨트롤러는 Bluetooth 기능을 갖추고 있으며 즐겨 사용 하는 게임 패드를 사용 하는 게임 및 앱을 재생 하는 데 사용할 수 있습니다. Xbox 무선 컨트롤러 S를 HoloLens와 연결 하려면 먼저 [컨트롤러 업데이트](http://support.xbox.com/xbox-one/accessories/update-controller-for-stereo-headset-adapter) 를 적용 해야 합니다. Xbox 무선 컨트롤러는 [XInput](https://msdn.microsoft.com/library/windows/desktop/hh405053(v=vs.85).aspx) 및 [Windows.Gaming.Input](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) Api에서 지원 됩니다. Bluetooth 컨트롤러의 추가 모델은 [Windows. 게이밍](https://msdn.microsoft.com/library/windows/apps/windows.gaming.input.aspx) API를 통해 액세스할 수 있습니다.

## <a name="improvements-and-fixes"></a>향상 된 기능 및 픽스

Microsoft는 Windows 10 기념일 업데이트의 나머지 부분과 동기화 하 고 있으므로 Hololens 관련 픽스 외에도 Windows 업데이트를 통해 플랫폼 안정성과 성능을 향상 시킬 수 있는 모든 것을 받게 됩니다. 사용자 의견은 매우 중요 하며 릴리스에 대 한 수정 사항의 우선 순위를 지정 합니다.

다음 환경이 개선 되었습니다.
* 로그인 환경.
* 작업 공간 연결입니다.
* 장치 전원 상태 전환에 대 한 전원 효율성.
* 혼합 현실 캡처의 안정성.
* Bluetooth 연결에 대 한 안정성
* 다중 앱 시나리오에서 홀로그램 지 속성

다음 문제를 해결 했습니다.
* Visual Studio 프로파일러 및 그래픽 디버거가 연결 되지 않습니다.
* 사진 & 문서는 장치 포털의 파일 탐색기에 표시 되지 않습니다.
* 조정 모드에서 커서를 위에 배치 하면 앱 바를 깜박일 수 있습니다.
* 조정 모드에 있을 때 눈에 주목 하는 커서 커서가 4 화살표 커서로 변경 됩니다.
* "Cortana 재생 음악"은 Groove를 시작 하지 않습니다.
* 이전 업데이트 후에 "이동 홈"을 말하면 핀 패널이 올바르게 표시 되지 않습니다.

## <a name="introducing-microsoft-hololens-commercial-suite"></a>Microsoft HoloLens 상용 제품군 소개

Microsoft HoloLens 상용 제품군은 엔터프라이즈 배포할 준비가 되었습니다. 초기 비즈니스 파트너 로부터 요청 된 [상업적 기능](commercial-features.md) 을 몇 개 추가 했습니다.

Microsoft HoloLens 상용 Suite를 구매 하려면 로컬 Microsoft 계정 관리자에 게 문의 하세요.

### <a name="key-commercial-features"></a>주요 상업용 기능 

* **키오스크 모드.** HoloLens 키오스크 모드를 사용 하면 데모 또는 전시 환경을 지원 하기 위해 실행할 앱을 제한할 수 있습니다.<br>
  ![키오스크 모드를 사용 하 여 HoloLens는 선택한 앱에 직접 실행 됩니다.](images/201608-kioskmode-400px.png)
* **HoloLens 용 MDM (모바일 장치 관리).** IT 부서는 Microsoft Intune 같은 솔루션을 사용 하 여 여러 HoloLens 장치를 동시에 관리할 수 있습니다. 설정을 관리하고 앱을 선택해서 설치하며 조직의 요구에 부합하는 보안 구성을 설정할 수 있습니다.<br>
  ![HoloLens의 모바일 장치 관리는 여러 장치에서 엔터프라이즈급 장치 관리 기능을 제공 합니다.](images/201608-enterprisemanagement-400px.png)
* **비즈니스에 대 한 Windows 업데이트입니다.** 장치에 대 한 제어 된 운영 체제 업데이트 및 장기 서비스 분기에 대 한 지원.
* **데이터 보안.** 다른 Windows 장치와 동일한 수준의 보안 보호를 제공 하기 위해 HoloLens에서 BitLocker 데이터 암호화가 사용 됩니다.
* **회사 액세스.** 조직의 모든 사용자가 HoloLens의 가상 개인 네트워크를 통해 회사 네트워크에 원격으로 연결할 수 있습니다. HoloLens는 자격 증명이 필요한 Wi-fi 네트워크에도 액세스할 수 있습니다.
* **비즈니스에 대 한 Microsoft Store입니다.** IT 부서에서 특정 HoloLens 사용에 대 한 회사 앱만 포함 하는 엔터프라이즈 개인 저장소를 설정할 수도 있습니다. 엔터프라이즈 소프트웨어를 선택한 엔터프라이즈 사용자 그룹에 안전 하 게 배포 합니다.

### <a name="development-edition-vs-commercial-suite"></a>개발 에디션 및 상용 제품군

<table>
<tr>
<th>기능</th><th>개발 버전</th><th>상용 제품군</th>
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
<td>등록 취소를 차단할 수 있습니다.</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>인증서 기반 회사 Wi-fi 액세스</td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft Store (소비자)</td><td style="text-align: center;">어설션</td><td style="text-align: center;">MDM을 통해 필터링</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/manage/working-with-line-of-business-apps">비즈니스 스토어 포털</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 보안 및 ID</th>
</tr><tr>
<td>AAD (Azure Active Directory를 사용 하 여 로그인</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>Microsoft 계정 (MSA)으로 로그인</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>PIN 잠금 해제를 사용 하는 차세대 자격 증명</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview">보안 부팅</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<th colspan="3" style="text-align: left;"> 서비스 및 지원</th>
</tr><tr>
<td>도착 하면 자동 시스템 업데이트</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td><a href="https://technet.microsoft.com/itpro/windows/plan/windows-update-for-business">비즈니스 Windows 업데이트</a></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<td>장기 서비스 분기</td><td></td><td style="text-align: center;">✔️</td>
</tr>
</table>

## <a name="prior-release-notes"></a>이전 릴리스 정보
* [릴리스 정보 - 2016년 5월](release-notes-may-2016.md)
* [릴리스 정보 - 2016년 3월](release-notes-march-2016.md)

## <a name="see-also"></a>참조
* [HoloLens 알려진 문제](hololens-known-issues.md)
* [상용 기능](commercial-features.md)
* [도구 설치](install-the-tools.md)
* [Using the HoloLens emulator(HoloLens 에뮬레이터 사용)](using-the-hololens-emulator.md)
