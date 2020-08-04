---
title: 시작 자습서 - 4. 장면에서 개체 위치 지정
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여 줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 71990db23b5154de916f0eda86a978885ab53547
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376635"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="782bf-105">4. 장면에서 개체 위치 지정</span><span class="sxs-lookup"><span data-stu-id="782bf-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="782bf-106">개요</span><span class="sxs-lookup"><span data-stu-id="782bf-106">Overview</span></span>

<span data-ttu-id="782bf-107">이 자습서에서는 자습서 자산을 가져오고 제공된 개체를 장면에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-107">In this tutorial, you will import the tutorial assets and position the provided objects in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="782bf-108">목표</span><span class="sxs-lookup"><span data-stu-id="782bf-108">Objectives</span></span>

* <span data-ttu-id="782bf-109">장면에 개체를 배치하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="782bf-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="782bf-110">MRTK의 그리드 개체 컬렉션 기능을 사용하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="782bf-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="782bf-111">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="782bf-111">Importing the tutorial assets</span></span>

<span data-ttu-id="782bf-112">다음 Unity 사용자 지정 패키지를 다운로드하여 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-112">Download and import the following Unity custom package:</span></span>

* [<span data-ttu-id="782bf-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="782bf-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

<span data-ttu-id="782bf-114">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-114">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="782bf-116">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [MRTK 가져오기](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-116">For a reminder on how to import a Unity custom package, you can refer to the [Importing the MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="creating-the-parent-object"></a><span data-ttu-id="782bf-117">부모 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="782bf-117">Creating the parent object</span></span>

<span data-ttu-id="782bf-118">Hierarchy 창에서 빈 영역을 마우스 오른쪽 단추로 클릭하고, **빈 항목 만들기**를 선택하여 빈 개체를 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-118">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="782bf-120">위의 이미지처럼 장면 및 게임 창을 나란히 표시하려면 게임 창을 장면 창의 오른쪽으로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-120">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="782bf-121">작업 영역을 사용자 지정하는 방법에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="782bf-121">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="782bf-122">새로 만든 개체를 마우스 오른쪽 단추로 클릭하고, **이름 바꾸기**를 선택하고, 이름을 **RoverExplorer**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-122">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-2.png)

<span data-ttu-id="782bf-124">RoverExplorer 개체가 선택된 상태에서 Inspector 창에서 다음과 같이 **Transform** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-124">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="782bf-125">**위치**: X = 0, Y = -0.6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="782bf-125">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="782bf-126">**회전**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="782bf-126">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="782bf-127">**크기 조정**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="782bf-127">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="782bf-129">카메라는 사용자 헤드를 나타내며 원점, X = 0, Y = 0, Z = 0에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-129">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="782bf-130">일반적으로 Unity의 1단위는 실제 세계의 약 1미터입니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-130">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="782bf-131">하지만 여기에는 예외가 있습니다. 예를 들어 개체가 크기 조정된 개체의 자식인 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-131">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="782bf-132">위의 시나리오에서 RoverExplorer는 2미터 앞에 배치되고 사용자 헤드보다 0.6 미터 아래에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-132">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="782bf-133">자습서 프리팹 추가</span><span class="sxs-lookup"><span data-stu-id="782bf-133">Adding the tutorial prefabs</span></span>

<span data-ttu-id="782bf-134">Project 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-134">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="782bf-136"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">프리팹</a>은 Unity로 저장된 미리 구성된 GameObject이며 프로젝트 전체에서 재사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-136">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="782bf-137">Project 창에서 **Table** 프리팹을 클릭하여 RoverExplorer 개체의 자식이 되도록 **RoverExplorer** 개체에 끌어 놓은 다음, Inspector 창에서 다음과 같이 **Transform** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-137">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="782bf-138">**위치**: X = 0, Y = -0.005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="782bf-138">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="782bf-139">**회전**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="782bf-139">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="782bf-140">**크기 조정**: X = 1.2, Y = 0.01, Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="782bf-140">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="782bf-142">위의 이미지에 표시된 것처럼 장면을 표시하려면 장면 창의 오른쪽 위 모서리에 있는 <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">장면 Gizmo</a>를 사용하여 시야각이 전방 Z 축을 따라 이동하도록 조정하고, MixedRealityPlayspace 개체를 두 번 클릭하여 카메라에 포커스를 설정하고, 필요에 따라 확대합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-142">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="782bf-143">Project 창에서 **RoverAssembly** 프리팹을 클릭하여 RoverExplorer 개체의 자식으로 만들도록 **RoverExplorer** 개체로 끌어 놓은 다음, Inspector 창에서 다음과 같이 **Transform** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-143">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="782bf-144">**위치**: X = -0.1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="782bf-144">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="782bf-145">**회전**: X = 0, Y = -135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="782bf-145">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="782bf-146">**크기 조정**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="782bf-146">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="782bf-148">컬렉션에서 개체 구성</span><span class="sxs-lookup"><span data-stu-id="782bf-148">Organizing objects in a collection</span></span>

<span data-ttu-id="782bf-149">Hierarchy 창에서 **RoverExplorer** 개체를 마우스 오른쪽 단추로 클릭하고 **빈 항목 만들기**를 선택하여 빈 개체를 RoverExplorer의 자식으로 추가하고, 개체 이름을 **RoverParts**로 설정하고 **Transform** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-149">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="782bf-150">**위치**: X = 0, Y = 0.06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="782bf-150">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="782bf-151">**회전**: X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="782bf-151">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="782bf-152">**크기 조정**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="782bf-152">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-1.png)

<span data-ttu-id="782bf-154">Hierarchy 창에서 모든 RoverExplorer > RoverAssembly > RoverModel > **Parts** 자식 개체를 선택하고, 마우스 오른쪽 단추로 클릭하고 **중복**을 선택하여 각 파트의 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-154">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="782bf-156">인접 개체를 여러 개 선택하려면 SHIFT 키를 누른 채 마우스를 사용하여 첫 번째 및 마지막 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-156">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="782bf-157">새로 중복된 Parts 자식 개체가 선택된 상태에서 이를 클릭하여 **RoverParts** 개체로 끌어 놓아 RoverParts 개체의 자식 개체로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-157">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-3.png)

<span data-ttu-id="782bf-159">장면 작업을 더 쉽게 수행할 수 있도록 Hierarchy 창에서 개체 왼쪽의 **눈** 아이콘을 클릭하여 **RoverExplorer** 개체에 대한 **장면 표시 유형**을 끄기로 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-159">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverExplorer** object off.</span></span> <span data-ttu-id="782bf-160">이렇게 하면 다음과 같이 게임 내 표시 유형을 변경하지 않고 장면 창에서 개체를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-160">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> <span data-ttu-id="782bf-162">장면 표시 유형 컨트롤에 대한 내용 및 이 컨트롤을 사용하여 장면 보기와 워크플로를 최적화하는 방법에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">장면 표시 유형</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="782bf-162">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="782bf-163">Hierarchy 창에서 추가된 **(1)** 을 **_Part**로 바꿔 RoverParts 자식 개체의 이름을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-163">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-5.png)

<span data-ttu-id="782bf-165">Hierarchy 창에서 **RoverParts** 개체를 선택한 다음, Inspector 창에서 **구성 요소 추가** 단추를 클릭하고, **GridObjectCollection**을 검색하고 선택하여 GridObjectCollection 구성 요소를 RoverParts 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-165">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-6.png)

<span data-ttu-id="782bf-167">다음과 같이 **GridObjectCollection** 구성 요소 값을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-167">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="782bf-168">**정렬 유형**: 사전순</span><span class="sxs-lookup"><span data-stu-id="782bf-168">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="782bf-169">**레이아웃**: 수평</span><span class="sxs-lookup"><span data-stu-id="782bf-169">**Layout**: Horizontal</span></span>
* <span data-ttu-id="782bf-170">**셀 너비**: 0.25</span><span class="sxs-lookup"><span data-stu-id="782bf-170">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="782bf-171">**부모에서의 거리**: 0.38</span><span class="sxs-lookup"><span data-stu-id="782bf-171">**Distance from parent**: 0.38</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-7.png)

<span data-ttu-id="782bf-173">그런 다음, **컬렉션 업데이트** 단추를 클릭하여 RoverParts 자식 개체의 위치를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-173">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="782bf-175">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-175">Congratulations</span></span>

<span data-ttu-id="782bf-176">이 자습서에서는 사용자를 기준으로 장면에 개체를 배치하고 MRTK의 그리드 개체 컬렉션 기능을 사용하여 컬렉션의 개체를 구성하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="782bf-176">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

[<span data-ttu-id="782bf-177">다음 자습서: 5. 해결기를 사용하여 동적 콘텐츠 만들기</span><span class="sxs-lookup"><span data-stu-id="782bf-177">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
