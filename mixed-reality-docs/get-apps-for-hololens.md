---
title: HoloLens에 앱을 다운로드 합니다.
description: HoloLens, 테스트용으로 로드 및 Microsoft Store 통해 둘 다에 대 한 앱 설치를 설명합니다.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: 테스트용으로 로드, 테스트용 로드, 테스트용으로 로드, 저장소, uwp, 앱 설치
ms.openlocfilehash: 5042c380e3a548e5001e045676190c2349a835a0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597555"
---
# <a name="get-apps-for-hololens"></a>HoloLens에 앱을 다운로드 합니다.

Windows 10 장치로 HoloLens HoloLens 위해 특별히 구축 된 새로운 앱 뿐만 아니라 앱 스토어에서 많은 기존 UWP 응용 프로그램을 지원 합니다. 이 기반으로 하려는 [개발](development-overview.md) 앱 또는 친구의 설치 및!

## <a name="installing-apps"></a>앱 설치

에 HoloLens에 새 앱을 설치 하는 방법은 세 가지가 있습니다. 기본 방법은 새 응용 프로그램을 Windows 스토어에서 설치할 수 있습니다. 장치 포털을 사용 하 여 사용자 고유의 응용 프로그램도 설치할 수는 있지만 또는 Visual Studio에서 배포 하 여 합니다.

### <a name="from-the-microsoft-store"></a>Microsoft Store
1. 수행을 [블 룸](gestures.md#bloom) 제스처를 열려면 합니다 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)합니다.
2. 스토어 앱을 선택 하 고 전 세계에이 타일을 배치할 누릅니다.
3. 스토어 앱이 열리면 원하는 모든 응용 프로그램에 대 한 검색할 검색 표시줄을 사용 합니다.
4. 선택 **가져옵니다** 또는 **설치** 응용 프로그램의 페이지 (제품을 구매 해야 할 수도 있습니다).

### <a name="installing-an-application-package-with-the-device-portal"></a>장치 포털을 사용 하 여 응용 프로그램 패키지 설치
1. 연결을 설정 [장치 포털](using-the-windows-device-portal.md) HoloLens 대상으로 합니다.
2. 로 이동 합니다 **앱** 왼쪽된 탐색 창에서 페이지입니다.
3. 아래 **앱 패키지** 응용 프로그램과 연결 된.appx 파일을 찾습니다.
  >[!IMPORTANT]
  >연결 된 모든 종속성 및 인증서 파일을 참조 해야 합니다.

4. 클릭 **이동**합니다.

![Windows Device Portal Microsoft HoloLens 앱 형식 설치](images/deviceportal-appmanager.jpg)<br>
Windows Device Portal 사용 하 여 HoloLens에 앱을 설치 하려면

### <a name="deploying-from-microsoft-visual-studio-2015"></a>Microsoft Visual Studio 2015에서 배포
1. 앱의 Visual Studio 솔루션 (.sln 파일)을 엽니다.
2. 프로젝트를 엽니다 **속성** 합니다.
3. 다음 빌드 구성을 선택 합니다. 마스터/x86/원격 컴퓨터입니다.
4. 원격 컴퓨터 선택 하면:
   * 해야 주소 지점 HoloLens' WiFi IP 주소입니다.
   * 유니버설 (암호화 되지 않은 프로토콜)로 인증을 설정 합니다.
5. 솔루션을 빌드하십시오.
6. 클릭 합니다 **원격 컴퓨터** 에 HoloLens 개발 PC에서에서 앱을 배포 하는 단추입니다. 이미 있는 경우 기존 빌드에는 HoloLens, 다시이 최신 버전을 설치 하려면 예 선택 합니다.<br>
  ![Visual Studio에서 Microsoft HoloLens 앱에 대 한 원격 컴퓨터에 배포](images/vs2015-remotedeployment.jpg)<br>
7. 응용 프로그램 설치를 자동으로 여 HoloLens에서 시작 합니다.
