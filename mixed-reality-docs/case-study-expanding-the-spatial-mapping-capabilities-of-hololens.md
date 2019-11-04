---
title: 사례 연구-HoloLens의 공간 매핑 기능 확장
description: Microsoft HoloLens에 대 한 첫 번째 앱을 만들 때 장치에서 공간 매핑의 경계를 푸시할 수 있는 정도를 확인 합니다.
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 공간 매핑
ms.openlocfilehash: 5142cb383d4408b29eb17eb5ede84d19b2533dc4
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436728"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>사례 연구-HoloLens의 공간 매핑 기능 확장

Microsoft HoloLens에 대 한 첫 번째 앱을 만들 때 장치에서 공간 매핑의 경계를 푸시할 수 있는 정도를 확인 합니다. Microsoft 스튜디오의 소프트웨어 엔지니어 인 Jeff Evertt는 사용자의 실제 환경에 holograms가 배치 되는 방식을 보다 강력 하 게 제어할 필요가 없는 새 기술이 개발 된 방식을 설명 합니다.

> [!NOTE]
> HoloLens 2는 environmentally 인식 응용 프로그램을 쉽게 개발할 수 있도록 설계 된 구조화 된 고급 환경 표현으로 혼합 현실 개발자를 제공 하는 새로운 [장면 이해 런타임을](scene-understanding.md)구현 합니다. 

## <a name="watch-the-video"></a>비디오 시청

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>공간 매핑 초과

HoloLens [에 대](https://www.microsoft.com/p/fragments/9nblggh5ggm8) 한 첫 번째 게임 인 HoloLens와 [젊은 Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)에서 작업 하는 동안, 실제 세계에서 holograms의 절차적 배치를 수행 하는 경우 사용자에 대 한 더 높은 수준의 이해를 요구 하 고 있습니다. 개발. 각 게임에는 고유한 특정 배치 요구 사항이 있습니다. 예를 들어 바닥 또는 테이블과 같은 여러 다른 표면을 구분 하 여 관련 위치에 대 한 단서를 제공할 수 있습니다. 또한 holographic 문자 (예: 소파 또는 자)가 될 수 있는 화면을 식별할 수 있도록 하려고 합니다. 젊은 Conker에서는 Conker와 자신의 상대가 플레이어의 방에서 발생 한 표면을 플랫폼으로 사용할 수 있습니다.

[Asobo 스튜디오](https://www.asobostudio.com/index.html), 이러한 게임을 위한 개발 파트너는이 문제를 해결 하 고 HoloLens의 공간 매핑 기능을 확장 하는 기술을 만들었습니다. 이를 사용 하 여 플레이어의 방을 분석 하 고 벽, 테이블, 한도, 층 등의 표면을 식별할 수 있습니다. 또한 제약 조건 집합에 대해 최적화 하 여 holographic 개체에 가장 적합 한 배치를 결정 하는 기능을 제공 합니다.

## <a name="the-spatial-understanding-code"></a>공간 이해 코드

Asobo의 원래 코드를 작성 하 고이 기술을 캡슐화 하는 라이브러리를 만들었습니다. Microsoft 및 Asobo는 이제이 코드를 오픈 소스로 사용 하 여 사용자가 자신의 프로젝트에서 사용할 수 있도록 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) 에서 사용할 수 있게 했습니다. 모든 소스 코드가 포함 되어 있으므로 요구 사항에 맞게 사용자 지정 하 고 커뮤니티의 개선 사항을 공유할 수 있습니다. C++ 해 찾기에 대 한 코드는 UWP DLL로 래핑되어 [MixedRealityToolkit 내에 포함 된 드롭 (prefab)](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)을 사용 하 여 Unity에 노출 되었습니다.

Unity 샘플에 포함 된 많은 유용한 쿼리를 사용 하 여 벽에서 빈 공간을 찾고, 바닥에 개체를 배치 하 고, 바닥에 개체를 배치 하 고, 사용할 문자 위치를 식별 하 고, 수많은 기타 공간을 이해 하는 쿼리를 사용할 수 있습니다.

HoloLens에서 제공 하는 공간 매핑 솔루션은 문제 공간의 전체 영역에 대 한 요구 사항을 충족 하기에 충분히 제네릭으로 설계 되었지만 공간 파악 모듈은 두 가지 특정 게임의 요구 사항을 지원 하도록 만들어졌습니다. 따라서 해당 솔루션은 특정 프로세스 및 가정 집합을 중심으로 구성 됩니다.
* **고정 크기 playspace**: 사용자가 init 호출에서 최대 playspace 크기를 지정 합니다.
* **일회성 검색 프로세스**:이 프로세스에는 사용자가 안내 하는 불연속 검색 단계가 필요 하며,이 단계는 playspace를 정의 합니다. 검색이 완료 될 때까지 쿼리 함수가 작동 하지 않습니다.
* **사용자 구동 재생 공간 "그리기"** : 검색 단계 중에 사용자가 플레이 공간을 이동 하 고 조회 하 여 포함 해야 하는 영역을 효과적으로 그릴 수 있습니다. 생성 된 메시는이 단계에서 사용자 의견을 제공 하는 데 중요 합니다.
* **실내 홈 또는 office 설정**: 쿼리 함수는 평평한 서피스와 벽 주위에 직각으로 디자인 됩니다. 소프트 제한입니다. 그러나 검사 단계 중에 주 축 분석을 완료 하 여 주 및 보조 축을 따라 메시 공간 분할을 최적화 합니다.

### <a name="room-scanning-process"></a>대화방 스캔 프로세스

공간 인식 모듈을 로드 하는 경우 가장 먼저 공간을 스캔 하 여 모든 사용 가능한 서피스 (예: 바닥, 천장 및 벽)를 식별 하 고 레이블을 지정 합니다. 검색 프로세스 중에는 공간을 확인 하 고 검색에 포함 해야 하는 영역을 "페인트" 합니다.

이 단계 중에 표시 되는 메시는 사용자가 검색 중인 대화방 부분을 알 수 있도록 하는 중요 한 시각적 피드백의 일부입니다. 공간 이해 모듈의 DLL은 내부적으로 playspace를 8cm 크기가 지정 된 voxel 큐브의 그리드로 저장 합니다. 검색의 초기 부분에서 주 구성 요소 분석을 완료 하 여 방의 축을 확인 합니다. 내부적으로 이러한 축에 맞춰진 voxel 공간을 저장 합니다. 메시는 거의 매 초 마다 voxel 볼륨에서 isosurface를 추출 하 여 생성 됩니다.

![흰색의 공간 매핑 메시 및 녹색의 playspace 메시 이해](images/spatial-mapping-500px.png)

흰색의 공간 매핑 메시 및 녹색의 playspace 메시 이해



포함 된 SpatialUnderstanding.cs 파일은 검사 단계 프로세스를 관리 합니다. 다음 함수를 호출 합니다.
* **SpatialUnderstanding_Init**: 시작 시 한 번 호출 됩니다.
* **GeneratePlayspace_InitScan**: 검색 단계를 시작 해야 함을 나타냅니다.
* **GeneratePlayspace_UpdateScan_DynamicScan**: 검색 프로세스를 업데이트 하기 위해 각 프레임 이라고 합니다. 카메라 위치와 방향이 전달 되며 위에 설명 된 playspace 그리기 프로세스에 사용 됩니다.
* **GeneratePlayspace_RequestFinish**: playspace를 마무리 하기 위해 호출 됩니다. 이렇게 하면 검색 단계에서 "칠해진" 영역을 사용 하 여 playspace를 정의 하 고 잠급니다. 응용 프로그램은 검색 단계 중에 통계를 쿼리할 수 있으며 사용자 의견을 제공 하기 위해 사용자 지정 메시를 쿼리할 수 있습니다.
* **Import_UnderstandingMesh**: 검색 하는 동안 모듈에서 제공 하는 **SpatialUnderstandingCustomMesh** 동작을 이해 하는 데에는 프로세스에 의해 생성 된 사용자 지정 메쉬가 정기적으로 쿼리 됩니다. 그리고 검사가 완료 된 후에도이 작업이 한 번 수행 됩니다.

**SpatialUnderstanding** 동작으로 구동 되는 검색 흐름은 **initscan**을 호출한 다음 각 프레임을 **UpdateScan** 합니다. 통계 쿼리가 적절 한 검사 범위를 보고할 때 사용자는 **Requestfinish** 를 호출 하 여 검색 단계의 끝을 나타내는 탭을 이동할 수 있습니다. **UpdateScan** 는 반환 값이 DLL 처리를 완료 했음을 나타냅니다.

## <a name="the-queries"></a>쿼리

검색이 완료 되 면 다음 세 가지 유형의 쿼리를 인터페이스에서 액세스할 수 있습니다.
* **토폴로지 쿼리**: 검색 된 대화방의 토폴로지를 기반으로 하는 빠른 쿼리입니다.
* **셰이프 쿼리**: 이러한 작업은 사용자가 정의 하는 사용자 지정 셰이프와 잘 일치 하는 가로 표면을 찾기 위해 토폴로지 쿼리 결과를 활용 합니다.
* **개체 배치 쿼리**: 이러한 쿼리는 개체에 대 한 규칙 및 제약 조건 집합을 기반으로 최적 위치를 찾는 보다 복잡 한 쿼리입니다.

세 가지 기본 쿼리 외에도 태그가 지정 된 서피스 형식을 검색 하는 데 사용할 수 있는 raycasting 인터페이스와 사용자 지정 watertight 대화방 메쉬가 복사 될 수 있습니다.

### <a name="topology-queries"></a>토폴로지 쿼리

DLL 내에서 토폴로지 관리자는 환경의 레이블 지정을 처리 합니다. 위에서 언급 한 것 처럼 대부분의 데이터는 voxel 볼륨 내에 포함 된 surfels 내에 저장 됩니다. 또한 **PlaySpaceInfos** 구조체를 사용 하 여 전 세계 맞춤 (아래에 자세히 설명), 층 및 천장 높이를 포함 하 여 playspace에 대 한 정보를 저장 합니다.

추론은 바닥, 천장 및 벽을 결정 하는 데 사용 됩니다. 예를 들어 1 개의 m2 노출 영역이 있는 가장 크고 가장 작은 가로 표면은 바닥으로 간주 됩니다. 검색 프로세스 중에 카메라 경로도이 프로세스에서 사용 됩니다.

토폴로지 관리자에 의해 노출 되는 쿼리의 하위 집합은 DLL을 통해 노출 됩니다. 노출 된 토폴로지 쿼리는 다음과 같습니다.
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

각 쿼리에는 쿼리 유형과 관련 된 매개 변수 집합이 있습니다. 다음 예에서는 사용자가 원하는 볼륨의 최소 높이 & 너비, 바닥의 최소 배치 높이 및 볼륨 앞에 있는 최소 여유 공간을 지정 합니다. 모든 측정이 미터 단위입니다.




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

이러한 각 쿼리는 미리 할당 된 **TopologyResult** 구조체 배열을 사용 합니다. **Locationcount** 매개 변수는 전달 된 배열의 길이를 지정 합니다. 반환 값은 반환 된 위치 수를 보고 합니다. 이 수는 전달 된 **Locationcount** 매개 변수 보다 크지 않습니다.

**TopologyResult** 에는 반환 된 볼륨의 중심 위치, 방향 (예: 일반) 및 찾은 공간의 크기가 포함 됩니다.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Unity 샘플에서 이러한 각 쿼리는 가상 UI 패널의 단추에 연결 됩니다. 샘플에서는 이러한 각 쿼리에 대 한 매개 변수를 적절 한 값으로 하드 코드 합니다. 더 많은 예제는 샘플 코드의 *SpaceVisualizer.cs* 를 참조 하세요.

### <a name="shape-queries"></a>셰이프 쿼리

DLL 내에서 shape analyzer (**ShapeAnalyzer_W**)는 토폴로지 분석기를 사용 하 여 사용자가 정의한 사용자 지정 셰이프와 일치 시킵니다. Unity 샘플에는 쿼리 메뉴의 셰이프 탭에 표시 되는 미리 정의 된 셰이프 집합이 있습니다.

셰이프 분석은 가로 표면 에서만 작동 합니다. 예를 들어, 소파는 평평한 좌석 표면 및 소파 위쪽의 평면에 의해 정의 됩니다. 셰이프 쿼리는 두 개의 서피스가 정렬 되 고 연결 된 특정 크기, 높이 및 가로 세로 막대의 두 표면을 찾습니다. Api 용어를 사용 하 여 소파와 소파의 위쪽은 셰이프 구성 요소 이며 맞춤 요구 사항은 셰이프 구성 요소 제약 조건입니다.

"Sittable" 개체에 대 한 Unity 샘플 (**ShapeDefinition.cs**)에 정의 된 예제 쿼리는 다음과 같습니다.




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

각 셰이프 쿼리는 각각 구성 요소 제약 조건 집합과 구성 요소 간의 종속성을 나열 하는 셰이프 제약 조건 집합을 포함 하는 도형 구성 요소 집합으로 정의 됩니다. 이 예에는 단일 구성 요소 정의에 세 개의 제약 조건이 포함 되 고 구성 요소 간의 모양 제약 조건 (구성 요소 하나만 있는 경우)이 포함 되지 않습니다.

이와 대조적으로, 소파 셰이프에는 두 개의 셰이프 구성 요소와 4 개의 셰이프 제약 조건이 있습니다. 구성 요소는 사용자의 구성 요소 목록에서 인덱스로 식별 됩니다 (이 예제에서는 0 및 1).




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

래퍼 함수는 사용자 지정 셰이프 정의를 쉽게 만들기 위해 Unity 모듈에서 제공 됩니다. 구성 요소 및 모양 제약 조건의 전체 목록은 **ShapeComponentConstraint** 및 **ShapeConstraint** 구조 내의 **SpatialUnderstandingDll.cs** 에서 찾을 수 있습니다.

![파란색 사각형은가 중 셰이프 쿼리의 결과를 강조 표시 합니다.](images/chair-shape-query-500px.png)

파란색 사각형은가 중 셰이프 쿼리의 결과를 강조 표시 합니다.



### <a name="object-placement-solver"></a>개체 배치 해 찾기

개체 배치 쿼리를 사용 하 여 실제 방에 있는 이상적인 위치를 식별 하 여 개체를 배치할 수 있습니다. 개체 규칙 및 제약 조건이 지정 된 경우 해 찾기가 최적 위치를 찾습니다. 또한 **Solver_RemoveObject** 또는 **Solver_RemoveAllObjects** 호출을 통해 개체가 제거 될 때까지 개체 쿼리를 유지 하 여 제한 된 다중 개체 배치를 허용 합니다.

개체 배치 쿼리는 매개 변수가 있는 배치 유형, 규칙 목록 및 제약 조건 목록의 세 부분으로 구성 됩니다. 쿼리를 실행 하려면 다음 API를 사용 합니다.




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
이 함수는 개체 이름, 배치 정의 및 규칙 및 제약 조건 목록을 사용 합니다. 래퍼 C# 는 규칙 및 제약 조건 생성을 용이 하 게 하는 생성 도우미 함수를 제공 합니다. 배치 정의에는 쿼리 유형 즉, 다음 중 하나를 포함 합니다.




```
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

각 배치 형식에는 해당 형식에 고유한 매개 변수 집합이 있습니다. **Objectplacementdefinition** 구조에는 이러한 정의를 만들기 위한 정적 도우미 함수 집합이 포함 되어 있습니다. 예를 들어 개체를 바닥에 배치할 위치를 찾으려면 다음 함수를 사용할 수 있습니다. 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

배치 유형 외에도 규칙 및 제약 조건 집합을 제공할 수 있습니다. 규칙을 위반할 수 없습니다. 그러면 형식 및 규칙을 충족 하는 가능한 배치 위치가 제약 조건 집합에 대해 최적화 되어 최적의 배치 위치를 선택할 수 있습니다. 제공 된 정적 생성 함수를 통해 각 규칙 및 제약 조건을 만들 수 있습니다. 아래에는 규칙 및 제약 조건 생성 함수 예제가 나와 있습니다.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

아래의 개체 배치 쿼리는 이전에 배치 된 다른 개체와 대화방의 가운데 근처에서 절반 측정기 큐브를 표면의 가장자리에 배치 하는 위치를 찾고 있습니다.




```
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

성공 하면 배치 위치, 차원 및 방향을 포함 하는 **Objectplacementresult** 구조가 반환 됩니다. 또한 배치가 배치 된 개체의 내부 목록에 추가 됩니다. 이후 배치 쿼리에서는이 개체를 고려 합니다. Unity 샘플의 **LevelSolver.cs** 파일에는 더 많은 예제 쿼리가 포함 되어 있습니다.

![파란색 상자는 "카메라 위치에서 멀리" 규칙을 사용 하 여 바닥 쿼리의 세 위치에서 발생 한 결과를 보여 줍니다.](images/away-from-camera-position-500px.png)

파란색 상자는 "카메라 위치에서 멀리" 규칙을 사용 하 여 바닥 쿼리의 세 위치에서 발생 한 결과를 보여 줍니다.


**팁**
* 수준 또는 응용 프로그램 시나리오에 필요한 여러 개체의 배치 위치를 해결 하는 경우 먼저 필수적인 개체와 대량 개체를 해결 하 여 공간을 찾을 수 있는 확률을 최대화 합니다.
* 배치 순서는 중요 합니다. 개체 배치를 찾을 수 없는 경우 제한 된 구성으로 시도 합니다. 여러 방 구성에서 기능을 지원 하려면 대체 (fallback) 구성 집합이 있어야 합니다.

### <a name="ray-casting"></a>광선 캐스팅

세 가지 기본 쿼리 외에도, 광선 캐스팅 인터페이스를 사용 하 여 태그가 지정 된 서피스 형식을 검색 하 고, 방을 검색 하 고 완료 한 후에 사용자 지정 watertight playspace 메시를 복사할 수 있습니다. 레이블은 다음과 같은 표면에 대해 내부적으로 생성 됩니다. 바닥, 천장 및 벽입니다. **PlayspaceRaycast** 함수는 광선이 알려진 표면과 충돌 하는 경우를 반환 하 고, 해당 하는 경우에는 **RaycastResult**형식으로 해당 화면에 대 한 정보를 반환 합니다. 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

내부적으로 raycast는 playspace의 계산 된 8cm 제곱 voxel 표현에 대해 계산 됩니다. 각 voxel에는 처리 된 토폴로지 데이터 (surfels 라고도 함)를 포함 하는 surface 요소 집합이 포함 되어 있습니다. 교차 된 voxel 셀에 포함 된 surfels는 토폴로지 정보를 조회 하는 데 사용 되는 가장 일치 하는 항목과 비교 됩니다. 이 토폴로지 데이터에는 교차 된 표면의 노출 영역 뿐만 아니라 **SurfaceTypes** 열거형 형식으로 반환 되는 레이블 지정이 포함 됩니다.

Unity 샘플에서 커서는 각 프레임을 비춥니다. 첫째, Unity의 colliders에 대해 둘째, 모듈의 세계 표현 이해 마지막으로 UI 요소를 기준으로 합니다. 이 응용 프로그램에서 UI는 우선 순위, 이해 결과 및 마지막으로 Unity의 colliders를 가져옵니다. **SurfaceType** 은 커서 옆에 텍스트로 보고 됩니다.

![바닥과의 교차점을 보고 하는 raycast 결과](images/raycast-result-500px.jpg)

바닥과의 교차점을 보고 하는 raycast 결과


## <a name="get-the-code"></a>코드 다운로드

오픈 소스 코드는 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)에서 사용할 수 있습니다. 프로젝트에서 코드를 사용 하는 경우 [HoloLens 개발자 포럼](https://forums.hololens.com/) 을 통해 알려주세요. 작업을 확인할 때까지 기다릴 수 없습니다!

## <a name="about-the-author"></a>작성자 정보

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b> 는 인큐베이션부터 경험 개발까지 이전 며칠 이후 HoloLens에 대해 작업 한 소프트웨어 엔지니어링 리드입니다. HoloLens 이전에는 다양 한 플랫폼 및 게임의 Xbox Kinect 및 게임 업계에서 작업 했습니다. Jeff는 경고음이 들리고 현란한 광원을 사용 하는 로봇, 그래픽 및 사물에 대 한 열정적인입니다. 그는 새로운 작업을 배우고 소프트웨어, 하드웨어, 특히 두 부분이 교차 하는 공간에서 작업 하는 것을 활용할.</td>
</tr>
</table>



## <a name="see-also"></a>참고 항목
* [공간 매핑](spatial-mapping.md)
* [장면 이해](scene-understanding.md)
* [실내 스캔 시각화](room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo 스튜디오: HoloLens 개발 frontline의 단원](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
