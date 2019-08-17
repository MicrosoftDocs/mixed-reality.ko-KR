---
title: 새 공간에서 HoloLens 사용
description: HoloLens는 시간이 지남에 따라 공백이 표시 되는 모양을 학습 합니다. 사용자는 공간을 통해 특정 방법으로 HoloLens를 이동 하 여이 프로세스를 쉽게 수행할 수 있습니다.
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Windows Mixed Reality, 디자인, 공간 매핑, HoloLens, 표면 재구성, 메시, 헤드 추적, 매핑
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566022"
---
# <a name="use-hololens-in-new-spaces"></a><span data-ttu-id="2d5c3-105">새 공간에서 HoloLens 사용</span><span class="sxs-lookup"><span data-stu-id="2d5c3-105">Use HoloLens in New Spaces</span></span>

<span data-ttu-id="2d5c3-106">사용자가 공간을 이동할 때 HoloLens *맵*또는 해당 환경에 대 한 정보를 학습 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-106">HoloLens *maps*, or learns information about, its environment as the user moves around a space.</span></span> <span data-ttu-id="2d5c3-107">시간이 지남에 따라 HoloLens는 관찰 된 환경의 모든 부분에 대 한 *공간 맵을* 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-107">Over time, the HoloLens builds up a *spatial map* of all parts of the environment that have been observed.</span></span> <span data-ttu-id="2d5c3-108">HoloLens는 환경의 변경 내용이 관찰 될 때 지도를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-108">HoloLens updates the map as changes in the environment are observed.</span></span> <span data-ttu-id="2d5c3-109">이 검색은 앱 시작 사이에 자동으로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-109">This scan will automatically persist between app launches.</span></span>

<span data-ttu-id="2d5c3-110">장치를 켜 있고 사용자가 로그인 한 경우 HoloLens가 맵을 만들고 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-110">HoloLens will create and update maps as long as the device is on and a user is logged in.</span></span> <span data-ttu-id="2d5c3-111">장치를 보유 하거나 장치를 사용 하는 경우 장치는 해당 영역을 매핑하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-111">If you hold or wear the device with the cameras pointed at a space, the device will try to map the area.</span></span> <span data-ttu-id="2d5c3-112">HoloLens는 시간 경과에 따라 공간을 자연스럽 게 알 수 있지만 공간을 더 빠르고 효율적으로 매핑하는 데 사용할 수 있는 팁과 트릭을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-112">While the HoloLens will learn a space naturally over time, there are tips and tricks available to map the space faster and more efficiently.</span></span> 

<span data-ttu-id="2d5c3-113">HoloLens가 공간을 매핑할 수 없거나 보정을 벗어난 경우 제한 된 모드로 전환 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-113">If your HoloLens can’t map your space or is out of calibration, you may enter Limited mode.</span></span> <span data-ttu-id="2d5c3-114">제한 된 모드에서는 holograms를 주변에 놓을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-114">In Limited mode, you won’t be able to place holograms in your surroundings.</span></span>

## <a name="tips-and-tricks-for-mapping-spaces"></a><span data-ttu-id="2d5c3-115">공간 매핑을 위한 팁과 요령</span><span class="sxs-lookup"><span data-stu-id="2d5c3-115">Tips and tricks for mapping spaces</span></span>

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a><span data-ttu-id="2d5c3-116">혼합 현실에 대해 공간이 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-116">Make sure the space is set up for mixed reality</span></span>

<span data-ttu-id="2d5c3-117">환경의 기능을 사용 하면 HoloLens가 공간을 해석 하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-117">Features in an environment can make it difficult for the HoloLens to interpret a space.</span></span> <span data-ttu-id="2d5c3-118">조명 수준, 공간의 재질, 개체 레이아웃 등은 모두 HoloLens에서 영역을 매핑하는 방법에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-118">Light levels, materials in the space, the layout of objects, and more can all affect how HoloLens maps an area.</span></span>

<span data-ttu-id="2d5c3-119">Hololens의 공간을 설정 하기 위한 팁과 기타 혼합 현실 장치는 [hololens의 환경 고려 사항](environment-considerations-for-hololens.md)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-119">Tips for setting up your space for HoloLens and other mixed reality devices can be found in [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

### <a name="understand-the-scenarios-for-the-area"></a><span data-ttu-id="2d5c3-120">영역에 대 한 시나리오 이해</span><span class="sxs-lookup"><span data-stu-id="2d5c3-120">Understand the scenarios for the area</span></span>

<span data-ttu-id="2d5c3-121">가장 많은 시간을 할애 하 여 가장 많은 시간을 할애 하 여 지도가 적절 하 고 완전 하 게 사용할 수 있도록 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-121">It is important to spend the most time where you will be using the HoloLens so that the map is relevant and complete.</span></span> 

<span data-ttu-id="2d5c3-122">예를 들어, HoloLens의 사용자 시나리오에서 점 A에서 Point B로 이동 하는 경우, 이동 하는 동안 모든 방향에서 두 번까지 경로를 2-3 번 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-122">For example, if a user scenario for HoloLens involves moving from Point A to Point B, walk that path two to three times, looking in all directions as you move.</span></span> 

### <a name="walk-slowly-around-the-space"></a><span data-ttu-id="2d5c3-123">공간을 느리게 탐색</span><span class="sxs-lookup"><span data-stu-id="2d5c3-123">Walk slowly around the space</span></span>

<span data-ttu-id="2d5c3-124">영역 주위를 너무 빨리 탐색 하는 경우 HoloLens가 영역 매핑을 누락 하 게 될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-124">If you walk too quickly around the area, it's likely that the HoloLens will miss mapping areas.</span></span> <span data-ttu-id="2d5c3-125">공간을 천천히 탐색 하 고, 5-8 피트 마다 중지 하 여 주변에서 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-125">Walk slowly around the space, stopping every 5-8 feet to look around at your surroundings.</span></span>

<span data-ttu-id="2d5c3-126">부드러운 이동은 HoloLens가 더 effeciently를 지도 하는 데도 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-126">Smooth movements also help the HoloLens map more effeciently.</span></span>

### <a name="look-in-all-directions"></a><span data-ttu-id="2d5c3-127">모든 방향 살펴보기</span><span class="sxs-lookup"><span data-stu-id="2d5c3-127">Look in all directions</span></span>

<span data-ttu-id="2d5c3-128">공간을 매핑하는 경우에는 데이터가 서로 상대적으로 이동 하는 지점에 대 한 데이터를 더 많이 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-128">Looking around as you map the space gives the HoloLens more data on where points are relative to each other.</span></span> 

<span data-ttu-id="2d5c3-129">예를 들어, 검색 하지 않는 경우 HoloLens에서 실내의 상한 위치를 모를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-129">If you don't look up, for example, the HoloLens may not know where the ceiling in a room is.</span></span> 

<span data-ttu-id="2d5c3-130">공간을 매핑하면 바닥에서 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-130">Don't forget to look down at the floor as you map the space.</span></span>

### <a name="cover-key-areas-multiple-times"></a><span data-ttu-id="2d5c3-131">주요 영역을 여러 번 커버</span><span class="sxs-lookup"><span data-stu-id="2d5c3-131">Cover key areas multiple times</span></span>

<span data-ttu-id="2d5c3-132">영역을 여러 번 이동 하면 첫 번째 연습에서 누락 했을 수 있는 기능을 선택 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-132">Moving through an area multiple times will help pick up features you may have missed on the first walkthrough.</span></span> <span data-ttu-id="2d5c3-133">2 ~ 3 배의 영역을 탐색 하 여 이상적인 맵을 작성 해 보세요.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-133">Try traversing an area two to three times to build an ideal map.</span></span>

<span data-ttu-id="2d5c3-134">가능 하면 이러한 이동을 반복 하는 동안 한 방향으로 영역을 이동 하는 데 소요 되는 시간을 이동한 다음, 원래 상태로 전환 하 고 다시 연습 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-134">If possible, while repeating these movements, spend time walking through an area in one direction, then turn around and walk back the way you came.</span></span>

### <a name="take-your-time-mapping-the-area"></a><span data-ttu-id="2d5c3-135">영역 매핑</span><span class="sxs-lookup"><span data-stu-id="2d5c3-135">Take your time mapping the area</span></span>

<span data-ttu-id="2d5c3-136">HoloLens가 전체 지도 하 고 해당 환경에 맞게 조정 되는 데 15 ~ 20 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-136">It can take between 15 and 20 minutes for the HoloLens to fully map and adjust itself to its surroundings.</span></span> <span data-ttu-id="2d5c3-137">HoloLens를 자주 사용 하려는 공간이 있는 경우 해당 시간을 앞으로 이동 하 여 공간을 매핑하면 나중에 문제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-137">If you have a space in which you plan to use a HoloLens frequently, taking that time up front to map the space can prevent issues later on.</span></span> 

## <a name="possible-errors-in-the-spatial-map"></a><span data-ttu-id="2d5c3-138">공간 맵에서 발생할 수 있는 오류</span><span class="sxs-lookup"><span data-stu-id="2d5c3-138">Possible errors in the spatial map</span></span>

<span data-ttu-id="2d5c3-139">공간 매핑 데이터의 오류는 다음 세 가지 범주 중 하나에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-139">Errors in spatial mapping data fall into one of three categories:</span></span>

* <span data-ttu-id="2d5c3-140">*구멍*: 실제 서피스가 공간 매핑 데이터에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-140">*Holes*: Real-world surfaces are missing from the spatial mapping data.</span></span>
* <span data-ttu-id="2d5c3-141">*Hallucinations*: 실제 세계에 존재 하지 않는 공간 매핑 데이터에 서피스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-141">*Hallucinations*: Surfaces exist in the spatial mapping data that do not exist in the real world.</span></span>
* <span data-ttu-id="2d5c3-142">*Wormholes*: 이는 실제로는 맵의 다른 부분에 있는 것으로 간주 하 여 공간 맵의 일부를 ' 손실 ' 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-142">*Wormholes*: HoloLens 'loses' part of the spatial map by thinking it is in a different part of the map than it actually is.</span></span>
* <span data-ttu-id="2d5c3-143">*편차*: 공간 매핑 데이터의 표면은 실제 화면에 완전히 맞추고, 푸시 또는 끌어올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-143">*Bias*: Surfaces in the spatial mapping data are imperfectly aligned with real-world surfaces, either pushed in or pulled out.</span></span>

<span data-ttu-id="2d5c3-144">[Holograms를 삭제](environment-considerations-for-hololens.md) 하 고 공간을 다시 매핑하여 이러한 오류 중 상당수를 완화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d5c3-144">Many of these errors can be mitigated by [deleting your holograms](environment-considerations-for-hololens.md) and re-mapping the space.</span></span>