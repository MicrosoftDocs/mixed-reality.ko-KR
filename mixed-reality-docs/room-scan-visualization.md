---
title: 대화방 검색 시각화
description: 공간 매핑 데이터를 필요한 응용 프로그램에 자동으로 시간이 지남에 따라이 데이터를 수집 하려면 장치에 의존 하 고 사용자로 세션 전반에 걸쳐 활성 장치를 사용 하 여 해당 환경을 살펴봅니다.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality를 앱 패턴을 디자인, HoloLens, 공간 검색, 공간 재구성, 화면 매핑을 메시
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829908"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="f669a-104">대화방 검색 시각화</span><span class="sxs-lookup"><span data-stu-id="f669a-104">Room scan visualization</span></span>

<span data-ttu-id="f669a-105">공간 매핑 데이터를 필요한 응용 프로그램에 자동으로 시간이 지남에 따라이 데이터를 수집 하려면 장치에 의존 하 고 사용자로 세션 전반에 걸쳐 활성 장치를 사용 하 여 해당 환경을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="f669a-106">완성도이 데이터의 품질을 다양 한 사용자가 수행 하는 탐색, 탐색 이후 경과 된 시간은 어떻게 양과 장치 영역을 검색 하므로 가구 등 문 개체가 이동 하는지 여부를 비롯 한 요인에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="f669a-107">유용한 공간 매핑 데이터를 위해 응용 프로그램 개발자가 몇 가지 옵션이.</span><span class="sxs-lookup"><span data-stu-id="f669a-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="f669a-108">어떤 이미 수집 된 의존 합니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="f669a-109">이 데이터가 완전 하지 않을 처음입니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="f669a-110">홈 Windows Mixed Reality로 가져오고 다음 환경에 사용 하려는 영역을 탐색 bloom 제스처를 사용 하려면 사용자에 게 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="f669a-111">모든 필요한 영역 장치가 알려져 있는지 확인 하려면 어 탭을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="f669a-112">사용자 지정 탐색 경험을 자체 응용 프로그램을 빌드하십시오.</span><span class="sxs-lookup"><span data-stu-id="f669a-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="f669a-113">Note는 이러한 모든 경우에서 탐색 하는 동안 수집 되는 실제 데이터는 시스템으로 저장 되며 응용 프로그램에서이 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="f669a-114">장치 지원</span><span class="sxs-lookup"><span data-stu-id="f669a-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f669a-115"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="f669a-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f669a-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="f669a-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="f669a-117"><a href="immersive-headset-hardware-details.md"><strong>몰입 형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="f669a-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f669a-118">대화방 검색 시각화</span><span class="sxs-lookup"><span data-stu-id="f669a-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="f669a-119">✔️</span><span class="sxs-lookup"><span data-stu-id="f669a-119">✔️</span></span></td>
        <td><span data-ttu-id="f669a-120">❌</span><span class="sxs-lookup"><span data-stu-id="f669a-120">❌</span></span></td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="f669a-121">사용자 지정 검색 환경을 구축합니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-121">Building a custom scanning experience</span></span>

<span data-ttu-id="f669a-122">응용 프로그램은 해당 완결성과 품질을 개선 하기 위해 추가 단계를 수행 하려면 사용자 할지 판단에 환경 시작할 때 공간 매핑 데이터를 분석 하려면 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-122">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="f669a-123">분석 품질을 향상 시킬 수는 경우, 개발자는 시각화를 나타내기 위해 전 세계에 오버레이 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="f669a-124">환경의 일부가 되려면 얼마나 많은 사용자가 주변에 총 볼륨 필요</span><span class="sxs-lookup"><span data-stu-id="f669a-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="f669a-125">데이터를 개선 하기 위해 사용자가 이동 되어야 위치</span><span class="sxs-lookup"><span data-stu-id="f669a-125">Where the user should go to improve data</span></span>

<span data-ttu-id="f669a-126">사용자가 "good" 검색을 사용 하면 어떤 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-126">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="f669a-127">표시 되지 않거나 등 검색 – 직선 화 정도, 실제 벽에서의 거리를 계산 하도록 하는 경우 검색할 지시 해야 합니다. 개발자는 검색 또는 탐색 단계 동안 공간 매핑 데이터 새로 고침을 포함 하는 피드백 루프를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="f669a-128">대부분의 경우에 것이 사용자에 게 알리고 필요한지 않습니다 (예: 살펴보고 한계 조회 가구 뒤)를 가장 필요한 검사 품질을 얻기 위해.</span><span class="sxs-lookup"><span data-stu-id="f669a-128">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="f669a-129">연속 공간 매핑 및 캐시</span><span class="sxs-lookup"><span data-stu-id="f669a-129">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="f669a-130">공간 매핑 데이터는 데이터 원본 응용 프로그램에서 사용할 수 있는 가장 높은 가중치입니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-130">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="f669a-131">와 같은 성능 문제를 방지 하려면 프레임을 삭제 하거나 일지를이 데이터의 소비 해야 신중 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-131">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="f669a-132">유용 하거나 저하를 경험 하는 동안 active 검색 될 수 있습니다 및 개발자는 경험을 기반으로 사용할 방법을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-132">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="f669a-133">캐시 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="f669a-133">Cached spatial mapping</span></span>

<span data-ttu-id="f669a-134">캐시 공간 매핑의 경우 응용 프로그램은 일반적으로 공간 매핑 데이터의 스냅숏을 생성 하 고 환경의 기간에 대 한이 스냅숏을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-134">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="f669a-135">**이점**</span><span class="sxs-lookup"><span data-stu-id="f669a-135">**Benefits**</span></span>
* <span data-ttu-id="f669a-136">오버 헤드 감소 시스템에 큰 기능 열을 환경을 최고의 실행 하는 cpu 성능을 향상 하는 동안.</span><span class="sxs-lookup"><span data-stu-id="f669a-136">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="f669a-137">공간 데이터의 변경 하 여 중단 되지 하므로 주 경험의 간단한 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-137">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="f669a-138">단일 한 번에 물리학, 그래픽 및 기타 목적을 위해 공간 데이터의 사후 처리 비용입니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-138">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="f669a-139">**단점**</span><span class="sxs-lookup"><span data-stu-id="f669a-139">**Drawbacks**</span></span>
* <span data-ttu-id="f669a-140">캐시 된 데이터에서 실제 개체 또는 사용자의 이동을 반영 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-140">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="f669a-141">예를 들어</span><span class="sxs-lookup"><span data-stu-id="f669a-141">E.g.</span></span> <span data-ttu-id="f669a-142">응용 프로그램 문을 엽니다 때 고려할 실제로 닫히기 이제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-142">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="f669a-143">데이터의 캐시 된 버전을 유지 하기 위해 잠재적으로 더 많은 응용 프로그램 메모리입니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="f669a-144">이 메서드에 대 한 좋은 경우 통제 된 환경 인지 테이블 위쪽 게임을 합니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="f669a-145">연속 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="f669a-145">Continuous spatial mapping</span></span>

<span data-ttu-id="f669a-146">특정 응용 프로그램은 사용할 수 있습니다에 공간 매핑 데이터를 새로 고치려면 검색을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="f669a-147">**이점**</span><span class="sxs-lookup"><span data-stu-id="f669a-147">**Benefits**</span></span>
* <span data-ttu-id="f669a-148">별도 검색 또는 탐색 경험을 사전 응용 프로그램에 빌드할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="f669a-149">실제 개체의 이동은 약간의 지연이와 이지만 해당 게임에서 반영 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="f669a-150">**단점**</span><span class="sxs-lookup"><span data-stu-id="f669a-150">**Drawbacks**</span></span>
* <span data-ttu-id="f669a-151">기본 환경의 구현에서 더 높은 복잡성입니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="f669a-152">그래픽 또는 물리학 추가 처리를 증분 방식으로 이러한 시스템에서 수집 해야 하는 변경 내용으로 잠재적인 오버 헤드입니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-152">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="f669a-153">더 높은, 열 및 CPU 사용량</span><span class="sxs-lookup"><span data-stu-id="f669a-153">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="f669a-154">이 메서드에 대 한 좋은 경우 여기서 제공 해야 하는 예를 들어 holographic 자동차 현장에서 드라이브를 올바르게 열림 또는 닫힘 인지에 따라 도어에 범프 할 수 있는 개체를 이동 하는 상호 작용은 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="f669a-154">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="f669a-155">참조</span><span class="sxs-lookup"><span data-stu-id="f669a-155">See also</span></span>
* [<span data-ttu-id="f669a-156">공간 매핑 디자인</span><span class="sxs-lookup"><span data-stu-id="f669a-156">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="f669a-157">좌표계</span><span class="sxs-lookup"><span data-stu-id="f669a-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="f669a-158">공간 음향 디자인</span><span class="sxs-lookup"><span data-stu-id="f669a-158">Spatial sound design</span></span>](spatial-sound-design.md)
