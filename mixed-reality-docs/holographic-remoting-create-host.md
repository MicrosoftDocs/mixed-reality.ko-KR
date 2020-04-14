---
title: Holographic Remoting 원격 앱 작성
description: 원격 컴퓨터에서 렌더링 되는 Holographic Remoting 원격 앱 원격 콘텐츠를 만들면 HoloLens 2로 스트리밍할 수 있습니다. 이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: 6c6da16d83f593d9987bf7e534f9f663f11abd01
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278121"
---
# <a name="writing-a-holographic-remoting-remote-app"></a><span data-ttu-id="5ebc2-105">Holographic Remoting 원격 앱 작성</span><span class="sxs-lookup"><span data-stu-id="5ebc2-105">Writing a Holographic Remoting remote app</span></span>

>[!IMPORTANT]
><span data-ttu-id="5ebc2-106">이 문서에서는 HoloLens 2 용 원격 응용 프로그램을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-106">This document describes the creation of a remote application for HoloLens 2.</span></span> <span data-ttu-id="5ebc2-107">HoloLens 용 원격 응용 프로그램 **(첫 번째 gen)** 은 NuGet 패키지 **버전 1.x를 사용**해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-107">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="5ebc2-108">즉, HoloLens 2 용으로 작성 된 원격 응용 프로그램은 HoloLens 1과 호환 되지 않으며 그 반대의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-108">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="5ebc2-109">HoloLens 1에 대 한 설명서는 [여기](add-holographic-remoting.md)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="5ebc2-110">Holographic Remoting 원격 앱을 만들면 원격 컴퓨터에서 렌더링 되는 원격 콘텐츠를 HoloLens 2로 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-110">By creating a Holographic Remoting remote app, remote content that is rendered on a remote machine can be streamed to HoloLens 2.</span></span> <span data-ttu-id="5ebc2-111">이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="5ebc2-112">이 페이지 및 작업 프로젝트의 모든 코드는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="5ebc2-113">Holographic remoting을 사용 하면 앱이 데스크톱 PC 또는 UWP 장치 (예: Xbox One)에서 렌더링 된 Holographic 콘텐츠를 사용 하 여 HoloLens 2를 대상으로 지정할 수 있으며, 더 많은 시스템 리소스에 대 한 액세스를 허용 하 고 원격 [몰입 형 보기](app-views.md) 를 기존 데스크톱 PC 소프트웨어에 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-113">Holographic remoting allows an app to target HoloLens 2 with holographic content rendered on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="5ebc2-114">원격 앱은 HoloLens 2에서 입력 데이터 스트림을 받고, 가상 몰입 형 보기에서 콘텐츠를 렌더링 하 고, 콘텐츠 프레임을 HoloLens 2로 다시 스트리밍합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-114">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="5ebc2-115">연결은 표준 Wi-fi를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="5ebc2-116">Holographic Remoting은 NuGet 패킷을 통해 데스크톱 또는 UWP 앱에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="5ebc2-117">연결을 처리 하 고 몰입 형 보기에서 렌더링 하는 추가 코드가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="5ebc2-118">일반적인 원격 연결의 경우 대기 시간은 50 밀리초로 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="5ebc2-119">플레이어 앱은 실시간으로 대기 시간을 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5ebc2-120">필수 조건</span><span class="sxs-lookup"><span data-stu-id="5ebc2-120">Prerequisites</span></span>

<span data-ttu-id="5ebc2-121">좋은 출발점은 Windows Mixed Reality API를 대상으로 하는 작동 하는 DirectX 기반 데스크톱 또는 UWP 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-121">A good starting point is a working DirectX based Desktop or UWP app which targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="5ebc2-122">자세한 내용은 [DirectX 개발 개요](directx-development-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-122">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="5ebc2-123">Holographic 프로젝트 템플릿이 좋은 출발점입니다. [ C++ ](creating-a-holographic-directx-project.md)</span><span class="sxs-lookup"><span data-stu-id="5ebc2-123">The [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="5ebc2-124">Holographic 원격을 사용 하는 모든 앱은 [다중 스레드 아파트](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)를 사용 하도록 작성 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-124">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="5ebc2-125">[단일 스레드 아파트](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) 를 사용 하는 것은 지원 되지만, 재생 하는 동안 일지 성능이 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-125">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="5ebc2-126">/Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) 사용 하는 경우 다중 스레드 아파트는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-126">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="5ebc2-127">Holographic 원격 NuGet 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="5ebc2-127">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="5ebc2-128">Visual Studio에서 프로젝트에 NuGet 패키지를 추가 하려면 다음 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-128">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="5ebc2-129">Visual Studio에서 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-129">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="5ebc2-130">프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리 ...** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-130">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="5ebc2-131">표시 되는 패널에서 **찾아보기** 를 클릭 한 다음 "Holographic Remoting"을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-131">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="5ebc2-132">**Holographic**를 선택 하 고 최신 **2.x 버전을** 선택 하 고 **설치**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-132">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="5ebc2-133">**미리 보기** 대화 상자가 표시 되 면 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-133">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="5ebc2-134">표시 되는 다음 대화 상자는 사용권 계약입니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-134">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="5ebc2-135">**동의** 함을 클릭 하 여 사용권 계약에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-135">Click on **I Accept** to accept the license agreement.</span></span>

>[!NOTE]
><span data-ttu-id="5ebc2-136">HoloLens 1을 대상으로 하는 개발자에 게는 NuGet 패키지의 버전 **1. x. x** 를 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="5ebc2-137">자세한 내용은 [Holographic 원격 추가 (HoloLens (첫 번째 gen))](add-holographic-remoting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-137">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="5ebc2-138">원격 컨텍스트 만들기</span><span class="sxs-lookup"><span data-stu-id="5ebc2-138">Create the remote context</span></span>

<span data-ttu-id="5ebc2-139">첫 번째 단계로 응용 프로그램은 원격 컨텍스트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-139">As a first step the application should create a remote context.</span></span>

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
><span data-ttu-id="5ebc2-140">Holographic Remoting은 원격 특정 런타임을 사용 하 여 Windows의 일부인 Windows Mixed Reality 런타임을 대체 하는 방식으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="5ebc2-141">이 작업은 원격 컨텍스트를 만드는 동안 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-141">This is done during the creation of the remote context.</span></span> <span data-ttu-id="5ebc2-142">이러한 이유로 원격 컨텍스트를 만들기 전에 Windows Mixed Reality API를 호출 하면 예기치 않은 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-142">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="5ebc2-143">혼합 현실 API와의 상호 작용 전에 가능한 한 빨리 원격 컨텍스트를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-143">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="5ebc2-144">이후에 만들어지거나 검색 된 개체를 사용 하 여 CreateRemoteContext를 호출 하기 전에 Windows Mixed Reality API를 통해 만들어지거나 검색 된 개체를 혼합 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="5ebc2-145">다음으로 holographic 공간을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-145">Next the holographic space needs to be created.</span></span> <span data-ttu-id="5ebc2-146">CoreWindow 지정은 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-146">Specifying a CoreWindow is not required.</span></span> <span data-ttu-id="5ebc2-147">CoreWindow 없는 데스크톱 앱은 단순히 ```nullptr```전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-147">Desktop apps that do not have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="5ebc2-148">장치에 연결</span><span class="sxs-lookup"><span data-stu-id="5ebc2-148">Connect to the device</span></span>

<span data-ttu-id="5ebc2-149">원격 앱이 콘텐츠를 렌더링할 준비가 되 면 장치에 대 한 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-149">Once the remote app is ready for rendering content a connection to the device can be established.</span></span>

<span data-ttu-id="5ebc2-150">다음 두 가지 방법 중 하나로 연결을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-150">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="5ebc2-151">원격 앱은 장치에서 실행 중인 플레이어에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-151">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="5ebc2-152">장치에서 실행 되는 플레이어가 원격 앱에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-152">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="5ebc2-153">원격 앱에서 HoloLens 2로의 연결을 설정 하려면 호스트 이름 및 포트를 지정 하는 원격 컨텍스트에서 ```Connect``` 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-153">To establish a connection from the remote app to HoloLens 2 call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="5ebc2-154">Holographic Remoting 플레이어에서 사용 하는 포트는 **8265**입니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-154">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="5ebc2-155">모든 C++/WINRT API ```Connect```는 처리 해야 하는 WinRT:: hresult_error을 throw 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-155">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="5ebc2-156">[ C++/Winrt](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) 언어 프로젝션을 사용 하지 않으려면 Holographic Remoting NuGet 패키지 내에 있는 파일 ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-156">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="5ebc2-157">여기에는 기본 COM 인터페이스의 선언이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-157">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="5ebc2-158">그러나 C++/winrt를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-158">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="5ebc2-159">원격 앱에서 들어오는 연결을 수신 하는 작업은 ```Listen``` 메서드를 호출 하 여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-159">Listening for incoming connections on the remote app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="5ebc2-160">이 호출 중에 핸드셰이크 포트와 전송 포트를 모두 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-160">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="5ebc2-161">핸드셰이크 포트는 초기 핸드셰이크에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-161">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="5ebc2-162">그런 다음 데이터는 전송 포트를 통해 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-162">The data is then send over the transport port.</span></span> <span data-ttu-id="5ebc2-163">기본적으로 **8265** 및 **8266** 이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-163">By default **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="5ebc2-164">NuGet 패키지 내의 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` Holographic Remoting에서 노출 하는 API에 대 한 자세한 설명서를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-164">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="5ebc2-165">원격 특정 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="5ebc2-165">Handling Remoting specific events</span></span>

<span data-ttu-id="5ebc2-166">원격 컨텍스트는 연결 상태를 모니터링 하는 데 중요 한 세 개의 이벤트를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-166">The remote context exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="5ebc2-167">OnConnected: 장치에 대 한 연결이 성공적으로 설정 되 면 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-167">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="5ebc2-168">OnDisconnected: 설정 된 연결이 닫히거나 연결을 설정할 수 없는 경우 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-168">OnDisconnected: Triggered if an established connection is closed or a connection could not be established.</span></span>
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) <span data-ttu-id="5ebc2-169">OnListening: 들어오는 연결에 대 한 수신 대기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-169">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="5ebc2-170">또한 원격 컨텍스트의 ```ConnectionState``` 속성을 사용 하 여 연결 상태를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-170">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="5ebc2-171">음성 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="5ebc2-171">Handling speech events</span></span>

<span data-ttu-id="5ebc2-172">원격 음성 인터페이스를 사용 하 여 HoloLens 2에 음성 트리거를 등록 하 고 원격 응용 프로그램에 원격으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-172">Using the remote speech interface it is possible to register speech triggers with HoloLens 2 and have them remoted to the remote application.</span></span>

<span data-ttu-id="5ebc2-173">이 추가 멤버는 원격 음성의 상태를 추적 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-173">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="5ebc2-174">먼저 원격 음성 인터페이스를 검색 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-174">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="5ebc2-175">비동기 도우미 메서드를 사용 하 여 원격 음성을 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-175">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="5ebc2-176">초기화는 상당한 시간이 걸릴 수 있으므로이 작업은 비동기적으로 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-176">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="5ebc2-177">[/WinRT를 사용한 C++동시성 및 비동기 작업](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) 은/winrt. 사용 하 여 C++비동기 함수를 작성 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-177">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

<span data-ttu-id="5ebc2-178">인식 될 구를 지정 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-178">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="5ebc2-179">음성 문법 xml 파일 내의 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-179">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="5ebc2-180">자세한 내용은 [기본 XML 문법을 만드는 방법](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-180">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="5ebc2-181">```ApplyParameters```하려면 사전 벡터 내부에 전달 하 여를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-181">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="5ebc2-182">OnRecognizedSpeech 콜백 내에서 음성 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-182">Inside the OnRecognizedSpeech callback the speech events can then be processed:</span></span>

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="5ebc2-183">스트리밍 콘텐츠를 로컬로 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-183">Preview streamed content locally</span></span>

<span data-ttu-id="5ebc2-184">장치에 전송 되는 원격 앱에 동일한 콘텐츠를 표시 하려면 원격 컨텍스트의 ```OnSendFrame``` 이벤트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-184">To display the same content in the remote app that is send to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="5ebc2-185">Holographic 원격 라이브러리가 현재 프레임을 원격 장치로 보낼 때마다 ```OnSendFrame``` 이벤트가 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-185">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="5ebc2-186">이는 콘텐츠를 사용 하 여 데스크톱 또는 UWP 창으로 array.blit 하는 데 가장 적합 한 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-186">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a><span data-ttu-id="5ebc2-187">깊이 예측</span><span class="sxs-lookup"><span data-stu-id="5ebc2-187">Depth Reprojection</span></span>

<span data-ttu-id="5ebc2-188">[2.1.0](holographic-remoting-version-history.md#v2.1.0)버전부터 Holographic Remoting은 [깊이 재 프로젝션을](hologram-stability.md#reprojection)지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-188">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting supports [Depth Reprojection](hologram-stability.md#reprojection).</span></span> <span data-ttu-id="5ebc2-189">이를 위해서는 색 버퍼 외에도 원격 응용 프로그램에서 HoloLens 2로 깊이 버퍼를 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-189">This requires, in addition to the color buffer, to also stream the depth buffer from the Remote application to the HoloLens 2.</span></span> <span data-ttu-id="5ebc2-190">기본적으로 깊이 버퍼는 색 버퍼의 해상도 절반으로 스트리밍됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-190">By default the depth buffer is streamed at half the resolution of the color buffer.</span></span> <span data-ttu-id="5ebc2-191">다음과 같이 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-191">This can be changed as follows:</span></span>

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

<span data-ttu-id="5ebc2-192">HoloLens 2에 대 한 연결을 설정 하기 전에 ```ConfigureDepthVideoStream```를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-192">Note, ```ConfigureDepthVideoStream``` must be called before establishing a connection to the HoloLens 2.</span></span> <span data-ttu-id="5ebc2-193">가장 좋은 장소는 원격 컨텍스트를 만든 직후입니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-193">The best place is right after you have created the remote context.</span></span> <span data-ttu-id="5ebc2-194">가능한 값은 전체, 절반 및 사분기 해상도입니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-194">Possible values are full, half, and quater resolution.</span></span> <span data-ttu-id="5ebc2-195">기본값은 반 해상도입니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-195">Default is half resolution.</span></span> <span data-ttu-id="5ebc2-196">전체 해상도 깊이 버퍼를 사용 하면 대역폭 요구 사항에도 영향을 미치므로 ```CreateRemoteContext```하는 데 제공 하는 최대 대역폭 값에서을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-196">Keep in mind that using a full resolution depth buffer also affects bandwidth requirements and needs to be accounted for in the maximum bandwidth value you provide to ```CreateRemoteContext```.</span></span>

<span data-ttu-id="5ebc2-197">해상도를 구성 하는 것 외에도 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)를 통해 깊이 버퍼를 커밋해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-197">Beside configuring the resolution you also have to commit a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

<span data-ttu-id="5ebc2-198">되도록에서 깊이 다시 프로젝션이 작동 하는지 확인 하려면 장치 포털을 통해 깊이 시각화 도우미를 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-198">To verify if depth reprojection is correclty working on HoloLens 2 you can enable a depth visualizer via the Device Portal.</span></span> <span data-ttu-id="5ebc2-199">자세한 내용은 [깊이가 올바르게 설정 되었는지 확인](hologram-stability.md#verifying-depth-is-set-correctly) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-199">See [Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) for details.</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="5ebc2-200">선택 사항: 사용자 지정 데이터 채널</span><span class="sxs-lookup"><span data-stu-id="5ebc2-200">Optional: Custom data channels</span></span>

<span data-ttu-id="5ebc2-201">사용자 지정 데이터 채널은 이미 설정 된 원격 연결을 통해 사용자 데이터를 전송 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-201">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="5ebc2-202">자세한 내용은 [사용자 지정 데이터 채널](holographic-remoting-custom-data-channels.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5ebc2-202">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ebc2-203">관련 항목</span><span class="sxs-lookup"><span data-stu-id="5ebc2-203">See Also</span></span>
* [<span data-ttu-id="5ebc2-204">사용자 지정 Holographic Remoting 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="5ebc2-204">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="5ebc2-205">사용자 지정 홀로그램 원격 데이터 채널</span><span class="sxs-lookup"><span data-stu-id="5ebc2-205">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="5ebc2-206">Holographic 원격을 사용 하 여 보안 연결 설정</span><span class="sxs-lookup"><span data-stu-id="5ebc2-206">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="5ebc2-207">Holographic 원격 문제 해결 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="5ebc2-207">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="5ebc2-208">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="5ebc2-208">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="5ebc2-209">Microsoft 개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="5ebc2-209">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
