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
# <a name="native-development-overview"></a><span data-ttu-id="f7f15-104">네이티브 개발 개요</span><span class="sxs-lookup"><span data-stu-id="f7f15-104">Native development overview</span></span>

<span data-ttu-id="f7f15-105">Windows Mixed Reality 응용 프로그램은 다음 Api를 사용 하 여 HoloLens 및 기타 몰입 형 헤드셋에 대 한 [Mixed Reality](mixed-reality.md) 환경을 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-105">Windows Mixed Reality applications use the following APIs to build [mixed-reality](mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

 - [<span data-ttu-id="f7f15-106">홀로그램 렌더링</span><span class="sxs-lookup"><span data-stu-id="f7f15-106">Holographic rendering</span></span>](rendering.md)
 - [<span data-ttu-id="f7f15-107">응시</span><span class="sxs-lookup"><span data-stu-id="f7f15-107">Gaze</span></span>](gaze-and-commit.md)
 - [<span data-ttu-id="f7f15-108">지우는</span><span class="sxs-lookup"><span data-stu-id="f7f15-108">Gesture</span></span>](gaze-and-commit.md#composite-gestures)
 - [<span data-ttu-id="f7f15-109">동작 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="f7f15-109">Motion controller</span></span>](motion-controllers.md)
 - [<span data-ttu-id="f7f15-110">음성</span><span class="sxs-lookup"><span data-stu-id="f7f15-110">Voice</span></span>](voice-input.md)
 - [<span data-ttu-id="f7f15-111">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="f7f15-111">Spatial mapping</span></span>](spatial-mapping.md)

<span data-ttu-id="f7f15-112">[Unity](unity-development-overview.md)와 같은 3d 엔진을 사용 하 여 혼합 현실 응용 프로그램을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-112">You can create mixed reality applications by using a 3D engine, such as [Unity](unity-development-overview.md).</span></span> <span data-ttu-id="f7f15-113">또는 DirectX 11 또는 DirectX 12를 사용 하 여 Windows Mixed Reality Api에 직접 코딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-113">Or you can directly code to the Windows Mixed Reality APIs by using DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="f7f15-114">플랫폼을 직접 활용 하는 경우에는 기본적으로 자체 미들웨어 또는 프레임 워크를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-114">If you leverage the platform directly, you essentially build your own middleware or framework.</span></span> <span data-ttu-id="f7f15-115">Windows Api는 및 C++ C#모두에서 작성 된 응용 프로그램을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-115">The Windows APIs support applications that are written in both C++ and C#.</span></span> <span data-ttu-id="f7f15-116">를 사용 C#하는 경우 응용 프로그램은 [SharpDX](https://sharpdx.org/) 오픈 소스 소프트웨어 라이브러리를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-116">If you use C#, your application can leverage the [SharpDX](https://sharpdx.org/) open source software library.</span></span>

<span data-ttu-id="f7f15-117">Windows Mixed Reality는 다음과 같은 [두 가지 종류의 앱을](app-views.md)지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-117">Windows Mixed Reality supports [two kinds of apps](app-views.md):</span></span>
* <span data-ttu-id="f7f15-118">[HOLOGRAPHICSPACE api](getting-a-holographicspace.md) 또는 [OpenXR api](openxr.md) 를 사용 하 여 헤드셋 표시를 채우는 사용자에 게 [몰입 형 보기](app-views.md) 를 렌더링 하는 **혼합 현실 응용 프로그램** (UWP 또는 Win32)</span><span class="sxs-lookup"><span data-stu-id="f7f15-118">**Mixed-reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](app-views.md) to the user that fills the headset display</span></span>
* <span data-ttu-id="f7f15-119">DirectX, XAML 또는 다른 프레임 워크를 사용 하 여 Windows Mixed Reality 홈의 슬레이트에서 [2d 뷰](app-views.md#2d-views) 를 렌더링 하는 **2d 앱** (UWP)</span><span class="sxs-lookup"><span data-stu-id="f7f15-119">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="f7f15-120">[2d 보기 및 몰입 형 보기](app-views.md) 에 대 한 DirectX 개발 간의 차이점은 주로 holographic 렌더링 및 공간 입력에 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-120">The differences between DirectX development for [2D views and immersive views](app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="f7f15-121">UWP 응용 프로그램의 [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) 또는 Win32 응용 프로그램의 HWND는 필수 이며 거의 동일 하 게 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-121">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="f7f15-122">앱에서 사용할 수 있는 WinRT Api의 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-122">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="f7f15-123">하지만 holographic 기능을 활용 하려면 이러한 Api의 다른 하위 집합을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-123">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="f7f15-124">예를 들어이 swapchain present 및 프레임은 holographic 응용 프로그램에 대해 시스템에서 관리 되므로 포즈 예측 프레임 루프를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-124">For example, the swapchain and frame present is managed by the system for holographic applications in order to enable a pose-predicted frame loop.</span></span>

## <a name="get-started-with-openxr"></a><span data-ttu-id="f7f15-125">OpenXR 시작</span><span class="sxs-lookup"><span data-stu-id="f7f15-125">Get started with OpenXR</span></span>

<span data-ttu-id="f7f15-126">OpenXR를 사용 하 여 개발할 수 있습니다는 HoloLens 2 또는 Windows Mixed Reality 모던 헤드셋 바탕 화면입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-126">You can develop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset on the desktop.</span></span>  <span data-ttu-id="f7f15-127">헤드셋에 액세스할 수 없는 경우 HoloLens 2 에뮬레이터 또는 Windows Mixed Reality 시뮬레이터를 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-127">If you don't have access to a headset, you can use the HoloLens 2 Emulator or the Windows Mixed Reality Simulator instead.</span></span>

<span data-ttu-id="f7f15-128">HoloLens 2 또는 몰입 형 Windows Mixed Reality 헤드셋 용 OpenXR 응용 프로그램 개발을 시작 하려면 [OpenXR 개발을 시작 하는 방법](openxr-getting-started.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f7f15-128">To start developing OpenXR applications for HoloLens 2 or immersive Windows Mixed Reality headsets, see [how to get started with OpenXR development](openxr-getting-started.md).</span></span>

## <a name="get-started-with-winrt"></a><span data-ttu-id="f7f15-129">WinRT 시작</span><span class="sxs-lookup"><span data-stu-id="f7f15-129">Get started with WinRT</span></span>

<span data-ttu-id="f7f15-130">몰입 형 응용 프로그램 개발을 시작 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-130">To begin developing immersive applications:</span></span>
* <span data-ttu-id="f7f15-131">**Uwp 앱**의 경우 [Visual Studio의 템플릿을 사용 하 여 새 UWP 프로젝트를 만듭니다](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="f7f15-131">For **UWP apps**, [use the templates in Visual Studio to create a new UWP project](creating-a-holographic-directx-project.md).</span></span> <span data-ttu-id="f7f15-132">사용자의 언어, 시각적 개체 C++ 또는 시각적 C#개체를 기준으로 **WINDOWS Universal** > **Holographic**에서 UWP 템플릿을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-132">Based on your language, Visual C++ or Visual C#, find the UWP templates under **Windows Universal** > **Holographic**.</span></span>
* <span data-ttu-id="f7f15-133">**Win32 응용 프로그램**의 경우 [ *basichologram* Win32 샘플에서 시작](creating-a-holographic-directx-project.md#creating-a-win32-project)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-133">For **Win32 applications**, [start from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project).</span></span>

<span data-ttu-id="f7f15-134">이 단계는 기존 응용 프로그램 또는 엔진에 holographic 렌더링 지원을 추가 하는 데 필요한 코드를 가져오는 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-134">This step is a great way to get the code that you need to add holographic rendering support to an existing application or engine.</span></span> <span data-ttu-id="f7f15-135">코드 및 개념은 실시간 대화형 소프트웨어 개발자에 게 친숙 한 방식으로 템플릿에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-135">The code and concepts are presented in the template in a way that's familiar to any developer of real-time interactive software.</span></span>

<span data-ttu-id="f7f15-136">다음 항목에서는 Windows Mixed Reality 지원을 DirectX 기반 미들웨어에 추가할 때의 기본 요구 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-136">The following topics describe the base requirements when you add Windows Mixed Reality support to DirectX-based middleware.</span></span>

* <span data-ttu-id="f7f15-137">[Holographic DirectX 프로젝트 만들기](creating-a-holographic-directx-project.md): 설명서와 결합 된 holographic 응용 프로그램 템플릿에서는 사용 된 것과 비교한 차이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-137">[Create a holographic DirectX project](creating-a-holographic-directx-project.md): The holographic application template coupled with the documentation shows the differences compared to what you're used to.</span></span> <span data-ttu-id="f7f15-138">또한 헤드에 있는 동안 작동 하도록 설계 된 장치에 대 한 특별 한 요구 사항도 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-138">It also describes the special requirements for a device that's designed to function while resting on your head.</span></span>
* <span data-ttu-id="f7f15-139">[HolographicSpace 가져오기](getting-a-holographicspace.md): 먼저 응용 프로그램에 렌더링할 각 헤드 위치를 나타내는 HolographicFrame 개체의 시퀀스를 제공 하는 HolographicSpace를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-139">[Get a HolographicSpace](getting-a-holographicspace.md): You first need to create a HolographicSpace that gives your application the sequence of HolographicFrame objects that represent each head position from which you'll render.</span></span>
* <span data-ttu-id="f7f15-140">[DirectX에서 렌더링](rendering-in-directx.md): holographic이 swapchain present에는 두 개의 렌더링 대상이 있으므로 앱이 렌더링 되는 방식을 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-140">[Render in DirectX](rendering-in-directx.md): Because a holographic swapchain has two render targets, you must make some changes to the way your app renders.</span></span>
* <span data-ttu-id="f7f15-141">[DirectX에서 시스템 좌표계](coordinate-systems-in-directx.md): Windows Mixed Reality는 사용자의 안내에 따라 전 세계의 이해를 학습 하 고 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-141">[Coordinate systems in DirectX](coordinate-systems-in-directx.md): Windows Mixed Reality learns and updates its understanding of the world as the user walks around.</span></span> <span data-ttu-id="f7f15-142">이렇게 하면 응용 프로그램에서 공간 앵커 및 사용자의 정의 된 공간 단계를 비롯 한 사용자의 환경에 대 한 이유를 사용 하는 공간 좌표계가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-142">This provides spatial coordinate systems that applications use to reason about the user's surroundings, including spatial anchors and the user's defined spatial stage.</span></span>

## <a name="add-mixed-reality-capabilities-and-inputs"></a><span data-ttu-id="f7f15-143">혼합 현실 기능 및 입력 추가</span><span class="sxs-lookup"><span data-stu-id="f7f15-143">Add mixed reality capabilities and inputs</span></span>

<span data-ttu-id="f7f15-144">모던 앱 사용자에 게 가능한 최상의 환경을 제공 하려면 다음 주요 구성 요소를 지원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-144">To provide the best possible experience for users of your immersive app, you should support the following key building blocks:</span></span>

* [<span data-ttu-id="f7f15-145">DirectX의 헤드 및 눈 응시</span><span class="sxs-lookup"><span data-stu-id="f7f15-145">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="f7f15-146">DirectX의 헤드 및 모션 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="f7f15-146">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="f7f15-147">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="f7f15-147">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="f7f15-148">공간 음향</span><span class="sxs-lookup"><span data-stu-id="f7f15-148">Spatial sound</span></span>](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)
* [<span data-ttu-id="f7f15-149">DirectX의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="f7f15-149">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)

<span data-ttu-id="f7f15-150">이러한 기능은 다양 한 모던 응용 프로그램에서 DirectX 응용 프로그램에도 노출 되는 다른 주요 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="f7f15-150">These are other key features that many immersive applications use that are also exposed to DirectX applications:</span></span>

* [<span data-ttu-id="f7f15-151">DirectX의 공유 공간 앵커</span><span class="sxs-lookup"><span data-stu-id="f7f15-151">Shared spatial anchors in DirectX</span></span>](shared-spatial-anchors-in-directx.md)
* [<span data-ttu-id="f7f15-152">DirectX의 키보드, 마우스 및 컨트롤러 입력</span><span class="sxs-lookup"><span data-stu-id="f7f15-152">Keyboard, mouse, and controller input in DirectX</span></span>](keyboard-mouse-and-controller-input-in-directx.md)

## <a name="see-also"></a><span data-ttu-id="f7f15-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7f15-153">See also</span></span>
* [<span data-ttu-id="f7f15-154">앱 모델</span><span class="sxs-lookup"><span data-stu-id="f7f15-154">App model</span></span>](app-model.md)
* [<span data-ttu-id="f7f15-155">앱 보기</span><span class="sxs-lookup"><span data-stu-id="f7f15-155">App views</span></span>](app-views.md)
