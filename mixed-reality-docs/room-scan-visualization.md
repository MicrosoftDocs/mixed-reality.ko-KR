---
title: 대화방 스캔 시각화
description: 공간 매핑 데이터를 필요로 하는 응용 프로그램은 사용자가 장치를 활성화 하 여 환경을 탐색 하면서 시간 및 세션 간에이 데이터를 자동으로 수집 하는 장치에 의존 합니다.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 앱 패턴, 디자인, HoloLens, 회의실 검색, 공간 매핑, 메시
ms.openlocfilehash: bdb070407f27d04046bd022894c7a8a01b9658d1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437518"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="03e78-104">대화방 스캔 시각화</span><span class="sxs-lookup"><span data-stu-id="03e78-104">Room scan visualization</span></span>

<span data-ttu-id="03e78-105">공간 매핑 데이터를 필요로 하는 응용 프로그램은 사용자가 장치를 활성화 하 여 환경을 탐색 하면서 시간 및 세션 간에이 데이터를 자동으로 수집 하는 장치에 의존 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="03e78-106">이 데이터의 완성도와 품질은 사용자가 수행한 탐색 크기, 탐색 이후 경과 된 시간, 장치에서 영역을 스캔 한 후 가구 및 문과 같은 개체가 이동 했는지 여부를 포함 하는 다양 한 요인에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="03e78-107">유용한 공간 매핑 데이터를 보장 하기 위해 응용 프로그램 개발자는 다음과 같은 몇 가지 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="03e78-108">이미 수집 된 것을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="03e78-109">이 데이터는 처음에 완전 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="03e78-110">블 룸 제스처를 사용 하 여 Windows Mixed Reality 홈으로 이동한 다음 환경에 사용 하려는 영역을 탐색 하도록 사용자에 게 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="03e78-111">무선 탭을 사용 하 여 필요한 모든 영역이 장치에 알려져 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="03e78-112">자체 응용 프로그램에서 사용자 지정 탐색 환경을 구축 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="03e78-113">이러한 모든 경우 탐색 중에 수집 된 실제 데이터는 시스템에 의해 저장 되며 응용 프로그램에서이 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="03e78-114">장치 지원</span><span class="sxs-lookup"><span data-stu-id="03e78-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="03e78-115"><strong>기능과</strong></span><span class="sxs-lookup"><span data-stu-id="03e78-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="03e78-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="03e78-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="03e78-117"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="03e78-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="03e78-118">대화방 스캔 시각화</span><span class="sxs-lookup"><span data-stu-id="03e78-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="03e78-119">✔️</span><span class="sxs-lookup"><span data-stu-id="03e78-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="03e78-120">사용자 지정 스캔 환경 구축</span><span class="sxs-lookup"><span data-stu-id="03e78-120">Building a custom scanning experience</span></span>

<span data-ttu-id="03e78-121">응용 프로그램은 사용자가 추가 단계를 수행 하 여 완성도와 품질을 향상 시킬 것인지 여부를 판단 하기 위해 환경 시작 시 공간 매핑 데이터를 분석할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-121">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="03e78-122">분석에서 품질을 향상할 것으로 표시 하는 경우 개발자는 다음을 나타내기 위해 전 세계 오버레이에 대 한 시각화를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="03e78-123">사용자가 환경에 포함 해야 하는 총 볼륨의 양</span><span class="sxs-lookup"><span data-stu-id="03e78-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="03e78-124">사용자가 데이터 개선을 위해 이동 해야 하는 위치</span><span class="sxs-lookup"><span data-stu-id="03e78-124">Where the user should go to improve data</span></span>

<span data-ttu-id="03e78-125">사용자는 "좋은" 검색을 수행 하는 것을 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-125">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="03e78-126">검색을 평가 하도록 요청 하는 경우 (예를 들어 낮추면, 실제 벽 으로부터의 거리 등) 확인할 내용을 표시 하거나 표시 해야 합니다. 개발자는 검색 또는 탐색 단계 중 공간 매핑 데이터를 새로 고치는 작업을 포함 하는 피드백 루프를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="03e78-127">필요한 검색 품질을 얻기 위해 수행 해야 하는 작업을 사용자에 게 알리는 것이 가장 좋을 수 있습니다. 예를 들어 천장, 가구를 찾는 등의 작업을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-127">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="03e78-128">캐시 된 공간 및 연속 공간 간 매핑</span><span class="sxs-lookup"><span data-stu-id="03e78-128">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="03e78-129">공간 매핑 데이터는 데이터 원본 응용 프로그램에서 사용할 수 있는 가장 높은 가중치입니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-129">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="03e78-130">드롭된 프레임 또는 일지 같은 성능 문제를 방지 하려면이 데이터의 소비를 신중 하 게 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-130">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="03e78-131">환경에서의 활성 검색은 유용 하거나 나쁜 영향을 받을 수 있으며, 개발자는 환경을 기반으로 사용할 방법을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-131">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="03e78-132">캐시 된 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="03e78-132">Cached spatial mapping</span></span>

<span data-ttu-id="03e78-133">캐시 된 공간 매핑의 경우 응용 프로그램은 일반적으로 공간 매핑 데이터의 스냅숏을 사용 하 고 환경 기간 동안이 스냅숏을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-133">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="03e78-134">**혜택**</span><span class="sxs-lookup"><span data-stu-id="03e78-134">**Benefits**</span></span>
* <span data-ttu-id="03e78-135">경험을 실행 하는 동안 시스템에서 오버 헤드가 줄어들고 성능이 크게 향상 되 고 열 및 cpu 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-135">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="03e78-136">공간 데이터의 변경으로 인해 중단 되지 않으므로 기본 환경을 간단 하 게 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-136">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="03e78-137">물리학, 그래픽 및 기타 목적을 위해 공간 데이터의 post 처리에 대 한 단일 일회성 비용입니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-137">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="03e78-138">**단점**</span><span class="sxs-lookup"><span data-stu-id="03e78-138">**Drawbacks**</span></span>
* <span data-ttu-id="03e78-139">실제 개체 또는 사람들의 이동은 캐시 된 데이터에 의해 반영 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-139">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="03e78-140">예:</span><span class="sxs-lookup"><span data-stu-id="03e78-140">E.g.</span></span> <span data-ttu-id="03e78-141">응용 프로그램은 실제로 닫혀 있을 때 도어를 열어 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-141">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="03e78-142">캐시 된 버전의 데이터를 유지 관리 하기 위한 응용 프로그램 메모리가 더 많이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-142">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="03e78-143">이 메서드에 대 한 좋은 사례는 제어 되는 환경 또는 테이블 상위 게임입니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-143">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="03e78-144">연속 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="03e78-144">Continuous spatial mapping</span></span>

<span data-ttu-id="03e78-145">특정 응용 프로그램은 계속 검색을 사용 하 여 공간 매핑 데이터를 새로 고칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-145">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="03e78-146">**혜택**</span><span class="sxs-lookup"><span data-stu-id="03e78-146">**Benefits**</span></span>
* <span data-ttu-id="03e78-147">응용 프로그램에 대 한 별도의 검색 또는 탐색 환경에서 작성 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-147">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="03e78-148">실제 개체의 이동은 약간의 지연이 있지만 게임에서 반영할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-148">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="03e78-149">**단점**</span><span class="sxs-lookup"><span data-stu-id="03e78-149">**Drawbacks**</span></span>
* <span data-ttu-id="03e78-150">주요 환경 구현의 복잡성이 높아집니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-150">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="03e78-151">이러한 시스템에서 변경 내용을 증분 방식으로 수집 수 있도록 그래픽 또는 물리학의 추가 처리에 대 한 잠재적인 오버 헤드가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-151">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="03e78-152">높은 전원, 열 및 CPU 영향.</span><span class="sxs-lookup"><span data-stu-id="03e78-152">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="03e78-153">이 메서드에 대 한 좋은 사례는 holograms가 개체를 이동 하는 것으로 예상 되는 경우입니다. 예를 들어 바닥에서 구동 하는 holographic 자동차는 열려 있는지 닫혀 있는지에 따라 도어를 올바르게 전환 하려는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03e78-153">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="03e78-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="03e78-154">See also</span></span>
* [<span data-ttu-id="03e78-155">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="03e78-155">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="03e78-156">좌표계</span><span class="sxs-lookup"><span data-stu-id="03e78-156">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="03e78-157">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="03e78-157">Spatial sound design</span></span>](spatial-sound-design.md)
