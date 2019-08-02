---
title: Holographic 원격 호스트 앱 작성
description: 원격 컴퓨터에서 렌더링 되는 Holographic 원격 호스트 앱 원격 콘텐츠를 만들면 HoloLens 2로 스트리밍할 수 있습니다. 이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다.
author: bethau
ms.author: bethau
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: 95cf98504f26e2362b3c4fd38e7d9228350798f3
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718067"
---
# <a name="writing-a-holographic-remoting-host-app"></a><span data-ttu-id="4f5dd-105">Holographic 원격 호스트 앱 작성</span><span class="sxs-lookup"><span data-stu-id="4f5dd-105">Writing a Holographic Remoting host app</span></span>

>[!IMPORTANT]
><span data-ttu-id="4f5dd-106">이 문서에서는 HoloLens 2 용 호스트 응용 프로그램을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-106">This document describes the creation of a host application for HoloLens 2.</span></span> <span data-ttu-id="4f5dd-107">**HoloLens 1** 용 호스트 응용 프로그램은 NuGet **패키지 버전 1.x**를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-107">Host application for **HoloLens 1** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="4f5dd-108">이는 HoloLens 2 용으로 작성 된 호스트 응용 프로그램이 HoloLens 1과 호환 되지 않거나 그 반대의 경우를 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-108">This implies that host applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="4f5dd-109">HoloLens 1에 대 한 설명서는 [여기](add-holographic-remoting.md)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-109">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="4f5dd-110">원격 컴퓨터에서 렌더링 된 원격 Holographic 원격 호스트 앱을 만들면 HoloLens 2로 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-110">By creating a Holographic Remoting host app remote content that is rendered on a remote machine can be streamed to HoloLens 2.</span></span> <span data-ttu-id="4f5dd-111">이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-111">This article describes how this can be achieved.</span></span> <span data-ttu-id="4f5dd-112">이 페이지 및 작업 프로젝트의 모든 코드는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-112">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="4f5dd-113">Holographic remoting을 사용 하면 앱이 데스크톱 PC 또는 UWP 장치 (예: Xbox One)에서 호스트 되는 Holographic 콘텐츠를 사용 하 여 HoloLens 2를 대상으로 지정할 수 있으며, 더 많은 시스템 리소스에 액세스 하 고 원격 [몰입 형 보기](app-views.md) 를 기존에 통합할 수 있습니다. 데스크톱 PC 소프트웨어.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-113">Holographic remoting allows an app to target HoloLens 2 with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="4f5dd-114">원격 호스트 앱은 HoloLens 2에서 입력 데이터 스트림을 받고, 가상 몰입 형 보기에서 콘텐츠를 렌더링 하 고, 콘텐츠 프레임을 HoloLens 2로 다시 스트리밍합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-114">A remoting host app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="4f5dd-115">연결은 표준 Wi-fi를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-115">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="4f5dd-116">Holographic Remoting은 NuGet 패킷을 통해 데스크톱 또는 UWP 앱에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-116">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="4f5dd-117">연결을 처리 하 고 몰입 형 보기에서 렌더링 하는 추가 코드가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-117">Additional code is required which handles the connection and renders in an immersive view.</span></span>

<span data-ttu-id="4f5dd-118">일반적인 원격 연결의 경우 대기 시간은 50 밀리초로 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-118">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="4f5dd-119">플레이어 앱은 실시간으로 대기 시간을 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-119">The player app can report the latency in real-time.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4f5dd-120">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="4f5dd-120">Prerequisites</span></span>

<span data-ttu-id="4f5dd-121">좋은 출발점은 Windows Mixed Reality API를 대상으로 하는 작동 하는 DirectX 기반 데스크톱 또는 UWP 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-121">A good starting point is a working DirectX based Desktop or UWP app which targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="4f5dd-122">자세한 내용은 [DirectX 개발 개요](directx-development-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-122">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="4f5dd-123">Holographic 프로젝트 템플릿이 좋은 출발점입니다. [ C++ ](creating-a-holographic-directx-project.md)</span><span class="sxs-lookup"><span data-stu-id="4f5dd-123">The [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="4f5dd-124">Holographic 원격을 사용 하는 모든 앱은 [다중 스레드 아파트](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)를 사용 하도록 작성 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-124">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="4f5dd-125">[단일 스레드 아파트](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) 를 사용 하는 것은 지원 되지만, 재생 하는 동안 일지 성능이 저하 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-125">The use of a [single-threaded apartment](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="4f5dd-126">/Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) 를 사용 하는 경우 다중 스레드 아파트는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-126">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="4f5dd-127">Holographic 원격 NuGet 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="4f5dd-127">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="4f5dd-128">Visual Studio에서 프로젝트에 NuGet 패키지를 추가 하려면 다음 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-128">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="4f5dd-129">Visual Studio에서 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-129">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="4f5dd-130">프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리 ...** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-130">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="4f5dd-131">표시 되는 패널에서 **찾아보기** 를 클릭 한 다음 "Holographic Remoting"을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-131">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="4f5dd-132">**Holographic**를 선택 하 고 최신 **2.x 버전을** 선택 하 고 **설치**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-132">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="4f5dd-133">**미리 보기** 대화 상자가 표시 되 면 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-133">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="4f5dd-134">표시 되는 다음 대화 상자는 사용권 계약입니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-134">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="4f5dd-135">**동의** 함을 클릭 하 여 사용권 계약에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-135">Click on **I Accept** to accept the license agreement.</span></span>

>[!NOTE]
><span data-ttu-id="4f5dd-136">HoloLens 1을 대상으로 하는 개발자에 게는 NuGet 패키지의 버전 **1. x. x** 를 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-136">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="4f5dd-137">자세한 내용은 [Holographic 원격 추가 (HoloLens 1)](add-holographic-remoting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-137">For details see [Add Holographic Remoting (HoloLens 1)](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="4f5dd-138">원격 컨텍스트 만들기</span><span class="sxs-lookup"><span data-stu-id="4f5dd-138">Create the remote context</span></span>

<span data-ttu-id="4f5dd-139">첫 번째 단계로 응용 프로그램은 원격 컨텍스트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-139">As a first step the application should create a remote context.</span></span>

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
><span data-ttu-id="4f5dd-140">Holographic Remoting은 원격 특정 런타임을 사용 하 여 Windows의 일부인 Windows Mixed Reality 런타임을 대체 하는 방식으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="4f5dd-141">이 작업은 원격 컨텍스트를 만드는 동안 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-141">This is done during the creation of the remote context.</span></span> <span data-ttu-id="4f5dd-142">이러한 이유로 원격 컨텍스트를 만들기 전에 Windows Mixed Reality API를 호출 하면 예기치 않은 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-142">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="4f5dd-143">혼합 현실 API와의 상호 작용 전에 가능한 한 빨리 원격 컨텍스트를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-143">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="4f5dd-144">이후에 만들어지거나 검색 된 개체를 사용 하 여 CreateRemoteContext를 호출 하기 전에 Windows Mixed Reality API를 통해 만들어지거나 검색 된 개체를 혼합 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="4f5dd-145">다음으로 holographic 공간을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-145">Next the holographic space needs to be created.</span></span> <span data-ttu-id="4f5dd-146">CoreWindow 지정은 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-146">Specifying a CoreWindow is not required.</span></span> <span data-ttu-id="4f5dd-147">CoreWindow 없는 데스크톱 앱은 ```nullptr```만 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-147">Desktop apps that do not have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="4f5dd-148">장치에 연결</span><span class="sxs-lookup"><span data-stu-id="4f5dd-148">Connect to the device</span></span>

<span data-ttu-id="4f5dd-149">호스트 앱이 콘텐츠를 렌더링할 준비가 되 면 장치에 대 한 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-149">Once the host app is ready for rendering content a connection to the device can be established.</span></span>

<span data-ttu-id="4f5dd-150">다음 두 가지 방법 중 하나로 연결을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-150">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="4f5dd-151">호스트 앱은 장치에서 실행 중인 플레이어에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-151">The host app connects to the player running on the device.</span></span>
2) <span data-ttu-id="4f5dd-152">장치에서 실행 중인 플레이어는 호스트 앱에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-152">The player running on the device connects to the host app.</span></span>

<span data-ttu-id="4f5dd-153">호스트 앱에서 HoloLens 2로의 연결을 설정 하려면 호스트 이름 ```Connect``` 및 포트를 지정 하는 원격 컨텍스트에서 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-153">To establish a connection from the host app to HoloLens 2 call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="4f5dd-154">Holographic Remoting 플레이어에서 사용 하는 포트는 **8265**입니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-154">The port used by the Holographic Remoting Player is **8265**.</span></span>

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
><span data-ttu-id="4f5dd-155">Any C++/winrt API ```Connect``` 와 마찬가지로 처리 해야 하는 winrt:: hresult_error을 throw 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-155">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="4f5dd-156">[ C++/Winrt](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/) 언어 프로젝션을 사용 하지 않으려면 Holographic Remoting ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` NuGet 패키지 내에 있는 파일을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-156">To avoid using [C++/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="4f5dd-157">여기에는 기본 COM 인터페이스의 선언이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-157">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="4f5dd-158">그러나 C++/winrt를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-158">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="4f5dd-159">호스트 앱에서 들어오는 연결을 수신 하는 작업은 메서드를 ```Listen``` 호출 하 여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-159">Listening for incoming connections on the host app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="4f5dd-160">이 호출 중에 핸드셰이크 포트와 전송 포트를 모두 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-160">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="4f5dd-161">핸드셰이크 포트는 초기 핸드셰이크에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-161">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="4f5dd-162">그런 다음 데이터는 전송 포트를 통해 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-162">The data is then send over the transport port.</span></span> <span data-ttu-id="4f5dd-163">기본적으로 **8265** 및 **8266** 이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-163">By default **8265** and **8266** are used.</span></span>

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
><span data-ttu-id="4f5dd-164">NuGet ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 패키지 내에는 Holographic Remoting에서 노출 하는 API에 대 한 자세한 설명서가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-164">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="4f5dd-165">원격 특정 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="4f5dd-165">Handling Remoting specific events</span></span>

<span data-ttu-id="4f5dd-166">원격 컨텍스트는 연결 상태를 모니터링 하는 데 중요 한 세 개의 이벤트를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-166">The remote context exposes three events which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="4f5dd-167">OnConnected: 장치에 대 한 연결이 성공적으로 설정 되 면 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-167">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="4f5dd-168">OnDisconnected: 설정 된 연결이 닫히거나 연결을 설정할 수 없는 경우에 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-168">OnDisconnected: Triggered if an established connection is closed or a connection could not be established.</span></span>
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
3) <span data-ttu-id="4f5dd-169">OnListening: 들어오는 연결에 대 한 수신 대기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-169">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="4f5dd-170">또한 원격 컨텍스트의 속성을 ```ConnectionState``` 사용 하 여 연결 상태를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-170">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="4f5dd-171">음성 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="4f5dd-171">Handling speech events</span></span>

<span data-ttu-id="4f5dd-172">원격 음성 인터페이스를 사용 하 여 HoloLens 2에 음성 트리거를 등록 하 고 호스트 응용 프로그램에 원격으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-172">Using the remote speech interface it is possible to register speech triggers with HoloLens 2 and have them remoted to the host application.</span></span>

<span data-ttu-id="4f5dd-173">이 추가 멤버는 원격 음성의 상태를 추적 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-173">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="4f5dd-174">먼저 원격 음성 인터페이스를 검색 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-174">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="4f5dd-175">비동기 도우미 메서드를 사용 하 여 원격 음성을 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-175">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="4f5dd-176">초기화는 상당한 시간이 걸릴 수 있으므로이 작업은 비동기적으로 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-176">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="4f5dd-177">[/WinRT를 사용한 C++동시성 및 비동기 작업](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) 은/winrt. 사용 하 여 C++비동기 함수를 작성 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-177">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

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
    std::weak_ptr<SampleHostMain> sampleHostMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleHostMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleHostMain = sampleHostMainWeak.lock())
            {
                sampleHostMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"en-US", grammarFile, dictionary);
}
```

<span data-ttu-id="4f5dd-178">인식 될 구를 지정 하는 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-178">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="4f5dd-179">음성 문법 xml 파일 내의 사양입니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-179">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="4f5dd-180">자세한 내용은 [기본 XML 문법을 만드는 방법](https://docs.microsoft.com/en-us/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-180">See [How to create a basic XML Grammar](https://docs.microsoft.com/en-us/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="4f5dd-181">를 사전 벡터 내부에 ```ApplyParameters```전달 하 여 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-181">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="4f5dd-182">OnRecognizedSpeech 콜백 내에서 음성 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-182">Inside the OnRecognizedSpeech callback the speech events can then be processed:</span></span>

```cpp
void SampleHostMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
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

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="4f5dd-183">스트리밍 콘텐츠를 로컬로 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-183">Preview streamed content locally</span></span>

<span data-ttu-id="4f5dd-184">장치에 전송 되는 호스트 앱에 동일한 콘텐츠를 표시 하려면 원격 컨텍스트의 이벤트 ```OnSendFrame``` 를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-184">To display the same content in the host app that is send to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="4f5dd-185">이 ```OnSendFrame``` 이벤트는 Holographic 원격 라이브러리가 현재 프레임을 원격 장치로 보낼 때마다 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-185">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="4f5dd-186">이는 콘텐츠를 사용 하 여 데스크톱 또는 UWP 창으로 array.blit 하는 데 가장 적합 한 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-186">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

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

## <a name="optional-custom-data-channels"></a><span data-ttu-id="4f5dd-187">선택 사항: 사용자 지정 데이터 채널</span><span class="sxs-lookup"><span data-stu-id="4f5dd-187">Optional: Custom data channels</span></span>

<span data-ttu-id="4f5dd-188">사용자 지정 데이터 채널은 이미 설정 된 원격 연결을 통해 사용자 데이터를 전송 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-188">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="4f5dd-189">자세한 내용은 [사용자 지정 데이터 채널](holographic-remoting-custom-data-channels.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4f5dd-189">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f5dd-190">관련 항목</span><span class="sxs-lookup"><span data-stu-id="4f5dd-190">See Also</span></span>
* [<span data-ttu-id="4f5dd-191">사용자 지정 Holographic Remoting 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="4f5dd-191">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="4f5dd-192">사용자 지정 Holographic 원격 데이터 채널</span><span class="sxs-lookup"><span data-stu-id="4f5dd-192">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="4f5dd-193">Holographic 원격을 사용 하 여 보안 연결 설정</span><span class="sxs-lookup"><span data-stu-id="4f5dd-193">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="4f5dd-194">Holographic 원격 문제 해결 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="4f5dd-194">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="4f5dd-195">Holographic 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="4f5dd-195">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="4f5dd-196">Microsoft 개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="4f5dd-196">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)