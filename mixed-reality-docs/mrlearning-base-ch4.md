---
title: 시작 자습서 - 5. 3D 개체와 상호 작용
description: 3D 개체 구성, 기본 조작을 위한 경계 상자와 같은 기본 3D 콘텐츠 및 사용자 환경에 대해 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 419b381c1240b2cc10708eab03245ed3aabfa859
ms.sourcegitcommit: 61291e83536c8cb2e8401a8e66060128ede35922
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416135"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="ebaef-105">5. 3D 개체와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="ebaef-105">5. Interacting with 3D objects</span></span>

<span data-ttu-id="ebaef-106">이 자습서에서는 컬렉션의 일부로 3D 개체 구성, 기본 조작을 위한 경계 상자, 근거리 및 원거리 상호 작용, 손 추적을 사용하는 터치 및 잡기 제스처 등의 기본 3D 콘텐츠 및 사용자 환경에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-106">In this tutorial, you will learn about basic 3D content and user experience, such as organizing 3D objects as part of a collection, bounding boxes for basic manipulation, near and far interaction, and touch and grab gestures with hand tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="ebaef-107">목표</span><span class="sxs-lookup"><span data-stu-id="ebaef-107">Objectives</span></span>

* <span data-ttu-id="ebaef-108">다른 학습 목표에 사용되는 3D 개체 패널 만들기</span><span class="sxs-lookup"><span data-stu-id="ebaef-108">Create a panel of 3D objects which will be used for the other learning objectives</span></span>
* <span data-ttu-id="ebaef-109">경계 상자 구현</span><span class="sxs-lookup"><span data-stu-id="ebaef-109">Implement bounding boxes</span></span>
* <span data-ttu-id="ebaef-110">이동, 회전, 크기 조정 등의 기본 조작을 위한 3D 개체 구성</span><span class="sxs-lookup"><span data-stu-id="ebaef-110">Configure 3D objects for basic manipulation such as move, rotate, and scale</span></span>
* <span data-ttu-id="ebaef-111">근거리 및 원거리 조작 살펴보기</span><span class="sxs-lookup"><span data-stu-id="ebaef-111">Explore near and far interaction</span></span>
* <span data-ttu-id="ebaef-112">잡기 및 터치와 같은 추가적인 손 추적 제스처 알아보기</span><span class="sxs-lookup"><span data-stu-id="ebaef-112">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="ebaef-113">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="ebaef-113">Importing the tutorial assets</span></span>

<span data-ttu-id="ebaef-114">다음 Unity 사용자 지정 패키지를 다운로드하여 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-114">Download and import the Unity custom package:</span></span>

* [<span data-ttu-id="ebaef-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span><span class="sxs-lookup"><span data-stu-id="ebaef-115">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

<span data-ttu-id="ebaef-116">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-116">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="ebaef-118">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-118">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="decluttering-the-scene-view"></a><span data-ttu-id="ebaef-119">장면 보기 정리</span><span class="sxs-lookup"><span data-stu-id="ebaef-119">Decluttering the scene view</span></span>

<span data-ttu-id="ebaef-120">장면을 좀 더 쉽게 작업할 수 있도록 개체 왼쪽의 **눈** 아이콘을 클릭하여 **큐브** 및 **ButtonCollection** 개체의 **장면 표시 유형**을 끄기로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-120">To make it easier to work with your scene, set the **scene visibility** for the **Cube** and **ButtonCollection** objects to off by clicking the **eye** icon to the left of the objects.</span></span> <span data-ttu-id="ebaef-121">이렇게 하면 다음과 같이 게임 내 표시 유형을 변경하지 않고 [장면] 창에서 개체를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-121">This hides the object in the Scene window without changing their in-game visibility:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="ebaef-123">장면 표시 유형 컨트롤에 대한 내용 및 이 컨트롤을 사용하여 장면 보기와 워크플로를 최적화하는 방법에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">장면 표시 유형</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebaef-123">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can visit Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

## <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="ebaef-124">컬렉션에서 3D 개체 구성</span><span class="sxs-lookup"><span data-stu-id="ebaef-124">Organizing 3D objects in a collection</span></span>

<span data-ttu-id="ebaef-125">이 섹션에서는 이 자습서의 다음 섹션에서 3D 개체와 상호 작용하는 다양한 방법을 살펴볼 때 사용할 3D 개체 패널을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-125">In this section, you will create a panel of 3D objects which you will use when exploring various ways of interacting with 3D objects in the following sections of this tutorial.</span></span> <span data-ttu-id="ebaef-126">특히 3 x 3 그리드에 배치되도록 3D 개체를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-126">Specifically, you will configure the 3D objects to be positioned on a 3 x 3 grid.</span></span>

<span data-ttu-id="ebaef-127">[단추 패널을 만들 때](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection)와 마찬가지로, 여기서 수행할 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-127">Similarly to when you [created a panel of buttons](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), the main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="ebaef-128">3D 개체를 부모 개체의 부모로 지정</span><span class="sxs-lookup"><span data-stu-id="ebaef-128">Parent the 3D objects to a parent object</span></span>
2. <span data-ttu-id="ebaef-129">Grid Object Collection(스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="ebaef-129">Add and configure the Grid Object Collection (Script) component</span></span>

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a><span data-ttu-id="ebaef-130">1. 3D 개체를 부모 개체의 부모로 지정</span><span class="sxs-lookup"><span data-stu-id="ebaef-130">1. Parent the 3D objects to a parent object</span></span>

<span data-ttu-id="ebaef-131">[계층 구조] 창에서 **빈 개체를 만들고**, 적절한 이름(예: **3DObjectCollection**)을 지정하고, 적절한 위치(예: X = 0, Y =-0.2, Z = 2)에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-131">In the Hierarchy window, **create an empty object**, give it a suitable name, for example, **3DObjectCollection**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

<span data-ttu-id="ebaef-132">[프로젝트] 창에서 **자산** > **MRTK.Tutorials.GettingStarted** > **프리팹**으로 이동하여 다음 프리팹을 **3DObjectCollection**의 **부모로 지정**합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-132">In the Project window, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs**, then **parent** the following prefabs to the **3DObjectCollection**:</span></span>

* <span data-ttu-id="ebaef-133">Cheese</span><span class="sxs-lookup"><span data-stu-id="ebaef-133">Cheese</span></span>
* <span data-ttu-id="ebaef-134">CoffeeCup</span><span class="sxs-lookup"><span data-stu-id="ebaef-134">CoffeeCup</span></span>
* <span data-ttu-id="ebaef-135">EarthCore</span><span class="sxs-lookup"><span data-stu-id="ebaef-135">EarthCore</span></span>
* <span data-ttu-id="ebaef-136">Octa</span><span class="sxs-lookup"><span data-stu-id="ebaef-136">Octa</span></span>
* <span data-ttu-id="ebaef-137">Platonic</span><span class="sxs-lookup"><span data-stu-id="ebaef-137">Platonic</span></span>
* <span data-ttu-id="ebaef-138">TheModule</span><span class="sxs-lookup"><span data-stu-id="ebaef-138">TheModule</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

<span data-ttu-id="ebaef-140">다음과 같이 [계층 구조] 창에서 **3DObjectCollection** 개체의 자식 개체로 **3개 큐브를 만들고** 변환 **배율**을 X = 0.15, Y = 0.15, Z = 0.15로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-140">In the Hierarchy window, **create three cubes** as a child objects of the **3DObjectCollection** and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="ebaef-142">위에 나열된 단계를 수행하는 방법은 [사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성](mrlearning-base-ch2.md) 자습서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ebaef-142">For a reminder on how to do the steps listed above, you can refer to the [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md) tutorial.</span></span>

<span data-ttu-id="ebaef-143">각 큐브를 볼 수 있도록 다음과 같이 큐브 위치를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-143">Reposition the cubes so you can see each cube:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

<span data-ttu-id="ebaef-145">[프로젝트] 창에서 **자산** > **MixedRealityToolkit.SDK** > **StandardAssets** > **재질**로 이동하여 MRTK와 함께 제공된 재질을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-145">In the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** to see materials provided with the MRTK.</span></span>

<span data-ttu-id="ebaef-146">다음과 같은 적절한 재질을 **클릭**하여 각 큐브의 메시 렌더러 **재질** 요소 0 속성으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-146">**Click-and-drag** a suitable material on to each cube's Mesh Renderer **Materials** Element 0 property, for example:</span></span>

* <span data-ttu-id="ebaef-147">MRTK_Standard_GlowingCyan</span><span class="sxs-lookup"><span data-stu-id="ebaef-147">MRTK_Standard_GlowingCyan</span></span>
* <span data-ttu-id="ebaef-148">MRTK_Standard_GlowingOrange</span><span class="sxs-lookup"><span data-stu-id="ebaef-148">MRTK_Standard_GlowingOrange</span></span>
* <span data-ttu-id="ebaef-149">MRTK_Standard_Green</span><span class="sxs-lookup"><span data-stu-id="ebaef-149">MRTK_Standard_Green</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="ebaef-151">2. Grid Object Collection(스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="ebaef-151">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="ebaef-152">**3DObjectCollection** 개체에 **Grid Object Collection(스크립트)** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-152">Add a **Grid Object Collection (Script)** component to the **3DObjectCollection** object, and configure it as follows:</span></span>

* <span data-ttu-id="ebaef-153">자식 개체가 부모 개체 아래에 배치된 순서대로 정렬되도록 **정렬 형식**을 **자식 개체**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-153">Change **Sort Type** to **Child Order** to ensure the child objects are sorted in the order you have placed them under the parent object</span></span>

<span data-ttu-id="ebaef-154">그런 다음, 다음과 같이 **컬렉션 업데이트** 단추를 클릭하여 새 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-154">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a><span data-ttu-id="ebaef-156">3D 개체 조작</span><span class="sxs-lookup"><span data-stu-id="ebaef-156">Manipulating 3D objects</span></span>

<span data-ttu-id="ebaef-157">이 섹션에서는 이전 섹션에서 만든 패널의 모든 3D 개체를 조작하는 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-157">In this section, you will add the ability to manipulate all the 3D objects in the panel you created in the previous section.</span></span> <span data-ttu-id="ebaef-158">그리고 프리팹 개체의 경우 사용자가 추적 손으로 이러한 개체에 손을 뻗어 잡을 수 있도록 설정할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-158">Additionally, for the prefab objects, you will enable users to reach out and grab these objects with tracked hands.</span></span> <span data-ttu-id="ebaef-159">그런 다음, 개체에 적용할 수 있는 몇 가지 조작 동작을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-159">Then you will explore a few manipulation behaviors that you can apply to your objects.</span></span>

<span data-ttu-id="ebaef-160">이를 위해 수행할 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-160">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="ebaef-161">모든 개체에 조작 처리기(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-161">Add the Manipulation Handler (Script) component to all the objects</span></span>
2. <span data-ttu-id="ebaef-162">프리팹 개체에 근거리 잡기형 상호 작용(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-162">Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>
3. <span data-ttu-id="ebaef-163">조작 처리기(스크립트) 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="ebaef-163">Configure the Manipulation Handler (Script) component</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ebaef-164">**개체를 조작**하려면 개체에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-164">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="ebaef-165">**충돌체** 구성 요소(예: 상자 충돌체)</span><span class="sxs-lookup"><span data-stu-id="ebaef-165">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="ebaef-166">**조작 처리기(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="ebaef-166">**Manipulation Handler (Script)** component</span></span>
>
> <span data-ttu-id="ebaef-167">추적 손으로 개체에 대한 **조작** 및 **잡기**를 수행하려면 개체에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-167">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="ebaef-168">**충돌체** 구성 요소(예: 상자 충돌체)</span><span class="sxs-lookup"><span data-stu-id="ebaef-168">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="ebaef-169">**조작 처리기(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="ebaef-169">**Manipulation Handler (Script)** component</span></span>
> * <span data-ttu-id="ebaef-170">**근거리 잡기형 상호 작용(스크립트) 구성 요소**</span><span class="sxs-lookup"><span data-stu-id="ebaef-170">**Near Interaction Grabbable (Script)** component</span></span>

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a><span data-ttu-id="ebaef-171">1. 모든 개체에 조작 처리기(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-171">1. Add the Manipulation Handler (Script) component to all the objects</span></span>

<span data-ttu-id="ebaef-172">[계층 구조] 창에서 **Cheese** 개체를 선택하고, **Shift** 키를 누른 채 **Cube () 2** 개체를 선택하고, 모든 개체에 **조작 처리기(스크립트)** 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-172">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **Cube () 2** object and add the **Manipulation Handler (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="ebaef-174">이 자습서의 학습 목표를 달성하기 위해 이미 프리팹에 충돌체가 추가되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-174">For the purpose of this tutorial, colliders have already been added to the prefabs.</span></span> <span data-ttu-id="ebaef-175">큐브 개체와 같은 Unity 기본 형식의 경우 개체를 만들 때 충돌체 구성 요소가 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-175">For Unity primitives, such as the Cube objects, the Collider component is automatically added when the object is created.</span></span> <span data-ttu-id="ebaef-176">위의 이미지에서 충돌체는 녹색 윤곽선으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-176">In the image above, the colliders are represented by the green outlines.</span></span> <span data-ttu-id="ebaef-177">충돌체에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">충돌체</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebaef-177">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a><span data-ttu-id="ebaef-178">2. 프리팹 개체에 근거리 잡기형 상호 작용(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-178">2. Add the Near Interaction Grabbable (Script) component to the prefab objects</span></span>

<span data-ttu-id="ebaef-179">[계층 구조] 창에서 **Cheese** 개체를 선택하고, **Shift** 키를 누른 채 **TheModule** 개체를 선택하고, 모든 개체에 **근거리 잡기형 상호 작용(스크립트)** 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-179">In the Hierarchy window, select the **Cheese** object, hold down the **Shift** key, and then select the **TheModule** object and add the **Near Interaction Grabbable (Script)** component to all the objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a><span data-ttu-id="ebaef-181">3. 조작 처리기(스크립트) 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="ebaef-181">3. Configure the Manipulation Handler (Script) component</span></span>

#### <a name="default-manipulation"></a><span data-ttu-id="ebaef-182">기본 조작</span><span class="sxs-lookup"><span data-stu-id="ebaef-182">Default manipulation</span></span>

<span data-ttu-id="ebaef-183">**Cube** 개체의 경우 기본 조작 동작을 경험하도록 다음과 같이 모든 속성을 기본값으로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-183">For the **Cube** object, leave all properties at default, to experience the default manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> <span data-ttu-id="ebaef-185">구성 요소를 기본값으로 초기화하려면 구성 요소의 [설정] 아이콘을 선택하고 [초기화]를 선택하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-185">To reset a component to its default values, you can select the component's Settings icon and select Reset.</span></span>

#### <a name="restrict-manipulation-to-scale-only"></a><span data-ttu-id="ebaef-186">조작을 배율 전용으로 제한</span><span class="sxs-lookup"><span data-stu-id="ebaef-186">Restrict manipulation to scale only</span></span>

<span data-ttu-id="ebaef-187">**Cube (1)** 개체의 경우 사용자가 개체의 크기를 변경할 수 있도록 **양손 조작 유형**을 **배율**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-187">For the **Cube (1)** object, change **Two Handed Manipulation Type** to **Scale** to only allow the user to change the object's size:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a><span data-ttu-id="ebaef-189">사용자로부터 고정된 거리로 이동 제한</span><span class="sxs-lookup"><span data-stu-id="ebaef-189">Constrain the movement to a fixed distance from the user</span></span>

<span data-ttu-id="ebaef-190">**Cube (2)** 개체의 경우 이동된 개체가 사용자로부터 동일한 거리를 유지하도록 **이동에 대한 제약 조건**을 **Fix Distance From Head(헤드로부터의 거리 고정)** 로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-190">For the **Cube (2)** object, change **Constraint On Movement** to **Fix Distance From Head** so that when the object is moved, it stays at the same distance from the user:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a><span data-ttu-id="ebaef-192">기본 잡기형 조작</span><span class="sxs-lookup"><span data-stu-id="ebaef-192">Default grabbable manipulation</span></span>

<span data-ttu-id="ebaef-193">**Cheese**, **CoffeCup** 및 **EarthCore** 개체의 경우 기본 잡기형 조작 동작을 경험하도록 다음과 같이 모든 속성을 기본값으로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-193">For the **Cheese**, **CoffeCup**, and **EarthCore** objects, leave all properties at default, to experience the default grabbable manipulation behavior:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a><span data-ttu-id="ebaef-195">원거리 조작 기능 제거</span><span class="sxs-lookup"><span data-stu-id="ebaef-195">Remove the ability of far manipulation</span></span>

<span data-ttu-id="ebaef-196">**Octa** 개체의 경우 사용자가 추적 손을 사용하여 개체와 직접 상호 작용하는 것만 가능하도록 **원거리 조작 허용** 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-196">For the **Octa** object, un-check the **Allow Far Manipulation** checkbox to make it so the user can only interact with the object directly using tracked hands:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a><span data-ttu-id="ebaef-198">개체가 중심을 축으로 회전하도록 설정</span><span class="sxs-lookup"><span data-stu-id="ebaef-198">Make an object rotate around its center</span></span>

<span data-ttu-id="ebaef-199">**Platonic** 개체의 경우 사용자가 한 손으로 개체를 돌리면 개체가 중심을 축으로 회전하도록 **한 손 회전 모드 근거리** 및 **한 손 회전 모드 원거리**를 **개체 중심을 축으로 회전**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-199">For the **Platonic** object, change **One Hand Rotation Mode Near** and **One Hand Rotation Mode Far** to **Rotate About Object Center** to make it so when the user rotates the object with one hand, it rotates around the object's center:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a><span data-ttu-id="ebaef-201">개체가 릴리스된 후 이동 유지</span><span class="sxs-lookup"><span data-stu-id="ebaef-201">Keep movement after object is released</span></span>

<span data-ttu-id="ebaef-202">**TheModule** 개체의 경우 물리학을 사용하도록 **Rigidbody** 구성 요소를 추가한 다음, 개체가 중력의 영향을 받지 않도록 **중력 사용** 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-202">For the **TheModule** object, add a **Rigidbody** component to enable physics, and then un-check the **Use Gravity** checkbox so the object is not affected by gravity:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

<span data-ttu-id="ebaef-204">다시 조작 처리기(스크립트) 구성 요소에서, 개체가 사용자의 손에서 떨어지면 계속 움직이도록 **릴리스 동작**이 **속도 유지** 및 **각속도 유지**로 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-204">Back on the Manipulation Handler (Script) component, verify that the **Release Behavior** is set to both **Keep Velocity** and **Keep Angular Velocity** so that once the object is released from the user's hand, it continues to move:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

<span data-ttu-id="ebaef-206">조작 처리기 구성 요소 및 관련 속성에 대한 자세한 내용을 보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [조작 처리기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebaef-206">To learn more about the Manipulation handler component and its associated properties, you can visit the [Manipulation handler](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="ebaef-207">경계 상자 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-207">Adding bounding boxes</span></span>

<span data-ttu-id="ebaef-208">경계 상자를 사용하면 크기 조정 및 회전에 사용할 수 있는 핸들을 제공하여 근거리 및 원거리 상호 작용 모두에서 한 손으로 개체를 보다 쉽고 직관적으로 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-208">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="ebaef-209">이 예제에서는 EarthCore 개체에 경계 상자를 추가할 것입니다. 그러면 이전 섹션에서 구성한 개체 조작을 사용하여 이 개체와 상호 작용하고, 경계 상자 핸들을 사용하여 크기를 조정하고 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-209">In this example, you will add a bounding box to the EarthCore object so this object can now be interacted with using the object manipulation you configured in the previous section, as well as, scaled and rotated using the bounding box handles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ebaef-210">**경계 상자**를 사용하려면 개체에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-210">To be able to use a **bounding box**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="ebaef-211">**충돌체** 구성 요소(예: 상자 충돌체)</span><span class="sxs-lookup"><span data-stu-id="ebaef-211">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="ebaef-212">**경계 상자(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="ebaef-212">**Bounding Box (Script)** component</span></span>

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a><span data-ttu-id="ebaef-213">1. EarthCore 개체에 경계 상자(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-213">1. Add the Bounding Box (Script) component to the EarthCore object</span></span>

<span data-ttu-id="ebaef-214">[검사기] 창에서 **EarthCore** 개체를 선택하고 EarthCore 개체에 **경계 상자(스크립트)** 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-214">In the Inspector window, select the **EarthCore** object and add the **Bounding Box (Script)** component to the EarthCore object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> <span data-ttu-id="ebaef-216">런타임에 경계 상자 시각화가 생성되므로 게임 모드로 전환하기 전에는 보이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-216">The Bounding Box visualizations is created at run time and therefore not visible before you enter Game mode.</span></span>

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a><span data-ttu-id="ebaef-217">2. 편집기 내 시뮬레이션을 사용하여 경계 상자 시각화 및 테스트</span><span class="sxs-lookup"><span data-stu-id="ebaef-217">2. Visualize and test the bounding box using the in-editor simulation</span></span>

<span data-ttu-id="ebaef-218">[재생] 단추를 눌러 게임 모드로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-218">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="ebaef-219">그리고 다음과 같이 스페이스바를 길게 눌러 손을 호출하고 마우스를 사용하여 경계 상자와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-219">Then press and hold the spacebar to bring up the hand and use the mouse to interact with the bounding box:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

<span data-ttu-id="ebaef-221">경계 상자 구성 요소 및 관련 속성에 대한 자세한 내용을 보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [조작 처리기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebaef-221">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-touch-effects"></a><span data-ttu-id="ebaef-222">터치 효과 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-222">Adding touch effects</span></span>

<span data-ttu-id="ebaef-223">이 예제에서는 손으로 개체를 터치할 때 이벤트를 트리거하도록 설정할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-223">In this example, you will enable events to be triggered when you touch an object with your hand.</span></span> <span data-ttu-id="ebaef-224">특히 사용자가 Octa 개체를 터치하면 소리 효과를 재생하도록 구성하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-224">Specifically, you will configure the Octa object to play a sound effect when the user touches it.</span></span>

<span data-ttu-id="ebaef-225">이를 위해 수행할 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-225">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="ebaef-226">개체에 오디오 원본 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-226">Add an Audio Source component to the object</span></span>
2. <span data-ttu-id="ebaef-227">개체에 근거리 터치형 상호 작용(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-227">Add the Near Interaction Touchable (Script) component to the object</span></span>
3. <span data-ttu-id="ebaef-228">개체에 손 상호 작용 터치(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-228">Add the Hand Interaction Touch (Script) component to the object</span></span>
4. <span data-ttu-id="ebaef-229">On Touch Started 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="ebaef-229">Implement the On Touch Started event</span></span>
5. <span data-ttu-id="ebaef-230">편집기 내 시뮬레이션을 사용하여 터치 상호 작용 테스트</span><span class="sxs-lookup"><span data-stu-id="ebaef-230">Test the touch interaction using the in-editor simulation</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ebaef-231">**터치 이벤트를 트리거**하려면 개체에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-231">To be able to **trigger touch events**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="ebaef-232">**충돌체** 구성 요소. 가급적이면 상자 충돌체</span><span class="sxs-lookup"><span data-stu-id="ebaef-232">**Collider** component, preferably a Box Collider</span></span>
> * <span data-ttu-id="ebaef-233">**근거리 터치형 상호 작용(스크립트) 구성 요소**</span><span class="sxs-lookup"><span data-stu-id="ebaef-233">**Near Interaction Touchable (Script)** component</span></span>
> * <span data-ttu-id="ebaef-234">**손 상호 작용 터치(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="ebaef-234">**Hand Interaction Touch (Script)** component</span></span>

> [!NOTE]
> <span data-ttu-id="ebaef-235">손 상호 작용 터치(스크립트) 구성 요소는 MRTK에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-235">The Hand Interaction Touch (Script) component is not part of MRTK.</span></span> <span data-ttu-id="ebaef-236">이 자습서의 자산과 함께 가져왔으며 원래는 MixedReality Toolkit Unity 예제에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-236">It was imported with this tutorial's assets and originally part of the MixedReality Toolkit Unity Examples.</span></span>

### <a name="1-add-an-audio-source-component-to-the-object"></a><span data-ttu-id="ebaef-237">1. 개체에 오디오 원본 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-237">1. Add an Audio Source component to the object</span></span>

<span data-ttu-id="ebaef-238">다음과 같이 [계층 구조] 창에서 **Octa** 개체를 선택하고 **오디오 원본** 구성 요소를 Octa 개체에 추가한 다음, 공간 오디오를 사용하도록 **공간 블렌드**를 1로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-238">In the Hierarchy window, select the **Octa** object, add an **Audio Source** component to the Octa object, and then change **Spatial Blend** to 1 to enable spatial audio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a><span data-ttu-id="ebaef-240">2. 개체에 근거리 터치형 상호 작용(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-240">2. Add the Near Interaction Touchable (Script) component to the object</span></span>

<span data-ttu-id="ebaef-241">다음과 같이 **Octa** 개체를 선택한 상태에서 **근거리 터치형 상호 작용(스크립트)** 구성 요소를 Octa 개체에 추가한 다음, **경계 고정** 및 **중심 고정** 단추를 클릭하여 근거리 터치형 상호 작용(스크립트)의 로컬 중심 및 경계 속성을 BoxCollider에 맞게 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-241">With the **Octa** object still selected, add the **Near Interaction Touchable (Script)** component to the Octa object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a><span data-ttu-id="ebaef-243">3. 개체에 손 상호 작용 터치(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="ebaef-243">3. Add the Hand Interaction Touch (Script) component to the object</span></span>

<span data-ttu-id="ebaef-244">다음과 같이 **Octa** 개체를 선택한 상태에서 **손 상호 작용 터치(스크립트)** 구성 요소를 Octa 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-244">With the **Octa** object still selected, add the **Hand Interaction Touch (Script)** component to the Octa object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a><span data-ttu-id="ebaef-246">4. On Touch Started 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="ebaef-246">4. Implement the On Touch Started event</span></span>

<span data-ttu-id="ebaef-247">**손 상호 작용 터치(스크립트)** 구성 요소에서 작은 **+** 아이콘을 클릭하여 새 **On Touch Started ()** 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-247">On the **Hand Interaction Touch (Script)** component, click the small **+** icon to create a new **On Touch Started ()** event.</span></span> <span data-ttu-id="ebaef-248">다음과 같이 이벤트를 수신하도록 **Octa** 개체를 구성하고 트리거할 동작으로 **AudioSource.PlayOneShot**을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-248">Then configure the **Octa** object to receive the event and define **AudioSource.PlayOneShot** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

<span data-ttu-id="ebaef-250">**자산** > **MixedRealityToolkit.SDK** > **StandardAssets** > 재질로 이동하여 MRTK와 함께 제공된 오디오 클립을 살펴본 다음, **오디오 클립** 필드에 적절한 오디오 클립(예: MRTK_Gem 오디오 클립)을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-250">Navigate to **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials to see audio clips provided with the MRTK, and then assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> <span data-ttu-id="ebaef-252">이벤트를 구현하는 방법에 대한 내용은 [손 추적 제스처 및 상호 작용 가능 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ebaef-252">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a><span data-ttu-id="ebaef-253">5. 편집기 내 시뮬레이션을 사용하여 터치 상호 작용 테스트</span><span class="sxs-lookup"><span data-stu-id="ebaef-253">5. Test the touch interaction using the in-editor simulation</span></span>

<span data-ttu-id="ebaef-254">[재생] 단추를 눌러 게임 모드로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-254">Press the Play button to enter Game mode.</span></span> <span data-ttu-id="ebaef-255">다음과 같이 스페이스바를 길게 눌러 손을 호출하고 마우스로 Octa 개체를 터치하여 소리 효과를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-255">Then press and hold the spacebar to bring up the hand and use the mouse to touch the Octa object and trigger the sound effect:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> <span data-ttu-id="ebaef-257">터치 상호 작용을 테스트할 때, 그리고 위의 이미지에서 본 것처럼, Octa 개체를 터치할 때 색이 맥동합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-257">As you saw when testing the touch interaction, and as shown in the image above, the Octa object color pulsated while it was touched.</span></span> <span data-ttu-id="ebaef-258">이 효과는 손 상호 작용 터치(스크립트) 구성 요소에 하드 코딩되며 위의 단계에서 완료한 이벤트 구성의 결과물이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-258">This effect is hard coded into the Hand Interaction Touch (Script) component and not a result of the event configuration you completed in the steps above.</span></span>
>
> <span data-ttu-id="ebaef-259">이 효과를 사용하지 않도록 설정하려면 줄 32 'TargetRenderer = GetComponentInChildren<Renderer>();'를 주석 처리하면 됩니다. 그러면 TargetRenderer가 null로 유지되고 색이 맥동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-259">If you want to disable this effect, you can, for example, comment out or line 32 'TargetRenderer = GetComponentInChildren<Renderer>();' which will result in the TargetRenderer remaining null and the color not pulsating.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ebaef-260">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-260">Congratulations</span></span>

<span data-ttu-id="ebaef-261">이 자습서에서는 그리드 컬렉션에서 3D 개체를 구성하는 방법과 근거리 상호 작용(추적 손으로 직접 잡기) 및 원거리 상호 작용(응시 레이 또는 손 레이 사용)을 사용하여 이러한 개체를 조작(크기 조정, 회전 및 이동)하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-261">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="ebaef-262">또한 3D 개체 주위에 경계 상자를 배치하는 방법과 경계 상자에서 핸들을 사용하고 사용자 지정하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-262">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the handles on the bounding boxes.</span></span> <span data-ttu-id="ebaef-263">마지막으로 개체를 터치할 때 이벤트를 트리거하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="ebaef-263">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="ebaef-264">다음 단원: 6. 고급 입력 옵션 탐색</span><span class="sxs-lookup"><span data-stu-id="ebaef-264">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
