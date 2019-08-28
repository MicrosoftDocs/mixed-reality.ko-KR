---
title: 사용자 지정 Holographic Remoting 플레이어 작성
description: 사용자 지정 Holographic 원격 플레이어 앱을 만들면 원격 컴퓨터에 렌더링 된 콘텐츠를 HoloLens 2로 표시할 수 있는 사용자 지정 응용 프로그램을 만들 수 있습니다. 이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: fdc3d3bbd72d0812377d6a70c975f2111e1a2224
ms.sourcegitcommit: ca949efe0279995a376750d89e23d7123eb44846
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68718097"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="f708a-105">사용자 지정 Holographic Remoting 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="f708a-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="f708a-106">이 문서에서는 HoloLens 2에 대 한 사용자 지정 플레이어 응용 프로그램을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="f708a-107">HoloLens 2 용으로 작성 된 사용자 지정 플레이어는 HoloLens 1 용으로 작성 된 호스트 응용 프로그램과 호환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-107">Custom players written for HoloLens 2 are not compatible with host applications written for HoloLens 1.</span></span> <span data-ttu-id="f708a-108">이는 두 응용 프로그램이 모두 NuGet **패키지 버전 2.x**를 사용 해야 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="f708a-109">사용자 지정 Holographic 원격 플레이어 앱을 만들면 HoloLens 2의 원격 컴퓨터에서 [몰입 형 보기](app-views.md) 를 표시할 수 있는 사용자 지정 응용 프로그램을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="f708a-110">이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="f708a-111">이 페이지 및 작업 프로젝트의 모든 코드는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="f708a-112">Holographic 원격 플레이어를 사용 하면 앱에서 데스크톱 PC 또는 UWP 장치 (예: Xbox One)에서 [렌더링](rendering.md) 된 Holographic 콘텐츠를 표시 하 여 더 많은 시스템 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="f708a-113">Holographic Remoting player 앱은 입력 데이터를 Holographic Remoting 호스트 응용 프로그램으로 스트리밍하 고 비디오 및 오디오 스트림으로 몰입 형 보기를 다시 받습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-113">A Holographic Remoting player app streams input data to a Holographic Remoting host application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="f708a-114">연결은 표준 Wi-fi를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="f708a-115">플레이어 앱을 만들려면 NuGet 패키지를 사용 하 여 UWP 앱에 Holographic 원격을 추가 하 고, 연결을 처리 하 고 몰입 형 뷰를 표시 하는 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="f708a-116">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="f708a-116">Prerequisites</span></span>

<span data-ttu-id="f708a-117">좋은 출발점은 이미 Windows Mixed Reality API를 대상으로 하는 작동 하는 DirectX 기반 UWP 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="f708a-118">자세한 내용은 [DirectX 개발 개요](directx-development-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f708a-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="f708a-119">기존 앱이 없고 처음부터 시작 하려면 [ C++ holographic 프로젝트 템플릿이](creating-a-holographic-directx-project.md) 좋은 출발점입니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="f708a-120">Holographic 원격을 사용 하는 모든 앱은 [다중 스레드 아파트](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)를 사용 하도록 작성 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="f708a-121">[단일 스레드 아파트](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) 사용 하는 것은 지원 되지만, 재생 하는 동안 일지 성능이 저하 되 고 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-121">The use of a [single-threaded appartment](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="f708a-122">/Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) 를 사용 하는 경우 다중 스레드 아파트는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="f708a-123">Holographic 원격 NuGet 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="f708a-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="f708a-124">Visual Studio에서 프로젝트에 NuGet 패키지를 추가 하려면 다음 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="f708a-125">Visual Studio에서 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="f708a-126">프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리 ...** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="f708a-127">표시 되는 패널에서 **찾아보기** 를 클릭 한 다음 "Holographic Remoting"을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="f708a-128">**Holographic**를 선택 하 고 최신 **2.x 버전을** 선택 하 고 **설치**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="f708a-129">**미리 보기** 대화 상자가 표시 되 면 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="f708a-130">표시 되는 다음 대화 상자는 사용권 계약입니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="f708a-131">**동의** 함을 클릭 하 여 사용권 계약에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="f708a-132">NuGet ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 패키지 내에는 Holographic Remoting에서 노출 하는 API에 대 한 자세한 설명서가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="f708a-133">응용 프로그램의 appxmanifest.xml을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="f708a-134">응용 프로그램이 NuGet 패키지에 의해 추가 된 Holographic를 인식 하도록 하려면 프로젝트에서 다음 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="f708a-135">솔루션 탐색기에서 **appxmanifest.xml** 파일을 마우스 오른쪽 단추로 클릭 하 고 **연결 프로그램 ...을** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="f708a-136">**XML (텍스트) 편집기** 를 선택 하 고 확인을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="f708a-137">파일에 다음 줄을 추가 하 고 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-137">Add the following lines to the file and save</span></span>
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a><span data-ttu-id="f708a-138">플레이어 컨텍스트 만들기</span><span class="sxs-lookup"><span data-stu-id="f708a-138">Create the player context</span></span>

<span data-ttu-id="f708a-139">첫 번째 단계로 응용 프로그램은 플레이어 컨텍스트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-139">As a first step the application should create a player context.</span></span>

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting host and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
><span data-ttu-id="f708a-140">Holographic Remoting은 원격 특정 런타임을 사용 하 여 Windows의 일부인 Windows Mixed Reality 런타임을 대체 하는 방식으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="f708a-141">플레이어 컨텍스트를 만드는 동안이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="f708a-142">이러한 이유로 플레이어 컨텍스트를 만들기 전에 Windows Mixed Reality API를 호출 하면 예기치 않은 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="f708a-143">권장 되는 방법은 혼합 현실 API와의 상호 작용 전에 가능한 한 빨리 플레이어 컨텍스트를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="f708a-144">이후에 만들어지거나 검색 된 개체를 사용 하 여를 호출 하기 전에 Windows Mixed Reality ```PlayerContext::Create()``` API를 통해 만들어지거나 검색 된 개체를 혼합 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="f708a-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create()``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="f708a-145">그런 다음 [HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)를 호출 하 여 HolographicSpace를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a><span data-ttu-id="f708a-146">호스트에 연결</span><span class="sxs-lookup"><span data-stu-id="f708a-146">Connect to the host</span></span>

<span data-ttu-id="f708a-147">플레이어 앱이 콘텐츠를 렌더링할 준비가 되 면 호스트에 대 한 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-147">Once the player app is ready for rendering content a connection to the host can be established.</span></span>

<span data-ttu-id="f708a-148">시나리오별 방법 중 하나로 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-148">The connection can be established in one of the follwing ways:</span></span>
1) <span data-ttu-id="f708a-149">HoloLens 2에서 실행 되는 플레이어 앱은 호스트 앱에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-149">The player app running on HoloLens 2 connects to the host app.</span></span>
2) <span data-ttu-id="f708a-150">호스트 앱은 HoloLens 2에서 실행 중인 플레이어 앱에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-150">The host app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="f708a-151">플레이어 앱에서 호스트로 연결 하려면 호스트 이름 및 포트를 ```Connect``` 지정 하는 플레이어 컨텍스트의 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-151">To connect from the player app to the host call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="f708a-152">기본 포트는 **8265**입니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-152">The default port is **8265**.</span></span>

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
><span data-ttu-id="f708a-153">Any C++/winrt API ```Connect``` 와 마찬가지로 처리 해야 하는 winrt:: hresult_error을 throw 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="f708a-154">플레이어 앱에서 들어오는 연결을 수신 하는 작업은 메서드를 ```Listen``` 호출 하 여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="f708a-155">이 호출 중에 핸드셰이크 포트와 전송 포트를 모두 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="f708a-156">핸드셰이크 포트는 초기 핸드셰이크에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="f708a-157">그런 다음 데이터는 전송 포트를 통해 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-157">The data is then send over the transport port.</span></span> <span data-ttu-id="f708a-158">기본적으로 포트 번호 **8265** 및 **8266** 이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-158">By default port number **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a><span data-ttu-id="f708a-159">연결 관련 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="f708a-159">Handling connection related events</span></span>

<span data-ttu-id="f708a-160">는 ```PlayerContext``` 연결 상태를 모니터링 하는 세 개의 이벤트를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="f708a-161">OnConnected: 호스트에 대 한 연결이 성공적으로 설정 되 면 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-161">OnConnected: Triggered when a connection to the host has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="f708a-162">OnDisconnected: 설정 된 연결이 종료 되거나 연결을 설정할 수 없는 경우에 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
><span data-ttu-id="f708a-163">가능한 ```ConnectionFailureReason``` 값은 ```Microsoft.Holographic.AppRemoting.idl``` [파일](#idl)에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="f708a-164">OnListening: 들어오는 연결에 대 한 수신 대기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="f708a-165">또한 플레이어 컨텍스트의 속성을 ```ConnectionState``` 사용 하 여 연결 상태를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="f708a-166">원격으로 렌더링 된 프레임을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="f708a-167">원격으로 렌더링 된 콘텐츠를 표시 하려면 ```PlayerContext::BlitRemoteFrame()``` [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)를 렌더링 하는 동안를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame()``` while rendering a [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="f708a-168">```BlitRemoteFrame()```현재 HolographicFrame에 대 한 백 버퍼가 렌더링 대상으로 바인딩되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-168">```BlitRemoteFrame()``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="f708a-169">백 버퍼는 [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) 속성을 통해 [HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) 에서 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="f708a-170">호출 되 면 ```BlitRemoteFrame()``` 호스트 응용 프로그램에서 수신 된 최신 프레임을 HolographicFrame의 백 버퍼에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-170">When called, ```BlitRemoteFrame()``` copies the latest received frame from the host application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="f708a-171">원격 응용 프로그램에서 원격 프레임을 렌더링 하는 동안 포커스 지점을 지정 하는 경우에도 포커스 지점 집합이 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="f708a-172">```PlayerContext::BlitRemoteFrame()```현재 프레임의 포커스 지점을 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-172">```PlayerContext::BlitRemoteFrame()``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="f708a-173">대체 (fallback) 포커스 지점을 지정 하려면 이전 ```PlayerContext::BlitRemoteFrame()```에 [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-173">To specifiy a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame()```.</span></span> 
>- <span data-ttu-id="f708a-174">원격 포커스 지점을 과도 하 게 쓰려면 [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame()```를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-174">To overrwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame()```.</span></span>

<span data-ttu-id="f708a-175">성공 하면를 ```BlitRemoteFrame()``` 반환 ```BlitResult::Success_Color```합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-175">On success, ```BlitRemoteFrame()``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="f708a-176">그렇지 않으면 실패 원인을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="f708a-177">```BlitResult::Failed_NoRemoteFrameAvailable```: 사용할 수 있는 원격 프레임이 없기 때문에 실패 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="f708a-178">```BlitResult::Failed_NoCamera```: 카메라가 없어 실패 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="f708a-179">선택 사항: 마지막 원격 프레임에 대 한 통계 가져오기</span><span class="sxs-lookup"><span data-stu-id="f708a-179">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="f708a-180">성능 또는 네트워크 문제를 진단 하려면 ```PlayerContext::LastFrameStatistics``` 속성을 통해 마지막 원격 프레임에 대 한 통계를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-180">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="f708a-181">[HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)를 호출 하는 동안 통계가 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-181">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="f708a-182">자세한 내용은```Microsoft.Holographic.AppRemoting.idl``` [파일](#idl)의 ```PlayerFrameStatistics```설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f708a-182">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="f708a-183">선택 사항: 사용자 지정 데이터 채널</span><span class="sxs-lookup"><span data-stu-id="f708a-183">Optional: Custom data channels</span></span>

<span data-ttu-id="f708a-184">사용자 지정 데이터 채널은 이미 설정 된 원격 연결을 통해 사용자 데이터를 전송 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f708a-184">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="f708a-185">자세한 내용은 [사용자 지정 데이터 채널](holographic-remoting-custom-data-channels.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f708a-185">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="f708a-186">관련 항목</span><span class="sxs-lookup"><span data-stu-id="f708a-186">See Also</span></span>
* [<span data-ttu-id="f708a-187">Holographic 원격 호스트 앱 작성</span><span class="sxs-lookup"><span data-stu-id="f708a-187">Writing a Holographic Remoting host app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="f708a-188">사용자 지정 Holographic 원격 데이터 채널</span><span class="sxs-lookup"><span data-stu-id="f708a-188">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="f708a-189">Holographic 원격을 사용 하 여 보안 연결 설정</span><span class="sxs-lookup"><span data-stu-id="f708a-189">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="f708a-190">Holographic 원격 문제 해결 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="f708a-190">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="f708a-191">Holographic 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="f708a-191">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="f708a-192">Microsoft 개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="f708a-192">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)