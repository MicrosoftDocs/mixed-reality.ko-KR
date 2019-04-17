---
title: HolographicSpace 가져오기
description: HolographicSpace API, holographic 렌더링 및 공간 입력에 대 한 핵심 개념을 설명합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HolographicSpace CoreWindow를 공간 입력 하 고, 렌더링, 스왑 체인, holographic 프레임, 업데이트 루프, 게임 루프, 참조 프레임, locatability, 샘플 코드, 연습
ms.openlocfilehash: 828352203b20ec38275796b3f172e7ecc5df3f00
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605082"
---
# <a name="getting-a-holographicspace"></a>HolographicSpace 가져오기

합니다 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> 클래스는 holographic 세계로 포털입니다. 몰입 형 렌더링을 제어, 카메라 데이터를 제공 하 고 공간 추론 Api에 대 한 액세스를 제공 합니다. UWP 앱에 대 한 만들어집니다 <a href="https://docs.microsoft.com/api/windows.ui.core.corewindow" target="_blank">CoreWindow</a> 또는 Win32 앱의 HWND입니다.

## <a name="set-up-the-holographic-space"></a>Holographic 공간 설정

Windows Mixed Reality 앱을 만드는 첫 번째 단계는 holographic 공간 개체를 만들기. 기존 Windows 앱에 해당 응용 프로그램 보기 코어 기간에 대해 생성 하는 Direct3D 스왑 체인 렌더링 합니다. 이 스왑 체인 holographic UI에서 슬레이트를 표시 됩니다. 응용 프로그램 보기를 2D 슬레이트 대신 holographic 하려면 스왑 체인 대신 해당 코어 창에 대 한 holographic 공간을 만듭니다. 이 holographic 공백으로 만들어진 holographic 프레임이 제시 케이블의 앱을 전체 화면 렌더링 모드에 넣습니다.

에 대 한를 **UWP 앱** [에서 시작 합니다 *Holographic DirectX 11 앱 (유니버설 Windows) 템플릿을*](creating-a-holographic-directx-project.md),이 코드에 대 한 표시를 **SetWindow** AppView.cpp에서 메서드를 제공 합니다.

```cpp
m_holographicSpace = HolographicSpace::CreateForCoreWindow(window);
```

에 대 한는 **Win32 응용 프로그램** [에서 시작 합니다 *BasicHologram* Win32 샘플](creating-a-holographic-directx-project.md#creating-a-win32-project), 살펴봅니다 **App::CreateWindowAndHolographicSpace** 에 대 한는 HWND를 만들고 연결을 만들어 몰입 형 HWND를 변환 하는 방법의 예제 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>:
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

이제는 UWP CoreWindow 또는 Win32 HWND를 HolographicSpace 얻어진, holographic 카메라를 처리 하 고, 좌표계를 만들고, holographic 렌더링을 수행 하는 HolographicSpace 사용 합니다. 현재 holographic 공간 DirectX 템플릿에서 여러 위치에서 사용 됩니다.
* 합니다 **DeviceResources** 클래스 HolographicSpace 개체에서 Direct3D 장치를 만들기 위해 일부 정보를 가져올 해야 합니다. Holographic 디스플레이 연결 된 DXGI 어댑터 ID입니다. 합니다 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> 클래스를 만들고 각 holographic 카메라에 대 한 백 버퍼와 같은 장치 기반 리소스를 관리 앱의 Direct3D 11 장치를 사용 합니다. 내부에서 수행이 함수에 관심이 있다면 DeviceResources.cpp에서 찾을 수 있습니다.
* 함수 **DeviceResources::InitializeUsingHolographicSpace** 어댑터를 가져오는 방법을 보여 줍니다 없는 기본 어댑터를 지정 하는 기본 어댑터를 선택 하는 방법과-LUID를 조회 하 여 합니다.
* 앱의 기본 클래스에서 holographic 공간을 사용 하 여 **AppView::SetWindow** 하거나 **App::CreateWindowAndHolographicSpace** 업데이트 및 렌더링 합니다.

>[!NOTE]
>아래 섹션에 템플릿에서 함수 이름을 언급 하는 동안 같은 **AppView::SetWindow** 는 가정 holographic UWP 앱 템플릿에서 시작을 표시 하는 코드 조각 UWP 및 Win32 앱 간에 동일 하 게 적용 됩니다.

설치에 자세히 알아봅니다 다음으로 프로세스 **SetHolographicSpace** 담당 AppMain 클래스에서.

## <a name="subscribe-to-camera-events-create-and-remove-camera-resources"></a>카메라 이벤트를 구독할 만들 있고 카메라 리소스 제거

응용 프로그램의 holographic 콘텐츠 holographic 해당 공간에 있으며은 하나 이상의 holographic 카메라 장면에서 다양 한 측면을 나타내는 품질이. 이제 홀로그램 공간 했으므로 holographic 카메라에 대 한 데이터를 받을 수 있습니다.

앱에 응답 해야 **CameraAdded** 는 카메라, 백 버퍼의 렌더링 대상 뷰 같은 만들어 모든 리소스는 이벤트와 관련이 있습니다. 이 코드에서 볼 수 있습니다 합니다 **DeviceResources::SetHolographicSpace** 함수를 호출한 **AppView::SetWindow** 앱에서 모든 holographic 프레임을 만들기 전에:

```cpp
m_cameraAddedToken = m_holographicSpace.CameraAdded(
    std::bind(&AppMain::OnCameraAdded, this, _1, _2));
```

앱에 응답 해야 **CameraRemoved** 해당 카메라에 대해 생성 된 리소스를 해제 하 여 이벤트입니다.

**DeviceResources::SetHolographicSpace**:

```cpp
m_cameraRemovedToken = m_holographicSpace.CameraRemoved(
    std::bind(&AppMain::OnCameraRemoved, this, _1, _2));
```

이벤트 처리기 흐름을 원활 하 게 holographic 렌더링을 유지 하기 위해 몇 가지 작업을 완료 해야 앱이 전혀 렌더링 될 수 있도록 하 고 있습니다. 코드 및 세부 정보에 대 한 설명: 찾을 수 있습니다 **OnCameraAdded** 하 고 **OnCameraRemoved** 이해 하려면 기본 클래스에서 방법을 **m_cameraResources** 맵은 에 의해 처리 **DeviceResources**합니다.

현재, AppMain 및 holographic 카메라에 알아야 할 앱을 설정 하는 설치를 위해 노력 합니다. 이 점을 염두에서를 사용 하 여 다음 두 가지 요구 사항 확인 하 려 것:

1. 에 대 한 합니다 **CameraAdded** 이벤트 처리기에서 앱을 사용할 수 비동기적으로 리소스를 만들고 새 holographic 카메라에 대 한 자산 로드를 완료 합니다. 이 작업을 완료 하려면 둘 이상의 프레임을 사용 하는 앱 요청을 지연을 비동기적으로 로드 한 후 지연을 완료합니다 [PPL 작업](https://docs.microsoft.com/cpp/parallel/concrt/parallel-patterns-library-ppl) 비동기 작업을 수행할 수 있습니다. 앱은 이벤트 처리기를 종료 되 면 또는 지연을 완료 되 면 바로 해당 카메라에 렌더링할 준비가 되었는지 확인 해야 합니다. 이벤트 처리기를 종료 또는 완료 지연을 시스템에 앱을 포함 하는 카메라를 사용 하 여 holographic 프레임을 받을 준비가 이제 인지 알려 줍니다.

2. 앱을 수신 하는 경우는 **CameraRemoved** 이벤트 함수 번 마우스 오른쪽 단추로 백 버퍼 및 종료에 대 한 모든 참조를 해제 해야 합니다. 렌더링 대상 뷰 및 기타 리소스에 대 한 참조를 보유할 수 있는 포함 된 [IDXGIResource](https://docs.microsoft.com/windows/desktop/api/dxgi/nn-dxgi-idxgiresource)합니다. 앱도 확인 해야 백 버퍼 렌더링 대상으로 연결 되어 있지 않은지에 표시 된 대로 **CameraResources::ReleaseResourcesForBackBuffer**합니다. 함께 작업 속도 위해 앱 백 버퍼를 해제 하 고 시작 작업을 비동기적으로 카메라를 종료 하는 데 필요한 다른 모든 작업을 완료할 수 있습니다. Holographic 앱 템플릿을이 용도로 사용할 수 있는 PPL 작업을 포함 합니다.

>[!NOTE]
>표시 되 면 추가 또는 제거 카메라를 사용 하 여 프레임에서 확인 하려는 경우는 **HolographicFrame** [AddedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.addedcameras) 하 고 [RemovedCameras](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.removedcameras) 속성입니다.

## <a name="create-a-frame-of-reference-for-your-holographic-content"></a>Holographic 콘텐츠에 대 한 참조 프레임 만들기

응용 프로그램의 콘텐츠를 배치 되어야 합니다는 [공간 좌표계](coordinate-systems-in-directx.md) 는 HolographicSpace에서 렌더링할 합니다. 시스템에 제공에 대 한 좌표 시스템을 설정 하는 데 사용할 수 있는 두 개의 주 프레임의 참조를 제공 합니다.

Windows Holographic에서 참조 프레임의 두 종류가 있습니다: 장치에 연결 된 프레임 및 장치 사용자의 환경을 통해 이동함에 따라 고정 되어 참조 프레임을 참조 합니다. Holographic 앱 템플릿은 기본적으로 고정 참조 프레임을 사용합니다. 이 세계 잠긴 홀로그램을 렌더링 하는 가장 간단한 방법 중 하나입니다.

고정 참조 프레임은 장치의 현재 위치 근처 위치를 안정화 하도록 설계 되었습니다. 즉, 장치 멀리 좌표 장치 주위 공간에 대 한 자세한 정보를 학습 하는 대로 사용자의 환경에 대해 약간 드리프트 수 있습니다. 두 가지 방법으로 고정 참조 프레임을 만들려면:에서 좌표 시스템을 획득 합니다 [공간 단계](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), 하거나 기본값을 사용 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>합니다. 몰입 형 헤드셋에 대 한 Windows Mixed Reality 앱을 만드는 경우 권장 되는 시작점은는 [공간 단계](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-a-spatial-stage), 또한 플레이어 착용 몰입 형 헤드셋의 기능에 대 한 정보를 제공 하는 합니다. 여기에서 기본값을 사용 하는 방법을 보여 줍니다 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>합니다.

공간 로케이터 Windows Mixed Reality 장치를 나타내는 장치 동작을 추적 및 해당 위치를 기준으로 인식할 수 있는 좌표 시스템을 제공 합니다.

**AppMain::OnHolographicDisplayIsAvailableChanged**:

```cpp
spatialLocator = SpatialLocator::GetDefault();
```

앱을 실행 하는 경우 고정 참조 프레임을 한 번 만듭니다. 앱을 실행 하는 경우 장치의 위치에 배치 하 여 원본과 세계 좌표 시스템을 정의 하는 것과 비슷합니다. 이 참조 프레임은 장치를 사용 하 여 이동 하지 않습니다.

**AppMain::SetHolographicSpace**:

```cpp
m_stationaryReferenceFrame =
    m_spatialLocator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```

모든 참조 프레임은 사용자 환경 관련 하 여 y 축이 "up" 가리키는지 의미 정렬 중력입니다. Windows "오른손" 좌표계를 사용 하므로 – z 축 방향으로 참조 프레임을 만들 때 장치는 연결 "forward" 방향을 사용 하 여 일치 합니다.

>[!NOTE]
>앱에 필요한 개별 홀로그램의 정확한 위치를 사용 하 여는 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a> 실제에서 위치로 개별 홀로그램을 고정 합니다. 예를 들어, 사용자는 특별 한 관심 지점을 나타내는 경우 공간 앵커를 사용 합니다. 앵커 위치 드리프트 하지 않습니다, 하지만 조정할 수 있습니다. 기본적으로 앵커를 조정 하는 경우이 용이 하 게 해당 위치에 다음 여러 프레임을 통해 수정 사항이 발생 한 후입니다. 응용 프로그램에 따라이 발생 하는 경우 좋습니다 조정 다른 방식으로 (예: 하 여 처리 하 여 홀로그램 보기에서 될 때까지 연기). 합니다 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystem" target="_blank">RawCoordinateSystem</a> 속성 및 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted" target="_blank">RawCoordinateSystemAdjusted</a> 이벤트를 통해 이러한 사용자 지정 합니다.

## <a name="respond-to-locatability-changed-events"></a>Locatability 변경 이벤트에 응답

전 세계 잠긴 홀로그램 렌더링 자체 세계에서 찾을 수 있으려면 장치가 필요 합니다. 이 항상 못할 환경 조건으로 인해 하 고 그렇다면 사용자 수 예상 하는 추적 작업이 중단 되는 시각적으로 표시 합니다. 이 시각적 표시는 전 세계에 고정 하는 대신 장치에 연결 하는 참조 프레임을 사용 하 여 렌더링 되어야 합니다.

앱이 어떤 이유로 중단 되는 추적 하는 경우 알림을 받을 요청할 수 있습니다. 자체 세계 변경 내용을 찾으려고 장치의 기능을 탐지 LocatabilityChanged 이벤트에 등록 합니다. **AppMain::SetHolographicSpace:**

```cpp
m_locatabilityChangedToken = m_spatialLocator.LocatabilityChanged(
    std::bind(&HolographicApp6Main::OnLocatabilityChanged, this, _1, _2));
```

홀로그램을 전 세계를 고정으로 렌더링할 수 없으면 확인 하려면이 이벤트를 사용 합니다.

## <a name="see-also"></a>참조
* [DirectX의 렌더링](rendering-in-directx.md)
* [DirectX의 좌표계](coordinate-systems-in-directx.md)
