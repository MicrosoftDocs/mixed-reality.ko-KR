---
title: Unity 개발 개요
description: Unity에서 혼합 현실 앱 빌드를 시작 합니다.
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트, 포팅, 기능, 카메라, 시뮬레이션, 에뮬레이션, 설명서
ms.openlocfilehash: 24217b4c61bf2d438ebc1c4114bc9dc20dc62f64
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414522"
---
# <a name="unity-development-overview"></a>Unity 개발 개요

[혼합 현실 앱](app-views.md) 을 빌드하기 위한 가장 빠른 경로는 [Unity](http://aka.ms/HoloLensUnity)를 사용 하는 것입니다. [Unity 자습서](https://unity3d.com/learn/tutorials)를 탐색 하는 데 시간이 소요 되는 것이 좋습니다. 자산이 필요한 경우 Unity는 포괄적인 [자산 저장소](https://www.assetstore.unity3d.com/)를 포함 합니다. Unity를 기본적으로 이해 하 고 나면 [자습서](tutorials.md) 를 방문 하 여 unity를 사용한 혼합 현실 개발의 세부 사항을 배울 수 있습니다. Unity [혼합 현실 포럼](http://forum.unity3d.com/forums/hololens.102/) 을 방문 하 여 unity에서 혼합 현실 앱을 빌드하는 커뮤니티의 나머지 부분과 함께 실행 될 수 있는 문제에 대 한 해결 방법을 찾아보세요.


Unity를 사용 하 여 혼합 현실 앱 빌드를 시작 하려면 먼저 [도구를 설치](install-the-tools.md)합니다. 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>혼합 현실 도구 키트를 사용 하는 새 Unity 프로젝트 

Unity에서 개발 하는 가장 쉬운 방법은 Mixed Reality Toolkit의 도움을 주는 것입니다. Project를 자동으로 설치 하 고 개발을 가속화 하는 혼합 현실 기능 집합을 제공 합니다. 자세히 알아보고 시작 하려면 [Mixed Reality Toolkit v2](mrtk-getting-started.md) 를 확인 하세요. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Windows Mixed Reality로 기존 Unity 앱 포팅

Windows Mixed Reality로 이식 하는 기존 Unity 프로젝트를 사용 하는 경우 [unity 포팅 가이드](porting-guides.md) 에 따라 시작 하세요.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality에 대 한 새 Unity 프로젝트 구성

Mixed Reality Toolkit를 가져오지 않고 새 Unity 프로젝트를 만들려는 경우에는 Windows Mixed Reality에 대해 수동으로 변경 해야 하는 몇 가지 Unity 설정 집합이 있습니다. 이러한 항목은 프로젝트별 및 장면의 두 범주로 구분 됩니다. [Windows Mixed Reality에 대해 새 Unity 프로젝트를 구성](Configure-Unity-Project.md) 하는 단계별 가이드는 여기를 참조 하세요.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>혼합 현실 기능 및 입력 추가

프로젝트를 사용 하 여 MRTK v 2를 설정 하거나 위에서 설명한 대로 프로젝트를 구성한 후에는 표준 Unity 게임 개체 (예: 카메라)가 자동으로 작동 하 **고, 카메라**위치가 사용자가 전 세계를 이동 합니다.

[공간 단계](coordinate-systems.md#spatial-coordinate-systems), [제스처, 동작 컨트롤러](gestures-and-motion-controllers-in-unity.md) 또는 [음성 입력과](voice-input-in-unity.md) 같은 Windows 혼합 현실 기능에 대 한 지원을 추가 하면 Unity에 직접 빌드된 api를 사용 하 여 구현 됩니다. 

먼저, 해당 환경에서 대상으로 할 수 있는 [환경 규모](coordinate-systems.md) 를 검토 합니다.
* **방향** 또는 **대규모 환경을**구축 하려는 경우 Unity의 추적 공간 형식을 [고정](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)으로 설정 해야 합니다.
* 대규모 또는 **공간 규모의 환경을**구축  하려는 경우 Unity의 추적 공간 유형이 [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)로 설정 되었는지 확인 해야 합니다.
* 사용자가 5 미터를 초과 하 여 로밍할 수 있도록 HoloLens에서 **세계 규모** 의 경험을 구축 하려는 경우 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) 구성 요소를 사용 해야 합니다.

혼합 현실 응용 프로그램의 모든 핵심 구성 요소는 다른 Unity Api와 일치 하는 방식으로 노출 됩니다. 혼합 현실 도구 키트를 통해 사용할 수도 있습니다.
* [카메라](camera-in-unity.md)
* [좌표계](coordinate-systems-in-unity.md)
* [응시](gaze-in-unity.md)
* [제스처 및 동작 컨트롤러](gestures-and-motion-controllers-in-unity.md)
* [음성 입력 ](voice-input-in-unity.md)
* [지속성](persistence-in-unity.md)
* [공간 음향](spatial-sound-in-unity.md)
* [공간 매핑](spatial-mapping-in-unity.md)

많은 혼합 현실 응용 프로그램에서 Unity 앱에도 노출 되는 다른 주요 기능을 사용 합니다.
* [공유 환경](shared-experiences-in-unity.md)
* [위치를 찾을 수 있는 카메라](locatable-camera-in-unity.md)
* [포커스 지점](focus-point-in-unity.md)
* [추적 손실](tracking-loss-in-unity.md)
* [키보드](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>실제 또는 시뮬레이션 된 장치에서 Unity 프로젝트 실행

Holographic Unity 프로젝트를 테스트할 준비가 되 면 다음 단계는 [Unity Visual Studio 솔루션을 내보내고 빌드하](exporting-and-building-a-unity-visual-studio-solution.md)는 것입니다.

이 VS 솔루션을 사용 하면 실제 또는 시뮬레이션 된 장치를 사용 하 여 다음 세 가지 방법 중 하나로 응용 프로그램을 실행할 수 있습니다.
* [실제 HoloLens 또는 Windows Mixed Reality 모던 헤드셋에 배포](using-visual-studio.md)
* [HoloLens 에뮬레이터에 배포](using-the-hololens-emulator.md)
* [Windows Mixed Reality 몰입 형 헤드셋 시뮬레이터에 배포](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity 설명서

Windows 개발자 센터에서 제공 하는이 설명서 외에 Unity는 Unity 편집기와 함께 Windows Mixed Reality 기능에 대 한 설명서를 설치 합니다. Unity 제공 설명서에는 두 개의 개별 섹션이 포함 되어 있습니다.
1. **Unity 스크립팅 참조**
    * 설명서의이 섹션에는 Unity에서 제공 하는 스크립팅 API에 대 한 세부 정보가 포함 되어 있습니다.
    * Unity 편집기에서 **도움말 > 스크립팅 참조** 를 통해 액세스할 수 있습니다.
2. **Unity 수동**
    * 이 설명서는 기본에서 고급 기술로 Unity를 사용 하는 방법을 배우는 데 도움이 되도록 설계 되었습니다.
    * **Help > Manual** 를 통해 Unity 편집기에서 액세스할 수 있습니다.

## <a name="see-also"></a>참조
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [MR 기본 100: Unity 시작](holograms-100.md)
* [Unity 권장 설정](recommended-settings-for-unity.md)
* [Unity의 권장 성능](performance-recommendations-for-unity.md)
* [Unity Visual Studio 솔루션 내보내기 및 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
* [HoloLens용 Unity 앱에서 Windows 네임스페이스 사용](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Unity 및 Visual Studio 사용 모범 사례](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 플레이 모드](unity-play-mode.md)
* [포팅 가이드](porting-guides.md)
