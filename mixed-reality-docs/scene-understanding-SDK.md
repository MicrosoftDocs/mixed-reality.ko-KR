---
title: 장면 이해 SDK
description: 장면에 대 한 프로그래밍 가이드-SDK 이해
author: szymons
ms.author: szymons
ms.date: 07/08/19
ms.topic: article
keywords: 장면 이해, 공간 매핑, Windows Mixed Reality, Unity
ms.openlocfilehash: 152ffdbd84798c164963717a8dc41beb2e1a0902
ms.sourcegitcommit: e9a55528965048ce34f8247ef6e544f9f432ee37
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69559858"
---
## <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="78505-104">장면 이해 SDK 개요</span><span class="sxs-lookup"><span data-stu-id="78505-104">Scene Understanding SDK Overview</span></span>

<span data-ttu-id="78505-105">장면 이해의 목표는 혼합 현실 장치에서 캡처하는 구조화 되지 않은 환경 센서 데이터를 변환 하 고 직관적이 고 쉽게 개발할 수 있는 강력 하 고 추상화 된 표현으로 변환 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-105">The goal of Scene Understanding is to transform the un-structured environment sensor data that your Mixed Reality device captures and to convert it into a powerful but abstracted representation that is intuitive and easy to develop for.</span></span> <span data-ttu-id="78505-106">SDK는 응용 프로그램과 장면 이해 런타임의 통신 계층으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="78505-107">3d 표현 및 2d 응용 프로그램의 2D 사각형/패널에 대 한 3d 장면 그래프와 같은 기존 표준 구문을 모방 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-107">It's aimed to mimic existing standard constructs such as 3d scene graphs for 3d representations and 2D rectangles/panels for 2d applications.</span></span> <span data-ttu-id="78505-108">구성 장면 이해를 모방 하는 것은 사용할 수 있는 구체적인 프레임 워크에 매핑됩니다. 일반적으로 SceneUnderstanding은 프레임 워크와 상호 작용 하는 다양 한 프레임 워크 간의 상호 운용성을 가능 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-108">While the constructs Scene Understanding mimics will map to concrete frameworks you may use, in general SceneUnderstanding is framework agnostic allowing for interop between varied frameworks that interact with it.</span></span> <span data-ttu-id="78505-109">장면 이해는 SDK의 역할을 발전 시킬 때 새로운 표현과 기능이 통합 프레임 워크 내에서 계속 노출 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="78505-110">이 문서에서는 먼저 개발 환경/사용법을 파악 하는 데 도움이 되는 개략적인 개념을 소개 하 고 특정 클래스 및 구문에 대 한 자세한 설명서를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-110">In this document we will first introduce high level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="78505-111">SDK는 어디에서 얻을 까 요?</span><span class="sxs-lookup"><span data-stu-id="78505-111">Where do I get the SDK?</span></span>

<span data-ttu-id="78505-112">SceneUnderstanding SDK는 NuGet을 통해 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="78505-113">SceneUnderstanding SDK</span><span class="sxs-lookup"><span data-stu-id="78505-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="78505-114">시작 하기 전에 SDK는 UWP 위에서 실행 되며 Windows SDK 버전 18362 이상이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-114">Before you begin please note that the SDK runs on top of the UWP, and requires Windows SDK version 18362 or higher.</span></span> 

### <a name="the-scene"></a><span data-ttu-id="78505-115">장면</span><span class="sxs-lookup"><span data-stu-id="78505-115">The Scene</span></span>

<span data-ttu-id="78505-116">혼합 현실 장치는 환경에서 표시 되는 내용에 대 한 정보를 지속적으로 통합 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-116">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="78505-117">장면 이해는 이러한 모든 데이터 원본을 funnels 하나의 단일 단일 추상화를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-117">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="78505-118">장면 이해는 단일 사물 (예: 벽/천장/층)의 인스턴스를 나타내는 [SceneObjects](scene-understanding-SDK.md#sceneobjects) 의 컴퍼지션 인 장면을 생성 합니다. 장면 개체 자체는이 SceneObject을 구성 하는 더 세분화 된 부분을 나타내는 [SceneComponents](scene-understanding-SDK.md#scenecomponents) 의 컴퍼지션입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-118">Scene Understanding generates Scenes which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (e.g. a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents](scene-understanding-SDK.md#scenecomponents) which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="78505-119">구성 요소의 예는 quads 및 메시 이지만 나중에 경계 상자, 충돌 mehses, 메타 데이터 등을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-119">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision mehses, metadata etc...</span></span>

<span data-ttu-id="78505-120">원시 센서 데이터를 장면으로 변환 하는 프로세스는 매우 큰 공간 (~ 50x50m)에 대해 보통 공간 (~ 10x10m)에서 분까지 몇 초 정도 걸릴 수 있으며, 따라서 응용 프로그램 요청.</span><span class="sxs-lookup"><span data-stu-id="78505-120">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for very large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="78505-121">대신, 요청 시 응용 프로그램에서 장면 생성이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-121">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="78505-122">SceneObserver 클래스에는 장면을 계산 하거나 Deserialize 할 수 있는 정적 메서드가 있습니다. 그러면이를 열거/상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-122">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="78505-123">"Compute" 작업은 요청 시 실행 되며 CPU에서 실행 되지만 별도의 프로세스 (혼합 현실 드라이버)에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-123">The "Compute" action is executed on-demand and executes on the CPU but in a seperate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="78505-124">그러나 다른 프로세스에서 계산을 수행 하는 동안 결과 장면 데이터는 응용 프로그램에서 장면 개체에 저장 되 고 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-124">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="78505-125">다음은이 프로세스 흐름을 보여 주고 장면 이해 런타임과 상호 작용 하는 두 개의 응용 프로그램 예제를 보여 주는 다이어그램입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-125">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![프로세스 다이어그램](images/SU-ProcessFlow.png)

<span data-ttu-id="78505-127">왼쪽에는 항상 자체 프로세스에서 실행 되 고 실행 되는 혼합 현실 런타임의 다이어그램이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-127">On the left hand side is a diagram of the mixed reality runtime which is always on and running in its own process.</span></span> <span data-ttu-id="78505-128">이 런타임은 장치 추적, 표면 재구성 및 전 세계의 이해를 위해 장면에서 이해 하는 기타 작업을 수행 하는 작업을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-128">This runtime is responsible for performing device tracking, surface reconstruction, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="78505-129">다이어그램의 오른쪽에는 장면 이해를 활용 하는 두 개의 이론적인 응용 프로그램이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-129">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="78505-130">첫 번째 응용 프로그램은 내부적으로 장면 이해 SDK를 사용 하는 MRTK를 사용 하 고, 두 번째 앱은 두 개의 sepereate 장면 인스턴스를 계산 하 여 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-130">The first application interfaces with MRTK which uses the Scene Understanding SDK internally, the second app computes and uses two sepereate scene instances.</span></span> <span data-ttu-id="78505-131">이 다이어그램의 3 개 장면이 모두 백그라운드의 개별 인스턴스를 생성 하 고, 한 장면의 응용 프로그램과 장면 개체 간에 공유 되는 전역 상태를 추적 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-131">All 3 Scenes in this diagram generate distinct instances of the scenes, the driver is not tracking global state that is shared between applications and Scene Objects in one scene are not found in another.</span></span> <span data-ttu-id="78505-132">장면 이해는 시간에 따라 추적 하는 메커니즘을 제공 하지만이 작업은 SDK 및 코드를 사용 하 여 수행 됩니다 .이 추적을 수행 하는 코드는 앱 프로세스의 SDK에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-132">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK and code the code that performs this tracking is running in the SDK in your app's process.</span></span>

<span data-ttu-id="78505-133">각 장면은 응용 프로그램의 메모리 공간에 해당 데이터를 저장 하기 때문에 장면 개체의 모든 기능 또는 내부 데이터가 항상 응용 프로그램의 프로세스에서 실행 된다고 가정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-133">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

#### <a name="layout"></a><span data-ttu-id="78505-134">레이아웃</span><span class="sxs-lookup"><span data-stu-id="78505-134">Layout</span></span>

<span data-ttu-id="78505-135">장면 이해를 이해 하려면 런타임이 구성 요소를 논리적 및 물리적으로 표시 하는 방법을 알고 이해 하는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-135">To work with Scene Understanding it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="78505-136">장면은 주요 수정이 필요 하지 않고 미래의 요구 사항을 충족 하는 pliable 기본 구조를 유지 하면서 간단 하 게 선택 된 특정 레이아웃을 가진 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="78505-136">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="78505-137">장면에서는 모든 구성 요소 (모든 장면 개체의 빌딩 블록)를 단순 목록에 저장 하 고 특정 구성 요소가 다른 항목을 참조 하는 참조를 통해 계층 구조와 컴퍼지션을 정의 하 여이를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-137">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="78505-138">아래에서는 플랫 및 논리적 형식으로 된 구조의 예를 보여 주고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-138">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="78505-139">논리적 레이아웃</span><span class="sxs-lookup"><span data-stu-id="78505-139">Logical Layout</span></span></th><th><span data-ttu-id="78505-140">물리적 레이아웃</span><span class="sxs-lookup"><span data-stu-id="78505-140">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="78505-141">장면의</span><span class="sxs-lookup"><span data-stu-id="78505-141">Scene</span></span>
  <ul>
  <li><span data-ttu-id="78505-142">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="78505-142">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="78505-143">Mesh_1</span><span class="sxs-lookup"><span data-stu-id="78505-143">Mesh_1</span></span></li>
      <li><span data-ttu-id="78505-144">Quad_1</span><span class="sxs-lookup"><span data-stu-id="78505-144">Quad_1</span></span></li>
      <li><span data-ttu-id="78505-145">Quad_2</span><span class="sxs-lookup"><span data-stu-id="78505-145">Quad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="78505-146">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="78505-146">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="78505-147">Quad_1</span><span class="sxs-lookup"><span data-stu-id="78505-147">Quad_1</span></span></li>
      <li><span data-ttu-id="78505-148">Quad_3</span><span class="sxs-lookup"><span data-stu-id="78505-148">Quad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="78505-149">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="78505-149">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="78505-150">Mesh_3</span><span class="sxs-lookup"><span data-stu-id="78505-150">Mesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="78505-151">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="78505-151">SceneObject_1</span></span></li>
  <li><span data-ttu-id="78505-152">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="78505-152">SceneObject_2</span></span></li>
  <li><span data-ttu-id="78505-153">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="78505-153">SceneObject_3</span></span></li>
  <li><span data-ttu-id="78505-154">Quad_1</span><span class="sxs-lookup"><span data-stu-id="78505-154">Quad_1</span></span></li>
  <li><span data-ttu-id="78505-155">Quad_2</span><span class="sxs-lookup"><span data-stu-id="78505-155">Quad_2</span></span></li>
  <li><span data-ttu-id="78505-156">Quad_3</span><span class="sxs-lookup"><span data-stu-id="78505-156">Quad_3</span></span></li>
  <li><span data-ttu-id="78505-157">Mesh_1</span><span class="sxs-lookup"><span data-stu-id="78505-157">Mesh_1</span></span></li>
  <li><span data-ttu-id="78505-158">Mesh_2</span><span class="sxs-lookup"><span data-stu-id="78505-158">Mesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="78505-159">이 그림에서는 장면의 물리적 레이아웃과 논리적 레이아웃 간의 차이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="78505-159">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="78505-160">오른쪽에는 장면을 열거할 때 응용 프로그램에 표시 되는 데이터의 계층적 레이아웃이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-160">On the right we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="78505-161">왼쪽에는 장면이 실제로는 필요한 경우 개별적으로 액세스할 수 있는 12 개의 고유 구성 요소로 구성 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-161">On the left we see that the scene is actually comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="78505-162">새 장면을 처리할 때 응용 프로그램이이 계층 구조를 논리적으로 탐색 하는 것이 좋지만, 장면 업데이트를 추적할 때 일부 응용 프로그램은 두 장면 간에 공유 되는 특정 구성 요소를 대상으로 하는 경우에만 관심이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-162">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

### <a name="high-level-overview"></a><span data-ttu-id="78505-163">개략적인 개요</span><span class="sxs-lookup"><span data-stu-id="78505-163">High-level Overview</span></span>

<span data-ttu-id="78505-164">다음 섹션에서는 장면 이해의 구문에 대 한 개략적인 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-164">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="78505-165">이 섹션을 읽으면 장면이 표시 되는 방법 및 다양 한 구성 요소를 사용 하는 방법에 대 한 이해를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-165">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="78505-166">다음 섹션에서는이 개요에서 달았습니다 구체적인 코드 예제 및 추가 세부 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-166">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

#### <a name="scenecomponents"></a><span data-ttu-id="78505-167">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="78505-167">SceneComponents</span></span>

<span data-ttu-id="78505-168">이제 배경의 논리적 레이아웃을 이해 했으므로 이제 SceneComponents의 개념과 계층 구조를 작성 하는 데 사용 되는 방법을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-168">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they are used to compose hierarchy.</span></span> <span data-ttu-id="78505-169">SceneComponents는 단일 핵심 항목 (예: 메시 또는 쿼드 또는 경계 상자)을 나타내는 SceneUnderstanding에서 가장 세분화 된 decompositions입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-169">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, e.g. a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="78505-170">SceneComponents은 독립적으로 업데이트 될 수 있고 다른 SceneComponents에서 참조할 수 있는 항목입니다. 따라서이 유형의 추적/참조 메커니즘을 허용 하는 단일 전역 속성의 고유 Id가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-170">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique Id, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="78505-171">Id는 장면 계층의 논리적 컴퍼지션 뿐만 아니라 개체 지 속성 (한 장면을 다른 장면으로 업데이트 하는 동작)에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-171">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="78505-172">새로 계산 된 모든 장면을 고유 하 게 처리 하 고 그 안의 모든 데이터를 간단히 열거 하는 경우 Id는 대체로 사용자에 게 투명 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-172">If you are treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="78505-173">그러나 여러 업데이트에 대 한 구성 요소를 추적 하려는 경우 Id를 사용 하 여 장면 개체 간 SceneComponents을 인덱싱합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-173">However, if you are planning to track components over several updates you will use the Ids to index and find SceneComponents between Scene objects.</span></span>

#### <a name="sceneobjects"></a><span data-ttu-id="78505-174">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="78505-174">SceneObjects</span></span>

<span data-ttu-id="78505-175">SceneObject은 "사물" (예: 벽, 층, 천장 등)의 인스턴스를 나타내는 SceneComponent입니다. Kind 속성으로 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-175">A SceneObject is a SceneComponent that represents an instance of a "thing" e.g. a wall, a floor, a ceiling, etc... expressed by their Kind property.</span></span> <span data-ttu-id="78505-176">SceneObjects는 기 하 도형 이므로 공간에서 해당 위치를 나타내는 함수와 속성이 있지만 기하학적 또는 논리적 구조는 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-176">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="78505-177">대신, SceneObjects는 다른 SceneComponents, 특히 SceneQuads 및 SceneMeshes를 참조 하 여 시스템에서 지 원하는 다양 한 표현을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-177">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads and SceneMeshes which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="78505-178">새 장면을 계산 하면 응용 프로그램에서 관심 있는 항목을 처리 하는 장면의 SceneObjects을 열거 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-178">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="78505-179">SceneObjects에는 다음 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-179">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="78505-180">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="78505-180">SceneObjectKind</span></span></th> <th><span data-ttu-id="78505-181">설명</span><span class="sxs-lookup"><span data-stu-id="78505-181">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="78505-182">배경</span><span class="sxs-lookup"><span data-stu-id="78505-182">Background</span></span></td><td><span data-ttu-id="78505-183">SceneObject는 인식 되는 다른 종류의 장면 개체 중 하나가 <b>아닌</b> 것으로 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-183">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="78505-184">이 클래스는 배경을 벽/층/천장 등이 아닌 것으로 알려진 경우 알 수 없는와 혼동 해서는 안 됩니다. unknown은 아직 분류 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-184">This class should not be confused with Unknown where Background is known not to be wall/floor/ceiling etc... while unknown is not yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="78505-185">벽</span><span class="sxs-lookup"><span data-stu-id="78505-185">Wall</span></span></td><td><span data-ttu-id="78505-186">실제 벽입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-186">A physical wall.</span></span> <span data-ttu-id="78505-187">벽은 불균형 환경 구조로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-187">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="78505-188">평면</span><span class="sxs-lookup"><span data-stu-id="78505-188">Floor</span></span></td><td><span data-ttu-id="78505-189">바닥은 한 번에 진행할 수 있는 모든 표면입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-189">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="78505-190">참고: 계단은 층이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="78505-190">Note: stairs are not floors.</span></span> <span data-ttu-id="78505-191">또한이 층은 walkable 표면을 가정 하므로 단일 층을 명시적으로 가정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-191">Also note, that floors assume any walkable surface and therefore there is no explicit assumption of a singular floor.</span></span> <span data-ttu-id="78505-192">다중 수준 구조, 경사 등 ... 모두 바닥으로 분류 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-192">Multi-level structures, ramps etc... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="78505-193">Ceiling</span><span class="sxs-lookup"><span data-stu-id="78505-193">Ceiling</span></span></td><td><span data-ttu-id="78505-194">방의 위쪽 표면입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-194">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="78505-195">플랫폼</span><span class="sxs-lookup"><span data-stu-id="78505-195">Platform</span></span></td><td><span data-ttu-id="78505-196">Holograms를 놓을 수 있는 커다란 플랫 표면입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-196">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="78505-197">이는 테이블, 싱크대 및 기타 넓은 가로 표면을 나타내는 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-197">These tend to represent tables, countertops and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="78505-198">World</span><span class="sxs-lookup"><span data-stu-id="78505-198">World</span></span></td><td><span data-ttu-id="78505-199">레이블 지정과 무관 한 기하학적 데이터의 예약 된 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-199">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="78505-200">EnableWorldMesh 업데이트 플래그를 설정 하 여 생성 된 메시는 세계로 분류 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-200">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="78505-201">알 수 없음</span><span class="sxs-lookup"><span data-stu-id="78505-201">Unknown</span></span></td><td><span data-ttu-id="78505-202">이 장면 개체는 아직 분류 되어 있으며 종류를 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-202">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="78505-203">이 개체는 아무것도 될 수 있으므로 배경과 혼동 해서는 안 됩니다. 시스템은 아직 충분히 강력한 분류로 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-203">This should not be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

#### <a name="scenemesh"></a><span data-ttu-id="78505-204">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="78505-204">SceneMesh</span></span>

<span data-ttu-id="78505-205">SceneMesh은 삼각형 목록을 사용 하 여 임의 기하학적 개체의 기 하 도형에 근사치를 주는 SceneComponent입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-205">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="78505-206">SceneMeshes는 여러 다른 컨텍스트에서 사용 되며, watertight 셀 구조의 구성 요소를 나타내거나 장면에 연결 된 제한 되지 않은 표면 재구성을 나타내는 WorldMesh로 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-206">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh which represents the unbounded Surface Reconstruction associated with the Scene.</span></span> <span data-ttu-id="78505-207">각 메시와 함께 제공 되는 인덱스 및 꼭 짓 점 데이터는 모든 최신 렌더링 Api에서 삼각형 메시를 렌더링 하는 데 사용 되는 [꼭 짓 점 및 인덱스 버퍼](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) 와 동일한 익숙한 레이아웃을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-207">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="78505-208">장면 이해에서 메시는 32 비트 인덱스를 사용 하며 특정 렌더링 엔진에 대 한 청크로 분할 되어야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-208">Note that in Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="scenequad"></a><span data-ttu-id="78505-209">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="78505-209">SceneQuad</span></span>

<span data-ttu-id="78505-210">SceneQuad는 3d 세계를 차지 하는 2d 표면을 나타내는 SceneComponent입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-210">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="78505-211">SceneQuads는 ARKit Arkit Eanchor 또는 Arkit 평면과 유사 하 게 사용할 수 있지만, 플랫 앱 또는 확대 된 UX에서 사용 하기 위해 2d canvas로 더 높은 수준의 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-211">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="78505-212">quads에 대 한 2D 특정 Api가 제공 되어 배치 및 레이아웃을 간단 하 게 사용할 수 있으며, quads를 사용 하 여 개발 (렌더링 제외)을 개발 하는 것은 3d 메시 보다 2d 캔버스 작업에 더 유사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-212">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

### <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="78505-213">SDK 세부 정보 및 참조 장면 이해</span><span class="sxs-lookup"><span data-stu-id="78505-213">Scene Understanding SDK Details and Reference</span></span>

#### <a name="sdk"></a><span data-ttu-id="78505-214">SDK</span><span class="sxs-lookup"><span data-stu-id="78505-214">SDK</span></span>

<span data-ttu-id="78505-215">다음 섹션에서는 SceneUnderstanding의 기본 사항에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="78505-215">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="78505-216">이 섹션에서는 SceneUnderstanding를 사용 하는 방법을 확인 하기 위해 샘플 응용 프로그램을 탐색 하는 데 충분 한 컨텍스트를 제공 해야 하는 기본 사항에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-216">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

#### <a name="initialization"></a><span data-ttu-id="78505-217">초기화</span><span class="sxs-lookup"><span data-stu-id="78505-217">Initialization</span></span>

<span data-ttu-id="78505-218">SceneUnderstanding를 사용 하는 첫 번째 단계는 응용 프로그램에서 장면 개체에 대 한 참조를 얻는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-218">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="78505-219">이 작업은 두 가지 방법 중 하나로 수행할 수 있습니다. 즉, 드라이버에서 장면을 계산 하거나 과거에 계산 된 기존 장면을 deserialize 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-219">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="78505-220">후자는 혼합 현실 장치 없이 응용 프로그램 및 환경을 신속 하 게 프로토타입화 할 수 있는 개발 과정에서 SceneUnderstanding 작업에 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-220">The latter is particularly useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="78505-221">SceneObserver를 사용 하 여 장면을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-221">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="78505-222">장면을 만들기 전에 응용 프로그램은 SceneUnderstanding를 지원 하는지 확인 하 고 SceneUnderstanding에 필요한 정보에 대 한 사용자 액세스를 요청할 수 있도록 장치를 쿼리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-222">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="78505-223">RequestAccessAsync ()를 호출 하지 않으면 새 장면을 계산 하는 작업이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-223">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="78505-224">다음으로는 혼합 현실 헤드셋을 기반으로 하는 새 장면을 계산 하 고 10 미터 반지름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-224">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10 meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.Compute(querySettings, 10.0f);
```

#### <a name="initialization-from-data-aka-the-pc-path"></a><span data-ttu-id="78505-225">데이터에서 초기화 (즉,.</span><span class="sxs-lookup"><span data-stu-id="78505-225">Initialization from Data (aka.</span></span> <span data-ttu-id="78505-226">PC 경로)</span><span class="sxs-lookup"><span data-stu-id="78505-226">the PC Path)</span></span>

<span data-ttu-id="78505-227">직접 소비를 위해 장면을 계산할 수 있지만 나중에 사용할 수 있도록 serialize 된 형식으로 계산 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-227">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="78505-228">이는 개발자가 장치 없이 작업을 수행 하 고 장면 이해를 테스트할 수 있도록 하는 개발에 매우 유용한 것으로 입증 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-228">This has proven to be very useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="78505-229">장면을 직렬화 하는 작업은 응용 프로그램에 의해 로컬에서 deserialize 되는 대신 응용 프로그램에 반환 되는 것과 거의 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-229">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="78505-230">사용자는 직접 deserialize 하거나 나중에 사용할 수 있도록 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-230">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneUnderstanding.QuerySettings querySettings;

// Compute a scene but serialized as a byte array
byte[] newSceneBlob = SceneObserver.ComputeSerialized(querySettings, 10.0f);

// If we want to use it immediatley we can de-serialize the scene ourselves
Scene mySceneDeSerialized = Scene.Deserialize(newSceneBlob);

// Save newSceneBlob for later
```

#### <a name="sceneobject-enumeration"></a><span data-ttu-id="78505-231">SceneObject 열거형</span><span class="sxs-lookup"><span data-stu-id="78505-231">SceneObject Enumeration</span></span>

<span data-ttu-id="78505-232">이제 응용 프로그램에 장면이 있으므로 응용 프로그램은 SceneObjects를 보고 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-232">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="78505-233">**SceneObjects** 속성에 액세스 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-233">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

#### <a name="component-update-and-re-finding-components"></a><span data-ttu-id="78505-234">구성 요소 업데이트 및 구성 요소 다시 찾기</span><span class="sxs-lookup"><span data-stu-id="78505-234">Component update and re-finding components</span></span>

<span data-ttu-id="78505-235">***FindComponent***라는 장면에서 구성 요소를 검색 하는 또 다른 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-235">There is another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="78505-236">이 함수는 추적 개체를 업데이트 하 고 후속 장면에서 찾을 때 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-236">This function is useful when updating tracking objects and finding them in subsequent scenes.</span></span> <span data-ttu-id="78505-237">다음 코드는 이전 장면을 기준으로 새 장면을 계산 하 고 새 장면에서 바닥을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-237">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, but tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.Compute(querySettings, 10.0f, myScene);

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attatched to this floor transform
}
```

### <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="78505-238">장면 개체에서 메시 및 Quads 액세스</span><span class="sxs-lookup"><span data-stu-id="78505-238">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="78505-239">SceneObjects 발견 되 면 응용 프로그램은 구성 된 quads/메시를 포함 하는 데이터에 액세스 하려고 할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-239">Once SceneObjects have been found your application will most likely want to access the data that is contained n the quads/meshes that it is comprised of.</span></span> <span data-ttu-id="78505-240">이 데이터는 ***Quads*** 및 ***메시*** 속성을 사용 하 여 액세스 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-240">This data is accessed with the ***Quads*** and ***Meshes*** properties.</span></span> <span data-ttu-id="78505-241">다음 코드는 floor 개체의 모든 quads 및 메시를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-241">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the matrix for the SceneObject
System.Numerics.Matrix4x4 floorTransform = firstFloor.LocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="78505-242">이는 장면 원점에 상대적인 변환을 포함 하는 SceneObject입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-242">Notice that it is the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="78505-243">이는 SceneObject가 "사물"의 인스턴스를 나타내므로 공간에 과정이 quads와 망상은 부모를 기준으로 변환 되는 기 하 도형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="78505-243">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="78505-244">별도의 SceneObjects가 동일한 SceneMesh/SceneQuad SceneComponewnts를 참조할 수 있으며 SceneObject에 두 개 이상의 SceneMesh/SceneQuad가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-244">It is possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponewnts, and it is also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="78505-245">변형 처리</span><span class="sxs-lookup"><span data-stu-id="78505-245">Dealing with Transforms</span></span>

<span data-ttu-id="78505-246">장면 이해는 변환을 처리할 때 일반적인 3D 장면 표현과 맞추는 시도를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-246">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="78505-247">따라서 각 장면은 가장 일반적인 3D 환경 표현과 마찬가지로 단일 좌표계로 한정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-247">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="78505-248">응용 프로그램이 단일 원본에서 제공 하는 작업의 제한을 스트레치 하는 장면을 처리 하는 경우 SceneObjects에 SpatialAnchors에 앵커를 적용 하거나 여러 개의 장면을 생성 하 고 함께 병합할 수 있습니다. 장면:: OriginSpatialGraphNodeId에 의해 정의 된 하나의 NodeId 지역화 된 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-248">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene::OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="78505-249">예를 들어 다음 unity 코드는 windows 인식 및 Unity Api를 사용 하 여 좌표계를 함께 맞추는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="78505-249">The following unity code, for example, shows how to use windows perception and Unity APIs to align coordinate systems together:</span></span>


```cs
    public static System.Numerics.Matrix4x4? GetSceneToUnityTransform(Guid nodeId)
    {
        System.Numerics.Matrix4x4? sceneToUnityTransform; 
       
        SpatialCoordinateSystem sceneSpatialCoordinateSystem = Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(nodeId);
        SpatialCoordinateSystem unitySpatialCoordinateSystem = (SpatialCoordinateSystem)System.Runtime.InteropServices.Marshal.GetObjectForIUnknown(UnityEngine.XR.WSA.WorldManager.GetNativeISpatialCoordinateSystemPtr());

        sceneToUnityTransform = sceneSpatialCoordinateSystem.TryGetTransformTo(unitySpatialCoordinateSystem);

        if (sceneToUnityTransform != null)
        {
            sceneToUnityTransform = TransformUtils.ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
        }
        
        return sceneToUnityTransform;
    }

    /// <summary>
    /// Converts a transformation matrix from right handed (+x is right, +y is up, +z is back) to left handed (+x is right, +y is up, +z is front).
    /// </summary>
    /// <param name="transformationMatrix">Right-handed transformation matrix to convert.</param>
    /// <returns>Converted left-handed matrix.</returns>
    public System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 transformationMatrix)
    {
        transformationMatrix.M13 = -transformationMatrix.M13;
        transformationMatrix.M23 = -transformationMatrix.M23;
        transformationMatrix.M43 = -transformationMatrix.M43;

        transformationMatrix.M31 = -transformationMatrix.M31;
        transformationMatrix.M32 = -transformationMatrix.M32;
        transformationMatrix.M34 = -transformationMatrix.M34;

        return transformationMatrix;
    }
```

<span data-ttu-id="78505-250">그리고 다음 코드는이 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-250">And the following code calls this function:</span></span>

```cs
System.Numerics.Matrix4x4? sceneToUnityTransform = TransformUtils.GetSceneToUnityTransform(scene.OriginSpatialGraphNodeId);

// Set the root transform
Vector3 t;
Quaternion r;
Vector3 s;

System.Numerics.Matrix4x4.Decompose(sceneToUnityTransform, out s, out r, out t);
SceneRoot.Transform.SetPositionAndRotation(t, r);
```

### <a name="quad"></a><span data-ttu-id="78505-251">Led</span><span class="sxs-lookup"><span data-stu-id="78505-251">Quad</span></span>

<span data-ttu-id="78505-252">Quads는 2D 배치 시나리오를 용이 하 게 하기 위해 설계 되었으며 2D canvas UX 요소에 대 한 확장으로 간주 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-252">Quads were designed to facilitate 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="78505-253">Quads는 SceneObjects의 구성 요소이 고 3D로 렌더링 될 수 있지만 쿼드 Api 자체는 Quads이 2D 구조인 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-253">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="78505-254">익스텐트, 모양, 배치를 위한 Api 제공 등의 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-254">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="78505-255">Quads는 사각형 범위를 갖지만 임의의 모양의 2d 표면을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="78505-255">Quads have rectangular extents, but they represent arbitrarily shaped 2d surfaces.</span></span> <span data-ttu-id="78505-256">3D 환경 quads와 상호 작용 하는 이러한 2D 표면에서 배치를 사용 하도록 설정 하려면 이러한 상호 작용을 가능 하 게 하는 유틸리티를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-256">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="78505-257">현재 장면 이해는 **Findcentermostplacement** 및 **GetOcclusionMask**의 두 가지 함수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-257">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetOcclusionMask**.</span></span> <span data-ttu-id="78505-258">FindCentermostPlacement는 개체를 배치할 수 있는 쿼드에서 위치를 찾고, 제공 하는 경계 상자가 기본 화면에 상주할 수 있도록 하는 개체에 가장 적합 한 위치를 찾으려고 시도 하는 높은 수준의 API입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-258">FindCentermostPlacement is a high level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will reside on the underlying surface.</span></span>

<span data-ttu-id="78505-259">다음 예에서는 가장 높은 배치 가능한 위치를 찾고 4 번째에 홀로그램을 고정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="78505-259">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new node QuadTransformNode as a child of Root, and set the transform from quad[0].Transform
                // Step 2: Create your hologram and set it as a child of QuadTransformNode
                // Step 3: Set the QuadTransformNode tranform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="78505-260">1-3 단계는 특정 프레임 워크/구현에 따라 달라 지지만 테마는 유사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-260">Steps 1-3 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="78505-261">쿼드은 일반적으로 사용 되지 않으며 공백으로 지역화 된 경계가 있는 2D 평면을 나타내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="78505-261">It is important to note that the Quad is not usually intended to be, is just represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="78505-262">엔진/프레임 워크에서 쿼드가 있는 위치를 확인 하 고 쿼드을 기준으로 개체를 루 팅 하면 holograms가 올바르게 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78505-262">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly.</span></span> <span data-ttu-id="78505-263">자세한 내용은 특정 구현을 표시 하는 quads의 샘플을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="78505-263">For more detailed information please see our samples on quads which show specific implementations.</span></span>

### <a name="mesh"></a><span data-ttu-id="78505-264">그물</span><span class="sxs-lookup"><span data-stu-id="78505-264">Mesh</span></span>

<span data-ttu-id="78505-265">메시는 개체 또는 환경의 기하학적 표현을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="78505-265">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="78505-266">[공간 매핑](spatial-mapping.md), 메시 인덱스 및 각 공간 표면 메시와 함께 제공 되는 꼭 짓 점 데이터는 모든 최신 렌더링 api에서 삼각형 메시 렌더링에 사용 되는 꼭 짓 점 및 인덱스 버퍼와 동일한 친숙 한 레이아웃을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-266">Much like [spatial mapping](spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="78505-267">이 데이터를 참조 하는 데 사용 되는 특정 Api는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-267">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(float[] vertices);
```

<span data-ttu-id="78505-268">\* \* 참고: GetVertices 모든 3 개의 튜플 부동 소수점 값이 데카르트 x, y 및 z 공간의 단일 좌표를 나타내는 꼭 짓 점 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-268">\*\*Note: GetVertices returns a list of vertices where every 3-tuple of floating point values represents a single coordinate in cartesian x,y and z space.</span></span>

<span data-ttu-id="78505-269">다음 코드에서는 메시 구조에서 삼각형 목록을 생성 하는 예제를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-269">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
float[] positions = new float[mesh.VertexCount * 3];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="78505-270">인덱스/꼭 짓 점 버퍼는 인덱스/꼭 짓 점 수를 > 해야 합니다. 그렇지 않으면 효율적인 메모리 다시 사용을 허용 하는 크기를 임의로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78505-270">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory re-use.</span></span>

### <a name="developing-with-scene-understandings"></a><span data-ttu-id="78505-271">장면 사항을 이해를 사용 하 여 개발</span><span class="sxs-lookup"><span data-stu-id="78505-271">Developing with Scene Understandings</span></span>

<span data-ttu-id="78505-272">이 시점에서 런타임 및 SDK의 핵심 구성 요소를 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-272">At this point you should understand the core building blocks of the Scene Understanding runtime and SDK.</span></span> <span data-ttu-id="78505-273">강력 하 고 복잡 한 점은 액세스 패턴, 3d 프레임 워크와의 상호 작용, 공간 계획, 방 분석, 탐색, 물리 등과 같은 고급 작업을 수행 하기 위해 이러한 Api 위에 작성할 수 있는 도구입니다. 시나리오를 표현할 수 있도록 적절 한 방향으로 안내 하는 샘플에서이를 캡처해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-273">The bulk of the power and complexity lies in access patterns, interaction with 3d frameworks, and tools that can be written on top of these APIs to perform more advanced tasks like spatial planning, room analysis, navigation, physics etc... We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="78505-274">주소를 지정 하지 않는 샘플/시나리오가 있는 경우 microsoft에서 알려 주시기 바랍니다. 필요한 내용을 문서화/프로토타입으로 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="78505-274">If there are samples/scenarios we are not addressing, please let us know and we will try to document/prototype what you need.</span></span>

## <a name="see-also"></a><span data-ttu-id="78505-275">참조</span><span class="sxs-lookup"><span data-stu-id="78505-275">See also</span></span>

* [<span data-ttu-id="78505-276">공간 매핑</span><span class="sxs-lookup"><span data-stu-id="78505-276">spatial mapping</span></span>](spatial-mapping.md)
