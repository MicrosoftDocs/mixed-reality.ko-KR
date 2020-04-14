---
title: 사용자 지정 Holographic 원격 데이터 채널
description: 사용자 지정 데이터 채널은 이미 설정 된 Holographic 원격 연결을 통해 사용자 데이터를 전송 하는 데 사용할 수 있습니다.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, 원격 서비스, Holographic 원격 작업
ms.openlocfilehash: 12fa47b6b3a46521a9e6029cab61fa1c628c06e9
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278101"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="ccd09-104">사용자 지정 Holographic 원격 데이터 채널</span><span class="sxs-lookup"><span data-stu-id="ccd09-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="ccd09-105">이 지침은 HoloLens 2의 Holographic Remoting에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="ccd09-106">사용자 지정 데이터 채널을 사용 하 여 설정 된 원격 연결을 통해 사용자 지정 데이터를 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="ccd09-107">사용자 지정 데이터 채널에는 두 사용자 지정 앱 간의 통신을 허용 하므로 사용자 지정 원격 앱 및 사용자 지정 플레이어 앱이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-107">Custom data channels require a custom remote app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="ccd09-108">간단한 ping-ping 예제는 [Holographic Remoting 샘플 github 리포지토리](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)내부의 원격 및 플레이어 샘플에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-108">A simple ping-pong example can be found in the remote and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="ccd09-109">SampleRemoteMain/SamplePlayerMain 파일 내의 ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` 주석 처리를 제거 하 여 샘플 코드를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleRemoteMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="ccd09-110">사용자 지정 데이터 채널 만들기</span><span class="sxs-lookup"><span data-stu-id="ccd09-110">Create a custom data channel</span></span>


<span data-ttu-id="ccd09-111">사용자 지정 데이터 채널을 만들려면 다음 필드가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="ccd09-112">연결이 설정 되 면 원격 측 및/또는 플레이어 쪽에서 새 데이터 채널 만들기를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-112">After a connection was successfully established, the creation of new data channels can be initiated from either the remote side and/or the player side.</span></span> <span data-ttu-id="ccd09-113">RemoteContext와 PlayerContext는 모두이 작업을 수행 하는 ```CreateDataChannel()``` 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method to do this.</span></span> <span data-ttu-id="ccd09-114">첫 번째 매개 변수는 후속 작업에서 데이터 채널을 식별 하는 데 사용 되는 채널 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-114">The first parameter is the channel ID which is used to identify the data channel in subsequent operations.</span></span> <span data-ttu-id="ccd09-115">두 번째 매개 변수는이 채널의 데이터가 다른 쪽으로 전송 되는 우선 순위를 지정 하는 우선 순위입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-115">The second parameter is the priority which specifies the priority with which data of this channel is transferred to the other side.</span></span> <span data-ttu-id="ccd09-116">채널 Id에 대 한 유효한 범위는 0부터 시작 하 여 원격 64 측의 경우 63을 포함 하 고, 플레이어 쪽에 대 한 127을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-116">The valid range for channel IDs is 0 up to and including 63 for the remote side and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="ccd09-117">유효한 우선 순위는 ```Low```, ```Medium``` 또는 ```High``` (양쪽 모두)입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-117">Valid priorities are ```Low```, ```Medium``` or ```High``` (on both sides).</span></span>

<span data-ttu-id="ccd09-118">**원격** 쪽에서 데이터 채널 만들기를 시작 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-118">To initiate the creation of a data channel on the **remote** side:</span></span>
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="ccd09-119">**플레이어** 쪽에서 데이터 채널 만들기를 시작 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-119">To initiate the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="ccd09-120">새 사용자 지정 데이터 채널을 만들려면 한 쪽 (원격 또는 플레이어)만 ```CreateDataChannel``` 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-120">To create a new custom data channel, only one side (either remote or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="ccd09-121">사용자 지정 데이터 채널 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="ccd09-121">Handling custom data channel events</span></span>

<span data-ttu-id="ccd09-122">사용자 지정 데이터 채널을 설정 하려면 플레이어와 원격 측 모두에서 ```OnDataChannelCreated``` 이벤트를 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the remote side).</span></span> <span data-ttu-id="ccd09-123">사용자 데이터 채널을 양쪽에서 만들고이 채널을 통해 데이터를 보내고 받는 데 사용할 수 있는 ```IDataChannel``` 개체를 제공 하는 경우 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="ccd09-124">```OnDataChannelCreated``` 이벤트에 수신기를 등록 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="ccd09-125">데이터가 수신 될 때 알림 메시지를 받으려면 ```OnDataChannelCreated``` 처리기에서 제공 하는 ```IDataChannel``` 개체의 ```OnDataReceived``` 이벤트에 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="ccd09-126">데이터 채널이 닫히면 ```OnClosed``` 이벤트에 등록 하 여 알림 메시지를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

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

## <a name="sending-data"></a><span data-ttu-id="ccd09-127">데이터 보내기</span><span class="sxs-lookup"><span data-stu-id="ccd09-127">Sending data</span></span>

<span data-ttu-id="ccd09-128">사용자 지정 데이터 채널을 통해 데이터를 보내려면 ```IDataChannel::SendData()``` 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="ccd09-129">첫 번째 매개 변수는 보내야 하는 데이터에 대 한 ```winrt::array_view<const uint8_t>```입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-129">The first parameter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="ccd09-130">두 번째 매개 변수는 다른 쪽에서 수신을 승인할 때까지 데이터를 다시 보내야 하는 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-130">The second parameter specifies where the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="ccd09-131">네트워크 상태가 잘못 된 경우 동일한 데이터 패킷이 두 번 이상 도착할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="ccd09-132">수신 코드에서이 상황을 처리할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="ccd09-133">사용자 지정 데이터 채널 닫기</span><span class="sxs-lookup"><span data-stu-id="ccd09-133">Closing a custom data channel</span></span>

<span data-ttu-id="ccd09-134">사용자 지정 데이터 채널을 닫으려면 ```IDataChannel::Close()``` 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="ccd09-135">사용자 지정 데이터 채널이 닫히면 두 쪽 모두 ```OnClosed``` 이벤트에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd09-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="ccd09-136">관련 항목</span><span class="sxs-lookup"><span data-stu-id="ccd09-136">See Also</span></span>
* [<span data-ttu-id="ccd09-137">Holographic Remoting 원격 앱 작성</span><span class="sxs-lookup"><span data-stu-id="ccd09-137">Writing a Holographic Remoting remote app</span></span>](holographic-remoting-create-host.md)
* [<span data-ttu-id="ccd09-138">사용자 지정 Holographic Remoting 플레이어 앱 작성</span><span class="sxs-lookup"><span data-stu-id="ccd09-138">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="ccd09-139">Holographic 원격 문제 해결 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="ccd09-139">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="ccd09-140">홀로그램 원격 소프트웨어 사용 조건</span><span class="sxs-lookup"><span data-stu-id="ccd09-140">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="ccd09-141">Microsoft 개인 정보 취급 방침</span><span class="sxs-lookup"><span data-stu-id="ccd09-141">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
