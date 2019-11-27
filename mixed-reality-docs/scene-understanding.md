---
title: 장면 이해
description: HoloLens의 장면 이해 기능 소개
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: 장면 이해, 공간 매핑, Windows Mixed Reality, Unity
ms.openlocfilehash: bacec5e6a9bfda49d4ad6d3dd849156c9cc09add
ms.sourcegitcommit: 83698638b93c5ba77b3ffc399f1706482539f27b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74539700"
---
# <a name="scene-understanding"></a><span data-ttu-id="b08a2-104">장면 이해</span><span class="sxs-lookup"><span data-stu-id="b08a2-104">Scene understanding</span></span>

<span data-ttu-id="b08a2-105">장면 이해는 environmentally 인식 응용 프로그램을 쉽게 개발할 수 있도록 설계 된 구조적인 고급 환경 표현을 포함 하는 혼합 현실 개발자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-105">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="b08a2-106">장면 이해는 매우 정확 하 고 구조화 되지 않은 [공간 매핑과](spatial-mapping.md) 새로운 AI 기반 런타임과 같이 기존의 혼합 현실 런타임의 강력한 기능을 결합 하 여이를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-106">Scene understanding does this by combining the power of existing mixed reality runtimes such as the highly accurate less structured [spatial mapping](spatial-mapping.md) and new AI driven runtimes.</span></span> <span data-ttu-id="b08a2-107">이러한 기술을 결합 하 여 장면 이해는 Unity 또는 ARKit/Arkit와 같은 프레임 워크에서 사용한 것과 유사한 3D 환경의 표현을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-107">By combining these technologies, Scene understanding generates representations of 3D environments that are similar to those you may have used in frameworks such as Unity or ARKit/ARCore.</span></span> <span data-ttu-id="b08a2-108">장면 이해 진입점은 새 장면을 계산 하기 위해 응용 프로그램에서 호출 하는 장면 관찰자로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-108">The Scene understanding entry point begins with a Scene Observer which is called by your application to compute a new scene.</span></span> <span data-ttu-id="b08a2-109">현재이 기술은 3 가지 고유 하지만 관련 개체 범주를 생성할 수 있습니다. 간소화 된 watertight 환경 메시: 간소화 된 평면 영역 구조를 유추 하 고 Quads를 호출 하는 배치를 위한 평면 영역 및의 [스냅숏을 만듭니다. ](spatial-mapping.md)노출 되는 Quads/Watertight 데이터에 맞는 공간 매핑 메시입니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-109">Today the technology is capable of generating 3 distinct but related object categories: simplified watertight environment meshes that infer the planar room structure without clutter, plane regions for placement that we call Quads, and a snapshot of the [spatial mapping](spatial-mapping.md) mesh that aligns with the Quads/Watertight data that we surface.</span></span>

![공간 매핑 메시, 레이블이 지정 된 평면 표면, watertight 메시](images/SUScenarios.png)

<span data-ttu-id="b08a2-111">이 문서는 시나리오 개요를 제공 하 고 장면 이해 및 공간 매핑 공유의 관계를 명확 하 게 설명 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-111">This document is intended to provide a scenario overview and to clarify the relationship that Scene understanding and Spatial mapping share.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="b08a2-112">장면 이해로 개발</span><span class="sxs-lookup"><span data-stu-id="b08a2-112">Developing with Scene Understanding</span></span>

<span data-ttu-id="b08a2-113">이 문서에서는 런타임 및 개념을 이해 하는 데만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-113">This article only serves to introduce the Scene Understanding runtime and concepts.</span></span> <span data-ttu-id="b08a2-114">장면 이해를 통해 개발 하는 방법에 대 한 설명서를 찾으려는 경우 다음에 관심이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-114">If you are looking for documentation on how to develop with Scene Understanding you may be interested in the following:</span></span>

[<span data-ttu-id="b08a2-115">장면 이해 SDK 개요</span><span class="sxs-lookup"><span data-stu-id="b08a2-115">Scene Understanding SDK overview</span></span>](scene-understanding-SDK.md)

<span data-ttu-id="b08a2-116">샘플 GitHub 사이트에서 장면 이해 샘플 앱을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-116">You can download the Scene Understanding Sample app from the sample GitHub site:</span></span>

[<span data-ttu-id="b08a2-117">장면 이해 샘플</span><span class="sxs-lookup"><span data-stu-id="b08a2-117">Scene Understanding Sample</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample)

<span data-ttu-id="b08a2-118">장치를 사용 하지 않고 장면 이해를 시도 하기 위해 샘플 장면에 액세스 하려는 경우 샘플 자산 폴더에는 장면이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-118">If you do not have a device and wish to access sample scenes to try Scene Understanding out, there are scenes in the sample asset folder:</span></span>

[<span data-ttu-id="b08a2-119">장면 이해 샘플 장면</span><span class="sxs-lookup"><span data-stu-id="b08a2-119">Scene Understanding Sample Scenes</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a><span data-ttu-id="b08a2-120">SDK</span><span class="sxs-lookup"><span data-stu-id="b08a2-120">SDK</span></span>

<span data-ttu-id="b08a2-121">장면 Understandiing를 개발 하는 방법에 대 한 자세한 내용은 장면 이해의 작동 방식 및이에 대해 개발 하는 방법에 대 한 세부 정보를 보려면 [장면 이해 SDK 개요](scene-understanding-SDK.md) 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b08a2-121">If you are looking for  specific details on how to develop for Scene Understandiing, For details on how Scene understanding works and how to develop for it, please see the [Scene Understanding SDK overview](scene-understanding-SDK.md) documentation.</span></span>


### <a name="sample"></a><span data-ttu-id="b08a2-122">샘플</span><span class="sxs-lookup"><span data-stu-id="b08a2-122">Sample</span></span>


## <a name="device-support"></a><span data-ttu-id="b08a2-123">장치 지원</span><span class="sxs-lookup"><span data-stu-id="b08a2-123">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b08a2-124"><strong>기능과</strong></span><span class="sxs-lookup"><span data-stu-id="b08a2-124"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b08a2-125"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b08a2-125"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b08a2-126"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b08a2-126"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b08a2-127"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="b08a2-127"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b08a2-128">장면 이해</span><span class="sxs-lookup"><span data-stu-id="b08a2-128">Scene understanding</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="b08a2-129">✔️</span><span class="sxs-lookup"><span data-stu-id="b08a2-129">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a><span data-ttu-id="b08a2-130">일반 시나리오</span><span class="sxs-lookup"><span data-stu-id="b08a2-130">Common usage scenarios</span></span>

<span data-ttu-id="b08a2-131">![일반적인 공간 매핑 사용 시나리오의 그림: 배치, 폐색, 물리 및 탐색](images/sm-concepts-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="b08a2-131">![Illustrations of common Spatial mapping usage scenarios: Placement, Occlusion, Physics and Navigation](images/sm-concepts-1000px.png)</span></span><br>
<span data-ttu-id="b08a2-132">*일반적인 공간 매핑 사용 시나리오: 배치, 폐색, 물리 및 탐색.*</span><span class="sxs-lookup"><span data-stu-id="b08a2-132">*Common spatial mapping usage scenarios: placement, occlusion, physics and navigation.*</span></span>

<br>

<span data-ttu-id="b08a2-133">환경 인식 응용 프로그램 (배치, 폐색, 물리 등)에 대 한 핵심 시나리오의 대부분은 공간 매핑과 장면 이해를 통해 주소를 지정할 수 있습니다 .이 섹션에서는 이러한 차이를 강조 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-133">Many of the core scenarios for environment aware applications (placement, occlusion, physics, etc.) are addressable by both Spatial mapping and Scene understanding, this section highlights these differences.</span></span> <span data-ttu-id="b08a2-134">장면 이해와 공간 매핑의 핵심 차이점은 최대 정확성과 구조 및 단순성의 대기 시간에 대 한 균형입니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-134">A core difference between Scene understanding and Spatial mapping is a tradeoff of maximal accuracy and latency to structure and simplicity.</span></span> <span data-ttu-id="b08a2-135">응용 프로그램에서 가능한 가장 낮은 대기 시간을 필요로 하 고 메시 삼각형만 필요한 경우에는 공간 매핑에 직접 액세스 해야 합니다. 그러나 더 높은 수준의 처리를 수행 하는 경우에는 장면 이해 모델로 전환 하는 것을 고려할 수 있습니다. 는 기능의 상위 집합을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-135">If your application requires the lowest-latency possible and requires mesh triangles only you will want to access Spatial Mapping directly, however if you are performing higher level processing you may consider switching to the Scene understanding model as it should provide you with a superset of functionality.</span></span> <span data-ttu-id="b08a2-136">또한 장면 이해에서는 공간 매핑 메시를 표현의 일부로 제공 하므로 항상 가장 완전 하 고 정확한 공간 매핑 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-136">Also note, that because Scene understanding provides the spatial mapping mesh as part of its representation, you will always have access to the most complete and accurate spatial mapping data possible.</span></span>

 <span data-ttu-id="b08a2-137">다음 섹션에서는 새 장면 이해 SDK의 컨텍스트에서 핵심 공간 매핑 시나리오를 다시 방문 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-137">The following sections re-visit the core spatial mapping scenarios in the context of the new Scene understanding SDK.</span></span>

### <a name="placement"></a><span data-ttu-id="b08a2-138">배치</span><span class="sxs-lookup"><span data-stu-id="b08a2-138">Placement</span></span>

<span data-ttu-id="b08a2-139">장면 이해에서는 배치 시나리오를 간소화 하기 위해 특별히 설계 된 새 구문을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-139">Scene understanding provides new constructs specifically designed to simplify placement scenarios.</span></span> <span data-ttu-id="b08a2-140">장면은 holograms을 배치할 수 있는 플랫 표면을 설명 하는 SceneQuads 라는 기본 형식을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-140">A scene can compute primitives called SceneQuads which describe flat surfaces on which holograms can be placed.</span></span> <span data-ttu-id="b08a2-141">SceneQuads는 특별히 배치를 중심으로 디자인 되었으며 2D 표면을 설명 하 고 해당 화면에 배치 하기 위한 API를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-141">SceneQuads have specifically been designed around placement and describe a 2D surface and provide an API for placement on that surface.</span></span> <span data-ttu-id="b08a2-142">이전에는 삼각형 메시를 사용 하 여 배치를 수행할 때 쿼드의 모든 영역을 검색 하 고 구멍 채우기/사후 처리를 수행 하 여 개체 배치를 위한 좋은 위치를 확인 해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-142">Previously, when using the triangle mesh to perform placement, one had to scan all areas of the quad and perform hole filling/post-processing to identify good locations for object placement.</span></span> <span data-ttu-id="b08a2-143">장면 이해 런타임은 스캔 되지 않은 쿼드 영역을 유추 하 고 표면의 일부가 아닌 쿼드 영역을 무효화 하는 데 사용할 수 있으므로 Quads에는 항상 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-143">This is not always necessary with Quads, as the Scene understanding runtime is capable of inferring which areas of the quad that were not scanned, and invalidate areas of the quad that are not part of the surface.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="b08a2-144">유추를 사용 하지 않도록 설정 하 고, 스캔 된 영역에 대 한 배치 영역을 SceneQuads ![.](images/SUQuads.png)</span><span class="sxs-lookup"><span data-stu-id="b08a2-144">![SceneQuads with inference disabled, capturing placement areas for scanned regions.](images/SUQuads.png)</span></span><br>
       <span data-ttu-id="b08a2-145">**이미지 #1** -유추가 사용 하지 않도록 설정 된 SceneQuads, 스캔 한 영역에 대 한 배치 영역 캡처</span><span class="sxs-lookup"><span data-stu-id="b08a2-145">**Image #1** - SceneQuads with inference disabled, capturing placement areas for scanned regions.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="b08a2-146">유추를 사용 하는 ![Quads는 더 이상 스캔 된 영역으로 제한 되지 않습니다.](images/SUWatertight.png)</span><span class="sxs-lookup"><span data-stu-id="b08a2-146">![Quads with inference enabled, placement is no longer limited to scanned areas.](images/SUWatertight.png)</span></span><br>
        <span data-ttu-id="b08a2-147">**이미지 #2** -유추를 사용 하도록 설정 하면 배치가 더 이상 스캔 된 영역으로 제한 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-147">**Image #2** - Quads with inference enabled, placement is no longer limited to scanned areas.</span></span>
    :::column-end:::
:::row-end:::

<br>


<span data-ttu-id="b08a2-148">응용 프로그램에서 2D 또는 3D holograms를 환경의 고정 구조에 배치 하려는 경우 배치를 위한 SceneQuads의 단순성과 편의성은 [공간 매핑](spatial-mapping.md) 메시에서이 정보를 계산 하는 것 보다 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-148">If your application intends to place 2D or 3D holograms on rigid structures of your environment, the simplicity and convenience of SceneQuads for placement is preferable to computing this information from the [spatial mapping](spatial-mapping.md) mesh.</span></span> <span data-ttu-id="b08a2-149">이 항목에 대 한 자세한 내용은 참조 [장면 이해 SDK 참조](scene-understanding-SDK.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b08a2-149">For more details on this topic, please see the [Scene understanding SDK reference](scene-understanding-SDK.md)</span></span>

<span data-ttu-id="b08a2-150">**참고** 공간 매핑 메시에 의존 하는 레거시 배치 코드의 경우 EnableWorldMesh 설정을 설정 하 여 SceneQuads와 함께 공간 매핑 메시를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-150">**Note** For legacy placement code that depends on the spatial mapping mesh, the spatial mapping mesh can be computed along with SceneQuads by setting EnableWorldMesh setting.</span></span> <span data-ttu-id="b08a2-151">장면 이해 API가 응용 프로그램의 대기 시간 요구 사항에 맞지 않는 경우 [공간 매핑 api](spatial-mapping.md#placement)를 계속 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-151">If Scene understanding API does not satisfy your application's latency requirements, we recommend you continue to use the [Spatial mapping API](spatial-mapping.md#placement).</span></span>

### <a name="occlusion"></a><span data-ttu-id="b08a2-152">폐색</span><span class="sxs-lookup"><span data-stu-id="b08a2-152">Occlusion</span></span>

<span data-ttu-id="b08a2-153">[공간 매핑 폐색](spatial-mapping.md#occlusion) 환경의 실시간 상태를 캡처하는 가장 낮은 방법으로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-153">[Spatial mapping occlusion](spatial-mapping.md#occlusion) remains the least latent way to capture the real-time state of the environment.</span></span> <span data-ttu-id="b08a2-154">이는 매우 동적인 장면에서 폐색을 제공 하는 데 유용할 수 있지만 여러 가지 이유로 폐색에 대 한 장면 이해를 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-154">Though this may be useful to provide occlusion in highly dynamic scenes, you may wish to consider Scene understanding for occlusion for several reasons.</span></span> <span data-ttu-id="b08a2-155">장면 이해로 생성 된 공간 매핑 메시를 사용 하는 경우 로컬 캐시에 저장 되지 않으므로 인식 Api에서 사용할 수 없는 공간 매핑에서 데이터를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-155">If you use the spatial mapping mesh generated by Scene Understanding you can request data from spatial mapping that would not be stored in the local cache and therefore not available to you from the perception APIs.</span></span> <span data-ttu-id="b08a2-156">Watertight 메시와 함께 폐색에 대 한 공간 매핑을 사용 하면 특히 스캔 되지 않은 대화방 구조를 완료 하는 추가 값이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-156">Using Spatial Mapping for occlusion alongside watertight meshes will provide additional value, specifically completion of un-scanned room structure.</span></span>

<span data-ttu-id="b08a2-157">요구 사항에 따라 장면 이해의 대기 시간이 길어질 수 있는 경우, 응용 프로그램 개발자는 장면 이해 watertight 메시를 사용 하 고 한꺼번에의 공간 매핑 메시를 평면 표현과 함께 사용 하는 것을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-157">If your requirements can tolerate the increased latency of Scene understanding, application developers should consider using the Scene understanding watertight mesh, and presumably the spatial mapping mesh in unison with planar representations.</span></span> <span data-ttu-id="b08a2-158">이를 통해 간소화 된 watertight 폐색는 가장 현실적인 폐색 지도를 제공 하는 보다 정교한 nonplanar 기 하 도형으로 결혼 하는 "두 가지 세계 모두"를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-158">This would provide a "best of both worlds" where simplified watertight occlusion is married with finer nonplanar geometry providing the most realistic occlusion maps possible.</span></span>

### <a name="physics"></a><span data-ttu-id="b08a2-159">물리</span><span class="sxs-lookup"><span data-stu-id="b08a2-159">Physics</span></span>

<span data-ttu-id="b08a2-160">장면 이해에서는 공간 매핑 메시가 적용 하는 물리의 많은 제한 사항을 처리 하는 의미 체계를 사용 하 여 공간을 분해 하는 watertight 메시를 생성 합니다</span><span class="sxs-lookup"><span data-stu-id="b08a2-160">Scene understanding generates watertight meshes that decompose space with semantics specifically to address many limitations to physics that spatial mapping meshes impose.</span></span> <span data-ttu-id="b08a2-161">Watertight 구조체를 사용 하면 물리학 광선 캐스팅이 항상 적중 되며, 의미 체계 분해를 통해 실내 탐색을 위한 탐색 메시를 보다 간단 하 게 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-161">Watertight structures ensure physics ray casts always hit, and semantic decomposition allows for simpler generation of nav meshes for indoor navigation.</span></span> <span data-ttu-id="b08a2-162">[폐색](#occlusion) 섹션에서 설명한 것 처럼 EnableSceneObjectMeshes 및 EnableWorldMesh를 사용 하 여 장면 만들기는 가능 하면 실제로 완전히 완전 한 메시를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-162">As described in the section on [occlusion](#occlusion) creating a scene with EnableSceneObjectMeshes and EnableWorldMesh will produce the most physically complete mesh possible.</span></span> <span data-ttu-id="b08a2-163">환경 메쉬의 watertight 속성은 적중 테스트가 적중 하는 표면에 도달 하지 않도록 방지 하 고 메시 데이터를 사용 하면 물리학가 방 구조만이 아니라 장면의 모든 개체와 상호 작용 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-163">The watertight property of the environment mesh will prevent hit tests from failing to hit surfaces and the mesh data will ensure that physics are interacting with all objects in the scene and not just the room structure.</span></span>

### <a name="navigation"></a><span data-ttu-id="b08a2-164">탐색</span><span class="sxs-lookup"><span data-stu-id="b08a2-164">Navigation</span></span>

<span data-ttu-id="b08a2-165">의미 체계 클래스로 분해 된 평면 메시는 탐색 및 경로 계획에 이상적인 구문이 며 [공간 매핑 탐색](spatial-mapping.md#navigation) 개요에 설명 된 많은 문제를 감속 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-165">Planar meshes decomposed by semantic class are ideal constructs for navigation and path planning, easing many of the issues described in the [Spatial mapping navigation](spatial-mapping.md#navigation) overview.</span></span> <span data-ttu-id="b08a2-166">장면에서 계산 되는 SceneMesh 개체는 이미 표면 유형에 의해 구성 되어 있지 않습니다. 탐색-메시 생성은 사용할 수 있는 서피스로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-166">The SceneMesh objects computed in the scene are already de-composed by surface type ensuring that nav-mesh generation is limited to surfaces that can be walked on.</span></span> <span data-ttu-id="b08a2-167">구조는 간단 하기 때문에 Unity와 같은 3d 엔진의 동적 탐색-메시 생성은 실시간 요구 사항에 따라 realistic 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-167">Due to the simplicity of the floor structure, dynamic nav-mesh generation in 3d engines such as Unity are attainable depending on real-time requirements.</span></span>

<span data-ttu-id="b08a2-168">정확한 탐색을 생성 하는 메시는 현재 사후 처리가 필요 합니다. 즉, 탐색이 복잡 한/테이블을 통해 전달 되지 않도록 응용 프로그램이 바닥에 계속 occluders 야 합니다. 이를 수행 하는 가장 정확한 방법은 장면이 EnableWorldMesh 플래그를 사용 하 여 계산 되는 경우 제공 되는 세계 메시 데이터를 프로젝션 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-168">Generating accurate nav-meshes currently still requires post-processing, namely applications must still project occluders on to the floor to ensure that navigation does not pass through clutter/tables etc... The most accurate way to accomplish this is to project the world mesh data which is provided if the scene is computed with the EnableWorldMesh flag.</span></span>

### <a name="visualization"></a><span data-ttu-id="b08a2-169">시각화</span><span class="sxs-lookup"><span data-stu-id="b08a2-169">Visualization</span></span>

<span data-ttu-id="b08a2-170">[공간 매핑 시각화](spatial-mapping.md#visualization) 를 사용 하 여 환경에 대 한 실시간 피드백을 제공할 수 있지만, 평면 및 watertight 개체의 단순성은 더 많은 성능과 시각적 품질을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-170">While [spatial mapping visualization](spatial-mapping.md#visualization) can be used for real-time feedback of the environment, there are many scenarios where the simplicity of planar and watertight objects provides more performance or visual quality.</span></span> <span data-ttu-id="b08a2-171">공간 매핑을 사용 하 여 설명 하는 그림자 프로젝션 및 접지 기술은 Quads 또는 planar watertight 메시에서 제공 되는 평면 표면에서 투영 된 경우 더 보기 편 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-171">Shadow projection and grounding techniques that are described using spatial mapping may be more pleasing if projected on the planar surfaces provided by Quads or the planar watertight mesh.</span></span> <span data-ttu-id="b08a2-172">이는 장면에서 유추할 수 있는 팩트 때문에 철저 한 사전 검사가 최적이 아닌 환경/시나리오에서 특히 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-172">This is especially true for environments/scenarios where thorough pre-scanning is not optimal due to the fact that the scene will infer, and complete environments and planar assumptions will minimize artifacts.</span></span>

<span data-ttu-id="b08a2-173">또한 공간 매핑에서 반환 된 총 표면 수는 내부 공간 캐시에 의해 제한 되는 반면 장면 이해의 공간 매핑 메시 버전은 캐시 되지 않은 공간 매핑 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-173">Additionally, the total number of surfaces returned by Spatial Mapping is limited by the internal spatial cache, while Scene understanding's version of the Spatial Mapping mesh is able to access spatial mapping data that is not cached.</span></span> <span data-ttu-id="b08a2-174">이로 인해 시각화 또는 추가 메시 처리를 위해 장면 이해는 단일 공간 보다 큰 공간에 대 한 메시 표현을 캡처하는 데 더 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-174">Because of this, Scene understanding is more suited to capturing mesh representations for larger spaces (for example, larger than a single room) for visualization or further mesh processing.</span></span> <span data-ttu-id="b08a2-175">EnableWorldMesh를 사용 하 여 반환 되는 세계 메시는 전체에 걸쳐 일관 된 세부 수준을 가지 며,이는 와이어 프레임으로 렌더링 되는 경우 더 많은 보기 편 시각화를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b08a2-175">The world mesh returned with EnableWorldMesh will have a consistent level of detail throughout, which may yield a more pleasing visualization if rendered as wireframe.</span></span>

### <a name="see-also"></a><span data-ttu-id="b08a2-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b08a2-176">See Also</span></span>

* [<span data-ttu-id="b08a2-177">장면 이해 SDK</span><span class="sxs-lookup"><span data-stu-id="b08a2-177">Scene understanding SDK</span></span>](scene-understanding-SDK.md)
* [<span data-ttu-id="b08a2-178">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="b08a2-178">Spatial mapping</span></span>](spatial-mapping.md)
