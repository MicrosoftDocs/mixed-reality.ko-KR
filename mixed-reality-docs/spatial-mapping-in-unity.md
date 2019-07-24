---
title: Unity의 공간 매핑
description: Unity에서 사용자를 중심으로 실제 형상과의 렌더링 및 충돌
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, 공간 매핑, 렌더러, collider, 메시, 스캔, 구성 요소
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148645"
---
# <a name="spatial-mapping-in-unity"></a>Unity의 공간 매핑

이 항목에서는 Unity 프로젝트에서 [공간 매핑을](spatial-mapping.md) 사용 하는 방법에 대해 설명 합니다. 폐색, 방 분석 등을 위해 HoloLens 장치 주변의 표면을 나타내는 삼각형 메시를 검색 합니다.

Unity에는 다음과 같은 방법으로 개발자에 게 노출 되는 공간 매핑에 대 한 완벽 한 지원이 포함 되어 있습니다.
1. 공간 매핑 구성 요소는 MixedRealityToolkit에서 사용할 수 있으며 공간 매핑을 시작 하기 위한 편리 하 고 빠른 경로를 제공 합니다.
2. 모든 제어 기능을 제공 하 고 보다 정교한 응용 프로그램별 사용자 지정을 가능 하 게 하는 하위 수준 공간 매핑 Api

앱에서 공간 매핑을 사용 하려면 Appxmanifest.xml에 spatialPerception 기능을 설정 해야 합니다.

## <a name="setting-the-spatialperception-capability"></a>SpatialPerception 기능 설정

앱이 공간 매핑 데이터를 사용 하도록 하려면 SpatialPerception 기능을 사용 하도록 설정 해야 합니다.

SpatialPerception 기능을 사용 하도록 설정 하는 방법:
1. Unity 편집기에서 **"플레이어 설정"** 창 (편집 > 프로젝트 설정 > 플레이어)을 엽니다.
2. **"Windows 스토어"** 탭을 클릭 합니다.
3. " **게시 설정"** 을 확장 하 고 " **기능"** 목록에서 **"SpatialPerception"** 기능을 확인 합니다.

Unity 프로젝트를 Visual Studio 솔루션으로 이미 내보낸 경우 새 폴더로 내보내거나 [Visual studio의 appxmanifest.xml에서이 기능](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)을 수동으로 설정 해야 합니다.

공간 매핑에는 10.0.10586.0 이상의 MaxVersionTested 필요 합니다.
1. Visual Studio의 솔루션 탐색기에서 appxmanifest.xml를 마우스 오른쪽 단추로 클릭 하 고 **코드 보기** 를 선택 **합니다.**
2. **Targetdevicefamily** 를 지정 하 고 **MaxVersionTested = "10.0.10240.0"** 를 **MaxVersionTested = "10.0.10586.0"** 로 변경 하는 줄을 찾습니다.
3. Appxmanifest.xml를 **저장** 합니다.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Unity의 기본 제공 공간 매핑 구성 요소 시작

Unity는 앱, **공간 매핑 렌더러** 및 **공간 매핑 Collider**에 공간 매핑을 쉽게 추가 하기 위한 2 개의 구성 요소를 제공 합니다.

### <a name="spatial-mapping-renderer"></a>공간 매핑 렌더러

공간 매핑 렌더러를 사용 하면 공간 매핑 메시를 시각화할 수 있습니다.

![Unity의 공간 매핑 렌더러](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>공간 매핑 Collider

공간 매핑 Collider는 공간 매핑 메시를 사용 하 여 물리학 등의 holographic 콘텐츠 (또는 문자) 조작을 허용 합니다.

![Unity의 공간 매핑 Collider](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>기본 제공 공간 매핑 구성 요소 사용

실제 화면을 시각화 하 고 상호 작용 하려는 경우 두 구성 요소를 모두 앱에 추가할 수 있습니다.

Unity 앱에서 이러한 두 구성 요소를 사용 하려면 다음을 수행 합니다.
1. 공간 표면 메시를 검색할 영역의 가운데에 있는 GameObject를 선택 합니다.
2. 검사기 창에서 **구성 요소** > **XR** > **공간 매핑 Collider** 또는 **공간 매핑 렌더러**를 추가 합니다.

이러한 구성 요소를 사용 하는 방법에 대 한 자세한 내용은 <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 설명서 사이트</a>에서 확인할 수 있습니다.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>기본 제공 공간 매핑 구성 요소 이상

이러한 구성 요소를 사용 하면 쉽게 끌어서 놓기를 통해 공간 매핑을 시작할 수 있습니다.  자세히 알아보려면 다음 두 가지 주요 경로를 살펴볼 수 있습니다.
* 낮은 수준의 메시 처리를 수행 하려면 하위 수준 공간 매핑 스크립트 API에 대 한 아래 섹션을 참조 하세요.
* 높은 수준의 메시 분석을 수행 하려면 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>의 SpatialUnderstanding 라이브러리에 대 한 아래 섹션을 참조 하세요.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>하위 수준 Unity 공간 매핑 API 사용

공간 매핑 렌더러 및 공간 매핑 Collider 구성 요소에서 가져오는 것 보다 더 많은 제어가 필요한 경우 하위 수준 공간 매핑 스크립트 Api를 사용할 수 있습니다.

**공간** *UnityEngine. XR. WSA*<br>
**형식**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

다음은 공간 매핑 Api를 사용 하는 응용 프로그램의 제안 된 흐름에 대 한 개요입니다.

### <a name="set-up-the-surfaceobservers"></a>SurfaceObserver 설정

공간 매핑 데이터가 필요한 각 응용 프로그램 정의 공간 영역에 대해 하나의 SurfaceObserver 개체를 인스턴스화합니다.

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

SetSurfaceObserver 개체가 SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox 또는 Set지 수를 호출 하 여 데이터를 제공할 공간 영역을 지정 합니다. 나중에 이러한 메서드 중 하나를 다시 호출 하 여 공간 영역을 다시 정의할 수 있습니다.

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

SurfaceObserver ()를 호출 하는 경우 공간 매핑 시스템에 새 정보가 있는 SurfaceObserver의 공간 영역에 있는 각 공간 표면의 처리기를 제공 해야 합니다. 이 처리기는 하나의 공간 표면의를 수신 합니다.

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>화면 변경 내용 처리

몇 가지 주요 사례를 처리할 수 있습니다. 동일한 코드 경로를 사용 하 고 제거할 수 있는 & 업데이트를 추가 했습니다.
* 예제에서 추가 된 & 업데이트 된 사례에서이 메시를 나타내는 GameObject를 사전에서 추가 하거나 가져오고, 필요한 구성 요소를 사용 하 여 SurfaceData 구조체를 만든 다음, RequestMeshDataAsync를 호출 하 여 GameObject를 메시 데이터로 채웁니다. 장면에서의 위치입니다.
* 제거 된 경우에는이 메시를 나타내는 GameObject를 사전에서 제거 하 고 삭제 합니다.

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

### <a name="handling-data-ready"></a>데이터 처리 준비 완료

OnDataReady 처리기는 SurfaceData 개체를 수신 합니다. WorldAnchor, MeshFilter 및 (선택 사항) 포함 하는 개체는 연결 된 공간 표면의 최신 상태를 반영 합니다. 필요에 따라 MeshFilter 개체의 메시 구성원에 액세스 하 여 메시 데이터의 분석 및/또는 [처리](spatial-mapping.md#mesh-processing) 를 수행 합니다. 최신 메시를 사용 하 여 공간 표면을 렌더링 하 고 (선택 사항) 물리 충돌과 raycasts에 사용 합니다. SurfaceData의 내용이 null이 아닌지 확인 하는 것이 중요 합니다.

### <a name="start-processing-on-updates"></a>업데이트 처리 시작

SurfaceObserver ()는 모든 프레임이 아니라 지연 시 호출 되어야 합니다.

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>상위 수준 메시 분석: SpatialUnderstanding

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> 는 Holographic Unity api를 기반으로 하는 holographic 개발을 위한 유용한 유틸리티 코드 모음입니다.

### <a name="spatial-understanding"></a>공간 이해

실제 세계에 holograms을 배치할 때 공간 매핑의 메시 및 surface 평면을 초과 하는 것이 좋은 경우가 많습니다. 배치가 procedurally 되 면 더 높은 수준의 환경 이해를 수행 하는 것이 좋습니다. 일반적으로 바닥, 천장 및 벽에 대 한 결정을 내려야 합니다. 또한 배치 제약 조건 집합에 대해 최적화 하 여 holographic 개체에 가장 적합 한 물리적 위치를 결정할 수 있습니다.

젊은 Conker 및 조각을 개발 하는 동안 Asobo 스튜디오은이 문제를 해결 하 고이를 위해 방 해 찾기를 개발 합니다. 이러한 각 게임에는 게임 관련 요구 사항이 있지만 공유 되는 핵심 공간을 이해 하는 기술이 있습니다. HoloToolkit SpatialUnderstanding 라이브러리는이 기술을 캡슐화 하 여 벽에서 빈 공간을 신속 하 게 찾고, 최대값에 개체를 배치 하 고, 문자를 놓을 수 있는 개체를 배치 하 고, 수많은 기타 공간을 이해 하는 쿼리를 수행할 수 있습니다.

모든 소스 코드가 포함 되어 있으므로 요구 사항에 맞게 사용자 지정 하 고 커뮤니티의 개선 사항을 공유할 수 있습니다. C++ 해 찾기에 대 한 코드는 UWP dll로 래핑되어 MixedRealityToolkit 내에 포함 된 prefab의 drop을 사용 하 여 Unity에 노출 되었습니다.

### <a name="understanding-modules"></a>모듈 이해

모듈에 의해 노출 되는 세 가지 기본 인터페이스에는 단순 화면 및 공간 쿼리를 위한 토폴로지, 개체 검색을 위한 모양, 개체 집합을 기반으로 하는 제약 조건에 대 한 개체 배치 시도 기 방법이 있습니다. 각각에 대 한 설명은 다음과 같습니다. 세 가지 기본 모듈 인터페이스 외에도, 광선 캐스팅 인터페이스를 사용 하 여 태그가 지정 된 서피스 형식을 검색 하 고 사용자 지정 watertight playspace 메시를 복사할 수 있습니다.

### <a name="ray-casting"></a>광선 캐스팅

방을 검색 하 고 완료 한 후에는 층, 천장 및 벽 같은 표면에 대 한 레이블이 내부적으로 생성 됩니다. "PlayspaceRaycast" 함수는 광선이 알려진 표면과 충돌 하는 경우를 반환 하 고, 해당 하는 경우에는 "RaycastResult" 형식으로 해당 화면에 대 한 정보를 반환 합니다.

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

내부적으로 raycast는 playspace의 계산 된 8cm 제곱 voxel 표현에 대해 계산 됩니다. 각 voxel에는 처리 된 토폴로지 데이터 (즉, surfels)를 포함 하는 surface 요소 집합이 포함 되어 있습니다. 교차 된 voxel 셀에 포함 된 surfels는 토폴로지 정보를 조회 하는 데 사용 되는 가장 일치 하는 항목과 비교 됩니다. 이 토폴로지 데이터에는 "SurfaceTypes" 열거형의 형식으로 반환 된 레이블 및 교차 된 표면의 노출 영역이 포함 됩니다.

Unity 샘플에서 커서는 각 프레임을 비춥니다. 먼저, Unity의 colliders에 대해 합니다. 두 번째는 모듈의 세계 표현에 대해 이해 합니다. 마지막으로 UI 요소를 다시 한 번 더 합니다. 이 응용 프로그램에서 UI는 우선 순위, 그 다음으로 이해 결과, 마지막으로 Unity의 colliders를 가져옵니다. SurfaceType은 커서 옆에 텍스트로 보고 됩니다.

![표면 형식의 레이블이 커서 옆에 표시 됩니다.](images/su-raycastresults-300px.jpg)<br>
*표면 형식의 레이블이 커서 옆에 표시 됩니다.*

### <a name="topology-queries"></a>토폴로지 쿼리

DLL 내에서 토폴로지 관리자는 환경의 레이블 지정을 처리 합니다. 위에서 언급 한 것 처럼 대부분의 데이터는 voxel 볼륨 내에 포함 된 surfels 내에 저장 됩니다. 또한 "PlaySpaceInfos" 구조체를 사용 하 여 전 세계 맞춤 (아래에 자세히 설명), 층 및 천장 높이를 포함 하 여 playspace에 대 한 정보를 저장 합니다. 추론은 바닥, 천장 및 벽을 결정 하는 데 사용 됩니다. 예를 들어 1 개의 m2 노출 영역이 있는 가장 크고 가장 작은 가로 표면은 바닥으로 간주 됩니다. 검색 프로세스 중에 카메라 경로도이 프로세스에서 사용 됩니다.

토폴로지 관리자에 의해 노출 되는 쿼리의 하위 집합은 dll을 통해 노출 됩니다. 노출 된 토폴로지 쿼리는 다음과 같습니다.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

각 쿼리에는 쿼리 유형과 관련 된 매개 변수 집합이 있습니다. 다음 예에서는 사용자가 원하는 볼륨의 최소 높이 & 너비, 바닥의 최소 배치 높이 및 볼륨 앞에 있는 최소 여유 공간을 지정 합니다. 모든 측정이 미터 단위입니다.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

이러한 각 쿼리는 미리 할당 된 "TopologyResult" 구조체 배열을 사용 합니다. "LocationCount" 매개 변수는 전달 된 배열의 길이를 지정 합니다. 반환 값은 반환 된 위치 수를 보고 합니다. 이 숫자는 전달 된 "locationCount" 매개 변수 보다 크지 않습니다.

"TopologyResult"에는 반환 된 볼륨의 중심 위치, 방향 (예: 일반) 및 찾은 공간의 크기가 포함 됩니다.

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

Unity 샘플에서 이러한 각 쿼리는 가상 UI 패널의 단추에 연결 됩니다. 샘플에서는 이러한 각 쿼리에 대 한 매개 변수를 적절 한 값으로 하드 코드 합니다. 더 많은 예제는 샘플 코드의 SpaceVisualizer.cs를 참조 하세요.

### <a name="shape-queries"></a>셰이프 쿼리

Dll 내부에서 셰이프 분석기 ("ShapeAnalyzer_W")는 토폴로지 분석기를 사용 하 여 사용자가 정의한 사용자 지정 셰이프와 일치 시킵니다. Unity 샘플은 셰이프 집합을 정의 하 고 셰이프 탭 내의 앱 내 쿼리 메뉴를 통해 결과를 제공 합니다. 사용자는 자신의 개체 셰이프 쿼리를 정의 하 고 응용 프로그램에 필요한 대로 해당 쿼리를 사용할 수 있습니다.

셰이프 분석은 가로 표면 에서만 작동 합니다. 예를 들어, 소파는 평평한 좌석 표면 및 소파 위쪽의 평면에 의해 정의 됩니다. 셰이프 쿼리는 두 개의 서피스가 정렬 되 고 연결 된 특정 크기, 높이 및 가로 세로 막대의 두 표면을 찾습니다. Api 용어를 사용 하 여 소파와 후면 위쪽은 셰이프 구성 요소 이며 맞춤 요구 사항은 셰이프 구성 요소 제약 조건입니다.

"Sittable" 개체에 대 한 Unity 샘플 (ShapeDefinition.cs)에 정의 된 예제 쿼리는 다음과 같습니다.

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

각 셰이프 쿼리는 각각 구성 요소 제약 조건 집합과 구성 요소 간의 종속성을 나열 하는 셰이프 제약 조건 집합을 포함 하는 셰이프 구성 요소 집합으로 정의 됩니다. 이 예에는 단일 구성 요소 정의에 세 개의 제약 조건이 포함 되 고 구성 요소 간의 모양 제약 조건 (구성 요소 하나만 있는 경우)이 포함 되지 않습니다.

이와 대조적으로, 소파 셰이프에는 두 개의 셰이프 구성 요소와 4 개의 셰이프 제약 조건이 있습니다. 구성 요소는 사용자의 구성 요소 목록에서 인덱스로 식별 됩니다 (이 예제에서는 0 및 1).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

래퍼 함수는 사용자 지정 셰이프 정의를 쉽게 만들기 위해 Unity 모듈에서 제공 됩니다. 구성 요소 및 모양 제약 조건의 전체 목록은 "ShapeComponentConstraint"의 "SpatialUnderstandingDll.cs" 및 "ShapeConstraint" 구조체에서 찾을 수 있습니다.

![이 화면에서 사각형 모양을 찾았습니다.](images/su-shapequery-300px.jpg)<br>
*이 화면에서 사각형 모양을 찾았습니다.*

### <a name="object-placement-solver"></a>개체 배치 해 찾기

개체 배치 해결 기를 사용 하 여 개체를 배치할 실제 방에 있는 이상적인 위치를 식별할 수 있습니다. 개체 규칙과 제약 조건이 지정 된 경우 가장 적합 한 위치를 찾을 수 있습니다. 또한 개체 쿼리는 "Solver_RemoveObject" 또는 "Solver_RemoveAllObjects" 호출을 사용 하 여 개체가 제거 될 때까지 지속 되어 제한 된 다중 개체 배치를 허용 합니다. 개체 배치 쿼리는 매개 변수가 있는 배치 유형, 규칙 목록 및 제약 조건 목록의 세 부분으로 구성 됩니다. 쿼리를 실행 하려면 다음 API를 사용 합니다.

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

이 함수는 개체 이름, 배치 정의 및 규칙 및 제약 조건 목록을 사용 합니다. 래퍼 C# 는 규칙 및 제약 조건 생성을 용이 하 게 하는 생성 도우미 함수를 제공 합니다. 배치 정의에는 쿼리 유형 즉, 다음 중 하나를 포함 합니다.

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

각 배치 형식에는 해당 형식에 고유한 매개 변수 집합이 있습니다. "ObjectPlacementDefinition" 구조체에는 이러한 정의를 만들기 위한 정적 도우미 함수 집합이 포함 되어 있습니다. 예를 들어 바닥에서 개체를 배치할 위치를 찾으려면 다음 함수를 사용할 수 있습니다. 공용 정적 ObjectCreate_OnFloor (Vector3 halfDims) 배치 유형 외에도 규칙 및 제약 조건 집합을 제공할 수 있습니다. 규칙을 위반할 수 없습니다. 그러면 형식 및 규칙을 충족 하는 가능한 배치 위치가 최적의 배치 위치를 선택 하기 위해 제약 조건 집합에 대해 최적화 됩니다. 제공 된 정적 생성 함수를 통해 각 규칙 및 제약 조건을 만들 수 있습니다. 아래에는 규칙 및 제약 조건 생성 함수 예제가 나와 있습니다.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

아래 개체 배치 쿼리는 이전에 배치 된 다른 개체와 실내 가운데 근처에서 절반 측정기 큐브를 표면의 가장자리에 배치 하는 위치를 찾고 있습니다.

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

성공 하면 배치 위치, 차원 및 방향을 포함 하는 "ObjectPlacementResult" 구조가 반환 됩니다. 또한 배치가 배치 된 개체의 내부 목록에 추가 됩니다. 이후 배치 쿼리에서는이 개체를 고려 합니다. Unity 샘플의 "LevelSolver.cs" 파일에는 더 많은 예제 쿼리가 포함 되어 있습니다.

![개체 배치 결과](images/su-objectplacement-1000px.jpg)<br>
*그림 3: 파란 상자에는 바닥의 세 위치에서 카메라 위치 규칙을 벗어난 결과를 보여 주는 방법이 있습니다.*

수준 또는 응용 프로그램 시나리오에 필요한 여러 개체의 배치 위치를 해결 하는 경우에는 먼저 필요에 따라 공간을 찾을 수 있는 확률을 최대화 하기 위해 필수적인 개체와 큼 개체를 해결 합니다. 배치 순서는 중요 합니다. 개체 배치를 찾을 수 없는 경우 제한 된 구성으로 시도 합니다. 여러 방 구성에서 기능을 지원 하려면 대체 (fallback) 구성 집합이 있어야 합니다.

### <a name="room-scanning-process"></a>대화방 스캔 프로세스

HoloLens에서 제공 하는 공간 매핑 솔루션은 문제 공간의 전체 영역에 대 한 요구 사항을 충족 하기에 충분히 제네릭으로 설계 되었지만 공간 파악 모듈은 두 가지 특정 게임의 요구 사항을 지원 하도록 만들어졌습니다. 해당 솔루션은 아래에 요약 된 특정 프로세스 및 가정 집합을 중심으로 구성 됩니다.

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

사용자 구동 재생 공간 "그리기"-검사 단계 중에 사용자가 재생 속도를 이동 하 고 표시 하 여 포함 해야 하는 영역을 효과적으로 그려야 합니다. 생성 된 메시는이 단계에서 사용자 의견을 제공 하는 데 중요 합니다. 실내 홈 또는 office 설정 – 쿼리 함수는 직각으로 평면 및 벽 주위에 디자인 됩니다. 소프트 제한입니다. 그러나 검사 단계 중에 주 축 분석을 완료 하 여 주 및 보조 축을 따라 메시 공간 분할을 최적화 합니다. 포함 된 SpatialUnderstanding.cs 파일은 검사 단계 프로세스를 관리 합니다. 다음 함수를 호출 합니다.

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

"SpatialUnderstanding" 동작으로 구동 되는 검색 흐름은 InitScan을 호출한 다음 각 프레임을 UpdateScan 합니다. 통계 쿼리가 적절 한 검사를 보고 하면 사용자는 요청을 눌러 RequestFinish를 호출 하 여 검사 단계의 끝을 나타낼 수 있습니다. UpdateScan는 반환 값이 dll 처리를 완료 했음을 나타냅니다.

### <a name="understanding-mesh"></a>메시 이해

Dll 이해는 내부적으로 playspace를 8cm 크기의 voxel 큐브 그리드로 저장 합니다. 검색의 초기 부분에서 주 구성 요소 분석을 완료 하 여 방의 축을 확인 합니다. 내부적으로 이러한 축에 맞춰진 voxel 공간을 저장 합니다. 메시는 거의 매 초 마다 voxel 볼륨에서 isosurface를 추출 하 여 생성 됩니다. 

![Voxel 볼륨에서 생성 된 메시 생성](images/su-custommesh.jpg)<br>
*Voxel 볼륨에서 생성 된 메시 생성*

## <a name="troubleshooting"></a>문제 해결
* [SpatialPerception](#setting-the-spatialperception-capability) 기능을 설정 했는지 확인 합니다.
* 추적이 손실 되 면 다음 OnSurfaceChanged 이벤트는 모든 메시를 제거 합니다.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Mixed Reality Toolkit의 공간 매핑
Mixed Reality Toolkit v 2에서 공간 매핑을 사용 하는 방법에 대 한 자세한 내용은 MRTK docs의 <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">공간 인식 섹션</a> 을 참조 하세요.

## <a name="see-also"></a>참조
* [MR 공간 230: 공간 매핑](holograms-230.md)
* [좌표계](coordinate-systems.md)
* [Unity의 좌표계](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a>
* <a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine. 범위</a>
