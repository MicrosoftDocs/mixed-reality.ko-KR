---
title: Unreal의 공간 매핑
description: Unreal의 공간 매핑 사용 가이드
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, 공간 매핑
ms.openlocfilehash: ffa57749cd96e240ac4812f950f4e13a6dbc68bd
ms.sourcegitcommit: 45da0a056fa42088ff81ccdd11232830fbe8430f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84720409"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="5ab49-104">Unreal의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="5ab49-104">Spatial Mapping in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="5ab49-105">개요</span><span class="sxs-lookup"><span data-stu-id="5ab49-105">Overview</span></span>
<span data-ttu-id="5ab49-106">공간 매핑을 사용하면 HoloLens 주위의 세계를 표시하여 실제 세계의 표면에 개체를 배치함으로써 홀로그램이 사용자에게 더 현실감 있게 보이도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-106">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="5ab49-107">또한 공간 매핑은 실제 세계의 심도 큐를 사용하여 사용자의 세계에 개체를 고정합니다. 이렇게 하면 사용자가 이러한 홀로그램이 사실은 홀로그램의 공간에 있음을 알게 됩니다. 즉, 공간에 떠 있거나 사용자를 따라 이동하는 홀로그램이 실제처럼 느껴지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-107">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="5ab49-108">가능한 모든 상황에서 편안하게 항목을 배치하려 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-108">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="5ab49-109">공간 매핑 품질, 배치, 폐색, 렌더링 등에 대한 자세한 내용은 [공간 매핑](spatial-mapping.md) 문서에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-109">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="5ab49-110">공간 매핑 사용</span><span class="sxs-lookup"><span data-stu-id="5ab49-110">Enabling Spatial Mapping</span></span>

<span data-ttu-id="5ab49-111">HoloLens에서 공간 매핑을 사용하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-111">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="5ab49-112">**편집 > 프로젝트 설정**을 열고 **플랫폼** 섹션까지 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-112">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="5ab49-113">**HoloLens**를 선택하고 **공간 인식**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-113">Select **HoloLens** and check **Spatial Perception**.</span></span>

<span data-ttu-id="5ab49-114">공간 매핑을 옵트인하고 HoloLens 게임에서 **MRMesh**를 디버깅하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="5ab49-115">**ARSessionConfig**를 열고 **ARSettings > 세계 매핑** 섹션을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="5ab49-116">**추적된 기하 도형에서 메시 데이터 생성**을 선택합니다. 즉, HoloLens 플러그 인이 비동기로 공간 매핑 데이터를 가져오고 **MRMesh**를 통해 Unreal에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="5ab49-117">**MRMesh**에 있는 모든 삼각형의 흰색 와이어 프레임 윤곽선을 표시하려면 **와이어 프레임에서 메시 데이터 렌더링**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![Spatial Anchors 저장소 준비](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="5ab49-119">런타임에 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="5ab49-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="5ab49-120">다음 매개 변수를 수정하여 공간 매핑 런타임 동작을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="5ab49-121">**편집 > 프로젝트 설정**을 열고 **플랫폼** 섹션까지 아래로 스크롤한 다음, **HoloLens > 공간 매핑**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![Spatial Anchors 프로젝트 설정](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="5ab49-123">**입방미터당 최대 삼각형 수**는 공간 매핑 메시의 삼각형 밀도를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="5ab49-124">**공간 메싱 볼륨 크기**는 공간 매핑 데이터를 렌더링하고 업데이트할 플레이어 주변의 큐브 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="5ab49-125">애플리케이션 런타임 환경이 클 것으로 예상된다면 이 값이 실제 공간과 일치하게 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="5ab49-126">반대로 애플리케이션이 사용자 바로 주변의 표면에만 홀로그램을 배치하면 되는 경우에는 이 값이 더 작아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="5ab49-127">사용자가 월드를 걸어 다닐 때 공간 매핑 볼륨이 함께 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="5ab49-128">MRMesh 작업</span><span class="sxs-lookup"><span data-stu-id="5ab49-128">Working with MRMesh</span></span>
<span data-ttu-id="5ab49-129">런타임에 **MRMesh**에 액세스하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-129">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="5ab49-130">**ARTrackableNotify** 구성 요소를 청사진 행위자에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-130">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![Spatial Anchors AR 추적 가능 알림](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="5ab49-132">**ARTrackableNotify** 구성 요소를 선택하고 **세부 정보** 패널에서 **이벤트** 섹션을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-132">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="5ab49-133">모니터링할 이벤트에서 **+** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-133">Click the **+** button on the events you want to monitor.</span></span> 

![Spatial Anchors 이벤트](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="5ab49-135">이 경우 **추적된 기하 도형 추가** 이벤트가 모니터링되며 공간 매핑 데이터에 일치하는 유효한 세계 메시를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-135">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="5ab49-136">[UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) 구성 요소 API에서 이벤트의 전체 목록을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-136">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="5ab49-137">청사진 이벤트 그래프 또는 C++에서 메시의 재질을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-137">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="5ab49-138">아래의 스크린샷은 청사진 경로를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-138">The screenshot below shows the Blueprint route:</span></span> 

![Spatial Anchors 예제](images/unreal-spatialmapping-example.PNG)

<span data-ttu-id="5ab49-140">아래 코드에 표시된 것처럼 C++에서 `OnTrackableAdded` 대리자를 구독하여 가능한 즉시 `ARTrackedGeometry`를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-140">In C++, you can subscribe to the `OnTrackableAdded` delegate to get the `ARTrackedGeometry` as soon as it is available, shown in the code below.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="5ab49-141">프로젝트 build.cs 파일의 **PublicDependencyModuleNames** 목록에 **AugmentedReality**가 **반드시** 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-141">The project’s build.cs file **MUST** have **AugmentedReality** in the **PublicDependencyModuleNames** list.</span></span>
> - <span data-ttu-id="5ab49-142">여기에는 **UARTrackedGeometry**의 **MRMesh** 구성 요소를 검사할 수 있는 **ARBlueprintLibrary** 및 **MRMeshComponent**가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-142">This includes **ARBlueprintLibrary.h** and **MRMeshComponent.h**, which lets you inspect the **MRMesh** component of the **UARTrackedGeometry**.</span></span> 

![Spatial Anchors 예제 C++ 코드](images/unreal-spatialmapping-examplecode.PNG)

<span data-ttu-id="5ab49-144">공간 매핑이 **ARTrackedGeometries**를 통해 표시되는 유일한 데이터 형식은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-144">Spatial mapping is not the only type of data that gets surfaced through **ARTrackedGeometries**.</span></span> <span data-ttu-id="5ab49-145">공간 매핑 기하 도형인 `EARObjectClassification` 및 `World`도 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-145">You can check that the `EARObjectClassification` is `World`, which means this is spatial mapping geometry.</span></span> 

<span data-ttu-id="5ab49-146">업데이트 및 제거 이벤트에 대한 비슷한 대리자로</span><span class="sxs-lookup"><span data-stu-id="5ab49-146">There are similar delegates for updated and removed events:</span></span> 
- `AddOnTrackableUpdatedDelegate_Handle` 
- <span data-ttu-id="5ab49-147">`AddOnTrackableRemovedDelegate_Handle`을 차례로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-147">`AddOnTrackableRemovedDelegate_Handle`.</span></span> 

<span data-ttu-id="5ab49-148">[UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API에서 이벤트의 전체 목록을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5ab49-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ab49-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5ab49-149">See also</span></span>
* [<span data-ttu-id="5ab49-150">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="5ab49-150">Spatial mapping</span></span>](spatial-mapping.md)
