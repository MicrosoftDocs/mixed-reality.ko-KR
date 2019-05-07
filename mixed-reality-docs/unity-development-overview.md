---
title: Unity 개발 개요
description: 시작 빌드를 시작된 혼합 현실 앱 Unity에서.
author: thetuvix
ms.author: Yoyoz
ms.date: 04/15/2018
ms.topic: article
keywords: Unity, 혼합 현실, 개발, 시작, 새 프로젝트를 이식, 기능, 카메라, 시뮬레이션, 에뮬레이션, 설명서
ms.openlocfilehash: 2cdcd5e997ab7e3f6d340377464e453a8e7c025c
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873999"
---
# <a name="unity-development-overview"></a>Unity 개발 개요

가장 빠른 빌드 경로 [혼합된 현실 앱](app-views.md) 된 [Unity](http://aka.ms/HoloLensUnity)합니다. 탐색 하는 데 시간이 하는 것이 좋습니다 합니다 [Unity 자습서](https://unity3d.com/learn/tutorials)합니다. Unity에는 포괄적인 자산을 할 경우 [Asset Store](https://www.assetstore.unity3d.com/)합니다. Unity의 기본적인 이해를 만든 후 방문할 수 있습니다 합니다 [자습서](tutorials.md) Unity 사용한 혼합된 현실 개발의 세부 정보를 알아보려면 합니다. 방문 해야 합니다 [Unity 혼합 현실 포럼](http://forum.unity3d.com/forums/hololens.102/) Unity에서 혼합된 현실 앱을 빌드하는 커뮤니티의 나머지와 함께 문제를 발생할 수에 합니다.


Unity 사용 하 여 혼합된 현실 앱을 처음 빌드하는 방법을 [도구를 설치](install-the-tools.md)합니다. 

## <a name="new-unity-project-with-mixed-reality-toolkit"></a>혼합된 현실 도구 키트를 사용 하 여 새 Unity 프로젝트 

혼합 현실 Toolkit을 통해 Unity에서 개발 하는 가장 쉬운 방법은 됩니다. 자동으로 프로젝트를 사용 하 여 설치 하는 데 도움이 되 고 개발을 가속화 혼합 현실 기능 집합을 제공 합니다. 확인해 보십시오 [혼합 현실 Toolkit v2](mrtk-getting-started.md) 알아보고 시작 하세요. 

## <a name="porting-an-existing-unity-app-to-windows-mixed-reality"></a>Windows Mixed Reality로 기존 Unity 앱 이식

Windows Mixed Reality로 이식 하려는 기존 Unity 프로젝트에 있는 경우를 함께 수행 합니다 [Unity 포팅 가이드](porting-guides.md) 시작 하려면.

## <a name="configuring-new-unity-project-for-windows-mixed-reality"></a>Windows Mixed Reality에 대 한 새 Unity 프로젝트를 구성합니다.

혼합 현실 도구 키트를 가져오지 않고 새 Unity 프로젝트를 생성 하려는 경우 소규모의 두 범주로 구분 하는 Windows Mixed Reality를 수동으로 변경 해야 하는 Unity 설정 가지: 프로젝트별와 장면 당 합니다. 에 대 한 단계별 가이드 여기를 참조 하세요. [새 Unity 프로젝트에 대 한 Windows Mixed Reality를 구성 합니다.](Configure-Unity-Project.md)

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>혼합된 현실 기능 및 입력 추가

설정한 MRTK V2 프로젝트를 사용 하 여 위에서 설명한 대로 프로젝트를 구성 하거나, 표준 Unity 게임 개체 (예: 카메라)가 켜 집니다 즉시에 **장착 규모 환경**를 업데이트 하는 카메라의 위치를 사용 하 여 자동 사용자로 해당 헤드 전 세계를 통해 이동합니다.

Windows Mixed Reality 기능에 대 한 지원 같은 추가 [공간 단계](coordinate-systems.md#spatial-coordinate-systems)를 [제스처, 동작 컨트롤러](gestures-and-motion-controllers-in-unity.md) 또는 [입력 음성](voice-input-in-unity.md) 에 직접 작성 한 Api를 사용 하 여 이루어집니다 Unity 합니다. 

첫 번째 단계를 검토 해야 합니다 [눈금을 경험](coordinate-systems.md) 앱 대상으로 지정할 수 있는:
* 빌드 하려는 경우는 **방향 으로만 이동 가능한** 또는 **장착 규모 경험**를 설정 해야 합니다. Unity 공간 형식을 추적의 [고정](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)합니다.
* 빌드 하려는 경우는 **고정 크기 조정** 또는 **방 규모 환경**, Unity의 확인 해야 합니다. 공간 형식 추적을 설정 했습니다.는 [RoomScale](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience).
* 빌드 하려는 경우는 **전 세계 규모** HoloLens에서 experience 5m 초과 로밍 하는 사용자 수를 해야 사용 하는 [WorldAnchor](coordinate-systems-in-unity.md#building-a-world-scale-experience) 구성 요소.

혼합된 현실 앱에 대 한 핵심 구성 요소를 모두 다른 Unity Api를 사용 하 여 일관 된 방식으로 노출 됩니다. 혼합 현실 도구 키트를 통해 사용할 수 있습니다.
* [카메라](camera-in-unity.md)
* [좌표계](coordinate-systems-in-unity.md)
* [응시](gaze-in-unity.md)
* [제스처와 컨트롤러 동작](gestures-and-motion-controllers-in-unity.md)
* [음성 입력 ](voice-input-in-unity.md)
* [지속성](persistence-in-unity.md)
* [공간 음향](spatial-sound-in-unity.md)
* [공간 매핑](spatial-mapping-in-unity.md)

다 수의 혼합된 현실 앱은 원하는 사용 하려면 Unity 앱에도 표시 됩니다는 다른 주요 기능에는
* [공유 경험](shared-experiences-in-unity.md)
* [위치를 찾을 수 있는 카메라](locatable-camera-in-unity.md)
* [Focus point](focus-point-in-unity.md)
* [손실 추적](tracking-loss-in-unity.md)
* [키보드](keyboard-input-in-unity.md)

## <a name="running-your-unity-project-on-a-real-or-simulated-device"></a>실제 또는 시뮬레이트된 장치에서 Unity 프로젝트를 실행합니다.

다음 단계를 가져온 후 holographic Unity 프로젝트를 테스트할 준비가, [Unity Visual Studio 솔루션을 빌드하고 내보내기](exporting-and-building-a-unity-visual-studio-solution.md)합니다.

준비 되었으면에서 해당 VS 솔루션을 실행할 수 있습니다 다음 앱 세 가지 방법 중 하나에서 하나를 사용 하 여 실제 또는 시뮬레이트된 장치:
* [실제 HoloLens 또는 Windows Mixed Reality 몰입 형 헤드셋에 배포](using-visual-studio.md)
* [HoloLens 에뮬레이터에 배포](using-the-hololens-emulator.md)
* [Windows Mixed Reality 몰입 형 헤드셋 시뮬레이터에 배포](using-the-windows-mixed-reality-simulator.md)

## <a name="unity-documentation"></a>Unity 설명서

Windows 개발자 센터에서 사용할 수 있는이 문서에서는 외에도 Unity는 Unity 편집기와 함께 Windows Mixed Reality 기능에 대 한 설명서를 설치합니다. Unity는 설명서에는 별도 두 섹션이 포함 되어 있습니다.을 제공 합니다.
1. **Unity 스크립팅 참조**
    * 설명서의이 섹션에서는 Unity가 제공 하는 스크립팅 API의 세부 정보를 포함 합니다.
    * 통해 Unity 편집기에서 사용 하 여 액세스할 수 있는 **도움말 > 스크립팅 참조**
2. **Unity 설명서**
    * 이 설명서는 고급 기본 기술에서 Unity를 사용 하는 방법을 배울 수 있도록 설계 되었습니다.
    * 통해 Unity 편집기에서 사용 하 여 액세스할 수 있는 **도움말 > 수동**

## <a name="see-also"></a>참조
* [혼합 현실을 Toolkit v2](mrtk-getting-started.md)
* [MR 기본 100: Unity 시작](holograms-100.md)
* [Unity 권장 설정](recommended-settings-for-unity.md)
* [Unity의 권장 성능](performance-recommendations-for-unity.md)
* [Unity Visual Studio 솔루션 내보내기 및 빌드](exporting-and-building-a-unity-visual-studio-solution.md)
* [HoloLens용 Unity 앱에서 Windows 네임스페이스 사용](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Unity 및 Visual Studio 사용 모범 사례](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity 플레이 모드](unity-play-mode.md)
* [포팅 가이드](porting-guides.md)
