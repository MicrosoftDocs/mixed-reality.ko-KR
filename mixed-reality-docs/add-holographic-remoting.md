---
title: Holographic 원격 추가
description: Holographic 원격을 사용 하 여 네트워크를 통해 HoloLens에 holograms을 렌더링 하는 방법을 설명 합니다.
author: mikeriches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality, holograms, holographic remoting, 원격 렌더링, 네트워크 렌더링, HoloLens, 원격 holograms
ms.openlocfilehash: 2f6ade5552c993f66281d0be8a7e62c8f076deac
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277711"
---
# <a name="add-holographic-remoting-hololens-1st-gen"></a><span data-ttu-id="fe7b6-104">Holographic 원격 추가 (HoloLens (첫 번째 gen))</span><span class="sxs-lookup"><span data-stu-id="fe7b6-104">Add Holographic Remoting (HoloLens (1st gen))</span></span>

>[!IMPORTANT]
><span data-ttu-id="fe7b6-105">이 문서에서는 HoloLens 1 용 호스트 응용 프로그램을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="fe7b6-106">HoloLens 용 호스트 응용 프로그램 **(1 세대)** 은 NuGet **패키지 버전 1.x**를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="fe7b6-107">즉, HoloLens 1 용으로 작성 된 호스트 응용 프로그램은 HoloLens 2와 호환 되지 않으며 그 반대의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="fe7b6-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fe7b6-108">HoloLens 2</span></span>

<span data-ttu-id="fe7b6-109">Holographic 원격을 사용 하는 HoloLens 개발자는 HoloLens 2와 호환 되도록 앱을 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="fe7b6-110">이렇게 하려면 새 버전의 Holographic Remoting NuGet 패키지가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="fe7b6-111">Holographic Remoting NuGet 패키지를 사용 하는 응용 프로그램에서 2.0.0.0 보다 작은 버전 번호를 사용 하는 경우 HoloLens 2의 Holographic 원격 플레이어에 연결 하려고 하면 연결이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-111">If an application using the Holographic Remoting NuGet package with a version number smaller than 2.0.0.0 attempts to connect to the Holographic Remoting Player on HoloLens 2, the connection will fail.</span></span>

>[!NOTE]
><span data-ttu-id="fe7b6-112">HoloLens 2와 관련 한 지침은 [여기](holographic-remoting-create-host.md)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-host.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="fe7b6-113">데스크톱 또는 UWP 앱에 holographic 원격 추가</span><span class="sxs-lookup"><span data-stu-id="fe7b6-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="fe7b6-114">이 페이지에서는 데스크톱 또는 UWP 앱에 Holographic 원격 기능을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="fe7b6-115">Holographic remoting을 사용 하면 앱에서 데스크톱 PC 또는 UWP 장치 (예: Xbox One)에서 호스트 되는 Holographic 콘텐츠를 사용 하 여 HoloLens를 대상으로 지정할 수 있으며,이를 통해 더 많은 시스템 리소스에 액세스 하 고 기존 데스크톱 PC 소프트웨어에 원격 [몰입 형 보기](app-views.md) 를 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-115">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="fe7b6-116">원격 호스트 앱은 HoloLens에서 입력 데이터 스트림을 받고, 가상 몰입 형 보기에서 콘텐츠를 렌더링 하 고, 콘텐츠 프레임을 HoloLens로 다시 스트리밍합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-116">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="fe7b6-117">연결은 표준 Wi-fi를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-117">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="fe7b6-118">원격 기능을 사용 하려면 NuGet 패키지를 사용 하 여 데스크톱 또는 UWP 앱에 holographic 원격을 추가 하 고, 연결을 처리 하 고 몰입 형 보기에서 렌더링 하는 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-118">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="fe7b6-119">도우미 라이브러리는 장치 연결을 처리 하는 작업을 간소화 하는 코드 샘플에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-119">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="fe7b6-120">일반적인 원격 연결의 경우 대기 시간은 50 밀리초로 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-120">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="fe7b6-121">플레이어 앱은 실시간으로 대기 시간을 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-121">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="fe7b6-122">이 문서의 코드 조각은 현재 [ C++ holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되 C++는 것 처럼 C + 17-so-far working 규격 C++/winrt 대신/cx 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-122">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="fe7b6-123">개념은 C++/winrt 프로젝트와 동일 하지만 코드를 변환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-123">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="fe7b6-124">원격 NuGet 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="fe7b6-124">Get the remoting NuGet packages</span></span>

<span data-ttu-id="fe7b6-125">Holographic remoting에 대 한 NuGet 패키지를 가져오고 프로젝트에서 참조를 추가 하려면 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-125">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="fe7b6-126">Visual Studio에서 프로젝트로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-126">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="fe7b6-127">프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리 ...** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-127">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="fe7b6-128">표시 되는 패널에서 **찾아보기** 를 클릭 한 다음 "Holographic Remoting"을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-128">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="fe7b6-129">**Holographic** 를 선택 하 고 **설치**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-129">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="fe7b6-130">**미리 보기** 대화 상자가 표시 되 면 **확인**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-130">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="fe7b6-131">표시 되는 다음 대화 상자는 사용권 계약입니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-131">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="fe7b6-132">**동의** 함을 클릭 하 여 사용권 계약에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-132">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="fe7b6-133">HolographicStreamerHelpers 만들기</span><span class="sxs-lookup"><span data-stu-id="fe7b6-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="fe7b6-134">먼저 HolographicStreamerHelpers의 인스턴스가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-134">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="fe7b6-135">원격을 처리 하는 클래스에이를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-135">Add this to the class that will be handling remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="fe7b6-136">또한 연결 상태를 추적 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-136">You'll also need to track connection state.</span></span> <span data-ttu-id="fe7b6-137">미리 보기를 렌더링 하려면 질감을 복사 하 여 복사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-137">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="fe7b6-138">또한 연결 상태 잠금, HoloLens의 IP 주소를 저장 하는 몇 가지 방법 등의 몇 가지 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-138">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="fe7b6-139">HolographicStreamerHelpers를 초기화 하 고 HoloLens에 연결</span><span class="sxs-lookup"><span data-stu-id="fe7b6-139">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="fe7b6-140">HoloLens 장치에 연결 하려면 HolographicStreamerHelpers의 인스턴스를 만들고 대상 IP 주소에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-140">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="fe7b6-141">Holographic Remoting 라이브러리에서 인코더 및 디코더 해상도가 정확 하 게 일치 하도록 예상 하기 때문에 HoloLens 표시 너비 및 높이와 일치 하도록 비디오 프레임 크기를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-141">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

<span data-ttu-id="fe7b6-142">장치 연결이 비동기입니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-142">The device connection is asynchronous.</span></span> <span data-ttu-id="fe7b6-143">앱에서 연결, 연결 끊기 및 프레임 전송 이벤트에 대 한 이벤트 처리기를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-143">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="fe7b6-144">OnConnected 이벤트는 UI를 업데이트 하 고 렌더링을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-144">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="fe7b6-145">바탕 화면 코드 샘플에서는 "연결 된" 메시지로 창 제목을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-145">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="fe7b6-146">OnDisconnected 이벤트는 다시 연결, UI 업데이트 등을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-146">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="fe7b6-147">이 예에서는 일시적인 오류가 발생 하는 경우 다시 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-147">In this example, we reconnect if there is a transient failure.</span></span>

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

<span data-ttu-id="fe7b6-148">원격 구성 요소에서 프레임을 전송할 준비가 되 면 앱에 Send프레임 이벤트에서 복사본을 만들 수 있는 기회가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-148">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="fe7b6-149">여기에서 프레임을 스왑 체인에 복사 하 여 미리 보기 창에 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-149">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a><span data-ttu-id="fe7b6-150">Holographic 내용 렌더링</span><span class="sxs-lookup"><span data-stu-id="fe7b6-150">Render holographic content</span></span>

<span data-ttu-id="fe7b6-151">원격을 사용 하 여 콘텐츠를 렌더링 하려면 데스크톱 또는 UWP 앱 내에서 가상 IFrameworkView를 설정 하 고 원격에서 holographic 프레임을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-151">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="fe7b6-152">모든 Windows Holographic Api는이 뷰와 동일한 방식으로 사용 되지만 약간 다르게 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-152">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="fe7b6-153">Holographic space 및 speech 구성 요소를 직접 만드는 대신 HolographicRemotingHelpers 클래스에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-153">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="fe7b6-154">Run 메서드 내에서 업데이트 루프를 사용 하는 대신 데스크톱 또는 UWP 앱의 주 루프에서 틱 업데이트를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-154">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="fe7b6-155">이렇게 하면 데스크톱 또는 UWP 앱이 메시지 처리를 계속 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-155">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="fe7b6-156">Holographic app 뷰의 Tick () 메서드는 업데이트, 그리기, 표시 루프의 반복 하나를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-156">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

<span data-ttu-id="fe7b6-157">Holographic 앱 보기 업데이트, 렌더링 및 present 루프는 hpc에서 실행 하는 경우와 정확히 동일 합니다. 단, 데스크톱 PC에서 훨씬 더 많은 양의 시스템 리소스에 액세스할 수 있다는 점이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-157">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="fe7b6-158">더 많은 삼각형을 렌더링 하 고, 더 많은 그리기 패스를 사용 하 고, 더 많은 물리학를 수행 하 고, x64 프로세스를 사용 하 여 2gb 이상의 RAM이 필요한 콘텐츠를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-158">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="fe7b6-159">원격 세션의 연결을 끊고 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-159">Disconnect and end the remote session</span></span>

<span data-ttu-id="fe7b6-160">연결을 끊으려면 예를 들어 사용자가 UI 단추를 클릭 하 여 HolographicStreamerHelpers에서 연결 끊기 ()의 연결을 끊은 다음 개체를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-160">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a><span data-ttu-id="fe7b6-161">원격 플레이어 가져오기</span><span class="sxs-lookup"><span data-stu-id="fe7b6-161">Get the remoting player</span></span>

<span data-ttu-id="fe7b6-162">Windows Holographic remoting 플레이어는 연결할 원격 호스트 앱에 대 한 끝점으로 Windows 앱 스토어에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-162">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="fe7b6-163">Windows Holographic remoting 플레이어를 다운로드 하려면 HoloLens에서 Windows 앱 스토어를 방문 하 여 원격을 검색 하 고 앱을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-163">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="fe7b6-164">원격 플레이어에는 통계를 화면에 표시 하는 기능이 포함 되어 있습니다 .이 기능은 원격 호스트 앱을 디버그할 때 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-164">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="fe7b6-165">메모 및 리소스</span><span class="sxs-lookup"><span data-stu-id="fe7b6-165">Notes and resources</span></span>

<span data-ttu-id="fe7b6-166">Holographic 앱 보기는 holographic 공간을 초기화 하는 데 사용 해야 하는 Direct3D 장치에 앱을 제공 하는 방법이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-166">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="fe7b6-167">앱은이 Direct3D 장치를 사용 하 여 미리 보기 프레임을 복사 하 고 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-167">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="fe7b6-168">**코드 샘플:** Holographic 원격 코드 샘플을 사용할 수 있습니다. 여기에는 데스크톱 Win32, UWP DirectX 및 UWP for XAML의 원격 및 원격 호스트 프로젝트와 호환 되는 Holographic 응용 프로그램 보기가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-168">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="fe7b6-169">다운로드 하려면 다음을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-169">To get it, go here:</span></span>
* [<span data-ttu-id="fe7b6-170">원격을 위한 Windows Holographic 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="fe7b6-170">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="fe7b6-171">**디버깅 참고 사항:** Holographic Remoting 라이브러리는 첫 번째 예외를 throw 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-171">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="fe7b6-172">이러한 예외는 동시에 활성화 되는 Visual Studio 예외 설정에 따라 디버깅 세션에서 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-172">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="fe7b6-173">이러한 예외는 Holographic Remoting 라이브러리를 통해 내부적으로 catch 되며 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe7b6-173">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
