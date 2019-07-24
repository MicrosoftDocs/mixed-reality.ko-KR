---
title: DirectX의 공간 매핑
description: DirectX 앱에서 공간 매핑을 구현 하는 방법을 설명 합니다. 여기에는 유니버설 Windows 플랫폼 SDK에 포함 된 공간 매핑 샘플 응용 프로그램에 대 한 자세한 설명이 포함 되어 있습니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows mixed reality, 공간 매핑, 환경, 상호 작용, directx, winrt, api, 샘플 코드, UWP, SDK, 연습
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63550691"
---
# <a name="spatial-mapping-in-directx"></a>DirectX의 공간 매핑

이 항목에서는 DirectX 앱에서 [공간 매핑을](spatial-mapping.md) 구현 하는 방법에 대해 설명 합니다. 여기에는 유니버설 Windows 플랫폼 SDK에 포함 된 공간 매핑 샘플 응용 프로그램에 대 한 자세한 설명이 포함 되어 있습니다.

이 항목에서는 [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP 코드 샘플의 코드를 사용 합니다.

>[!NOTE]
>이 문서의 코드 조각은 현재 [ C++ holographic 프로젝트 템플릿에](creating-a-holographic-directx-project.md)사용 되 C++는 것 처럼 C + 17-so-far working 규격 C++/winrt 대신/cx 사용을 보여 줍니다.  개념은 C++/winrt 프로젝트와 동일 하지만 코드를 변환 해야 합니다.

## <a name="directx-development-overview"></a>DirectX 개발 개요

공간 매핑에 대 한 네이티브 응용 프로그램 개발에서는 [Windows. 공간](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) 네임 스페이스의 api를 사용 합니다. 이러한 Api는 [Unity](spatial-mapping-in-unity.md)에서 노출 하는 공간 매핑 api와 직접적으로 비슷한 방식으로 공간 매핑 기능을 완벽 하 게 제어할 수 있도록 합니다.

### <a name="perception-apis"></a>인식 Api

공간 매핑 개발을 위해 제공 되는 기본 유형은 다음과 같습니다.
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) 는 응용 프로그램에서 지정한 공간의 영역에 대 한 정보를 SpatialSurfaceInfo 개체의 형태로 제공 합니다.
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) 는 고유한 ID, 경계 볼륨 및 마지막 변경 시간을 포함 하 여 단일 파티션의 공간 표면을 설명 합니다. 요청 시 비동기적으로 SpatialSurfaceMesh을 제공 합니다.
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) 에는 SpatialSurfaceInfo에서 요청 된 SpatialSurfaceMesh 개체를 사용자 지정 하는 데 사용 되는 매개 변수가 포함 됩니다
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) 는 단일 공간 표면의 메시 데이터를 나타냅니다. 꼭 짓 점 위치, 꼭 짓 점 법선 및 삼각형 인덱스의 데이터는 멤버 SpatialSurfaceMeshBuffer 개체에 포함 되어 있습니다.
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) 는 단일 유형의 메시 데이터를 래핑합니다.

이러한 Api를 사용 하 여 응용 프로그램을 개발 하는 경우 기본 프로그램 흐름은 다음과 같이 표시 됩니다 (아래에 설명 된 샘플 응용 프로그램 참조).
- **SpatialSurfaceObserver 설정**
  - [Requestaccessasync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)를 호출 하 여 사용자가 장치의 공간 매핑 기능을 사용 하는 응용 프로그램에 대 한 권한을 부여 했는지 확인 합니다.
  - SpatialSurfaceObserver 개체를 인스턴스화합니다.
  - [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) 를 호출 하 여 공간 표면에 대 한 정보를 원하는 공간 영역을 지정 합니다. 나중에이 함수를 다시 호출 하 여 이러한 영역을 수정할 수 있습니다. 각 지역은 [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)를 사용 하 여 지정 됩니다.
  - 지정 된 공간 영역에서 공간 표면에 대해 새 정보를 사용할 수 있을 때마다 발생 하는 [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) 이벤트에 등록 합니다.
- **ObservedSurfacesChanged 이벤트 처리**
  - 이벤트 처리기에서 [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) 를 호출 하 여 SpatialSurfaceInfo 개체의 맵을 받습니다. 이 맵을 사용 하 여 [사용자 환경에](spatial-mapping.md#mesh-caching)있는 공간 표면의 레코드를 업데이트할 수 있습니다.
  - 각 SpatialSurfaceInfo 개체에 대해 [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) 를 쿼리하여 선택한 [공간 좌표계](coordinate-systems.md) 로 표현 된 표면의 공간 범위를 확인할 수 있습니다.
  - 공간 표면의 메시를 요청 하려는 경우 [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)를 호출 합니다. 원하는 삼각형 밀도와 반환 된 메시 데이터의 형식을 지정 하는 옵션을 제공할 수 있습니다.
- **수신 및 프로세스 메시**
  - TryComputeLatestMeshAsync에 대 한 각 호출은 aysnchronously 하나의 SpatialSurfaceMesh 개체를 반환 합니다.
  - 이 개체를 사용 하면 포함 된 SpatialSurfaceMeshBuffer 개체에 액세스 하 여 메시의 삼각형 인덱스, 꼭 짓 점 위치 및 (요청 된 경우) 꼭 짓 점 법선에 액세스할 수 있습니다. 이 데이터는 메시 렌더링에 사용 되는 [Direct3D 11 api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) 와 직접 호환 되는 형식입니다.
  - 여기에서 응용 프로그램은 필요에 따라 메시 데이터의 분석 또는 [처리](spatial-mapping.md#mesh-processing) 를 수행 하 고이를 [렌더링](spatial-mapping.md#rendering) 및 물리 [rayrayreyreyreyreyreyreing](spatial-mapping.md#raycasting-and-collision)
  - 한 가지 중요 한 정보는 메시 꼭 짓 점 위치 (예: 메시를 렌더링 하는 데 사용 되는 꼭 짓 점 셰이더)에 배율을 적용 하 여 버퍼에 저장 되는 최적화 된 정수 단위에서 미터까지 변환 해야 한다는 것입니다. [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)를 호출 하 여이 규모를 검색할 수 있습니다.

### <a name="troubleshooting"></a>문제 해결
* SpatialSurfaceMesh에서 반환 된 소수 자릿수를 사용 하 여 꼭 짓 점 셰이더의 메시 꼭 짓 점 위치를 조정 하는 것을 잊지 마세요 [. VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)

## <a name="spatial-mapping-code-sample-walkthrough"></a>공간 매핑 코드 샘플 연습

[Holographic 공간 매핑](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) 코드 샘플에는 surface 메시를 관리 하 고 렌더링 하기 위한 인프라를 포함 하 여 화면 메시를 앱에 로드 하기 시작 하는 데 사용할 수 있는 코드가 포함 되어 있습니다.

이제 DirectX 앱에 화면 매핑 기능을 추가 하는 방법을 살펴보겠습니다. [Windows Holographic 앱 템플릿](creating-a-holographic-directx-project.md) 프로젝트에이 코드를 추가 하거나 위에서 언급 한 코드 샘플을 탐색 하 여 수행할 수 있습니다. 이 코드 샘플은 Windows Holographic 앱 템플릿을 기반으로 합니다.

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>SpatialPerception 기능을 사용 하도록 앱 설정

앱은 공간 매핑 기능을 사용할 수 있어야 합니다. 이는 공간 메쉬가 개인 데이터로 간주 될 수 있는 사용자 환경의 표현 이기 때문에 필요 합니다. 앱에 대 한 appxmanifest.xml 파일에서이 기능을 선언 합니다. 예를 들면 다음과 같습니다.

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

이 기능은 **uap2** 네임 스페이스에서 제공 됩니다. 매니페스트에이 네임 스페이스에 대 한 액세스 권한을 얻으려면 &lt;패키지 > 요소에 *xlmns* 특성으로 포함 합니다. 예를 들면 다음과 같습니다.

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>공간 매핑 기능 지원 확인

Windows Mixed Reality는 공간 매핑을 지원 하지 않는 장치를 포함 하 여 다양 한 장치를 지원 합니다. 앱에서 공간 매핑을 사용 하거나 공간 매핑을 사용 하 여 기능을 제공 해야 하는 경우 사용을 시도 하기 전에 공간 매핑이 지원 되는지 확인 해야 합니다. 예를 들어 혼합 현실 앱에서 공간 매핑을 필요로 하는 경우 사용자가 공간 매핑을 사용 하지 않고 장치에서 실행 하려고 하면 해당 효과에 대 한 메시지가 표시 됩니다. 또는 앱이 사용자 환경 대신 자체 가상 환경을 렌더링 하 여 공간 매핑을 사용할 수 있을 때 발생 하는 것과 비슷한 환경을 제공할 수 있습니다. 모든 이벤트에서이 API를 사용 하면 공간 매핑 데이터를 가져오지 않고 적절 한 방법으로 응답 하지 않을 때 앱을 인식할 수 있습니다.

공간 매핑 지원에 대 한 현재 장치를 확인 하려면 먼저 UWP 계약이 수준 4 이상 인지 확인 한 다음 SpatialSurfaceObserver:: IsSupported ()를 호출 합니다. [Holographic 공간 매핑](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) 코드 샘플의 컨텍스트에서이 작업을 수행 하는 방법은 다음과 같습니다. 액세스를 요청 하기 직전에 지원이 선택 됩니다.

SpatialSurfaceObserver:: IsSupported () API는 SDK 버전 15063부터 사용할 수 있습니다. 필요한 경우이 API를 사용 하기 전에 프로젝트의 대상을 플랫폼 버전 15063으로 변경 합니다.

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

UWP 계약이 수준 4 보다 작은 경우에는 장치가 공간 매핑을 수행할 수 있는 것 처럼 앱이 진행 되어야 합니다.

### <a name="request-access-to-spatial-mapping-data"></a>공간 매핑 데이터에 대 한 액세스 요청

응용 프로그램은 표면 관찰자를 만들기 전에 공간 매핑 데이터에 대 한 액세스 권한을 요청 해야 합니다. 다음은이 페이지의 뒷부분에서 제공 하는 추가 세부 정보와 함께 Surface 매핑 코드 샘플을 기반으로 하는 예제입니다.

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a>Surface 관찰자 만들기

**Windows::P erception:: 공간::** surface 네임 스페이스는 [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)에서 지정 하는 하나 이상의 볼륨을 관찰 하는 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) 클래스를 포함 합니다. [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) 인스턴스를 사용 하 여 실시간으로 표면 메시 데이터에 액세스할 수 있습니다.

**Appmain .h**에서:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

이전 섹션에서 설명한 것 처럼 앱에서 사용할 수 있으려면 공간 매핑 데이터에 대 한 액세스를 요청 해야 합니다. 이 액세스 권한은 HoloLens에 자동으로 부여 됩니다.

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

다음으로, 특정 경계 볼륨을 관찰 하도록 surface 관찰자를 구성 해야 합니다. 여기서는 좌표계의 원점을 중심으로 20x20x5 미터 인 상자를 관찰 합니다.

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

대신 여러 경계 볼륨을 설정할 수 있습니다.

*의사 코드는 다음과 같습니다.*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

다른 경계 모양 (예: 대/소문자 구분)을 사용 하거나 축에 정렬 되지 않은 경계 상자를 사용할 수도 있습니다.

*의사 코드는 다음과 같습니다.*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Surface 매핑 데이터를 사용할 수 없을 때 앱에서 다른 작업을 수행 해야 하는 경우 [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) 이 **허용** 되지 않는 경우에 응답 하는 코드를 작성할 수 있습니다. 예를 들어 몰입 형 pc에서는 허용 되지 않습니다. 장치에는 공간 매핑에 대 한 하드웨어가 없기 때문에 장치가 연결 되었습니다. 이러한 장치의 경우 대신 사용자 환경 및 장치 구성에 대 한 정보를 위해 공간 단계를 사용 해야 합니다.

### <a name="initialize-and-update-the-surface-mesh-collection"></a>표면 메시 컬렉션 초기화 및 업데이트

Surface 관찰자가 성공적으로 만들어지면 surface 메시 컬렉션 초기화를 진행할 수 있습니다. 여기서는 끌어오기 모델 API를 사용 하 여 현재 관찰 된 표면의 현재 집합을 즉시 가져옵니다.

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

표면 메시 데이터를 가져오는 데 사용할 수 있는 푸시 모델도 있습니다. 사용자가 선택 하는 경우 끌어오기 모델만 사용 하도록 앱을 자유롭게 디자인할 수 있습니다 .이 경우에는 대개 프레임당 한 번 또는 게임 설정 중과 같은 특정 기간 동안 데이터를 폴링합니다. 그렇다면 위의 코드는 필요한 것입니다.

이 코드 샘플에서는 사용해 서 용도로 두 모델을 사용 하는 방법을 보여 주기 위해 선택 했습니다. 여기서는 시스템에서 변경을 인식할 때마다 최신 surface 메시 데이터를 받도록 이벤트를 구독 합니다.

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

코드 샘플도 이러한 이벤트에 응답 하도록 구성 됩니다. 이 작업을 수행 하는 방법을 살펴보겠습니다.

**참고:** 이는 앱이 메시 데이터를 처리 하는 가장 효율적인 방법이 아닐 수 있습니다. 이 코드는 명확 하 게 작성 되었으며 최적화 되지 않았습니다.

Surface 메시 데이터는 [Platform:: guid](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) 를 키 값으로 사용 하 여 [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) 개체를 저장 하는 읽기 전용 맵에 제공 됩니다.

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

이 데이터를 처리 하기 위해 컬렉션에 없는 키 값을 먼저 찾습니다. 샘플 앱에 데이터를 저장 하는 방법에 대 한 자세한 내용은이 항목의 뒷부분에 제공 됩니다.

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

또한 surface 메시 컬렉션에 있지만 더 이상 시스템 컬렉션에 없는 surface 메시를 제거 해야 합니다. 이렇게 하려면 메시를 추가 하 고 업데이트 하는 것과 유사한 작업을 수행 해야 합니다. 앱의 컬렉션에서 루프를 실행 하 고 있는 **Guid** 가 시스템 컬렉션에 있는지 확인 합니다. 시스템 컬렉션에 없으면 우리에서 제거 합니다.

AppMain .cpp의 이벤트 처리기에서:

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

RealtimeSurfaceMeshRenderer에서의 메시 정리 구현:

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>표면 메시 데이터 버퍼 획득 및 사용

Surface 메시 정보를 가져오는 것은 데이터 컬렉션을 끌어오고 해당 컬렉션에 대 한 업데이트를 처리 하는 것 만큼 쉽습니다. 이제 데이터를 사용 하는 방법에 대해 자세히 살펴보겠습니다.

이 코드 예제에서는 렌더링에 surface 메시를 사용 하도록 선택 했습니다. 실제 표면 뒤에 occluding holograms에 대 한 일반적인 시나리오입니다. 또한 메시를 렌더링 하거나 처리 된 버전을 렌더링 하 여 앱 또는 게임 기능 제공을 시작 하기 전에 검색 되는 대화방 영역을 사용자에 게 표시할 수 있습니다.

코드 샘플은 이전 섹션에서 설명한 이벤트 처리기에서 surface 메시 업데이트를 받을 때 프로세스를 시작 합니다. 이 함수에서 중요 한 코드 줄은 surface *메시*를 업데이트 하는 호출입니다. 이번에는 메시 정보를 이미 처리 했 고, 적합 한 것 처럼 사용 하기 위해 꼭 짓 점 및 인덱스 데이터를 가져오려고 합니다.

RealtimeSurfaceMeshRenderer에서:

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

샘플 코드는 데이터 클래스 **SurfaceMesh**가 메시 데이터 처리 및 렌더링을 처리 하도록 설계 되었습니다. 이러한 메시는 **RealtimeSurfaceMeshRenderer** 실제로 지도를 보관 하는 것입니다. 각 항목에는 가져온 SpatialSurfaceMesh에 대 한 참조가 있으며, 메시 꼭 짓 점 또는 인덱스 버퍼에 액세스 하거나 메시의 변환을 가져와야 하는 경우 언제 든 지 사용할 수 있습니다. 지금은 업데이트가 필요 하므로 메시에 플래그를 지정 합니다.

SurfaceMesh에서:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

다음 번에 메시를 표시 하 라는 메시지가 표시 될 때 먼저 플래그를 확인 합니다. 업데이트가 필요한 경우에는 GPU에서 꼭 짓 점 및 인덱스 버퍼가 업데이트 됩니다.

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

먼저 원시 데이터 버퍼를 가져옵니다.

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

그런 다음 HoloLens에서 제공 하는 메시 데이터를 사용 하 여 Direct3D 장치 버퍼를 만듭니다.

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

**참고:** 이전 코드 조각에서 사용 되는 CreateDirectXBuffer 도우미 함수는 Surface 매핑 코드 샘플을 참조 하세요. SurfaceMesh, GetDataFromIBuffer. 이제 장치 리소스 만들기가 완료 되 고 메시는 로드 되 고 업데이트 및 렌더링 준비가 된 것으로 간주 됩니다.

### <a name="update-and-render-surface-meshes"></a>표면 메시 업데이트 및 렌더링

SurfaceMesh 클래스에는 특수 업데이트 함수가 있습니다. 각 [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) 에는 고유한 변환이 있으며,이 샘플에서는 **SpatialStationaryReferenceFrame** 에 현재 좌표계를 사용 하 여 변환을 가져옵니다. 그런 다음 GPU에서 모델 상수 버퍼를 업데이트 합니다.

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

Surface 메시를 렌더링 해야 하는 경우 컬렉션을 렌더링 하기 전에 몇 가지 준비 작업을 수행 합니다. 현재 렌더링 구성에 대 한 셰이더 파이프라인을 설정 하 고 입력 어셈블러 단계를 설정 합니다. Holographic camera helper 클래스 **CameraResources** 는 이미 뷰/프로젝션 상수 버퍼를 설정 했습니다.

From **RealtimeSurfaceMeshRenderer:: Render**:

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

이 작업이 완료 되 면 메시를 반복 하 고 각 항목을 그리도록 지시 합니다. **참고:** 이 샘플 코드는 다른 종류의 고르기를 사용 하도록 최적화 되어 있지 않지만 앱에이 기능을 포함 해야 합니다.

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

개별 메시는 꼭 짓 점 및 인덱스 버퍼, stride 및 모델 변환 상수 버퍼를 설정 하는 작업을 담당 합니다. Windows Holographic 앱 템플릿에서 회전 하는 큐브와 마찬가지로, 인스턴스를 사용 하 여 stereoscopic 버퍼에 렌더링 합니다.

**SurfaceMesh::D raw**:

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a>표면 매핑의 렌더링 선택

표면 매핑 코드 샘플은 표면 메시 데이터의 폐색 전용 렌더링 및 surface 메시 데이터의 화면에 렌더링에 대 한 코드를 제공 합니다. 선택 하는 경로는 응용 프로그램에 따라 달라 집니다. 이 문서의 두 구성에 대해 살펴보겠습니다.

**Holographic 효과에 대 한 폐색 버퍼 렌더링**

현재 가상 카메라의 렌더링 대상 보기를 선택 취소 하 여 시작 합니다.

AppMain .cpp에서:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

이는 "미리 렌더링" 패스입니다. 여기서는 깊이만 렌더링 하도록 메시 렌더러를 요청 하 여 폐색 버퍼를 만듭니다. 이 구성에서는 렌더링 대상 뷰를 연결 하지 않으며, 메시 렌더러는 픽셀 셰이더 단계를 **nullptr** 로 설정 하므로 GPU가 픽셀을 그리지 않아도 됩니다. 기 하 도형은 깊이 버퍼로 래스터화됩니다. 그러면 그래픽 파이프라인이 중지 됩니다.

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

Surface Mapping 폐색 버퍼에 대 한 추가 깊이 테스트를 사용 하 여 holograms를 그릴 수 있습니다. 이 코드 샘플에서는 표면 뒤에 있는 경우 큐브의 픽셀을 다른 색으로 렌더링 합니다.

AppMain .cpp에서:

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

Hlsl의 코드를 기반으로 하는 SpecialEffectPixelShader:

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

**참고:** **GatherDepthLess** 루틴은 Surface 매핑 코드 샘플을 참조 하세요. SpecialEffectPixelShader. hlsl.

**화면 메시 데이터를 표시로 렌더링**

표면 메시를 스테레오 표시 버퍼에만 그릴 수도 있습니다. 조명을 사용 하 여 전체 얼굴을 그리도록 선택 했지만, 와이어 프레임을 자유롭게 그리거나 렌더링 하기 전에 메시를 처리 하 고 질감 지도를 적용 하는 등의 작업을 수행할 수 있습니다.

여기서 코드 샘플은 컬렉션을 그리기 위해 망상 렌더러에 지시 합니다. 이번에는 깊이 전용 패스를 지정 하지 않으므로 픽셀 셰이더를 연결 하 고 현재 가상 카메라에 대해 지정한 대상을 사용 하 여 렌더링 파이프라인을 완료 합니다.

```cpp
// SR mesh rendering pass: Draw SR mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>참조
* [홀로그램 DirectX 프로젝트 만들기](creating-a-holographic-directx-project.md)
* [Windows. 인식 공간 API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
