---
title: DirectX의 좌표계
description: Windows Mixed Reality 공간 로케이터, 참조 프레임, 공간 앵커 및 좌표계를 사용 하는 방법, SpatialStage를 사용 하는 방법, 추적 손실을 처리 하는 방법, 저장 하 고 앵커를 로드 하는 방법 및 안정화를 이미지 수행 하는 방법에 설명 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 코드, 이미지 안정화, 공간 앵커, 앵커 저장소 공간, 추적 손실, 연습 샘플 혼합 현실을, 공간 로케이터 공간 참조 프레임, 공간 좌표계, 공간 단계
ms.openlocfilehash: 5a48e0a829ba8647718e28ec20760d8a764b13fe
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628980"
---
# <a name="coordinate-systems-in-directx"></a>DirectX의 좌표계

[좌표계](coordinate-systems.md) Windows Mixed Reality Api에서 제공 하는 공간 이해에 대 한 기초를 형성 합니다.

오늘날의 장착 VR 또는 단일 회의실 VR 장치는 추적 된 공간에 하나의 기본 좌표계를 설정 합니다. Windows Mixed Reality 장치 HoloLens 대규모 정의 되지 않은 환경에서 사용할 수 있도록 설계 된 같은 장치를 검색 하 고 해당 환경에 대 한 사용자로 학습에서는 해결 합니다. 이렇게 하면 지속적으로 향상에 맞게 장치 사용자의 방 하지만 앱의 수명 간 관계 변경 되는 좌표계의 결과 대 한 정보입니다. Windows Mixed Reality 광범위 한 전 세계에 연결 된 참조 프레임 까지인 탐구 몰입 형 헤드셋에서 장치를 지원 합니다.

>[!NOTE]
>이 문서의 코드 조각 사용에 현재 방법을 보여 줍니다 C++/CX 대신 C + + 17 규격 C++/WinRT에 사용 되는 [ C++ holographic 프로젝트 템플릿을](creating-a-holographic-directx-project.md).  개념에 대 한 동일는 C++코드를 변환 해야 하지만 /WinRT 프로젝트입니다.

## <a name="spatial-coordinate-systems-in-windows"></a>Windows에서 공간 좌표계

Windows의 실제 좌표계에 대해 추론 하는 데 핵심 형식이 합니다 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>합니다. 이 형식의 인스턴스는 임의의 좌표 시스템을 나타내며 각각의 세부 정보를 알 수 없는 두 개의 좌표 시스템 간에 변환 하는 데 사용할 수 있는 변형 매트릭스를 가져오는 메서드를 제공 합니다.

점, 표면이, 또는 사용자의 환경 등의 볼륨으로 표시 하는 공간 정보를 반환 하는 메서드를 반환할 좌표에 대 한 가장 유용한 좌표계를 결정할 수 있도록 SpatialCoordinateSystem 매개 변수를 수락 합니다. 이러한 좌표에 대 한 단위 미터에서 항상 됩니다.

SpatialCoordinateSystem 장치의 위치를 표시 하는 것을 비롯 한 다른 좌표 시스템을 사용 하 여 동적 관계가 있습니다. 모든 시점에서 든 장치가 일부 좌표계 및 다른 것을 찾을 수 있습니다. 대부분의 좌표계 앱 기간 동안 이러한 찾을 수 없습니다를 처리할 준비가 되어 있어야 합니다.

응용 프로그램은 만들지 SpatialCoordinateSystems 직접-인식 Api를 통해 소비 대신 합니다. 인식 Api에서 좌표 시스템의 세 가지 기본 소스는에 설명 된 개념에 맵의 각 합니다 [좌표계](coordinate-systems.md) 페이지:
* 고정 참조 프레임을 가져오려면 만듭니다는 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> 현재에서 구입 하거나 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>합니다.
* 공간 앵커를 가져오려면 만듭니다는 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>합니다.
* 연결된 된 프레임의 참조를 가져오려면 만듭니다는 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>합니다.

이러한 개체를 반환한 좌표계 모두 사용 하 여 오른손 + 오른쪽에 y, + x 및 + z 이전 버전과 합니다. 양의 x 방향으로 왼쪽 또는 오른쪽의 손가락을 가리키고 고 양의 y 방향으로 컬링 양의 z-축 지점의 방향의 기억할 수 있습니다. 엄지가 가리키는 방향이 해당 좌표계에 대해 양의 z-축이 가리키는 방향입니다. 다음 그림은 이 두 좌표계를 보여 줍니다.

![왼쪽 및 오른쪽 좌표계](images/left-hand-right-hand.gif)<br>
*왼쪽 및 오른쪽 좌표계*

에 HoloLens의 위치를 기준으로 하는 SpatialCoordinateSystem 부트스트랩을 사용 합니다 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> 아래 섹션에 설명 된 대로 중 하나는 연결 또는 고정 참조 프레임을 만들 클래스입니다.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>홀로그램 공간 단계를 사용 하 여 전 세계에 배치

정적을 사용 하 여 좌표계 불투명 Windows Mixed Reality 몰입 형 헤드셋에는 액세스할 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> 속성입니다. 이 API는 모바일, 플레이어 경우 주위를 탐색 하기 위한 좌표계, 모바일 또는 플레이어 장착 되어 있는지 여부에 대 한 정보, 안전 영역 경계를 제공 하 고 헤드셋 방향성 인지 여부를 나타냅니다. 공간 스테이지에 대 한 업데이트에 대 한 이벤트 처리기 이기도합니다.

먼저, 공간 스테이지를 가져오기 하 고이에 대 한 업데이트 구독: 

에 대 한 코드 **공간 단계 초기화**

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

OnCurrentChanged 메서드에서 앱 공간 스테이지를 검사 하 고 플레이어 경험을 적절 하 게 업데이트 해야 합니다. 이 예에서 시각화의 단계 경계 뿐만 아니라 사용자 및 뷰의 스테이지의 범위 및 범위 이동 속성에 의해 지정 된 시작 위치를 제공 합니다. 또한로 대체할 것 고유한 고정 좌표계에 단계를 제공할 수 없는 경우.


에 대 한 코드 **공간 단계 업데이트**

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

시계 방향 순서로 단계 경계를 정의 하는 꼭 짓 점 집합이 제공 됩니다. Windows Mixed Reality 셸 사용자 않으면 가까워지면 경계에 펜스를을 그립니다. 고유한 목적 움직일 수 영역 triangularize 하고자 할 수 있습니다. 다음 알고리즘 triangularize 스테이지를 사용할 수 있습니다.


에 대 한 코드 **공간 단계 triangularization**

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>홀로그램 고정 참조 프레임을 사용 하 여 전 세계에 배치

합니다 [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) 프레임을 나타내는 클래스를 참조 하는 [움직이지 않고](coordinate-systems.md#stationary-frame-of-reference) 이동 사용자로 사용자의 환경을 기준으로 합니다. 이 참조 프레임 장치 거의 안정적인 유지 좌표 우선 순위를 지정 합니다. SpatialStationaryFrameOfReference의 주요 용도 중 하나를 홀로그램을 렌더링할 때 렌더링 엔진 내에서 기본 세계 좌표 시스템을 프록시로 경우

SpatialStationaryFrameOfReference을 사용 합니다 [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) 클래스 및 호출 [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)합니다.

Windows Holographic 앱 템플릿 코드:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* 고정 참조 프레임은 전체 공간을 기준으로 가장 적합된 한 위치를 제공 하도록 설계 되었습니다. 해당 참조 프레임 내에서 개별 위치 약간 드리프트 수 있습니다. 일반적인 장치 환경에 대 한 자세한 정보를 학습 하는 경우입니다.
* 개별 홀로그램 정확히 배치가 필요한 경우 실제에서 위치로 개별 홀로그램에 앵커를 SpatialAnchor 쓰일 수-예를 들어, 지점 사용자는 특별 한 관심을 나타냅니다. 앵커 위치 드리프트 하지 마십시오 있지만 수정할 수 있습니다. 앵커 수정 사항이 발생 한 후 다음 프레임부터 수정 된 위치가 사용 됩니다.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>홀로그램 공간 앵커를 사용 하 여 전 세계에 배치

[공간 앵커](coordinate-systems.md#spatial-anchors) 홀로그램 실제 환경에서 특정 위치에 배치 하는 좋은 방법, 시스템을 사용 하 여 앵커를 확인 합니다. 움직이지 않습니다 시간이 지남에 따라 합니다. 이 항목에서는 앵커 데이터로 작업 하는 방법과 만들고 앵커를 사용 하는 방법을 설명 합니다.

모든 위치 및 원하는 SpatialCoordinateSystem 내 방향에는 SpatialAnchor를 만들 수 있습니다. 장치 지금은 해당 좌표계를 찾을 수 있어야 하 고 시스템 한계 공간 앵커에 도달 하지 해야 합니다.

정의 되 면 초기 위치로의 방향을 확인 하 고 정확한 위치를 유지 하는 SpatialAnchor의 좌표계 지속적으로 조정 합니다. 그런 다음 홀로그램 고정에 나타나는 정확한 위치에 사용자의 환경을 렌더링할이 SpatialAnchor를 사용할 수 있습니다.

앵커 장소에 보관 되는 조정 작업의 효과 앵커 증가에서 거리도 확대 됩니다. 따라서 해당 앵커 원점에서 두 개에 대 한 3 미터는 기준으로 콘텐츠를 렌더링 하지 마십시오.

합니다 [coordinatesystem입니다](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) 속성 장치 앵커의 정확한 위치를 조정 하는 경우 적용할 감속/가속을 앵커에 상대적인 콘텐츠를 배치할 수 있도록 하는 좌표계를 가져옵니다.

사용 합니다 [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) 속성과 해당 [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) 직접 이러한 조정을 관리 하는 이벤트입니다.

### <a name="persist-and-share-spatial-anchors"></a>지속 및 공유 공간 앵커

사용 하 여 로컬로 SpatialAnchor를 유지할 수 있습니다 합니다 [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) 클래스 및 그런 다음 동일한 HoloLens 장치에 대 한 이후 앱 세션에 다시 가져옵니다.

사용 하 여 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a>, 앱 여러 HoloLens, iOS 및 Android 장치에서 찾을 수 있는 로컬 SpatialAnchor에서 견고한 클라우드 앵커를 만들 수 있습니다.  일반적인 공간 앵커를 여러 장치를 공유 각 사용자는 동일한 실제 위치에 해당 앵커에 상대적인 렌더링 된 콘텐츠를 볼 수입니다.  따라서 실시간 공유 환경.

사용할 수도 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a> HoloLens, iOS 및 Android 장치에서 비동기 홀로그램 지 속성에 대 한 합니다.  견고한 클라우드 공간 앵커를 공유 하 여 여러 장치 관찰할 수 있습니다 동일한 지속형된 홀로그램 시간이 지남에 따라 해당 장치를 동시에 함께 있는 경우에 합니다.

5 분을 사용해으로 시작 하려면 HoloLens 앱에서 공유 환경을 구축 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">공간 앵커 HoloLens Azure 빠른 시작</a>합니다.

Azure 공간 앵커를 사용 하 여 실행을 했으면 할 수 있습니다 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens에 앵커를 찾아서 만들</a>합니다.  연습에 사용할 수 있는 <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 및 iOS</a> 도 모든 장치에서 동일한 앵커를 공유할 수 있도록 합니다.

### <a name="create-spatialanchors-for-holographic-content"></a>SpatialAnchors holographic 콘텐츠 만들기

이 코드 샘플은 Windows Holographic 수정한 앱 템플릿을 만들려는 경우 앵커를 **누름** 제스처 검색 됩니다. 다음 렌더링 단계 동안 큐브에 앵커에 둡니다.

여러 앵커는 도우미 클래스에서 지원 되므로이 코드 샘플을 사용 하 여 원하는 만큼 많은 큐브를 배치할 수 있습니다!

앵커에 대 한 Id의 앱에서 제어 하는 것을 참고 합니다. 이 예제에서는 순차적인 앵커 앱 컬렉션에 현재 저장 된 앵커의 수에 따라 있는 명명 체계를 만들었습니다.

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>비동기적으로 로드 및 캐시에 SpatialAnchorStore

이 지 속성을 처리 하는 데 도움이 되는 SampleSpatialAnchorHelper 클래스를 작성 하는 방법을 알아보겠습니다 포함:
* Platform:: string 키로 인덱싱된 앵커 메모리 내 컬렉션에 저장 합니다.
* 시스템의 SpatialAnchorStore에서 앵커를 로드는 별도로 로컬 메모리 내 컬렉션입니다.
* 이렇게 하려면 앱을 선택 하는 경우는 SpatialAnchorStore에 앵커의 로컬 메모리 내 컬렉션을 저장 합니다.

저장 하는 방법은 다음과 같습니다 [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) 개체를 [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)합니다.

클래스 시작 되 면는 SpatialAnchorStore 비동기적으로 요청. 시스템 I/O API 로드 앵커 스토어와이 API는 대 한 비동기 I/O는 비차단 있도록 해야 합니다.

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

앵커를 저장 하는 데 사용할 수 있는 SpatialAnchorStore이 주어 집니다. 이 IMapView SpatialAnchors 있는 데이터 값을 사용 하 여 문자열 키 값을 연결 하는 경우 샘플 코드를 저장이 도우미 클래스의 공용 함수를 통해 액세스할 수 있는 전용 클래스 멤버 변수입니다.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>저장 하 고 앵커 저장소 로드할 suspend/resume 이벤트를 후크 두는 것을 잊지 마세요.

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>콘텐츠 앵커 저장소에 저장

시스템 앱 일시 중단 하는 경우 앵커 저장소 공간에 앵커를 저장 해야 합니다. 수도 있습니다 다른 시간에 앵커 앵커 저장소에 저장 하려면 처럼 앱의 구현에 필요한 수 있습니다.

SpatialAnchorStore를 메모리에 앵커를 저장 하는 준비 된 경우 컬렉션을 반복할 수 있으며 각각을 저장해 보세요.

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>앱 다시 시작 될 때 앵커 저장소에서 콘텐츠를 로드

앱에 다시 시작 되 면, 언제 든 지 앱의 implementaiton에 필요한 메모리 내 데이터베이스를 직접 SpatialAnchors 앵커 상점의 IMapView에서 이동해 서는 AnchorStore에 이전에 저장 된 앵커를 복원할 수 있습니다.

앵커는 SpatialAnchorStore에서 복원 하려면 관심 고유한 메모리 내 컬렉션에는 각각을 복원 합니다.

메모리 내 데이터베이스를 직접 SpatialAnchors; 필요 만든 SpatialAnchors를 사용 하 여 문자열을 연결 하는 방법이 있습니다. 샘플 코드, 선택는 Windows::Foundation::Collections::IMap 앵커를 저장 하는 데는 쉽게는 SpatialAnchorStore에 동일한 키 및 데이터 값을 사용 합니다.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>복원 되는 앵커 되지 않을 수 있습니다 과정이 바로. 예를 들어, 완전히 다른 빌드 또는 별도 대화방에 앵커 수 있습니다. 사용 하기 전에 AnchorStore에서 검색 하는 앵커를 locatability 테스트 해야 합니다.

<br>

>[!NOTE]
>이 예제 코드는 AnchorStore에서 모든 앵커를 검색할 것입니다. 요구 사항은; 아닙니다. 앱 수와 마찬가지로 선택할 앵커의 특정 하위 집합 구현에 의미 있는 문자열 키 값을 사용 하 여 합니다.

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>필요한 경우 앵커 저장소 지우기

경우에 따라 응용 프로그램 상태를 지우고 새 데이터를 작성 해야 합니다. 사용 하 여 그 방법은 다음과 같습니다 합니다 [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)합니다.

도우미 클래스를 사용 하 거의 필요 없는를 래핑하는 선택을 취소 합니다. 도우미 클래스는 SpatialAnchorStore 인스턴스를 소유 해야를 지정 하는 샘플 구현에서는 이렇게 하려면 선택 합니다.

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>예: 앵커 좌표계와 관련 된 고정 참조 프레임 좌표계

앵커에 있고 이미 대부분의 다른 내용 사용 하는 SpatialStationaryReferenceFrame 앵커의 좌표계에서 관련 하려는 경우를 가정해 보십시오. 사용할 수 있습니다 [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) 고정 참조 프레임의 변환 앵커 좌표 시스템에서 가져오려면:

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

이 프로세스는 두 가지 방식에서에 유용 합니다.
1. 두 프레임을 참조 하는 경우 서로 기준으로 이해할 수 있습니다 알려줍니다 및;
2. 그렇다면 다른 좌표 시스템에서 직접 이동 하려면 변환을 제공 합니다.

이 정보를 사용 하 여 두 참조 프레임 사이의 개체 간의 공간 관계 이해를 해야합니다.

렌더링을 위해 해당 원래 참조 프레임 또는 앵커에 따라 개체를 그룹화 하 여 더 나은 결과 가져올 수 있습니다. 각 그룹에 대 한 별도 그리기 단계를 수행 합니다. 보기 행렬은 처음에 동일한 좌표 시스템을 사용 하 여 만든 모델 변환 사용 하 여 개체에 대 한 더 정확 합니다.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>장치에 연결 된 참조 프레임을 사용 하 여 홀로그램 만들기

홀로그램을 렌더링 하 고 싶을 때 가지는 [연결 된 상태로 남아](coordinate-systems.md#attached-frame-of-reference) 장치의 위치, 예를 들어 장치가 해당 방향을 결정할 수만 때 정보, 정보 메시지를 디버깅 패널 및 하지 해당 공간 내의 위치입니다. 이렇게 하려면 연결 된 프레임의 참조를 사용 합니다.

SpatialLocatorAttachedFrameOfReference 클래스 대신 실제 장치를 기준으로 좌표계를 정의 합니다. 이 프레임에 머리글을 고정된 참조 프레임을 만들 때 사용자 방향 가리킵니다 연결 된 사용자의 환경을 기준으로 에 모든 방향 참조가 프레임에서 사용자가 장치를 회전할 때에 해당 고정된 머리글을 기준으로 합니다.

HoloLens에 대 한 해당이 프레임의 좌표계의 원점이 위치한 사용자의 헤드의 회전의 중심에 위치로 헤드 회전을 받지 않습니다 있도록 합니다. 앱은 사용자 앞에 홀로그램 위치로이 점 기준으로 오프셋을 지정할 수 있습니다.

SpatialLocatorAttachedFrameOfReference를 가져오려면 SpatialLocator 클래스를 사용 하 고 CreateAttachedFrameOfReferenceAtCurrentHeading 호출 합니다.

전체 범위의 Windows Mixed Reality 장치에 적용 되도록이 note 합니다.

### <a name="use-a-reference-frame-attached-to-the-device"></a>장치에 연결 하는 참조 프레임을 사용 하 여

이 섹션에서는 장치에 연결 된 참조 프레임이이 API를 사용 하 여 사용 하도록 설정 하려면 Windows Holographic 앱 템플릿에서에서는 변경 내용에 대해 알아봅니다. 참고가 "연결된" 홀로그램 고정 또는 고정 된 홀로그램와 함께 작동 하 고 장치를 일시적으로 전 세계에서 해당 위치를 찾을 수 없는 경우에 사용 될 수 있습니다.

먼저는 SpatialStationaryFrameOfReference 대신 SpatialLocatorAttachedFrameOfReference 저장할 템플릿을 변경 했습니다.

**HolographicTagAlongSampleMain.h**:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

From **HolographicTagAlongSampleMain.cpp**:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

이제 업데이트를 사용 하는 동안 프레임 예측을 사용 하 여에서 가져오는 타임 스탬프에 좌표계 가져옵니다.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>공간 포인터 포즈를 가져오고 사용자의 게이즈를 수행 합니다.

사용자가 따라야 하는 예제 홀로그램 하겠습니다 [gaze](gaze.md), holographic 셸 사용자 게이즈를 따라 수 있는 방법을 비슷합니다. 이 위해 동일한 타임 스탬프는 SpatialPointerPose 활용 하려면 필요 합니다.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

이 SpatialPointerPose에 따라 홀로그램을 배치 하는 데 필요한 정보에는 [사용자의 현재 머리글](gaze-in-directx.md)합니다.

사용자와 쾌적의 이유로 시간 동안 발생 하는 위치 변경 완만 하 게 선형 보간을 ("lerp")을 사용 합니다. 이것이 더 편리 하 게 사용자 자신의 게이즈를 홀로그램 잠금 보다입니다. Lerping tag-along 홀로그램의 위치 수 있습니다. 이동; 빨라져 여를 홀로그램 안정화 이 빨라져 하는 것은 하지 않은, 경우 사용자는 어떤 일반적으로 간주 됩니다 육안 식별 되지 않는 사용자의 헤드 이동으로 인해 지터 홀로그램을 표시 됩니다.

From **StationaryQuadRenderer::PositionHologram**:

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>디버깅 패널의 경우 위치를 변경 하려면 쪽 해제 홀로그램 잠시 보기 데 방해가 되지 않습니다 있도록 선택할 수 있습니다. 수행할 수 있습니다 하는 방법의 예는 다음과 같습니다.

For **StationaryQuadRenderer::PositionHologram**:

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>카메라 면 홀로그램 회전

것은 홀로그램 쿼드;에 경우에 단순히 위치로 충분 하지 않습니다. 또한 사용자 면 개체를 회전 해야 했습니다. 참고가이 회전 세계 좌표 공간에서이 유형의 빌보드 사용자 환경의 일부를 유지 하려면 홀로그램 허용 하기 때문에 발생 합니다. 보기 공간 빌보드 아니므로 편안한 마음으로 홀로그램 표시 방향; 잠깁니다. 이 경우 왼쪽 및 오른쪽 뷰 행렬 스테레오 렌더링을 방해 하지 않도록 하는 뷰 공간의 빌보드 변환을 획득 하기 위해 사이 보간도 해야 합니다. 여기서 사용자 면 X 및 Z 축에서 회전 합니다.

From **StationaryQuadRenderer::Update**:

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>연결 된 홀로그램 렌더링

예를 들어에서는 렌더링 하도록 선택할 수도 SpatialLocatorAttachedReferenceFrame의 좌표계에서 홀로그램을 홀로그램에서는 위치입니다. (다른 좌표 시스템을 사용 하 여 렌더링을 결정 했을 경우 해야 해당 좌표계에 장치에 연결 된 참조 프레임의 좌표계에서 변환을 가져오려고 합니다.)

From **HolographicTagAlongSampleMain::Render**:

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

정말 간단하죠. 홀로그램은 이제 "추적" 2m 사용자 게이즈 방향 앞에 위치 합니다.

>[!NOTE]
>이 예제에는 또한 추가 콘텐츠 로드-StationaryQuadRenderer.cpp를 참조 하세요.

## <a name="handling-tracking-loss"></a>손실 추적 처리

장치를 찾을 수 없는 자체 세계에서 하는 경우 앱 "손실 추적"을 경험 했습니다. Windows Mixed Reality 앱은 이러한 위치 추적 시스템 중단을 처리할 수 있어야 합니다. 이러한 중단을 관찰할 수 있습니다, 그리고 및 기본 SpatialLocator LocatabilityChanged 이벤트를 사용 하 여 응답을 생성 합니다.

**AppMain::SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

필요에 따라 앱 LocatabilityChanged 이벤트를 받으면 동작을 변경할 수 있습니다. 예를 들어 PositionalTrackingInhibited 상태의 앱 수 정상 작업을 일시 중지 및 렌더링을 [tag-along 홀로그램](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) 는 경고 메시지를 표시 합니다.

이미 만들어진 LocatabilityChanged 처리기를 사용 하 여 Windows Holographic 앱 템플릿을 제공 됩니다. 기본적으로 위치 추적을 사용할 수 없는 경우 디버그 콘솔에서 경고를 표시 합니다. 앱에서 필요에 따라 응답을 제공 하 여이 처리기에 코드를 추가할 수 있습니다.

**AppMain.cpp:**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>공간 매핑

합니다 [공간 매핑](spatial-mapping-in-directx.md) Api를 사용 하면 화면 메시에 대 한 모델 변환을 가져오려면 좌표 시스템의 사용 합니다.

## <a name="see-also"></a>참조
* [좌표계](coordinate-systems.md)
* [공간 앵커](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [DirectX의 헤드 및 눈 응시](gaze-in-directx.md)
* [실습 및 DirectX에서 컨트롤러 동작](hands-and-motion-controllers-in-directx.md)
* [DirectX의 공간 매핑](spatial-mapping-in-directx.md)
