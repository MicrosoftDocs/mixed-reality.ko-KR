---
title: DirectX 개발 개요
description: 혼합 현실 Windows Api를 직접 사용 하 여 혼합된 현실 DirectX 기반 엔진을 구축 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, holographic 렌더링, 네이티브, 네이티브 앱, WinRT, WinRT 앱 플랫폼 Api, 사용자 지정 엔진, 미들웨어
ms.openlocfilehash: 60c4de7025099f38f0902e2ff24579e7088835a6
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628986"
---
# <a name="directx-development-overview"></a>DirectX 개발 개요

Windows Mixed Reality 앱을 사용 합니다 [holographic 렌더링](rendering.md), [gaze](gaze.md)를 [제스처](gestures.md)를 [동작 컨트롤러](motion-controllers.md), [음성 ](voice-input.md) 하 고 [공간 매핑](spatial-mapping.md) Api를 빌드 [혼합 현실을](mixed-reality.md) HoloLens 및 몰입 형 헤드셋에 대 한 환경. 혼합된 현실 앱 같은 3D 엔진을 사용 하 여 만들 수 있습니다 [Unity](unity-development-overview.md), 또는 DirectX 11 또는 DirectX 12를 사용 하 여 Windows 혼합 현실 Api를 직접 코딩할 수 있습니다. 플랫폼을 직접 활용 하는 경우 기본적으로 제작할 수 있습니다 고유한 미들웨어 또는 프레임 워크입니다. Windows Api를 둘 다로 작성 된 앱 지원 C++ 및 C#합니다. 사용 하려는 경우 C#를 응용 프로그램을 활용할 수 있습니다는 [SharpDX](http://sharpdx.org/) 오픈 소스 소프트웨어 라이브러리입니다.

Windows Mixed Reality 지원 [두 가지 종류의 앱](app-views.md):
* **혼합 현실 앱** (UWP 또는 Win32) 사용 하는 합니다 [HolographicSpace API](getting-a-holographicspace.md) 렌더링 하는 [몰입 형 뷰](app-views.md) 채우는 헤드셋 표시를 사용자에 게 합니다.
* **2D 앱** (UWP)를 사용 하는 DirectX, XAML 또는 다른 프레임 워크를 렌더링 하 [2D 뷰](app-views.md#2d-views) Windows Mixed Reality 홈에서 슬레이트에 있습니다.

DirectX 개발에 대 한 차이점 [2D 뷰 및 몰입 형 뷰](app-views.md) 은 주로 holographic 관련된 렌더링 및 공간 입력 합니다. UWP 앱의 [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) 또는 Win32 앱의 HWND 여전히 필요 하며 동일 거의 마찬가지로 WinRT Api 앱에 사용할 수 있습니다. 그러나 사용 하 여 이러한 Api의 다른 하위 집합 holographic 기능 활용. 예를 들어 스왑 체인 holographic 앱에 대 한 시스템에서 관리 되는 및를 DXGI 대신 HolographicSpace API를 사용 하 여 작업할 [프레임이 제시](rendering-in-directx.md)합니다.

몰입 형 앱을 개발 하려면:
* 에 대 한 **UWP 앱**하십시오 [템플릿을 사용 하 여 Visual Studio에서 새 UWP 프로젝트를 만듭니다](creating-a-holographic-directx-project.md)합니다. 프로그램 언어를 기반으로 **시각적 C++**  또는 **Visual C#** , UWP 템플릿을 아래를 보면 **Windows 유니버설**  >   **Holographic**합니다.
* 에 대 한 **Win32 앱**를 [에서 시작 합니다 *BasicHologram* Win32 샘플](creating-a-holographic-directx-project.md#creating-a-win32-project)합니다.

이것이 기존 앱 또는 엔진에 holographic 렌더링 지원을 추가 해야 하는 코드를 가져올 수 있는 좋은 방법입니다. 코드 및 개념의 실시간 대화형 소프트웨어 개발자에 게 친숙 한 방식으로 템플릿에 표시 됩니다.

## <a name="getting-started"></a>시작

다음 항목에는 Windows Mixed Reality 지원 DirectX 기반 미들웨어를 추가 하는 기본 요구 사항을 설명 합니다.
* [Holographic DirectX 프로젝트를 만드는](creating-a-holographic-directx-project.md): 설명서를 함께 holographic 앱 템플릿을 사용 하는 머리 놓여 하는 동안 작동 하도록 설계 된 장치에서 도입 된 특별 한 요구와 어떻게 다른 표시 됩니다.
* [가져오기는 HolographicSpace](getting-a-holographicspace.md): 제공 하는 앱 렌더링에서는 각 헤드 위치를 나타내는 HolographicFrame 개체의 시퀀스를 HolographicSpace를 만들려면 먼저 해야 합니다.
* [DirectX의 렌더링](rendering-in-directx.md): Holographic 스왑 체인 두 렌더링 대상에 있으므로 응용 프로그램 렌더링 방식에 일부 변경을 수행 해야 가능성이 높습니다.
* [DirectX의 좌표계](coordinate-systems-in-directx.md): Windows Mixed Reality 학습 하 고 앱 공간 앵커 및 사용자 정의 된 공간 단계를 포함 하 여 사용자의 주변 환경에 대 한 이유를 사용 하는 공간 좌표계 제공, 사용자 안내도 전 세계의 이해를 업데이트 합니다.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>혼합된 현실 기능 및 입력 추가

몰입 형 앱의 사용자에 대 한 가능한 최상의 환경의 사용 하려면 다음 주요 구성 요소를 지원 하려면:
* [DirectX의 헤드 및 눈 응시](gaze-in-directx.md)
* [실습 및 DirectX에서 컨트롤러 동작](hands-and-motion-controllers-in-directx.md)
* [DirectX의 음성 입력](voice-input-in-directx.md)
* [DirectX의 공간 음향](spatial-sound-in-directx.md)
* [DirectX의 공간 매핑](spatial-mapping-in-directx.md)

다른 키 많은 몰입 형 앱을 사용 하려고 하는 제공 되는 기능 또한 DirectX 앱에는
* [DirectX의 공유 공간 앵커](shared-spatial-anchors-in-directx.md)
* [DirectX의 위치를 찾을 수 있는 카메라](locatable-camera-in-directx.md)
* [DirectX의 키보드, 마우스 및 컨트롤러 입력](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>참조
* [앱 모델](app-model.md)
* [앱 보기](app-views.md)
