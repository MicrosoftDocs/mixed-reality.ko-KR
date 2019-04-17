---
title: Unity의 지 속성
description: 지 속성을 사용 하면 개별 홀로그램 또는 작업 영역을 찾고 다음 나중에 앱의 사용 대부분을 통해 기대 원하는 위치에 고정 사용자가 있습니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistence, Unity
ms.openlocfilehash: b6a67e52b3a5ce724a90eb1a479c5eda74b0c4cb
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605077"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="0003e-104">Unity의 지 속성</span><span class="sxs-lookup"><span data-stu-id="0003e-104">Persistence in Unity</span></span>

<span data-ttu-id="0003e-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="0003e-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="0003e-106">**클래스:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="0003e-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="0003e-107">WorldAnchorStore 홀로그램 특정 실제 위치에 응용 프로그램의 인스턴스에서 유지 하는 위치를 holographic 환경을 만드는 키입니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="0003e-108">원하는 찾을 나중에 앱의 여러 기능을 통해 필요한 경우 사용자가 개별 홀로그램 또는 작업 영역을 고정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="0003e-109">홀로그램 세션 간에 유지 하는 방법</span><span class="sxs-lookup"><span data-stu-id="0003e-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="0003e-110">WorldAnchorStore를 사용 하면 세션 전반에 걸쳐 WorldAnchor의 위치를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="0003e-111">홀로그램 세션 전반에 걸쳐를 실제로 유지 하려면 개별적으로 추적 하기 위해 특정 world 앵커를 사용 하는 프로그램 Gameobject 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="0003e-112">GameObject 루트 world 앵커를 사용 하 여 만들고 자식이 하는 것이 효율적 로컬 위치 오프셋 값을 사용 하 여 홀로그램 고정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="0003e-113">이전 세션에서 홀로그램을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="0003e-114">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="0003e-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="0003e-115">전 세계 앵커의 id를 제공 하는 전 세계 앵커와 관련 된 앱 데이터를 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="0003e-116">전 세계 앵커를 해당 id에서 로드</span><span class="sxs-lookup"><span data-stu-id="0003e-116">Load a world anchor from its id</span></span>

<span data-ttu-id="0003e-117">이후 세션에 대 한 홀로그램을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="0003e-118">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="0003e-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="0003e-119">Id를 지정 하는 전 세계 앵커를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="0003e-120">Id와 함께 전 세계 앵커와 관련 된 앱 데이터를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="0003e-121">WorldAnchorStore 가져오기</span><span class="sxs-lookup"><span data-stu-id="0003e-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="0003e-122">작업을 수행 하려는 경우 이동할 준비가 알 수 있도록 관련 WorldAnchorStore에 대 한 참조를 유지 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="0003e-123">호출 하려는 이므로 비동기 호출을 잠재적으로 시작 되 자 마자</span><span class="sxs-lookup"><span data-stu-id="0003e-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="0003e-124">StoreLoaded는 WorldAnchorStore 로드가 완료 된 경우에 대 한 처리기를이 예제의 경우:</span><span class="sxs-lookup"><span data-stu-id="0003e-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="0003e-125">이제 저장 하 고 특정 World 앵커를 로드 하는 데 사용 됩니다 WorldAnchorStore에 대 한 참조가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="0003e-126">WorldAnchor 저장</span><span class="sxs-lookup"><span data-stu-id="0003e-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="0003e-127">에 저장 하려면 단순히 이름을 새로운 저장 하 고 저장 하려는 경우 이전에 얻은 것 WorldAnchor 전달 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="0003e-128">(저장소 참고: 동일한 문자열에 두 개의 앵커를 저장 하는 동안 실패입니다. 저장 false를 반환 합니다).</span><span class="sxs-lookup"><span data-stu-id="0003e-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="0003e-129">새 저장 하기 전에 이전 저장을 삭제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-129">You need to Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="0003e-130">WorldAnchor 로드</span><span class="sxs-lookup"><span data-stu-id="0003e-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="0003e-131">하 고 로드 하려면:</span><span class="sxs-lookup"><span data-stu-id="0003e-131">And to load:</span></span>

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

<span data-ttu-id="0003e-132">또한 저장소를 사용할 수 있습니다. 이전에 저장 하는 앵커를 제거 하려면 delete () 및 저장소를 제공 합니다. Clear ()-모든 이전에 저장 된 데이터를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="0003e-133">기존 앵커를 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="0003e-134">이전에 저장 된 앵커를 검색할 GetAllIds를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="0003e-135">여러 장치에 대 한 유지 홀로그램</span><span class="sxs-lookup"><span data-stu-id="0003e-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="0003e-136">사용할 수 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> 에서 해당 장치에서 동일한 변수가 없는 경우에 여러 HoloLens, iOS 및 Android 장치에서 앱 다음 찾을 수 있는 로컬 WorldAnchor, 견고한 클라우드 앵커를 만들려면 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="0003e-137">클라우드 앵커 영구 이기 때문에 시간이 지남에 따라 여러 장치 각 볼 수 콘텐츠 동일한 실제 위치에 해당 앵커에 상대적인 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="0003e-138">5 분을 사용해으로 시작 하려면 Unity에서 공유 환경을 구축 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">빠른 시작 Azure 공간 앵커 Unity</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="0003e-139">Azure 공간 앵커를 사용 하 여 실행을 했으면 할 수 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity에서 앵커를 찾아서 만들</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="0003e-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="see-also"></a><span data-ttu-id="0003e-140">관련 항목</span><span class="sxs-lookup"><span data-stu-id="0003e-140">See Also</span></span>
* [<span data-ttu-id="0003e-141">공간 앵커 지 속성</span><span class="sxs-lookup"><span data-stu-id="0003e-141">Spatial anchor persistence</span></span>](coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="0003e-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 공간 앵커</a></span><span class="sxs-lookup"><span data-stu-id="0003e-142"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="0003e-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 공간 앵커 Unity 용 SDK</a></span><span class="sxs-lookup"><span data-stu-id="0003e-143"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
