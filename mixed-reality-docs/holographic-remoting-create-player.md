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
# <a name="writing-a-custom-holographic-remoting-player-app"></a>사용자 지정 Holographic Remoting 플레이어 앱 작성

>[!IMPORTANT]
>이 문서에서는 HoloLens 2에 대 한 사용자 지정 플레이어 응용 프로그램을 만드는 방법을 설명 합니다. HoloLens 2 용으로 작성 된 사용자 지정 플레이어는 HoloLens 1 용으로 작성 된 호스트 응용 프로그램과 호환 되지 않습니다. 이는 두 응용 프로그램이 모두 NuGet **패키지 버전 2.x**를 사용 해야 함을 의미 합니다.

사용자 지정 Holographic 원격 플레이어 앱을 만들면 HoloLens 2의 원격 컴퓨터에서 [몰입 형 보기](app-views.md) 를 표시할 수 있는 사용자 지정 응용 프로그램을 만들 수 있습니다. 이 문서에서는이를 달성할 수 있는 방법에 대해 설명 합니다. 이 페이지 및 작업 프로젝트의 모든 코드는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)에서 찾을 수 있습니다.

Holographic 원격 플레이어를 사용 하면 앱에서 데스크톱 PC 또는 UWP 장치 (예: Xbox One)에서 [렌더링](rendering.md) 된 Holographic 콘텐츠를 표시 하 여 더 많은 시스템 리소스에 액세스할 수 있습니다. Holographic Remoting player 앱은 입력 데이터를 Holographic Remoting 호스트 응용 프로그램으로 스트리밍하 고 비디오 및 오디오 스트림으로 몰입 형 보기를 다시 받습니다. 연결은 표준 Wi-fi를 사용 하 여 수행 됩니다. 플레이어 앱을 만들려면 NuGet 패키지를 사용 하 여 UWP 앱에 Holographic 원격을 추가 하 고, 연결을 처리 하 고 몰입 형 뷰를 표시 하는 코드를 작성 합니다. 

## <a name="prerequisites"></a>사전 요구 사항

좋은 출발점은 이미 Windows Mixed Reality API를 대상으로 하는 작동 하는 DirectX 기반 UWP 앱입니다. 자세한 내용은 [DirectX 개발 개요](directx-development-overview.md)를 참조 하세요. 기존 앱이 없고 처음부터 시작 하려면 [ C++ holographic 프로젝트 템플릿이](creating-a-holographic-directx-project.md) 좋은 출발점입니다.

>[!IMPORTANT]
>Holographic 원격을 사용 하는 모든 앱은 [다중 스레드 아파트](https://docs.microsoft.com/en-us/windows/win32/com/multithreaded-apartments)를 사용 하도록 작성 되어야 합니다. [단일 스레드 아파트](https://docs.microsoft.com/en-us/windows/win32/com/single-threaded-apartments) 사용 하는 것은 지원 되지만, 재생 하는 동안 일지 성능이 저하 되 고 가능 합니다. /Winrt C++ [winrt:: init_apartment](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/get-started) 를 사용 하는 경우 다중 스레드 아파트는 기본값입니다.

## <a name="get-the-holographic-remoting-nuget-package"></a>Holographic 원격 NuGet 패키지 가져오기

Visual Studio에서 프로젝트에 NuGet 패키지를 추가 하려면 다음 단계를 수행 해야 합니다.
1. Visual Studio에서 프로젝트를 엽니다.
2. 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **NuGet 패키지 관리 ...** 를 선택 합니다.
3. 표시 되는 패널에서 **찾아보기** 를 클릭 한 다음 "Holographic Remoting"을 검색 합니다.
4. **Holographic**를 선택 하 고 최신 **2.x 버전을** 선택 하 고 **설치**를 클릭 합니다.
5. **미리 보기** 대화 상자가 표시 되 면 **확인**을 클릭 합니다.
6. 표시 되는 다음 대화 상자는 사용권 계약입니다. **동의** 함을 클릭 하 여 사용권 계약에 동의 합니다.

>[!IMPORTANT]
><a name="idl"></a>NuGet ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` 패키지 내에는 Holographic Remoting에서 노출 하는 API에 대 한 자세한 설명서가 포함 되어 있습니다.

## <a name="modify-the-packageappxmanifest-of-the-application"></a>응용 프로그램의 appxmanifest.xml을 수정 합니다.

응용 프로그램이 NuGet 패키지에 의해 추가 된 Holographic를 인식 하도록 하려면 프로젝트에서 다음 단계를 수행 해야 합니다.

1. 솔루션 탐색기에서 **appxmanifest.xml** 파일을 마우스 오른쪽 단추로 클릭 하 고 **연결 프로그램 ...을** 선택 합니다.
2. **XML (텍스트) 편집기** 를 선택 하 고 확인을 클릭 합니다.
3. 파일에 다음 줄을 추가 하 고 저장 합니다.
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
## <a name="create-the-player-context"></a>플레이어 컨텍스트 만들기

첫 번째 단계로 응용 프로그램은 플레이어 컨텍스트를 만들어야 합니다.

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
>Holographic Remoting은 원격 특정 런타임을 사용 하 여 Windows의 일부인 Windows Mixed Reality 런타임을 대체 하는 방식으로 작동 합니다. 플레이어 컨텍스트를 만드는 동안이 작업을 수행 합니다. 이러한 이유로 플레이어 컨텍스트를 만들기 전에 Windows Mixed Reality API를 호출 하면 예기치 않은 동작이 발생할 수 있습니다. 권장 되는 방법은 혼합 현실 API와의 상호 작용 전에 가능한 한 빨리 플레이어 컨텍스트를 만드는 것입니다. 이후에 만들어지거나 검색 된 개체를 사용 하 여를 호출 하기 전에 Windows Mixed Reality ```PlayerContext::Create()``` API를 통해 만들어지거나 검색 된 개체를 혼합 하지 마세요.

그런 다음 [HolographicSpace. CreateForCoreWindow](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)를 호출 하 여 HolographicSpace를 만들 수 있습니다.

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-host"></a>호스트에 연결

플레이어 앱이 콘텐츠를 렌더링할 준비가 되 면 호스트에 대 한 연결을 설정할 수 있습니다.

시나리오별 방법 중 하나로 연결을 설정할 수 있습니다.
1) HoloLens 2에서 실행 되는 플레이어 앱은 호스트 앱에 연결 됩니다.
2) 호스트 앱은 HoloLens 2에서 실행 중인 플레이어 앱에 연결 합니다.

플레이어 앱에서 호스트로 연결 하려면 호스트 이름 및 포트를 ```Connect``` 지정 하는 플레이어 컨텍스트의 메서드를 호출 합니다. 기본 포트는 **8265**입니다.

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
>Any C++/winrt API ```Connect``` 와 마찬가지로 처리 해야 하는 winrt:: hresult_error을 throw 할 수 있습니다.

플레이어 앱에서 들어오는 연결을 수신 하는 작업은 메서드를 ```Listen``` 호출 하 여 수행할 수 있습니다. 이 호출 중에 핸드셰이크 포트와 전송 포트를 모두 지정할 수 있습니다. 핸드셰이크 포트는 초기 핸드셰이크에 사용 됩니다. 그런 다음 데이터는 전송 포트를 통해 전송 됩니다. 기본적으로 포트 번호 **8265** 및 **8266** 이 사용 됩니다.

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


## <a name="handling-connection-related-events"></a>연결 관련 이벤트 처리

는 ```PlayerContext``` 연결 상태를 모니터링 하는 세 개의 이벤트를 노출 합니다.
1) OnConnected: 호스트에 대 한 연결이 성공적으로 설정 되 면 트리거됩니다.
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) OnDisconnected: 설정 된 연결이 종료 되거나 연결을 설정할 수 없는 경우에 트리거됩니다.
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
>가능한 ```ConnectionFailureReason``` 값은 ```Microsoft.Holographic.AppRemoting.idl``` [파일](#idl)에 설명 되어 있습니다.

3) OnListening: 들어오는 연결에 대 한 수신 대기를 시작 합니다.
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

또한 플레이어 컨텍스트의 속성을 ```ConnectionState``` 사용 하 여 연결 상태를 쿼리할 수 있습니다.
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a>원격으로 렌더링 된 프레임을 표시 합니다.

원격으로 렌더링 된 콘텐츠를 표시 하려면 ```PlayerContext::BlitRemoteFrame()``` [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe)를 렌더링 하는 동안를 호출 합니다. 

```BlitRemoteFrame()```현재 HolographicFrame에 대 한 백 버퍼가 렌더링 대상으로 바인딩되어야 합니다. 백 버퍼는 [Direct3D11BackBuffer](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) 속성을 통해 [HolographicCameraRenderingParameters](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) 에서 받을 수 있습니다.

호출 되 면 ```BlitRemoteFrame()``` 호스트 응용 프로그램에서 수신 된 최신 프레임을 HolographicFrame의 백 버퍼에 복사 합니다. 원격 응용 프로그램에서 원격 프레임을 렌더링 하는 동안 포커스 지점을 지정 하는 경우에도 포커스 지점 집합이 설정 됩니다.

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
>```PlayerContext::BlitRemoteFrame()```현재 프레임의 포커스 지점을 덮어쓸 수 있습니다. 
>- 대체 (fallback) 포커스 지점을 지정 하려면 이전 ```PlayerContext::BlitRemoteFrame()```에 [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) 를 호출 합니다. 
>- 원격 포커스 지점을 과도 하 게 쓰려면 [HolographicCameraRenderingParameters:: SetFocusPoint](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) ```PlayerContext::BlitRemoteFrame()```를 호출 합니다.

성공 하면를 ```BlitRemoteFrame()``` 반환 ```BlitResult::Success_Color```합니다. 그렇지 않으면 실패 원인을 반환 합니다.
- ```BlitResult::Failed_NoRemoteFrameAvailable```: 사용할 수 있는 원격 프레임이 없기 때문에 실패 했습니다.
- ```BlitResult::Failed_NoCamera```: 카메라가 없어 실패 했습니다.

## <a name="optional-get-statistics-about-the-last-remote-frame"></a>선택 사항: 마지막 원격 프레임에 대 한 통계 가져오기

성능 또는 네트워크 문제를 진단 하려면 ```PlayerContext::LastFrameStatistics``` 속성을 통해 마지막 원격 프레임에 대 한 통계를 검색할 수 있습니다. [HolographicFrame::P resentusingcurrentprediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)를 호출 하는 동안 통계가 업데이트 됩니다.

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

자세한 내용은```Microsoft.Holographic.AppRemoting.idl``` [파일](#idl)의 ```PlayerFrameStatistics```설명서를 참조 하세요.

## <a name="optional-custom-data-channels"></a>선택 사항: 사용자 지정 데이터 채널

사용자 지정 데이터 채널은 이미 설정 된 원격 연결을 통해 사용자 데이터를 전송 하는 데 사용할 수 있습니다. 자세한 내용은 [사용자 지정 데이터 채널](holographic-remoting-custom-data-channels.md) 을 참조 하세요.

## <a name="see-also"></a>관련 항목
* [Holographic 원격 호스트 앱 작성](holographic-remoting-create-host.md)
* [사용자 지정 Holographic 원격 데이터 채널](holographic-remoting-custom-data-channels.md)
* [Holographic 원격을 사용 하 여 보안 연결 설정](holographic-remoting-secure-connection.md)
* [Holographic 원격 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [Holographic 원격 소프트웨어 사용 조건](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인 정보 취급 방침](https://go.microsoft.com/fwlink/?LinkId=521839)