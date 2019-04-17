---
title: Holographic DirectX 앱에서 XAML 사용
description: 2D XAML 뷰 및 DirectX 앱 및 XAML 뷰 및 몰입 형 뷰 모두 효율적으로 사용 하는 방법의 몰입 형 뷰 간의 전환의 영향에 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 관리, xaml, 키보드, 연습에서는 windows 혼합된 현실 등 UWP 앱에서 볼 DirectX
ms.openlocfilehash: 32b2feea0cb6b8aba972c1772451ca7b5b9946d5
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598685"
---
# <a name="using-xaml-with-holographic-directx-apps"></a><span data-ttu-id="d749c-104">Holographic DirectX 앱에서 XAML 사용</span><span class="sxs-lookup"><span data-stu-id="d749c-104">Using XAML with holographic DirectX apps</span></span>

<span data-ttu-id="d749c-105">이 항목에서는 전환의 영향을 설명 합니다. [2D XAML 뷰 및 몰입 형 뷰](app-views.md) DirectX 앱 및 XAML 뷰 및 몰입 형 뷰 모두 효율적으로 사용 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-105">This topic explains the impact of switching between [2D XAML views and immersive views](app-views.md) in your DirectX app, and how to make efficient use of both a XAML view and immersive view.</span></span>

## <a name="xaml-view-switching-overview"></a><span data-ttu-id="d749c-106">개요를 전환 하는 XAML 보기</span><span class="sxs-lookup"><span data-stu-id="d749c-106">XAML view switching overview</span></span>

<span data-ttu-id="d749c-107">HoloLens에서 2D XAML 뷰를 나중에 표시 될 수 있는 일반적으로 몰입 형 앱을 해당 XAML 뷰를 먼저 초기화 하 고 즉시 여기에서 몰입 형 뷰를 전환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-107">On HoloLens, a generally immersive app that may later display a 2D XAML view must initialize that XAML view first and immediately switch to an immersive view from there.</span></span> <span data-ttu-id="d749c-108">즉, 앱 작업을 수행 하려면 먼저 XAML 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-108">This means XAML will load before your app can do anything.</span></span> <span data-ttu-id="d749c-109">결과적으로, 시작 시간을 조금 향상 되 고 XAML을 계속 백그라운드;에 있는 동안 앱 프로세스에서 메모리 공간을 차지 시작 지연 시간 및 사용 현황은 어떤 앱에 따라 달라 집니다 메모리의 양을 기본 뷰로 전환 하기 전에 XAML을 사용 하 여 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-109">As a result, there will be a small increase in your startup time, and XAML will continue to occupy memory space in your app process while it resides in the background; the amount of startup delay and memory usage depends on what your app does with XAML before switching to the native view.</span></span> <span data-ttu-id="d749c-110">아무 일도 하지 몰입 형 보기 시작 점을 제외 하면 처음에는 코드에 XAML 시작에서 하는 경우에 영향을 부 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-110">If you do nothing in your XAML start up code at first except start your immersive view, the impact should be minor.</span></span> <span data-ttu-id="d749c-111">또한 사용자 holographic 렌더링, 몰입도 높은 뷰로 직접 수행 되므로 해당 렌더링에 대 한 XAML 관련 제한을 요청할지를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-111">Also, because your holographic rendering is done directly to the immersive view, you will avoid any XAML-related restrictions on that rendering.</span></span>

<span data-ttu-id="d749c-112">CPU와 GPU에 대 한 메모리 사용량을 계산 하는 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-112">Note that the memory usage counts for both CPU and GPU.</span></span> <span data-ttu-id="d749c-113">Direct3D 11 가상 그래픽 메모리 스왑할 수 있지만 XAML GPU 리소스의 일부 또는 전부를 스왑할 못할 것 이며 눈에 띄는 성능 저하가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-113">Direct3D 11 is able to swap virtual graphics memory, but it might not be able to swap out some or all of the XAML GPU resources, and there might be a noticeable performance hit.</span></span> <span data-ttu-id="d749c-114">어느 방법이 든 모든 XAML 기능을 로드 하지 있습니다 하지 필요한 앱에 대 한 더 많은 공간을 둡니다를 더 나은 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-114">Either way, not loading any XAML features you don't need will leave more room for your app and provide a better experience.</span></span>

## <a name="xaml-view-switching-workflow"></a><span data-ttu-id="d749c-115">워크플로 전환 하는 XAML 보기</span><span class="sxs-lookup"><span data-stu-id="d749c-115">XAML view switching workflow</span></span>

<span data-ttu-id="d749c-116">몰입 형 모드에 XAML에서 직접이 되는 앱에 대 한 워크플로 다음과 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-116">The workflow for an app that goes directly from XAML to immersive mode is like so:</span></span>
* <span data-ttu-id="d749c-117">앱이 2D XAML 보기에서 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-117">The app starts up in the 2D XAML view.</span></span>
* <span data-ttu-id="d749c-118">앱의 XAML 시작 시퀀스는 현재 시스템 holographic 렌더링을 지원 하는지 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-118">The app’s XAML startup sequence detects if the current system supports holographic rendering:</span></span>
* <span data-ttu-id="d749c-119">그렇다면 앱 몰입 형 뷰를 만들고 바로 앞으로 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-119">If so, the app creates the immersive view and brings it to the foreground right away.</span></span> <span data-ttu-id="d749c-120">XAML 로드 필요 하지 않은 항목에 대 한 모든 렌더링 클래스 및 XAML 보기에서 로드 하는 자산을 포함 하 여 Windows Mixed Reality 장치에서 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-120">XAML loading is skipped for anything not necessary on Windows Mixed Reality devices, including any rendering classes and asset loading in the XAML view.</span></span> <span data-ttu-id="d749c-121">앱을 사용 하는 XAML 키보드 입력에 대 한 경우 해당 입력된 페이지도 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-121">If the app is using XAML for keyboard input, that input page should still be created.</span></span>
* <span data-ttu-id="d749c-122">그러지 않으면 XAML 뷰 비즈니스 평소 처럼 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-122">If not, the XAML view can proceed with business as usual.</span></span>

## <a name="tip-for-rendering-graphics-across-both-views"></a><span data-ttu-id="d749c-123">두 보기에서 그래픽 렌더링에 대 한 팁</span><span class="sxs-lookup"><span data-stu-id="d749c-123">Tip for rendering graphics across both views</span></span>

<span data-ttu-id="d749c-124">앱을 Windows Mixed Reality의 XAML 뷰에 대 한 DirectX에서 어느 정도의 렌더링을 구현 하는 경우 가장 좋은 두 보기를 사용 하 여 사용할 수 있는 하나의 렌더러를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-124">If your app needs to implement some amount of rendering in DirectX for the XAML view in Windows Mixed Reality, your best bet is to create one renderer that can work with both views.</span></span> <span data-ttu-id="d749c-125">렌더러 뷰 모두에서 액세스할 수 있는 하나의 인스턴스가 있어야 합니다. 및 2D 및 holographic 렌더링 간을 전환할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d749c-125">The renderer should be one instance that can be accessed from both views, and it should be able to switch between 2D and holographic rendering.</span></span> <span data-ttu-id="d749c-126">로드 시간, 메모리 영향 및 보기를 전환할 때 교환할 리소스의 크기를 줄입니다 GPU 자산만 한 번만 로드 됩니다 이런 방식으로이.</span><span class="sxs-lookup"><span data-stu-id="d749c-126">That way GPU assets are only loaded once - this reduces load times, memory impact, and the amount of resources to be swapped when switching views.</span></span>
