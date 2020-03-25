---
title: 네이티브 개발 개요
description: Windows Mixed Reality Api를 직접 사용 하 여 DirectX 기반 혼합 현실 엔진을 빌드합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, holographic 렌더링, 네이티브, 네이티브 앱, WinRT, WinRT 앱, 플랫폼 Api, 사용자 지정 엔진, 미들웨어
ms.openlocfilehash: 5c61739ea6c90b4547c5c9927cf2129304650926
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80159999"
---
# <a name="native-development-overview"></a>네이티브 개발 개요

Windows Mixed Reality 응용 프로그램은 다음 Api를 사용 하 여 HoloLens 및 기타 몰입 형 헤드셋에 대 한 [Mixed Reality](mixed-reality.md) 환경을 구축 합니다.

 - [홀로그램 렌더링](rendering.md)
 - [응시](gaze-and-commit.md)
 - [지우는](gaze-and-commit.md#composite-gestures)
 - [동작 컨트롤러](motion-controllers.md)
 - [음성](voice-input.md)
 - [공간 매핑](spatial-mapping.md)

[Unity](unity-development-overview.md)와 같은 3d 엔진을 사용 하 여 혼합 현실 응용 프로그램을 만들 수 있습니다. 또는 DirectX 11 또는 DirectX 12를 사용 하 여 Windows Mixed Reality Api에 직접 코딩할 수 있습니다. 플랫폼을 직접 활용 하는 경우에는 기본적으로 자체 미들웨어 또는 프레임 워크를 빌드합니다. Windows Api는 및 C++ C#모두에서 작성 된 응용 프로그램을 지원 합니다. 를 사용 C#하는 경우 응용 프로그램은 [SharpDX](https://sharpdx.org/) 오픈 소스 소프트웨어 라이브러리를 활용할 수 있습니다.

Windows Mixed Reality는 다음과 같은 [두 가지 종류의 앱을](app-views.md)지원 합니다.
* [HOLOGRAPHICSPACE api](getting-a-holographicspace.md) 또는 [OpenXR api](openxr.md) 를 사용 하 여 헤드셋 표시를 채우는 사용자에 게 [몰입 형 보기](app-views.md) 를 렌더링 하는 **혼합 현실 응용 프로그램** (UWP 또는 Win32)
* DirectX, XAML 또는 다른 프레임 워크를 사용 하 여 Windows Mixed Reality 홈의 슬레이트에서 [2d 뷰](app-views.md#2d-views) 를 렌더링 하는 **2d 앱** (UWP)

[2d 보기 및 몰입 형 보기](app-views.md) 에 대 한 DirectX 개발 간의 차이점은 주로 holographic 렌더링 및 공간 입력에 문제가 있습니다. UWP 응용 프로그램의 [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) 또는 Win32 응용 프로그램의 HWND는 필수 이며 거의 동일 하 게 유지 됩니다. 앱에서 사용할 수 있는 WinRT Api의 경우에도 마찬가지입니다. 하지만 holographic 기능을 활용 하려면 이러한 Api의 다른 하위 집합을 사용 해야 합니다. 예를 들어이 swapchain present 및 프레임은 holographic 응용 프로그램에 대해 시스템에서 관리 되므로 포즈 예측 프레임 루프를 사용할 수 있습니다.

## <a name="get-started-with-openxr"></a>OpenXR 시작

OpenXR를 사용 하 여 개발할 수 있습니다는 HoloLens 2 또는 Windows Mixed Reality 모던 헤드셋 바탕 화면입니다.  헤드셋에 액세스할 수 없는 경우 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.

HoloLens 2 또는 몰입 형 Windows Mixed Reality 헤드셋 용 OpenXR 응용 프로그램 개발을 시작 하려면 [OpenXR 개발을 시작 하는 방법](openxr-getting-started.md)을 참조 하세요.

## <a name="get-started-with-winrt"></a>WinRT 시작

몰입 형 응용 프로그램 개발을 시작 하려면 다음을 수행 합니다.
* **Uwp 앱**의 경우 [Visual Studio의 템플릿을 사용 하 여 새 UWP 프로젝트를 만듭니다](creating-a-holographic-directx-project.md). 사용자의 언어, 시각적 개체 C++ 또는 시각적 C#개체를 기준으로 **WINDOWS Universal** > **Holographic**에서 UWP 템플릿을 찾습니다.
* **Win32 응용 프로그램**의 경우 [ *basichologram* Win32 샘플에서 시작](creating-a-holographic-directx-project.md#creating-a-win32-project)합니다.

이 단계는 기존 응용 프로그램 또는 엔진에 holographic 렌더링 지원을 추가 하는 데 필요한 코드를 가져오는 좋은 방법입니다. 코드 및 개념은 실시간 대화형 소프트웨어 개발자에 게 친숙 한 방식으로 템플릿에 제공 됩니다.

다음 항목에서는 Windows Mixed Reality 지원을 DirectX 기반 미들웨어에 추가할 때의 기본 요구 사항에 대해 설명 합니다.

* [Holographic DirectX 프로젝트 만들기](creating-a-holographic-directx-project.md): 설명서와 결합 된 holographic 응용 프로그램 템플릿에서는 사용 된 것과 비교한 차이점을 보여 줍니다. 또한 헤드에 있는 동안 작동 하도록 설계 된 장치에 대 한 특별 한 요구 사항도 설명 합니다.
* [HolographicSpace 가져오기](getting-a-holographicspace.md): 먼저 응용 프로그램에 렌더링할 각 헤드 위치를 나타내는 HolographicFrame 개체의 시퀀스를 제공 하는 HolographicSpace를 만들어야 합니다.
* [DirectX에서 렌더링](rendering-in-directx.md): holographic이 swapchain present에는 두 개의 렌더링 대상이 있으므로 앱이 렌더링 되는 방식을 변경 해야 합니다.
* [DirectX에서 시스템 좌표계](coordinate-systems-in-directx.md): Windows Mixed Reality는 사용자의 안내에 따라 전 세계의 이해를 학습 하 고 업데이트 합니다. 이렇게 하면 응용 프로그램에서 공간 앵커 및 사용자의 정의 된 공간 단계를 비롯 한 사용자의 환경에 대 한 이유를 사용 하는 공간 좌표계가 제공 됩니다.

## <a name="add-mixed-reality-capabilities-and-inputs"></a>혼합 현실 기능 및 입력 추가

모던 앱 사용자에 게 가능한 최상의 환경을 제공 하려면 다음 주요 구성 요소를 지원 해야 합니다.

* [DirectX의 헤드 및 눈 응시](gaze-in-directx.md)
* [DirectX의 헤드 및 모션 컨트롤러](hands-and-motion-controllers-in-directx.md)
* [DirectX의 음성 입력](voice-input-in-directx.md)
* [공간 음향](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [DirectX의 공간 매핑](spatial-mapping-in-directx.md)

이러한 기능은 다양 한 모던 응용 프로그램에서 DirectX 응용 프로그램에도 노출 되는 다른 주요 기능입니다.

* [DirectX의 공유 공간 앵커](shared-spatial-anchors-in-directx.md)
* [DirectX의 키보드, 마우스 및 컨트롤러 입력](keyboard-mouse-and-controller-input-in-directx.md)

## <a name="see-also"></a>참고 항목
* [앱 모델](app-model.md)
* [앱 보기](app-views.md)
