---
title: Unity에서 로컬 앵커 전송
description: 앵커 Unity 응용 프로그램에서 여러 HoloLens 장치 간에 전송 합니다.
author: fieldsJacksonG
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: 공유, 앵커, WorldAnchor, MR 공유 250, WorldAnchorTransferBatch, SpatialPerception, 전송, 로컬 앵커 전송, 앵커 내보내기, 앵커 가져오기
ms.openlocfilehash: 82bcd07417fd5aa1b265ebc3c8edc939101dd783
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605057"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="c51d8-104">Unity에서 로컬 앵커 전송</span><span class="sxs-lookup"><span data-stu-id="c51d8-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="c51d8-105">수 없는 상황 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>, 로컬 앵커 전송 두 번째 HoloLens 장치에서 가져올 앵커를 내보내려면 하나 HoloLens 장치를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="c51d8-106">로컬 앵커 전송을 제공 보다 덜 강력 앵커 회수 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>, iOS 및 Android 장치의이 방식으로 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="c51d8-107">SpatialPerception 기능 설정</span><span class="sxs-lookup"><span data-stu-id="c51d8-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="c51d8-108">공간 앵커를 전송 하는 앱에 대 한 순서로 합니다 *SpatialPerception* 기능을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="c51d8-109">사용 하도록 설정 하는 방법을 합니다 *SpatialPerception* 기능:</span><span class="sxs-lookup"><span data-stu-id="c51d8-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="c51d8-110">Unity 편집기에서 엽니다는 **"플레이어 설정"** 창 (편집 > 프로젝트 설정 > Player)</span><span class="sxs-lookup"><span data-stu-id="c51d8-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="c51d8-111">클릭 합니다 **"Windows Store"** 탭</span><span class="sxs-lookup"><span data-stu-id="c51d8-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="c51d8-112">확장 **"게시 설정"** 확인 합니다 **"SpatialPerception"** 의 기능을 **"기능"** 목록</span><span class="sxs-lookup"><span data-stu-id="c51d8-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="c51d8-113">이미 Unity 프로젝트를 Visual Studio 솔루션을 내보낸 경우 해야 새 폴더 또는 수동으로 내보낼 [이 기능은 Visual Studio에서 AppxManifest 설정](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)합니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="c51d8-114">앵커 전송</span><span class="sxs-lookup"><span data-stu-id="c51d8-114">Anchor Transfer</span></span>

<span data-ttu-id="c51d8-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span><span class="sxs-lookup"><span data-stu-id="c51d8-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="c51d8-116">**형식**: *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="c51d8-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="c51d8-117">전송 하는 [WorldAnchor](coordinate-systems-in-unity.md), 하나 전송할 앵커를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="c51d8-118">하나의 HoloLens의 사용자는 자신의 환경을 검색 하 고 수동으로 또는 프로그래밍 방식으로 공간을 공유 환경에 대 한 앵커의 시점을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="c51d8-119">이 점을 나타내는 데이터 직렬화 및 환경에서 공유 하는 다른 장치에 전송 될 수입니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="c51d8-120">그런 다음 각 장치는 앵커 데이터를 역직렬화 하 고 공간에서 해당 지점을 찾으려고 시도.</span><span class="sxs-lookup"><span data-stu-id="c51d8-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="c51d8-121">앵커 전송 작업에 대 한 순서를 나타내는 앵커 지점을 식별할 수 있도록 각 장치를 충분히 환경에서 검색 한 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="c51d8-122">설치 프로그램</span><span class="sxs-lookup"><span data-stu-id="c51d8-122">Setup</span></span>

<span data-ttu-id="c51d8-123">이 페이지의 샘플 코드에 초기화 해야 하는 몇 가지 필드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="c51d8-124">*GameObject rootGameObject* 은 *GameObject* 에 Unity의를 *WorldAnchor* 에 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="c51d8-125">이 공유 환경에서 한 명의 사용자 배치할 *GameObject* 및 다른 사용자에 게 데이터 내보내기.</span><span class="sxs-lookup"><span data-stu-id="c51d8-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="c51d8-126">*WorldAnchor gameRootAnchor* 되는 *UnityEngine.XR.WSA.WorldAnchor* 켜져 있는 *rootGameObject*합니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="c51d8-127">*바이트 importedData* 각 클라이언트가 네트워크를 통해 받고 serialize 된 앵커에 대 한 바이트 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a><span data-ttu-id="c51d8-128">내보내기</span><span class="sxs-lookup"><span data-stu-id="c51d8-128">Exporting</span></span>

<span data-ttu-id="c51d8-129">내보내려면 하기만 *WorldAnchor* 및 새로운이 라는 수신 응용 프로그램에 적합 한 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="c51d8-130">공유 환경에서 하나의 클라이언트 공유 앵커를 내보내려면 다음이 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="c51d8-131">만들기는 *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="c51d8-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="c51d8-132">추가 된 *WorldAnchors* 전송할</span><span class="sxs-lookup"><span data-stu-id="c51d8-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="c51d8-133">내보내기 시작</span><span class="sxs-lookup"><span data-stu-id="c51d8-133">Begin the export</span></span>
4. <span data-ttu-id="c51d8-134">처리를 *OnExportDataAvailable* 데이터로 이벤트에는 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="c51d8-135">처리를 *OnExportComplete* 이벤트</span><span class="sxs-lookup"><span data-stu-id="c51d8-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="c51d8-136">만듭니다는 *WorldAnchorTransferBatch* 무엇을 캡슐화 하에서는 전송 되며 다음 바이트에 내보낼:</span><span class="sxs-lookup"><span data-stu-id="c51d8-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="c51d8-137">데이터를 사용할 수 있게 되 면 바이트 클라이언트 또는 버퍼에 데이터의 세그먼트를 사용할 수 있으므로 보내고 원하는 모든 수단을 통해:</span><span class="sxs-lookup"><span data-stu-id="c51d8-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="c51d8-138">내보내기에서는 데이터 및 실패 한 serialization 전송 된 있을 경우 완료 되 면 데이터를 삭제 하도록 클라이언트를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="c51d8-139">Serialization에 성공한 경우 모든 데이터가 전송 되었는지을 시작할 수를 가져오는 클라이언트에 게 알리는:</span><span class="sxs-lookup"><span data-stu-id="c51d8-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a><span data-ttu-id="c51d8-140">가져오기</span><span class="sxs-lookup"><span data-stu-id="c51d8-140">Importing</span></span>

<span data-ttu-id="c51d8-141">모든 바이트를 보낸 사람 으로부터 받은 후에 다시 데이터를 가져올 수 있습니다는 *WorldAnchorTransferBatch* 동일한 물리적 위치로 루트 게임 개체를 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="c51d8-142">참고 가져오기 때로는 일시적으로 실패 하 고 다시 시도해 야 합니다.:</span><span class="sxs-lookup"><span data-stu-id="c51d8-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

<span data-ttu-id="c51d8-143">후를 *GameObject* 통해 잠겨 합니다 *LockObject* 갖습니다 하 호출을 *WorldAnchor* 환경에서는 동일한 실제 위치에 유지 됩니다는 하지만에 있을 수는 Unity에서 다른 위치로 다른 사용자 보다는 공간을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51d8-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

