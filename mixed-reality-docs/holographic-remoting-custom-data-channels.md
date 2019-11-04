---
title: 사용자 지정 Holographic 원격 데이터 채널
description: 사용자 지정 데이터 채널은 이미 설정 된 Holographic 원격 연결을 통해 사용자 데이터를 전송 하는 데 사용할 수 있습니다.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: a862fa52695c7bfb94b58c6c0b85606a112835da
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434280"
---
# <a name="custom-holographic-remoting-data-channels"></a>사용자 지정 Holographic 원격 데이터 채널

>[!NOTE]
>이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.

사용자 지정 데이터 채널을 사용 하 여 설정 된 원격 연결을 통해 사용자 지정 데이터를 전송 합니다.

>[!IMPORTANT]
>사용자 지정 데이터 채널에는 두 사용자 지정 앱 간의 통신을 허용 하므로 사용자 지정 호스트 앱 및 사용자 지정 플레이어 앱이 필요 합니다.

>[!TIP]
>간단한 ping-ping 예제는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)내의 호스트 및 플레이어 샘플에서 찾을 수 있습니다. SampleHostMain/SamplePlayerMain 파일 내의 ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` 주석 처리를 제거 하 여 샘플 코드를 사용 하도록 설정 합니다.


## <a name="create-a-custom-data-channel"></a>사용자 지정 데이터 채널 만들기


사용자 지정 데이터 채널을 만들려면 다음 필드가 필요 합니다.
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

연결이 성공적으로 설정 된 후에는 호스트 측 및/또는 플레이어 쪽에서 새 데이터 채널 만들기를 시작할 수 있습니다. RemoteContext와 PlayerContext는 모두이 작업을 수행 하는 ```CreateDataChannel()``` 메서드를 제공 합니다. 첫 번째 매개 변수는 susequent 작업에서 데이터 채널을 식별 하는 데 사용 되는 채널 ID입니다. 두 번째 매개 변수는이 채널의 데이터가 다른 쪽으로 전송 되는 우선 순위를 지정 하는 우선 순위입니다. 채널 Id의 유효한 범위는 0부터 시작 하 고, 호스트 측의 경우 63을 포함 하 고, 플레이어 쪽에 대 한 127을 포함 하 여 64까지 포함 합니다. 유효한 우선 순위는 ```Low```, ```Medium``` 또는 ```High``` (양쪽 모두)입니다.

**호스트** 쪽에서 데이터 채널 만들기를 시작 하려면 다음을 수행 합니다.
```cpp
// Valid channel ids for channels created on the host side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

**플레이어** 쪽에서 데이터 채널 만들기를 시작 하려면 다음을 수행 합니다.
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>새 사용자 지정 데이터 채널을 만들려면 한 쪽 (호스트 또는 플레이어)만 ```CreateDataChannel``` 메서드를 호출 해야 합니다.

## <a name="handling-custom-data-channel-events"></a>사용자 지정 데이터 채널 이벤트 처리

사용자 지정 데이터 채널을 설정 하려면 플레이어와 호스트 쪽 모두에서 ```OnDataChannelCreated``` 이벤트를 처리 해야 합니다. 사용자 데이터 채널을 양쪽에서 만들고이 채널을 통해 데이터를 보내고 받는 데 사용할 수 있는 ```IDataChannel``` 개체를 제공 하는 경우 트리거됩니다.

```OnDataChannelCreated``` 이벤트에 수신기를 등록 하려면 다음을 수행 합니다.
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

데이터가 수신 될 때 알림 메시지를 받으려면 ```OnDataChannelCreated``` 처리기에서 제공 하는 ```IDataChannel``` 개체의 ```OnDataReceived``` 이벤트에 등록 합니다. 데이터 채널이 닫히면 ```OnClosed``` 이벤트에 등록 하 여 알림 메시지를 받습니다.

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a>데이터 보내기

사용자 지정 데이터 채널을 통해 데이터를 보내려면 ```IDataChannel::SendData()``` 메서드를 사용 합니다. 첫 번째 매개 변수는 보내야 하는 데이터에 대 한 ```winrt::array_view<const uint8_t>```입니다. 두 번째 매개 변수는 다른 쪽에서 수신을 승인할 때까지 데이터를 다시 전송 해야 하는지 여부를 지정 합니다. 

>[!IMPORTANT]
>네트워크 상태가 잘못 된 경우 동일한 데이터 패킷이 두 번 이상 도착할 수 있습니다. 수신 코드에서이 상황을 처리할 수 있어야 합니다.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>사용자 지정 데이터 채널 닫기

사용자 지정 데이터 채널을 닫으려면 ```IDataChannel::Close()``` 메서드를 사용 합니다. 사용자 지정 데이터 채널이 닫히면 두 쪽 모두 ```OnClosed``` 이벤트에서 알림이 표시 됩니다.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>참고 항목
* [Holographic 원격 호스트 앱 작성](holographic-remoting-create-host.md)
* [사용자 지정 Holographic Remoting 플레이어 앱 작성](holographic-remoting-create-player.md)
* [Holographic 원격 문제 해결 및 제한 사항](holographic-remoting-troubleshooting.md)
* [홀로그램 원격 소프트웨어 사용 조건](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft 개인 정보 취급 방침](https://go.microsoft.com/fwlink/?LinkId=521839)
