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
# <a name="local-anchor-transfers-in-unity"></a>Unity에서 로컬 앵커 전송

수 없는 상황 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>, 로컬 앵커 전송 두 번째 HoloLens 장치에서 가져올 앵커를 내보내려면 하나 HoloLens 장치를 사용 합니다.

>[!NOTE]
>로컬 앵커 전송을 제공 보다 덜 강력 앵커 회수 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a>, iOS 및 Android 장치의이 방식으로 지원 되지 않습니다.

### <a name="setting-the-spatialperception-capability"></a>SpatialPerception 기능 설정

공간 앵커를 전송 하는 앱에 대 한 순서로 합니다 *SpatialPerception* 기능을 사용할 수 있어야 합니다.

사용 하도록 설정 하는 방법을 합니다 *SpatialPerception* 기능:
1. Unity 편집기에서 엽니다는 **"플레이어 설정"** 창 (편집 > 프로젝트 설정 > Player)
2. 클릭 합니다 **"Windows Store"** 탭
3. 확장 **"게시 설정"** 확인 합니다 **"SpatialPerception"** 의 기능을 **"기능"** 목록

>[!NOTE]
>이미 Unity 프로젝트를 Visual Studio 솔루션을 내보낸 경우 해야 새 폴더 또는 수동으로 내보낼 [이 기능은 Visual Studio에서 AppxManifest 설정](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)합니다.

### <a name="anchor-transfer"></a>앵커 전송

**Namespace:** *UnityEngine.XR.WSA.Sharing*<br>
**형식**: *WorldAnchorTransferBatch*

전송 하는 [WorldAnchor](coordinate-systems-in-unity.md), 하나 전송할 앵커를 설정 해야 합니다. 하나의 HoloLens의 사용자는 자신의 환경을 검색 하 고 수동으로 또는 프로그래밍 방식으로 공간을 공유 환경에 대 한 앵커의 시점을 선택 합니다. 이 점을 나타내는 데이터 직렬화 및 환경에서 공유 하는 다른 장치에 전송 될 수입니다. 그런 다음 각 장치는 앵커 데이터를 역직렬화 하 고 공간에서 해당 지점을 찾으려고 시도. 앵커 전송 작업에 대 한 순서를 나타내는 앵커 지점을 식별할 수 있도록 각 장치를 충분히 환경에서 검색 한 해야 합니다.

### <a name="setup"></a>설치 프로그램

이 페이지의 샘플 코드에 초기화 해야 하는 몇 가지 필드가 있습니다.
1. *GameObject rootGameObject* 은 *GameObject* 에 Unity의를 *WorldAnchor* 에 구성 요소입니다. 이 공유 환경에서 한 명의 사용자 배치할 *GameObject* 및 다른 사용자에 게 데이터 내보내기.
2. *WorldAnchor gameRootAnchor* 되는 *UnityEngine.XR.WSA.WorldAnchor* 켜져 있는 *rootGameObject*합니다.
3. *바이트 importedData* 각 클라이언트가 네트워크를 통해 받고 serialize 된 앵커에 대 한 바이트 배열입니다.

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

### <a name="exporting"></a>내보내기

내보내려면 하기만 *WorldAnchor* 및 새로운이 라는 수신 응용 프로그램에 적합 한 알아야 합니다. 공유 환경에서 하나의 클라이언트 공유 앵커를 내보내려면 다음이 단계를 수행 합니다.
1. 만들기는 *WorldAnchorTransferBatch*
2. 추가 된 *WorldAnchors* 전송할
3. 내보내기 시작
4. 처리를 *OnExportDataAvailable* 데이터로 이벤트에는 사용할 수 있게 됩니다.
5. 처리를 *OnExportComplete* 이벤트

만듭니다는 *WorldAnchorTransferBatch* 무엇을 캡슐화 하에서는 전송 되며 다음 바이트에 내보낼:

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

데이터를 사용할 수 있게 되 면 바이트 클라이언트 또는 버퍼에 데이터의 세그먼트를 사용할 수 있으므로 보내고 원하는 모든 수단을 통해:

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

내보내기에서는 데이터 및 실패 한 serialization 전송 된 있을 경우 완료 되 면 데이터를 삭제 하도록 클라이언트를 알려 줍니다. Serialization에 성공한 경우 모든 데이터가 전송 되었는지을 시작할 수를 가져오는 클라이언트에 게 알리는:

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

### <a name="importing"></a>가져오기

모든 바이트를 보낸 사람 으로부터 받은 후에 다시 데이터를 가져올 수 있습니다는 *WorldAnchorTransferBatch* 동일한 물리적 위치로 루트 게임 개체를 잠급니다. 참고 가져오기 때로는 일시적으로 실패 하 고 다시 시도해 야 합니다.:

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

후를 *GameObject* 통해 잠겨 합니다 *LockObject* 갖습니다 하 호출을 *WorldAnchor* 환경에서는 동일한 실제 위치에 유지 됩니다는 하지만에 있을 수는 Unity에서 다른 위치로 다른 사용자 보다는 공간을 조정 합니다.

