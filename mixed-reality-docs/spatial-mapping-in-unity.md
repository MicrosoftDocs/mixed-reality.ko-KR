---
title: Unity에서 공간 매핑
description: 렌더링 및 unity에서와 관련해 서 실제 형상와 충돌 합니다.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity 공간 매핑, 렌더러, collider, 메시, 검색, 구성 요소
ms.openlocfilehash: 8f7bad1651ab31b2e83ad9d9c8f465547fbbdc5a
ms.sourcegitcommit: 2f600e5ad00cd447b180b0f89192b4b9d86bbc7e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2019
ms.locfileid: "67148645"
---
# <a name="spatial-mapping-in-unity"></a>Unity에서 공간 매핑

이 항목에서는 사용 하는 방법 설명 [공간 매핑](spatial-mapping.md) Unity 프로젝트에서 HoloLens 장치 배치, 폐색, 공간 분석 등에 대 한 주변에 화면을 나타내는 삼각형 메시를 검색 합니다.

Unity에는 다음과 같은 방법으로 개발자에 게 노출 되는 공간 매핑에 대 한 전체 지원이 됩니다.
1. 공간을 MixedRealityToolkit에서 사용할 수 있는 구성 요소를 매핑, 제공 하는 편리 하 고 빠른 경로 공간 매핑을 사용 하 여 시작
2. 하위 공간 매핑 전체를 제공 하는 Api 제어 하 고 더 복잡 한 응용 프로그램 특정 사용자 지정을 사용 하도록 설정

앱에서 공간 매핑을 사용 하려면 spatialPerception 기능에 AppxManifest에서 설정 해야 합니다.

## <a name="setting-the-spatialperception-capability"></a>SpatialPerception 기능 설정

공간 매핑 데이터를 사용 하는 앱에 대 한 순서로 SpatialPerception 기능 활성화 되어야 합니다.

SpatialPerception 기능을 사용 하도록 설정 하는 방법:
1. Unity 편집기에서 엽니다는 **"플레이어 설정"** 창 (편집 > 프로젝트 설정 > Player)
2. 클릭 합니다 **"Windows Store"** 탭
3. 확장 **"게시 설정"** 확인 합니다 **"SpatialPerception"** 의 기능을 **"기능"** 목록

Visual Studio 솔루션에 이미 Unity 프로젝트를 내보낸 경우 해야 하거나 내보낼 새 폴더 또는 수동으로 [이 기능은 Visual Studio에서 AppxManifest 설정](spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)합니다.

공간 매핑에는 적어도 10.0.10586.0의 MaxVersionTested도를 필요합니다.
1. Visual Studio에서 마우스 오른쪽 단추로 클릭 **Package.appxmanifest** 솔루션 탐색기에서 선택 **코드 보기**
2. 지정 하는 줄을 찾습니다 **TargetDeviceFamily** 변경할 **MaxVersionTested "10.0.10240.0" =** 에 **MaxVersionTested "10.0.10586.0" =**
3. **저장** Package.appxmanifest 합니다.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Unity의 기본 제공 공간 매핑 구성 요소를 사용 하 여 시작

Unity는 쉽게 공간 매핑에 앱을 추가 하는 것에 대 한 2 개 구성 요소가 **공간 매핑 렌더러** 하 고 **공간 매핑 Collider**합니다.

### <a name="spatial-mapping-renderer"></a>공간 매핑 렌더러

공간 매핑 메시의 시각화에 대 한 공간 매핑 렌더러를 수 있습니다.

![Unity에서 공간 매핑 렌더러](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>공간 매핑 Collider

공간 매핑 Collider holographic 콘텐츠 (또는 문자)에 대 한 허용과 같은 상호 작용 물리학 공간 매핑 메시를 사용 하 여 합니다.

![Unity에서 Collider 공간 매핑](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>기본 제공 공간 매핑 구성 요소를 사용 하 여

시각화와 물리적 표면은 상호 작용 하려는 경우 앱에 두 구성 요소를 추가할 수 있습니다.

Unity 앱에서 이러한 두 구성 요소를 사용:
1. 공간 표면 메시를 검색 하려는 영역의 가운데에 GameObject를 선택 합니다.
2. 검사기 창에서 **Add Component** > **XR** > **공간 매핑 Collider** 또는 **공간 매핑 렌더러**합니다.

이러한 구성 요소를 사용 하는 방법에 자세한 세부 정보를 찾을 수 있습니다 합니다 <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity 설명서 사이트</a>합니다.

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>기본 제공 공간 매핑 구성 요소를 넘어

이러한 구성 요소 확인이 끌어서 놓기 쉽게 시작 하기 위한 공간 매핑.  진행 하려는 경우 두 가지 주요 경로가 있습니다 탐색:
* 고유한 하위 메시에 처리를 위해 하위 수준 공간 매핑 스크립트 API에 대 한 아래 섹션을 참조 합니다.
* 더 높은 수준의 메시 분석을 수행 하기에 SpatialUnderstanding 라이브러리에 대 한 아래 섹션을 참조 하세요 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>합니다.

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>API를 사용 하는 하위 수준 Unity 공간 매핑

공간 매핑 렌더러 및 공간 매핑 Collider 구성 요소에서 것 보다 더 많은 제어가 필요한 경우에 하위 수준 공간 매핑 스크립트 Api를 사용할 수 있습니다.

**Namespace:** *UnityEngine.XR.WSA*<br>
**형식**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

다음은 공간 매핑 Api를 사용 하는 응용 프로그램에 대 한 제안 된 흐름에 대 한 개요입니다.

### <a name="set-up-the-surfaceobservers"></a>SurfaceObserver(s) 설정

에 대 한 공간 매핑 데이터를 해야 하는 공간의 각 응용 프로그램에서 정의한 영역에 대 한 하나의 SurfaceObserver 개체를 인스턴스화하십시오.

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, 또는 SetVolumeAsFrustum를 호출 하 여 각 SurfaceObserver 개체에 대 한 데이터를 제공 하는 공간의 지역을 지정 합니다. 단순히 이러한 방법 중 하나를 다시 호출 하 여 영역을 나중에 공간을 재정의할 수 있습니다.

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

SurfaceObserver.Update()를 호출 하면 각 공간 화면 공간 매핑 시스템에 대 한 새 정보가 있는 공간의 SurfaceObserver의 지역에 대 한 처리기를 제공 해야 합니다. 하나의 공간 표면에 대 한 처리기를 수신 합니다.

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a>화면 변경 내용 처리

처리에 몇 가지 주요 경우가 있습니다. 추가 및 동일 하 게 사용할 수 있는 업데이트 된 코드 경로 및 제거 합니다.
* 예제에서 추가 및 업데이트 된 경우에서에서는 더하거나이 사전에서 메시, SurfaceData 구조체 필요한 구성 요소를 사용 하 여 만든 메시 데이터로 GameObject를 채우는 데 RequestMeshDataAsync 호출 GameObject 나타내는 가져오기 및 장면에 배치 합니다.
* 제거의 경우 사전에서이 메시를 나타내는 GameObject를 제거 하 고 삭제 합니다.

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

### <a name="handling-data-ready"></a>데이터 준비를 처리합니다.

OnDataReady 처리기 SurfaceData 개체를 받습니다. WorldAnchor, MeshFilter 고 (선택 사항) MeshCollider 개체에 연결 된 공간 화면의 최신 상태를 반영 합니다. 필요에 따라 분석을 수행 하거나 [처리](spatial-mapping.md#mesh-processing) MeshFilter 개체의 메시 멤버에 액세스 하 여 메시 데이터입니다. 최신 메시를 사용 하 여 공간 화면을 렌더링 하 고 (선택 사항) 사용 raycasts 및 물리학 충돌 합니다. SurfaceData 내용의 null 인지 확인 하는 것이 반드시 합니다.

### <a name="start-processing-on-updates"></a>업데이트에 대 한 처리를 시작 합니다.

SurfaceObserver.Update() 지연 모든 프레임에서 호출 되어야 합니다.

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

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a>더 높은 수준의 메시 분석: SpatialUnderstanding

합니다 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> holographic Unity Api를 기반으로 구축 holographic 개발에 대 한 유용한 유틸리티 코드의 컬렉션인 경우.

### <a name="spatial-understanding"></a>공간 이해

실제에서 홀로그램을 배치 하는 경우 공간 매핑 외 메시 및 평면 표면 이동할는 것이 좋습니다. 배치는 절차적 완료 되 면 더 높은 수준의 환경 이해 좋습니다. 이 일반적으로 floor, ceiling, 및 벽에 대 한 결정을 내리는 필요 합니다. 또한 holographic 개체에 대 한 가장 좋은 물리적 위치를 확인 하기 위해 배치 제약 조건 집합에 대해 최적화할 수 있습니다.

Asobo Studios Young Conker 조각을을 개발 하는 동안이 목적을 위해 공간 solver 개발에이 문제가 머리에 직면 합니다. 이러한 각 게임 게임 특정 요구 사항 있었지만 이러한 핵심 기술 공간 이해를 공유 합니다. 식별 벽, 개체 한계를 배치할 위치에 빈 공간 찾기 신속 하 게 할 수 있도록 하는 라이브러리에는이 기술은 캡슐화 HoloToolkit.SpatialUnderstanding 보관, 문자 및 다른 공간 이해 쿼리 수많은에 배치 합니다.

소스 코드의 모든 요구 사항에 맞게 사용자 지정 하 고 커뮤니티에 향상 된 기능을 공유할 수 있도록 포함 됩니다. 에 대 한 코드는 C++ solver UWP dll로 래핑 되었으며 prefab은 MixedRealityToolkit 내에 포함 된에서 drop을 사용 하 여 Unity에 노출 합니다.

### <a name="understanding-modules"></a>이해 모듈

모듈에 의해 노출 되는 세 가지 기본 인터페이스가: 간단한 화면 및 공간 쿼리, 개체 감지에 대 한 셰이프 및 개체 집합의 제약 조건 기반 배치에 대 한 개체 배치 해 찾기에 대 한 토폴로지입니다. 이러한 각 옵션은 아래 설명 되어 있습니다. 세 개의 주 모듈 인터페이스를 외에도 태그가 지정 된 화면 형식을 검색할 ray 캐스팅 인터페이스를 사용할 수 및 사용자 지정 watertight playspace 메시 복사할 수 있습니다.

### <a name="ray-casting"></a>광선 캐스팅

대화방을 검색 하 고 완료 된 후 레이블 floor, ceiling, 및 벽 같은 표면에 내부적으로 생성 됩니다. 함수 광선을 그린 받고 광선과 알려진된 화면을 사용 하 여 충돌 하는 경우 그리고 있다면 반환 "PlayspaceRaycast", "RaycastResult"의 형태로 해당 화면에 대 한 정보입니다.

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

내부적으로 raycast는 playspace의 3 제곱 계산된 8 cm voxel 표현에 대해 계산 됩니다. 각 voxel 처리 토폴로지 데이터 (즉, surfels)를 사용 하 여 화면 요소의 집합을 포함합니다. 교차 voxel 셀 내에 포함 된 surfels 비교한 후 가장 일치 하는 토폴로지 정보를 찾는 데 사용 됩니다. 이 토폴로지 데이터 교차 된 노출의 노출 영역 뿐만 아니라 "SurfaceTypes" 열거형 형식의 반환 레이블을 포함 되어 있습니다.

Unity 샘플에서는 커서 각 프레임을 광선을 캐스팅합니다. Unity의 colliders 첫째,에 대 한. 둘째, 이해 모듈의 세계 표현에 대 한입니다. 와 마지막으로 다시 UI 요소입니다. 이 응용 프로그램에서 UI 이해 하면 Unity의 colliders 및 마지막으로, 다음 우선 순위를 가져옵니다. SurfaceType 커서 옆에 있는 텍스트로 보고 됩니다.

![화면 형식 커서 옆에 있는 라고 합니다.](images/su-raycastresults-300px.jpg)<br>
*화면 형식 커서 옆에 있는 라고 합니다.*

### <a name="topology-queries"></a>쿼리 토폴로지

DLL 내에서 토폴로지 manager 환경의 레이블 지정을 처리 합니다. 위에서 설명 했 듯이 surfels, voxel 볼륨 내에 포함 된 내에 저장 된 데이터를 많이 합니다. 또한 "PlaySpaceInfos" 구조 world 맞춤 (자세한 내용은 아래 참조), floor, ceiling 높이 등을 playspace에 대 한 정보를 저장 됩니다. 추론은 floor, ceiling, 및 벽을 결정 하는 데 사용 됩니다. 예를 들어, 1의 m2 노출 영역 보다 큰를 사용 하 여 가장 크고 가장 낮은 가로 화면 바닥을 간주 됩니다. 검색 프로세스 중 카메라 경로에서이 프로세스는 참고 합니다.

토폴로지 관리자에 의해 노출 되는 쿼리의 하위 집합만 아웃 dll을 통해 노출 됩니다. 노출 된 토폴로지 쿼리는 다음과 같습니다.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

각 쿼리 매개 변수, 쿼리 형식에 특정 집합을에 있습니다. 다음 예제에서는 사용자의 최소 높이 및 원하는 볼륨, floor, 및 최소한의 여유 공간 볼륨 앞에 위의 최소 배치 높이 너비를 지정합니다. 모든 측정 미터의 경우

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

이 쿼리는 각각 "TopologyResult" 구조의 사전 할당 된 배열이 됩니다. "LocationCount" 매개 변수에 전달 된 배열의 길이 지정합니다. 반환 값은 반환 된 위치 수를 보고합니다. 이 수는 전달 된 보다 큰 "locationCount" 매개 변수에서입니다.

"TopologyResult" 반환 된 볼륨, 연결 방향 (즉, 표준) 및 검색 공간의 크기의 가운데 위치를 포함합니다.

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

Unity 샘플에서, 가상 UI 패널에서 단추에 이러한 쿼리는 각 연결 됩니다. 하드 샘플의 적절 한 값으로이 쿼리는 각각에 대 한 매개 변수를 코드입니다. 예를 보려면 샘플 코드에서 SpaceVisualizer.cs를 참조 하세요.

### <a name="shape-queries"></a>셰이프 쿼리

Dll 내에서 셰이프 분석기 ("ShapeAnalyzer_W")는 사용자가 정의한 사용자 지정 셰이프를 대조할 토폴로지 분석기를 사용 합니다. Unity 샘플 셰이프 집합을 정의 하 고 셰이프 탭 내의 앱에서 쿼리 메뉴를 통해 결과 출력을 노출 합니다. 목적은 사용자가 자신의 개체 셰이프 쿼리를 정의 하 고 확인 수는 해당 응용 프로그램에서 필요에 따라를 사용 합니다.

셰이프 분석만 가로 화면에서 작동 하는 참고 합니다. 예를 들어, 소파, 플랫 사용자 화면과 플랫 맨 뒤로 소파에 의해 정의 됩니다. Shape 쿼리의 정렬 및 연결 된 두 개의 화면을 사용 하 여 특정 크기, 높이 및 측면 범위의 두 화면을 찾습니다. Api 용어를 사용 하 couch 자리와 백 맨 위에 셰이프 구성 요소 및 맞춤 요구 사항은 셰이프 구성 요소 제약 조건입니다.

"Sittable" 개체에 대 한 Unity 샘플 (ShapeDefinition.cs)에 정의 된 쿼리의 예는 다음과 같습니다.

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

Shape 쿼리의 각 구성 요소 제약 조건 집합 및 셰이프 제약 조건의 집합을 사용 하 여 각 셰이프 구성 요소 집합을 정의한는 구성 요소 간의 종속성을 나열 합니다. 이 예제 (구성 요소가 하나만 하므로)는 단일 구성 요소 정의 및 구성 요소 간에 모양 제약 없이 세 가지 제약 조건을 포함 합니다.

반면, 소파 모양을 두 셰이프 구성 요소와 네 개의 셰이프 제약 조건에 있습니다. 구성 요소는 (0과 1이 예제의) 사용자의 구성 요소 목록에서 해당 인덱스로 식별 되는 참고 합니다.

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

래퍼 함수는 사용자 지정 셰이프 정의 쉽게 만들기 위한 Unity 모듈에서 제공 됩니다. 구성 요소 및 셰이프 제약 조건의 전체 목록은 "SpatialUnderstandingDll.cs" "ShapeComponentConstraint" 및 "ShapeConstraint" 구조 내에 있습니다.

![이 화면에서 사각형 셰이프를 찾을 수합니다](images/su-shapequery-300px.jpg)<br>
*이 화면에서 사각형 셰이프를 찾을 수합니다*

### <a name="object-placement-solver"></a>개체 배치 해 찾기

개체를 배치 하는 물리적 공간에 이상적인 위치를 식별할 수 개체 배치 해 사용할 수 있습니다. 개체 규칙 및 제약 조건이 지정 된 위치를 적합 해를 찾기가 찾습니다. 또한 개체 쿼리는 "Solver_RemoveObject"를 사용 하 여 개체가 제거 되거나 "Solver_RemoveAllObjects" 호출을 허용 제한 다중 개체 배치 될 때까지 유지 됩니다. 개체 배치 쿼리 세 부분으로 구성 됩니다: 매개 변수, 규칙의 목록 및 제약 조건 목록을 사용 하 여 배치 형식입니다. 쿼리를 실행 하려면 다음 API를 사용 합니다.

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

이 함수는 개체 이름, 배치 정 및 규칙 및 제약 조건 목록을 사용합니다. C# 래퍼 생성 규칙 및 제약 조건 생성을 간편 하 게 도우미 함수를 제공 합니다. 배치 정의는 다음 중 하나 이므로 쿼리 형식을 포함합니다.

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

매개 변수 형식에 고유 집합에 각 배치 형식 "ObjectPlacementDefinition" 구조에는 이러한 정의 만들기 위한 정적 도우미 함수 집합을 포함 합니다. 예를 들어, 현장에서 개체를 삽입할 수 있는 위치를 찾으려면 다음 함수를 사용할 수 있습니다. 공용 정적 ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) 외에 배치 형식, 규칙 및 제약 조건 집합을 제공할 수 있습니다. 규칙을 위반할 수 없습니다. 형식 및 규칙을 충족 하는 위치를 배치 하는 다음 제약 조건 집합에 대 한 최적의 배치 위치를 선택 하기 위해 최적화 됩니다. 제공 된 정적 생성 함수에 의해 각 제약 조건 및 규칙을 만들 수 있습니다. 규칙 및 제약 조건 생성 함수 예제는 아래 제공 됩니다.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

개체 아래의 배치 쿼리를 찾고 절반 미터 큐브는 화면의 가장자리에 배치 하는, 다른에서 이전에 개체 배치 대화방의 가운데 근처 위치 합니다.

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

성공 하면 배치 위치를 포함 하는 "ObjectPlacementResult" 구조체 차원과 방향을 반환 됩니다. 또한 배치는 dll의 내부 목록을 배치 하는 개체에 추가 됩니다. 후속 배치 쿼리를이 개체를 고려 됩니다. Unity 예제의 "LevelSolver.cs" 파일을 더 많은 예제 쿼리를 포함합니다.

![개체 배치의 결과](images/su-objectplacement-1000px.jpg)<br>
*그림 3: 파란색 상자 floor 세 위치에서 결과 사용 하 여 카메라 위치 규칙에서 쿼리 하는 방법*

수준 또는 응용 프로그램 시나리오에 필요한 여러 개체의 배치 위치에 대 한 해결 하는 경우 먼저 공간을 찾을 수 있는 확률을 최대화 하려면에서 필수적인 및 큰 개체를 해결 합니다. 배치 순서가 중요 합니다. 개체 배치를 찾을 수 없는 경우에 덜 제한적된 구성 해 보십시오. 대체 (fallback) 구성 집합을는 것이 많은 공간 구성에서 기능을 지 원하는 데 중요 합니다.

### <a name="room-scanning-process"></a>대화방 검색 프로세스

HoloLens를 제공한 공간 매핑 솔루션은 문제 공간 전체의 요구에 맞게 충분히 제네릭으로 되도록 설계 되었지만, 공간 이해 모듈을 두 특정 게임의 요구를 지원 하도록 빌드 되었습니다. 해당 솔루션은 특정 프로세스 및 아래에 요약 가정 집합이 구성 됩니다.

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

사용자 구동 playspace "그리기" – 검색 단계에서는 사용자 이동 하 고 효과적으로 포함 해야 하는 영역을 그리기 속도 수행 하는 관련 찾습니다. 생성 된 메시 반드시이 단계에서 사용자에 게 피드백을 제공 합니다. 실내 홈 또는 office 설치 – 쿼리 함수 평면 표면 및 직각으로 벽 바탕으로 설계 되었습니다. 소프트 제한 됩니다. 그러나 검색 단계에서는 기본 축 분석을 주 및 부 축 따라 메시 공간 분할을 최적화 하기 위해 완료 됩니다. 포함된 된 SpatialUnderstanding.cs 파일 검색 단계 프로세스를 관리합니다. 다음 함수를 호출합니다.

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

"SpatialUnderstanding" 동작을 통해 제어 스캐닝 흐름을 각 프레임 InitScan, 다음 UpdateScan 호출 합니다. 통계 쿼리는 적절 한 검사를 보고, 사용자 RequestFinish 검사 단계의 끝을 나타내기 위해 호출 airtap에 허용 됩니다. 반환 될 때까지 호출할 UpdateScan 계속 값 dll 처리 완료 되었음을 나타냅니다.

### <a name="understanding-mesh"></a>이해 메시

이해 dll을 playspace 크기가 8 cm voxel 큐브에 포함 된 표를 내부적으로 저장합니다. 검색의 시작 부분에서 하는 동안 대화방의 축을 확인 하려면 기본 구성 요소 분석을 완료 됩니다. 내부적으로 이러한 축 정렬 해당 voxel 공간을 저장 합니다. 메시를 isosurface voxel 볼륨에서 추출 하 여 약 1 초 마다 생성 됩니다. 

![생성 된 메시 voxel 볼륨에서 생성](images/su-custommesh.jpg)<br>
*생성 된 메시 voxel 볼륨에서 생성*

## <a name="troubleshooting"></a>문제 해결
* 설정 했는지 확인 합니다 [SpatialPerception](#setting-the-spatialperception-capability) 기능
* 추적 손실 되 면 다음 OnSurfaceChanged 이벤트는 모든 메시를 제거 합니다.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>혼합된 현실 도구 키트의 공간 매핑
혼합 현실 Toolkit v2를 사용 하 여 공간 매핑 사용에 대 한 자세한 내용은 참조는 <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">공간 인식 섹션</a> MRTK 문서.

## <a name="see-also"></a>참조
* [MR 공간 230: 공간 매핑](holograms-230.md)
* [좌표계](coordinate-systems.md)
* [Unity의 좌표계](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="http://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="http://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>
