---
title: 시작 자습서 - 5. Solver를 사용하여 동적 콘텐츠 만들기
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: cbeaa8b65b7aecc0600294b3739fedfb903e568e
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306656"
---
# <a name="5-creating-dynamic-content-using-solvers"></a><span data-ttu-id="a6ddf-105">5. Solver를 사용하여 동적 콘텐츠 만들기</span><span class="sxs-lookup"><span data-stu-id="a6ddf-105">5. Creating dynamic content using Solvers</span></span>

## <a name="overview"></a><span data-ttu-id="a6ddf-106">개요</span><span class="sxs-lookup"><span data-stu-id="a6ddf-106">Overview</span></span>

<span data-ttu-id="a6ddf-107">이 자습서에서는 복잡한 공간 배치 시나리오를 해결하기 위해 MRTK의 사용 가능한 배치 도구인 Solver를 사용하여 홀로그램을 동적으로 배치하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-107">In this tutorial, you will explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="a6ddf-108">MRTK의 Solver는 개체가 사용자 또는 장면의 기타 게임 개체를 따르도록 만드는 데 사용되는 스크립트 및 동작 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-108">In the MRTK, Solvers are a system of scripts and behaviors used to allow objects to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="a6ddf-109">또한 특정 위치에 맞춰서 앱을 보다 직관적으로 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-109">They can also be used to snap to certain positions, making your app more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="a6ddf-110">목표</span><span class="sxs-lookup"><span data-stu-id="a6ddf-110">Objectives</span></span>

* <span data-ttu-id="a6ddf-111">MRTK 해결기 소개</span><span class="sxs-lookup"><span data-stu-id="a6ddf-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="a6ddf-112">Solver를 사용하여 사용자를 개체로 안내하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="a6ddf-112">Learn how to use Solvers to direct the user to objects</span></span>
* <span data-ttu-id="a6ddf-113">Solver를 사용하여 개체의 위치를 변경하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="a6ddf-113">Learn how to use Solvers to reposition objects</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="a6ddf-114">MRTK에서 해결기의 위치</span><span class="sxs-lookup"><span data-stu-id="a6ddf-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="a6ddf-115">MRTK의 해결기는 MRTK SDK 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="a6ddf-116">프로젝트에서 사용할 수 있는 Solver를 보려면 프로젝트 창에서 **Assets** > **MRTK** > **SDK** > **Features** > **Utilities** > **Solvers**로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MRTK** > **SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section1-step1-1.png)

<span data-ttu-id="a6ddf-118">이 자습서에서는 Directional Indicator(방향 표시) Solver 및 Tap To Place(탭하여 위치 지정) Solver 구현을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-118">In this tutorial, we will review the implementation of the Directional Indicator Solver and the Tap To Place Solver.</span></span> <span data-ttu-id="a6ddf-119">MRTK에서 사용할 수 있는 Solver의 전체 범위를 알아보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-119">To learn more about the full range of Solvers available in the MRTK, you can refer to the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!NOTE]
> <span data-ttu-id="a6ddf-120">Directional Indicator(방향 표시) Solver는 실험적인 기능이 때문에 위에 언급된 Solver 폴더에 없지만 Assets > MRTK > SDK > Experimental > Features > Utilities 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-120">The Directional Indicator Solver is not located in the Solvers folders referenced above, but in the Assets > MRTK > SDK > Experimental > Features > Utilities folders, because it is an experimental feature.</span></span>

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a><span data-ttu-id="a6ddf-121">Directional Indicator(방향 표시) Solver를 사용하여 사용자를 개체로 안내</span><span class="sxs-lookup"><span data-stu-id="a6ddf-121">Using the Directional Indicator Solver to direct the user to objects</span></span>

<span data-ttu-id="a6ddf-122">프로젝트 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** 폴더로 이동하여 **Chevron** 프리팹을 클릭하여 Hierarchy(계층 구조) 창으로 끌어서 놓은 후 Transform(변환) **위치**를 X = 0, Y = 0, Z = 2로 설정하여 RoverExplorer 개체 근처에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-122">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **Chevron** prefab into the Hierarchy window, and set it's Transform **Position** to X = 0, Y = 0, Z = 2 to position it near the RoverExplorer object:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="a6ddf-124">카메라 또는 장면의 다른 아이콘이 개체를 숨기거나 방해가 되면, 위 이미지와 같이 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos를 끄기 위치로 전환</a>하여 아이콘을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-124">If you find that the camera or any other icons in your scene are hiding the objects or are distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span> <span data-ttu-id="a6ddf-125">Gizmo 메뉴에 대한 내용 및 이 메뉴를 사용하여 장면 보기를 최적화하는 방법에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmo 메뉴</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-125">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>

<span data-ttu-id="a6ddf-126">새로 추가된 Chevron 개체 **표시기**의 이름을 변경한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **DirectionalIndicator** 및 **Directional Indicator Controller(스크립트)** 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-126">Rename the newly added Chevron object **Indicator**, then in the Inspector window, use the **Add Component** button to add the **DirectionalIndicator** and the **Directional Indicator Controller (Script)** component:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="a6ddf-128">Solver를 추가하면(이 경우, DirectionalIndicator 구성 요소) SolverHandler 구성 요소가 Solver에 필요하기 때문에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-128">When you add a Solver, in this case, the DirectionalIndicator component, the SolverHandler component is automatically added because Solvers require it.</span></span>

> [!NOTE]
> <span data-ttu-id="a6ddf-129">Directional Indicator Controller(스크립트)는 MRTK의 일부는 아니지만 자습서 자산에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-129">The Directional Indicator Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="a6ddf-130">DirectionalIndicator 및 SolverHandler 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-130">Configure the DirectionalIndicator and SolverHandler components as follows:</span></span>

* <span data-ttu-id="a6ddf-131">**SolverHandler** 구성 요소의 **Tracked Target Type**(추적 대상 유형)이 **Head**로 설정되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="a6ddf-131">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="a6ddf-132">**RoverExplorer**를 Hierarchy(계층 구조) 창에서 **None (Transform)** 필드로 끌어서 놓아 **DirectionalIndicator** 구성 요소의 **Directional Target**(방향성 대상)에 할당</span><span class="sxs-lookup"><span data-stu-id="a6ddf-132">Assign the **RoverExplorer** to the **DirectionalIndicator** component's **Directional Target** by dragging it from the Hierarchy window into the **None (Transform)** field</span></span>
* <span data-ttu-id="a6ddf-133">**View Offset**(보기 오프셋)을 0.2로 변경</span><span class="sxs-lookup"><span data-stu-id="a6ddf-133">Change the **View Offset** to 0.2</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-3.png)

<span data-ttu-id="a6ddf-135">재생 단추를 눌러 게임 모드로 전환하고, 마우스 오른쪽 단추를 누른 상태에서 마우스를 왼쪽이나 오른쪽으로 움직여서 응시 방향을 회전하면서 다음 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-135">Press the Play button to enter Game mode, press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="a6ddf-136">RoverExplorer 개체에서 눈길을 돌리면 표시기 개체가 나타나고 RoverExplorer 개체를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-136">When you look away from the RoverExplorer object, the Indicator object will appear and point towards the RoverExplorer object</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="a6ddf-138">Scene(장면) 창에 카메라 광선이 보이지 않으면 위 이미지와 같이 Gizmo 메뉴가 활성화되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-138">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled, as shown in the image above.</span></span>

> [!TIP]
> <span data-ttu-id="a6ddf-139">편집기 내 입력 시뮬레이션을 사용하는 방법은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [편집기 내 손 입력 시뮬레이션을 사용하여 장면 테스트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-139">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!TIP]
> <span data-ttu-id="a6ddf-140">컴퓨터에 마이크가 있으면 음성 명령 "toggle diagnostics"를 사용하여 게임 창에 나타나는 Diagnostics(진단) 패널의 활성 상태를 쉽게 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-140">If your computer has a microphone, you can easily toggle the active state of the Diagnostics panel that appears in the Game window by using the speech command "toggle diagnostics."</span></span> <span data-ttu-id="a6ddf-141">또는, MRTK Configuration Profile(MRTK 구성 프로필) > Diagnostics(진단) > Enable Diagnostics System(진단 시스템 활성화)에서 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-141">Alternatively, you can disable it in the MRTK Configuration Profile > Diagnostics > Enable Diagnostics System.</span></span> <span data-ttu-id="a6ddf-142">하지만 일반적으로 개발 중에 Diagnostics System(진단 시스템)을 활성 상태로 유지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-142">However, it is generally recommended to keep the Diagnostics System active during development.</span></span>

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a><span data-ttu-id="a6ddf-143">Tap to Place(탭하여 위치 지정) Solver를 사용하여 개체 위치 변경</span><span class="sxs-lookup"><span data-stu-id="a6ddf-143">Using the Tap to Place Solver to reposition objects</span></span>

<span data-ttu-id="a6ddf-144">Hierarchy(계층 구조) 창에서 RoverExplorer > **RoverAssembly** 개체를 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **Tap To Place(스크립트)** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-144">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **Tap To Place (Script)** component, and configure it as follows:</span></span>

* <span data-ttu-id="a6ddf-145">**SolverHandler** 구성 요소의 **Tracked Target Type**(추적 대상 유형)이 **Head**로 설정되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="a6ddf-145">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="a6ddf-146">**Keep Orientation Vertical**(방향을 세로로 유지) 확인란 선택</span><span class="sxs-lookup"><span data-stu-id="a6ddf-146">Check the **Keep Orientation Vertical** checkbox</span></span>
* <span data-ttu-id="a6ddf-147">**Magnetic Surfaces**(자기 표면) > **Element 0**(요소 0) 드롭다운에서 **Spatial Awareness**(공간 인식)를 제외한 모든 옵션을 선택 취소</span><span class="sxs-lookup"><span data-stu-id="a6ddf-147">From the **Magnetic Surfaces** > **Element 0** dropdown, uncheck all options expect **Spatial Awareness**</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a6ddf-149">Magnetic Surfaces(자기 표면) 설정은 개체를 배치할 때 Tap To Place(스크립트) 구성 요소가 어떤 개체를 감지할 수 있는지 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-149">The Magnetic Surfaces setting determines which objects the Tap To Place (Script) component can detect when placing an object.</span></span> <span data-ttu-id="a6ddf-150">이 설정을 Spatial Awareness(공간 인식) 전용으로 변경하면 Tap To Place(스크립트) 구성 요소는 Spatial Awareness라는 Unity 레이어의 개체에만 Rover를 배치할 수 있으며, 이것은 기본적으로 HoloLens에서 생성된 공간 인식 메시입니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-150">By changing the setting to only Spatial Awareness, the Tap To Place (Script) component will only be able to place the Rover on objects on the Unity Layer named Spatial Awareness, which by default is the Spatial Awareness Mesh generated by the HoloLens.</span></span>
>
><span data-ttu-id="a6ddf-151">레이어에 대해 자세히 알아보려면 Unity의 <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">레이어</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-151">To learn more about Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Layers</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="a6ddf-152">HoloLens에서 Tap To Place 기능을 테스트할 때 공간 인식 메시를 보려면 Spatial Mesh Observer의 표시 옵션을 임시로 Visible로 설정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-152">If you want to see the Spatial Awareness Mesh when testing the Tap To Place functionality on your HoloLens, you can temporarily set the Spatial Mesh Observer's Display Option to Visible.</span></span> <span data-ttu-id="a6ddf-153">표시 옵션을 변경하는 방법은 [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-153">For a reminder on how to change the Display Option, you can refer to the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="a6ddf-154">Hierarchy(계층 구조) 창에서 RoverAssembly 개체를 선택한 상태로 Inspector(인스펙터) 창에서 **On Placing Started ()** 이벤트를 찾아서 **+** 아이콘을 클릭하여 새 이벤트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-154">With the RoverAssembly object still selected in the Hierarchy window, in the Inspector window, locate the **On Placing Started ()** event and click the **+** icon to add a new event:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-2.png)

<span data-ttu-id="a6ddf-156">이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-156">Configure the event as follows:</span></span>

* <span data-ttu-id="a6ddf-157">**RoverAssembly** 개체를 Hierarchy(계층 구조) 창에서 **None (Object)** 필드로 끌어서 놓아 On Placing Started () 이벤트의 수신기로 지정</span><span class="sxs-lookup"><span data-stu-id="a6ddf-157">Assign the **RoverAssembly** object as a listener for the On Placing Started () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="a6ddf-158">**No Function**(함수 없음) 드롭다운에서 **TapToPlace** > **float SurfaceNormalOffset**을 선택하여 이벤트가 트리거될 때 SurfaceNormalOffset 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="a6ddf-158">From the **No Function** dropdown, select **TapToPlace** > **float SurfaceNormalOffset** to update the SurfaceNormalOffset property value when the event is triggered</span></span>
* <span data-ttu-id="a6ddf-159">인수가 **0**으로 설정되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="a6ddf-159">Verify that the argument is set to **0**</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-3.png)

<span data-ttu-id="a6ddf-161">Hierarchy(계층 구조) 창에서 빈 지점을 마우스 오른쪽 단추로 클릭하고 **3D 개체** > **큐브**를 선택하여 지면을 나타내는 임시 개체를 생성하고 **Transform**(변환) 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-161">In the Hierarchy window, right-click on an empty spot and select **3D Object** > **Cube**, to create a temporary object representing the ground, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="a6ddf-162">**위치**: X = 0, Y = -1.65, Z = 6</span><span class="sxs-lookup"><span data-stu-id="a6ddf-162">**Position**: X = 0, Y = -1.65, Z = 6</span></span>
* <span data-ttu-id="a6ddf-163">**회전**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="a6ddf-163">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="a6ddf-164">**배율**: X = 10, Y = 0.2, Z = 10</span><span class="sxs-lookup"><span data-stu-id="a6ddf-164">**Scale**: X = 10, Y = 0.2, Z = 10</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-4.png)

<span data-ttu-id="a6ddf-166">Hierarchy(계층 구조) 창에서 임시 큐브를 선택한 상태로 Inspector(인스펙터) 창에서 **레이어** 드롭다운을 사용하여 큐브의 레이어 설정에 **Spatial Awareness**(공간 인식) 레이어만 포함하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-166">With the temporary Cube still selected in the Hierarchy window, in the Inspector window, use the **Layers** dropdown to change the Cube's Layer setting only to include the **Spatial Awareness** layer:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-5.png)

<span data-ttu-id="a6ddf-168">재생 단추를 눌러 게임 모드로 전환한 다음, 시선이 RoverAssembly 개체에 도달할 때까지 마우스 오른쪽 단추를 누른 상태로 마우스를 아래로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-168">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse down until the gaze hit's the RoverAssembly object:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-6.png)

<span data-ttu-id="a6ddf-170">마우스 왼쪽 단추를 클릭하여 Tap To Place(탭하여 위치 지정) 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-170">Click the left mouse button to start the tap-to-place process:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-7.png)

<span data-ttu-id="a6ddf-172">마우스 오른쪽 단추를 누른 상태에서 마우스를 왼쪽이나 오른쪽으로 움직여서 응시 방향을 회전하고 배치에 만족하면 마우스 왼쪽 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-172">Press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, when you are happy with the placement, click the left mouse button:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-8.png)

<span data-ttu-id="a6ddf-174">게임 모드에서 기능 테스트를 마쳤으면 큐브 개체를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택하여 장면에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-174">Once you are done testing the feature in the Game mode, right-click on the Cube object and select **Delete** to remove it from the scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a><span data-ttu-id="a6ddf-176">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-176">Congratulations</span></span>

<span data-ttu-id="a6ddf-177">이 자습서에서는 MRTK의 Directional Indicator(방향 표시) Solver를 사용하여 UI 요소가 직관적으로 사용자를 개체로 안내하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-177">In this tutorial, you learned how to use the MRTK's Directional Indicator Solver to have a UI element intuitively direct the user to objects.</span></span> <span data-ttu-id="a6ddf-178">Tap To Place(탭하여 위치 지정) Solver를 사용하여 개체의 위치를 쉽게 조정하는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-178">You also learned how to use the Tap To Place Solver to reposition objects easily.</span></span>

<span data-ttu-id="a6ddf-179">MRTK에 포함된 이러한 Solver와 다른 Solver에 대해 자세히 알아보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a6ddf-179">To learn more about these and other solvers included with the MRTK,  you can refer to the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="a6ddf-180">다음 자습서: 6. 사용자 인터페이스 만들기</span><span class="sxs-lookup"><span data-stu-id="a6ddf-180">Next Tutorial: 6. Creating user interfaces</span></span>](mr-learning-base-06.md)
