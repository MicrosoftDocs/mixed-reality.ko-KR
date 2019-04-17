---
title: 개발 개요
description: 이 문서에서는 Windows Mixed Reality 앱 개발의 기본 구성 요소를 설명 합니다.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: 시작, 시작된 기본 사항, HoloLens, HoloLens 2 몰입 형 헤드셋, unity, visual studio
ms.openlocfilehash: 1d23e458477cc23252ccd4c44f67c400aa356965
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605112"
---
# <a name="development-overview"></a>개발 개요

다양 한 개발자 기술 사용 하 여 혼합된 현실 앱을 개발할 수 있습니다.  HoloLens 사용 하 여 빌드된 앱을 실행 합니다 [유니버설 Windows 플랫폼](https://dev.windows.com/getstarted)합니다.  몰입 형 헤드셋 Win32 응용 프로그램 뿐만 아니라 유니버설 Windows 플랫폼 앱을 실행합니다.
Unity와 같은 미들웨어 도구 가져오기, 혼합된 현실 환경 현재 빌드를 시작할 수 있습니다.  오픈 소스 활용 [혼합 현실 Toolkit](install-the-tools.md) 신속 하 게 시작 합니다.
<a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">실제로 서비스를 혼합</a>와 같은 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>, 다양 한 플랫폼 간 개발자 기술에 통합할 수 있는 Sdk가 있습니다.

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>혼합된 현실 개발의 기본 사항

[혼합 현실을](mixed-reality.md) 환경을 환경 이해를 위한 새로운 Windows 기능으로 사용 됩니다. 이러한 배치 하는 개발자 도구를 사용을 [홀로그램](hologram.md) 실제 상황에서 사용자가 디지털 세계에 대 한 문자 그대로 살펴봄으로써 이동할 수 있도록 합니다. 

다음은 혼합된 현실 개발을 위한 핵심 구성 요소입니다.

<table>
<tr>
<th>입력</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (첫 번째 범용)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td> <a href="gaze.md">헤드 응시</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">응시</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> 실습 / <a href="gestures.md">제스처</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">음성</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">Gamepad</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">컨트롤러 동작</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> 인식 및 공간 기능</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (첫 번째 범용)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">세계 좌표</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">소리 공간</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">공간 매핑</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



에 대 한 기본 조작 모델은 [HoloLens](hololens-hardware-details.md) 됩니다 [gaze](gaze.md)에 [제스처](gestures.md), 및 [음성](voice-input.md)라고도, *GGV* . [Windows Mixed Reality 몰입 형 헤드셋](immersive-headset-hardware-details.md) 도 사용 하 여 게이즈 및 음성 있지만 스왑 [컨트롤러 동작](motion-controllers.md) 제스처에 대 한 합니다.


Windows, 마우스, 키보드, 게임 패드 등 사용 가능한 입력된 에코 시스템에서 이익을 얻을 모든 혼합된 현실 Windows 기반 장치. HoloLens를 사용 하 여 [하드웨어 accessories](hardware-accessories.md) Bluetooth를 통해 연결 됩니다. 몰입 형 헤드셋을 사용 하 여 accessories Bluetooth, USB, 및 기타 지원 되는 프로토콜을 통해 호스트 PC에 연결 합니다.

와 같은 환경 이해 기능 [좌표](coordinate-systems.md)를 [공간 소리](spatial-sound.md), 및 [공간 매핑](spatial-mapping.md) 실제로 혼합 하는 데 필요한 기능을 제공 합니다. 공간 매핑은 HoloLens, 고유 및 홀로그램 사용자 및 실제 이들을 모두와 상호 작용할 수 있습니다. 디지털 세계의 이동에 적용할 사용자의 이동을 허용 하는 좌표계입니다.

[홀로그램](hologram.md) 빛과 소리를 사용 하는 내용이 [holographic 렌더링](rendering.md)합니다. 에 설명 된 대로 배치 및 지 속성의 경험을 이해 합니다 [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md) ("셸" 라고도 함)는 뛰어난 방식으로 접지 사용자 환경에 있습니다.

## <a name="tools-for-developing-for-mixed-reality"></a>혼합된 현실 용 개발을 위한 도구

사용 하는 도구에 따라 달라 집니다 합니다 [앱의 스타일](app-views.md) 빌드 하려는 합니다.
* [2D 뷰를 사용 하 여 앱](building-2d-apps.md) Windows Phone, PC, 태블릿 등 환경에 적합 한 유니버설 Windows 플랫폼 앱 빌드에 대 한 도구를 활용 합니다. Windows Mixed Reality 집에 배치 하는 2D 프로젝션으로 숙련 된 되며 다중 장치 유형 (휴대폰 및 PC 포함)에 대해 작업할 수 있습니다.
* 몰입 형 및 holographic 앱 혼합 현실 Windows Api를 활용 하도록 설계 된 도구를 필요로 합니다. 우리가 [Unity를 사용 하는 것이 좋습니다](unity-development-overview.md) 혼합된 현실 앱을 빌드할 수 있습니다. 자신의 엔진 구축에 관심이 있는 개발자 수 [DirectX 및 기타 Windows Api를 사용 하 여](directx-development-overview.md)입니다.

빌드 중인 앱의 형식에 관계 없이 이러한 도구에는 앱 개발 환경을 원활 하 게 합니다.
* [Visual Studio 및 Windows SDK](using-visual-studio.md)
* [Windows 디바이스 포털](using-the-windows-device-portal.md)
* [HoloLens 에뮬레이터](using-the-hololens-emulator.md) (HoloLens 2 에뮬레이터 출시 예정)
* [Windows Mixed Reality 시뮬레이터](using-the-windows-mixed-reality-simulator.md)
* [앱 품질 기준](app-quality-criteria.md)

## <a name="see-also"></a>참조
* [도구 설치](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">혼합된 현실 서비스</a>
* [혼합된 현실 자습서](academy.md)
* [오픈 소스 프로젝트](open-source-projects.md)
* [MR Basics 100: Unity를 사용 하 여 시작](holograms-100.md)
* [Windows Mixed Reality 최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Windows 스토어에 앱 제출](submitting-an-app-to-the-microsoft-store.md)
