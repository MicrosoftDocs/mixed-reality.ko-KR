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
# <a name="writing-a-holographic-remoting-host-app"></a>Holographic 원격 호스트 앱 작성

>[!IMPORTANT]
>이 문서에서는 HoloLens 2 용 호스트 응용 프로그램을 만드는 방법을 설명 합니다. **HoloLens 1** 용 호스트 응용 프로그램은 NuGet **패키지 버전 1.x**를 사용 해야 합니다. 이는 HoloLens 2 용으로 작성 된 호스트 응용 프로그램이 HoloLens 1과 호환 되지 않거나 그 반대의 경우를 의미 합니다. HoloLens 1에 대 한 설명서는 [여기](add-holographic-remoting.md)에서 찾을 수 있습니다.

원격 컴퓨터에서 렌더링 된 원격 Holographic 원격 호스트 앱을 만들면 HoloLens 2로 스트리밍할 수 있습니다. 이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다. 이 페이지 및 작업 프로젝트의 모든 코드는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.

Holographic remoting을 사용 하면 앱이 데스크톱 PC 또는 UWP 장치 (예: Xbox One)에서 호스트 되는 Holographic 콘텐츠를 사용 하 여 HoloLens 2를 대상으로 지정할 수 있으며, 더 많은 시스템 리소스에 액세스 하 고 원격 [몰입 형 보기](app-views.md) 를 기존에 통합할 수 있습니다. 데스크톱 PC 소프트웨어. 원격 호스트 앱은 HoloLens 2에서 입력 데이터 스트림을 받고, 가상 몰입 형 보기에서 콘텐츠를 렌더링 하 고, 콘텐츠 프레임을 HoloLens 2로 다시 스트리밍합니다. 연결은 표준 Wi-fi를 사용 하 여 수행 됩니다. Holographic Remoting은 NuGet 패킷을 통해 데스크톱 또는 UWP 앱에 추가 됩니다. 연결을 처리 하 고 몰입 형 보기에서 렌더링 하는 추가 코드가 필요 합니다.

일반적인 원격 연결의 경우 대기 시간은 50 밀리초로 낮습니다. 플레이어 앱은 실시간으로 대기 시간을 보고할 수 있습니다.

## <a name="prerequisites"></a>사전 요구 사항

좋은 출발점은 Windows Mixed Reality API를 대상으로 하는 작동 하는 DirectX 기반 데스크톱 또는 UWP 앱입니다. 자세한 내용은 [DirectX 개발 개요](directx-development-overview.md)를 참조 하세요. Holographic 프로젝트 템플릿이 좋은 출발점입니다. [ C++ ](creating-a-holographic-directx-project.md)

>[!IMPORTANT]
>Holographic 원격을 사용 하는 모든 앱은 [다중 스레드 아파트](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)를 사용 하도록 작성 되어야 합니다. [단일 스레드 아파트](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) 를 사용 하는 것은 지원 되지만, 재생 하는 동안 일지 성능이 저하 될 수 있습니다. /Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) 를 사용 하는 경우 다중 스레드 아파트는 기본값입니다.



## <a name="get-the-holographic-remoting-nuget-package"></a>Holographic 원격 NuGet 패키지 가져오기

Visual Studio에서 프로젝트에 NuGet 패키지를 추가 하려면 다음 단계를 수행 해야 합니다.
1. Visual Studio에서 프로젝트를 엽니다.
2. 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리 ...** 를 선택 합니다.
3. 표시 되는 패널에서 **찾아보기** 를 클릭 한 다음 "Holographic Remoting"을 검색 합니다.
4. **Holographic**를 선택 하 고 최신 **2.x 버전을** 선택 하 고 **설치**를 클릭 합니다.
5. **미리 보기** 대화 상자가 표시 되 면 **확인**을 클릭 합니다.
6. 표시 되는 다음 대화 상자는 사용권 계약입니다. **동의** 함을 클릭 하 여 사용권 계약에 동의 합니다.

>[!NOTE]
>HoloLens 1을 대상으로 하는 개발자에 게는 NuGet 패키지의 버전 **1. x. x** 를 계속 사용할 수 있습니다. 자세한 내용은 [Holographic 원격 추가 (HoloLens 1)](add-holographic-remoting.md)를 참조 하세요.

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

다음으로 holographic 공간을 만들어야 합니다. CoreWindow 지정은 필요 하지 않습니다. CoreWindow 없는 데스크톱 앱은 ```nullptr```만 전달할 수 있습니다.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>장치에 연결

호스트 앱이 콘텐츠를 렌더링할 준비가 되 면 장치에 대 한 연결을 설정할 수 있습니다.

다음 두 가지 방법 중 하나로 연결을 수행할 수 있습니다.
1) 호스트 앱은 장치에서 실행 중인 플레이어에 연결 됩니다.
2) 장치에서 실행 중인 플레이어는 호스트 앱에 연결 됩니다.

호스트 앱에서 HoloLens 2로의 연결을 설정 하려면 호스트 이름 ```Connect``` 및 포트를 지정 하는 원격 컨텍스트에서 메서드를 호출 합니다. Holographic Remoting 플레이어에서 사용 하는 포트는 **8265**입니다.

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
>Any C++/winrt API ```Connect``` 와 마찬가지로 처리 해야 하는 winrt:: hresult_error을 throw 할 수 있습니다.

>[!TIP]
>[ C++/Winrt](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/) 언어 프로젝션을 사용 하지 않으려면 Holographic Remoting ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` NuGet 패키지 내에 있는 파일을 포함할 수 있습니다. 여기에는 기본 COM 인터페이스의 선언이 포함 됩니다. 그러나 C++/winrt를 사용 하는 것이 좋습니다.

호스트 앱에서 들어오는 연결을 수신 하는 작업은 메서드를 ```Listen``` 호출 하 여 수행할 수 있습니다. 이 호출 중에 핸드셰이크 포트와 전송 포트를 모두 지정할 수 있습니다. 핸드셰이크 포트는 초기 핸드셰이크에 사용 됩니다. 그런 다음 데이터는 전송 포트를 통해 전송 됩니다. 기본적으로 **8265** 및 **8266** 이 사용 됩니다.

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
>NuGet ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 패키지 내에는 Holographic Remoting에서 노출 하는 API에 대 한 자세한 설명서가 포함 되어 있습니다.

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
2) OnDisconnected: 설정 된 연결이 닫히거나 연결을 설정할 수 없는 경우에 트리거됩니다.
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

또한 원격 컨텍스트의 속성을 ```ConnectionState``` 사용 하 여 연결 상태를 쿼리할 수 있습니다.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>음성 이벤트 처리

원격 음성 인터페이스를 사용 하 여 HoloLens 2에 음성 트리거를 등록 하 고 호스트 응용 프로그램에 원격으로 연결할 수 있습니다.

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

비동기 도우미 메서드를 사용 하 여 원격 음성을 초기화할 수 있습니다. 초기화는 상당한 시간이 걸릴 수 있으므로이 작업은 비동기적으로 수행 해야 합니다. [/WinRT를 사용한 C++동시성 및 비동기 작업](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) 은/winrt. 사용 하 여 C++비동기 함수를 작성 하는 방법을 설명 합니다.

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

인식 될 구를 지정 하는 방법에는 두 가지가 있습니다.
1) 음성 문법 xml 파일 내의 사양입니다. 자세한 내용은 [기본 XML 문법을 만드는 방법](https://docs.microsoft.com/en-us/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) 을 참조 하세요.
2) 를 사전 벡터 내부에 ```ApplyParameters```전달 하 여 지정 합니다.

OnRecognizedSpeech 콜백 내에서 음성 이벤트를 처리할 수 있습니다.

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

## <a name="preview-streamed-content-locally"></a>스트리밍 콘텐츠를 로컬로 미리 봅니다.

장치에 전송 되는 호스트 앱에 동일한 콘텐츠를 표시 하려면 원격 컨텍스트의 이벤트 ```OnSendFrame``` 를 사용할 수 있습니다. 이 ```OnSendFrame``` 이벤트는 Holographic 원격 라이브러리가 현재 프레임을 원격 장치로 보낼 때마다 트리거됩니다. 이는 콘텐츠를 사용 하 여 데스크톱 또는 UWP 창으로 array.blit 하는 데 가장 적합 한 시간입니다.

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

## <a name="optional-custom-data-channels"></a>선택 사항: 사용자 지정 데이터 채널

사용자 지정 데이터 채널은 이미 설정 된 원격 연결을 통해 사용자 데이터를 전송 하는 데 사용할 수 있습니다. 자세한 내용은 [사용자 지정 데이터 채널](holographic-remoting-custom-data-channels.md) 을 참조 하세요.

## <a name="see-also"></a>관련 항목
* [사용자 지정 Holographic Remoting 플레이어 앱 작성](holographic-remoting-create-player.md)
* [사용자 지정 Holographic 원격 데이터 채널](holographic-remoting-custom-data-channels.md)
* [Holographic 원격을 사용 하 여 보안 연결 설정](holographic-remoting-secure-connection.md)
* [Holographic 원격 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [Holographic 원격 소프트웨어 사용 조건](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인 정보 취급 방침](https://go.microsoft.com/fwlink/?LinkId=521839)