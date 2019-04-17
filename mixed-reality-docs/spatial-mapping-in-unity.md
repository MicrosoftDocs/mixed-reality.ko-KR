---
title: Unity에서 공간 매핑
description: 렌더링 및 unity에서와 관련해 서 실제 형상와 충돌 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity 공간 매핑, 렌더러, collider, 메시, 검색, 구성 요소
ms.openlocfilehash: f938f5921cb2c06342a9ebcd376d690c10584df9
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605157"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="0373b-104">Unity에서 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="0373b-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="0373b-105">이 항목에서는 사용 하는 방법 설명 [공간 매핑](spatial-mapping.md) Unity 프로젝트에서 HoloLens 장치 배치, 폐색, 공간 분석 등에 대 한 주변에 화면을 나타내는 삼각형 메시를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-105">This topic describes how to use [spatial mapping](spatial-mapping.md) in your Unity project, retrieving triangle meshes that represent the surfaces in the world around a HoloLens device, for placement, occlusion, room analysis and more.</span></span>

<span data-ttu-id="0373b-106">Unity에는 다음과 같은 방법으로 개발자에 게 노출 되는 공간 매핑에 대 한 전체 지원이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-106">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="0373b-107">공간을 MixedRealityToolkit에서 사용할 수 있는 구성 요소를 매핑, 제공 하는 편리 하 고 빠른 경로 공간 매핑을 사용 하 여 시작</span><span class="sxs-lookup"><span data-stu-id="0373b-107">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="0373b-108">하위 공간 매핑 전체를 제공 하는 Api 제어 하 고 더 복잡 한 응용 프로그램 특정 사용자 지정을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="0373b-108">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application specific customization</span></span>

<span data-ttu-id="0373b-109">앱에서 공간 매핑을 사용 하려면 spatialPerception 기능에 AppxManifest에서 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-109">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="0373b-110">SpatialPerception 기능 설정</span><span class="sxs-lookup"><span data-stu-id="0373b-110">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="0373b-111">공간 매핑 데이터를 사용 하는 앱에 대 한 순서로 SpatialPerception 기능 활성화 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-111">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="0373b-112">SpatialPerception 기능을 사용 하도록 설정 하는 방법:</span><span class="sxs-lookup"><span data-stu-id="0373b-112">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="0373b-113">Unity 편집기에서 엽니다는 **"플레이어 설정"** 창 (편집 > 프로젝트 설정 > Player)</span><span class="sxs-lookup"><span data-stu-id="0373b-113">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="0373b-114">클릭 합니다 **"Windows Store"** 탭</span><span class="sxs-lookup"><span data-stu-id="0373b-114">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="0373b-115">확장 **"게시 설정"** 확인 합니다 **"SpatialPerception"** 의 기능을 **"기능"** 목록</span><span class="sxs-lookup"><span data-stu-id="0373b-115">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

<span data-ttu-id="0373b-116">Visual Studio 솔루션에 이미 Unity 프로젝트를 내보낸 경우 해야 하거나 내보낼 새 폴더 또는 수동으로 [이 기능은 Visual Studio에서 AppxManifest 설정](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-116">Note that if you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="0373b-117">공간 매핑에는 적어도 10.0.10586.0의 MaxVersionTested도를 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-117">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="0373b-118">Visual Studio에서 마우스 오른쪽 단추로 클릭 **Package.appxmanifest** 솔루션 탐색기에서 선택 **코드 보기**</span><span class="sxs-lookup"><span data-stu-id="0373b-118">In Visual Studio, right click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="0373b-119">지정 하는 줄을 찾습니다 **TargetDeviceFamily** 변경할 **MaxVersionTested "10.0.10240.0" =** 에 **MaxVersionTested "10.0.10586.0" =**</span><span class="sxs-lookup"><span data-stu-id="0373b-119">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="0373b-120">**저장** Package.appxmanifest 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-120">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="0373b-121">Unity의 기본 제공 공간 매핑 구성 요소를 사용 하 여 시작</span><span class="sxs-lookup"><span data-stu-id="0373b-121">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="0373b-122">Unity는 쉽게 공간 매핑에 앱을 추가 하는 것에 대 한 2 개 구성 요소가 **공간 매핑 렌더러** 하 고 **공간 매핑 Collider**합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-122">Unity offers 2 components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="0373b-123">공간 매핑 렌더러</span><span class="sxs-lookup"><span data-stu-id="0373b-123">Spatial Mapping Renderer</span></span>

<span data-ttu-id="0373b-124">공간 매핑 메시의 시각화에 대 한 공간 매핑 렌더러를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-124">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Unity에서 공간 매핑 렌더러](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="0373b-126">공간 매핑 Collider</span><span class="sxs-lookup"><span data-stu-id="0373b-126">Spatial Mapping Collider</span></span>

<span data-ttu-id="0373b-127">공간 매핑 Collider holographic 콘텐츠 (또는 문자)에 대 한 허용과 같은 상호 작용 물리학 공간 매핑 메시를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-127">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Unity에서 Collider 공간 매핑](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="0373b-129">기본 제공 공간 매핑 구성 요소를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="0373b-129">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="0373b-130">시각화와 물리적 표면은 상호 작용 하려는 경우 앱에 두 구성 요소를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-130">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="0373b-131">Unity 앱에서 이러한 두 구성 요소를 사용:</span><span class="sxs-lookup"><span data-stu-id="0373b-131">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="0373b-132">공간 표면 메시를 검색 하려는 영역의 가운데에 GameObject를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-132">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="0373b-133">검사기 창에서 **Add Component** > **XR** > **공간 매핑 Collider** 또는 **공간 매핑 렌더러**합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-133">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="0373b-134">이러한 구성 요소를 사용 하는 방법에 자세한 세부 정보를 찾을 수 있습니다 합니다 <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 설명서 사이트</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-134">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="0373b-135">기본 제공 공간 매핑 구성 요소를 넘어</span><span class="sxs-lookup"><span data-stu-id="0373b-135">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="0373b-136">이러한 구성 요소 확인이 끌어서 놓기 쉽게 시작 하기 위한 공간 매핑.</span><span class="sxs-lookup"><span data-stu-id="0373b-136">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span> <span data-ttu-id="0373b-137"> 진행 하려는 경우 두 가지 주요 경로가 있습니다 탐색:</span><span class="sxs-lookup"><span data-stu-id="0373b-137"> When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="0373b-138">고유한 하위 메시에 처리를 위해 하위 수준 공간 매핑 스크립트 API에 대 한 아래 섹션을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-138">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="0373b-139">더 높은 수준의 메시 분석을 수행 하기에 SpatialUnderstanding 라이브러리에 대 한 아래 섹션을 참조 하세요 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-139">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="0373b-140">API를 사용 하는 하위 수준 Unity 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="0373b-140">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="0373b-141">공간 매핑 렌더러 및 공간 매핑 Collider 구성 요소에서 것 보다 더 많은 제어가 필요한 경우에 하위 수준 공간 매핑 스크립트 Api를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-141">If you need more control than you get from the Spatial Mapping Renderer and Spatial Mapping Collider components, you can use the low-level Spatial Mapping script APIs.</span></span>

<span data-ttu-id="0373b-142">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="0373b-142">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="0373b-143">**형식**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="0373b-143">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="0373b-144">다음은 공간 매핑 Api를 사용 하는 응용 프로그램에 대 한 제안 된 흐름에 대 한 개요입니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-144">The following is an outline of the suggested flow for an application that uses the spatial mapping APIs.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="0373b-145">SurfaceObserver(s) 설정</span><span class="sxs-lookup"><span data-stu-id="0373b-145">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="0373b-146">에 대 한 공간 매핑 데이터를 해야 하는 공간의 각 응용 프로그램에서 정의한 영역에 대 한 하나의 SurfaceObserver 개체를 인스턴스화하십시오.</span><span class="sxs-lookup"><span data-stu-id="0373b-146">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="0373b-147">SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, 또는 SetVolumeAsFrustum를 호출 하 여 각 SurfaceObserver 개체에 대 한 데이터를 제공 하는 공간의 지역을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-147">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="0373b-148">단순히 이러한 방법 중 하나를 다시 호출 하 여 영역을 나중에 공간을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-148">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="0373b-149">SurfaceObserver.Update()를 호출 하면 각 공간 화면 공간 매핑 시스템에 대 한 새 정보가 있는 공간의 SurfaceObserver의 지역에 대 한 처리기를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-149">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="0373b-150">하나의 공간 표면에 대 한 처리기를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-150">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="0373b-151">화면 변경 내용 처리</span><span class="sxs-lookup"><span data-stu-id="0373b-151">Handling Surface Changes</span></span>

<span data-ttu-id="0373b-152">처리에 몇 가지 주요 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-152">There are several main cases to handle.</span></span> <span data-ttu-id="0373b-153">추가 및 동일 하 게 사용할 수 있는 업데이트 된 코드 경로 및 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-153">Added & Updated which can use the same code path and Removed.</span></span>
* <span data-ttu-id="0373b-154">예제에서 추가 및 업데이트 된 경우에서에서는 더하거나이 사전에서 메시, SurfaceData 구조체 필요한 구성 요소를 사용 하 여 만든 메시 데이터로 GameObject를 채우는 데 RequestMeshDataAsync 호출 GameObject 나타내는 가져오기 및 장면에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-154">In the Added & Updated cases in the example, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="0373b-155">제거의 경우 사전에서이 메시를 나타내는 GameObject를 제거 하 고 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-155">In the Removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a><span data-ttu-id="0373b-156">데이터 준비를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-156">Handling Data Ready</span></span>

<span data-ttu-id="0373b-157">OnDataReady 처리기 SurfaceData 개체를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-157">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="0373b-158">WorldAnchor, MeshFilter 고 (선택 사항) MeshCollider 개체에 연결 된 공간 화면의 최신 상태를 반영 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-158">The WorldAnchor, MeshFilter and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="0373b-159">필요에 따라 분석을 수행 하거나 [처리](spatial-mapping.md#mesh-processing) MeshFilter 개체의 메시 멤버에 액세스 하 여 메시 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-159">Optionally perform analysis and/or [processing](spatial-mapping.md#mesh-processing) of the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="0373b-160">최신 메시를 사용 하 여 공간 화면을 렌더링 하 고 (선택 사항) 사용 raycasts 및 물리학 충돌 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-160">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="0373b-161">SurfaceData 내용의 null 인지 확인 하는 것이 반드시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-161">It's important to confirm that the contents of the SurfaceData are not null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="0373b-162">업데이트에 대 한 처리를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-162">Start processing on updates</span></span>

<span data-ttu-id="0373b-163">SurfaceObserver.Update() 지연 모든 프레임에서 호출 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-163">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="0373b-164">더 높은 수준의 메시 분석: SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="0373b-164">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="0373b-165">합니다 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> holographic Unity Api를 기반으로 구축 holographic 개발에 대 한 유용한 유틸리티 코드의 컬렉션인 경우.</span><span class="sxs-lookup"><span data-stu-id="0373b-165">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of helpful utility code for holographic development built upon the holographic Unity APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="0373b-166">공간 이해</span><span class="sxs-lookup"><span data-stu-id="0373b-166">Spatial Understanding</span></span>

<span data-ttu-id="0373b-167">실제에서 홀로그램을 배치 하는 경우 공간 매핑 외 메시 및 평면 표면 이동할는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-167">When placing holograms in the physical world it is often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="0373b-168">배치는 절차적 완료 되 면 더 높은 수준의 환경 이해 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-168">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="0373b-169">이 일반적으로 floor, ceiling, 및 벽에 대 한 결정을 내리는 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-169">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="0373b-170">또한 holographic 개체에 대 한 가장 좋은 물리적 위치를 확인 하기 위해 배치 제약 조건 집합에 대해 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-170">In addition, the ability to optimize against a set of placement constraints to determining the most desirable physical locations for holographic objects.</span></span>

<span data-ttu-id="0373b-171">Asobo Studios Young Conker 조각을을 개발 하는 동안이 목적을 위해 공간 solver 개발에이 문제가 머리에 직면 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-171">During the development of Young Conker and Fragments, Asobo Studios faced this problem head on, developing a room solver for this purpose.</span></span> <span data-ttu-id="0373b-172">이러한 각 게임 게임 특정 요구 사항 있었지만 이러한 핵심 기술 공간 이해를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-172">Each of these games had game specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="0373b-173">식별 벽, 개체 한계를 배치할 위치에 빈 공간 찾기 신속 하 게 할 수 있도록 하는 라이브러리에는이 기술은 캡슐화 HoloToolkit.SpatialUnderstanding 보관, 문자 및 다른 공간 이해 쿼리 수많은에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-173">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="0373b-174">소스 코드의 모든 요구 사항에 맞게 사용자 지정 하 고 커뮤니티에 향상 된 기능을 공유할 수 있도록 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-174">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="0373b-175">에 대 한 코드는 C++ solver UWP dll로 래핑 되었으며 prefab은 MixedRealityToolkit 내에 포함 된에서 drop을 사용 하 여 Unity에 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-175">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="0373b-176">이해 모듈</span><span class="sxs-lookup"><span data-stu-id="0373b-176">Understanding Modules</span></span>

<span data-ttu-id="0373b-177">모듈에 의해 노출 되는 세 가지 기본 인터페이스가: 간단한 화면 및 공간 쿼리, 개체 감지에 대 한 셰이프 및 개체 집합의 제약 조건 기반 배치에 대 한 개체 배치 해 찾기에 대 한 토폴로지입니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-177">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint based placement of object sets.</span></span> <span data-ttu-id="0373b-178">이러한 각 옵션은 아래 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-178">Each of these is described below.</span></span> <span data-ttu-id="0373b-179">세 개의 주 모듈 인터페이스를 외에도 태그가 지정 된 화면 형식을 검색할 ray 캐스팅 인터페이스를 사용할 수 및 사용자 지정 watertight playspace 메시 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-179">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="0373b-180">광선 캐스팅</span><span class="sxs-lookup"><span data-stu-id="0373b-180">Ray Casting</span></span>

<span data-ttu-id="0373b-181">대화방을 검색 하 고 완료 된 후 레이블 floor, ceiling, 및 벽 같은 표면에 내부적으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-181">After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="0373b-182">함수 광선을 그린 받고 광선과 알려진된 화면을 사용 하 여 충돌 하는 경우 그리고 있다면 반환 "PlayspaceRaycast", "RaycastResult"의 형태로 해당 화면에 대 한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-182">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="0373b-183">내부적으로 raycast는 playspace의 3 제곱 계산된 8 cm voxel 표현에 대해 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-183">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="0373b-184">각 voxel 처리 토폴로지 데이터 (즉, surfels)를 사용 하 여 화면 요소의 집합을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-184">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="0373b-185">교차 voxel 셀 내에 포함 된 surfels 비교한 후 가장 일치 하는 토폴로지 정보를 찾는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-185">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="0373b-186">이 토폴로지 데이터 교차 된 노출의 노출 영역 뿐만 아니라 "SurfaceTypes" 열거형 형식의 반환 레이블을 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-186">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="0373b-187">Unity 샘플에서는 커서 각 프레임을 광선을 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-187">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="0373b-188">Unity의 colliders 첫째,에 대 한.</span><span class="sxs-lookup"><span data-stu-id="0373b-188">First, against Unity’s colliders.</span></span> <span data-ttu-id="0373b-189">둘째, 이해 모듈의 세계 표현에 대 한입니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-189">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="0373b-190">와 마지막으로 다시 UI 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-190">And finally, again UI elements.</span></span> <span data-ttu-id="0373b-191">이 응용 프로그램에서 UI 이해 하면 Unity의 colliders 및 마지막으로, 다음 우선 순위를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-191">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="0373b-192">SurfaceType 커서 옆에 있는 텍스트로 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-192">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="0373b-193">![화면 형식 커서 옆에 있는 라고 합니다.](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0373b-193">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="0373b-194">*화면 형식 커서 옆에 있는 라고 합니다.*</span><span class="sxs-lookup"><span data-stu-id="0373b-194">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="0373b-195">쿼리 토폴로지</span><span class="sxs-lookup"><span data-stu-id="0373b-195">Topology Queries</span></span>

<span data-ttu-id="0373b-196">DLL 내에서 토폴로지 manager 환경의 레이블 지정을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-196">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="0373b-197">위에서 설명 했 듯이 surfels, voxel 볼륨 내에 포함 된 내에 저장 된 데이터를 많이 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-197">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="0373b-198">또한 "PlaySpaceInfos" 구조 world 맞춤 (자세한 내용은 아래 참조), floor, ceiling 높이 등을 playspace에 대 한 정보를 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-198">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="0373b-199">추론은 floor, ceiling, 및 벽을 결정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-199">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="0373b-200">예를 들어, 1의 m2 노출 영역 보다 큰를 사용 하 여 가장 크고 가장 낮은 가로 화면 바닥을 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-200">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="0373b-201">검색 프로세스 중 카메라 경로에서이 프로세스는 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-201">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="0373b-202">토폴로지 관리자에 의해 노출 되는 쿼리의 하위 집합만 아웃 dll을 통해 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-202">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="0373b-203">노출 된 토폴로지 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-203">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="0373b-204">각 쿼리 매개 변수, 쿼리 형식에 특정 집합을에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-204">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="0373b-205">다음 예제에서는 사용자의 최소 높이 및 원하는 볼륨, floor, 및 최소한의 여유 공간 볼륨 앞에 위의 최소 배치 높이 너비를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-205">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="0373b-206">모든 측정 미터의 경우</span><span class="sxs-lookup"><span data-stu-id="0373b-206">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="0373b-207">이 쿼리는 각각 "TopologyResult" 구조의 사전 할당 된 배열이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-207">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="0373b-208">"LocationCount" 매개 변수에 전달 된 배열의 길이 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-208">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="0373b-209">반환 값은 반환 된 위치 수를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-209">The return value reports the number of returned locations.</span></span> <span data-ttu-id="0373b-210">이 수는 전달 된 보다 큰 "locationCount" 매개 변수에서입니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-210">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="0373b-211">"TopologyResult" 반환 된 볼륨, 연결 방향 (즉, 표준) 및 검색 공간의 크기의 가운데 위치를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-211">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

<span data-ttu-id="0373b-212">Unity 샘플에서, 가상 UI 패널에서 단추에 이러한 쿼리는 각 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-212">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="0373b-213">하드 샘플의 적절 한 값으로이 쿼리는 각각에 대 한 매개 변수를 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-213">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="0373b-214">예를 보려면 샘플 코드에서 SpaceVisualizer.cs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0373b-214">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="0373b-215">셰이프 쿼리</span><span class="sxs-lookup"><span data-stu-id="0373b-215">Shape Queries</span></span>

<span data-ttu-id="0373b-216">Dll 내에서 셰이프 분석기 ("ShapeAnalyzer_W")는 사용자가 정의한 사용자 지정 셰이프를 대조할 토폴로지 분석기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-216">Inside of the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="0373b-217">Unity 샘플 셰이프 집합을 정의 하 고 셰이프 탭 내의 앱에서 쿼리 메뉴를 통해 결과 출력을 노출 합니다. 목적은 사용자가 자신의 개체 셰이프 쿼리를 정의 하 고 확인 수는 해당 응용 프로그램에서 필요에 따라를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-217">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="0373b-218">셰이프 분석만 가로 화면에서 작동 하는 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-218">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="0373b-219">예를 들어, 소파, 플랫 사용자 화면과 플랫 맨 뒤로 소파에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-219">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="0373b-220">Shape 쿼리의 정렬 및 연결 된 두 개의 화면을 사용 하 여 특정 크기, 높이 및 측면 범위의 두 화면을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-220">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="0373b-221">Api 용어를 사용 하 couch 자리와 백 맨 위에 셰이프 구성 요소 및 맞춤 요구 사항은 셰이프 구성 요소 제약 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-221">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="0373b-222">"Sittable" 개체에 대 한 Unity 샘플 (ShapeDefinition.cs)에 정의 된 쿼리의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-222">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="0373b-223">Shape 쿼리의 각 구성 요소 제약 조건 집합 및 셰이프 제약 조건의 집합을 사용 하 여 각 셰이프 구성 요소 집합을 정의한는 구성 요소 간의 종속성을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-223">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="0373b-224">이 예제 (구성 요소가 하나만 하므로)는 단일 구성 요소 정의 및 구성 요소 간에 모양 제약 없이 세 가지 제약 조건을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-224">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="0373b-225">반면, 소파 모양을 두 셰이프 구성 요소와 네 개의 셰이프 제약 조건에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-225">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="0373b-226">구성 요소는 (0과 1이 예제의) 사용자의 구성 요소 목록에서 해당 인덱스로 식별 되는 참고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-226">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="0373b-227">래퍼 함수는 사용자 지정 셰이프 정의 쉽게 만들기 위한 Unity 모듈에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-227">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="0373b-228">구성 요소 및 셰이프 제약 조건의 전체 목록은 "SpatialUnderstandingDll.cs" "ShapeComponentConstraint" 및 "ShapeConstraint" 구조 내에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-228">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="0373b-229">![이 화면에서 사각형 셰이프를 찾을 수합니다](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0373b-229">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="0373b-230">*이 화면에서 사각형 셰이프를 찾을 수합니다*</span><span class="sxs-lookup"><span data-stu-id="0373b-230">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="0373b-231">개체 배치 해 찾기</span><span class="sxs-lookup"><span data-stu-id="0373b-231">Object Placement Solver</span></span>

<span data-ttu-id="0373b-232">개체를 배치 하는 물리적 공간에 이상적인 위치를 식별할 수 개체 배치 해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-232">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="0373b-233">개체 규칙 및 제약 조건이 지정 된 위치를 적합 해를 찾기가 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-233">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="0373b-234">또한 개체 쿼리는 "Solver_RemoveObject"를 사용 하 여 개체가 제거 되거나 "Solver_RemoveAllObjects" 호출을 허용 제한 다중 개체 배치 될 때까지 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-234">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="0373b-235">개체 배치 쿼리 세 부분으로 구성 됩니다: 매개 변수, 규칙의 목록 및 제약 조건 목록을 사용 하 여 배치 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-235">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="0373b-236">쿼리를 실행 하려면 다음 API를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-236">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="0373b-237">이 함수는 개체 이름, 배치 정 및 규칙 및 제약 조건 목록을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-237">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="0373b-238">C# 래퍼 생성 규칙 및 제약 조건 생성을 간편 하 게 도우미 함수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-238">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="0373b-239">배치 정의는 다음 중 하나 이므로 쿼리 형식을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-239">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

<span data-ttu-id="0373b-240">매개 변수 형식에 고유 집합에 각 배치 형식</span><span class="sxs-lookup"><span data-stu-id="0373b-240">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="0373b-241">"ObjectPlacementDefinition" 구조에는 이러한 정의 만들기 위한 정적 도우미 함수 집합을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-241">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="0373b-242">예를 들어, 현장에서 개체를 삽입할 수 있는 위치를 찾으려면 다음 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-242">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="0373b-243">공용 정적 ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) 외에 배치 형식, 규칙 및 제약 조건 집합을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-243">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="0373b-244">규칙을 위반할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-244">Rules cannot be violated.</span></span> <span data-ttu-id="0373b-245">형식 및 규칙을 충족 하는 위치를 배치 하는 다음 제약 조건 집합에 대 한 최적의 배치 위치를 선택 하기 위해 최적화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-245">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="0373b-246">제공 된 정적 생성 함수에 의해 각 제약 조건 및 규칙을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-246">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="0373b-247">규칙 및 제약 조건 생성 함수 예제는 아래 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-247">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="0373b-248">개체 아래의 배치 쿼리를 찾고 절반 미터 큐브는 화면의 가장자리에 배치 하는, 다른에서 이전에 개체 배치 대화방의 가운데 근처 위치 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-248">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="0373b-249">성공 하면 배치 위치를 포함 하는 "ObjectPlacementResult" 구조체 차원과 방향을 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-249">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="0373b-250">또한 배치는 dll의 내부 목록을 배치 하는 개체에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-250">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="0373b-251">후속 배치 쿼리를이 개체를 고려 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-251">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="0373b-252">Unity 예제의 "LevelSolver.cs" 파일을 더 많은 예제 쿼리를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-252">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="0373b-253">![개체 배치의 결과](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="0373b-253">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="0373b-254">*그림 3: 파란색 상자 floor 세 위치에서 결과 사용 하 여 카메라 위치 규칙에서 쿼리 하는 방법*</span><span class="sxs-lookup"><span data-stu-id="0373b-254">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="0373b-255">수준 또는 응용 프로그램 시나리오에 필요한 여러 개체의 배치 위치에 대 한 해결 하는 경우 먼저 공간을 찾을 수 있는 확률을 최대화 하려면에서 필수적인 및 큰 개체를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-255">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="0373b-256">배치 순서가 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-256">Placement order is important.</span></span> <span data-ttu-id="0373b-257">개체 배치를 찾을 수 없는 경우에 덜 제한적된 구성 해 보십시오.</span><span class="sxs-lookup"><span data-stu-id="0373b-257">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="0373b-258">대체 (fallback) 구성 집합을는 것이 많은 공간 구성에서 기능을 지 원하는 데 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-258">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="0373b-259">대화방 검색 프로세스</span><span class="sxs-lookup"><span data-stu-id="0373b-259">Room Scanning Process</span></span>

<span data-ttu-id="0373b-260">HoloLens를 제공한 공간 매핑 솔루션은 문제 공간 전체의 요구에 맞게 충분히 제네릭으로 되도록 설계 되었지만, 공간 이해 모듈을 두 특정 게임의 요구를 지원 하도록 빌드 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-260">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="0373b-261">해당 솔루션은 특정 프로세스 및 아래에 요약 가정 집합이 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-261">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="0373b-262">사용자 구동 playspace "그리기" – 검색 단계에서는 사용자 이동 하 고 효과적으로 포함 해야 하는 영역을 그리기 속도 수행 하는 관련 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-262">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="0373b-263">생성 된 메시 반드시이 단계에서 사용자에 게 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-263">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="0373b-264">실내 홈 또는 office 설치 – 쿼리 함수 평면 표면 및 직각으로 벽 바탕으로 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-264">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="0373b-265">소프트 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-265">This is a soft limitation.</span></span> <span data-ttu-id="0373b-266">그러나 검색 단계에서는 기본 축 분석을 주 및 부 축 따라 메시 공간 분할을 최적화 하기 위해 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-266">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="0373b-267">포함된 된 SpatialUnderstanding.cs 파일 검색 단계 프로세스를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-267">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="0373b-268">다음 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-268">It calls the following functions.</span></span>

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

<span data-ttu-id="0373b-269">"SpatialUnderstanding" 동작을 통해 제어 스캐닝 흐름을 각 프레임 InitScan, 다음 UpdateScan 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-269">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="0373b-270">통계 쿼리는 적절 한 검사를 보고, 사용자 RequestFinish 검사 단계의 끝을 나타내기 위해 호출 airtap에 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-270">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="0373b-271">반환 될 때까지 호출할 UpdateScan 계속 값 dll 처리 완료 되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-271">UpdateScan continues to be called until it’s return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="0373b-272">이해 메시</span><span class="sxs-lookup"><span data-stu-id="0373b-272">Understanding Mesh</span></span>

<span data-ttu-id="0373b-273">이해 dll을 playspace 크기가 8 cm voxel 큐브에 포함 된 표를 내부적으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-273">The understanding dll internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="0373b-274">검색의 시작 부분에서 하는 동안 대화방의 축을 확인 하려면 기본 구성 요소 분석을 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-274">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="0373b-275">내부적으로 이러한 축 정렬 해당 voxel 공간을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-275">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="0373b-276">메시를 isosurface voxel 볼륨에서 추출 하 여 약 1 초 마다 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-276">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="0373b-277">![생성 된 메시 voxel 볼륨에서 생성](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="0373b-277">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="0373b-278">*생성 된 메시 voxel 볼륨에서 생성*</span><span class="sxs-lookup"><span data-stu-id="0373b-278">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="0373b-279">문제 해결</span><span class="sxs-lookup"><span data-stu-id="0373b-279">Troubleshooting</span></span>
* <span data-ttu-id="0373b-280">설정 했는지 확인 합니다 [SpatialPerception](#setting-the-spatialperception-capability) 기능</span><span class="sxs-lookup"><span data-stu-id="0373b-280">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="0373b-281">추적 손실 되 면 다음 OnSurfaceChanged 이벤트는 모든 메시를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="0373b-281">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="0373b-282">혼합된 현실 도구 키트의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="0373b-282">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="0373b-283">혼합 현실 Toolkit v2를 사용 하 여 공간 매핑 사용에 대 한 자세한 내용은 참조는 <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">공간 인식 섹션</a> MRTK 문서.</span><span class="sxs-lookup"><span data-stu-id="0373b-283">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="see-also"></a><span data-ttu-id="0373b-284">참조</span><span class="sxs-lookup"><span data-stu-id="0373b-284">See also</span></span>
* [<span data-ttu-id="0373b-285">MR 공간 230: 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="0373b-285">MR Spatial 230: Spatial mapping</span></span>](holograms-230.md)
* [<span data-ttu-id="0373b-286">좌표계</span><span class="sxs-lookup"><span data-stu-id="0373b-286">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="0373b-287">Unity의 좌표계</span><span class="sxs-lookup"><span data-stu-id="0373b-287">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="0373b-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="0373b-288"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="0373b-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="0373b-289"><a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="0373b-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="0373b-290"><a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="0373b-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="0373b-291"><a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
