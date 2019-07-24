---
title: Unity의 지 속성
description: 지 속성을 사용 하면 사용자가 원하는 위치에 개별 holograms 또는 작업 영역을 고정 한 다음, 앱의 많은 사용을 원하는 경우 나중에 찾을 수 있습니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, 지 속성, Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524781"
---
# <a name="persistence-in-unity"></a>Unity의 지 속성

**공간** *UnityEngine. XR*<br>
**클래스** *WorldAnchorStore*

WorldAnchorStore는 응용 프로그램의 여러 인스턴스에서 holograms 특정 실제 위치에 유지 되는 holographic 환경을 만드는 핵심입니다. 이렇게 하면 사용자가 원하는 위치에 개별 holograms 또는 작업 영역을 고정 한 다음, 앱의 여러 사용을 원하는 위치에서 나중에 찾을 수 있습니다.

## <a name="how-to-persist-holograms-across-sessions"></a>세션 간에 holograms를 유지 하는 방법

WorldAnchorStore를 사용 하면 세션 간에 WorldAnchor의 위치를 유지할 수 있습니다. 실제로 세션 간에 holograms을 유지 하려면 특정 세계 앵커를 사용 하는 Gameobject를 별도로 추적 해야 합니다. 일반적으로 세계 앵커를 사용 하 여 GameObject 루트를 만들고 로컬 위치 오프셋을 사용 하 여 자식을 holograms 고정 하는 것이 좋습니다.

이전 세션에서 holograms를 로드 하려면 다음을 수행 합니다.
1. WorldAnchorStore 가져오기
2. 세계 앵커와 관련 된 앱 데이터를 로드 하 여 세계 앵커의 id를 제공 합니다.
3. 해당 id에서 전 세계 앵커 로드

이후 세션에 대해 holograms를 저장 하려면:
1. WorldAnchorStore 가져오기
2. Id를 지정 하 여 전 세계 앵커 저장
3. Id와 함께 세계 앵커와 관련 된 앱 데이터 저장

### <a name="getting-the-worldanchorstore"></a>WorldAnchorStore 가져오기

WorldAnchorStore에 대 한 참조를 유지 하 여 작업을 수행 하려는 경우 준비가 되었다는 것을 알 수 있습니다. 비동기 호출 이므로 시작 하는 즉시,를 호출 하려고 합니다.

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

이 경우 WorldAnchorStore가 로드를 완료 한 경우에 대 한 처리기입니다.

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

이제 특정 세계 앵커를 저장 하 고 로드 하는 데 사용할 WorldAnchorStore에 대 한 참조가 있습니다.

### <a name="saving-a-worldanchor"></a>WorldAnchor 저장

저장 하기 위해 저장 하는 항목의 이름을로 하 고 저장 하려는 경우 앞에서 받은 WorldAnchor에 전달 하기만 하면 됩니다. 참고: 두 앵커를 같은 문자열에 저장 하려고 하면 실패 합니다 (store. Save는 false를 반환 합니다. 이전 저장을 삭제 한 후 새 저장을 저장 해야 합니다.

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>WorldAnchor 로드

로드 하려면 다음을 수행 합니다.

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

저장소를 추가로 사용할 수도 있습니다. Delete ()-이전에 저장 하 고 저장 한 앵커를 제거 합니다. 이전에 저장 된 모든 데이터를 제거 하려면 ()를 선택 취소 합니다.

### <a name="enumerating-existing-anchors"></a>기존 앵커 열거

이전에 저장 된 앵커를 검색 하려면 GetAllIds를 호출 합니다.

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>여러 장치에 대 한 holograms 유지

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 를 사용 하 여 로컬 WorldAnchor에서 영 속 클라우드 앵커를 만들 수 있습니다. 그러면 앱이 여러 HoloLens, IOS 및 Android 장치에서 해당 장치를 동시에 함께 제공 하지 않는 경우에도 해당 장치를 찾을 수 있습니다.  클라우드 앵커는 지속 되기 때문에 시간에 따른 여러 장치는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.

Unity에서 공유 환경 빌드를 시작 하려면 5 분 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 공간 앵커 Unity 퀵 스타트</a>를 사용해 보세요.

Azure 공간 앵커를 사용 하 여 실행 하면 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 만들고 찾을</a>수 있습니다.

## <a name="see-also"></a>관련 항목
* [공간 앵커 지 속성](coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Unity 용 Azure 공간 앵커 SDK</a>
