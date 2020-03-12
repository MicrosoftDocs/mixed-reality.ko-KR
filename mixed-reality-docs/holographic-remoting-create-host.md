---
title: Holographic Remoting 원격 앱 작성
description: 원격 컴퓨터에서 렌더링 되는 Holographic Remoting 원격 앱 원격 콘텐츠를 만들면 HoloLens 2로 스트리밍할 수 있습니다. 이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다.
author: FlorianBagarMicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: 76e37499fd32a82e6846c6c7cac1a292ef6b553a
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/11/2020
ms.locfileid: "79092304"
---
# <a name="writing-a-holographic-remoting-remote-app"></a>Holographic Remoting 원격 앱 작성

>[!IMPORTANT]
>이 문서에서는 HoloLens 2 용 원격 응용 프로그램을 만드는 방법을 설명 합니다. HoloLens 용 원격 응용 프로그램 **(첫 번째 gen)** 은 NuGet 패키지 **버전 1.x를 사용**해야 합니다. 즉, HoloLens 2 용으로 작성 된 원격 응용 프로그램은 HoloLens 1과 호환 되지 않으며 그 반대의 경우도 마찬가지입니다. HoloLens 1에 대 한 설명서는 [여기](add-holographic-remoting.md)에서 찾을 수 있습니다.

Holographic Remoting 원격 앱을 만들면 원격 컴퓨터에서 렌더링 되는 원격 콘텐츠를 HoloLens 2로 스트리밍할 수 있습니다. 이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다. 이 페이지 및 작업 프로젝트의 모든 코드는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.

Holographic remoting을 사용 하면 앱이 데스크톱 PC 또는 UWP 장치 (예: Xbox One)에서 렌더링 된 Holographic 콘텐츠를 사용 하 여 HoloLens 2를 대상으로 지정할 수 있으며, 더 많은 시스템 리소스에 대 한 액세스를 허용 하 고 원격 [몰입 형 보기](app-views.md) 를 기존 데스크톱 PC 소프트웨어에 통합할 수 있습니다. 원격 앱은 HoloLens 2에서 입력 데이터 스트림을 받고, 가상 몰입 형 보기에서 콘텐츠를 렌더링 하 고, 콘텐츠 프레임을 HoloLens 2로 다시 스트리밍합니다. 연결은 표준 Wi-fi를 사용 하 여 수행 됩니다. Holographic Remoting은 NuGet 패킷을 통해 데스크톱 또는 UWP 앱에 추가 됩니다. 연결을 처리 하 고 몰입 형 보기에서 렌더링 하는 추가 코드가 필요 합니다.

일반적인 원격 연결의 경우 대기 시간은 50 밀리초로 낮습니다. 플레이어 앱은 실시간으로 대기 시간을 보고할 수 있습니다.

## <a name="prerequisites"></a>필수 조건

좋은 출발점은 Windows Mixed Reality API를 대상으로 하는 작동 하는 DirectX 기반 데스크톱 또는 UWP 앱입니다. 자세한 내용은 [DirectX 개발 개요](directx-development-overview.md)를 참조 하세요. Holographic 프로젝트 템플릿이 좋은 출발점입니다. [ C++ ](creating-a-holographic-directx-project.md)

>[!IMPORTANT]
>Holographic 원격을 사용 하는 모든 앱은 [다중 스레드 아파트](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)를 사용 하도록 작성 되어야 합니다. [단일 스레드 아파트](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) 를 사용 하는 것은 지원 되지만, 재생 하는 동안 일지 성능이 저하 될 수 있습니다. /Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) 사용 하는 경우 다중 스레드 아파트는 기본값입니다.



## <a name="get-the-holographic-remoting-nuget-package"></a>Holographic 원격 NuGet 패키지 가져오기

Visual Studio에서 프로젝트에 NuGet 패키지를 추가 하려면 다음 단계를 수행 해야 합니다.
1. Visual Studio에서 프로젝트를 엽니다.
2. 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리 ...** 를 선택 합니다.
3. 표시 되는 패널에서 **찾아보기** 를 클릭 한 다음 "Holographic Remoting"을 검색 합니다.
4. **Holographic**를 선택 하 고 최신 **2.x 버전을** 선택 하 고 **설치**를 클릭 합니다.
5. **미리 보기** 대화 상자가 표시 되 면 **확인**을 클릭 합니다.
6. 표시 되는 다음 대화 상자는 사용권 계약입니다. **동의** 함을 클릭 하 여 사용권 계약에 동의 합니다.

>[!NOTE]
>HoloLens 1을 대상으로 하는 개발자에 게는 NuGet 패키지의 버전 **1. x. x** 를 계속 사용할 수 있습니다. 자세한 내용은 [Holographic 원격 추가 (HoloLens (첫 번째 gen))](add-holographic-remoting.md)를 참조 하세요.

## <a name="create-the-remote-context"></a>원격 컨텍스트 만들기

첫 번째 단계로 응용 프로그램은 원격 컨텍스트를 만들어야 합니다.

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
>Holographic Remoting은 원격 특정 런타임을 사용 하 여 Windows의 일부인 Windows Mixed Reality 런타임을 대체 하는 방식으로 작동 합니다. 이 작업은 원격 컨텍스트를 만드는 동안 수행 됩니다. 이러한 이유로 원격 컨텍스트를 만들기 전에 Windows Mixed Reality API를 호출 하면 예기치 않은 동작이 발생할 수 있습니다. 혼합 현실 API와의 상호 작용 전에 가능한 한 빨리 원격 컨텍스트를 만드는 것이 좋습니다. 이후에 만들어지거나 검색 된 개체를 사용 하 여 CreateRemoteContext를 호출 하기 전에 Windows Mixed Reality API를 통해 만들어지거나 검색 된 개체를 혼합 하지 마세요.

다음으로 holographic 공간을 만들어야 합니다. CoreWindow 지정은 필요 하지 않습니다. CoreWindow 없는 데스크톱 앱은 단순히 ```nullptr```전달할 수 있습니다.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>장치에 연결

원격 앱이 콘텐츠를 렌더링할 준비가 되 면 장치에 대 한 연결을 설정할 수 있습니다.

다음 두 가지 방법 중 하나로 연결을 수행할 수 있습니다.
1) 원격 앱은 장치에서 실행 중인 플레이어에 연결 합니다.
2) 장치에서 실행 되는 플레이어가 원격 앱에 연결 합니다.

원격 앱에서 HoloLens 2로의 연결을 설정 하려면 호스트 이름 및 포트를 지정 하는 원격 컨텍스트에서 ```Connect``` 메서드를 호출 합니다. Holographic Remoting 플레이어에서 사용 하는 포트는 **8265**입니다.

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
>모든 C++/WINRT API ```Connect```는 처리 해야 하는 WinRT:: hresult_error을 throw 할 수 있습니다.

>[!TIP]
>[ C++/Winrt](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) 언어 프로젝션을 사용 하지 않으려면 Holographic Remoting NuGet 패키지 내에 있는 파일 ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` 포함 될 수 있습니다. 여기에는 기본 COM 인터페이스의 선언이 포함 됩니다. 그러나 C++/winrt를 사용 하는 것이 좋습니다.

원격 앱에서 들어오는 연결을 수신 하는 작업은 ```Listen``` 메서드를 호출 하 여 수행할 수 있습니다. 이 호출 중에 핸드셰이크 포트와 전송 포트를 모두 지정할 수 있습니다. 핸드셰이크 포트는 초기 핸드셰이크에 사용 됩니다. 그런 다음 데이터는 전송 포트를 통해 전송 됩니다. 기본적으로 **8265** 및 **8266** 이 사용 됩니다.

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
>NuGet 패키지 내의 ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` Holographic Remoting에서 노출 하는 API에 대 한 자세한 설명서를 포함 합니다.

## <a name="handling-remoting-specific-events"></a>원격 특정 이벤트 처리

원격 컨텍스트는 연결 상태를 모니터링 하는 데 중요 한 세 개의 이벤트를 노출 합니다.
1) OnConnected: 장치에 대 한 연결이 성공적으로 설정 되 면 트리거됩니다.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnected: 설정 된 연결이 닫히거나 연결을 설정할 수 없는 경우 트리거됩니다.
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
3) OnListening: 들어오는 연결에 대 한 수신 대기를 시작 합니다.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

또한 원격 컨텍스트의 ```ConnectionState``` 속성을 사용 하 여 연결 상태를 쿼리할 수 있습니다.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>음성 이벤트 처리

원격 음성 인터페이스를 사용 하 여 HoloLens 2에 음성 트리거를 등록 하 고 원격 응용 프로그램에 원격으로 연결할 수 있습니다.

이 추가 멤버는 원격 음성의 상태를 추적 하는 데 필요 합니다.

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

먼저 원격 음성 인터페이스를 검색 해야 합니다.

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

비동기 도우미 메서드를 사용 하 여 원격 음성을 초기화할 수 있습니다. 초기화는 상당한 시간이 걸릴 수 있으므로이 작업은 비동기적으로 수행 해야 합니다. [/WinRT를 사용한 C++동시성 및 비동기 작업](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) 은/winrt. 사용 하 여 C++비동기 함수를 작성 하는 방법을 설명 합니다.

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

인식 될 구를 지정 하는 방법에는 두 가지가 있습니다.
1) 음성 문법 xml 파일 내의 사양입니다. 자세한 내용은 [기본 XML 문법을 만드는 방법](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) 을 참조 하세요.
2) ```ApplyParameters```하려면 사전 벡터 내부에 전달 하 여를 지정 합니다.

OnRecognizedSpeech 콜백 내에서 음성 이벤트를 처리할 수 있습니다.

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

## <a name="preview-streamed-content-locally"></a>스트리밍 콘텐츠를 로컬로 미리 봅니다.

장치에 전송 되는 원격 앱에 동일한 콘텐츠를 표시 하려면 원격 컨텍스트의 ```OnSendFrame``` 이벤트를 사용할 수 있습니다. Holographic 원격 라이브러리가 현재 프레임을 원격 장치로 보낼 때마다 ```OnSendFrame``` 이벤트가 트리거됩니다. 이는 콘텐츠를 사용 하 여 데스크톱 또는 UWP 창으로 array.blit 하는 데 가장 적합 한 시간입니다.

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

## <a name="depth-reprojection"></a>깊이 예측

[2.1.0](holographic-remoting-version-history.md#v2.1.0)버전부터 Holographic Remoting은 [깊이 재 프로젝션을](hologram-stability.md#reprojection)지원 합니다. 이를 위해서는 색 버퍼 외에도 원격 응용 프로그램에서 HoloLens 2로 깊이 버퍼를 스트리밍할 수 있습니다. 기본적으로 깊이 버퍼는 색 버퍼의 해상도 절반으로 스트리밍됩니다. 다음과 같이 변경할 수 있습니다.

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

HoloLens 2에 대 한 연결을 설정 하기 전에 ```ConfigureDepthVideoStream```를 호출 해야 합니다. 가장 좋은 장소는 원격 컨텍스트를 만든 직후입니다. 가능한 값은 전체, 절반 및 사분기 해상도입니다. 기본값은 반 해상도입니다. 전체 해상도 깊이 버퍼를 사용 하면 대역폭 요구 사항에도 영향을 미치므로 ```CreateRemoteContext```하는 데 제공 하는 최대 대역폭 값에서을 고려해 야 합니다.

해상도를 구성 하는 것 외에도 [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)를 통해 깊이 버퍼를 커밋해야 합니다.

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

되도록에서 깊이 다시 프로젝션이 작동 하는지 확인 하려면 장치 포털을 통해 깊이 시각화 도우미를 사용 하도록 설정할 수 있습니다. 자세한 내용은 [깊이가 올바르게 설정 되었는지 확인](hologram-stability.md#verifying-depth-is-set-correctly) 을 참조 하세요.

## <a name="optional-custom-data-channels"></a>선택 사항: 사용자 지정 데이터 채널

사용자 지정 데이터 채널은 이미 설정 된 원격 연결을 통해 사용자 데이터를 전송 하는 데 사용할 수 있습니다. 자세한 내용은 [사용자 지정 데이터 채널](holographic-remoting-custom-data-channels.md) 을 참조 하세요.

## <a name="see-also"></a>관련 항목
* [사용자 지정 Holographic Remoting 플레이어 앱 작성](holographic-remoting-create-player.md)
* [사용자 지정 홀로그램 원격 데이터 채널](holographic-remoting-custom-data-channels.md)
* [Holographic 원격을 사용 하 여 보안 연결 설정](holographic-remoting-secure-connection.md)
* [Holographic 원격 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [홀로그램 원격 소프트웨어 사용 조건](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인 정보 취급 방침](https://go.microsoft.com/fwlink/?LinkId=521839)
