---
title: DirectX에서 시스템 좌표계
description: Windows Mixed Reality 공간 로케이터, 참조 프레임, 공간 앵커 및 좌표계를 사용 하는 방법, SpatialStage를 사용 하는 방법, 추적 손실을 처리 하는 방법, 앵커를 저장 및 로드 하는 방법 및 이미지 안정화를 수행 하는 방법을 설명 합니다.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 혼합 현실, 공간 로케이터, 공간 참조 프레임, 공간 좌표 시스템, 공간 스테이지, 샘플 코드, 이미지 안정화, 공간 앵커, 공간 앵커 저장소, 추적 손실, 연습
ms.openlocfilehash: 5a48e0a829ba8647718e28ec20760d8a764b13fe
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65628980"
---
# <a name="coordinate-systems-in-directx"></a>DirectX에서 시스템 좌표계

[좌표계](coordinate-systems.md) 는 Windows Mixed Reality api에서 제공 하는 공간 이해의 기반을 형성 합니다.

오늘날의 고정 된 VR 또는 단일 대화방 VR 장치는 추적 된 공간을 나타내는 하나의 기본 좌표계를 설정 합니다. Windows Mixed Reality 장치 (예: HoloLens)는 정의 되지 않은 많은 환경에서 사용 하도록 설계 되었으며, 장치는 사용자가 안내 하는 환경에 대 한 정보를 검색 하 고 학습 합니다. 이를 통해 장치는 사용자의 방에 대 한 정보를 지속적으로 개선 하는 데 적응 하지만 앱의 수명 주기를 통해 서로 관계를 변경 하는 좌표계를 생성 합니다. Windows Mixed Reality는 전 세계에 연결 된 참조 프레임을 통해 장착 된 모던 헤드셋에서 다양 한 장치를 지원 합니다.

>[!NOTE]
>이 문서의 코드 조각은 현재 [ C++ holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되 C++는 것 처럼 C + 17-so-far working 규격 C++/winrt 대신/cx 사용을 보여 줍니다.  개념은 C++/winrt 프로젝트와 동일 하지만 코드를 변환 해야 합니다.

## <a name="spatial-coordinate-systems-in-windows"></a>Windows의 공간 좌표계

Windows에서 실제 좌표계를 설명 하는 데 사용 되는 핵심 유형은 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>입니다. 이 형식의 인스턴스는 임의의 좌표계를 나타내며, 각에 대 한 세부 정보를 이해 하지 않고도 두 좌표계 간에 변환 하는 데 사용할 수 있는 변환 매트릭스를 가져오는 메서드를 제공 합니다.

사용자의 환경에서 요소, 광선 또는 볼륨으로 표시 되는 공간 정보를 반환 하는 메서드는 SpatialCoordinateSystem 매개 변수를 사용 하 여 이러한 좌표가 반환 될 때 가장 유용한 좌표계를 결정할 수 있습니다. 이러한 좌표의 단위는 항상 미터 단위입니다.

SpatialCoordinateSystem에는 장치의 위치를 나타내는 것을 비롯 하 여 다른 좌표계와의 동적 관계가 있습니다. 특정 시점에 장치는 다른 좌표계가 아닌 일부 좌표계를 찾을 수 있습니다. 대부분의 좌표계에서 앱은 찾을 수 없는 기간을 처리할 준비를 해야 합니다.

응용 프로그램은 직접 SpatialCoordinateSystems를 만들지 않아야 합니다. 대신 인식 Api를 통해 사용 해야 합니다. 인식 Api에는 좌표계의 세 가지 기본 소스가 있습니다. 각 소스는 [좌표계](coordinate-systems.md) 페이지에 설명 된 개념에 매핑됩니다.
* 고정 참조 프레임을 가져오려면 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> 을 만들거나 현재 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>에서 하나를 가져옵니다.
* 공간 앵커를 가져오려면 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>을 만듭니다.
* 참조의 연결 된 프레임을 가져오려면 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>을 만듭니다.

이러한 개체에서 반환 되는 모든 좌표계는 직각으로, + y up, + x를 오른쪽에, + z는 역방향입니다. 양의 x 방향에서 왼쪽 또는 오른쪽 손가락을 가리키고 양의 y 방향으로 curl 하 여 양의 z 축 점이 가리키는 방향을 기억할 수 있습니다. 엄지가 가리키는 방향이 해당 좌표계에 대해 양의 z-축이 가리키는 방향입니다. 다음 그림은 이 두 좌표계를 보여 줍니다.

![왼쪽 및 오른쪽 좌표계](images/left-hand-right-hand.gif)<br>
*왼쪽 및 오른쪽 좌표계*

HoloLens의 위치를 기반으로 SpatialCoordinateSystem를 부트스트랩 하려면 아래 섹션에 설명 된 대로 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> 클래스를 사용 하 여 참조의 고정 또는 고정 프레임을 만듭니다.

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>공간 단계를 사용 하 여 전 세계에 holograms 두기

불투명 Windows Mixed Reality 몰입 형 헤드셋의 좌표계는 정적 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference:: Current</a> 속성을 사용 하 여 액세스 됩니다. 이 API는 좌표계, 플레이어의 꽂혀 있는지 여부에 대 한 정보, 플레이어가 모바일 인지 여부에 대 한 정보 및 헤드셋이 방향성 인지 여부를 나타내는 정보를 제공 합니다. 공간 단계에 대 한 업데이트에 대 한 이벤트 처리기도 있습니다.

먼저 공간 단계를 가져오고 그에 대 한 업데이트를 구독 합니다. 

**공간 스테이지 초기화** 에 대 한 코드

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

OnCurrentChanged 메서드에서 앱은 공간 단계를 검사 하 고 그에 따라 플레이어 환경을 업데이트 해야 합니다. 이 예제에서는 스테이지 경계의 시각화 뿐만 아니라 사용자가 지정 하는 시작 위치와 스테이지의 보기 범위와 이동 속성 범위를 제공 합니다. 또한 단계를 제공할 수 없는 경우에는 자체의 고정 좌표계로 대체 합니다.


**공간 스테이지 업데이트** 에 대 한 코드

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

스테이지 경계를 정의 하는 꼭 짓 점 집합은 시계 방향으로 제공 됩니다. Windows Mixed Reality shell은 사용자가 해당 영역에 접근 하는 경우 경계에서 울타리를 그립니다. 사용자의 목적에 맞게 walkable 영역을 triangularize 수 있습니다. 다음 알고리즘을 사용 하 여 단계를 triangularize 수 있습니다.


**공간 스테이지 triangularization** 코드

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>고정 된 참조 프레임을 사용 하 여 holograms를 전 세계에 두기

[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) 클래스는 사용자가 이동 하는 동안 사용자의 주변을 기준으로 [고정 된 상태로 유지](coordinate-systems.md#stationary-frame-of-reference) 되는 참조 프레임을 나타냅니다. 이 참조 프레임은 장치 근처의 좌표를 안정적으로 유지 합니다. SpatialStationaryFrameOfReference의 한 가지 주요 사용은 holograms를 렌더링할 때 렌더링 엔진 내에서 기본 세계 좌표계로 작동 하는 것입니다.

SpatialStationaryFrameOfReference을 가져오려면 [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) 클래스를 사용 하 고 [Createstationaryframeofreferenceatcurrentlocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)을 호출 합니다.

Windows Holographic 앱 템플릿 코드에서 다음을 수행 합니다.

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* 고정 참조 프레임은 전체 공간에 맞춰 최적 위치를 제공 하도록 설계 되었습니다. 해당 참조 프레임 내의 개별 위치는 약간 드리프트 할 수 있습니다. 이는 장치가 환경에 대해 더 자세히 알게 되기 때문에 정상입니다.
* 개별 holograms를 정확 하 게 배치 해야 하는 경우에는 SpatialAnchor를 사용 하 여 개별 홀로그램을 실제 세계의 위치에 고정 해야 합니다. 예를 들어 사용자가 특별 한 관심을 나타내는 지점입니다. 앵커 위치는 드리프트 되지 않지만 수정할 수 있습니다. 수정이 발생 한 후에는 다음 프레임에서 시작 하는 수정 된 위치를 앵커에서 사용 합니다.

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>공간 앵커를 사용 하 여 holograms을 전 세계에 두기

[공간 앵커](coordinate-systems.md#spatial-anchors) 는 시간이 지남에 따라 앵커가 유지 되도록 하는 시스템을 사용 하 여 실제 세계의 특정 위치에 holograms를 넣는 좋은 방법입니다. 이 항목에서는 앵커를 만들고 사용 하는 방법과 앵커 데이터로 작업 하는 방법에 대해 설명 합니다.

선택한 SpatialCoordinateSystem 내에서 임의 위치와 방향으로 SpatialAnchor을 만들 수 있습니다. 장치는 현재 좌표계를 찾을 수 있어야 하 고, 시스템은 공간 앵커의 한도에 도달 해서는 안 됩니다.

정의 된 SpatialAnchor의 좌표계는 초기 위치의 정확한 위치와 방향을 유지 하기 위해 지속적으로 조정 됩니다. 그런 다음이 SpatialAnchor를 사용 하 여 정확한 위치의 사용자 환경에서 수정 된 것으로 표시 되는 holograms를 렌더링할 수 있습니다.

앵커를 그대로 유지 하는 조정 효과는 앵커에서의 거리가 증가할수록 확대 됩니다. 따라서 해당 앵커의 원점에서 약 3 미터 이상인 앵커를 기준으로 콘텐츠를 렌더링 하지 않아야 합니다.

[CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) 속성은 장치에서 앵커의 정확한 위치를 조정할 때 감속/가속을 적용 하 여 앵커를 기준으로 콘텐츠를 배치 하는 데 사용할 수 있는 좌표계를 가져옵니다.

[RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) 속성 및 해당 [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) 이벤트를 사용 하 여 이러한 조정을 직접 관리할 수 있습니다.

### <a name="persist-and-share-spatial-anchors"></a>공간 앵커 유지 및 공유

[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) 클래스를 사용 하 여 SpatialAnchor를 로컬로 유지 한 다음 동일한 HoloLens 장치에서 이후 앱 세션으로 다시 가져올 수 있습니다.

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 공간 앵커</a>를 사용 하 여 로컬 SpatialAnchor에서 영 속 클라우드 앵커를 만들 수 있습니다. 그러면 앱이 여러 HoloLens, IOS 및 Android 장치에서 찾을 수 있습니다.  여러 장치에서 공통 공간 앵커를 공유 하 여 각 사용자는 동일한 물리적 위치에서 해당 앵커에 대해 렌더링 된 콘텐츠를 볼 수 있습니다.  이렇게 실제 세계 공유 환경을 제공합니다.

HoloLens, iOS 및 Android 디바이스에서 비대칭 홀로그램 지속에 <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>를 사용할 수도 있습니다.  유지되는 클라우드 공간 앵커를 공유하면 여러 디바이스가 동시에 함께 존재하지 않는 경우에도 시간 경과에 따라 같은 지속형 홀로그램을 관찰할 수 있습니다.

HoloLens 앱에서 공유 환경 빌드를 시작 하려면 5 분 <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 공간 앵커 HoloLens 빠른</a>시작을 사용해 보세요.

Azure 공간 앵커를 사용 하 여 실행 하면 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens에서 앵커를 만들고 찾을</a>수 있습니다.  <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android 및 iOS</a> 에 대 한 연습을 사용할 수 있으므로 모든 장치에서 동일한 앵커를 공유할 수 있습니다.

### <a name="create-spatialanchors-for-holographic-content"></a>Holographic 콘텐츠에 대 한 SpatialAnchors 만들기

이 코드 샘플에서는 **누름** 제스처가 검색 될 때 앵커를 만들도록 Windows Holographic 앱 템플릿을 수정 했습니다. 그러면 큐브가 렌더링 단계 중에 앵커에 배치 됩니다.

도우미 클래스에서 여러 앵커를 지원 하기 때문에이 코드 샘플을 사용 하 여 원하는 만큼의 큐브를 삽입할 수 있습니다.

앵커의 Id는 앱에서 제어 하는 항목입니다. 이 예제에서는 앱의 앵커 컬렉션에 현재 저장 되어 있는 앵커의 수를 기준으로 순차적으로 명명 스키마를 만들었습니다.

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>SpatialAnchorStore를 비동기적으로 로드 하 고 캐시 합니다.

다음을 포함 하 여이 지 속성을 처리 하는 데 도움이 되는 SampleSpatialAnchorHelper 클래스를 작성 하는 방법을 살펴보겠습니다.
* Platform:: String 키로 인덱싱된 메모리 내 앵커의 컬렉션을 저장 합니다.
* 로컬 메모리 내 컬렉션과 별도로 유지 되는 시스템의 SpatialAnchorStore에서 앵커를 로드 하는 중입니다.
* 앱에서이 작업을 선택 하면 SpatialAnchorStore에 대 한 로컬 메모리 내 앵커 컬렉션을 저장 합니다.

[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)에 [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) 개체를 저장 하는 방법은 다음과 같습니다.

클래스가 시작 되 면 SpatialAnchorStore를 비동기적으로 요청 합니다. 이 작업에는 API가 앵커 저장소를 로드할 때 시스템 i/o가 포함 됩니다 .이 API는 비동기 방식으로 수행 되므로 i/o가 차단 되지 않습니다.

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

앵커를 저장 하는 데 사용할 수 있는 SpatialAnchorStore 제공 됩니다. 문자열에 해당 하는 키 값을 SpatialAnchors 데이터 값과 연결 하는 IMapView입니다. 이 샘플 코드에서는 도우미 클래스의 public 함수를 통해 액세스할 수 있는 개인 클래스 멤버 변수에이를 저장 합니다.

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>일시 중단/다시 시작 이벤트를 연결 하 여 앵커 저장소를 저장 하 고 로드 하는 것을 잊지 마세요.

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

### <a name="save-content-to-the-anchor-store"></a>앵커 저장소에 콘텐츠 저장

시스템이 앱을 일시 중단 하는 경우 공간 앵커를 앵커 저장소에 저장 해야 합니다. 응용 프로그램의 구현에 필요한 것 처럼 다른 시간에 앵커 저장소에 앵커를 저장 하도록 선택할 수도 있습니다.

SpatialAnchorStore에 메모리 내 앵커를 저장할 준비가 되 면 컬렉션을 반복 하 여 각 컬렉션을 저장 해 볼 수 있습니다.

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>앱이 다시 시작 될 때 앵커 저장소에서 콘텐츠 로드

앱이 다시 시작 될 때 또는 앱의 implementaiton 필요한 다른 모든 시간에 이전에 AnchorStore에 저장 된 앵커를 앵커 저장소의 IMapView에서 SpatialAnchors의 고유한 메모리 내 데이터베이스로 전송 하 여 복원할 수 있습니다.

SpatialAnchorStore에서 앵커를 복원 하려면 원하는 각 항목을 자체 메모리 내 컬렉션에 복원 합니다.

SpatialAnchors의 고유한 메모리 내 데이터베이스가 필요 합니다. 사용자가 만든 SpatialAnchors과 문자열을 연결 하는 몇 가지 방법이 있습니다. 샘플 코드에서는 Windows:: Foundation:: Collections:: IMap을 사용 하 여 앵커를 저장 하도록 선택 합니다 .이를 통해 SpatialAnchorStore에 동일한 키와 데이터 값을 쉽게 사용할 수 있습니다.

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>복원 되는 앵커는 당장 과정이 되지 않을 수 있습니다. 예를 들어 별도의 방에 있는 앵커 이거나 다른 빌딩에 있을 수 있습니다. AnchorStore에서 검색 된 앵커는 사용 하기 전에 locatability을 테스트 해야 합니다.

<br>

>[!NOTE]
>이 예제 코드에서는 AnchorStore에서 모든 앵커를 검색 합니다. 이는 요구 사항이 아닙니다. 앱은 구현에 의미가 있는 문자열 키 값을 사용 하 여 앵커의 특정 하위 집합을 선택 하 고 선택할 수 있습니다.

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

경우에 따라 앱 상태를 지우고 새 데이터를 작성 해야 합니다. [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)를 사용 하 여이 작업을 수행 하는 방법은 다음과 같습니다.

도우미 클래스를 사용 하 여 Clear 함수를 래핑하는 것은 거의 필요 하지 않습니다. 도우미 클래스에는 SpatialAnchorStore 인스턴스를 소유 하는 책임이 있으므로 샘플 구현에서이 작업을 수행 하도록 선택 했습니다.

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>예: 앵커 좌표계와 고정 참조 프레임 좌표계 연결

앵커가 있고 앵커 좌표계의 특정 항목을 대부분의 다른 콘텐츠에 대해 이미 사용 하 고 있는 SpatialStationaryReferenceFrame 연결 하려는 경우를 가정해 보겠습니다. [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) 를 사용 하 여 앵커의 좌표계에서 고정 참조 프레임에 대 한 변환을 가져올 수 있습니다.

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

이 프로세스는 다음과 같은 두 가지 방법으로 유용 합니다.
1. 두 참조 프레임을 서로 비교 하 여 이해할 수 있는지 여부를 알려 줍니다.
2. 그렇다면 한 좌표계에서 다른 좌표계로 직접 이동 하는 변환을 제공 합니다.

이 정보를 사용 하면 두 참조 프레임 간의 개체 간 공간 관계를 이해할 수 있습니다.

렌더링의 경우 원래 참조 프레임이 나 앵커를 기준으로 개체를 그룹화 하 여 더 나은 결과를 얻을 수 있습니다. 각 그룹에 대해 별도의 그리기 패스를 수행 합니다. 뷰 행렬은 처음에 동일한 좌표계를 사용 하 여 생성 된 모델 변환이 있는 개체에 대해 보다 정확 합니다.

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>장치에 연결 된 참조 프레임을 사용 하 여 holograms 만들기

장치 위치에 연결 된 상태를 [유지](coordinate-systems.md#attached-frame-of-reference) 하는 홀로그램을 렌더링 하려는 경우가 있습니다. 예를 들어, 장치에서 해당 방향을 결정 하 고 해당 위치를 확인할 수 없을 때 정보 메시지를 표시 합니다. 공간. 이를 위해 참조의 연결 된 프레임을 사용 합니다.

SpatialLocatorAttachedFrameOfReference 클래스는 실제 기반이 아니라 장치에 상대적인 좌표계를 정의 합니다. 이 프레임에는 참조 프레임을 만들 때 사용자가 연결 된 방향을 가리키는 사용자의 주변을 기준으로 하는 고정 머리글이 있습니다. 이 참조 프레임의 모든 방향은 사용자가 장치를 회전 하는 경우에도 해당 고정 된 제목을 기준으로 합니다.

HoloLens의 경우이 프레임 좌표계의 원점은 사용자 헤드의 회전 중심에 위치 하 여 해당 위치는 헤드 회전의 영향을 받지 않습니다. 앱은이 점에 상대적인 오프셋을 지정 하 여 사용자 앞에 holograms을 배치할 수 있습니다.

SpatialLocatorAttachedFrameOfReference을 가져오려면 SpatialLocator 클래스를 사용 하 고 CreateAttachedFrameOfReferenceAtCurrentHeading를 호출 합니다.

이는 Windows Mixed Reality 장치의 전체 범위에 적용 됩니다.

### <a name="use-a-reference-frame-attached-to-the-device"></a>장치에 연결 된 참조 프레임 사용

이 섹션에서는 Windows Holographic 앱 템플릿에서 변경한 내용에 대해 설명 하 고이 API를 사용 하 여 장치에 연결 된 참조 프레임을 사용 하도록 설정 합니다. 이 "연결 된" 홀로그램은 고정 또는 고정 된 holograms 함께 작동 하며, 장치에서 전 세계의 위치를 찾을 수 없는 경우에도 사용할 수 있습니다.

먼저, SpatialStationaryFrameOfReference 대신 SpatialLocatorAttachedFrameOfReference를 저장 하도록 템플릿을 변경 했습니다.

**HolographicTagAlongSampleMain**에서:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

**HolographicTagAlongSampleMain**에서:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

업데이트 중에는 이제 프레임 예측을 사용 하 여에서 가져온 타임 스탬프의 좌표계를 가져옵니다.

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>공간 포인터 포즈를 가져오고 사용자의 응시를 따릅니다.

Holographic shell이 사용자의 응시를 따르는 방법과 유사 하 게 사용자의 [응시](gaze.md)를 따르기 위해 예제 홀로그램을 원합니다. 이를 위해 동일한 타임 스탬프에서 SpatialPointerPose을 가져와야 합니다.

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

이 SpatialPointerPose에는 [사용자의 현재 제목](gaze-in-directx.md)에 따라 홀로그램을 배치 하는 데 필요한 정보가 있습니다.

사용자가 편안 하 게 생각 하는 경우 선형 보간 ("lerp")을 사용 하 여 일정 기간 동안 발생 하는 변화를 원활 하 게 합니다. 이는 홀로그램을 응시로 잠그는 것 보다 사용자에 게 더 친숙 합니다. 태그를 따라 홀로그램의 위치도 Lerping 이동을 감소 시켜 홀로그램의 안정화를 사용할 수 있습니다. 이러한 완충를 수행 하지 않은 경우 일반적으로 사용자 헤드의 imperceptible 이동으로 간주 되는 것으로 간주 되므로 사용자가 홀로그램 지터를 볼 수 있습니다.

**StationaryQuadRenderer::P Osit홀로그램 홀로그램**:

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
>디버깅 패널의 경우 뷰를 액세스가 방해 하지 않도록 홀로그램의 위치를 약간 아래로 변경 하도록 선택할 수 있습니다. 이러한 작업을 수행 하는 방법의 예는 다음과 같습니다.

**StationaryQuadRenderer::P Osit. 홀로그램**:

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

### <a name="rotate-the-hologram-to-face-the-camera"></a>카메라를 향하는 홀로그램 회전

홀로그램에 배치 하는 것 만으로는 충분 하지 않습니다 .이 경우에는 4입니다. 또한 사용자에 게는 개체를 회전 해야 합니다. 이 유형의 billboarding은 홀로그램을 사용자 환경의 일부로 유지할 수 있기 때문에 세계 공간에서 발생 합니다. 뷰 공간 billboarding는 홀로그램이 표시 방향으로 잠겨 있으므로 편안 하지 않습니다. 이 경우에는 스테레오 렌더링을 방해 하지 않는 뷰 공간 빌보드 변환을 얻기 위해 왼쪽과 오른쪽 뷰 행렬 사이를 보간 해야 할 수도 있습니다. 여기서는 X 및 Z 축을 중심으로 회전 하 여 사용자를 확인 합니다.

**StationaryQuadRenderer:: Update**에서:

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

이 예에서는 홀로그램을 배치할 SpatialLocatorAttachedReferenceFrame의 좌표계에서 홀로그램을 렌더링 하도록 선택 합니다. 다른 좌표계를 사용 하 여 렌더링 하기로 결정 한 경우에는 장치 연결 참조 프레임의 좌표계에서 해당 좌표계로 변환을 가져와야 합니다.

From **HolographicTagAlongSampleMain:: Render**:

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

정말 간단하죠. 그러면 홀로그램은 사용자의 응시 방향 앞에서 2 미터의 위치를 "추적" 합니다.

>[!NOTE]
>이 예제에서는 추가 콘텐츠도 로드 합니다. StationaryQuadRenderer를 참조 하세요.

## <a name="handling-tracking-loss"></a>추적 손실 처리

장치를 세계에서 찾을 수 없는 경우 앱이 "추적 손실"를 경험 합니다. Windows Mixed Reality 앱은 위치 추적 시스템에 대 한 이러한 중단을 처리할 수 있어야 합니다. 기본 SpatialLocator의 LocatabilityChanged 이벤트를 사용 하 여 이러한 중단을 관찰 하 고 응답을 생성할 수 있습니다.

**Appmain:: SetHolographicSpace:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

앱이 LocatabilityChanged 이벤트를 수신 하는 경우 필요에 따라 동작을 변경할 수 있습니다. 예를 들어 PositionalTrackingInhibited 된 상태에서 앱은 정상 작업을 일시 중지 하 고 경고 메시지를 표시 하는 [태그를 따라 홀로그램](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) 을 렌더링할 수 있습니다.

Windows Holographic 앱 템플릿에는 이미 생성 된 LocatabilityChanged 처리기가 제공 됩니다. 기본적으로 위치 추적을 사용할 수 없는 경우 디버그 콘솔에 경고를 표시 합니다. 앱에서 필요에 따라 응답을 제공 하기 위해이 처리기에 코드를 추가할 수 있습니다.

**Appmain .cpp에서:**

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

[공간 매핑](spatial-mapping-in-directx.md) api는 좌표계를 사용 하 여 표면 망상의 모델 변환을 가져옵니다.

## <a name="see-also"></a>참조
* [좌표계](coordinate-systems.md)
* [공간 앵커](spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [DirectX의 헤드 및 눈 응시](gaze-in-directx.md)
* [DirectX의 헤드 및 모션 컨트롤러](hands-and-motion-controllers-in-directx.md)
* [DirectX의 공간 매핑](spatial-mapping-in-directx.md)
