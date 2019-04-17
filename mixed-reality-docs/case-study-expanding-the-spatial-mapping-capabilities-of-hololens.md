---
title: 사례 연구-HoloLens의 공간 매핑 기능을 확장
description: Microsoft HoloLens 대 한 첫 번째 응용 프로그램을 만들 때 즉시 공간 매핑의 경계 장치에 푸시할 수 있습니다는 얼마나만 볼 수 있었습니다.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 공간 매핑
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602835"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a>사례 연구-HoloLens의 공간 매핑 기능을 확장

Microsoft HoloLens 대 한 첫 번째 응용 프로그램을 만들 때 즉시 공간 매핑의 경계 장치에 푸시할 수 있습니다는 얼마나만 볼 수 있었습니다. Microsoft Studios 소프트웨어 엔지니어로, Jeff Evertt에서 사용자의 실제 환경에서 홀로그램 배치 되는 방법을 보다 자세히 제어 해야 하는 새로운 기술 된 개발 하는 방법을 설명 합니다.

## <a name="watch-the-video"></a>비디오를 시청 하세요.

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a>공간 매핑 초과

작업 하는 동안 [조각](https://www.microsoft.com/p/fragments/9nblggh5ggm8) 하 고 [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), 두는 실제에서 홀로그램 절차 배치를 할 때 했던 더 높은 수준 알게 HoloLens에 대 한 첫 번째 게임, 사용자의 환경에 대 한 이해를 제공 합니다. 각 게임 자체 특정 배치 요구 했습니다. 조각에서 예를 들어, 하려는 다양 한 표면 구분할 수 있으려면-바닥 또는 테이블과 같은-단서 관련 위치에 배치 합니다. 또한는 life-size holographic 문자 수에 소파 등의 자를 화면을 식별할 수 하려고 합니다. Young Conker Conker 및가 상대방에 게 플랫폼으로 플레이어의 방에 발생된 화면을 사용할 수 있게 되기를 원했습니다.

[Asobo Studios](http://www.asobostudio.com/index.html), 이러한 게임 개발 파트너는이 문제를 할애 직면 만들어지고 HoloLens의 공간 매핑 기능을 확장 하는 기술입니다. 이 사용 하 고 수 있었습니다 플레이어의 대화방을 분석 벽, 테이블의 자 바닥 등과 같은 화면을 식별 합니다. 또한 에게도 holographic 개체에 대 한 최상의 배치를 결정 하는 제약 조건의 집합에 대해 최적화할 수 있습니다.

## <a name="the-spatial-understanding-code"></a>코드 공간 이해

Asobo의 원본 코드를 수행 하 고이 기술을 캡슐화 하는 라이브러리를 만들었습니다. Microsoft Asobo 이제이 코드 오픈 소스 및에서 사용할 수 있는 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) 자체 프로젝트에서 사용할 수 있습니다. 모든 소스 코드 요구 사항에 맞게 사용자 지정 하 고 커뮤니티에 향상 된 기능을 공유할 수 있도록 포함 됩니다. 에 대 한 코드는 C++ solver UWP DLL로 래핑 되었으며 사용 하 여 Unity에 노출 되는 [드롭인 prefab MixedRealityToolkit 내에 포함 된](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)합니다.

많은 유용한 쿼리 최대값 또는 현장에서 큰 공간 개체를 배치, 보관, 문자 및 다른 이해 공간 쿼리 수많은 위치를 식별 합니다. 벽에 빈 공간을 찾을 수 있도록 Unity 샘플에 포함 되어 있습니다.

HoloLens를 제공한 공간 매핑 솔루션은 문제 공간 전체의 요구에 맞게 충분히 제네릭으로 되도록 설계 되었지만, 공간 이해 모듈을 두 특정 게임의 요구를 지원 하도록 빌드 되었습니다. 따라서 해당 솔루션은 특정 프로세스 및 가정 집합이 구성 되어 있습니다.
* **고정 크기 playspace**: 사용자는 init 호출의 최대 playspace 크기를 지정합니다.
* **일회성 검색 프로세스가**: 프로세스에 필요한 별도 playspace 정의 해결은 사용자가 위치 하는 단계를 검색 합니다. 쿼리 함수 검색이 종료 된 후까지 작동 하지 않습니다.
* **사용자 구동 playspace "그리기"**: 검색 단계에서는 사용자 이동 하 고 효과적으로 포함 해야 하는 영역을 그리기는 playspace 주위 찾습니다. 생성 된 메시 반드시이 단계에서 사용자에 게 피드백을 제공 합니다.
* **실내 집 이나 사무실 설치**: 쿼리 함수를 평면 표면 및 직각으로 벽 바탕으로 설계 되었습니다. 소프트 제한 됩니다. 그러나 검색 단계에서는 기본 축 분석을 주 및 부 축 따라 메시 공간 분할을 최적화 하기 위해 완료 됩니다.

### <a name="room-scanning-process"></a>대화방 검색 프로세스

가장 먼저 수행할 작업 사용 가능한 모든 화면에 공간 검색은 공간 이해 모듈을 로드 하는 경우-floor, ceiling, 벽 등-식별 되 고 레이블이 지정 됩니다. 검색 과정에서 분야를 살펴보면 사용자 공간 및 "그리기 ' 검색에 포함 되어야 하는 영역입니다.

이 단계 중에 나타나는 메시 대화방 부분 검색 됨을 알 수 있게 해 주는 시각적 피드백을 중요 한 부분입니다. 공간 이해 모듈에 대 한 DLL을 playspace 크기가 8 cm voxel 큐브에 포함 된 표를 내부적으로 저장합니다. 검색의 시작 부분에서 하는 동안 대화방의 축을 확인 하려면 기본 구성 요소 분석을 완료 됩니다. 내부적으로 이러한 축 정렬 해당 voxel 공간을 저장 합니다. 메시를 isosurface voxel 볼륨에서 추출 하 여 약 1 초 마다 생성 됩니다.

![녹색에서 메시 공간 흰색에서 메시 매핑 및 playspace 이해](images/spatial-mapping-500px.png)

녹색에서 메시 공간 흰색에서 메시 매핑 및 playspace 이해



포함된 된 SpatialUnderstanding.cs 파일 검색 단계 프로세스를 관리합니다. 다음 함수를 호출합니다.
* **SpatialUnderstanding_Init**: 시작할 때 한 번 호출 합니다.
* **GeneratePlayspace_InitScan**: 검색 단계를 시작 해야 함을 나타냅니다.
* **GeneratePlayspace_UpdateScan_DynamicScan**: 각 프레임 업데이트 검색 프로세스를 호출 합니다. 카메라 위치 및 방향에 전달 하 고 위에서 설명한 playspace 그리기 프로세스에 사용 됩니다.
* **GeneratePlayspace_RequestFinish**: playspace 완료 하기 위해 호출 됩니다. 이 정의 하 고는 playspace 잠금 영역 "그린" 검사 단계 중에 사용 됩니다. 응용 프로그램의 검색 단계 뿐만 아니라 쿼리 사용자에 게 피드백을 제공 하기 위한 사용자 지정 메시 중 통계를 쿼리할 수 있습니다.
* **Import_UnderstandingMesh**: 를 검색 하는 동안 합니다 **SpatialUnderstandingCustomMesh** 동작 모듈에서 제공 하 고 이해 prefab에 배치 프로세스에서 생성 하는 사용자 지정 메시를 정기적으로 쿼리하여 됩니다. 또한 이렇게 한 번 더 검색 종료 된 후 합니다.

검사 흐름을 기반으로 합니다 **SpatialUnderstanding** 동작 호출 **InitScan**, 다음 **UpdateScan** 각 프레임입니다. 사용자 수를 호출 하는 airtap 통계 쿼리에 적절 한 검사를 보고할 때 **RequestFinish** 검사 단계의 끝을 나타냅니다. **UpdateScan** 반환 될 때까지 호출할 계속 값 DLL 처리 완료 되었음을 나타냅니다.

## <a name="the-queries"></a>쿼리

검색이 완료 되 면 세 가지 유형의 쿼리 인터페이스에 액세스할 수 있습니다.
* **토폴로지 쿼리**: 이들은 스캔 한 대화방의 토폴로지를 기반으로 하는 빠른 쿼리입니다.
* **쿼리 셰이프**: 이러한 사용자 지정 셰이프를 정의 하는 좋은 일치 하는 가로 화면을 찾으려면 토폴로지 쿼리의 결과 활용 합니다.
* **배치 쿼리 개체**: 이 복잡 한 쿼리 규칙 집합과 개체에 대 한 제약 조건에 따라 가장 적합된 한 위치를 찾습니다는입니다.

세 가지 기본 쿼리 외에도 태그가 지정 된 화면 형식을 검색 하려면 사용할 수 있는 플레이어가 인터페이스 이며 지정 watertight 방 메시를 복사할 수 있습니다.

### <a name="topology-queries"></a>쿼리 토폴로지

DLL 내에서 토폴로지 manager 환경의 레이블 지정을 처리 합니다. 위에서 설명 했 듯이 surfels voxel 볼륨 내에서 포함 된 내에 저장 된 데이터를 많이 합니다. 또한 합니다 **PlaySpaceInfos** 구조 world 맞춤 (자세한 내용은 아래 참조), floor, ceiling 높이 등을 playspace에 대 한 정보를 저장 하는 합니다.

추론은 floor, ceiling, 및 벽을 결정 하는 데 사용 됩니다. 예를 들어, 1의 m2 노출 영역 보다 큰를 사용 하 여 가장 크고 가장 낮은 가로 화면 바닥을 간주 됩니다. 검색 프로세스 중 카메라 경로에서이 프로세스는 참고 합니다.

토폴로지 관리자에 의해 노출 되는 쿼리의 하위 집합만 아웃 DLL을 통해 노출 됩니다. 노출 된 토폴로지 쿼리는 다음과 같습니다.
* QueryTopology_FindPositionsOnWalls
* QueryTopology_FindLargePositionsOnWalls
* QueryTopology_FindLargestWall
* QueryTopology_FindPositionsOnFloor
* QueryTopology_FindLargestPositionsOnFloor
* QueryTopology_FindPositionsSittable

각 쿼리 매개 변수, 쿼리 형식에 특정 집합을에 있습니다. 다음 예제에서는 사용자의 최소 높이 및 원하는 볼륨, floor, 및 최소한의 여유 공간 볼륨 앞에 위의 최소 배치 높이 너비를 지정합니다. 모든 측정 미터의 경우




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

이 쿼리는 각각의 미리 할당 된 배열을 받아 **TopologyResult** 구조입니다. 합니다 **locationCount** 매개 변수 전달 된 배열의 길이 지정 합니다. 반환 값은 반환 된 위치 수를 보고합니다. 이 수는 해당 전달 기능에 보다 큰 **locationCount** 매개 변수입니다.

합니다 **TopologyResult** 반환 된 볼륨, 연결 방향 (즉, 표준) 및 검색 공간의 크기의 가운데 위치를 포함 합니다.




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

Unity 샘플에서, 가상 UI 패널에서 단추에 이러한 쿼리는 각 연결 됩니다. 하드 샘플의 적절 한 값으로이 쿼리는 각각에 대 한 매개 변수를 코드입니다. 참조 *SpaceVisualizer.cs* 더 많은 예제에 대 한 샘플 코드입니다.

### <a name="shape-queries"></a>셰이프 쿼리

셰이프 분석기 DLL 내에서 (**ShapeAnalyzer_W**) 사용자가 정의한 사용자 지정 셰이프를 대조할 토폴로지 분석기를 사용 합니다. Unity 샘플 미리 정의 된 집합이 쿼리 메뉴 셰이프 탭에 표시 되는 셰이프.

셰이프 분석만 가로 화면에서 작동 하는 참고 합니다. 예를 들어, 소파, 플랫 사용자 화면과 플랫 맨 뒤로 소파에 의해 정의 됩니다. Shape 쿼리의 정렬 및 연결 된 두 개의 화면을 사용 하 여 특정 크기, 높이 및 측면 범위의 두 화면을 찾습니다. Api 용어를 사용 하 소파 뒷면의 위쪽과 couch 사용자는 셰이프 구성 요소 및 요구 사항은 맞춤 셰이프 구성 요소 제한이 있습니다.

Unity 예제에 정의 하는 예제 쿼리 (**ShapeDefinition.cs**), "sittable" 개체는 다음과 같습니다.




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

Shape 쿼리의 각 구성 요소 제약 조건 집합 및 구성 요소 간의 종속성을 나열 하는 셰이프 제약 조건의 집합을 사용 하 여 각 셰이프 구성 요소 집합으로 정의 됩니다. 이 예제 (구성 요소가 하나만 하므로)는 단일 구성 요소 정의 및 구성 요소 간에 모양 제약 없이 세 가지 제약 조건을 포함 합니다.

반면, 소파 모양을 두 셰이프 구성 요소와 네 개의 셰이프 제약 조건에 있습니다. 구성 요소는 (0과 1이 예제의) 사용자의 구성 요소 목록에서 해당 인덱스로 식별 되는 참고 합니다.




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

래퍼 함수는 사용자 지정 셰이프 정의 쉽게 만들기 위한 Unity 모듈에서 제공 됩니다. 구성 요소 및 셰이프 제약 조건의 전체 목록은에서 찾을 수 있습니다 **SpatialUnderstandingDll.cs** 내 합니다 **ShapeComponentConstraint** 하며 **ShapeConstraint** 구조입니다.

![파란색 사각형 chair shape 쿼리의 결과 강조 표시합니다.](images/chair-shape-query-500px.png)

파란색 사각형 chair shape 쿼리의 결과 강조 표시합니다.



### <a name="object-placement-solver"></a>개체 배치 해 찾기

개체를 배치 하는 물리적 공간에 이상적인 위치를 식별할 수 개체 배치 쿼리를 사용할 수 있습니다. 해 찾기에서 지정 된 개체 규칙 및 제약 조건 가장 적합된 한 위치를 찾습니다. 개체 쿼리 개체를 사용 하 여 제거 될 때까지 유지 하는 또한 **Solver_RemoveObject** 하거나 **Solver_RemoveAllObjects** 호출을 허용 다중 개체 배치를 제한 합니다.

개체 배치 쿼리의 세 부분으로 구성 됩니다: 매개 변수, 규칙의 목록 및 제약 조건 목록을 사용 하 여 배치 형식입니다. 쿼리를 실행 하려면 다음 API를 사용 합니다.




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
이 함수는 개체 이름, 배치 정 및 규칙 및 제약 조건 목록을 사용합니다. C# 래퍼 생성 규칙 및 제약 조건 생성을 간편 하 게 도우미 기능을 제공 합니다. 배치 정의 쿼리 형식이 포함-다음 중 하나 이므로:




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

매개 변수 형식에 고유 집합에 각 배치 형식 합니다 **ObjectPlacementDefinition** 구조 이러한 정의 만들기 위한 정적 도우미 함수 집합을 포함 합니다. 예를 들어, 현장에서 개체를 삽입할 수 있는 위치를 찾으려면 다음 함수를 사용할 수 있습니다. 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

배치 형식 외에도 제약 조건 및 규칙 집합을 제공할 수 있습니다. 규칙을 위반할 수 없습니다. 형식 및 규칙을 충족 하는 배치 하는 위치는 다음 최적의 배치 위치를 선택 하는 제약 조건의 집합에 대해 최적화 됩니다. 제공 된 정적 생성 함수에 의해 각 제약 조건 및 규칙을 만들 수 있습니다. 규칙 및 제약 조건 생성 함수 예제는 아래 제공 됩니다.




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

아래 개체 배치 쿼리는 절반 미터 큐브는 화면의 가장자리에 배치 하는, 다른에서 이전에 개체 배치 대화방의 가운데 근처 위치를 찾고 있습니다.




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

성공한 경우는 **ObjectPlacementResult** 배치 위치, 크기 및 방향을 포함 구조에 반환 됩니다. 또한 배치는 DLL의 내부 목록을 배치 하는 개체에 추가 됩니다. 후속 배치 쿼리를이 개체를 고려 됩니다. 합니다 **LevelSolver.cs** Unity 샘플에서 파일에 더 많은 예제 쿼리에 포함 되어 있습니다.

![파랑 상자로 "자리 비움 카메라 위치"에서 규칙을 사용 하 여 세 곳에서 Floor 쿼리에서 결과 보여 줍니다.](images/away-from-camera-position-500px.png)

파랑 상자로 "자리 비움 카메라 위치"에서 규칙을 사용 하 여 세 곳에서 Floor 쿼리에서 결과 보여 줍니다.


**팁:**
* 수준 또는 응용 프로그램 시나리오에 필요한 여러 개체의 배치 위치에 대 한 해결 하는 경우 먼저 공간을 찾을 수 있는 가능성을 최대화 하기 위해 필수적인 및 큰 개체를 해결 합니다.
* 배치 순서가 중요 합니다. 개체 배치를 찾을 수 없는 경우에 덜 제한적된 구성 해 보십시오. 대체 (fallback) 구성 집합을는 것이 많은 공간 구성에서 기능을 지 원하는 데 중요 합니다.

### <a name="ray-casting"></a>광선 캐스팅

세 가지 기본 쿼리 외에도 광선 캐스팅 인터페이스를 노출 태그가 지정 된 형식을 검색 하려면 사용할 수 및 사용자 지정 watertight playspace 메시를 복사할 수 있습니다 아웃 대화방 검색 및 종료 된 후 레이블은 내부적으로 생성 화면 같은 합니다 floor, ceiling, 및 벽 합니다. **PlayspaceRaycast** 함수 광선을 그린 받고 광선과 알려진된 화면을 사용 하 여 충돌 하는 경우 및 그렇다면 반환 형식으로 해당 화면에 대 한 정보를 **RaycastResult**합니다. 


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

내부적으로 raycast는 playspace의 3 제곱 계산된 8 cm voxel 표현에 대해 계산 됩니다. 각 voxel 처리 토폴로지 데이터 (surfels이 라고도 함)를 사용 하 여 화면 요소의 집합을 포함합니다. 교차 voxel 셀 내에 포함 된 surfels 비교한 후 가장 일치 하는 토폴로지 정보를 찾는 데 사용 됩니다. 이 토폴로지 데이터가 레이블을의 형태로 반환 합니다 **SurfaceTypes** 열거형에서 교차 된 노출의 노출 영역 뿐만 아니라 합니다.

Unity 샘플에서는 커서 각 프레임을 광선을 캐스팅합니다. Unity의 colliders;에 대해 먼저 둘째, 이해 모듈의 세계 표현을;에 대 한 UI 요소에 대해 마지막으로 합니다. 이 응용 프로그램 UI는 우선 순위를 이해 하면 및 마지막으로, Unity의 colliders을 가져옵니다. 합니다 **SurfaceType** 커서 옆에 있는 텍스트로 보고 됩니다.

![Raycast 결과 교집합 바닥을 보고 합니다.](images/raycast-result-500px.jpg)

Raycast 결과 교집합 바닥을 보고 합니다.


## <a name="get-the-code"></a>코드 다운로드

오픈 소스 코드는 사용할 수 있습니다 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)합니다. 에 알려 주세요 합니다 [HoloLens 개발자 포럼](https://forums.hololens.com/) 프로젝트에서 코드를 사용 하는 경우. 이 사용 하 여 확인할 주십시오!

## <a name="about-the-author"></a>저자 소개

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <b>Jeff Evertt</b> 가 개발 환경에 인큐베이션에서 초기 시절 HoloLens에서 작업 하는 소프트웨어 엔지니어링 잠재 고객. HoloLens, 전에 Xbox Kinect 및 다양 한 플랫폼 및 게임에서 게임 업계는 것이 근무 합니다. Jeff는 로봇 공학, 그래픽 및 경고음을 이동 하는 화려한 광원을 사용 하 여 작업 하는 데 열정입니다. 새로운 것을 배우고 작업 소프트웨어, 하드웨어 및 두 교차 하는 공간에서 특히 즐깁니다.</td>
</tr>
</table>



## <a name="see-also"></a>참조
* [공간 매핑](spatial-mapping.md)
* [공간 매핑 디자인](spatial-mapping-design.md)
* [대화방 검색 시각화](room-scan-visualization.md)
* [MixedRealityToolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [Asobo Studio: HoloLens 개발 제일선 교훈](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
