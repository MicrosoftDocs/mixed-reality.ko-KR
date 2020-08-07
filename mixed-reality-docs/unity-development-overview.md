---
title: Unity 개발 개요
description: Unity에서 혼합 현실 앱 빌드를 시작합니다.
author: thetuvix
ms.author: kurtie
ms.date: 07/29/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트, 포팅, 기능, 카메라, 시뮬레이션, 에뮬레이션, 설명서
ms.openlocfilehash: 4679e1a2b58a7e0d77e6b295803624a4de1fac19
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476715"
---
# <a name="unity-development-overview"></a>Unity 개발 개요

[혼합 현실 앱](app-views.md)을 빌드하는 가장 빠른 경로는 [Unity](https://unity.com)를 사용하는 것입니다. 잠시 시간을 내어 [Unity 자습서](https://unity3d.com/learn/tutorials)를 살펴보는 것이 좋습니다. 자산이 필요한 경우 Unity에는 포괄적인 [Asset Store](https://www.assetstore.unity3d.com/)(자산 저장소)가 있습니다. Unity를 기본적으로 이해한 경우 [자습서](tutorials.md)를 참조하여 Unity에서 혼합 현실을 개발하는 방법에 대해 자세히 알아볼 수 있습니다. [Unity Mixed Reality 포럼](https://forum.unity3d.com/forums/hololens.102/)을 방문하여 Unity에서 혼합 현실 앱을 빌드하는 나머지 커뮤니티와 교류하고 발생할 수 있는 문제에 대한 해결 방법을 찾습니다.

Unity를 사용하여 혼합 현실 앱 빌드를 시작하려면 먼저 [도구를 설치](install-the-tools.md)하세요.

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>Mixed Reality Toolkit를 사용하는 새 Unity 프로젝트 

Unity에서 개발하는 가장 쉬운 방법은 Mixed Reality Toolkit을 사용하는 것입니다. 이를 통해 프로젝트를 자동으로 설정하고 개발을 가속화하는 혼합 현실 기능 세트를 제공할 수 있습니다. 자세한 내용을 알아보고 시작하려면 [Mixed Reality Toolkit v2](mrtk-getting-started.md)를 확인하세요. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>기존 Unity 앱을 Windows Mixed Reality에 포팅

Windows Mixed Reality에 포팅할 기존 Unity 프로젝트가 있는 경우 [Unity 포팅 가이드](porting-guides.md)에 따라 시작하세요.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality용 새 Unity 프로젝트 구성

Mixed Reality Toolkit을 가져오지 않고 새 Unity 프로젝트를 만드는 경우, Windows Mixed Reality에 대해 변경해야 하는 작은 Unity 설정 세트가 있습니다. 이러한 설정은 두 가지 범주, 즉 프로젝트별 및 장면별 범주로 구분됩니다. 단계별 가이드는 [Windows Mixed Reality용 새 Unity 프로젝트 구성](Configure-Unity-Project.md)을 참조하세요.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>혼합 현실 기능 및 입력 추가

프로젝트를 사용하여 MRTK V2를 설정하거나 위에서 설명한 대로 프로젝트가 구성되면, 표준 Unity 게임 개체(예: 카메라)가 **착석 규모 환경**을 위해 즉시 켜지며 현실 세계에서 사용자의 머리 움직임에 따라 카메라의 위치가 자동으로 업데이트됩니다.

Windows Mixed Reality 기능에 대한 지원(예: [공간 스테이지](coordinate-systems.md#spatial-coordinate-systems), [제스처, 모션 컨트롤러](gestures-and-motion-controllers-in-unity.md) 또는 [음성 입력](voice-input-in-unity.md))은 Unity에 직접 빌드된 API를 사용하여 추가됩니다. 

먼저 애플리케이션에서 대상으로 지정할 수 있는 [환경 규모](coordinate-systems.md)를 검토합니다.
* **방향 전용** 또는 **착석 규모 환경**을 빌드하려면 Unity의 추적 공간 형식을 [고정](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)으로 설정해야 합니다.
* **기립 규모** 또는 **실내 규모 환경**을 빌드하려면 Unity의 추적 공간 형식을 [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)로 설정해야 합니다.
* 사용자가 5m 이상 배회할 수 있는 **세계 규모** 환경을 HoloLens에 빌드하려면 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) 구성 요소를 사용해야 합니다.

혼합 현실 애플리케이션의 모든 핵심 구성 요소는 다른 Unity API와 일치하는 방식으로 공개됩니다. 이러한 구성 요소는 Mixed Reality Toolkit를 통해서도 사용할 수 있습니다.
* [카메라](camera-in-unity.md)
* [좌표계](coordinate-systems-in-unity.md)
* [응시](gaze-in-unity.md)
* [제스처 및 모션 컨트롤러](gestures-and-motion-controllers-in-unity.md)
* [음성 입력 ](voice-input-in-unity.md)
* [지속성](persistence-in-unity.md)
* [공간 음향](spatial-sound-in-unity.md)
* [공간 매핑](spatial-mapping-in-unity.md)

Unity 앱에도 공개되고 많은 혼합 현실 애플리케이션에서 사용하도록 하려는 다른 주요 기능은 다음과 같습니다.
* [공유 환경](shared-experiences-in-unity.md)
* [위치를 찾을 수 있는 카메라](locatable-camera-in-unity.md)
* [포커스 지점](focus-point-in-unity.md)
* [추적 손실](tracking-loss-in-unity.md)
* [키보드](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>실제 디바이스 또는 시뮬레이션된 디바이스에서 Unity 프로젝트 실행

홀로그램 Unity 프로젝트를 테스트할 준비가 되면 다음 단계로 [Unity Visual Studio 솔루션을 내보내고 빌드](exporting-and-building-a-unity-visual-studio-solution.md)합니다.

이 VS 솔루션을 사용하면 실제 디바이스 또는 시뮬레이션된 디바이스를 사용하여 다음 세 가지 방법 중 하나에서 애플리케이션을 실행할 수 있습니다.
* [실제 HoloLens 또는 Windows Mixed Reality 몰입형 헤드셋에 배포](using-visual-studio.md)
* [HoloLens 에뮬레이터에 배포](using-the-hololens-emulator.md)
* [Windows Mixed Reality 몰입형 헤드셋 시뮬레이터에 배포](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity 설명서

Unity는 docs.microsoft.com에서 사용할 수 있는 이 설명서 외에도 Windows Mixed Reality 기능에 대한 설명서를 Unity 편집기와 함께 설치합니다. Unity에서 제공하는 설명서에는 다음과 같은 두 개의 개별 섹션이 있습니다.
1. **Unity 스크립팅 참조**
    * 설명서의 이 섹션에는 Unity에서 제공하는 스크립팅 API에 대한 세부 정보가 포함되어 있습니다.
    * Unity 편집기에서 **도움말 > 스크립팅 참조**를 통해 액세스할 수 있습니다.
2. **Unity 설명서**
    * 이 설명서는 기본 기술에서 고급 기술에 이르기까지 Unity를 사용하는 방법을 익히는 데 도움이 되도록 설계되었습니다.
    * Unity 편집기에서 **도움말 > 설명서**를 통해 액세스할 수 있습니다.

## <a name="see-also"></a>참고 항목
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [MR 기본 100: Unity 시작](holograms-100.md)
* [Unity 권장 설정](recommended-settings-for-unity.md)
* [Unity의 권장 성능](performance-recommendations-for-unity.md)
* [Unity Visual Studio 솔루션 내보내기 및 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
* [HoloLens용 Unity 앱에서 Windows 네임스페이스 사용](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Unity 및 Visual Studio 사용 모범 사례](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 플레이 모드](unity-play-mode.md)
* [포팅 가이드](porting-guides.md)
