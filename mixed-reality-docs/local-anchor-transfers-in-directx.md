---
title: DirectX에서 로컬 앵커 전송
description: 공간 앵커를 전송 하 여 두 개의 HoloLens 장치를 동기화 하는 방법에 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: 공간 앵커, 전송, 멀티 플레이 게임, HoloLens, 동기화 시나리오, 연습, 샘플 코드, 전송, 로컬 앵커 전송, 앵커 내보내기, 가져오기 앵커를 보려면
ms.openlocfilehash: 5d03f4bfa764b9948ec4718bce86127cfcc3e303
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605067"
---
# <a name="local-anchor-transfers-in-directx"></a>DirectX에서 로컬 앵커 전송

수 없는 상황 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>, 로컬 앵커 전송 두 번째 HoloLens 장치에서 가져올 앵커를 내보내려면 하나 HoloLens 장치를 사용 합니다.

>[!NOTE]
>로컬 앵커 전송을 제공 보다 덜 강력 앵커 회수 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>, iOS 및 Android 장치의이 방식으로 지원 되지 않습니다.

>[!NOTE]
>이 문서의 코드 조각 사용에 현재 방법을 보여 줍니다 C++/CX 대신 C + + 17 규격 C++/WinRT에 사용 되는 [ C++ holographic 프로젝트 템플릿을](creating-a-holographic-directx-project.md).  개념에 대 한 동일는 C++코드를 변환 해야 하지만 /WinRT 프로젝트입니다.

## <a name="transferring-spatial-anchors"></a>공간 앵커를 전송합니다.

공간 앵커를 사용 하 여 Windows Mixed Reality 장치 간에 전송할 수 있습니다 합니다 [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)합니다. 이 API를 사용 하 여 모든 지원 센서 데이터와 전 세계에서 정확한 해당 위치를 찾는 데 필요한 앵커를 번들 하 고 다음 다른 장치에서 해당 번들을 가져올 수 있습니다. 두 번째 장치에서 앱에는 앵커를 가져온 후 각 앱에는 공유 실제 환경에서 같은 위치에 나타납니다 공간 앵커 좌표계를 사용 하 여 홀로그램 렌더링할 수 있습니다.

공간 앵커를 다른 장치 형식 간에 전송할 수 없는 경우에 예를 들어 HoloLens 공간 앵커는 몰입 형 헤드셋을 사용 하 여 찾을 수 있는 수 있습니다 note 합니다.  전송 된 앵커 iOS 또는 Android 장치를 사용 하 여 호환 되지 않습니다.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>SpatialPerception 기능을 사용 하도록 앱 설정

앱 사용 하려면 먼저 spatialPerception 기능을 사용 하는 권한을 부여 해야 합니다 [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)합니다. 중요 한 정보가 포함 될 수 있는 해당 앵커의 주변에 시간이 지남에 따라 수집 된 센서 이미지를 공유 하는 작업이 필요 공간 앵커를 전송 하기 때문에 이것이 필요한입니다.

앱에 대해 package.appxmanifest 파일에서이 기능을 선언 합니다. 예를 들면 다음과 같습니다.

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

제공 되는 기능을 **uap2** 네임 스페이스입니다. 매니페스트에이 네임 스페이스에 대 한 액세스를 가져오려고로 포함를 *xlmns* 특성을 &lt;패키지 > 요소입니다. 예를 들면 다음과 같습니다.

```
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**참고:** 앱을 SpatialAnchor 내보내기/가져오기 Api에 액세스 하기 전에 런타임 시에 기능을 요청 해야 합니다. 참조 [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) 아래 예제에서입니다.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>SpatialAnchorTransferManager를 사용 하 여 내보내 앵커 데이터 직렬화

도우미 함수를 내보내려면 코드 샘플에 포함 됩니다 (직렬화) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) 데이터입니다. 이 내보내기 API 앵커를 사용 하 여 문자열을 연결 하는 키-값 쌍의 컬렉션의 모든 앵커를 serialize 합니다.

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

첫째, 데이터 스트림을 설정 해야 합니다. 이렇게 하면 미국 1에 있습니다.) 사용 하 여 TryExportAnchorsAsync 앱 2 소유한 버퍼에 데이터를 저장 합니다.) std:: vector는 고유한 메모리 버퍼로-인, WinRT 데이터 스트림-내보낸된 바이트 버퍼 스트림에서 데이터를 읽을&lt;바이트 >.

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

공간 데이터를 시스템에서 내보낸 앵커를 포함 하 여 액세스할 수 있는 권한을 요청 해야 합니다.

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

권한을 얻게 수행 하는 경우 앵커 내보낸 데이터 스트림을 읽을 수 있습니다. 여기서도 DataReader 만들고 InputStream 데이터 읽기를 사용 하는 방법을 보여줍니다.

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

스트림에서 바이트를 읽은 것 후 고유한 데이터 버퍼에 저장할 수에서는 다음과 같이 합니다.

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>SpatialAnchorTransferManager를 사용 하 여 시스템에 가져와서 앵커 데이터를 deserialize 합니다.

도우미 함수는 이전에 내보낸된 데이터를 로드 하는 코드 샘플에 포함 됩니다. 제외 하 고이 데이터는 네트워크 소켓 같은 다른 원본에서 가져온이 deserialization 함수는 SpatialAnchorStore-제공 하는 것에 유사한 키-값 쌍의 컬렉션을 제공 합니다. 처리할 수 있습니다 및 오프 라인을 사용 하 여 앱에서 메모리를 저장 하기 전에이 데이터에 대 한 설명 (있는 경우) 또는 앱의 SpatialAnchorStore 합니다.

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

먼저 앵커 데이터에 액세스 하는 스트림 개체를 생성 해야 합니다. 에서는 쓰기 데이터는 버퍼에서 시스템 버퍼를 SpatialAnchors 시스템에는 바이트의 버퍼에서 앵커를 가져오는 목표를 위해 메모리 내 데이터 스트림에 쓰는 DataWriter 만들어 됩니다.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

다시 한 번, 앱에 사용자의 환경에 대 한 개인 정보를 포함할 수 있는 공간 앵커 데이터를 내보낼 수 있는 권한이 있는지 확인 해야 합니다.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

액세스가 허용 되 면 경우에 시스템 데이터 스트림으로 버퍼에서 바이트를 작성할 수 했습니다.

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

데이터 스트림에서 바이트를 저장 하는 데 성공한 경우에 SpatialAnchorTransferManager를 사용 하 여 해당 데이터를 가져올 수 있습니다 노력 합니다.

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

데이터를 가져와야 할 경우 앵커를 사용 하 여 문자열을 연결 하는 키-값 쌍의 맵 보기를 얻게 됩니다. 이 고유한 메모리 내 데이터 컬렉션에 로드 하 고 해당 컬렉션을 사용 하 여 사용 하 여 관심이 앵커를 검색할 수 있습니다.

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

**참고:** 한다고 해 서 앵커를 가져올 수 있습니다, 반드시 바로 사용할 수 있습니다. 앵커; 완전히 다른 룸 또는 다른 물리적 위치에 있을 수 있습니다. 앵커 받은 장치에 알려진된 현재 환경에 상대적인 앵커 위치를 복원 하려면, 앵커 생성 된 환경에 대 한 충분 한 시각적 정보까지 찾을 수 없습니다. 클라이언트 구현에서 라이브 콘텐츠를 사용 하려면 계속 하기 전에 좌표 시스템의 로컬 또는 참조 프레임을 기준으로 앵커를 찾는 것이 좋습니다. 예를 들어 앵커 않더라도 되기 시작할 때까지 주기적으로 현재 좌표계를 기준으로 앵커를 배치 해 보십시오.

## <a name="special-considerations"></a>특별 고려 사항

합니다 [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API를 통해 여러 [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) 를 동일한 불투명 이진 blob로 내보낼 수 있습니다. 그러나 단일 SpatialAnchor 또는 여러 SpatialAnchors 단일 호출에서 내보낸 여부에 따라 blob를 포함 하는 데이터의 미묘한 차이점이 있습니다.

### <a name="export-of-a-single-spatialanchor"></a>단일 SpatialAnchor 내보내기

환경은 SpatialAnchor 가져오는 장치에서 인식 될 수 있도록는 SpatialAnchor 주변의 환경의 표현을 포함 하는 blob입니다. 가져오기가 완료 되 면 새 SpatialAnchor 장치에 제공 됩니다. 앵커의 주변에 사용자가 최근에 가정 하 고, 찾을 수 있는 것 및 홀로그램은 SpatialAnchor 연결할를 렌더링할 수 있습니다. 이러한 홀로그램은 SpatialAnchor 내보낼 원본 장치에서 이전과 동일한 실제 위치에 표시 됩니다.

![단일 SpatialAnchor 내보내기](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>여러 SpatialAnchors 내보내기

단일 SpatialAnchor의 내보내기와 같은 blob를 지정 된 모든 SpatialAnchors 주변의 환경의 표현을 포함 합니다. 또한 blob는 동일한 물리적 공간에 있는 경우 포함된 된 SpatialAnchors 간의 연결에 대 한 정보를 포함 합니다. 이 두 인접 SpatialAnchors를 가져온 경우 다음을 홀로그램에 첨부 됨을 의미 합니다 *두 번째* 장치에만 주변 환경 인식 하는 경우에 SpatialAnchor 찾을 수 있는 것은 *첫 번째* 두 SpatialAnchors 간에 충분 한 계산 하기 위해 데이터 변환 하므로 SpatialAnchor, blob에 포함 되었습니다. 두 SpatialAnchors 개별적으로 내보낸 경우 (두 개의 별도 TryExportSpatialAnchors에 대 한 호출의) 수는 첫 번째를 찾을 수 있는 경우 두 번째 SpatialAnchor에 홀로그램 연결에 대 한 blob에 포함 된 충분 한 데이터를 합니다.

![단일 TryExportAnchorsAsync 호출을 사용 하 여 내보낸 여러 앵커](images/multipleanchors.png) ![각 앵커에 대 한 별도 TryExportAnchorsAsync 호출을 사용 하 여 내보낸 여러 앵커](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>예: Windows::Networking::StreamSocket를 사용 하 여 앵커 데이터 보내기

여기에서는 TCP 네트워크를 통해 전송 하 여 내보낸된 앵커 데이터를 사용 하는 방법의 예가 제공 합니다. HolographicSpatialAnchorTransferSample에서입니다.

WinRT StreamSocket 클래스 PPL 작업 라이브러리를 사용합니다. 네트워크 오류의 경우 오류가 다시 throw 되는 예외를 사용 하 여 체인의 다음 작업으로 반환 됩니다. 예외는 오류 상태를 나타내는 HRESULT를 포함 합니다.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Tcp는 Windows::Networking::StreamSocketListener를 사용 하 여 내보낸된 앵커 데이터 보내기

연결을 수신 하는 서버 인스턴스를 만듭니다.

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

연결을 수신 하는 경우, 클라이언트 소켓 연결을 사용 하 여 앵커 데이터를 전송 합니다.

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

이제 내보낸된 앵커 데이터가 포함 된 데이터 스트림을 보낼 시작할 수 있습니다.

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

스트림 자체를 보내드릴 수, 전에 먼저 헤더 패킷을 보냅니다 해야 합니다. 이 헤더 패킷 고정 길이 여야 하며 앵커 데이터 스트림에서 바이트의 가변 배열 길이 나타낼 수도 있어야 합니다. 보낼 다른 헤더 데이터가 없기이 예제의 경우 하므로 헤더는 4 바이트 이며는 32 비트 부호 없는 정수를 포함.

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

스트림 길이 (바이트)를 클라이언트에 전송 된 후 데이터 스트림 자체를 소켓 스트림에 쓸 진행할 수 있습니다. 그러면 앵커 저장소 바이트 클라이언트로 전송 될 수 있습니다.

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

이 항목의 앞부분에서 설명 했 듯이 네트워크 오류 상태 메시지를 포함 하는 예외를 처리 하는 준비 된 것 이어야 합니다. 예기치 않은 오류에 대 한 디버그 콘솔에 예외 정보를 작성할 수 있습니다 다음과 같이 합니다. 이 코드 샘플 연결을 완료할 수 없는 경우 또는 앵커 데이터를 보내는 완료할 수 없는 경우 발생 하는 결과 대 한 단서를 제공 됩니다.

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>내보낸된 앵커 데이터를 받기 위해 TCP를 Windows::Networking::StreamSocket 사용

먼저 서버에 연결 해야 합니다. 이 코드 샘플 만들기는 StreamSocket를 구성 하 고 소켓 연결을 사용 하는 네트워크 데이터를 얻기 위해 사용할 수 있는 DataReader를 만드는 방법을 보여 줍니다.

**참고:** 이 샘플 코드를 실행 하는 경우에 구성 하 고 클라이언트를 시작 하기 전에 서버를 시작 하는 확인 합니다.

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

연결을 한 후 데이터를 전송 하도록 서버를 기다릴 수 했습니다. 스트림 데이터 판독기에서 LoadAsync를 호출 하 여이 작업을 수행 합니다.

첫 번째 집합이 수신 바이트, 이전 섹션에 설명 된 대로 앵커 데이터 스트림 바이트 길이 나타내는 헤더 패킷을 항상 있어야 합니다.

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

...

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

헤더 패킷을 받은 후 알게 리라 앵커 데이터의 바이트 수입니다. 스트림에서 해당 바이트를 진행할 수 있습니다.

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

앵커 데이터 스트림을 수신 하기 위한 코드는 다음과 같습니다. 스트림에서 바이트를 먼저 로드는 마찬가지로 이 작업에는 네트워크에서 해당 크기 바이트를 수신 하는 StreamSocket 대기로 완료 하려면 다소 시간이 걸릴 수 있습니다.

로드 작업이 완료 되 면 바이트 수를 읽을 수 있습니다. 앵커 데이터 스트림에 대 한 것으로 예상 바이트 수를 받은 경우 수 해 보면 앵커 데이터 가져오기 그러지 않으면 있습니다 받아야 일종의 오류가 있습니다. 예를 들어이 항목은 데이터 스트림을 보내는 완료할 수 또는 전체 데이터 스트림을 클라이언트에서 받을 수 전에 네트워크의 작동이 전에 서버 인스턴스가 종료 될 때 발생할 수 있습니다.

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

다시, 알 수 없는 네트워크 오류를 처리 하도록 준비 있어야 합니다.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

정말 간단하죠. 이제 네트워크를 통해 받은 앵커를 찾는 시도 하는 데 충분 한 정보가 있어야 합니다. 마찬가지로 클라이언트를 제대로 찾을 앵커; 공간에 대 한 충분 한 시각적 추적 데이터 있어야 함을 note합니다 그래도 작동 하지 않으면 즉시 잠시를 따라 이동 합니다. 여전히 작동 하지 않으면 경우 서버 자세한 앵커 보내고 네트워크 통신을 사용 하 여 클라이언트에 대해 작동 하는 것에 동의 합니다. HolographicSpatialAnchorTransferSample 다운로드, 클라이언트 및 서버 Ip 구성 및 HoloLens 장치 클라이언트 및 서버에 배포 하 여 시도할 수 있습니다.

## <a name="see-also"></a>참조
* [병렬 패턴 라이브러리 PPL)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows.Networking.StreamSocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [Windows.Networking.StreamSocketListener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
