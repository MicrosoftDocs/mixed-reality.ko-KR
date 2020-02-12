---
title: 자습서 시작-5. 3D 개체와 상호 작용
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: a1b26d56b4693ef23f2d77ba53e0961693489a3a
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130284"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="0b9b2-104">5.3D 개체와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="0b9b2-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="0b9b2-105">이 자습서에서는 기본 3D 콘텐츠 및 사용자 환경에 대해 설명 합니다. 예를 들어, 3D 개체를 컬렉션의 일부로 구성 하 고, 기본 조작을 위한 경계 상자를 구성 하 고, 근거리 및 원거리 상호 작용을 제공 하 고, 터치 및 잡기 제스처를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-105">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="0b9b2-106">목표</span><span class="sxs-lookup"><span data-stu-id="0b9b2-106">Objectives</span></span>

* <span data-ttu-id="0b9b2-107">다른 학습 목표에 사용 되는 3D 개체의 패널을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-107">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="0b9b2-108">경계 상자 구현</span><span class="sxs-lookup"><span data-stu-id="0b9b2-108">Implement bounding boxes</span></span>
* <span data-ttu-id="0b9b2-109">이동, 회전, 크기 조정 등의 기본 조작을 위해 3D 개체를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-109">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="0b9b2-110">근거리 및 원거리 조작 살펴보기</span><span class="sxs-lookup"><span data-stu-id="0b9b2-110">Explore near and far interaction</span></span>
* <span data-ttu-id="0b9b2-111">잡기, 터치 등의 추가 수동 추적 제스처에 대해 알아보기</span><span class="sxs-lookup"><span data-stu-id="0b9b2-111">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="0b9b2-112">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="0b9b2-112">Importing the tutorial assets</span></span>

<span data-ttu-id="0b9b2-113">Unity 사용자 지정 패키지를 다운로드 하 고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-113">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="0b9b2-114">MRTK. HoloLens2.2.2.0.0. unitypackage를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-114">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage)

<span data-ttu-id="0b9b2-115">자습서 자산을 가져온 후 프로젝트 창이 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-115">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="0b9b2-117">Unity 사용자 지정 패키지를 가져오는 방법에 대 한 미리 알림은 [혼합 현실 도구 키트 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 명령을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-117">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="0b9b2-118">장면 보기 Decluttering</span><span class="sxs-lookup"><span data-stu-id="0b9b2-118">Decluttering the scene view</span></span>

<span data-ttu-id="0b9b2-119">장면에서 작업을 더 쉽게 수행 하려면 개체 왼쪽의 **눈 모양** 아이콘을 클릭 하 여 큐브 및 buttoncollection 개체에 대 한 **장면 표시 유형을** off로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-119">To make it easier to work with your scene, set the **scene visibility** for the Cube and ButtonCollection objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="0b9b2-120">이렇게 하면 게임에서 표시 되지 않는 표시를 변경 하지 않고 장면 창에서 개체를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-120">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="0b9b2-122">장면 표시 유형 컨트롤 및 장면 보기와 워크플로를 최적화 하는 데 사용할 수 있는 방법에 대 한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">장면 표시 유형</a> 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-122">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="0b9b2-123">컬렉션에서 3D 개체 구성</span><span class="sxs-lookup"><span data-stu-id="0b9b2-123">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="0b9b2-124">이 섹션에서는이 자습서의 다음 섹션에서 3D 개체와 상호 작용 하는 다양 한 방법을 살펴볼 때 사용할 3D 개체의 패널을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-124">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="0b9b2-125">특히 3D 개체가 3 x 3 모눈에 배치 되도록 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-125">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="0b9b2-126">[단추 패널을 만든](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)경우와 마찬가지로이를 위해 수행 해야 하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-126">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="0b9b2-127">부모 개체에 대 한 3D 개체의 부모</span><span class="sxs-lookup"><span data-stu-id="0b9b2-127">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="0b9b2-128">Grid 개체 컬렉션 (스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="0b9b2-128">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="0b9b2-129">1. 부모 개체에 대 한 3D 개체의 부모</span><span class="sxs-lookup"><span data-stu-id="0b9b2-129">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="0b9b2-130">계층 창에서 **빈 개체를 만들고**적절 한 이름 (예: **3DObjectCollection**)을 지정한 다음 적절 한 위치에 배치 합니다 (예: X = 0, Y =-0.2, Z = 2).</span><span class="sxs-lookup"><span data-stu-id="0b9b2-130">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="0b9b2-131">프로젝트 창에서 **자산** > **mrtk로 이동 합니다. 자습서. GetPrefabs** 가 > 시작 **된 후 다음 Prefabs를** **3DObjectCollection**로.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-131">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **Parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="0b9b2-132">치즈</span><span class="sxs-lookup"><span data-stu-id="0b9b2-132">Cheese</span></span>
* <span data-ttu-id="0b9b2-133">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="0b9b2-133">CoffeeCup</span></span>
* <span data-ttu-id="0b9b2-134">EarthCore</span><span class="sxs-lookup"><span data-stu-id="0b9b2-134">EarthCore</span></span>
* <span data-ttu-id="0b9b2-135">Octa</span><span class="sxs-lookup"><span data-stu-id="0b9b2-135">Octa</span></span>
* <span data-ttu-id="0b9b2-136">Platonic</span><span class="sxs-lookup"><span data-stu-id="0b9b2-136">Platonic</span></span>
* <span data-ttu-id="0b9b2-137">TheModule</span><span class="sxs-lookup"><span data-stu-id="0b9b2-137">TheModule</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="0b9b2-139">계층 창에서 **3 개의 큐브** 를 **3DObjectCollection** 의 자식 개체로 만들고 해당 변환 **배율을** X = 0.15, Y = 0.15, Z = 0.15로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-139">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section3-step1-2.png)

<!-- TODO: Finish -->
> [!TIP]
> <span data-ttu-id="0b9b2-141">위에 나열 된 단계를 수행 하는 방법에 대 한 미리 알림은 [사용자 인터페이스 만들기 및 혼합 현실 도구 키트 구성](mrlearning-base-ch2.md) 자습서를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-141">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="0b9b2-142">각 큐브를 볼 수 있도록 큐브 위치를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-142">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="0b9b2-144">프로젝트 창에서 **자산** > **MixedRealityToolkit** > **standardassets** > **자료** 로 이동 하 여 mrtk와 함께 제공 되는 자료를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-144">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="0b9b2-145">각 큐브의 메시 렌더러 **재질** 요소 0 속성에 적합 한 자료를 클릭 하 여 **끌어 놓습니다** . 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-145">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="0b9b2-146">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="0b9b2-146">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="0b9b2-147">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="0b9b2-147">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="0b9b2-148">MRTK_Standard_Green:</span><span class="sxs-lookup"><span data-stu-id="0b9b2-148">MRTK_Standard_Green:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="0b9b2-150">2. 그리드 개체 컬렉션 (스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="0b9b2-150">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="0b9b2-151">3DObjectCollection 개체에 **그리드 개체 컬렉션 (스크립트)** 구성 요소를 추가 하 고 다음과 같이 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-151">Add a **Grid Object Collection (Script)** component to the 3DObjectCollection object, and configure it as follows:</span></span>

* <span data-ttu-id="0b9b2-152">**정렬 유형** 을 자식 순서로 변경 하 여 자식 개체가 부모 개체 아래에 배치 된 순서 대로 정렬 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-152">Change **Sort Type** to Child Order to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="0b9b2-153">그런 다음 **컬렉션 업데이트** 단추를 클릭 하 여 새 구성을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-153">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="0b9b2-155">3D 개체 조작</span><span class="sxs-lookup"><span data-stu-id="0b9b2-155">Manipulating 3D objects</span></span>

<span data-ttu-id="0b9b2-156">이 섹션에서는 이전 섹션에서 만든 패널의 모든 3D 개체를 조작 하는 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-156">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="0b9b2-157">또한 prefab 개체의 경우 사용자가 추적 된 손으로 이러한 개체를 연결 하 고 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-157">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="0b9b2-158">그런 다음 개체에 적용할 수 있는 몇 가지 조작 동작을 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-158">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="0b9b2-159">이를 위해 수행 하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-159">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="0b9b2-160">모든 개체에 조작 처리기 (스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="0b9b2-160">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="0b9b2-161">Prefab 개체에 Near 인터랙션 Grabbable (스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="0b9b2-161">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="0b9b2-162">조작 처리기 (스크립트) 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="0b9b2-162">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b9b2-163">개체를 **조작할**수 있으려면 개체에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-163">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="0b9b2-164">**Collider** component (예: 상자 collider)</span><span class="sxs-lookup"><span data-stu-id="0b9b2-164">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="0b9b2-165">**조작 처리기 (스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0b9b2-165">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="0b9b2-166">**추적 된 손을 사용 하 여 개체**를 **조작** 하 고 잡기 위해서는 개체에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-166">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="0b9b2-167">**Collider** component (예: 상자 collider)</span><span class="sxs-lookup"><span data-stu-id="0b9b2-167">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="0b9b2-168">**조작 처리기 (스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0b9b2-168">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="0b9b2-169">**Near 인터랙션 Grabbable (스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0b9b2-169">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="0b9b2-170">1. 모든 개체에 조작 처리기 (스크립트) 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-170">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="0b9b2-171">계층 창에서 **치즈** 개체를 선택 하 고 **shift** 키를 누른 채 **Cube ()** 개체를 선택 하 고 모든 개체에 **조작 처리기 (스크립트)** 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-171">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube ()** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="0b9b2-173">이 자습서에서는 colliders가 이미 prefabs에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-173">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="0b9b2-174">큐브 개체와 같은 Unity 기본 형식의 경우 개체를 만들 때 Collider 구성 요소가 자동으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-174">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="0b9b2-175">위의 이미지에서 colliders는 녹색 윤곽선으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-175">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="0b9b2-176">Colliders에 대 한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-176">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="0b9b2-177">2. prefab 개체에 Near 인터랙션 Grabbable (스크립트) 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-177">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="0b9b2-178">계층 창에서 **치즈** 개체를 선택 하 고 **shift** 키를 누른 상태에서 **TheModule** 개체를 선택 하 고 모든 개체에 **Near 인터랙션 Grabbable (스크립트)** 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-178">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="0b9b2-180">3. 조작 처리기 (스크립트) 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="0b9b2-180">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="0b9b2-181">기본 조작</span><span class="sxs-lookup"><span data-stu-id="0b9b2-181">Default manipulation</span></span>

<span data-ttu-id="0b9b2-182">**큐브** 개체의 경우 기본 조작 동작을 수행 하려면 모든 속성을 기본적으로 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-182">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="0b9b2-184">구성 요소를 기본값으로 다시 설정 하려면 구성 요소의 설정 아이콘을 선택 하 고 다시 설정을 선택 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-184">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="0b9b2-185">조작을 확장 전용으로 제한</span><span class="sxs-lookup"><span data-stu-id="0b9b2-185">Restrict manipulation to scale only</span></span>

<span data-ttu-id="0b9b2-186">**Cube (1)** 개체의 경우 사용자가 개체의 크기를 변경할 수 있도록 **두 개의 전달 조작 유형을** Scale으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-186">For the **Cube (1)** object, change **Two Handed Manipulation Type** to Scale to only allow the user to change the object's size:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="0b9b2-188">사용자 로부터 고정 거리가 이동 하도록 제한</span><span class="sxs-lookup"><span data-stu-id="0b9b2-188">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="0b9b2-189">**Cube (2)** 개체의 경우 이동 **시** 의 거리를 변경 하 여 Head에서의 거리를 수정 합니다. 그러면 개체가 이동 될 때 사용자와 동일한 거리가 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-189">For the **Cube (2)** object, change **Constraint On Movement** to Fix Distance From Head so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="0b9b2-191">기본 grabbable 조작</span><span class="sxs-lookup"><span data-stu-id="0b9b2-191">Default grabbable manipulation</span></span>

<span data-ttu-id="0b9b2-192">**치즈**, **CoffeCup**및 **EarthCore** 개체의 경우 기본 grabbable 조작 동작을 수행 하려면 모든 속성을 기본적으로 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-192">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="0b9b2-194">Far 조작 기능 제거</span><span class="sxs-lookup"><span data-stu-id="0b9b2-194">Remove the ability of far manipulation</span></span>

<span data-ttu-id="0b9b2-195">**Octa** 개체의 경우에는 사용자가 추적 된 손을 사용 하 여 직접 개체와 상호 작용할 수 있도록 [ **Far 조작 허용** ] 확인란의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-195">For the **Octa** object, uncheck the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="0b9b2-197">개체의 중심을 기준으로 개체를 회전 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="0b9b2-197">Make an object rotate around its center</span></span>

<span data-ttu-id="0b9b2-198">**Platonic** 개체의 경우에는 한 번 회전 **모드** 를 변경 하 여 개체 중심을 **회전할 수 있습니다** . 그러면 사용자가 개체를 한 손으로 회전할 때 개체의 중심을 기준으로 회전 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-198">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to Rotate About Object Center to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="prevent-movement-after-object-is-released"></a><span data-ttu-id="0b9b2-200">개체를 릴리스한 후의 이동 방지</span><span class="sxs-lookup"><span data-stu-id="0b9b2-200">Prevent movement after object is released</span></span>

<span data-ttu-id="0b9b2-201">**TheModule** 개체의 경우 사용자의 손으로 개체가 해제 되 면 계속 이동 하지 않도록 **릴리스 동작** 을 Nothing으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-201">For the **TheModule** object, change **Release Behavior** to Nothing so that once the object is released from the user's hand, it doesn’t continue to move:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="0b9b2-203">조작 처리기 구성 요소 및 관련 속성에 대해 자세히 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [조작 처리기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) 가이드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-203">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="0b9b2-204">경계 상자 추가</span><span class="sxs-lookup"><span data-stu-id="0b9b2-204">Adding bounding boxes</span></span>

<span data-ttu-id="0b9b2-205">경계 상자를 사용 하면 크기 조정 및 회전에 사용할 수 있는 핸들을 제공 하 여 거의 상호 작용 모두에 대 한 개체를 보다 쉽고 직관적으로 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-205">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="0b9b2-206">이 예제에서는 EarthCore 개체에 경계 상자를 추가 하 여이 개체를 이제 이전 섹션에서 구성한 개체 조작 및 경계 상자 핸들을 사용 하 여 크기 조정 및 회전을 사용 하 여 상호 작용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-206">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b9b2-207">**경계 상자**를 사용할 수 있으려면 개체에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-207">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="0b9b2-208">**Collider** component (예: 상자 collider)</span><span class="sxs-lookup"><span data-stu-id="0b9b2-208">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="0b9b2-209">**경계 상자 (스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0b9b2-209">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="0b9b2-210">1. EarthCore 개체에 경계 상자 (스크립트) 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-210">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="0b9b2-211">검사기 창에서 **EarthCore** 개체를 선택 하 고 EarthCore 개체에 **경계 상자 (스크립트)** 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-211">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="0b9b2-213">경계 상자 시각화는 런타임에 생성 되므로 게임 모드를 시작 하기 전에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-213">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="0b9b2-214">2. 편집기 내 시뮬레이션을 사용 하 여 경계 상자 시각화 및 테스트</span><span class="sxs-lookup"><span data-stu-id="0b9b2-214">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="0b9b2-215">게임 모드를 시작 하려면 재생 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-215">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="0b9b2-216">그런 다음 스페이스바를 누르고 마우스를 사용 하 여 경계 상자와 상호 작용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-216">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="0b9b2-218">경계 상자 구성 요소 및 관련 속성에 대 한 자세한 내용은 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [경계 상자](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 가이드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-218">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="0b9b2-219">터치 효과 추가</span><span class="sxs-lookup"><span data-stu-id="0b9b2-219">Adding touch effects</span></span>

<span data-ttu-id="0b9b2-220">이 예제에서는 개체를 손으로 이동할 때 이벤트를 트리거할 수 있도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-220">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="0b9b2-221">특히 Octa 개체가 사용자에 게 닿을 때 소리 효과를 재생 하도록 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-221">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="0b9b2-222">이를 위해 수행 하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-222">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="0b9b2-223">오디오 원본 구성 요소를 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-223">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="0b9b2-224">개체에 Near 인터랙션 Touchable (스크립트) 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-224">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="0b9b2-225">개체에 손 모양 상호 작용 터치 (스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="0b9b2-225">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="0b9b2-226">터치 시작 시 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="0b9b2-226">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="0b9b2-227">편집기에서 시뮬레이션을 사용 하 여 터치 상호 작용 테스트</span><span class="sxs-lookup"><span data-stu-id="0b9b2-227">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b9b2-228">**터치 이벤트를 트리거할**수 있으려면 개체에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-228">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="0b9b2-229">**Collider** component, 가급적 상자 Collider</span><span class="sxs-lookup"><span data-stu-id="0b9b2-229">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="0b9b2-230">**Near 인터랙션 Touchable (스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0b9b2-230">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="0b9b2-231">**직접 상호 작용 터치 (스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0b9b2-231">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="0b9b2-232">핸드 상호 작용 터치 (스크립트) 구성 요소는 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-232">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="0b9b2-233">이 자습서의 자산과 원래 MixedReality Toolkit Unity 예제의 일부로 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-233">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="0b9b2-234">1. 오디오 원본 구성 요소를 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-234">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="0b9b2-235">계층 창에서 **Octa** 개체를 선택 하 고 **오디오 원본** 구성 요소를 Octa 개체에 추가한 다음 공간 **Blend** 를 1로 변경 하 여 공간 오디오를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-235">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="0b9b2-237">2. Near 인터랙션 Touchable (스크립트) 구성 요소를 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-237">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="0b9b2-238">**Octa** 개체를 선택한 상태에서 **near 인터랙션 Touchable (스크립트)** 구성 요소를 Octa 개체에 추가한 다음, **범위 수정** 및 **수정 센터** 단추를 클릭 하 여와 일치 하는 근접 한 상호 작용 Touchable (스크립트)의 로컬 센터 및 범위 속성을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-238">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="0b9b2-240">3. 개체에 손 모양 상호 작용 터치 (스크립트) 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-240">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="0b9b2-241">**Octa** 개체를 선택한 상태에서 Octa 개체에 **손 모양 상호 작용 터치 (스크립트)** 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-241">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="0b9b2-243">4. 터치 시작 시 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="0b9b2-243">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="0b9b2-244">핸드 상호 작용 터치 (스크립트) 구성 요소에서 small **+** 아이콘을 클릭 하 여 새 **터치 시작 ()** 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-244">On the Hand Interaction Touch (Script) component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="0b9b2-245">그런 다음 이벤트를 수신 하도록 **Octa** 개체를 구성 하 고 트리거할 동작으로 **PlayOneShot** 를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-245">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="0b9b2-247">**자산** > **MixedRealityToolkit** > **standardassets** > 자료로 이동 하 여 mrtk와 함께 제공 되는 오디오 클립을 확인 하 고 **오디오 클립** 필드 (예: MRTK_Gem 오디오 클립)에 적절 한 오디오 클립을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-247">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="0b9b2-249">이벤트를 구현 하는 방법에 대 한 미리 알림은 [손 추적 제스처 및 interactable 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-249">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="0b9b2-250">5. 편집기 내 시뮬레이션을 사용 하 여 터치 상호 작용 테스트</span><span class="sxs-lookup"><span data-stu-id="0b9b2-250">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="0b9b2-251">게임 모드를 시작 하려면 재생 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-251">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="0b9b2-252">그런 다음 스페이스바를 누르고 마우스를 사용 하 여 Octa 개체를 터치 하 고 소리 효과를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-252">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="0b9b2-254">터치 상호 작용을 테스트할 때와 위의 이미지에 표시 된 것 처럼 Octa 개체 색은 작업을 수행 하는 동안 pulsated.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-254">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="0b9b2-255">이 효과는 직접 상호 작용 터치 (스크립트) 구성 요소에 하드 코딩 되며 위 단계에서 완료 한 이벤트 구성의 결과가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-255">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="0b9b2-256">이 효과를 사용 하지 않도록 설정 하려면 예를 들어 주석 출력 또는 줄 32 ' TargetRenderer = GetComponentInChildren<Renderer>(); '를 사용할 수 있습니다. 그러면 TargetRenderer 남은 null과 색이 pulsating 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-256">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="0b9b2-257">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-257">Congratulations</span></span>

<span data-ttu-id="0b9b2-258">이 자습서에서는 그리드 컬렉션에서 3D 개체를 구성 하는 방법 및 거의 상호 작용 (추적 된 손으로 직접 이동) 및 먼 상호 작용 (응시 광선 또는 핸드 광선 사용)을 사용 하 여 이러한 개체를 조작 하는 방법 (크기 조정, 회전 및 이동)을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-258">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="0b9b2-259">3D 개체 주위에 경계 상자를 배치 하는 방법 및 경계 상자에서 핸들을 사용 하 고 사용자 지정 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-259">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="0b9b2-260">마지막으로 개체를 터치할 때 이벤트를 트리거하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="0b9b2-260">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="0b9b2-261">다음 단원: 6. 고급 입력 옵션 탐색</span><span class="sxs-lookup"><span data-stu-id="0b9b2-261">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
