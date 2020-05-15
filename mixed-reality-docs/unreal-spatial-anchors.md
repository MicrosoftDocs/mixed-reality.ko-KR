---
title: Unreal의 Spatial Anchors
description: Unreal의 공간 앵커 사용 가이드
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 개발, 기능, 설명서, 가이드, 홀로그램, 공간 앵커
ms.openlocfilehash: c35d8efc9998aac5b40de833e5acbf7f80353e6b
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840142"
---
# <a name="spatial-anchors-in-unreal"></a><span data-ttu-id="3e061-104">Unreal의 Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="3e061-104">Spatial Anchors in Unreal</span></span>

<span data-ttu-id="3e061-105">공간 앵커는 애플리케이션 세션 사이의 실제 공간에서 홀로그램을 유지하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-105">Spatial anchors are used to persist holograms in real-world space between application sessions.</span></span>  <span data-ttu-id="3e061-106">이는 Unreal을 통해 ARPins로 표시되며 향후 세션에서 로드될 HoloLens의 앵커 저장소에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-106">This gets surfaced through Unreal as ARPins and gets saved in the HoloLens’ anchor store to be loaded in future sessions.</span></span> 

<span data-ttu-id="3e061-107">앵커를 저장하거나 로드하기 전에 먼저 앵커 저장소가 준비되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-107">Before saving or loading anchors, first check that the anchor store is ready.</span></span>  <span data-ttu-id="3e061-108">앵커 저장소가 준비되기 전에 HoloLens 앵커 기능을 호출하려고 시도해도 성공하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-108">Attempting to call any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![Spatial Anchors 저장소 준비](images/unreal-spatialanchors-store-ready.PNG)

## <a name="save-anchors"></a><span data-ttu-id="3e061-110">앵커 저장</span><span class="sxs-lookup"><span data-stu-id="3e061-110">Save Anchors</span></span>

<span data-ttu-id="3e061-111">세계에 고정해야 하는 구성 요소가 애플리케이션에 있으면 다음 순서에 따라 앵커 저장소에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-111">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![Spatial Anchors 저장](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="3e061-113">여기에서는 행위자를 알려진 위치에 생성하고, 그 위치와 행위자의 클래스를 기반으로 한 이름을 가진 ARPin을 만들고, 행위자를 ARPin에 추가하고, 핀을 HoloLens 앵커 저장소에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-113">Here, we are spawning an actor at a known location, creating an ARPin with that location and a name based on the actor’s class, adding the actor to the ARPin, and saving the pin to the HoloLens anchor store.</span></span>  <span data-ttu-id="3e061-114">선택한 앵커 이름은 고유해야 하므로 이 예제에서는 현재 타임 스탬프를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-114">The anchor name we choose must be unique, so in this example we append the current timestamp.</span></span>  <span data-ttu-id="3e061-115">앵커가 앵커 저장소에 성공적으로 저장한 경우, 시스템 > 맵 관리자 > 디바이스에 저장된 앵커 파일에서 HoloLens 디바이스 포털에서 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-115">If the anchor successfully saves to the anchor store, it can be inspected in the HoloLens device portal under System > Map manager > Anchor Files Saved On Device.</span></span> 

## <a name="load-anchors"></a><span data-ttu-id="3e061-116">앵커 로드</span><span class="sxs-lookup"><span data-stu-id="3e061-116">Load Anchors</span></span>

<span data-ttu-id="3e061-117">애플리케이션이 시작되면 다음 Blueprint를 호출하여 구성 요소를 앵커 위치에 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-117">When an application starts, the following blueprint can be called to restore components to their anchor locations:</span></span>

![Spatial Anchors 로드](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="3e061-119">이 예제에서는 앵커 저장소의 모든 앵커를 반복하고, 행위자를 ID에 생성하고, 앵커 저장소의 ARPin에 행위자를 고정합니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-119">In this example, we iterate over all of the anchors in the anchor store, spawn an actor at identity, and pin that actor to the ARPin from the anchor store.</span></span>  <span data-ttu-id="3e061-120">앵커는 홀로그램이 저장된 위치를 기준으로 홀로그램 위치를 다시 설정하는 것을 담당하므로 행위자를 ID에 생성하는 것이 중요합니다. 따라서 여기에 추가된 변환은 앵커에 오프셋을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-120">It is important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved, so any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="3e061-121">앵커 ID는 앵커의 저장된 이름에 따라 다른 행위자가 생성될 수 있도록 쿼리되기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-121">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="remove-anchors"></a><span data-ttu-id="3e061-122">앵커 제거</span><span class="sxs-lookup"><span data-stu-id="3e061-122">Remove Anchors</span></span> 

<span data-ttu-id="3e061-123">앵커로 작업이 완료되면 향후 세션에 포함되지 않도록 전체 앵커 저장소를 지우거나 앵커 저장소에서 개별 앵커를 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e061-123">When done with an anchor, the entire anchor store can be cleared, or individual anchors can be removed from the anchor store so they are not included in future sessions:</span></span> 

![Spatial Anchors 제거](images/unreal-spatialanchors-remove.PNG)

## <a name="see-also"></a><span data-ttu-id="3e061-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3e061-125">See also</span></span>
* [<span data-ttu-id="3e061-126">공간 앵커</span><span class="sxs-lookup"><span data-stu-id="3e061-126">Spatial anchors</span></span>](spatial-anchors.md)
* [<span data-ttu-id="3e061-127">좌표계</span><span class="sxs-lookup"><span data-stu-id="3e061-127">Coordinate systems</span></span>](coordinate-systems.md)
