---
title: Holographic 원격 추가
description: 네트워크를 통해는 HoloLens에 홀로그램 렌더링할 Holographic Remoting을 사용 하는 방법에 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 렌더링, HoloLens, 원격 홀로그램 네트워크, 원격 렌더링, holographic remoting, 홀로그램
ms.openlocfilehash: 4726c6af43fe1b89fc8298e459a1af9dfa5fc667
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605127"
---
# <a name="add-holographic-remoting"></a>Holographic 원격 추가

> [!NOTE]
> HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.

## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Holographic 원격 데스크톱 또는 UWP 앱 추가

이 페이지에서는 Holographic 원격 데스크톱 또는 UWP 앱에 추가 하는 방법을 설명 합니다.

Holographic 원격 데스크톱 PC 또는 Xbox One 많은 시스템 리소스에 대 한 액세스를 허용 하 고 통합할 수 원격와 같은 UWP 장치 호스트 holographic 콘텐츠로 HoloLens를 대상으로 앱을 사용 하면 [몰입형뷰](app-views.md) 기존 데스크톱 PC 소프트웨어에 있습니다. 원격 호스트 앱을 가상 몰입 형 뷰에서 콘텐츠를 렌더링 하며 콘텐츠 프레임 HoloLens로 다시 스트리밍합니다는 HoloLens에서 입력된 데이터 스트림을 받는 합니다. 표준 Wi-fi를 사용 하 여 연결 됩니다. 원격을 사용 하려면 NuGet 패키지를 사용 하 여 holographic 원격 데스크톱 또는 UWP 앱에 추가할 한 연결을 처리 하는 몰입 형 뷰를 렌더링 하는 코드를 작성 합니다. 도우미 라이브러리는 장치 연결을 처리 하는 작업을 간소화 하는 코드 샘플에 포함 됩니다.

일반적인 원격 연결의 대기 시간이 50ms 하위 해야 합니다. 플레이어 앱 실시간 대기 시간을 보고할 수 있습니다.

>[!NOTE]
>이 문서의 코드 조각 사용에 현재 방법을 보여 줍니다 C++/CX 대신 C + + 17 규격 C++/WinRT에 사용 되는 [ C++ holographic 프로젝트 템플릿을](creating-a-holographic-directx-project.md).  개념에 대 한 동일는 C++코드를 변환 해야 하지만 /WinRT 프로젝트입니다.

### <a name="get-the-remoting-nuget-packages"></a>원격 NuGet 패키지 가져오기

Holographic remoting에 대 한 NuGet 패키지를 다운로드 하려면 다음이 단계를 수행 하 고 프로젝트에서 참조를 추가 합니다.
1. Visual Studio에서 프로젝트를 이동 합니다.
2. 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 선택 **NuGet 패키지 관리...**
3. 표시 되는 패널에서 클릭 **찾아보기** 고 "원격 Holographic"를 검색 합니다.
4. 선택 **Microsoft.Holographic.Remoting** 누릅니다 **설치**합니다.
5. 경우는 **미리 보기** 대화 상자가 나타나면 클릭 **확인**합니다.
6. 다음 대화 상자가 나타나면 사용권 계약 됩니다. 클릭할 **동의** 라이선스 계약에 동의 합니다.

### <a name="create-the-holographicstreamerhelpers"></a>HolographicStreamerHelpers 만들기

먼저 HolographicStreamerHelpers 인스턴스에 필요합니다. 원격 처리 될 하는 클래스에 추가 합니다.

```
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

연결 상태를 추적 해야 합니다. 미리 보기를 렌더링 하려는 경우 텍스처를 복사 해야 합니다. 또한 몇 가지 연결 상태 잠금처럼, HoloLens의 IP 주소를 저장 하는 방법이 필요 하 고 등입니다.

```
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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>HoloLens에 연결한 HolographicStreamerHelpers 초기화

HoloLens 장치에 연결 하려면 HolographicStreamerHelpers 인스턴스의 만들고 대상 IP 주소에 연결 합니다. Holographic 원격 라이브러리 예상 인코더 및 디코더 해결 정확 하 게 일치 하기 때문에 HoloLens 표시 너비와 높이 맞게 비디오 프레임 크기를 설정 해야 합니다.

```
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

장치 연결은 비동기적입니다. Connect에 대 한 이벤트 처리기를 제공 하 여 앱 요구 사항을 끊고 프레임 이벤트를 전송 합니다.

OnConnected 이벤트 UI를 업데이트할 수 있습니다, 그리고 렌더링, 시작 및 등 데스크톱 코드 샘플에서는 "연결된" 메시지를 사용 하 여 창 제목을 업데이트 합니다.

```
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

다시, UI 업데이트 등에 OnDisconnected 이벤트를 처리할 수 있습니다. 이 예제에서는 일시적인 오류가 발생 하는 경우 다시 했습니다.

```
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

Remoting 구성 요소는 프레임을 보낼 준비가 되 면 앱 복사본을 SendFrameEvent에서 시키는 기회가 제공 됩니다. 여기에서는 미리 보기 창에 표시할 수 있도록 스왑 체인에 프레임을 복사 합니다.

```
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

### <a name="render-holographic-content"></a>Holographic 콘텐츠를 렌더링 합니다.

콘텐츠를 렌더링 하 여 데스크톱 또는 UWP 앱 내에서 가상 IFrameworkView 설정 및 remoting에서 holographic 프레임 처리 원격 서비스를 사용 합니다. Windows Holographic Api를 모두 사용 하 여가이 보기에서 동일한 방식으로 약간 다르게 설정 됩니다.

를 만드는 대신 해당 직접 HolographicRemotingHelpers 클래스에서 holographic 공간 및 음성 구성 요소를 가져옵니다.

```
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

실행 메서드 내에서 update 루프를 사용 하는 대신 눈금 업데이트 데스크톱 또는 UWP 앱의 기본 루프를 제공할 수 있습니다. 따라서, 데스크톱 또는 UWP 앱의 메시지 처리를 제어 합니다.

```
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Holographic 앱 보기의 Tick() 메서드 업데이트, 그리기, 현재 루프의 반복 하나를 완료합니다.

```
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

Holographic 앱 보기 업데이트, 렌더링 및 있는 루프 이므로 정확히 동일한 HoloLens-에서 실행할 때 데스크톱 PC에서 훨씬 더 많이 시스템 리소스에 대 한 액세스를 포함 한다는 점을 제외 합니다. 수 많은 자세한 삼각형을 렌더링, 자세한 그리기 전달을 자세한 물리학 및 x64 사용 하 여 필요한 콘텐츠를 로드 하는 프로세스 보다 2GB의 RAM 수행 합니다.

### <a name="disconnect-and-end-the-remote-session"></a>연결을 끊고 원격 세션을 종료

연결 끊기-예를 들어, 사용자 연결을 끊을-UI 단추를 클릭할 때 Disconnect() HolographicStreamerHelpers에서 호출 하 고 개체를 해제 합니다.

```
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

## <a name="get-the-remoting-player"></a>원격 플레이어 가져오기

Windows Holographic 원격 플레이어에 연결할 앱을 원격 호스트에 대 한 끝점으로 Windows 앱 스토어에서 제공 됩니다. Windows Holographic 원격 플레이어를 가져오려면 원격에 대 한 검색에 HoloLens에서 Windows 앱 스토어를 방문 하 고 앱을 다운로드 합니다. 원격 플레이어 앱을 호스트 하는 원격 디버깅할 때 유용할 수 있는 통계를 화면에 표시 하는 기능을 포함 합니다.

## <a name="notes-and-resources"></a>정보 및 리소스

Holographic 앱 보기 holographic 공간 초기화를 사용 해야 하는 Direct3D 장치를 사용 하 여 앱을 제공 하는 방법이 필요 합니다. 복사 및 미리 보기 프레임을 표시할 앱이 Direct3D 장치를 사용 해야 합니다.

```
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**코드 샘플:** 전체 Holographic Remoting 코드 샘플은 원격 데스크톱 Win32, UWP DirectX 및 XAML 사용 하 여 UWP 프로젝트를 원격 호스트와 호환 되는 holographic 응용 프로그램 보기를 포함 하는 사용할 수 있습니다. 이 가져오려면 여기로 이동 합니다.
* [원격 연결을 위해 Windows Holographic 코드 샘플](https://github.com/Microsoft/HoloLensCompanionKit/)

**디버깅 참고:** Holographic 원격 라이브러리 첫째 예외를 throw 할 수 있습니다. 이러한 예외 디버깅 시 활성 상태인 Visual Studio 예외 설정에 따라 세션에서 볼 수 있습니다. 이러한 예외 Holographic 원격 라이브러리에서 내부적으로 발생 하 고 무시할 수 있습니다.
