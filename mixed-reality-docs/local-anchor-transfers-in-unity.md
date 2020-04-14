---
title: Unity의 로컬 앵커 전송
description: Unity 응용 프로그램에서 여러 HoloLens 장치 간에 앵커를 전송 합니다.
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: 공유, 고정, WorldAnchor, MR 공유 250, WorldAnchorTransferBatch, SpatialPerception, 전송, 로컬 앵커 전송, 앵커 내보내기, 앵커 가져오기
ms.openlocfilehash: fd071f736add094fd65ae4d889f8008eefd8515d
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278061"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="f0596-104">Unity의 로컬 앵커 전송</span><span class="sxs-lookup"><span data-stu-id="f0596-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="f0596-105"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>를 사용할 수 없는 경우 로컬 앵커 전송에서는 한 hololens 장치에서 두 번째 hololens 장치에서 가져올 앵커를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="f0596-106">로컬 앵커 전송은 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>보다 더 강력 하지 않은 앵커 회수를 제공 하며, IOS 및 Android 장치는이 방식에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="f0596-107">SpatialPerception 기능 설정</span><span class="sxs-lookup"><span data-stu-id="f0596-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="f0596-108">앱이 공간 앵커를 전송 하려면 *SpatialPerception* 기능을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="f0596-109">*SpatialPerception* 기능을 사용 하도록 설정 하는 방법:</span><span class="sxs-lookup"><span data-stu-id="f0596-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="f0596-110">Unity 편집기에서 **"플레이어 설정"** 창 (편집 > 프로젝트 설정 > 플레이어)을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="f0596-111">**"Windows 스토어"** 탭을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="f0596-112">" **게시 설정"** 을 확장 하 고 " **기능"** 목록에서 **"SpatialPerception"** 기능을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="f0596-113">Unity 프로젝트를 Visual Studio 솔루션으로 이미 내보낸 경우에는 새 폴더로 내보내거나 [Visual studio의 appxmanifest.xml에서이 기능](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)을 수동으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="f0596-114">앵커 전송</span><span class="sxs-lookup"><span data-stu-id="f0596-114">Anchor Transfer</span></span>

<span data-ttu-id="f0596-115">**네임 스페이스:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="f0596-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="f0596-116">**유형**: *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="f0596-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="f0596-117">[WorldAnchor](coordinate-systems-in-unity.md)를 전송 하려면 전송할 앵커를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-117">To transfer a [WorldAnchor](coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="f0596-118">한 HoloLens 사용자는 자신의 환경을 검색 하 고 수동으로 또는 프로그래밍 방식으로 공간에서 공유 환경의 앵커로 지정 된 지점을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="f0596-119">그런 다음이 지점을 나타내는 데이터를 직렬화 하 고 환경에서 공유 되는 다른 장치로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="f0596-120">그런 다음 각 장치는 앵커 데이터를 역직렬화 하 고 공간에서 해당 지점을 찾으려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="f0596-121">Anchor 전송이 작동 하려면 각 장치에서 앵커가 나타내는 점을 식별할 수 있도록 충분 한 환경에서 검색 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="f0596-122">설치</span><span class="sxs-lookup"><span data-stu-id="f0596-122">Setup</span></span>

<span data-ttu-id="f0596-123">이 페이지의 샘플 코드에는 초기화 해야 하는 몇 가지 필드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="f0596-124">*GameObject rootGameObject* 는 *WorldAnchor* 구성 요소가 있는 Unity의 *GameObject* 입니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="f0596-125">공유 환경의 한 사용자가이 *GameObject* 를 추가 하 고 다른 사용자에 게 데이터를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="f0596-126">*WorldAnchor gameRootAnchor* 는 *RootGameObject*에 있는 *unityengine. WorldAnchor* 입니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="f0596-127">*byte [] importedData* 는 각 클라이언트가 네트워크를 통해 수신 하는 직렬화 된 앵커의 바이트 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

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

### <a name="exporting"></a><span data-ttu-id="f0596-128">내보내려면</span><span class="sxs-lookup"><span data-stu-id="f0596-128">Exporting</span></span>

<span data-ttu-id="f0596-129">이를 내보내려면 수신 앱에 적합 하도록 *WorldAnchor* 및이를 호출 하는 것을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="f0596-130">공유 환경의 한 클라이언트는 다음 단계를 수행 하 여 공유 앵커를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="f0596-131">*WorldAnchorTransferBatch* 만들기</span><span class="sxs-lookup"><span data-stu-id="f0596-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="f0596-132">전송할 *WorldAnchors* 추가</span><span class="sxs-lookup"><span data-stu-id="f0596-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="f0596-133">내보내기 시작</span><span class="sxs-lookup"><span data-stu-id="f0596-133">Begin the export</span></span>
4. <span data-ttu-id="f0596-134">데이터를 사용할 수 있게 되 면 *Onexportdataavailable* 이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="f0596-135">*Onexportcomplete* 이벤트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="f0596-136">전송 될 항목을 캡슐화 하는 *WorldAnchorTransferBatch* 를 만든 다음이를 바이트로 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="f0596-137">데이터를 사용할 수 있게 되 면 데이터 세그먼트를 사용할 수 있게 되 면 클라이언트 또는 버퍼에 바이트를 보내고 원하는 모든 방법을 통해 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="f0596-138">내보내기가 완료 되 면 데이터를 전송 하 고 serialization에 실패 한 경우 데이터를 삭제 하도록 클라이언트에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="f0596-139">Serialization에 성공 하면 모든 데이터가 전송 되었고 가져오기를 시작할 수 있음을 클라이언트에 게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

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

### <a name="importing"></a><span data-ttu-id="f0596-140">내보내고</span><span class="sxs-lookup"><span data-stu-id="f0596-140">Importing</span></span>

<span data-ttu-id="f0596-141">보낸 사람 으로부터 모든 바이트를 받은 후에는 데이터를 다시 *WorldAnchorTransferBatch* 가져와서 루트 게임 개체를 동일한 물리적 위치에 잠글 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="f0596-142">참고: 가져오기가 transiently 실패 하 고 다시 시도해 야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

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

<span data-ttu-id="f0596-143">*Lockobject* 호출을 통해 *GameObject* 잠긴 후에는 전 세계의 동일한 물리적 위치에 유지 되는 *WorldAnchor* 를 갖게 되지만 다른 사용자와 동일한 Unity 좌표 공간의 다른 위치에 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0596-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>

