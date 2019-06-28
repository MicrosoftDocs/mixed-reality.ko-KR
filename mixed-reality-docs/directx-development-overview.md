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
# <a name="directx-development-overview"></a><span data-ttu-id="6ed7d-104">DirectX 개발 개요</span><span class="sxs-lookup"><span data-stu-id="6ed7d-104">DirectX development overview</span></span>


<span data-ttu-id="6ed7d-105">Windows Mixed Reality 응용 프로그램을 사용 합니다 [holographic 렌더링](rendering.md), [gaze](gaze.md)를 [제스처](gestures.md), [동작 컨트롤러](motion-controllers.md)를 [음성](voice-input.md), 및 [공간 매핑](spatial-mapping.md) 작성 하는 Api [혼합 현실을](mixed-reality.md) HoloLens 및 몰입 형 헤드셋에 대 한 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-105">Windows Mixed Reality applications use the [holographic rendering](rendering.md), [gaze](gaze.md), [gesture](gestures.md), [motion controller](motion-controllers.md), [voice](voice-input.md), and [spatial mapping](spatial-mapping.md) APIs to build [mixed reality](mixed-reality.md) experiences for HoloLens and immersive headsets.</span></span> <span data-ttu-id="6ed7d-106">와 같은 3D 엔진을 사용 하 여 혼합된 현실 응용 프로그램을 만들 수 있습니다 [Unity](unity-development-overview.md), 또는 DirectX 11 또는 DirectX 12를 사용 하 여 Windows 혼합 현실 Api를 직접 코딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-106">You can create mixed reality applications using a 3D engine, such as [Unity](unity-development-overview.md), or you can directly code to the Windows Mixed Reality APIs using DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="6ed7d-107">플랫폼을 직접 활용 하는 경우 기본적으로 제작할 수 있습니다 고유한 미들웨어 또는 프레임 워크입니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-107">If you are leveraging the platform directly, you'll essentially be building your own middleware or framework.</span></span> <span data-ttu-id="6ed7d-108">Windows Api를 둘 다 작성 된 응용 프로그램 지원 C++ 및 C#합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-108">The Windows APIs support applications written in both C++ and C#.</span></span> <span data-ttu-id="6ed7d-109">사용 하려는 경우 C#를 응용 프로그램을 활용할 수 있습니다는 [SharpDX](http://sharpdx.org/) 오픈 소스 소프트웨어 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-109">If you choose to use C#, your application can leverage the [SharpDX](http://sharpdx.org/) open source software library.</span></span>


<span data-ttu-id="6ed7d-110">Windows Mixed Reality 지원 [두 가지 종류의 앱](app-views.md):</span><span class="sxs-lookup"><span data-stu-id="6ed7d-110">Windows Mixed Reality supports [two kinds of apps](app-views.md):</span></span>
* <span data-ttu-id="6ed7d-111">**실제로 응용 프로그램 혼합** (UWP 또는 Win32)를 사용 하는 합니다 [HolographicSpace API](getting-a-holographicspace.md) 렌더링 하는 [몰입 형 보기](app-views.md) 채우는 헤드셋 표시를 사용자에 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-111">**Mixed reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) to render an [immersive view](app-views.md) to the user that fills the headset display.</span></span>
* <span data-ttu-id="6ed7d-112">**2D 앱** (UWP)을 사용 하 여 DirectX, XAML, 또는 다른 프레임 워크 렌더링 [2D 뷰](app-views.md#2d-views) Windows Mixed Reality 홈에서 슬레이트에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-112">**2D apps** (UWP) that use DirectX, XAML, or other frameworks to render [2D views](app-views.md#2d-views) on slates in the Windows Mixed Reality home.</span></span>


<span data-ttu-id="6ed7d-113">DirectX 개발에 대 한 차이점 [2D 뷰 및 몰입 형 뷰](app-views.md) 은 주로 holographic 관련된 렌더링 및 공간 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-113">The differences between DirectX development for [2D views and immersive views](app-views.md) are primarily related to holographic rendering and spatial input.</span></span> <span data-ttu-id="6ed7d-114">UWP 응용 프로그램 [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) Win32 응용 프로그램의 HWND가 필요 하며, 동일 주로 응용 프로그램에 사용 가능한 WinRT Api와 마찬가지로 또는 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-114">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required, and remain largely the same, as do the WinRT APIs available to your application.</span></span> <span data-ttu-id="6ed7d-115">그러나 holographic 기능을 활용 하는 이러한 Api의 다른 하위 집합을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-115">However, you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="6ed7d-116">예를 들어 스왑 체인 holographic appslications에 대 한 시스템에서 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-116">For example, the swap chain is managed by the system for holographic appslications.</span></span> <span data-ttu-id="6ed7d-117">DXGI에 보다는 HolographicSpace API를 사용 하 여 작업할 [프레임이 제시](rendering-in-directx.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-117">You work with the HolographicSpace API rather than DXGI to [present frames](rendering-in-directx.md).</span></span>

<span data-ttu-id="6ed7d-118">몰입 형 응용 프로그램을 개발 하려면:</span><span class="sxs-lookup"><span data-stu-id="6ed7d-118">To begin developing immersive applications:</span></span>
* <span data-ttu-id="6ed7d-119">에 대 한 **UWP 앱**하십시오 [템플릿을 사용 하 여 Visual Studio에서 새 UWP 프로젝트를 만듭니다](creating-a-holographic-directx-project.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-119">For **UWP apps**, [create a new UWP project using the templates in Visual Studio](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="6ed7d-120">해당 언어에 따라 **시각적 C++**  또는 **Visual C#** 에서 UWP 템플릿을 찾을 수 있습니다 **Windows 유니버설**  >   **Holographic**합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-120">Based on your language, **Visual C++** or **Visual C#**, you can find the UWP templates under **Windows Universal** > **Holographic**.</span></span>
* <span data-ttu-id="6ed7d-121">에 대 한 **Win32 응용 프로그램**를 [에서 시작 합니다 *BasicHologram* Win32 샘플](creating-a-holographic-directx-project.md#creating-a-win32-project)합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-121">For **Win32 applications**, [start from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project).</span></span>

<span data-ttu-id="6ed7d-122">이것이 holographic 렌더링 지원 기존 응용 프로그램 또는 엔진에 추가 해야 하는 코드를 가져올 수 있는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-122">This is a great way to get the code that you need to add holographic rendering support to an existing application or engine.</span></span> <span data-ttu-id="6ed7d-123">코드 및 개념의 실시간 대화형 소프트웨어 개발자에 게 친숙 한 방식으로 템플릿에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-123">Code and concepts are presented in the template in a way that's familiar to any developer of real-time interactive software.</span></span>


## <a name="getting-started"></a><span data-ttu-id="6ed7d-124">시작</span><span class="sxs-lookup"><span data-stu-id="6ed7d-124">Getting started</span></span>

<span data-ttu-id="6ed7d-125">다음 항목에는 Windows Mixed Reality 지원 DirectX 기반 미들웨어를 추가 하는 기본 요구 사항을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-125">The following topics discuss the base requirements of adding Windows Mixed Reality support to DirectX-based middleware:</span></span>

* <span data-ttu-id="6ed7d-126">[Holographic DirectX 프로젝트를 만드는](creating-a-holographic-directx-project.md): 설명서를 함께 holographic 응용 프로그램 템플릿에 어떤 뿐만 아니라 머리 놓여 하는 동안 작동 하도록 설계 된 장치에서 도입 된 특별 한 요구 간의 차이점을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-126">[Creating a holographic DirectX project](creating-a-holographic-directx-project.md): The holographic application template coupled with the documentation shows you the differences between what you're used to as well as the special requirements introduced by a device that's designed to function while resting on your head.</span></span>
* <span data-ttu-id="6ed7d-127">[가져오기는 HolographicSpace](getting-a-holographicspace.md): 응용 프로그램 렌더링에서는 각 헤드 위치를 나타내는 HolographicFrame 개체의 시퀀스를 제공 하는 HolographicSpace를 만들려면 먼저 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-127">[Getting a HolographicSpace](getting-a-holographicspace.md): You'll first need to create a HolographicSpace That will provide your application the sequence of HolographicFrame objects that represent each head position from which you'll render.</span></span>
* <span data-ttu-id="6ed7d-128">[DirectX의 렌더링](rendering-in-directx.md): Holographic 스왑 체인 두 렌더링 대상에 있으므로 응용 프로그램이 렌더링 방식에 대 한 일부 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-128">[Rendering in DirectX](rendering-in-directx.md): Since a holographic swap chain has two render targets, you'll need to make some changes to the way your application renders.</span></span>
* <span data-ttu-id="6ed7d-129">[DirectX의 좌표계](coordinate-systems-in-directx.md): Windows Mixed Reality 학습 하 고 해당 이해는 전 세계의 관련 사용자에 설명 하는 대로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-129">[Coordinate systems in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality learns and updates its understanding of the world as the user walks around.</span></span> <span data-ttu-id="6ed7d-130">이 공간 좌표계 공간 앵커를 포함 하 여 사용자의 주변 환경에 대 한 이유를 사용 하 여 응용 프로그램을 사용자 정의 공간 단계를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-130">This provides spatial coordinate systems that applications use to reason about the user's surroundings, including spatial anchors and the user's defined spatial stage.</span></span>

## <a name="adding-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="6ed7d-131">혼합된 현실 기능 및 입력 추가</span><span class="sxs-lookup"><span data-stu-id="6ed7d-131">Adding mixed reality capabilities and inputs</span></span>

<span data-ttu-id="6ed7d-132">몰입 형 appslication 프로그램의 사용자에 대 한 가능한 최상의 환경의 사용 하려면 다음 주요 구성 요소를 지원 하려면:</span><span class="sxs-lookup"><span data-stu-id="6ed7d-132">To enable the best possible experience for users of your immersive appslication, you'll want to support the following key building blocks:</span></span>

* [<span data-ttu-id="6ed7d-133">DirectX의 헤드 및 눈 응시</span><span class="sxs-lookup"><span data-stu-id="6ed7d-133">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="6ed7d-134">DirectX의 헤드 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="6ed7d-134">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="6ed7d-135">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="6ed7d-135">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="6ed7d-136">DirectX의 공간 음향</span><span class="sxs-lookup"><span data-stu-id="6ed7d-136">Spatial sound in DirectX</span></span>](spatial-sound-in-directx.md)
* [<span data-ttu-id="6ed7d-137">DirectX의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="6ed7d-137">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)


<span data-ttu-id="6ed7d-138">기능은 다른 키 많은 몰입 형 응용 프로그램을 사용 하려고 하는 DirectX 응용 프로그램에도 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ed7d-138">There are other key features that many immersive applications will want to use that are also exposed to DirectX applicaitons:</span></span>

* [<span data-ttu-id="6ed7d-139">DirectX의 공유 공간 앵커</span><span class="sxs-lookup"><span data-stu-id="6ed7d-139">Shared spatial anchors in DirectX</span></span>](shared-spatial-anchors-in-directx.md)
* [<span data-ttu-id="6ed7d-140">DirectX의 위치를 찾을 수 있는 카메라</span><span class="sxs-lookup"><span data-stu-id="6ed7d-140">Locatable camera in DirectX</span></span>](locatable-camera-in-directx.md)
* [<span data-ttu-id="6ed7d-141">DirectX의 키보드, 마우스 및 컨트롤러 입력</span><span class="sxs-lookup"><span data-stu-id="6ed7d-141">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard,-mouse,-and-controller-input-in-directx.md)

## <a name="see-also"></a><span data-ttu-id="6ed7d-142">참조</span><span class="sxs-lookup"><span data-stu-id="6ed7d-142">See also</span></span>
* [<span data-ttu-id="6ed7d-143">앱 모델</span><span class="sxs-lookup"><span data-stu-id="6ed7d-143">App model</span></span>](app-model.md)
* [<span data-ttu-id="6ed7d-144">앱 보기</span><span class="sxs-lookup"><span data-stu-id="6ed7d-144">App views</span></span>](app-views.md)
