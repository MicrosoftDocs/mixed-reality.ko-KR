---
title: HolographicSpace 가져오기
description: Holographic 렌더링 및 공간 입력의 핵심 개념인 HolographicSpace API에 대해 설명 합니다.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace, CoreWindow, 공간 입력, 렌더링, 스왑 체인, holographic 프레임, 업데이트 루프, 게임 루프, 참조 프레임, locatability, 샘플 코드, 연습
ms.openlocfilehash: 76211c8a5394e2e296748253df4eac063841746c
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277831"
---
# <a name="getting-a-holographicspace"></a><span data-ttu-id="7fcab-104">HolographicSpace 가져오기</span><span class="sxs-lookup"><span data-stu-id="7fcab-104">Getting a HolographicSpace</span></span>

<span data-ttu-id="7fcab-105"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> 클래스는 holographic 세계의 포털입니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-105">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class is your portal into the holographic world.</span></span> <span data-ttu-id="7fcab-106">몰입 형 렌더링을 제어 하 고, 카메라 데이터를 제공 하 고, 공간 추론 Api에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-106">It controls immersive rendering, provides camera data, and provides access to spatial reasoning APIs.</span></span> <span data-ttu-id="7fcab-107">UWP 앱의 <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> 또는 Win32 앱의 HWND에 대해 하나를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-107">You will create one for your UWP app's <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> or your Win32 app's HWND.</span></span>

## <a name="set-up-the-holographic-space"></a><span data-ttu-id="7fcab-108">Holographic 공간 설정</span><span class="sxs-lookup"><span data-stu-id="7fcab-108">Set up the holographic space</span></span>

<span data-ttu-id="7fcab-109">Holographic space 개체를 만드는 첫 번째 단계는 Windows Mixed Reality 앱을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-109">Creating the holographic space object is the first step in making your Windows Mixed Reality app.</span></span> <span data-ttu-id="7fcab-110">기존 Windows 앱은 응용 프로그램 보기의 핵심 창에 대해 만들어진 Direct3D 스왑 체인으로 렌더링 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-110">Traditional Windows apps render to a Direct3D swap chain created for the core window of their application view.</span></span> <span data-ttu-id="7fcab-111">이 스왑 체인은 holographic UI의 슬레이트에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-111">This swap chain is displayed to a slate in the holographic UI.</span></span> <span data-ttu-id="7fcab-112">2D 슬레이트가 아닌 응용 프로그램 보기를 holographic 하려면 스왑 체인 대신 해당 코어 창에 holographic 공간을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-112">To make your application view holographic rather than a 2D slate, create a holographic space for its core window instead of a swap chain.</span></span> <span data-ttu-id="7fcab-113">이 holographic 공간에 의해 생성 된 holographic 프레임을 표시 하면 앱이 전체 화면 렌더링 모드로 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-113">Presenting holographic frames that are created by this holographic space puts your app into full-screen rendering mode.</span></span>

<span data-ttu-id="7fcab-114">[ *Holographic DirectX 11 앱 (유니버설 Windows) 템플릿*에서 시작](creating-a-holographic-directx-project.md)하는 **UWP 앱** 의 경우 appview .cpp의 **setwindow** 메서드에서이 코드를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-114">For a **UWP app** [starting from the *Holographic DirectX 11 App (Universal Windows) template*](creating-a-holographic-directx-project.md), look for this code in the **SetWindow** method in AppView.cpp:</span></span>

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

<span data-ttu-id="7fcab-115">[ *Basichologram* win32 샘플에서 시작](creating-a-holographic-directx-project.md#creating-a-win32-project)하는 **win32 앱** 에 대 한 자세한 내용은 **app:: CreateWindowAndHolographicSpace** 를 참조 하세요. 예를 들어, HWND를 만든 다음 연결 된 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>를 만들어 몰입 형 hwnd로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-115">For a **Win32 app** [starting from the *BasicHologram* Win32 sample](creating-a-holographic-directx-project.md#creating-a-win32-project), look at **App::CreateWindowAndHolographicSpace** for an example of how to create an HWND and then convert it into an immersive HWND by creating an associated <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:</span></span>
```cpp
void App::CreateWindowAndHolographicSpace(HINSTANCE hInstance, int nCmdShow)
{
    // Store the instance handle in our class variable.
    m_hInst = hInstance;

    // Create the window for the HolographicSpace.
    hWnd = CreateWindowW(
        m_szWindowClass, 
        m_szTitle,
        WS_VISIBLE,
        CW_USEDEFAULT, 
        0, 
        CW_USEDEFAULT, 
        0, 
        nullptr, 
        nullptr, 
        hInstance, 
        nullptr);

    if (!hWnd)
    {
        winrt::check_hresult(E_FAIL);
    }

    {
        // Use WinRT factory to create the holographic space.
        using namespace winrt::Windows::Graphics::Holographic;
        winrt::com_ptr<IHolographicSpaceInterop> holographicSpaceInterop =
            winrt::get_activation_factory<HolographicSpace, IHolographicSpaceInterop>();
        winrt::com_ptr<ABI::Windows::Graphics::Holographic::IHolographicSpace> spHolographicSpace;
        winrt::check_hresult(holographicSpaceInterop->CreateForWindow(
            hWnd, __uuidof(ABI::Windows::Graphics::Holographic::IHolographicSpace),
            winrt::put_abi(spHolographicSpace)));

        if (!spHolographicSpace)
        {
            winrt::check_hresult(E_FAIL);
        }

        // Store the holographic space.
        m_holographicSpace = spHolographicSpace.as<HolographicSpace>();
    }

    // The DeviceResources class uses the preferred DXGI adapter ID from the holographic
    // space (when available) to create a Direct3D device. The HolographicSpace
    // uses this ID3D11Device to create and manage device-based resources such as
    // swap chains.
    m_deviceResources->SetHolographicSpace(m_holographicSpace);

    // The main class uses the holographic space for updates and rendering.
    m_main->SetHolographicSpace(hWnd, m_holographicSpace);

    // Show the window. This will activate the holographic view and switch focus
    // to the app in Windows Mixed Reality.
    ShowWindow(hWnd, nCmdShow);
    UpdateWindow(hWnd);
}
```

<span data-ttu-id="7fcab-116">UWP CoreWindow 또는 Win32 HWND에 대해 HolographicSpace를 얻 었으 면 해당 HolographicSpace를 사용 하 여 holographic 카메라를 처리 하 고 좌표계를 만들며 holographic 렌더링을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-116">Now that you've obtained a HolographicSpace for either your UWP CoreWindow or Win32 HWND, you'll use that HolographicSpace to handle holographic cameras, create coordinate systems and do holographic rendering.</span></span> <span data-ttu-id="7fcab-117">현재 holographic 공간은 DirectX 템플릿의 여러 위치에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-117">The current holographic space is used in multiple places in the DirectX template:</span></span>
* <span data-ttu-id="7fcab-118">**DeviceResources** 클래스는 Direct3D 장치를 만들기 위해 HolographicSpace 개체에서 일부 정보를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-118">The **DeviceResources** class needs to get some information from the HolographicSpace object in order to create the Direct3D device.</span></span> <span data-ttu-id="7fcab-119">이는 holographic 표시와 연결 된 DXGI 어댑터 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-119">This is the DXGI adapter ID associated with the holographic display.</span></span> <span data-ttu-id="7fcab-120"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> 클래스는 앱의 Direct3D 11 장치를 사용 하 여 각 holographic 카메라에 대 한 백 버퍼와 같은 장치 기반 리소스를 만들고 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> class uses your app's Direct3D 11 device to create and manage device-based resources, such as the back buffers for each holographic camera.</span></span> <span data-ttu-id="7fcab-121">이 함수가 내부적으로 수행 하는 작업을 확인 하는 데 관심이 있는 경우 DeviceResources에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-121">If you're interested in seeing what this function does under the hood, you'll find it in DeviceResources.cpp.</span></span>
* <span data-ttu-id="7fcab-122">**DeviceResources:: InitializeUsingHolographicSpace** 함수는 LUID를 조회 하 여 어댑터를 가져오는 방법 및 기본 설정 된 어댑터가 지정 되지 않은 경우 기본 어댑터를 선택 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-122">The function **DeviceResources::InitializeUsingHolographicSpace** demonstrates how to obtain the adapter by looking up the LUID – and how to choose a default adapter when no preferred adapter is specified.</span></span>
* <span data-ttu-id="7fcab-123">앱의 주 클래스는 업데이트 및 렌더링을 위해 **Appview:: SetWindow** 또는 **App:: CreateWindowAndHolographicSpace** 의 holographic space를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-123">The app's main class uses the holographic space from **AppView::SetWindow** or **App::CreateWindowAndHolographicSpace** for updates and rendering.</span></span>

>[!NOTE]
><span data-ttu-id="7fcab-124">아래 섹션에서는 holographic UWP 앱 템플릿에서 시작한 것으로 가정 하는 **Appview:: SetWindow** 와 같은 템플릿의 함수 이름을 언급 하지만, 표시 되는 코드 조각은 UWP 및 Win32 앱에서 동일 하 게 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-124">While the sections below mention function names from the template like **AppView::SetWindow** that assume that you started from the holographic UWP app template, the code snippets you see will apply equally across UWP and Win32 apps.</span></span>

<span data-ttu-id="7fcab-125">다음으로, **SetHolographicSpace** 가 appmain 클래스에서 담당 하는 설치 프로세스를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-125">Next, we'll dive into the setup process that **SetHolographicSpace** is responsible for in the AppMain class.</span></span>

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a><span data-ttu-id="7fcab-126">카메라 이벤트 구독, 카메라 리소스 만들기 및 제거</span><span class="sxs-lookup"><span data-stu-id="7fcab-126">Subscribe to camera events, create and remove camera resources</span></span>

<span data-ttu-id="7fcab-127">앱의 holographic 콘텐츠는 holographic 공간에 상주 하며 장면의 여러 큐브 뷰를 나타내는 하나 이상의 holographic 카메라를 통해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-127">Your app's holographic content lives in its holographic space, and is viewed through one or more holographic cameras which represent different perspectives on the scene.</span></span> <span data-ttu-id="7fcab-128">이제 holographic 공간이 있으므로 holographic 카메라에 대 한 데이터를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-128">Now that you have the holographic space, you can receive data for holographic cameras.</span></span>

<span data-ttu-id="7fcab-129">앱은 백 버퍼 렌더링 대상 뷰와 같이 해당 카메라와 관련 된 리소스를 만들어 **CameraAdded** 이벤트에 응답 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-129">Your app needs to respond to **CameraAdded** events by creating any resources that are specific to that camera, like your back buffer render target view.</span></span> <span data-ttu-id="7fcab-130">앱이 holographic 프레임을 만들기 전에 **Appview:: SetWindow** 에 의해 호출 되는 **DeviceResources:: SetHolographicSpace** 함수에서이 코드를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-130">You can see this code in the **DeviceResources::SetHolographicSpace** function, called by **AppView::SetWindow** before the app creates any holographic frames:</span></span>

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

<span data-ttu-id="7fcab-131">또한 앱은 해당 카메라에 대해 만들어진 리소스를 해제 하 여 **CameraRemoved** 이벤트에 응답 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-131">Your app also needs to respond to **CameraRemoved** events by releasing resources that were created for that camera.</span></span>

<span data-ttu-id="7fcab-132">From **DeviceResources:: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="7fcab-132">From **DeviceResources::SetHolographicSpace**:</span></span>

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

<span data-ttu-id="7fcab-133">Holographic 렌더링을 원활 하 게 진행 하기 위해 이벤트 처리기에서 일부 작업을 완료 하 여 앱이 모든 작업을 렌더링할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-133">The event handlers must complete some work in order to keep holographic rendering flowing smoothly, and so that your app is able to render at all.</span></span> <span data-ttu-id="7fcab-134">세부 정보에 대 한 코드 및 주석을 읽어 보세요. **OnCameraAdded** 및 **OnCameraRemoved** For main 클래스에서 **DeviceResources**에 의해 처리 되는 **m_cameraResources** 방법에 대해 알아볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-134">Read the code and comments for the details: you can look for **OnCameraAdded** and **OnCameraRemoved** in your main class to understand how the **m_cameraResources** map is handled by **DeviceResources**.</span></span>

<span data-ttu-id="7fcab-135">지금은 앱이 holographic 카메라에 대해 알 수 있도록 하는 AppMain 및 설치 프로그램에 중점을 두었습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-135">Right now, we're focused on AppMain and the setup that it does to enable your app to know about holographic cameras.</span></span> <span data-ttu-id="7fcab-136">이와 관련 하 여 다음 두 가지 요구 사항을 기억해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-136">With this in mind, it's important to take note of the following two requirements:</span></span>

1. <span data-ttu-id="7fcab-137">**CameraAdded** 이벤트 처리기의 경우 앱은 비동기적으로 작업 하 여 리소스 만들기를 완료 하 고 새 holographic 카메라에 대 한 자산을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-137">For the **CameraAdded** event handler, the app can work asynchronously to finish creating resources and loading assets for the new holographic camera.</span></span> <span data-ttu-id="7fcab-138">이 작업을 완료 하는 데 둘 이상의 프레임을 사용 하는 앱은 지연을 요청 하 고 비동기적으로 로드 한 후에 지연 시간을 완료 해야 합니다. [PPL 작업](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) 을 사용 하 여 비동기 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-138">Apps that take more than one frame to complete this work should request a deferral, and complete the deferral after loading asynchronously; a [PPL task](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) can be used to do asynchronous work.</span></span> <span data-ttu-id="7fcab-139">앱은 이벤트 처리기를 종료할 때 또는 지연이 완료 될 때 바로 해당 카메라에 렌더링할 준비가 되었는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-139">Your app must ensure that it's ready to render to that camera right away when it exits the event handler, or when it completes the deferral.</span></span> <span data-ttu-id="7fcab-140">이벤트 처리기를 종료 하거나 지연을 완료 하면 앱이 해당 카메라를 포함 하는 holographic 프레임을 받을 준비가 되었음을 시스템에 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-140">Exiting the event handler or completing the deferral tells the system that your app is now ready to receive holographic frames with that camera included.</span></span>

2. <span data-ttu-id="7fcab-141">앱이 **CameraRemoved** 이벤트를 수신 하는 경우 백 버퍼에 대 한 모든 참조를 해제 하 고 바로 함수를 종료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-141">When the app receives a **CameraRemoved** event, it must release all references to the back buffer and exit the function right away.</span></span> <span data-ttu-id="7fcab-142">여기에는 렌더링 대상 뷰 및 [Idxgid 리소스](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)에 대 한 참조를 보유할 수 있는 다른 모든 리소스가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-142">This includes render target views, and any other resource that might hold a reference to the [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource).</span></span> <span data-ttu-id="7fcab-143">앱은 **CameraResources:: ReleaseResourcesForBackBuffer**에 표시 된 것 처럼 백 버퍼를 렌더링 대상으로 연결 하지 있는지도 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-143">The app must also ensure that the back buffer is not attached as a render target, as shown in **CameraResources::ReleaseResourcesForBackBuffer**.</span></span> <span data-ttu-id="7fcab-144">작업 속도를 높이기 위해 앱은 백 버퍼를 해제 한 다음 작업을 시작 하 여 해당 카메라를 종료 하는 데 필요한 다른 작업을 비동기적으로 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-144">To help speed things along, your app can release the back buffer and then launch a task to asynchronously complete any other work that is necessary to tear down that camera.</span></span> <span data-ttu-id="7fcab-145">Holographic 앱 템플릿에는 이러한 용도로 사용할 수 있는 PPL 태스크가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-145">The holographic app template includes a PPL task that you can use for this purpose.</span></span>

>[!NOTE]
><span data-ttu-id="7fcab-146">추가 되거나 제거 된 카메라가 프레임에 표시 되는 시점을 확인 하려는 경우 **HolographicFrame Ad** [카메라](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) 및 [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-146">If you want to determine when an added or removed camera shows up on the frame, use the **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) and [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) properties.</span></span>

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a><span data-ttu-id="7fcab-147">Holographic 콘텐츠에 대 한 참조 프레임 만들기</span><span class="sxs-lookup"><span data-stu-id="7fcab-147">Create a frame of reference for your holographic content</span></span>

<span data-ttu-id="7fcab-148">앱의 콘텐츠는 HolographicSpace에서 렌더링할 [공간 좌표계](coordinate-systems-in-directx.md) 로 배치 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-148">Your app's content must be positioned in a [spatial coordinate system](coordinate-systems-in-directx.md) to be rendered in the HolographicSpace.</span></span> <span data-ttu-id="7fcab-149">시스템은 holograms에 대 한 좌표계를 설정 하는 데 사용할 수 있는 참조의 두 가지 기본 프레임을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-149">The system provides two primary frames of reference which you can use to establish a coordinate system for your holograms.</span></span>

<span data-ttu-id="7fcab-150">Windows Holographic에는 두 가지 종류의 참조 프레임, 장치에 연결 된 참조 프레임 및 장치가 사용자 환경에서 이동할 때 고정 된 상태로 유지 되는 참조 프레임이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-150">There are two kinds of reference frames in Windows Holographic: reference frames attached to the device, and reference frames that remain stationary as the device moves through the user's environment.</span></span> <span data-ttu-id="7fcab-151">Holographic 앱 템플릿은 기본적으로 고정 참조 프레임을 사용 합니다. 이는 세계에서 잠긴 holograms을 렌더링 하는 가장 간단한 방법 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-151">The holographic app template uses a stationary reference frame by default; this is one of the simplest ways to render world-locked holograms.</span></span>

<span data-ttu-id="7fcab-152">고정 참조 프레임은 장치의 현재 위치 근처에서 안정화 되도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-152">Stationary reference frames are designed to stabilize positions near the device's current location.</span></span> <span data-ttu-id="7fcab-153">즉, 장치가 주변의 공간에 대해 더 잘 알게 될 때 장치에서 추가 된 좌표가 사용자 환경에 대해 약간의 편차를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-153">This means that coordinates further from the device are allowed to drift slightly with respect to the user's environment as the device learns more about the space around it.</span></span> <span data-ttu-id="7fcab-154">고정 된 참조 프레임을 만드는 방법에는 두 가지가 있습니다. [공간 단계](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)에서 좌표계를 얻거나 기본 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-154">There are two ways to create a stationary frame of reference: acquire the coordinate system from the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), or use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span> <span data-ttu-id="7fcab-155">몰입 형 헤드셋 용 Windows Mixed Reality 앱을 만드는 경우 권장 되는 시작 지점은 [공간 단계](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage)이며, 플레이어에서 마모 한 모던 헤드셋의 기능에 대 한 정보도 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-155">If you are creating a Windows Mixed Reality app for immersive headsets, the recommended starting point is the [spatial stage](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), which also provides information about the capabilities of the immersive headset worn by the player.</span></span> <span data-ttu-id="7fcab-156">여기서는 기본 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-156">Here, we show how to use the default <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>.</span></span>

<span data-ttu-id="7fcab-157">공간 로케이터는 Windows Mixed Reality 장치를 나타내며 장치의 동작을 추적 하 고 해당 위치를 기준으로 인식할 수 있는 좌표계를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-157">The spatial locator represents the Windows Mixed Reality device, and tracks the motion of the device and provides coordinate systems that can be understood relative to its location.</span></span>

<span data-ttu-id="7fcab-158">**Appmain:: OnHolographicDisplayIsAvailableChanged**:</span><span class="sxs-lookup"><span data-stu-id="7fcab-158">From **AppMain::OnHolographicDisplayIsAvailableChanged**:</span></span>

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

<span data-ttu-id="7fcab-159">앱이 시작 될 때 고정 된 참조 프레임을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-159">Create the stationary reference frame once when the app is launched.</span></span> <span data-ttu-id="7fcab-160">이는 응용 프로그램이 시작 될 때 장치의 위치에 원점이 배치 된 상태에서 세계 좌표계를 정의 하는 것과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-160">This is analogous to defining a world coordinate system, with the origin placed at the device's position when the app is launched.</span></span> <span data-ttu-id="7fcab-161">이 참조 프레임은 장치와 함께 이동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-161">This reference frame doesn't move with the device.</span></span>

<span data-ttu-id="7fcab-162">**Appmain:: SetHolographicSpace**:</span><span class="sxs-lookup"><span data-stu-id="7fcab-162">From **AppMain::SetHolographicSpace**:</span></span>

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

<span data-ttu-id="7fcab-163">모든 참조 프레임은 중력으로 정렬 되어 있습니다. 즉, y 축은 사용자 환경에 대해 "up"을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-163">All reference frames are gravity aligned, meaning that the y axis points "up" with respect to the user's environment.</span></span> <span data-ttu-id="7fcab-164">Windows에서는 "오른손" 좌표계를 사용 하기 때문에 참조 프레임이 만들어질 때-z 축의 방향이 장치를 향한 "전달" 방향과 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-164">Since Windows uses "right-handed" coordinate systems, the direction of the –z axis coincides with the "forward" direction the device is facing when the reference frame is created.</span></span>

>[!NOTE]
><span data-ttu-id="7fcab-165">앱에서 개별 holograms를 정확 하 게 배치 해야 하는 경우 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> 를 사용 하 여 개별 홀로그램을 실제 세계의 위치에 고정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-165">When your app requires precise placement of individual holograms, use a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> to anchor the individual hologram to a position in the real world.</span></span> <span data-ttu-id="7fcab-166">예를 들어 사용자가 특별 한 관심이 있는 지점을 나타내는 경우 공간 앵커를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-166">For example, use a spatial anchor when the user indicates a point to be of special interest.</span></span> <span data-ttu-id="7fcab-167">앵커 위치는 드리프트 하지 않지만 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-167">Anchor positions do not drift, but they can be adjusted.</span></span> <span data-ttu-id="7fcab-168">기본적으로, 앵커를 조정 하면 수정이 발생 한 후 다음 몇 개의 프레임에서 위치를 쉽게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-168">By default, when an anchor is adjusted, it eases its position into place over the next several frames after the correction has occurred.</span></span> <span data-ttu-id="7fcab-169">응용 프로그램에 따라이 경우 다른 방식으로 조정을 처리 하는 것이 좋습니다 (예: 홀로그램을 볼 수 없을 때까지 지연).</span><span class="sxs-lookup"><span data-stu-id="7fcab-169">Depending on your application, when this occurs you may want to handle the adjustment in a different manner (e.g. by deferring it until the hologram is out of view).</span></span> <span data-ttu-id="7fcab-170"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> 속성 및 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> 이벤트를 통해 이러한 사용자 지정을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-170">The <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> property and <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> events enable these customizations.</span></span>

## <a name="respond-to-locatability-changed-events"></a><span data-ttu-id="7fcab-171">Locatability 변경 이벤트에 응답</span><span class="sxs-lookup"><span data-stu-id="7fcab-171">Respond to locatability changed events</span></span>

<span data-ttu-id="7fcab-172">세계에서 잠긴 holograms를 렌더링 하려면 장치에서 장치를 직접 찾을 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-172">Rendering world-locked holograms requires the device to be able to locate itself in the world.</span></span> <span data-ttu-id="7fcab-173">이는 환경적 조건으로 인해 항상 가능 하지는 않을 수 있으며,이 경우 사용자는 추적 중단을 시각적으로 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-173">This may not always be possible due to environmental conditions, and if so, the user may expect a visual indication of the tracking interruption.</span></span> <span data-ttu-id="7fcab-174">이 시각적 표시는 전 세계에 고정 되지 않고 장치에 연결 된 참조 프레임을 사용 하 여 렌더링 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-174">This visual indication must be rendered using reference frames attached to the device, instead of stationary to the world.</span></span>

<span data-ttu-id="7fcab-175">어떤 이유로 든 추적이 중단 되 면 앱에서 알림이 전달 되도록 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-175">You app can request to be notified if tracking is interrupted for any reason.</span></span> <span data-ttu-id="7fcab-176">LocatabilityChanged 이벤트에 등록 하 여 장치의 자체 검색 기능이 변경 되는 경우를 감지 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-176">Register for the LocatabilityChanged event to detect when the device's ability to locate itself in the world changes.</span></span> <span data-ttu-id="7fcab-177">**Appmain:: SetHolographicSpace:**</span><span class="sxs-lookup"><span data-stu-id="7fcab-177">From **AppMain::SetHolographicSpace:**</span></span>

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

<span data-ttu-id="7fcab-178">그런 다음이 이벤트를 사용 하 여 holograms가 전 세계에 고정 될 수 없는 시기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fcab-178">Then use this event to determine when holograms cannot be rendered stationary to the world.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fcab-179">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7fcab-179">See also</span></span>
* [<span data-ttu-id="7fcab-180">DirectX의 렌더링</span><span class="sxs-lookup"><span data-stu-id="7fcab-180">Rendering in DirectX</span></span>](rendering-in-directx.md)
* [<span data-ttu-id="7fcab-181">DirectX의 좌표계</span><span class="sxs-lookup"><span data-stu-id="7fcab-181">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
