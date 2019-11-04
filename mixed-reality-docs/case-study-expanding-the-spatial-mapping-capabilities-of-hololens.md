---
title: 사례 연구-HoloLens의 공간 매핑 기능 확장
description: Microsoft HoloLens에 대 한 첫 번째 앱을 만들 때 장치에서 공간 매핑의 경계를 푸시할 수 있는 정도를 확인 합니다.
author: jevertt
ms.author: jemccull
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, 공간 매핑
ms.openlocfilehash: 5142cb383d4408b29eb17eb5ede84d19b2533dc4
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73436728"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="a1648-104">사례 연구-HoloLens의 공간 매핑 기능 확장</span><span class="sxs-lookup"><span data-stu-id="a1648-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="a1648-105">Microsoft HoloLens에 대 한 첫 번째 앱을 만들 때 장치에서 공간 매핑의 경계를 푸시할 수 있는 정도를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="a1648-106">Microsoft 스튜디오의 소프트웨어 엔지니어 인 Jeff Evertt는 사용자의 실제 환경에 holograms가 배치 되는 방식을 보다 강력 하 게 제어할 필요가 없는 새 기술이 개발 된 방식을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

> [!NOTE]
> <span data-ttu-id="a1648-107">HoloLens 2는 environmentally 인식 응용 프로그램을 쉽게 개발할 수 있도록 설계 된 구조화 된 고급 환경 표현으로 혼합 현실 개발자를 제공 하는 새로운 [장면 이해 런타임을](scene-understanding.md)구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-107">HoloLens 2 implements a new [Scene Understanding Runtime](scene-understanding.md), that provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> 

## <a name="watch-the-video"></a><span data-ttu-id="a1648-108">비디오 시청</span><span class="sxs-lookup"><span data-stu-id="a1648-108">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="a1648-109">공간 매핑 초과</span><span class="sxs-lookup"><span data-stu-id="a1648-109">Beyond spatial mapping</span></span>

<span data-ttu-id="a1648-110">HoloLens [에 대](https://www.microsoft.com/p/fragments/9nblggh5ggm8) 한 첫 번째 게임 인 HoloLens와 [젊은 Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1)에서 작업 하는 동안, 실제 세계에서 holograms의 절차적 배치를 수행 하는 경우 사용자에 대 한 더 높은 수준의 이해를 요구 하 고 있습니다. 개발.</span><span class="sxs-lookup"><span data-stu-id="a1648-110">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="a1648-111">각 게임에는 고유한 특정 배치 요구 사항이 있습니다. 예를 들어 바닥 또는 테이블과 같은 여러 다른 표면을 구분 하 여 관련 위치에 대 한 단서를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-111">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="a1648-112">또한 holographic 문자 (예: 소파 또는 자)가 될 수 있는 화면을 식별할 수 있도록 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-112">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="a1648-113">젊은 Conker에서는 Conker와 자신의 상대가 플레이어의 방에서 발생 한 표면을 플랫폼으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-113">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="a1648-114">[Asobo 스튜디오](https://www.asobostudio.com/index.html), 이러한 게임을 위한 개발 파트너는이 문제를 해결 하 고 HoloLens의 공간 매핑 기능을 확장 하는 기술을 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-114">[Asobo Studios](https://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="a1648-115">이를 사용 하 여 플레이어의 방을 분석 하 고 벽, 테이블, 한도, 층 등의 표면을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-115">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="a1648-116">또한 제약 조건 집합에 대해 최적화 하 여 holographic 개체에 가장 적합 한 배치를 결정 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-116">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="a1648-117">공간 이해 코드</span><span class="sxs-lookup"><span data-stu-id="a1648-117">The spatial understanding code</span></span>

<span data-ttu-id="a1648-118">Asobo의 원래 코드를 작성 하 고이 기술을 캡슐화 하는 라이브러리를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-118">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="a1648-119">Microsoft 및 Asobo는 이제이 코드를 오픈 소스로 사용 하 여 사용자가 자신의 프로젝트에서 사용할 수 있도록 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) 에서 사용할 수 있게 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-119">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="a1648-120">모든 소스 코드가 포함 되어 있으므로 요구 사항에 맞게 사용자 지정 하 고 커뮤니티의 개선 사항을 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-120">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="a1648-121">C++ 해 찾기에 대 한 코드는 UWP DLL로 래핑되어 [MixedRealityToolkit 내에 포함 된 드롭 (prefab)](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding)을 사용 하 여 Unity에 노출 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-121">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="a1648-122">Unity 샘플에 포함 된 많은 유용한 쿼리를 사용 하 여 벽에서 빈 공간을 찾고, 바닥에 개체를 배치 하 고, 바닥에 개체를 배치 하 고, 사용할 문자 위치를 식별 하 고, 수많은 기타 공간을 이해 하는 쿼리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-122">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="a1648-123">HoloLens에서 제공 하는 공간 매핑 솔루션은 문제 공간의 전체 영역에 대 한 요구 사항을 충족 하기에 충분히 제네릭으로 설계 되었지만 공간 파악 모듈은 두 가지 특정 게임의 요구 사항을 지원 하도록 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-123">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="a1648-124">따라서 해당 솔루션은 특정 프로세스 및 가정 집합을 중심으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-124">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="a1648-125">**고정 크기 playspace**: 사용자가 init 호출에서 최대 playspace 크기를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-125">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="a1648-126">**일회성 검색 프로세스**:이 프로세스에는 사용자가 안내 하는 불연속 검색 단계가 필요 하며,이 단계는 playspace를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-126">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="a1648-127">검색이 완료 될 때까지 쿼리 함수가 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-127">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="a1648-128">**사용자 구동 재생 공간 "그리기"** : 검색 단계 중에 사용자가 플레이 공간을 이동 하 고 조회 하 여 포함 해야 하는 영역을 효과적으로 그릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-128">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="a1648-129">생성 된 메시는이 단계에서 사용자 의견을 제공 하는 데 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-129">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="a1648-130">**실내 홈 또는 office 설정**: 쿼리 함수는 평평한 서피스와 벽 주위에 직각으로 디자인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-130">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="a1648-131">소프트 제한입니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-131">This is a soft limitation.</span></span> <span data-ttu-id="a1648-132">그러나 검사 단계 중에 주 축 분석을 완료 하 여 주 및 보조 축을 따라 메시 공간 분할을 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-132">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="a1648-133">대화방 스캔 프로세스</span><span class="sxs-lookup"><span data-stu-id="a1648-133">Room Scanning Process</span></span>

<span data-ttu-id="a1648-134">공간 인식 모듈을 로드 하는 경우 가장 먼저 공간을 스캔 하 여 모든 사용 가능한 서피스 (예: 바닥, 천장 및 벽)를 식별 하 고 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-134">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="a1648-135">검색 프로세스 중에는 공간을 확인 하 고 검색에 포함 해야 하는 영역을 "페인트" 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-135">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="a1648-136">이 단계 중에 표시 되는 메시는 사용자가 검색 중인 대화방 부분을 알 수 있도록 하는 중요 한 시각적 피드백의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-136">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="a1648-137">공간 이해 모듈의 DLL은 내부적으로 playspace를 8cm 크기가 지정 된 voxel 큐브의 그리드로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-137">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="a1648-138">검색의 초기 부분에서 주 구성 요소 분석을 완료 하 여 방의 축을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-138">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="a1648-139">내부적으로 이러한 축에 맞춰진 voxel 공간을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-139">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="a1648-140">메시는 거의 매 초 마다 voxel 볼륨에서 isosurface를 추출 하 여 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-140">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![흰색의 공간 매핑 메시 및 녹색의 playspace 메시 이해](images/spatial-mapping-500px.png)

<span data-ttu-id="a1648-142">흰색의 공간 매핑 메시 및 녹색의 playspace 메시 이해</span><span class="sxs-lookup"><span data-stu-id="a1648-142">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="a1648-143">포함 된 SpatialUnderstanding.cs 파일은 검사 단계 프로세스를 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-143">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="a1648-144">다음 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-144">It calls the following functions:</span></span>
* <span data-ttu-id="a1648-145">**SpatialUnderstanding_Init**: 시작 시 한 번 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-145">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="a1648-146">**GeneratePlayspace_InitScan**: 검색 단계를 시작 해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-146">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="a1648-147">**GeneratePlayspace_UpdateScan_DynamicScan**: 검색 프로세스를 업데이트 하기 위해 각 프레임 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-147">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="a1648-148">카메라 위치와 방향이 전달 되며 위에 설명 된 playspace 그리기 프로세스에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-148">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="a1648-149">**GeneratePlayspace_RequestFinish**: playspace를 마무리 하기 위해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-149">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="a1648-150">이렇게 하면 검색 단계에서 "칠해진" 영역을 사용 하 여 playspace를 정의 하 고 잠급니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-150">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="a1648-151">응용 프로그램은 검색 단계 중에 통계를 쿼리할 수 있으며 사용자 의견을 제공 하기 위해 사용자 지정 메시를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-151">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="a1648-152">**Import_UnderstandingMesh**: 검색 하는 동안 모듈에서 제공 하는 **SpatialUnderstandingCustomMesh** 동작을 이해 하는 데에는 프로세스에 의해 생성 된 사용자 지정 메쉬가 정기적으로 쿼리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-152">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="a1648-153">그리고 검사가 완료 된 후에도이 작업이 한 번 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-153">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="a1648-154">**SpatialUnderstanding** 동작으로 구동 되는 검색 흐름은 **initscan**을 호출한 다음 각 프레임을 **UpdateScan** 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-154">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="a1648-155">통계 쿼리가 적절 한 검사 범위를 보고할 때 사용자는 **Requestfinish** 를 호출 하 여 검색 단계의 끝을 나타내는 탭을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-155">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="a1648-156">**UpdateScan** 는 반환 값이 DLL 처리를 완료 했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-156">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="a1648-157">쿼리</span><span class="sxs-lookup"><span data-stu-id="a1648-157">The queries</span></span>

<span data-ttu-id="a1648-158">검색이 완료 되 면 다음 세 가지 유형의 쿼리를 인터페이스에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-158">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="a1648-159">**토폴로지 쿼리**: 검색 된 대화방의 토폴로지를 기반으로 하는 빠른 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-159">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="a1648-160">**셰이프 쿼리**: 이러한 작업은 사용자가 정의 하는 사용자 지정 셰이프와 잘 일치 하는 가로 표면을 찾기 위해 토폴로지 쿼리 결과를 활용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-160">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="a1648-161">**개체 배치 쿼리**: 이러한 쿼리는 개체에 대 한 규칙 및 제약 조건 집합을 기반으로 최적 위치를 찾는 보다 복잡 한 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-161">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="a1648-162">세 가지 기본 쿼리 외에도 태그가 지정 된 서피스 형식을 검색 하는 데 사용할 수 있는 raycasting 인터페이스와 사용자 지정 watertight 대화방 메쉬가 복사 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-162">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="a1648-163">토폴로지 쿼리</span><span class="sxs-lookup"><span data-stu-id="a1648-163">Topology queries</span></span>

<span data-ttu-id="a1648-164">DLL 내에서 토폴로지 관리자는 환경의 레이블 지정을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-164">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="a1648-165">위에서 언급 한 것 처럼 대부분의 데이터는 voxel 볼륨 내에 포함 된 surfels 내에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-165">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="a1648-166">또한 **PlaySpaceInfos** 구조체를 사용 하 여 전 세계 맞춤 (아래에 자세히 설명), 층 및 천장 높이를 포함 하 여 playspace에 대 한 정보를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-166">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="a1648-167">추론은 바닥, 천장 및 벽을 결정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-167">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="a1648-168">예를 들어 1 개의 m2 노출 영역이 있는 가장 크고 가장 작은 가로 표면은 바닥으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-168">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="a1648-169">검색 프로세스 중에 카메라 경로도이 프로세스에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-169">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="a1648-170">토폴로지 관리자에 의해 노출 되는 쿼리의 하위 집합은 DLL을 통해 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-170">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="a1648-171">노출 된 토폴로지 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-171">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="a1648-172">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="a1648-172">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="a1648-173">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="a1648-173">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="a1648-174">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="a1648-174">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="a1648-175">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="a1648-175">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="a1648-176">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="a1648-176">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="a1648-177">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="a1648-177">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="a1648-178">각 쿼리에는 쿼리 유형과 관련 된 매개 변수 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-178">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="a1648-179">다음 예에서는 사용자가 원하는 볼륨의 최소 높이 & 너비, 바닥의 최소 배치 높이 및 볼륨 앞에 있는 최소 여유 공간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-179">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="a1648-180">모든 측정이 미터 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-180">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="a1648-181">이러한 각 쿼리는 미리 할당 된 **TopologyResult** 구조체 배열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-181">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="a1648-182">**Locationcount** 매개 변수는 전달 된 배열의 길이를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-182">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="a1648-183">반환 값은 반환 된 위치 수를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-183">The return value reports the number of returned locations.</span></span> <span data-ttu-id="a1648-184">이 수는 전달 된 **Locationcount** 매개 변수 보다 크지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-184">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="a1648-185">**TopologyResult** 에는 반환 된 볼륨의 중심 위치, 방향 (예: 일반) 및 찾은 공간의 크기가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-185">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="a1648-186">Unity 샘플에서 이러한 각 쿼리는 가상 UI 패널의 단추에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-186">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="a1648-187">샘플에서는 이러한 각 쿼리에 대 한 매개 변수를 적절 한 값으로 하드 코드 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-187">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="a1648-188">더 많은 예제는 샘플 코드의 *SpaceVisualizer.cs* 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a1648-188">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="a1648-189">셰이프 쿼리</span><span class="sxs-lookup"><span data-stu-id="a1648-189">Shape queries</span></span>

<span data-ttu-id="a1648-190">DLL 내에서 shape analyzer (**ShapeAnalyzer_W**)는 토폴로지 분석기를 사용 하 여 사용자가 정의한 사용자 지정 셰이프와 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-190">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="a1648-191">Unity 샘플에는 쿼리 메뉴의 셰이프 탭에 표시 되는 미리 정의 된 셰이프 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-191">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="a1648-192">셰이프 분석은 가로 표면 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-192">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="a1648-193">예를 들어, 소파는 평평한 좌석 표면 및 소파 위쪽의 평면에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-193">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="a1648-194">셰이프 쿼리는 두 개의 서피스가 정렬 되 고 연결 된 특정 크기, 높이 및 가로 세로 막대의 두 표면을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-194">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="a1648-195">Api 용어를 사용 하 여 소파와 소파의 위쪽은 셰이프 구성 요소 이며 맞춤 요구 사항은 셰이프 구성 요소 제약 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-195">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="a1648-196">"Sittable" 개체에 대 한 Unity 샘플 (**ShapeDefinition.cs**)에 정의 된 예제 쿼리는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-196">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




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

<span data-ttu-id="a1648-197">각 셰이프 쿼리는 각각 구성 요소 제약 조건 집합과 구성 요소 간의 종속성을 나열 하는 셰이프 제약 조건 집합을 포함 하는 도형 구성 요소 집합으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-197">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="a1648-198">이 예에는 단일 구성 요소 정의에 세 개의 제약 조건이 포함 되 고 구성 요소 간의 모양 제약 조건 (구성 요소 하나만 있는 경우)이 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-198">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="a1648-199">이와 대조적으로, 소파 셰이프에는 두 개의 셰이프 구성 요소와 4 개의 셰이프 제약 조건이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-199">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="a1648-200">구성 요소는 사용자의 구성 요소 목록에서 인덱스로 식별 됩니다 (이 예제에서는 0 및 1).</span><span class="sxs-lookup"><span data-stu-id="a1648-200">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="a1648-201">래퍼 함수는 사용자 지정 셰이프 정의를 쉽게 만들기 위해 Unity 모듈에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-201">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="a1648-202">구성 요소 및 모양 제약 조건의 전체 목록은 **ShapeComponentConstraint** 및 **ShapeConstraint** 구조 내의 **SpatialUnderstandingDll.cs** 에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-202">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![파란색 사각형은가 중 셰이프 쿼리의 결과를 강조 표시 합니다.](images/chair-shape-query-500px.png)

<span data-ttu-id="a1648-204">파란색 사각형은가 중 셰이프 쿼리의 결과를 강조 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-204">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="a1648-205">개체 배치 해 찾기</span><span class="sxs-lookup"><span data-stu-id="a1648-205">Object placement solver</span></span>

<span data-ttu-id="a1648-206">개체 배치 쿼리를 사용 하 여 실제 방에 있는 이상적인 위치를 식별 하 여 개체를 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-206">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="a1648-207">개체 규칙 및 제약 조건이 지정 된 경우 해 찾기가 최적 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-207">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="a1648-208">또한 **Solver_RemoveObject** 또는 **Solver_RemoveAllObjects** 호출을 통해 개체가 제거 될 때까지 개체 쿼리를 유지 하 여 제한 된 다중 개체 배치를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-208">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="a1648-209">개체 배치 쿼리는 매개 변수가 있는 배치 유형, 규칙 목록 및 제약 조건 목록의 세 부분으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-209">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="a1648-210">쿼리를 실행 하려면 다음 API를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-210">To run a query, use the following API:</span></span>




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
<span data-ttu-id="a1648-211">이 함수는 개체 이름, 배치 정의 및 규칙 및 제약 조건 목록을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-211">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="a1648-212">래퍼 C# 는 규칙 및 제약 조건 생성을 용이 하 게 하는 생성 도우미 함수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-212">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="a1648-213">배치 정의에는 쿼리 유형 즉, 다음 중 하나를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-213">The placement definition contains the query type — that is, one of the following:</span></span>




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

<span data-ttu-id="a1648-214">각 배치 형식에는 해당 형식에 고유한 매개 변수 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-214">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="a1648-215">**Objectplacementdefinition** 구조에는 이러한 정의를 만들기 위한 정적 도우미 함수 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-215">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="a1648-216">예를 들어 개체를 바닥에 배치할 위치를 찾으려면 다음 함수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-216">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="a1648-217">배치 유형 외에도 규칙 및 제약 조건 집합을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-217">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="a1648-218">규칙을 위반할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-218">Rules cannot be violated.</span></span> <span data-ttu-id="a1648-219">그러면 형식 및 규칙을 충족 하는 가능한 배치 위치가 제약 조건 집합에 대해 최적화 되어 최적의 배치 위치를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-219">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="a1648-220">제공 된 정적 생성 함수를 통해 각 규칙 및 제약 조건을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-220">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="a1648-221">아래에는 규칙 및 제약 조건 생성 함수 예제가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-221">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="a1648-222">아래의 개체 배치 쿼리는 이전에 배치 된 다른 개체와 대화방의 가운데 근처에서 절반 측정기 큐브를 표면의 가장자리에 배치 하는 위치를 찾고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-222">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




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

<span data-ttu-id="a1648-223">성공 하면 배치 위치, 차원 및 방향을 포함 하는 **Objectplacementresult** 구조가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-223">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="a1648-224">또한 배치가 배치 된 개체의 내부 목록에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-224">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="a1648-225">이후 배치 쿼리에서는이 개체를 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-225">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="a1648-226">Unity 샘플의 **LevelSolver.cs** 파일에는 더 많은 예제 쿼리가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-226">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![파란색 상자는 "카메라 위치에서 멀리" 규칙을 사용 하 여 바닥 쿼리의 세 위치에서 발생 한 결과를 보여 줍니다.](images/away-from-camera-position-500px.png)

<span data-ttu-id="a1648-228">파란색 상자는 "카메라 위치에서 멀리" 규칙을 사용 하 여 바닥 쿼리의 세 위치에서 발생 한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-228">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="a1648-229">**팁**</span><span class="sxs-lookup"><span data-stu-id="a1648-229">**Tips:**</span></span>
* <span data-ttu-id="a1648-230">수준 또는 응용 프로그램 시나리오에 필요한 여러 개체의 배치 위치를 해결 하는 경우 먼저 필수적인 개체와 대량 개체를 해결 하 여 공간을 찾을 수 있는 확률을 최대화 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-230">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="a1648-231">배치 순서는 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-231">Placement order is important.</span></span> <span data-ttu-id="a1648-232">개체 배치를 찾을 수 없는 경우 제한 된 구성으로 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-232">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="a1648-233">여러 방 구성에서 기능을 지원 하려면 대체 (fallback) 구성 집합이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-233">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="a1648-234">광선 캐스팅</span><span class="sxs-lookup"><span data-stu-id="a1648-234">Ray casting</span></span>

<span data-ttu-id="a1648-235">세 가지 기본 쿼리 외에도, 광선 캐스팅 인터페이스를 사용 하 여 태그가 지정 된 서피스 형식을 검색 하 고, 방을 검색 하 고 완료 한 후에 사용자 지정 watertight playspace 메시를 복사할 수 있습니다. 레이블은 다음과 같은 표면에 대해 내부적으로 생성 됩니다. 바닥, 천장 및 벽입니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-235">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="a1648-236">**PlayspaceRaycast** 함수는 광선이 알려진 표면과 충돌 하는 경우를 반환 하 고, 해당 하는 경우에는 **RaycastResult**형식으로 해당 화면에 대 한 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-236">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


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

<span data-ttu-id="a1648-237">내부적으로 raycast는 playspace의 계산 된 8cm 제곱 voxel 표현에 대해 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-237">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="a1648-238">각 voxel에는 처리 된 토폴로지 데이터 (surfels 라고도 함)를 포함 하는 surface 요소 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-238">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="a1648-239">교차 된 voxel 셀에 포함 된 surfels는 토폴로지 정보를 조회 하는 데 사용 되는 가장 일치 하는 항목과 비교 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-239">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="a1648-240">이 토폴로지 데이터에는 교차 된 표면의 노출 영역 뿐만 아니라 **SurfaceTypes** 열거형 형식으로 반환 되는 레이블 지정이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-240">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="a1648-241">Unity 샘플에서 커서는 각 프레임을 비춥니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-241">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="a1648-242">첫째, Unity의 colliders에 대해 둘째, 모듈의 세계 표현 이해 마지막으로 UI 요소를 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-242">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="a1648-243">이 응용 프로그램에서 UI는 우선 순위, 이해 결과 및 마지막으로 Unity의 colliders를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-243">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="a1648-244">**SurfaceType** 은 커서 옆에 텍스트로 보고 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-244">The **SurfaceType** is reported as text next to the cursor.</span></span>

![바닥과의 교차점을 보고 하는 raycast 결과](images/raycast-result-500px.jpg)

<span data-ttu-id="a1648-246">바닥과의 교차점을 보고 하는 raycast 결과</span><span class="sxs-lookup"><span data-stu-id="a1648-246">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="a1648-247">코드 다운로드</span><span class="sxs-lookup"><span data-stu-id="a1648-247">Get the code</span></span>

<span data-ttu-id="a1648-248">오픈 소스 코드는 [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-248">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="a1648-249">프로젝트에서 코드를 사용 하는 경우 [HoloLens 개발자 포럼](https://forums.hololens.com/) 을 통해 알려주세요.</span><span class="sxs-lookup"><span data-stu-id="a1648-249">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="a1648-250">작업을 확인할 때까지 기다릴 수 없습니다!</span><span class="sxs-lookup"><span data-stu-id="a1648-250">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="a1648-251">작성자 정보</span><span class="sxs-lookup"><span data-stu-id="a1648-251">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="a1648-252"><b>Jeff Evertt</b> 는 인큐베이션부터 경험 개발까지 이전 며칠 이후 HoloLens에 대해 작업 한 소프트웨어 엔지니어링 리드입니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-252"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="a1648-253">HoloLens 이전에는 다양 한 플랫폼 및 게임의 Xbox Kinect 및 게임 업계에서 작업 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-253">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="a1648-254">Jeff는 경고음이 들리고 현란한 광원을 사용 하는 로봇, 그래픽 및 사물에 대 한 열정적인입니다.</span><span class="sxs-lookup"><span data-stu-id="a1648-254">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="a1648-255">그는 새로운 작업을 배우고 소프트웨어, 하드웨어, 특히 두 부분이 교차 하는 공간에서 작업 하는 것을 활용할.</span><span class="sxs-lookup"><span data-stu-id="a1648-255">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="a1648-256">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1648-256">See also</span></span>
* [<span data-ttu-id="a1648-257">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="a1648-257">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="a1648-258">장면 이해</span><span class="sxs-lookup"><span data-stu-id="a1648-258">Scene understanding</span></span>](scene-understanding.md)
* [<span data-ttu-id="a1648-259">실내 스캔 시각화</span><span class="sxs-lookup"><span data-stu-id="a1648-259">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="a1648-260">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="a1648-260">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="a1648-261">Asobo 스튜디오: HoloLens 개발 frontline의 단원</span><span class="sxs-lookup"><span data-stu-id="a1648-261">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](https://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
