---
title: DirectX의 공간 매핑
description: DirectX 앱에서 공간 매핑을 구현 하는 방법에 설명 합니다. 유니버설 Windows 플랫폼 SDK에 포함 된 공간 매핑 샘플 응용 프로그램에 대 한 자세한 설명은 포함 됩니다.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows 혼합 현실, 공간 매핑, 환경, 상호 작용, directx, winrt, api, 샘플 코드, UWP, SDK, 연습
ms.openlocfilehash: db3f1464158c04127e456cadd5fb633336909344
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605137"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="a44d8-105">DirectX의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="a44d8-105">Spatial mapping in DirectX</span></span>

<span data-ttu-id="a44d8-106">이 항목에서는 구현 하는 방법을 설명 [공간 매핑](spatial-mapping.md) DirectX 앱에서.</span><span class="sxs-lookup"><span data-stu-id="a44d8-106">This topic describes how to implement [spatial mapping](spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="a44d8-107">유니버설 Windows 플랫폼 SDK에 포함 된 공간 매핑 샘플 응용 프로그램에 대 한 자세한 설명은 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-107">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="a44d8-108">이 항목의 코드를 사용 합니다 [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP 코드 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="a44d8-109">이 문서의 코드 조각 사용에 현재 방법을 보여 줍니다 C++/CX 대신 C + + 17 규격 C++/WinRT에 사용 되는 [ C++ holographic 프로젝트 템플릿을](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="a44d8-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="a44d8-110">개념에 대 한 동일는 C++코드를 변환 해야 하지만 /WinRT 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="directx-development-overview"></a><span data-ttu-id="a44d8-111">DirectX 개발 개요</span><span class="sxs-lookup"><span data-stu-id="a44d8-111">DirectX development overview</span></span>

<span data-ttu-id="a44d8-112">공간 매핑에 대 한 네이티브 응용 프로그램 개발에서 Api를 사용 하 여 [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-112">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="a44d8-113">이러한 Api는 공간 매핑에 의해 노출 된 Api 직접 비슷한 방식으로 공간 매핑 기능에 대 한 모든 권한을 제공 [Unity](spatial-mapping-in-unity.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-113">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="a44d8-114">인식 Api</span><span class="sxs-lookup"><span data-stu-id="a44d8-114">Perception APIs</span></span>

<span data-ttu-id="a44d8-115">공간 매핑 개발을 위해 제공 되는 기본 형식 아래와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-115">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="a44d8-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) SpatialSurfaceInfo 개체의 형태로 사용자에 가까운 공간의 지역 응용 프로그램에서 지정한 화면에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-116">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="a44d8-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) 단일 파티션의 공간 화면, 고유 ID를 포함 하 여, 볼륨 및 마지막 변경 시간을 경계에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-117">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="a44d8-118">요청 시 비동기적으로 SpatialSurfaceMesh 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-118">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="a44d8-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) SpatialSurfaceInfo에서 요청한 SpatialSurfaceMesh 개체 사용자 지정 하는 데 사용 되는 매개 변수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-119">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="a44d8-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) 단일 공간 화면에 대 한 망상 조직 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-120">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="a44d8-121">꼭 짓 점 위치, 꼭 짓 점 법선 및 삼각형 인덱스에 대 한 데이터 멤버 SpatialSurfaceMeshBuffer 개체에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-121">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="a44d8-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) 단일 유형의 망상 조직 데이터를 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-122">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="a44d8-123">이러한 Api를 사용 하 여 응용 프로그램을 개발 하는 경우 기본 프로그램 흐름 (볼 수 있듯이 아래에 설명 된 샘플 응용 프로그램에서) 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-123">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="a44d8-124">**프로그램 SpatialSurfaceObserver 설정**</span><span class="sxs-lookup"><span data-stu-id="a44d8-124">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="a44d8-125">호출 [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), 사용자 장치의 공간 매핑 기능을 사용 하도록 응용 프로그램에 대 한 권한을 부여한 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-125">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="a44d8-126">SpatialSurfaceObserver 개체를 인스턴스화하십시오.</span><span class="sxs-lookup"><span data-stu-id="a44d8-126">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="a44d8-127">호출 [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) 영역 공간 표면에 대 한 정보를 원하는 간격을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-127">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="a44d8-128">단순히이 함수를 다시 호출 하 여 나중에 이러한 영역을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-128">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="a44d8-129">지역별로 사용 하 여 지정 된 [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-129">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="a44d8-130">에 등록 합니다 [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) 새 정보를 지정 하는 공간의 지역에서 공간 표면에 대 한 있을 때마다 발생 하는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-130">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="a44d8-131">**ObservedSurfacesChanged 이벤트 처리**</span><span class="sxs-lookup"><span data-stu-id="a44d8-131">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="a44d8-132">이벤트 처리기에서 호출 [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) 지도 SpatialSurfaceInfo 개체를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-132">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="a44d8-133">이 맵을 사용 하는 공간 화면의 사용자 레코드를 업데이트할 수 있습니다 [사용자의 환경에 존재](spatial-mapping.md#mesh-caching)합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-133">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="a44d8-134">각 SpatialSurfaceInfo 개체에 대해 쿼리할 수 있습니다 [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) 단위로 화면의 공간 익스텐트를 확인 하는 [공간 좌표계](coordinate-systems.md) 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-134">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="a44d8-135">공간 화면에 대 한 메시를 요청 하려는 경우 호출할 [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-135">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="a44d8-136">삼각형의 원하는 밀도 및 메시 반환 된 데이터의 형식을 지정 하는 옵션을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-136">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="a44d8-137">**수신 및 메시를 처리 합니다.**</span><span class="sxs-lookup"><span data-stu-id="a44d8-137">**Receive and process mesh**</span></span>
  - <span data-ttu-id="a44d8-138">TryComputeLatestMeshAsync 됩니다 aysnchronously 호출할 때마다 하나의 SpatialSurfaceMesh 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-138">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="a44d8-139">이 개체에서 삼각형 인덱스, 꼭 짓 점 위치에 액세스 하기 위해 포함 된 SpatialSurfaceMeshBuffer 개체에 액세스할 수 있습니다 (요청 된 경우) 및 메시의 꼭 짓 점 법선입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-139">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="a44d8-140">이 데이터를 직접 사용 하 여 호환 되는 형식 수를 [Direct3D 11 Api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) 메시 렌더링에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-140">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="a44d8-141">응용 프로그램은 여기에서 분석을 수행할 필요에 따라 수 또는 [처리](spatial-mapping.md#mesh-processing) 메시 데이터의 사용에 대 한 [렌더링](spatial-mapping.md#rendering) 와 물리학 [플레이어가 및 충돌](spatial-mapping.md#raycasting-and-collision)합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-141">From here your application can optionally perform analysis or [processing](spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](spatial-mapping.md#rendering) and physics [raycasting and collision](spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="a44d8-142">에 하나의 중요 한 세부 정보 확장 (예: 꼭 짓 점 셰이더는 메시 렌더링에 사용)의 메시 꼭 짓 점 위치를 적용 해야 미터제는 저장 된 버퍼에에 최적화 된 정수 단위에서 변환할은입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-142">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="a44d8-143">호출 하 여이 확장을 검색할 수 있습니다 [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-143">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="a44d8-144">문제 해결</span><span class="sxs-lookup"><span data-stu-id="a44d8-144">Troubleshooting</span></span>
* <span data-ttu-id="a44d8-145">반환 된 확장을 사용 하 여 꼭 짓 점 셰이더를 메시 꼭 짓 점 위치를 조정 해야 [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="a44d8-145">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="a44d8-146">공간 매핑 코드 샘플 연습</span><span class="sxs-lookup"><span data-stu-id="a44d8-146">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="a44d8-147">합니다 [Holographic 공간 매핑](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) 표면 메시를 관리 하기 위한 인프라를 포함 하 여 앱을 로드 하는 데 시작에 사용할 수 있으며 렌더링 표면 메시는 코드를 포함 하는 코드 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-147">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="a44d8-148">이제 DirectX 앱에 화면 매핑 기능을 추가 하는 방법을 단계별로 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-148">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="a44d8-149">이 코드를 추가할 수 있습니다 하 [Windows Holographic 앱 템플릿](creating-a-holographic-directx-project.md) 위에서 언급 한 코드 샘플을 통해 이동 하 여 프로젝트 또는 있습니다 따라 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-149">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="a44d8-150">이 코드 샘플은 Windows Holographic 앱 템플릿을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-150">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="a44d8-151">SpatialPerception 기능을 사용 하도록 앱 설정</span><span class="sxs-lookup"><span data-stu-id="a44d8-151">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="a44d8-152">앱 공간 매핑 기능을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-152">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="a44d8-153">왜냐하면 필요한 공간 메시는 개인 데이터를 간주 될 수 있는 사용자의 환경으로 표현한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-153">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="a44d8-154">앱에 대해 package.appxmanifest 파일에서이 기능을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-154">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="a44d8-155">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-155">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="a44d8-156">제공 되는 기능을 **uap2** 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-156">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="a44d8-157">매니페스트에이 네임 스페이스에 대 한 액세스를 가져오려고로 포함를 *xlmns* 특성을 &lt;패키지 > 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-157">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="a44d8-158">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-158">Here's an example:</span></span>

```xml
<Package
    xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="http://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="a44d8-159">공간 매핑 기능 지원에 대 한 확인</span><span class="sxs-lookup"><span data-stu-id="a44d8-159">Check for spatial mapping feature support</span></span>

<span data-ttu-id="a44d8-160">Windows Mixed Reality 다양 한 범위의 공간 매핑을 지원 하지 않는 장치를 비롯 한 장치를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-160">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="a44d8-161">앱 공간 매핑을 사용할 수 있습니다 또는 기능을 제공 하려면 공간 매핑을 사용 해야 하는 경우 확인 공간 매핑 사용 하기 전에 지원 되는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-161">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="a44d8-162">예를 들어 공간 매핑 혼합된 현실 앱에 필요한 경우 사용자가 공간 매핑하지 않고 장치에서 실행 하면 그 결과는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-162">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="a44d8-163">또는 앱 사용자의 환경에 공간 매핑을 사용할 수 있는 경우 어떤 상황이 유사한 환경을 제공 하는 대신 자체 가상 환경에 렌더링 하는 일을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-163">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="a44d8-164">어떠한 경우에이 API 앱을 경우 하지 공간 매핑 데이터를 가져오기 하 고 적절 한 방식으로 응답의 알아야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-164">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="a44d8-165">공간 매핑 지원에 대 한 현재 장치를 확인 하려면 먼저 4 이상의 수준에서 UWP 계약 인지를 확인 하 고 SpatialSurfaceObserver::IsSupported() 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-165">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="a44d8-166">컨텍스트에서 작업을 수행 하는 방법은 다음과 같습니다 합니다 [Holographic 공간 매핑](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) 코드 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-166">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="a44d8-167">지원은 액세스를 요청 하기 직전에 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-167">Support is checked just before requesting access.</span></span>

<span data-ttu-id="a44d8-168">SpatialSurfaceObserver::IsSupported() API는 SDK 버전 15063부터 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-168">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="a44d8-169">필요한 경우이 API를 사용 하기 전에 플랫폼 버전 15063 프로젝트 대상을 다시 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-169">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

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

<span data-ttu-id="a44d8-170">참고는 UWP 계약 수준 4 보다 작은 경우 앱을 계속할지 것 처럼 장치가 공간 매핑을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-170">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="a44d8-171">공간 매핑 데이터에 대 한 액세스를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-171">Request access to spatial mapping data</span></span>

<span data-ttu-id="a44d8-172">앱 화면 모든 관찰자가 만들기 전에 공간 매핑 데이터를 액세스할 수 있는 권한을 요청 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-172">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="a44d8-173">나중에이 페이지를 제공 하는 자세한 세부 정보를 사용 하 여 매핑 화면 코드 샘플을 따라 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-173">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

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

### <a name="create-a-surface-observer"></a><span data-ttu-id="a44d8-174">관찰자를 화면 만들기</span><span class="sxs-lookup"><span data-stu-id="a44d8-174">Create a surface observer</span></span>

<span data-ttu-id="a44d8-175">**Windows::Perception::Spatial::Surfaces** 네임 스페이스는 포함 된 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) 에서 지정 하는 하나 이상의 볼륨을 관찰 하는 클래스는 [ SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-175">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="a44d8-176">사용 된 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) 실시간에서 표면 메시 데이터에 액세스 하는 인스턴스.</span><span class="sxs-lookup"><span data-stu-id="a44d8-176">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="a44d8-177">**AppMain.h**:</span><span class="sxs-lookup"><span data-stu-id="a44d8-177">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="a44d8-178">이전 섹션에서 설명한 대로, 앱에서 사용 하려면 먼저 공간 매핑 데이터에 대 한 액세스를 요청 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-178">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="a44d8-179">이 액세스는 HoloLens에 자동으로 부여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-179">This access is granted automatically on the HoloLens.</span></span>

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

<span data-ttu-id="a44d8-180">다음으로, 특정 경계 볼륨을 관찰 하려면 화면 관찰자를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-180">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="a44d8-181">여기에서는 인 20 x 20 x 5 미터의 좌표계 원점에서 가운데에 있는 상자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-181">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

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

<span data-ttu-id="a44d8-182">참고는 여러 경계 볼륨을 대신 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-182">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="a44d8-183">*의사 코드입니다.*</span><span class="sxs-lookup"><span data-stu-id="a44d8-183">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="a44d8-184">경계 등 다른 모양은 만들-보기 꼭지점이 절 두 체를 사용 하 여 이기도 또는 축 없는 경계 상자를 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-184">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="a44d8-185">*의사 코드입니다.*</span><span class="sxs-lookup"><span data-stu-id="a44d8-185">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="a44d8-186">앱을 노출 매핑 데이터를 사용할 수 없는 경우 아무 것도 다르게 수행 하는 경우 사례에 응답 하는 코드를 작성할 수 있습니다 위치 합니다 [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) 아닙니다 **허용** -예를 들어, 이 허용 되지 않습니다 Pc에서 공간 매핑에 대 한 하드웨어 없으므로 해당 장치를 연결 하는 몰입 감이 뛰어난 장치를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-186">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="a44d8-187">이러한 장치의 경우 대신 사용자의 환경 및 장치 구성에 대 한 정보에 대 한 스테이지의 공간 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-187">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="a44d8-188">초기화 및 표면 메시 컬렉션 업데이트</span><span class="sxs-lookup"><span data-stu-id="a44d8-188">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="a44d8-189">노출 관찰자 성공적으로 만들어진 경우 표면 메시 컬렉션이 초기화를 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-189">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="a44d8-190">여기에 끌어오기 모델 API를 사용 하 여 관찰 된 화면의 현재 집합을 즉시 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-190">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

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

<span data-ttu-id="a44d8-191">표면 메시 데이터를 가져올 수 있는 푸시 모델 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-191">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="a44d8-192">무료를 선택 하면이 경우에서는 폴링하면 데이터에 대 한 자주-끌어오기 모델에만 사용 하도록 앱을 디자인 하는 예를 들어 프레임-당 한 번 또는 특정 기간 동안와 같은 게임 설치 중입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-192">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="a44d8-193">그렇다면 위의 코드를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-193">If so, the above code is what you need.</span></span>

<span data-ttu-id="a44d8-194">코드 샘플에서는 사용해 용도로 두 모델의 사용을 보여 주기 위해 선택 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-194">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="a44d8-195">이때 시스템 변경을 인식할 때마다 최신 표면 메시 데이터를 받기 위해 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-195">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="a44d8-196">코드 샘플은 또한 이러한 이벤트에 응답 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-196">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="a44d8-197">이렇게 하는 방법을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-197">Let's walk through how we do this.</span></span>

<span data-ttu-id="a44d8-198">**참고:** 망상 조직 데이터를 처리할 앱에 대 한 가장 효율적인 방법은 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-198">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="a44d8-199">이 코드 명확성을 위해 기록 되 고 최적화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-199">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="a44d8-200">표면 메시 데이터를 저장 하는 읽기 전용으로 지도에서 제공 됩니다 [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) 사용 하 여 개체 [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) 키 값으로.</span><span class="sxs-lookup"><span data-stu-id="a44d8-200">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="a44d8-201">이 데이터 처리를 위해 살펴봅니다 컬렉션에 없는 키 값에 대 한 첫 번째입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-201">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="a44d8-202">샘플 앱에서 데이터를 저장 하는 방법에 대 한 자세한 내용은이 항목의 뒷부분에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-202">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

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

<span data-ttu-id="a44d8-203">또한이 표면 메시 컬렉션에 있지만 더 이상 시스템 컬렉션에 없는 표면 메시를 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-203">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="a44d8-204">이렇게 하려면 어떤 앞서 살펴본 추가 하 고 메시; 업데이트에 대 한 반대과 유사 작업을 수행 해야 루프를 앱의 컬렉션에 있는지 확인 합니다 **Guid** 있다고 시스템 컬렉션에.</span><span class="sxs-lookup"><span data-stu-id="a44d8-204">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="a44d8-205">시스템 컬렉션에 없으면 우리에서 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-205">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="a44d8-206">AppMain.cpp에서 이벤트 처리기:</span><span class="sxs-lookup"><span data-stu-id="a44d8-206">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="a44d8-207">메시 정리 RealtimeSurfaceMeshRenderer.cpp에서 구현의:</span><span class="sxs-lookup"><span data-stu-id="a44d8-207">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="a44d8-208">획득 및 표면 메시 데이터 버퍼를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-208">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="a44d8-209">표면 메시 정보를 가져오는 했습니다 데이터 컬렉션을 가져와서 해당 컬렉션에 대 한 업데이트를 처리 하는 것 만큼 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-209">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="a44d8-210">이제 살펴보겠습니다 세부 데이터를 사용 하는 방법에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-210">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="a44d8-211">코드 예제에서는 렌더링 표면 메시를 사용 하기로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-211">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="a44d8-212">실제 화면 뒤 occluding 홀로그램에 대 한 일반적인 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-212">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="a44d8-213">메시를 렌더링 하거나 처리 된 버전을 렌더링할 수도 있습니다, 그리고 사용자의 영역을 표시 하려면 대화방 앱 이나 게임 기능 제공을 시작 하기 전에 검사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-213">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="a44d8-214">코드 샘플은 이전 섹션에서 설명 하는 이벤트 처리기에서 표면 메시 업데이트를 받을 때 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-214">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="a44d8-215">중요 한 코드 줄을이 함수에는 화면을 업데이트 하는 데 *메시*:이 시점에서는 이미 처리 메시 정보 고에서는 필요에 따라 사용을 꼭 짓 점 및 인덱스 데이터를 가져오려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-215">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="a44d8-216">RealtimeSurfaceMeshRenderer.cpp:</span><span class="sxs-lookup"><span data-stu-id="a44d8-216">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

<span data-ttu-id="a44d8-217">샘플 코드는 설계 되도록 데이터 클래스 **SurfaceMesh**, 핸들 메시 데이터 처리 및 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-217">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="a44d8-218">이러한 메시는 무엇을 **RealtimeSurfaceMeshRenderer** 실제로의 맵을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-218">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="a44d8-219">각각에서 왔는지에 SpatialSurfaceMesh에 대 한 참조가 있으며 메시에 서 변환을 가져오거나 메시 꼭 짓 점 또는 인덱스 버퍼 액세스 해야 하는 언제 든 지 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-219">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="a44d8-220">지금은 업데이트 필요 하다는 메시를 플래그 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-220">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="a44d8-221">SurfaceMesh.cpp:</span><span class="sxs-lookup"><span data-stu-id="a44d8-221">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="a44d8-222">메시는 자신을 그릴 하 라는 메시지가 표시 되며 다음 번 확인 플래그를 먼저 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-222">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="a44d8-223">업데이트가 필요한 경우 GPU에서 꼭 짓 점 및 인덱스 버퍼 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-223">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

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

<span data-ttu-id="a44d8-224">먼저, 원시 데이터 버퍼를 가져온:</span><span class="sxs-lookup"><span data-stu-id="a44d8-224">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="a44d8-225">그런 다음 Direct3D 장치 버퍼는 HoloLens 제공한 망상 조직 데이터를 사용 하 여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-225">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

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

<span data-ttu-id="a44d8-226">**참고:** 이전 코드 조각에 사용 되는 CreateDirectXBuffer 도우미 함수에 대 한 매핑 화면 코드 샘플을 참조 합니다. SurfaceMesh.cpp, GetDataFromIBuffer.h 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-226">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="a44d8-227">이제 장치 리소스 만들기가 완료 되 고 메시 로드 및 업데이트에 대 한 준비 되어 렌더링 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-227">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="a44d8-228">업데이트 및 표면 메시 렌더링</span><span class="sxs-lookup"><span data-stu-id="a44d8-228">Update and render surface meshes</span></span>

<span data-ttu-id="a44d8-229">SurfaceMesh 클래스에는 특수 한 업데이트 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-229">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="a44d8-230">각 [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) 자체 변환 있으며 샘플에 대 한 현재 좌표계를 사용 하는 **SpatialStationaryReferenceFrame** 변환을 가져오려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-230">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="a44d8-231">그런 다음 모델 상수 버퍼를 GPU에 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-231">Then it updates the model constant buffer on the GPU.</span></span>

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

<span data-ttu-id="a44d8-232">표면 메시 렌더링 시간이 되 면 컬렉션을 렌더링 하기 전에 일부 준비 작업을 수행 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-232">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="a44d8-233">현재 렌더링 구성에 대 한 셰이더 파이프라인을 설정 하 고 입력된 어셈블러를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-233">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="a44d8-234">holographic 카메라 도우미 클래스 **CameraResources.cpp** 이미 설정한 보기/프로젝션 상수 버퍼 지금 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-234">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="a44d8-235">From **RealtimeSurfaceMeshRenderer::Render**:</span><span class="sxs-lookup"><span data-stu-id="a44d8-235">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

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

<span data-ttu-id="a44d8-236">이 작업이 완료 되 면이 메시의 루프에서는 자신을 그리는 각각을 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-236">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="a44d8-237">**참고:** 이 샘플 코드 모든 종류의 꼭지점이 절 두 체 고르기를 사용 하도록 최적화 되어 있지 않지만 앱에서이 기능을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-237">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

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

<span data-ttu-id="a44d8-238">개별 메시는 고 꼭 짓 점 및 인덱스 버퍼, 진행 속도, 모델 변환 상수 버퍼를 설정 하는 일을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-238">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="a44d8-239">Windows Holographic 앱 템플릿에서 회전 큐브를에서와 마찬가지로 인스턴스를 사용 하 여 stereoscopic 버퍼에 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-239">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="a44d8-240">**SurfaceMesh::Draw**:</span><span class="sxs-lookup"><span data-stu-id="a44d8-240">From **SurfaceMesh::Draw**:</span></span>

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

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="a44d8-241">화면 매핑을 사용 하 여 렌더링 옵션</span><span class="sxs-lookup"><span data-stu-id="a44d8-241">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="a44d8-242">매핑 화면 코드 샘플은 표면 메시 데이터 폐색 전용 렌더링 하 고 화면 표면 메시 데이터 렌더링에 대 한 코드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-242">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="a44d8-243">선택한 경로 또는 둘 다 응용 프로그램에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-243">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="a44d8-244">이 문서에서 두 구성을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-244">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="a44d8-245">**Holographic 효과 대 한 렌더링 폐색 버퍼**</span><span class="sxs-lookup"><span data-stu-id="a44d8-245">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="a44d8-246">현재 가상 카메라에 대 한 렌더링 대상 뷰를 삭제 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-246">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="a44d8-247">AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="a44d8-247">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="a44d8-248">이 "미리 렌더링" 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-248">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="a44d8-249">여기서는 폐색 버퍼만을 깊이 렌더링 하는 메시 렌더러를 요청 하 여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-249">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="a44d8-250">이 구성에서는 렌더링 대상 뷰를 연결 하지 않습니다 및 픽셀 셰이더 단계 설정 하는 메시 렌더러 **nullptr** GPU 픽셀을 그릴 필요가 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-250">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="a44d8-251">기 하 도형 깊이 버퍼에 래스터화된 되며 자리 그래픽 파이프라인에서 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-251">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

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

<span data-ttu-id="a44d8-252">화면 매핑 폐색 버퍼에 대 한 추가 깊이 테스트를 사용 하 여 홀로그램을 내릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-252">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="a44d8-253">이 코드 샘플에서는 픽셀 렌더링 큐브에 다른 색 화면 뒤 경우.</span><span class="sxs-lookup"><span data-stu-id="a44d8-253">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="a44d8-254">AppMain.cpp:</span><span class="sxs-lookup"><span data-stu-id="a44d8-254">From AppMain.cpp:</span></span>

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

<span data-ttu-id="a44d8-255">SpecialEffectPixelShader.hlsl에서 코드를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-255">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

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

<span data-ttu-id="a44d8-256">**참고:** 에 대 한 우리의 **GatherDepthLess** 루틴 매핑 화면 코드 샘플을 참조 하세요. SpecialEffectPixelShader.hlsl.</span><span class="sxs-lookup"><span data-stu-id="a44d8-256">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="a44d8-257">**화면에 렌더링 표면 메시 데이터**</span><span class="sxs-lookup"><span data-stu-id="a44d8-257">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="a44d8-258">또한 표면 메시 스테레오 디스플레이 버퍼에 내릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-258">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="a44d8-259">조명으로 전체 얼굴을 그릴 선택 했지만 자유롭게 와이어 프레임을 그리려면, 메시 렌더링 되기 전에 처리, 질감 맵을 적용 및 등입니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-259">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="a44d8-260">여기에서 코드 샘플 컬렉션을 그릴 메시 렌더러를 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-260">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="a44d8-261">이 이번 픽셀 셰이더를 연결 하 고 현재 가상 카메라에 대 한 지정한 대상을 사용 하 여 렌더링 파이프라인을 완료 하도록 깊이 전용 패스를 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a44d8-261">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a44d8-262">참조</span><span class="sxs-lookup"><span data-stu-id="a44d8-262">See also</span></span>
* [<span data-ttu-id="a44d8-263">Holographic DirectX 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="a44d8-263">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="a44d8-264">Windows.Perception.Spatial API</span><span class="sxs-lookup"><span data-stu-id="a44d8-264">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
