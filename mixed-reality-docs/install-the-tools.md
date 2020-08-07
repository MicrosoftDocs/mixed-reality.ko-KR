---
title: 도구 설치
description: 혼합 현실 개발을 위해 준비하려면 여기에서 시작합니다. 이 문서는 항상 Unity, Visual Studio, HoloLens와 Windows Mixed Reality 몰입형 헤드셋 개발에 권장되는 기타 도구의 최신 버전을 반영합니다.
author: thetuvix
ms.author: alexturn
ms.date: 07/31/2020
ms.topic: article
ms.localizationpriority: high
keywords: up-to-date, tools, get started, basics, unity, visual studio, toolkit
ms.openlocfilehash: f5c779aa0bb89fe66b53419b03ec1b4d3e6b562b
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476906"
---
# <a name="install-the-tools"></a>도구 설치

Microsoft HoloLens 및 Windows Mixed Reality 몰입형(VR) 헤드셋을 위한 애플리케이션을 빌드하는 데 필요한 도구를 다운로드하세요. Windows Mixed Reality 개발을 위한 별도 SDK는 없으므로 Windows 10 SDK에서 Visual Studio를 사용합니다.

혼합 현실 디바이스가 없나요? [HoloLens 에뮬레이터](using-the-hololens-emulator.md)를 설치하면 HoloLens 없이도 혼합 현실 앱의 일부 기능을 테스트할 수 있습니다. [Windows Mixed Reality 시뮬레이터](using-the-windows-mixed-reality-simulator.md)를 사용하여 몰입형 헤드셋을 위한 혼합 현실 앱을 테스트할 수도 있습니다. Unity를 사용하는 경우 [MRTK(Mixed Reality Toolkit)](https://github.com/Microsoft/MixedRealityToolkit-Unity)의 입력 시뮬레이션을 사용하여 손 인식 및 시선 추적 입력과 같은 다양한 유형의 입력 상호 작용을 테스트할 수 있습니다.

혼합 현실 앱 만들기를 시작하는 가장 쉬운 방법은 Unity 게임 엔진을 설치하는 것입니다. 그러나 사용자 지정 엔진을 사용하려는 경우에는 DirectX에 대해 빌드할 수도 있습니다.

>[!TIP]
>이 페이지에 책갈피를 지정하고 정기적으로 확인하면서 혼합 현실 개발에 권장되는 각 도구를 최신 상태로 유지하세요.

<br>

## <a name="installation-checklist"></a>설치 검사 목록


| 도구 | 참고 |
|---------|---------|
| ![Windows 로고](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10**(수동 설치 링크)</a><br><br>PC의 운영 체제가 혼합 현실 애플리케이션을 빌드하는 플랫폼과 일치하도록 최신 버전의 Windows 10을 설치합니다.  | **Windows 10 설치** <br> 설정의 Windows 업데이트를 통해 또는 설치 미디어를 만들어(왼쪽 열의 링크 사용) 최신 버전의 Windows 10을 설치할 수 있습니다. <br><br>각 릴리스의 Windows 10에서 사용할 수 있는 최신 혼합 현실 기능에 대한 내용은 [현재 릴리스 정보](release-notes-october-2018.md)를 참조하세요. 설정 > 업데이트 및 보안 > 개발자용에서 **PC의 개발자 모드를 사용하도록 설정**합니다. <br><br> **엔터프라이즈 및 회사 관리용 PC에 대한 참고 사항**<br>조직의 IT 부서에서 PC를 관리하는 경우 업데이트하려면 해당 부서에 문의해야 할 수도 있습니다. <br><br> **Windows용 'N' 버전**<br> Windows Mixed Reality 몰입형(VR) 헤드셋은 'N' 버전의 Windows에서 지원되지 않습니다. |
| ![Visual Studio 로고](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019(16.2 이상)** (설치 링크)</a> <br><br>Windows 등을 위한 전기능 IDE(통합 개발 환경)입니다. Visual Studio를 사용하여 코드를 작성하고, 디버그하고, 테스트하고, 배포합니다. | 다음 워크로드를 설치합니다. <br><br>**● C++를 사용한 데스크톱 개발**<br>**● UWP(유니버설 Windows 플랫폼) 개발**<br><br>HoloLens 앱을 개발하려는 경우 UWP 워크로드 내에서 다음과 같은 선택적 구성 요소를 확인해야 합니다.<br><br>**● USB 디바이스 연결**<br><br>**● Unity에 대한 참고 사항:**<br>특정 목적을 위해 최신 버전의 Unity(비 LTS)를 설치하려는 경우가 아니면 Unity 워크로드를 Visual Studio 설치의 일부로 설치하지 *말고*, 대신 아래 설명된 것처럼 **Unity 2019 LTS** 스트림을 설치하는 것이 좋습니다.<br><br>**참고**<br>Visual Studio 2019 버전 16.0의 혼합 현실 앱 디버깅에는 몇 가지 알려진 이슈가 있습니다.  **Visual Studio 2019 버전 16.2 이상**으로 업데이트하세요. |
| ![Windows 로고](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK(10.0.18362.0)** (수동 설치 링크)</a> <br><br>HoloLens 2에서 Windows 10 앱을 빌드하기 위한 최신 헤더와 라이브러리, 메타데이터, 도구를 제공합니다. | **HoloLens 2 앱을 빌드하려면 Windows SDK 빌드 18362 이상을 설치해야 합니다.**<br> <br> 데스크톱 Windows Mixed Reality 헤드셋 또는 HoloLens(1세대)용 애플리케이션만 개발하는 경우에는 Visual Studio 2017에서 설치된 Windows SDK를 사용할 수 있습니다. |
| ![Visual Studio 로고](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2132415" target="_blank">**HoloLens 2 에뮬레이터(Windows Holographic 버전 2004, 2020년 6월 업데이트)** (설치 링크: 10.0.19041.1106)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens(1세대) 에뮬레이터**(설치 링크: 10.0.17763.134)</a> <br><br>이 에뮬레이터를 사용하면 실제 HoloLens 없이도 HoloLens 가상 머신 이미지에서 애플리케이션을 실행할 수 있습니다.<br> <br> | 에뮬레이터 시작 방법에 대한 자세한 내용은 [HoloLens 에뮬레이터 사용](using-the-hololens-emulator.md)을 참조하세요.<br> <br> 에뮬레이터 설치를 성공적으로 수행하려면 **시스템에서 Hyper-V를 지원해야 합니다**. 자세한 내용은 아래 시스템 요구 사항 섹션을 참조하세요. <br>|

## <a name="choose-your-engine"></a>엔진 선택

Windows 10, Visual Studio, Windows 10 SDK가 준비되었으면 빌드할 엔진을 선택하겠습니다. 

[!INCLUDE[](~/includes/tools-overview.md)]
