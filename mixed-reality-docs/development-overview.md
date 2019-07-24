---
title: 개발 개요
description: 이 문서에서는 Windows Mixed Reality 앱을 개발 하는 기본 구성 요소에 대해 간략하게 설명 합니다.
author: mattzmsft
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: 시작 하기, 기본 사항, HoloLens, HoloLens 2, 모던 헤드셋, unity, visual studio
ms.openlocfilehash: 23bd173f89a468b4403d44236534bfe811a968dd
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873987"
---
# <a name="development-overview"></a>개발 개요

혼합 현실 앱은 다양 한 개발자 기술을 사용 하 여 개발할 수 있습니다.  HoloLens는 [유니버설 Windows 플랫폼](https://dev.windows.com/getstarted)로 빌드된 앱을 실행 합니다.  모던 헤드셋은 유니버설 Windows 플랫폼 앱 및 Win32 응용 프로그램을 실행 합니다.
Unity와 같은 미들웨어 도구를 사용 하 여 지금 혼합 현실 환경 빌드를 시작할 수 있습니다.  오픈 소스 [혼합 현실 도구 키트](install-the-tools.md) 를 활용 하 여 빠르게 시작 하세요.
<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>와 같은 <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">혼합 현실 서비스</a>에는 다양 한 플랫폼 간 개발자 기술에도 통합할 수 있는 sdk가 있습니다.

>[!VIDEO https://www.youtube.com/embed/A784OdX8xzI]

## <a name="basics-of-mixed-reality-development"></a>혼합 현실 개발 기본 사항

[혼합 현실](mixed-reality.md) 환경에서는 환경 이해를 위한 새로운 Windows 기능이 지원됩니다. 이를 통해 개발자는 실제 세상에 [홀로그램](hologram.md)을 배치할 수 있으며, 사용자는 그야말로 걸어다니면서 디지털 세계를 이동할 수 있습니다. 

다음은 혼합 현실 개발을 위한 핵심 구성 요소입니다.

<table>
<tr>
<th>입력</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens(1세대)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> <a href="gaze.md">머리 응시</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="gaze.md">응시</a></td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> 손/ <a href="gestures.md">제스처</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr><tr>
<td> <a href="voice-input.md">음성</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="hardware-accessories.md">게임 패드</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="motion-controllers.md">모션 컨트롤러</a></td><td></td><td></td><td style="text-align: center;">✔️</td>
</tr><tr>
<th> 인식 및 공간 기능</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens(1세대)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></th>
</tr><tr>
<td> <a href="coordinate-systems.md">세계 좌표</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-sound.md">공간 음향</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td>
</tr><tr>
<td> <a href="spatial-mapping.md">공간 매핑</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>



[HoloLens](hololens-hardware-details.md)의 기본 조작 모델은 [응시](gaze.md), [제스처](gestures.md) 및 [음성](voice-input.md)으로, *GGV*라고도 합니다. [Windows Mixed Reality 몰입형 헤드셋](immersive-headset-hardware-details.md)의 경우도 응시 및 음성을 사용하지만 제스처를 위해 [모션 컨트롤러](motion-controllers.md)를 바꿉니다.


모든 Windows 기반 혼합 현실 장치는 마우스, 키보드, gamepads 등을 포함 하 여 Windows에서 사용할 수 있는 입력 에코 시스템을 활용 합니다. HoloLens를 사용할 경우 [하드웨어 액세서리](hardware-accessories.md)가 Bluetooth를 통해 연결됩니다. 몰입형 헤드셋을 사용하면 액세서리는 Bluetooth, USB 및 기타 지원되는 프로토콜을 통해 호스트 PC에 연결됩니다.

[좌표](coordinate-systems.md), [공간 음향](spatial-sound.md) 및 [공간 매핑](spatial-mapping.md)과 같은 환경 이해 기능은 혼합 현실에 필요한 기능을 제공합니다. 공간 매핑은 HoloLens에 고유하게 사용되며, 홀로그램이 사용자 및 주변의 실제 세계와 상호 작용할 수 있도록 합니다. 좌표계는 사용자의 움직임이 디지털 세계의 움직임에 영향을 미치도록 합니다.

[Holograms](hologram.md) 는 [holographic 렌더링](rendering.md)을 사용 하는 광원 및 소리로 구성 됩니다. [Windows Mixed Reality 홈](navigating-the-windows-mixed-reality-home.md)("셸"이라고도 함)이 나타내는 것처럼 배치 및 지속성 환경을 이해하면 사용자 환경에서 보다 편리하게 작업할 수 있습니다.

## <a name="tools-for-developing-for-mixed-reality"></a>혼합 현실용 개발을 위한 도구

사용하는 도구는 빌드하려는 [앱의 스타일](app-views.md)에 따라 다릅니다.
* [2D 뷰가 있는 앱](building-2d-apps.md)은 Windows Phone, PC, 태블릿 등의 환경에 적합한 유니버설 Windows 플랫폼 앱을 빌드하기 위한 도구를 활용합니다. 이러한 앱은 Windows Mixed Reality 홈에 배치된 2D 프로젝션을 통해 사용할 수 있으며 여러 디바이스 유형(휴대폰 및 PC 포함)에서 작동할 수 있습니다.
* 몰입형 및 홀로그래픽 앱은 Windows Mixed Reality API를 활용하도록 디자인된 도구가 필요합니다. 혼합 현실 앱을 빌드하려면 [Unity를 사용하는 것이 좋습니다](unity-development-overview.md). 고유한 엔진 구빌드에 관심이 있는 개발자는 [DirectX 및 기타 Windows API를 사용](directx-development-overview.md)할 수 있습니다.

빌드 중인 앱 유형에 관계없이, 다음과 같은 도구를 통해 앱 개발 환경을 원활하게 사용할 수 있습니다.
* [Visual Studio 및 Windows SDK](using-visual-studio.md)
* [Windows 디바이스 포털](using-the-windows-device-portal.md)
* [HoloLens 에뮬레이터](using-the-hololens-emulator.md) (HoloLens 2 에뮬레이터 출시 예정)
* [Windows Mixed Reality 시뮬레이터](using-the-windows-mixed-reality-simulator.md)
* [앱 품질 기준](app-quality-criteria.md)

## <a name="see-also"></a>참조
* [도구 설치](install-the-tools.md)
* <a href="https://azure.microsoft.com/topic/mixed-reality" target="_blank">혼합 현실 서비스</a>
* [Mixed Reality 자습서](tutorials.md)
* [오픈 소스 프로젝트](open-source-projects.md)
* [MR 기본 100: Unity 시작](holograms-100.md)
* [Windows Mixed Reality 최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Windows 스토어에 앱 제출](submitting-an-app-to-the-microsoft-store.md)
