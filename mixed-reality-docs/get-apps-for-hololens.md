---
title: HoloLens 용 앱 가져오기
description: Microsoft Store 및 테스트용 로드를 통해 HoloLens 용 앱을 설치 하는 방법을 설명 합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 테스트용으로 로드, side load, 테스트용 로드, 스토어, uwp, 앱, 설치
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522542"
---
# <a name="get-apps-for-hololens"></a>HoloLens 용 앱 가져오기

Windows 10 장치는 hololens를 위해 특별히 빌드된 새로운 앱 뿐만 아니라 앱 스토어에서 많은 기존 UWP 응용 프로그램을 지원 합니다. 이러한 앱을 기반으로 자신의 앱 또는 친구의 앱을 [개발](development-overview.md) 하 고 설치 하는 것도 좋습니다.

## <a name="installing-apps"></a>앱 설치

HoloLens에 새 앱을 설치 하는 방법에는 세 가지가 있습니다. 기본 방법은 Windows 스토어에서 새 응용 프로그램을 설치 하는 것입니다. 그러나 장치 포털을 사용 하거나 Visual Studio에서 배포 하 여 응용 프로그램을 직접 설치할 수도 있습니다.

### <a name="from-the-microsoft-store"></a>Microsoft Store에서
1. [블 룸](gestures.md#bloom) 제스처를 수행 하 여 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)를 엽니다.
2. 스토어 앱을 선택 하 고 탭 하 여이 타일을 전 세계에 추가 합니다.
3. 스토어 앱이 열리면 검색 표시줄을 사용 하 여 원하는 응용 프로그램을 찾습니다.
4. 응용 프로그램의 페이지에서 **가져오기** 또는 **설치** 를 선택 합니다 (구매가 필요할 수 있음).

### <a name="installing-an-application-package-with-the-device-portal"></a>장치 포털을 사용 하 여 응용 프로그램 패키지 설치
1. [장치 포털](using-the-windows-device-portal.md) 에서 대상 HoloLens로의 연결을 설정 합니다.
2. 왼쪽 탐색 영역에서 **앱** 페이지로 이동 합니다.
3. **앱 패키지** 아래에서 응용 프로그램과 연결 된 .appx 파일을 찾습니다.
  >[!IMPORTANT]
  >연결 된 종속성 및 인증서 파일을 모두 참조 해야 합니다.

4. **찾기**를 클릭합니다.

![Microsoft HoloLens의 Windows 장치 포털에서 앱 양식 설치](images/deviceportal-appmanager.jpg)<br>
Windows 장치 포털을 사용 하 여 HoloLens에 앱 설치

### <a name="deploying-from-microsoft-visual-studio-2015"></a>Microsoft Visual Studio 2015에서 배포
1. 앱의 Visual Studio 솔루션 (.sln 파일)을 엽니다.
2. 프로젝트의 **속성** 을 엽니다.
3. 다음 빌드 구성을 선택 합니다. Master/x86/원격 컴퓨터.
4. 원격 컴퓨터를 선택 하는 경우:
   * 주소가 HoloLens의 WiFi IP 주소를 가리키는지 확인 합니다.
   * 인증을 유니버설 (암호화 되지 않은 프로토콜)로 설정 합니다.
5. 솔루션을 빌드합니다.
6. **원격 컴퓨터** 단추를 클릭 하 여 개발 PC에서 HoloLens에 앱을 배포 합니다. HoloLens에 기존 빌드가 이미 있는 경우 예를 선택 하 여이 최신 버전을 다시 설치 합니다.<br>
  ![Visual Studio에서 Microsoft HoloLens로 앱에 대 한 원격 컴퓨터 배포](images/vs2015-remotedeployment.jpg)<br>
7. 응용 프로그램이 설치 되 고 HoloLens에 자동 실행 됩니다.
