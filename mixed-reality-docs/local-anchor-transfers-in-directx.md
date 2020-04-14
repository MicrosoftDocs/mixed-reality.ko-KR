---
title: DirectX의 로컬 앵커 전송
description: 공간 앵커를 전송 하 여 두 HoloLens 장치를 동기화 하는 방법을 설명 합니다.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 동기화, 공간 앵커, 전송, 여럿이, 보기, 시나리오, 연습, 샘플 코드, 전송, 로컬 앵커 전송, 앵커 내보내기, 앵커 가져오기
ms.openlocfilehash: e709f107e280f9c88a4f1af590cb62de301633fe
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278071"
---
# <a name="local-anchor-transfers-in-directx"></a>DirectX의 로컬 앵커 전송

<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>를 사용할 수 없는 경우 로컬 앵커 전송에서는 한 hololens 장치에서 두 번째 hololens 장치에서 가져올 앵커를 내보낼 수 있습니다.

>[!NOTE]
>로컬 앵커 전송은 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>보다 더 강력 하지 않은 앵커 회수를 제공 하며, IOS 및 Android 장치는이 방식에서 지원 되지 않습니다.

>[!NOTE]
>이 문서의 코드 조각은 현재 [ C++ holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되 C++는 것 처럼 C + 17-so-far working 규격 C++/winrt 대신/cx 사용을 보여 줍니다.  개념은 C++/winrt 프로젝트와 동일 하지만 코드를 변환 해야 합니다.

## <a name="transferring-spatial-anchors"></a>공간 앵커 전송

[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)를 사용 하 여 Windows Mixed Reality 장치 간에 공간 앵커를 전송할 수 있습니다. 이 API를 사용 하면 전 세계의 정확한 위치를 찾는 데 필요한 모든 지원 센서 데이터를 사용 하 여 앵커를 번들로 묶은 다음 해당 번들을 다른 장치에서 가져올 수 있습니다. 두 번째 장치의 앱이 해당 앵커를 가져온 후에는 각 앱이 해당 공유 공간 앵커의 좌표계를 사용 하 여 holograms를 렌더링할 수 있습니다. 그러면 실제 세계의 동일한 위치에 표시 됩니다.

공간 앵커는 서로 다른 장치 유형 간에 전송할 수 없습니다. 예를 들어 HoloLens 공간 앵커는 몰입 형 헤드셋을 사용 하 여 과정이 되지 않을 수 있습니다.  전송 된 앵커도 iOS 또는 Android 장치와 호환 되지 않습니다.

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>SpatialPerception 기능을 사용 하도록 앱 설정

앱에는 [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)를 사용 하기 전에 spatialPerception 기능을 사용할 수 있는 권한이 부여 되어야 합니다. 공간 앵커를 전송 하려면 해당 앵커 근처에서 시간에 따라 수집 된 센서 이미지를 공유 해야 합니다. 여기에는 중요 한 정보가 포함 될 수 있습니다.

앱에 대 한 appxmanifest.xml 파일에서이 기능을 선언 합니다. 예를 들면 다음과 같습니다.

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

이 기능은 **uap2** 네임 스페이스에서 제공 됩니다. 매니페스트에이 네임 스페이스에 대 한 액세스 권한을 얻으려면이를 &lt;Package > 요소에 *xlmns* 특성으로 포함 합니다. 예를 들면 다음과 같습니다.

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**참고:** 앱은 런타임에 SpatialAnchor 내보내기/가져오기 Api에 액세스할 수 있는 기능을 요청 해야 합니다. 아래 예제에서 [Requestaccessasync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) 를 참조 하세요.

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>SpatialAnchorTransferManager로 내보내서 앵커 데이터를 직렬화 합니다.

도우미 함수는 [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) 데이터를 내보내기 (직렬화) 하는 코드 샘플에 포함 되어 있습니다. 이 내보내기 API는 앵커와 함께 문자열을 연결 하는 키-값 쌍 컬렉션의 모든 앵커를 직렬화 합니다.

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

먼저 데이터 스트림을 설정 해야 합니다. 이렇게 하면 1이 됩니다.) TryExportAnchorsAsync를 사용 하 여 응용 프로그램 소유의 버퍼에 데이터를 저장 하 고 2를 사용 합니다.) WinRT 데이터 스트림 인 내보낸 바이트 버퍼 스트림에서 데이터를 std:: vector&lt;byte >의 고유한 메모리 버퍼로 읽습니다.

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

시스템에서 내보내는 앵커를 비롯 하 여 공간 데이터에 액세스 하기 위한 권한을 요청 해야 합니다.

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

Get 권한이 있고 앵커를 내보내는 경우 데이터 스트림을 읽을 수 있습니다. 여기서는 데이터를 읽는 데 사용할 DataReader 및 InputStream를 만드는 방법도 보여 줍니다.

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

스트림에서 바이트를 읽은 후와 같이 자체 데이터 버퍼에 저장할 수 있습니다.

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>SpatialAnchorTransferManager를 사용 하 여 시스템으로 가져와 앵커 데이터를 Deserialize 합니다.

코드 샘플에는 이전에 내보낸 데이터를 로드 하는 도우미 함수가 포함 되어 있습니다. 이 deserialization 함수는 SpatialAnchorStore에서 제공 하는 것과 비슷한 키-값 쌍의 컬렉션을 제공 합니다. 단, 네트워크 소켓과 같은 다른 원본에서이 데이터를 가져왔습니다. 앱 내 메모리 또는 앱의 SpatialAnchorStore (해당 하는 경우)를 사용 하 여 오프 라인으로 저장 하기 전에이 데이터를 처리 하 고 이유를 지정할 수 있습니다.

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

먼저, 고정 데이터에 액세스 하기 위해 stream 개체를 만들어야 합니다. 버퍼의 데이터를 시스템 버퍼에 기록할 것 이므로 메모리 내 데이터 스트림에 쓰는 Datawriter 여부를 만들어 바이트 버퍼에서 시스템에 SpatialAnchors로의 앵커를 가져오는 목표를 달성 합니다.

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

다시 한 번, 앱에는 사용자 환경에 대 한 개인 정보를 포함할 수 있는 공간 앵커 데이터를 내보낼 수 있는 권한이 있는지 확인 해야 합니다.

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

액세스가 허용 되 면 버퍼에서 시스템 데이터 스트림으로 바이트를 쓸 수 있습니다.

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

데이터 스트림에 바이트를 저장 하는 데 성공 하면 SpatialAnchorTransferManager를 사용 하 여 해당 데이터를 가져올 수 있습니다.

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

데이터를 가져올 수 있는 경우 문자열을 앵커와 연결 하는 키-값 쌍의 지도 보기가 표시 됩니다. 이를 자체 메모리 내 데이터 컬렉션에 로드 하 고 해당 컬렉션을 사용 하 여 사용 하려는 앵커를 찾을 수 있습니다.

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

**참고:** 앵커를 가져올 수 있기 때문에이는 바로 사용할 수 있다는 의미는 아닙니다. 앵커는 다른 방 또는 다른 실제 위치에 완전히 있을 수 있습니다. 앵커는 알려진 현재 환경에 상대적인 앵커의 위치를 복원 하기 위해 앵커를 만든 환경에 대 한 시각적 정보가 충분 한지 과정이 됩니다. 클라이언트 구현은 라이브 콘텐츠에 대 한 사용을 계속 하기 전에 로컬 좌표계 또는 참조 프레임에 상대적인 앵커를 찾아야 합니다. 예를 들어 앵커를 과정이 시작할 때까지 현재 좌표계에 상대적인 앵커를 찾으려고 시도 합니다.

## <a name="special-considerations"></a>특별 고려 사항

[TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API를 사용 하면 여러 [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) 을 동일한 불투명 이진 blob으로 내보낼 수 있습니다. 그러나 단일 호출에서 단일 SpatialAnchor 또는 여러 SpatialAnchors를 내보낼지 여부에 따라 blob에 포함 되는 데이터에는 약간의 차이가 있습니다.

### <a name="export-of-a-single-spatialanchor"></a>단일 SpatialAnchor 내보내기

Blob에는 SpatialAnchor 주변 환경의 표현이 포함 되어 있으므로 SpatialAnchor를 가져오는 장치에서 환경을 인식할 수 있습니다. 가져오기가 완료 되 면 장치에서 새 SpatialAnchor를 사용할 수 있습니다. 사용자가 최근에 앵커 근처에 있는 것으로 가정 하 고, SpatialAnchor에 연결 된 holograms을 과정이 하 여 렌더링할 수 있습니다. 이러한 holograms는 SpatialAnchor를 내보낸 원래 장치에서 수행한 것과 동일한 물리적 위치에 표시 됩니다.

![단일 SpatialAnchor 내보내기](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>여러 SpatialAnchors 내보내기

단일 SpatialAnchor 내보내기와 마찬가지로 blob에는 지정 된 모든 SpatialAnchors 주변 환경의 표현이 포함 되어 있습니다. 또한 blob에는 포함 된 SpatialAnchors 간의 연결에 대 한 정보 (동일한 실제 공간에 있는 경우)가 포함 됩니다. 즉, 인접 한 두 개의 SpatialAnchors를 가져온 경우 두 SpatialAnchors 간의 변환 계산에 충분 한 데이터가 blob에 포함 되어 있기 때문에 *두 번째* *SpatialAnchor에 연결* 된 홀로그램은 과정이 됩니다. 두 개의 SpatialAnchors (TryExportSpatialAnchors에 대 한 두 개의 개별 호출)를 개별적으로 내보낸 경우 첫 번째 SpatialAnchor에 연결 된 holograms에 대 한 blob에 포함 된 데이터가 충분 하지 않을 수 있습니다.

![단일 TryExportAnchorsAsync 호출을 사용 하 여 내보낸 여러 앵커](images/multipleanchors.png) ![각 앵커에 대해 별도의 TryExportAnchorsAsync 호출을 사용 하 여 내보낸 여러 앵커](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>예: Windows:: 네트워킹:: StreamSocket을 사용 하 여 앵커 데이터 보내기

여기서는 내보낸 앵커 데이터를 TCP 네트워크를 통해 전송 하 여 사용 하는 방법에 대 한 예제를 제공 합니다. 이는 HolographicSpatialAnchorTransferSample에서 가져온 것입니다.

WinRT StreamSocket 클래스는 PPL 작업 라이브러리를 사용 합니다. 네트워크 오류의 경우 다시 throw 되는 예외를 사용 하 여 체인의 다음 태스크에 오류가 반환 됩니다. 예외에는 오류 상태를 나타내는 HRESULT가 포함 됩니다.

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Windows:: 네트워킹:: StreamSocketListener를 TCP와 함께 사용 하 여 내보낸 앵커 데이터 보내기

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

연결이 수신 되 면 클라이언트 소켓 연결을 사용 하 여 앵커 데이터를 보냅니다.

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

이제 내보낸 앵커 데이터를 포함 하는 데이터 스트림을 보낼 수 있습니다.

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

스트림 자체를 보내기 전에 먼저 헤더 패킷을 보내야 합니다. 이 헤더 패킷은 고정 길이 여야 하 고, 앵커 데이터 스트림 인 바이트 배열 길이를 나타내야 합니다. 이 예제의 경우 보낼 다른 헤더 데이터가 없으므로 헤더의 길이는 4 바이트이 고 32 비트의 부호 없는 정수를 포함 합니다.

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

스트림 길이 (바이트)가 클라이언트에 전송 되 면 데이터 스트림 자체를 소켓 스트림에 쓸 수 있습니다. 이렇게 하면 앵커 저장소 바이트가 클라이언트에 전송 됩니다.

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

이 항목의 앞부분에서 설명한 대로 네트워크 오류 상태 메시지를 포함 하는 예외를 처리 하도록 준비 해야 합니다. 예기치 않은 오류에 대 한 예외 정보를 디버그 콘솔에 기록할 수 있습니다 (예:). 이렇게 하면 코드 샘플에서 연결을 완료할 수 없거나 앵커 데이터 보내기를 완료할 수 없는 경우 발생 하는 결과에 대 한 단서를 제공 합니다.

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Windows:: 네트워킹:: StreamSocket을 TCP와 함께 사용 하 여 내보낸 앵커 데이터 받기

먼저 서버에 연결 해야 합니다. 이 코드 샘플에서는 StreamSocket을 만들고 구성 하는 방법과 소켓 연결을 사용 하 여 네트워크 데이터를 가져오는 데 사용할 수 있는 DataReader를 만드는 방법을 보여 줍니다.

**참고:** 이 샘플 코드를 실행 하는 경우 클라이언트를 시작 하기 전에 서버를 구성 하 고 시작 해야 합니다.

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

연결이 되 면 서버에서 데이터를 보낼 때까지 기다릴 수 있습니다. 스트림 데이터 판독기에서 LoadAsync를 호출 하 여이 작업을 수행 합니다.

수신 하는 첫 번째 바이트 집합은 항상 헤더 패킷이 며, 이전 섹션에서 설명한 대로 앵커 데이터 스트림 바이트 길이를 나타냅니다.

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

헤더 패킷을 받은 후에는 예측 해야 하는 앵커 데이터의 바이트 수를 알 수 있습니다. 스트림에서 이러한 바이트를 계속 읽을 수 있습니다.

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

앵커 데이터 스트림을 수신 하기 위한 코드는 다음과 같습니다. 여기서는 먼저 스트림에서 바이트를 로드 합니다. 이 작업을 완료 하는 데 다소 시간이 걸릴 수 있습니다.

로드 작업이 완료 되 면 해당 바이트 수를 읽을 수 있습니다. 앵커 데이터 스트림에 필요한 바이트 수를 받은 경우 계속 해 서 앵커 데이터를 가져올 수 있습니다. 그렇지 않은 경우에는 일종의 오류가 발생 해야 합니다. 예를 들어이 문제는 서버 인스턴스가 데이터 스트림 전송을 마치기 전에 종료 되거나 네트워크에서 중단 되어 전체 데이터 스트림을 클라이언트에서 받을 수 있는 경우에 발생할 수 있습니다.

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

또한 알 수 없는 네트워크 오류를 처리 하도록 준비 해야 합니다.

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

정말 간단하죠. 이제 네트워크를 통해 받은 앵커를 찾으려고 시도 하는 데 충분 한 정보가 있어야 합니다. 다시, 클라이언트는 앵커를 찾기 위해 공간에 대 한 충분 한 시각적 추적 데이터가 있어야 합니다. 바로 작동 하지 않는 경우 잠시 연습을 수행해 보세요. 그래도 작동 하지 않으면 서버에서 더 많은 앵커를 보내고 네트워크 통신을 사용 하 여 클라이언트에 적용 되는 것에 동의 합니다. HolographicSpatialAnchorTransferSample를 다운로드 하 고 클라이언트 및 서버 Ip를 구성 하 고 클라이언트 및 서버 HoloLens 장치에 배포 하 여이를 시험해 볼 수 있습니다.

## <a name="see-also"></a>참고 항목
* [PPL (병렬 패턴 라이브러리)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows. f i f. StreamSocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [StreamSocketListener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
