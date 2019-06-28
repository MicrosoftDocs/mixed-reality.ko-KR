---
title: DirectX 개발 개요
description: 혼합 현실 Windows Api를 직접 사용 하 여 혼합된 현실 DirectX 기반 엔진을 구축 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: DirectX, holographic 렌더링, 네이티브, 네이티브 앱, WinRT, WinRT 앱 플랫폼 Api, 사용자 지정 엔진, 미들웨어
ms.openlocfilehash: da6beae6e256fef49481b581395e507b3f2acd04
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414380"
---
# <a name="directx-development-overview"></a>DirectX 개발 개요


Windows Mixed Reality 응용 프로그램을 사용 합니다 [holographic 렌더링](rendering.md), [gaze](gaze.md)를 [제스처](gestures.md), [동작 컨트롤러](motion-controllers.md)를 [음성](voice-input.md), 및 [공간 매핑](spatial-mapping.md) 작성 하는 Api [혼합 현실을](mixed-reality.md) HoloLens 및 몰입 형 헤드셋에 대 한 환경입니다. 와 같은 3D 엔진을 사용 하 여 혼합된 현실 응용 프로그램을 만들 수 있습니다 [Unity](unity-development-overview.md), 또는 DirectX 11 또는 DirectX 12를 사용 하 여 Windows 혼합 현실 Api를 직접 코딩할 수 있습니다. 플랫폼을 직접 활용 하는 경우 기본적으로 제작할 수 있습니다 고유한 미들웨어 또는 프레임 워크입니다. Windows Api를 둘 다 작성 된 응용 프로그램 지원 C++ 및 C#합니다. 사용 하려는 경우 C#를 응용 프로그램을 활용할 수 있습니다는 [SharpDX](http://sharpdx.org/) 오픈 소스 소프트웨어 라이브러리입니다.


Windows Mixed Reality 지원 [두 가지 종류의 앱](app-views.md):
* **실제로 응용 프로그램 혼합** (UWP 또는 Win32)를 사용 하는 합니다 [HolographicSpace API](getting-a-holographicspace.md) 렌더링 하는 [몰입 형 보기](app-views.md) 채우는 헤드셋 표시를 사용자에 게 합니다.
* **2D 앱** (UWP)을 사용 하 여 DirectX, XAML, 또는 다른 프레임 워크 렌더링 [2D 뷰](app-views.md#2d-views) Windows Mixed Reality 홈에서 슬레이트에 있습니다.


DirectX 개발에 대 한 차이점 [2D 뷰 및 몰입 형 뷰](app-views.md) 은 주로 holographic 관련된 렌더링 및 공간 입력 합니다. UWP 응용 프로그램 [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) Win32 응용 프로그램의 HWND가 필요 하며, 동일 주로 응용 프로그램에 사용 가능한 WinRT Api와 마찬가지로 또는 합니다. 그러나 holographic 기능을 활용 하는 이러한 Api의 다른 하위 집합을 사용 해야 합니다. 예를 들어 스왑 체인 holographic appslications에 대 한 시스템에서 관리 됩니다. DXGI에 보다는 HolographicSpace API를 사용 하 여 작업할 [프레임이 제시](rendering-in-directx.md)합니다.

몰입 형 응용 프로그램을 개발 하려면:
* 에 대 한 **UWP 앱**하십시오 [템플릿을 사용 하 여 Visual Studio에서 새 UWP 프로젝트를 만듭니다](creating-a-holographic-directx-project.md)합니다. 해당 언어에 따라 **시각적 C++**  또는 **Visual C#** 에서 UWP 템플릿을 찾을 수 있습니다 **Windows 유니버설**  >   **Holographic**합니다.
* 에 대 한 **Win32 응용 프로그램**를 [에서 시작 합니다 *BasicHologram* Win32 샘플](creating-a-holographic-directx-project.md#creating-a-win32-project)합니다.

이것이 holographic 렌더링 지원 기존 응용 프로그램 또는 엔진에 추가 해야 하는 코드를 가져올 수 있는 좋은 방법입니다. 코드 및 개념의 실시간 대화형 소프트웨어 개발자에 게 친숙 한 방식으로 템플릿에 표시 됩니다.


## <a name="getting-started"></a>시작

다음 항목에는 Windows Mixed Reality 지원 DirectX 기반 미들웨어를 추가 하는 기본 요구 사항을 설명 합니다.

* [Holographic DirectX 프로젝트를 만드는](creating-a-holographic-directx-project.md): 설명서를 함께 holographic 응용 프로그램 템플릿에 어떤 뿐만 아니라 머리 놓여 하는 동안 작동 하도록 설계 된 장치에서 도입 된 특별 한 요구 간의 차이점을 보여줍니다.
* [가져오기는 HolographicSpace](getting-a-holographicspace.md): 응용 프로그램 렌더링에서는 각 헤드 위치를 나타내는 HolographicFrame 개체의 시퀀스를 제공 하는 HolographicSpace를 만들려면 먼저 해야 합니다.
* [DirectX의 렌더링](rendering-in-directx.md): Holographic 스왑 체인 두 렌더링 대상에 있으므로 응용 프로그램이 렌더링 방식에 대 한 일부 변경 해야 합니다.
* [DirectX의 좌표계](coordinate-systems-in-directx.md): Windows Mixed Reality 학습 하 고 해당 이해는 전 세계의 관련 사용자에 설명 하는 대로 업데이트 합니다. 이 공간 좌표계 공간 앵커를 포함 하 여 사용자의 주변 환경에 대 한 이유를 사용 하 여 응용 프로그램을 사용자 정의 공간 단계를 제공 합니다.

## <a name="adding-mixed-reality-capabilities-and-inputs"></a>혼합된 현실 기능 및 입력 추가

몰입 형 appslication 프로그램의 사용자에 대 한 가능한 최상의 환경의 사용 하려면 다음 주요 구성 요소를 지원 하려면:

* [DirectX의 헤드 및 눈 응시](gaze-in-directx.md)
* [DirectX의 헤드 및 모션 컨트롤러](hands-and-motion-controllers-in-directx.md)
* [DirectX의 음성 입력](voice-input-in-directx.md)
* [DirectX의 공간 음향](spatial-sound-in-directx.md)
* [DirectX의 공간 매핑](spatial-mapping-in-directx.md)


기능은 다른 키 많은 몰입 형 응용 프로그램을 사용 하려고 하는 DirectX 응용 프로그램에도 표시 됩니다.

* [DirectX의 공유 공간 앵커](shared-spatial-anchors-in-directx.md)
* [DirectX의 위치를 찾을 수 있는 카메라](locatable-camera-in-directx.md)
* [DirectX의 키보드, 마우스 및 컨트롤러 입력](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a>참조
* [앱 모델](app-model.md)
* [앱 보기](app-views.md)
