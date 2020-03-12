---
title: 사용자 지정 Holographic Remoting 플레이어 작성
description: 사용자 지정 Holographic 원격 플레이어 앱을 만들면 원격 컴퓨터에 렌더링 된 콘텐츠를 HoloLens 2로 표시할 수 있는 사용자 지정 응용 프로그램을 만들 수 있습니다. 이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: eaa6549eb34d3a37c21b3decb348bf43594a110f
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092412"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="e1846-105">사용자 지정 Holographic Remoting 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="e1846-105">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="e1846-106">이 문서에서는 HoloLens 2에 대 한 사용자 지정 플레이어 응용 프로그램을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-106">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="e1846-107">HoloLens 2 용으로 작성 된 사용자 지정 플레이어는 HoloLens 1 용으로 작성 된 원격 응용 프로그램과 호환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-107">Custom players written for HoloLens 2 are not compatible with remote applications written for HoloLens 1.</span></span> <span data-ttu-id="e1846-108">이는 두 응용 프로그램이 모두 NuGet **패키지 버전 2.x**를 사용 해야 함을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-108">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="e1846-109">사용자 지정 Holographic 원격 플레이어 앱을 만들면 HoloLens 2의 원격 컴퓨터에서 [몰입 형 보기](app-views.md) 를 표시할 수 있는 사용자 지정 응용 프로그램을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-109">By creating a custom Holographic Remoting player app you can create a custom application capable of displaying [immersive views](app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="e1846-110">이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-110">This article describes how this can be achieved.</span></span> <span data-ttu-id="e1846-111">이 페이지 및 작업 프로젝트의 모든 코드는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-111">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="e1846-112">Holographic 원격 플레이어를 사용 하면 앱에서 데스크톱 PC 또는 UWP 장치 (예: Xbox One)에서 [렌더링](rendering.md) 된 Holographic 콘텐츠를 표시 하 여 더 많은 시스템 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-112">A Holographic Remoting player allows your app to display holographic content [rendered](rendering.md) on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources.</span></span> <span data-ttu-id="e1846-113">Holographic Remoting player 앱은 입력 데이터를 Holographic Remoting 원격 응용 프로그램으로 스트리밍하 고 비디오 및 오디오 스트림으로 몰입 형 보기를 다시 받습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-113">A Holographic Remoting player app streams input data to a Holographic Remoting remote application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="e1846-114">연결은 표준 Wi-fi를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-114">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="e1846-115">플레이어 앱을 만들려면 NuGet 패키지를 사용 하 여 UWP 앱에 Holographic 원격을 추가 하 고, 연결을 처리 하 고 몰입 형 뷰를 표시 하는 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-115">To create a player app, you will use a NuGet package to add Holographic Remoting to your UWP app, and write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="e1846-116">필수 조건</span><span class="sxs-lookup"><span data-stu-id="e1846-116">Prerequisites</span></span>

<span data-ttu-id="e1846-117">좋은 출발점은 이미 Windows Mixed Reality API를 대상으로 하는 작동 하는 DirectX 기반 UWP 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-117">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="e1846-118">자세한 내용은 [DirectX 개발 개요](directx-development-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e1846-118">For details see [DirectX development overview](directx-development-overview.md).</span></span> <span data-ttu-id="e1846-119">기존 앱이 없고 처음부터 시작 하려면 [ C++ holographic 프로젝트 템플릿이](creating-a-holographic-directx-project.md) 좋은 출발점입니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-119">If you do not have an existing app and want to start from scratch the [C++ holographic project template](creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="e1846-120">Holographic 원격을 사용 하는 모든 앱은 [다중 스레드 아파트](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)를 사용 하도록 작성 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-120">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="e1846-121">[단일 스레드 아파트](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) 사용 하는 것은 지원 되지만, 재생 하는 동안 일지 성능이 저하 되 고 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-121">The use of a [single-threaded appartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="e1846-122">/Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) 사용 하는 경우 다중 스레드 아파트는 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-122">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="e1846-123">Holographic 원격 NuGet 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="e1846-123">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="e1846-124">Visual Studio에서 프로젝트에 NuGet 패키지를 추가 하려면 다음 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-124">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="e1846-125">Visual Studio에서 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-125">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="e1846-126">프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리 ...** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-126">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="e1846-127">표시 되는 패널에서 **찾아보기** 를 클릭 한 다음 "Holographic Remoting"을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-127">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="e1846-128">**Holographic**를 선택 하 고 최신 **2.x 버전을** 선택 하 고 **설치**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-128">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and click **Install**.</span></span>
5. <span data-ttu-id="e1846-129">**미리 보기** 대화 상자가 표시 되 면 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-129">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="e1846-130">표시 되는 다음 대화 상자는 사용권 계약입니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-130">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="e1846-131">**동의** 함을 클릭 하 여 사용권 계약에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-131">Click on **I Accept** to accept the license agreement.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="e1846-132">NuGet 패키지 내의 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` Holographic Remoting에서 노출 하는 API에 대 한 자세한 설명서를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-132">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="e1846-133">응용 프로그램의 appxmanifest.xml을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-133">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="e1846-134">응용 프로그램이 NuGet 패키지에 의해 추가 된 Holographic를 인식 하도록 하려면 프로젝트에서 다음 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-134">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="e1846-135">솔루션 탐색기에서 **appxmanifest.xml** 파일을 마우스 오른쪽 단추로 클릭 하 고 **연결 프로그램 ...을** 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-135">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="e1846-136">**XML (텍스트) 편집기** 를 선택 하 고 확인을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-136">Select **XML (Text) Editor** and click OK</span></span>
3. <span data-ttu-id="e1846-137">파일에 다음 줄을 추가 하 고 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-137">Add the following lines to the file and save</span></span>
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
## <a name="create-the-player-context"></a><span data-ttu-id="e1846-138">플레이어 컨텍스트 만들기</span><span class="sxs-lookup"><span data-stu-id="e1846-138">Create the player context</span></span>

<span data-ttu-id="e1846-139">첫 번째 단계로 응용 프로그램은 플레이어 컨텍스트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-139">As a first step the application should create a player context.</span></span>

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
><span data-ttu-id="e1846-140">Holographic Remoting은 원격 특정 런타임을 사용 하 여 Windows의 일부인 Windows Mixed Reality 런타임을 대체 하는 방식으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-140">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="e1846-141">플레이어 컨텍스트를 만드는 동안이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-141">This is done during the creation of the player context.</span></span> <span data-ttu-id="e1846-142">이러한 이유로 플레이어 컨텍스트를 만들기 전에 Windows Mixed Reality API를 호출 하면 예기치 않은 동작이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-142">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="e1846-143">권장 되는 방법은 혼합 현실 API와의 상호 작용 전에 가능한 한 빨리 플레이어 컨텍스트를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-143">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="e1846-144">이후에 만들어지거나 검색 된 개체를 사용 하 여 ```PlayerContext::Create```를 호출 하기 전에 Windows Mixed Reality API를 통해 만들어지거나 검색 된 개체를 혼합 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="e1846-144">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="e1846-145">그런 다음 [HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)를 호출 하 여 HolographicSpace를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-145">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a><span data-ttu-id="e1846-146">원격 앱에 연결</span><span class="sxs-lookup"><span data-stu-id="e1846-146">Connect to the remote app</span></span>

<span data-ttu-id="e1846-147">플레이어 앱이 콘텐츠를 렌더링할 준비가 되 면 원격 앱에 대 한 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-147">Once the player app is ready for rendering content a connection to the remote app can be established.</span></span>

<span data-ttu-id="e1846-148">다음 방법 중 하나로 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-148">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="e1846-149">HoloLens 2에서 실행 중인 플레이어 앱은 원격 앱에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-149">The player app running on HoloLens 2 connects to the remote app.</span></span>
2) <span data-ttu-id="e1846-150">원격 앱은 HoloLens 2에서 실행 중인 플레이어 앱에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-150">The remote app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="e1846-151">플레이어 앱에서 원격 앱으로 연결 하려면 호스트 이름 및 포트를 지정 하는 플레이어 컨텍스트의 ```Connect``` 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-151">To connect from the player app to the remote app call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="e1846-152">기본 포트는 **8265**입니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-152">The default port is **8265**.</span></span>

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
><span data-ttu-id="e1846-153">모든 C++/WINRT API ```Connect```는 처리 해야 하는 WinRT:: hresult_error을 throw 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-153">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="e1846-154">플레이어 앱에서 들어오는 연결을 수신 하는 작업은 ```Listen``` 메서드를 호출 하 여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-154">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="e1846-155">이 호출 중에 핸드셰이크 포트와 전송 포트를 모두 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-155">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="e1846-156">핸드셰이크 포트는 초기 핸드셰이크에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-156">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="e1846-157">그런 다음 데이터는 전송 포트를 통해 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-157">The data is then send over the transport port.</span></span> <span data-ttu-id="e1846-158">기본적으로 포트 번호 **8265** 및 **8266** 이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-158">By default port number **8265** and **8266** are used.</span></span>

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


## <a name="handling-connection-related-events"></a><span data-ttu-id="e1846-159">연결 관련 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="e1846-159">Handling connection related events</span></span>

<span data-ttu-id="e1846-160">```PlayerContext```는 연결 상태를 모니터링 하는 세 개의 이벤트를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-160">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="e1846-161">OnConnected: 원격 앱에 대 한 연결이 성공적으로 설정 되 면 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-161">OnConnected: Triggered when a connection to the remote app has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="e1846-162">OnDisconnected: 설정 된 연결이 종료 되거나 연결을 설정할 수 없는 경우 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-162">OnDisconnected: Triggered if an established connection is terminated or a connection could not be established.</span></span>
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
><span data-ttu-id="e1846-163">가능한 ```ConnectionFailureReason``` 값은 ```Microsoft.Holographic.AppRemoting.idl``` [파일](#idl)에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-163">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="e1846-164">OnListening: 들어오는 연결에 대 한 수신 대기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-164">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="e1846-165">또한 플레이어 컨텍스트의 ```ConnectionState``` 속성을 사용 하 여 연결 상태를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-165">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="e1846-166">원격으로 렌더링 된 프레임을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-166">Display the remotely rendered frame</span></span>

<span data-ttu-id="e1846-167">원격으로 렌더링 된 콘텐츠를 표시 하려면 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)를 렌더링 하는 동안 ```PlayerContext::BlitRemoteFrame```를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-167">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame``` while rendering a [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="e1846-168">```BlitRemoteFrame```를 사용 하려면 현재 HolographicFrame의 백 버퍼가 렌더링 대상으로 바인딩되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-168">```BlitRemoteFrame``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="e1846-169">백 버퍼는 [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) 속성을 통해 [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) 에서 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-169">The back buffer can be received from the [HolographicCameraRenderingParameters](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="e1846-170">이 호출 되 면 ```BlitRemoteFrame``` 원격 응용 프로그램에서 수신 된 최신 프레임을 HolographicFrame의 백 버퍼에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-170">When called, ```BlitRemoteFrame``` copies the latest received frame from the remote application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="e1846-171">원격 응용 프로그램에서 원격 프레임을 렌더링 하는 동안 포커스 지점을 지정 하는 경우에도 포커스 지점 집합이 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-171">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="e1846-172">```PlayerContext::BlitRemoteFrame``` 현재 프레임의 포커스 지점을 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-172">```PlayerContext::BlitRemoteFrame``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="e1846-173">대체 (fallback) 포커스 지점을 지정 하려면 ```PlayerContext::BlitRemoteFrame```하기 전에 [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-173">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame```.</span></span> 
>- <span data-ttu-id="e1846-174">원격 포커스 지점을 덮어쓰려면 ```PlayerContext::BlitRemoteFrame```후 [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-174">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame```.</span></span>

<span data-ttu-id="e1846-175">성공 하면 ```BlitRemoteFrame```에서 ```BlitResult::Success_Color```를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-175">On success, ```BlitRemoteFrame``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="e1846-176">그렇지 않으면 실패 원인을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-176">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="e1846-177">```BlitResult::Failed_NoRemoteFrameAvailable```: 원격 프레임을 사용할 수 없기 때문에 실패 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-177">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="e1846-178">```BlitResult::Failed_NoCamera```: 카메라가 없어 실패 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-178">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="e1846-179">```BlitResult::Failed_RemoteFrameTooOld```: 원격 프레임이 너무 오래 되어 실패 했습니다 (PlayerContext:: BlitRemoteFrameTimeout 속성 참조).</span><span class="sxs-lookup"><span data-stu-id="e1846-179">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

>[!IMPORTANT]
> <span data-ttu-id="e1846-180">[2.1.0](holographic-remoting-version-history.md#v2.1.0) 버전부터 사용자 지정 플레이어를 사용 하 여 Holographic 원격을 통해 깊이 재 프로젝션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-180">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) it is possible with a custom player to use depth reprojection via Holographic Remoting.</span></span>

<span data-ttu-id="e1846-181">```BlitResult```는 다음과 같은 경우에 ```BlitResult::Success_Color_Depth``` 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-181">```BlitResult``` can also return ```BlitResult::Success_Color_Depth``` under the following conditions:</span></span>

- <span data-ttu-id="e1846-182">원격 앱이 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)를 통해 깊이 버퍼를 커밋 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-182">The remote app has committed a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>
- <span data-ttu-id="e1846-183">```BlitRemoteFrame```를 호출 하기 전에 사용자 지정 플레이어 앱이 유효한 깊이 버퍼를 바인딩 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-183">The custom player app has bound a valid depth buffer before calling ```BlitRemoteFrame```.</span></span>

<span data-ttu-id="e1846-184">이러한 조건이 충족 되는 경우 ```BlitRemoteFrame```는 원격 깊이를 현재 바인딩된 로컬 깊이 버퍼로 array.blit 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-184">If these conditions are met ```BlitRemoteFrame``` will blit the remote depth into the currently bound local depth buffer.</span></span> <span data-ttu-id="e1846-185">그러면 원격 렌더링 된 콘텐츠와 깊이 교차 하는 추가 로컬 콘텐츠를 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-185">You can then render additional local content which will have depth intersection with the remote rendered content.</span></span> <span data-ttu-id="e1846-186">또한 사용자 지정 플레이어에서 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) 를 통해 로컬 수준 버퍼를 커밋하여 원격 및 로컬 렌더링 된 콘텐츠에 대해 깊이 있게 프로젝션 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-186">Additionally you can commit the local depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) in your custom player to have depth reprojection for remote and local rendered content.</span></span> <span data-ttu-id="e1846-187">자세한 내용은 [깊이 Reprojection](hologram-stability.md#reprojection) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e1846-187">See [Depth Reprojection](hologram-stability.md#reprojection) for details.</span></span>

### <a name="projection-transform-mode"></a><span data-ttu-id="e1846-188">프로젝션 변환 모드</span><span class="sxs-lookup"><span data-stu-id="e1846-188">Projection Transform Mode</span></span>

<span data-ttu-id="e1846-189">Holographic Remoting을 통해 깊이 다시 프로젝션을 사용할 때 발생 하는 한 가지 문제는 사용자 지정 플레이어 앱에서 직접 렌더링 하는 로컬 콘텐츠와 다른 프로젝션 변환으로 원격 콘텐츠를 렌더링할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-189">One problem which surfaces when using depth reprojection via Holographic Remoting is that the remote content can be rendered with a different projection transform than local content directly rendered by your custom player app.</span></span> <span data-ttu-id="e1846-190">일반적인 사용 사례는 선수 및 원격 측면에서 근거리 및 far 평면 ( [HolographicCamera:: SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) 및 [HolographicCamera:: SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)를 통해)에 대해 서로 다른 값을 지정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-190">A common use-case is to specify different values for near and far plane (via [HolographicCamera::SetNearPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) and [HolographicCamera::SetFarPlaneDistance](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) on the player side and the remote side.</span></span> <span data-ttu-id="e1846-191">이 경우 플레이어 쪽의 프로젝션 변환에 멀리 떨어져 있는 원격 평면 거리 또는 로컬 항목이 반영 되어야 하는지는 명확 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-191">In this case it's not clear if the projection transform on the player side should reflect the remote near/far plane distances or the local ones.</span></span>

<span data-ttu-id="e1846-192">버전 [2.1.0](holographic-remoting-version-history.md#v2.1.0) 부터 ```PlayerContext::ProjectionTransformConfig```를 통해 프로젝션 변환 모드를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-192">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) you can control the projection transform mode via ```PlayerContext::ProjectionTransformConfig```.</span></span> <span data-ttu-id="e1846-193">지원되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-193">Supported values are:</span></span>

- <span data-ttu-id="e1846-194">```Local``` - [HolographicCameraPose::P rojectiontransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) 는 HolographicCamera에서 사용자 지정 플레이어 앱에 의해 설정 된 근거리/원거리 평면 거리를 반영 하는 프로젝션 변환을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-194">```Local``` - [HolographicCameraPose::ProjectionTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) returns a projection transform which reflects the near/far plane distances set by your custom player app on the HolographicCamera.</span></span>
- <span data-ttu-id="e1846-195">```Remote``` 프로젝션 변환은 원격 앱에서 지정 된 근거리/원거리 평면 거리를 반영 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-195">```Remote``` - Projection transform reflects the near/far plane distances specified by the remote app.</span></span>
- <span data-ttu-id="e1846-196">원격 앱 및 사용자 지정 플레이어 앱에서의 ```Merged``` 근거리/Far 비행기 거리가 병합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-196">```Merged``` - Near/Far plane distances from your remote app and your custom player app are merged.</span></span> <span data-ttu-id="e1846-197">기본적으로이 작업은 근거리 평면 거리의 최소 및 최대 평면 거리의 최대값을 차지 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-197">By default this is done by taking the minimum of the near plane distances and the maximum of the far plane distances.</span></span> <span data-ttu-id="e1846-198">원격 또는 로컬 쪽이 반전 된 경우 (근처 < 멀리 떨어져 있는 경우 멀리 떨어져 있는 근거리/원거리 비행기 거리가 대칭 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-198">In case either the remote or local side are inverted, say far < near, the remote near/far plane distances are flipped.</span></span>

## <span data-ttu-id="e1846-199">선택 사항: BlitRemoteFrameTimeout 설정<a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="e1846-199">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="e1846-200">```PlayerContext::BlitRemoteFrameTimeout``` 버전 [2.0.9](holographic-remoting-version-history.md#v2.0.9)부터 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-200">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="e1846-201">```PlayerContext::BlitRemoteFrameTimeout``` 속성은 새 원격 프레임을 받지 못한 경우 원격 프레임을 다시 사용 하는 시간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-201">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="e1846-202">일반적인 사용 사례는 특정 시간 동안 새 프레임을 받지 못한 경우 BlitRemoteFrame 시간 제한을 사용 하 여 빈 화면을 표시 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-202">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="e1846-203">사용 하도록 설정 하면 ```BlitRemoteFrame``` 메서드의 반환 형식을 사용 하 여 로컬로 렌더링 된 대체 콘텐츠로 전환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-203">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="e1846-204">시간 제한을 사용 하도록 설정 하려면 속성 값을 100ms 보다 크거나 같은 기간으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-204">To enable the timeout, set the property value to a duration equal or greater than 100ms.</span></span> <span data-ttu-id="e1846-205">시간 제한을 사용 하지 않도록 설정 하려면 속성을 0 duration으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-205">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="e1846-206">제한 시간을 설정 하 고 설정 된 기간 동안 원격 프레임을 받지 못한 경우에는 BlitRemoteFrame이 실패 하 고 새 원격 프레임을 받을 때까지 ```Failed_RemoteFrameTooOld``` 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-206">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="e1846-207">선택 사항: 마지막 원격 프레임에 대 한 통계 가져오기</span><span class="sxs-lookup"><span data-stu-id="e1846-207">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="e1846-208">성능 또는 네트워크 문제를 진단 하려면 ```PlayerContext::LastFrameStatistics``` 속성을 통해 마지막 원격 프레임에 대 한 통계를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-208">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="e1846-209">[HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)를 호출 하는 동안 통계가 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-209">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="e1846-210">자세한 내용은 ```Microsoft.Holographic.AppRemoting.idl``` [파일](#idl)의 ```PlayerFrameStatistics``` 설명서를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e1846-210">For more details, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="e1846-211">선택 사항: 사용자 지정 데이터 채널</span><span class="sxs-lookup"><span data-stu-id="e1846-211">Optional: Custom data channels</span></span>

<span data-ttu-id="e1846-212">사용자 지정 데이터 채널은 이미 설정 된 원격 연결을 통해 사용자 데이터를 전송 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1846-212">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="e1846-213">자세한 내용은 [사용자 지정 데이터 채널](holographic-remoting-custom-data-channels.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e1846-213">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1846-214">관련 항목</span><span class="sxs-lookup"><span data-stu-id="e1846-214">See Also</span></span>
* [<span data-ttu-id="e1846-215">Holographic Remoting 원격 앱 작성</span><span class="sxs-lookup"><span data-stu-id="e1846-215">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="e1846-216">사용자 지정 홀로그램 원격 데이터 채널</span><span class="sxs-lookup"><span data-stu-id="e1846-216">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="e1846-217">Holographic 원격을 사용 하 여 보안 연결 설정</span><span class="sxs-lookup"><span data-stu-id="e1846-217">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="e1846-218">Holographic 원격 문제 해결 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="e1846-218">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="e1846-219">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="e1846-219">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="e1846-220">Microsoft 개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="e1846-220">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
