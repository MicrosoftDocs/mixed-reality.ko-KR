---
title: DirectX의 로컬 앵커 전송
description: 공간 앵커를 전송 하 여 두 HoloLens 장치를 동기화 하는 방법을 설명 합니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 동기화, 공간 앵커, 전송, 여럿이, 보기, 시나리오, 연습, 샘플 코드, 전송, 로컬 앵커 전송, 앵커 내보내기, 앵커 가져오기
ms.openlocfilehash: f961862c3c49872484683e264fb9c62b5d0b60ee
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437961"
---
# <a name="local-anchor-transfers-in-directx"></a><span data-ttu-id="3cd19-104">DirectX의 로컬 앵커 전송</span><span class="sxs-lookup"><span data-stu-id="3cd19-104">Local anchor transfers in DirectX</span></span>

<span data-ttu-id="3cd19-105"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>를 사용할 수 없는 경우 로컬 앵커 전송에서는 한 hololens 장치에서 두 번째 hololens 장치에서 가져올 앵커를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="3cd19-106">로컬 앵커 전송은 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>보다 더 강력 하지 않은 앵커 회수를 제공 하며, IOS 및 Android 장치는이 방식에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

>[!NOTE]
><span data-ttu-id="3cd19-107">이 문서의 코드 조각은 현재 [ C++ holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되 C++는 것 처럼 C + 17-so-far working 규격 C++/winrt 대신/cx 사용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="3cd19-108">개념은 C++/winrt 프로젝트와 동일 하지만 코드를 변환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="transferring-spatial-anchors"></a><span data-ttu-id="3cd19-109">공간 앵커 전송</span><span class="sxs-lookup"><span data-stu-id="3cd19-109">Transferring spatial anchors</span></span>

<span data-ttu-id="3cd19-110">[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)를 사용 하 여 Windows Mixed Reality 장치 간에 공간 앵커를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-110">You can transfer spatial anchors between Windows Mixed Reality devices by using the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="3cd19-111">이 API를 사용 하면 전 세계의 정확한 위치를 찾는 데 필요한 모든 지원 센서 데이터를 사용 하 여 앵커를 번들로 묶은 다음 해당 번들을 다른 장치에서 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-111">This API lets you bundle up an anchor with all the supporting sensor data needed to find that exact place in the world, and then import that bundle on another device.</span></span> <span data-ttu-id="3cd19-112">두 번째 장치의 앱이 해당 앵커를 가져온 후에는 각 앱이 해당 공유 공간 앵커의 좌표계를 사용 하 여 holograms를 렌더링할 수 있습니다. 그러면 실제 세계의 동일한 위치에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-112">Once the app on the second device has imported that anchor, each app can render holograms using that shared spatial anchor's coordinate system, which will then appear in the same place in the real world.</span></span>

<span data-ttu-id="3cd19-113">공간 앵커는 서로 다른 장치 유형 간에 전송할 수 없습니다. 예를 들어 HoloLens 공간 앵커는 몰입 형 헤드셋을 사용 하 여 과정이 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-113">Note that spatial anchors are not able to transfer between different device types, for example a HoloLens spatial anchor may not be locatable using an immersive headset.</span></span>  <span data-ttu-id="3cd19-114">전송 된 앵커도 iOS 또는 Android 장치와 호환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-114">Transferred anchors are also not compatible with iOS or Android devices.</span></span>

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="3cd19-115">SpatialPerception 기능을 사용 하도록 앱 설정</span><span class="sxs-lookup"><span data-stu-id="3cd19-115">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="3cd19-116">앱에는 [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)를 사용 하기 전에 spatialPerception 기능을 사용할 수 있는 권한이 부여 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-116">Your app must be granted permission to use the spatialPerception capability before it can use the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="3cd19-117">공간 앵커를 전송 하려면 해당 앵커 근처에서 시간에 따라 수집 된 센서 이미지를 공유 해야 합니다. 여기에는 중요 한 정보가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-117">This is necessary because transferring a spatial anchor involves sharing sensor images gathered over time in vicinity of that anchor, which might include sensitive information.</span></span>

<span data-ttu-id="3cd19-118">앱에 대 한 appxmanifest.xml 파일에서이 기능을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-118">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="3cd19-119">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-119">Here's an example:</span></span>

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="3cd19-120">이 기능은 **uap2** 네임 스페이스에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-120">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="3cd19-121">매니페스트에이 네임 스페이스에 대 한 액세스 권한을 얻으려면이를 &lt;Package > 요소에 *xlmns* 특성으로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-121">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="3cd19-122">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-122">Here's an example:</span></span>

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

<span data-ttu-id="3cd19-123">**참고:** 앱은 런타임에 SpatialAnchor 내보내기/가져오기 Api에 액세스할 수 있는 기능을 요청 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-123">**NOTE:** Your app will need to request the capability at runtime before it can access SpatialAnchor export/import APIs.</span></span> <span data-ttu-id="3cd19-124">아래 예제에서 [Requestaccessasync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3cd19-124">See [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in the examples below.</span></span>

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a><span data-ttu-id="3cd19-125">SpatialAnchorTransferManager로 내보내서 앵커 데이터를 직렬화 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-125">Serialize anchor data by exporting it with the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="3cd19-126">도우미 함수는 [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) 데이터를 내보내기 (직렬화) 하는 코드 샘플에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-126">A helper function is included in the code sample to export (serialize) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) data.</span></span> <span data-ttu-id="3cd19-127">이 내보내기 API는 앵커와 함께 문자열을 연결 하는 키-값 쌍 컬렉션의 모든 앵커를 직렬화 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-127">This export API serializes all anchors in a collection of key-value pairs associating strings with anchors.</span></span>

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

<span data-ttu-id="3cd19-128">먼저 데이터 스트림을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-128">First, we need to set up the data stream.</span></span> <span data-ttu-id="3cd19-129">이렇게 하면 1이 됩니다.) TryExportAnchorsAsync를 사용 하 여 응용 프로그램 소유의 버퍼에 데이터를 저장 하 고 2를 사용 합니다.) WinRT 데이터 스트림 인 내보낸 바이트 버퍼 스트림에서 데이터를 std:: vector&lt;byte >의 고유한 메모리 버퍼로 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-129">This will allow us to 1.) use TryExportAnchorsAsync to put the data in a buffer owned by the app, and 2.) read data from the exported byte buffer stream - which is a WinRT data stream - into our own memory buffer, which is a std::vector&lt;byte>.</span></span>

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

<span data-ttu-id="3cd19-130">시스템에서 내보내는 앵커를 비롯 하 여 공간 데이터에 액세스 하기 위한 권한을 요청 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-130">We need to ask permission to access spatial data, including anchors that are exported by the system.</span></span>

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

<span data-ttu-id="3cd19-131">Get 권한이 있고 앵커를 내보내는 경우 데이터 스트림을 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-131">If we do get permission and anchors are exported, we can read the data stream.</span></span> <span data-ttu-id="3cd19-132">여기서는 데이터를 읽는 데 사용할 DataReader 및 InputStream를 만드는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-132">Here, we also show how to create the DataReader and InputStream we will use to read the data.</span></span>

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

<span data-ttu-id="3cd19-133">스트림에서 바이트를 읽은 후와 같이 자체 데이터 버퍼에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-133">After we read bytes from the stream, we can save them to our own data buffer like so.</span></span>

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a><span data-ttu-id="3cd19-134">SpatialAnchorTransferManager를 사용 하 여 시스템으로 가져와 앵커 데이터를 Deserialize 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-134">Deserialize anchor data by importing it into the system using the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="3cd19-135">코드 샘플에는 이전에 내보낸 데이터를 로드 하는 도우미 함수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-135">A helper function is included in the code sample to load previously exported data.</span></span> <span data-ttu-id="3cd19-136">이 deserialization 함수는 SpatialAnchorStore에서 제공 하는 것과 비슷한 키-값 쌍의 컬렉션을 제공 합니다. 단, 네트워크 소켓과 같은 다른 원본에서이 데이터를 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-136">This deserialization function provides a collection of key-value pairs, similar to what the SpatialAnchorStore provides - except that we got this data from another source, such as a network socket.</span></span> <span data-ttu-id="3cd19-137">앱 내 메모리 또는 앱의 SpatialAnchorStore (해당 하는 경우)를 사용 하 여 오프 라인으로 저장 하기 전에이 데이터를 처리 하 고 이유를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-137">You can process and reason about this data before storing it offline, using in-app memory, or (if applicable) your app's SpatialAnchorStore.</span></span>

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

<span data-ttu-id="3cd19-138">먼저, 고정 데이터에 액세스 하기 위해 stream 개체를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-138">First, we need to create stream objects to access the anchor data.</span></span> <span data-ttu-id="3cd19-139">버퍼의 데이터를 시스템 버퍼에 기록할 것 이므로 메모리 내 데이터 스트림에 쓰는 Datawriter 여부를 만들어 바이트 버퍼에서 시스템에 SpatialAnchors로의 앵커를 가져오는 목표를 달성 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-139">We will be writing the data from our buffer to a system buffer, so we will create a DataWriter that writes to an in-memory data stream in order to accomplish our goal of getting anchors from a byte buffer into the system as SpatialAnchors.</span></span>

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

<span data-ttu-id="3cd19-140">다시 한 번, 앱에는 사용자 환경에 대 한 개인 정보를 포함할 수 있는 공간 앵커 데이터를 내보낼 수 있는 권한이 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-140">Once again, we need to ensure the app has permission to export spatial anchor data, which could include private information about the user's environment.</span></span>

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

<span data-ttu-id="3cd19-141">액세스가 허용 되 면 버퍼에서 시스템 데이터 스트림으로 바이트를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-141">If access is allowed, we can write bytes from the buffer to a system data stream.</span></span>

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

<span data-ttu-id="3cd19-142">데이터 스트림에 바이트를 저장 하는 데 성공 하면 SpatialAnchorTransferManager를 사용 하 여 해당 데이터를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-142">If we were successful in storing bytes in the data stream, we can try to import that data using the SpatialAnchorTransferManager.</span></span>

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

<span data-ttu-id="3cd19-143">데이터를 가져올 수 있는 경우 문자열을 앵커와 연결 하는 키-값 쌍의 지도 보기가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-143">If the data is able to be imported, we get a map view of key-value pairs associating strings with anchors.</span></span> <span data-ttu-id="3cd19-144">이를 자체 메모리 내 데이터 컬렉션에 로드 하 고 해당 컬렉션을 사용 하 여 사용 하려는 앵커를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-144">We can load this into our own in-memory data collection, and use that collection to look for anchors that we are interested in using.</span></span>

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

<span data-ttu-id="3cd19-145">**참고:** 앵커를 가져올 수 있기 때문에이는 바로 사용할 수 있다는 의미는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-145">**NOTE:** Just because you can import an anchor, doesn't necessarily mean that you can use it right away.</span></span> <span data-ttu-id="3cd19-146">앵커는 다른 방 또는 다른 실제 위치에 완전히 있을 수 있습니다. 앵커는 알려진 현재 환경에 상대적인 앵커의 위치를 복원 하기 위해 앵커를 만든 환경에 대 한 시각적 정보가 충분 한지 과정이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-146">The anchor might be in a different room, or another physical location entirely; the anchor won't be locatable until the device that received it has enough visual information about the environment the anchor was created in, to restore the anchor's position relative to the known current environment.</span></span> <span data-ttu-id="3cd19-147">클라이언트 구현은 라이브 콘텐츠에 대 한 사용을 계속 하기 전에 로컬 좌표계 또는 참조 프레임에 상대적인 앵커를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-147">The client implementation should try locating the anchor relative to your local coordinate system or reference frame before continuing on to try to use it for live content.</span></span> <span data-ttu-id="3cd19-148">예를 들어 앵커를 과정이 시작할 때까지 현재 좌표계에 상대적인 앵커를 찾으려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-148">For example, try locating the anchor relative to a current coordinate system periodically until the anchor begins to be locatable.</span></span>

## <a name="special-considerations"></a><span data-ttu-id="3cd19-149">특별 고려 사항</span><span class="sxs-lookup"><span data-stu-id="3cd19-149">Special Considerations</span></span>

<span data-ttu-id="3cd19-150">[TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API를 사용 하면 여러 [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) 을 동일한 불투명 이진 blob으로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-150">The [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API allows multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) to be exported into the same opaque binary blob.</span></span> <span data-ttu-id="3cd19-151">그러나 단일 호출에서 단일 SpatialAnchor 또는 여러 SpatialAnchors를 내보낼지 여부에 따라 blob에 포함 되는 데이터에는 약간의 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-151">However, there is a subtle difference in what data the blob will include, depending on whether a single SpatialAnchor or multiple SpatialAnchors are exported in a single call.</span></span>

### <a name="export-of-a-single-spatialanchor"></a><span data-ttu-id="3cd19-152">단일 SpatialAnchor 내보내기</span><span class="sxs-lookup"><span data-stu-id="3cd19-152">Export of a single SpatialAnchor</span></span>

<span data-ttu-id="3cd19-153">Blob에는 SpatialAnchor 주변 환경의 표현이 포함 되어 있으므로 SpatialAnchor를 가져오는 장치에서 환경을 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-153">The blob contains a representation of the environment in the vicinity of the SpatialAnchor so that the environment can be recognized on the device that imports the SpatialAnchor.</span></span> <span data-ttu-id="3cd19-154">가져오기가 완료 되 면 장치에서 새 SpatialAnchor를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-154">After the import completes, the new SpatialAnchor will be available to the device.</span></span> <span data-ttu-id="3cd19-155">사용자가 최근에 앵커 근처에 있는 것으로 가정 하 고, SpatialAnchor에 연결 된 holograms을 과정이 하 여 렌더링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-155">Assuming the user has recently been in vicinity of the anchor, it will be locatable and holograms attached to the SpatialAnchor can be rendered.</span></span> <span data-ttu-id="3cd19-156">이러한 holograms는 SpatialAnchor를 내보낸 원래 장치에서 수행한 것과 동일한 물리적 위치에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-156">These holograms will show up in the same physical location that they did on the original device which exported the SpatialAnchor.</span></span>

![단일 SpatialAnchor 내보내기](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a><span data-ttu-id="3cd19-158">여러 SpatialAnchors 내보내기</span><span class="sxs-lookup"><span data-stu-id="3cd19-158">Export of multiple SpatialAnchors</span></span>

<span data-ttu-id="3cd19-159">단일 SpatialAnchor 내보내기와 마찬가지로 blob에는 지정 된 모든 SpatialAnchors 주변 환경의 표현이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-159">Like the export of a single SpatialAnchor, the blob contains a representation of the environment in the vicinity of all the specified SpatialAnchors.</span></span> <span data-ttu-id="3cd19-160">또한 blob에는 포함 된 SpatialAnchors 간의 연결에 대 한 정보 (동일한 실제 공간에 있는 경우)가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-160">In addition, the blob contains information about the connections between the included SpatialAnchors, if they are located in the same physical space.</span></span> <span data-ttu-id="3cd19-161">즉, 인접 한 두 개의 SpatialAnchors를 가져오는 경우 *두 번째* SpatialAnchor에 연결 된 홀로그램은 다음에 대 한 충분 한 데이터를 포함 하 여 *첫 번째* SpatialAnchor 주변 환경을 인식 하는 경우에도 과정이 됩니다. 두 SpatialAnchors 간의 계산 변환이 blob에 포함 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-161">This means that if two nearby SpatialAnchors are imported, then a hologram attached to the *second* SpatialAnchor would be locatable even if the device only recognizes the environment around the *first* SpatialAnchor, because enough data to compute transform between the two SpatialAnchors was included in the blob.</span></span> <span data-ttu-id="3cd19-162">두 개의 SpatialAnchors (TryExportSpatialAnchors에 대 한 두 개의 개별 호출)를 개별적으로 내보낸 경우 첫 번째 SpatialAnchor에 연결 된 holograms에 대 한 blob에 포함 된 데이터가 충분 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-162">If the two SpatialAnchors were exported individually (two separate calls to TryExportSpatialAnchors) then there may not be enough data included in the blob for holograms attached to the second SpatialAnchor to be locatable when the first one is located.</span></span>

![단일 TryExportAnchorsAsync 호출을 사용 하 여 내보낸 여러 앵커](images/multipleanchors.png) ![각 앵커에 대해 별도의 TryExportAnchorsAsync 호출을 사용 하 여 내보낸 여러 앵커](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a><span data-ttu-id="3cd19-165">예: Windows:: 네트워킹:: StreamSocket을 사용 하 여 앵커 데이터 보내기</span><span class="sxs-lookup"><span data-stu-id="3cd19-165">Example: Send anchor data using a Windows::Networking::StreamSocket</span></span>

<span data-ttu-id="3cd19-166">여기서는 내보낸 앵커 데이터를 TCP 네트워크를 통해 전송 하 여 사용 하는 방법에 대 한 예제를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-166">Here, we provide an example of how to use exported anchor data by sending it across a TCP network.</span></span> <span data-ttu-id="3cd19-167">이는 HolographicSpatialAnchorTransferSample에서 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-167">This is from the HolographicSpatialAnchorTransferSample.</span></span>

<span data-ttu-id="3cd19-168">WinRT StreamSocket 클래스는 PPL 작업 라이브러리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-168">The WinRT StreamSocket class uses the PPL task library.</span></span> <span data-ttu-id="3cd19-169">네트워크 오류의 경우 다시 throw 되는 예외를 사용 하 여 체인의 다음 태스크에 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-169">In the case of network errors, the error is returned to the next task in the chain using an exception that is re-thrown.</span></span> <span data-ttu-id="3cd19-170">예외에는 오류 상태를 나타내는 HRESULT가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-170">The exception contains an HRESULT indicating the error status.</span></span>

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a><span data-ttu-id="3cd19-171">Windows:: 네트워킹:: StreamSocketListener를 TCP와 함께 사용 하 여 내보낸 앵커 데이터 보내기</span><span class="sxs-lookup"><span data-stu-id="3cd19-171">Use a Windows::Networking::StreamSocketListener with TCP to send exported anchor data</span></span>

<span data-ttu-id="3cd19-172">연결을 수신 하는 서버 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-172">Create a server instance that listens for a connection.</span></span>

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

<span data-ttu-id="3cd19-173">연결이 수신 되 면 클라이언트 소켓 연결을 사용 하 여 앵커 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-173">When a connection is received, use the client socket connection to send anchor data.</span></span>

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

<span data-ttu-id="3cd19-174">이제 내보낸 앵커 데이터를 포함 하는 데이터 스트림을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-174">Now, we can begin to send a data stream that contains the exported anchor data.</span></span>

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

<span data-ttu-id="3cd19-175">스트림 자체를 보내기 전에 먼저 헤더 패킷을 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-175">Before we can send the stream itself, we must first send a header packet.</span></span> <span data-ttu-id="3cd19-176">이 헤더 패킷은 고정 길이 여야 하 고, 앵커 데이터 스트림 인 바이트 배열 길이를 나타내야 합니다. 이 예제의 경우 보낼 다른 헤더 데이터가 없으므로 헤더의 길이는 4 바이트이 고 32 비트의 부호 없는 정수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-176">This header packet must be of fixed length, and it must also indicate the length of the variable array of bytes that is the anchor data stream; in the case of this example we have no other header data to send, so our header is 4 bytes long and contains a 32-bit unsigned integer.</span></span>

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

<span data-ttu-id="3cd19-177">스트림 길이 (바이트)가 클라이언트에 전송 되 면 데이터 스트림 자체를 소켓 스트림에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-177">Once the stream length, in bytes, has been sent to the client, we can proceed to write the data stream itself to the socket stream.</span></span> <span data-ttu-id="3cd19-178">이렇게 하면 앵커 저장소 바이트가 클라이언트에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-178">This will cause the anchor store bytes to get sent to the client.</span></span>

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

<span data-ttu-id="3cd19-179">이 항목의 앞부분에서 설명한 대로 네트워크 오류 상태 메시지를 포함 하는 예외를 처리 하도록 준비 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-179">As noted earlier in this topic, we must be prepared to handle exceptions containing network error status messages.</span></span> <span data-ttu-id="3cd19-180">예기치 않은 오류에 대 한 예외 정보를 디버그 콘솔에 기록할 수 있습니다 (예:).</span><span class="sxs-lookup"><span data-stu-id="3cd19-180">For errors that are not expected, we can write the exception info to the debug console like so.</span></span> <span data-ttu-id="3cd19-181">이렇게 하면 코드 샘플에서 연결을 완료할 수 없거나 앵커 데이터 보내기를 완료할 수 없는 경우 발생 하는 결과에 대 한 단서를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-181">This will give us a clue as to what happened if our code sample is unable to complete the connection, or if it is unable to finish sending the anchor data.</span></span>

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a><span data-ttu-id="3cd19-182">Windows:: 네트워킹:: StreamSocket을 TCP와 함께 사용 하 여 내보낸 앵커 데이터 받기</span><span class="sxs-lookup"><span data-stu-id="3cd19-182">Use a Windows::Networking::StreamSocket with TCP to receive exported anchor data</span></span>

<span data-ttu-id="3cd19-183">먼저 서버에 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-183">First, we have to connect to the server.</span></span> <span data-ttu-id="3cd19-184">이 코드 샘플에서는 StreamSocket을 만들고 구성 하는 방법과 소켓 연결을 사용 하 여 네트워크 데이터를 가져오는 데 사용할 수 있는 DataReader를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-184">This code sample shows how to create and configure a StreamSocket, and create a DataReader that you can use to acquire network data using the socket connection.</span></span>

<span data-ttu-id="3cd19-185">**참고:** 이 샘플 코드를 실행 하는 경우 클라이언트를 시작 하기 전에 서버를 구성 하 고 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-185">**NOTE:** If you run this sample code, ensure that you configure and launch the server before starting the client.</span></span>

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

<span data-ttu-id="3cd19-186">연결이 되 면 서버에서 데이터를 보낼 때까지 기다릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-186">Once we have a connection, we can wait for the server to send data.</span></span> <span data-ttu-id="3cd19-187">스트림 데이터 판독기에서 LoadAsync를 호출 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-187">We do this by calling LoadAsync on the stream data reader.</span></span>

<span data-ttu-id="3cd19-188">수신 하는 첫 번째 바이트 집합은 항상 헤더 패킷이 며, 이전 섹션에서 설명한 대로 앵커 데이터 스트림 바이트 길이를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-188">The first set of bytes we receive should always be the header packet, which indicates the anchor data stream byte length as described in the previous section.</span></span>

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

<span data-ttu-id="3cd19-189">...</span><span class="sxs-lookup"><span data-stu-id="3cd19-189">...</span></span>

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

<span data-ttu-id="3cd19-190">헤더 패킷을 받은 후에는 예측 해야 하는 앵커 데이터의 바이트 수를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-190">After we have received the header packet, we know how many bytes of anchor data we should expect.</span></span> <span data-ttu-id="3cd19-191">스트림에서 이러한 바이트를 계속 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-191">We can proceed to read those bytes from the stream.</span></span>

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

<span data-ttu-id="3cd19-192">앵커 데이터 스트림을 수신 하기 위한 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-192">Here's our code for receiving the anchor data stream.</span></span> <span data-ttu-id="3cd19-193">여기서는 먼저 스트림에서 바이트를 로드 합니다. 이 작업을 완료 하는 데 다소 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-193">Again, we will first load the bytes from the stream; this operation may take some time to complete as the StreamSocket waits to receive that amount of bytes from the network.</span></span>

<span data-ttu-id="3cd19-194">로드 작업이 완료 되 면 해당 바이트 수를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-194">When the loading operation is complete, we can read that number of bytes.</span></span> <span data-ttu-id="3cd19-195">앵커 데이터 스트림에 필요한 바이트 수를 받은 경우 계속 해 서 앵커 데이터를 가져올 수 있습니다. 그렇지 않은 경우에는 일종의 오류가 발생 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-195">If we received the number of bytes that we expect for the anchor data stream, we can go ahead and import the anchor data; if not, there must have been some sort of error.</span></span> <span data-ttu-id="3cd19-196">예를 들어이 문제는 서버 인스턴스가 데이터 스트림 전송을 마치기 전에 종료 되거나 네트워크에서 중단 되어 전체 데이터 스트림을 클라이언트에서 받을 수 있는 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-196">For example, this can happen when the server instance terminates before it can finish sending the data stream, or the network goes down before the entire data stream can be received by the client.</span></span>

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

<span data-ttu-id="3cd19-197">또한 알 수 없는 네트워크 오류를 처리 하도록 준비 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-197">Again, we must be prepared to handle unknown network errors.</span></span>

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

<span data-ttu-id="3cd19-198">이제 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-198">That's it!</span></span> <span data-ttu-id="3cd19-199">이제 네트워크를 통해 받은 앵커를 찾으려고 시도 하는 데 충분 한 정보가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-199">Now, you should have enough information to try locating the anchors received over the network.</span></span> <span data-ttu-id="3cd19-200">다시, 클라이언트는 앵커를 찾기 위해 공간에 대 한 충분 한 시각적 추적 데이터가 있어야 합니다. 바로 작동 하지 않는 경우 잠시 연습을 수행해 보세요.</span><span class="sxs-lookup"><span data-stu-id="3cd19-200">Again, note that the client must have enough visual tracking data for the space to successfully locate the anchor; if it doesn't work right away, try walking around for a while.</span></span> <span data-ttu-id="3cd19-201">그래도 작동 하지 않으면 서버에서 더 많은 앵커를 보내고 네트워크 통신을 사용 하 여 클라이언트에 적용 되는 것에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-201">If it still doesn't work, have the server send more anchors, and use network communications to agree on one that works for the client.</span></span> <span data-ttu-id="3cd19-202">HolographicSpatialAnchorTransferSample를 다운로드 하 고 클라이언트 및 서버 Ip를 구성 하 고 클라이언트 및 서버 HoloLens 장치에 배포 하 여이를 시험해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3cd19-202">You can try this out by downloading the HolographicSpatialAnchorTransferSample, configuring your client and server IPs, and deploying it to client and server HoloLens devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="3cd19-203">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3cd19-203">See also</span></span>
* [<span data-ttu-id="3cd19-204">PPL (병렬 패턴 라이브러리)</span><span class="sxs-lookup"><span data-stu-id="3cd19-204">Parallel Patterns Library (PPL)</span></span>](https://msdn.microsoft.com/library/dd492418.aspx)
* [<span data-ttu-id="3cd19-205">Windows. f i f. StreamSocket</span><span class="sxs-lookup"><span data-stu-id="3cd19-205">Windows.Networking.StreamSocket</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [<span data-ttu-id="3cd19-206">StreamSocketListener</span><span class="sxs-lookup"><span data-stu-id="3cd19-206">Windows.Networking.StreamSocketListener</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
