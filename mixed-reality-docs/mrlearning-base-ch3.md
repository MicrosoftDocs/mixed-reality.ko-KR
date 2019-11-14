---
title: 자습서-4를 시작 합니다. 동적 콘텐츠 배치 및 solvers 사용
description: 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: ade7a839e03a306332bf18f1db49805f59c71429
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064260"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="f9368-105">4. 동적 콘텐츠 배치 및 solvers 사용</span><span class="sxs-lookup"><span data-stu-id="f9368-105">4. Placing dynamic content and using solvers</span></span>

<span data-ttu-id="f9368-106">Holograms은 사용자가 직관적이 고 원활 하 게 상호 작용 하는 방식으로 실제 환경에 배치 되는 경우 HoloLens 2를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="f9368-107">이 자습서에서는 MRTK의 사용 가능한 배치 도구 (solvers)를 사용 하 여 동적으로 holograms을 배치 하 여 복잡 한 공간 배치 시나리오를 해결 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools (known as solvers) to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="f9368-108">MRTK에서 solvers는 UI 요소에서 사용자, 사용자 또는 장면의 기타 게임 개체를 팔 로우 하는 데 사용 되는 스크립트 및 동작의 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-108">In the MRTK, solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="f9368-109">특정 위치로 빠르게 스냅하여 애플리케이션을 보다 직관적인 만드는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="f9368-110">목표</span><span class="sxs-lookup"><span data-stu-id="f9368-110">Objectives</span></span>

* <span data-ttu-id="f9368-111">MRTK 해결기 소개</span><span class="sxs-lookup"><span data-stu-id="f9368-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="f9368-112">해결기를 사용하여 단추 컬렉션이 사용자를 따르도록 하기</span><span class="sxs-lookup"><span data-stu-id="f9368-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="f9368-113">해결기를 사용하여 게임 개체가 사용자의 추적된 손을 따르도록 하기</span><span class="sxs-lookup"><span data-stu-id="f9368-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="f9368-114">지침</span><span class="sxs-lookup"><span data-stu-id="f9368-114">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="f9368-115">MRTK에서 해결기의 위치</span><span class="sxs-lookup"><span data-stu-id="f9368-115">Location of solvers in the MRTK</span></span>

 <span data-ttu-id="f9368-116">프로젝트에서 사용 가능한 solvers를 찾으려면 MRTK SDK 폴더 (MixedRealityToolkit 폴더)를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-116">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder).</span></span> <span data-ttu-id="f9368-117">유틸리티 폴더 아래 이미지에 표시 된 것 처럼 solvers 폴더가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-117">Under the utilities folder, you will see the solvers folder, as shown in the image below.</span></span>

![해결기](images/lesson3_chapter1_step1im.PNG)

>[!NOTE]
><span data-ttu-id="f9368-119">이 단원에서는 궤도 나 RadialView의 구현을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-119">In this lesson, we will only review the implementation of the Orbital solver and the RadialView solver.</span></span> <span data-ttu-id="f9368-120">MRTK에서 사용할 수 있는 solvers의 전체 범위에 대해 자세히 알아보려면 다음을 방문 하세요. [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)</span><span class="sxs-lookup"><span data-stu-id="f9368-120">To learn more about the full range of solvers available in the MRTK, visit: [https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="f9368-121">해결기를 사용하여 사용자 따르기</span><span class="sxs-lookup"><span data-stu-id="f9368-121">Use a Solver to Follow the User</span></span>

<span data-ttu-id="f9368-122">이 장의 목표는 사용자의 응시 방향을 따라가는 이전에 만든 단추 컬렉션을 개선 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-122">The goal of this chapter is to enhance the button collection that was previously created so that it follows the user’s gaze direction.</span></span> <span data-ttu-id="f9368-123">이전 버전의 MRTK 및 HoloToolkit에서는이를 tagalong 기능 이라고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-123">In the previous version of the MRTK and HoloToolkit, this was referred to as a tagalong functionality.</span></span>

1. <span data-ttu-id="f9368-124">이전 단원의 Button Collection 부모 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-124">Select the Button Collection parent object from the previous lesson.</span></span>

    ![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="f9368-126">검사기 패널에서 구성 요소 추가 단추를 클릭 하 고 궤도를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-126">In the Inspector panel, click the Add Component button and search for orbital.</span></span> <span data-ttu-id="f9368-127">궤도 구성 요소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-127">The Orbital component should appear.</span></span> <span data-ttu-id="f9368-128">이를 선택 하 여 궤도 구성 요소를 단추 컬렉션 게임 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-128">Select it to add the Orbital component to the Button Collection game object.</span></span>

    ![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

    >[!NOTE]
    ><span data-ttu-id="f9368-130">궤도 구성 요소를 추가 하면 시스템에서 필수 구성 요소인 SolverHandler 구성 요소도 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-130">When you add the Orbital component you will notice that the system also adds the SolverHandler component, which is a required component.</span></span>

3. <span data-ttu-id="f9368-131">사용자를 따르도록 단추 컬렉션을 구성 하려면 다음 조정을 구현 해야 합니다 (아래 이미지 참조).</span><span class="sxs-lookup"><span data-stu-id="f9368-131">In order to configure the Button Collection to follow the user, we need to implement the following adjustments (refer to the image below):</span></span>
    * <span data-ttu-id="f9368-132">궤도 스크립트에서 방향 유형 드롭다운 목록을 요 Only로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-132">In the Orbital script, set the Orientation Type drop-down list to Yaw Only.</span></span> <span data-ttu-id="f9368-133">이렇게 하면 사용자를 따를 때 개체의 축 하나만 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-133">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
    * <span data-ttu-id="f9368-134">모든 축에서 Local Offset을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-134">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="f9368-135">전역 오프셋을 x = 0, y =-0.1 및 z = 0.6로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-135">Set the World Offset to x = 0, y = -0.1, and z = 0.6.</span></span> <span data-ttu-id="f9368-136">이렇게 하면 개체의 이동이 잠기므로 사용자가 높이를 변경 하는 경우 개체는 실제 환경에서 고정 높이로 유지 되 고 사용자가 환경에 대해 이동할 때 계속 사용자를 따르도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-136">This locks movement of the object so that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="f9368-137">다양한 범위의 동작을 달성하기 위해 이러한 값을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-137">These values may be adjusted to achieve a wide range of behaviors.</span></span>
    * <span data-ttu-id="f9368-138">사용자가 자신의 머리를 충분히 멀리 전환 하 고 나 서 단추를 클릭 한 후에도 사용자의 보기를 따라 이동 하는 동작을 위해 전 세계 오프셋에 각도 스테핑 사용 확인란을 선택할 수 있습니다 (참고: 아래 이미지에 나와 있는 것 처럼 일부 화면에서는이 제목이 잘릴 수 있음). 예를 들어 개체가 90도 마다 사용자를 따르도록 하려면 단계 수를 4로 설정 합니다 (아래 예제에서는 녹색 화살표로 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="f9368-138">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the Use Angle Stepping For World Offset checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example below).</span></span>

    ![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="f9368-140">추적 된 손을 따르도록 개체 활성화</span><span class="sxs-lookup"><span data-stu-id="f9368-140">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="f9368-141">이 섹션에서는 RadialView 해를 사용 하 여 사용자의 추적 된 손을 따르도록 이전에 만든 Cube game 개체를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-141">In this section, we will configure the Cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="f9368-142">BaseScene 계층 구조에서 큐브 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-142">Select the Cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="f9368-143">검사기 패널에서 구성 요소 추가를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-143">Click Add Component in the Inspector panel.</span></span> <span data-ttu-id="f9368-144">검색 상자에 RadialView를 입력 하 고 RadialView 구성 요소를 선택 하 여 큐브에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-144">Type in RadialView in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="f9368-145">SolverHandler 구성 요소도 큐브에 자동으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-145">The SolverHandler component will also be automatically added to the cube.</span></span>

    ![mrlearning-base-ch3-3-step3](images/mrlearning-base-ch3-3-step1.png)

2. <span data-ttu-id="f9368-147">헤드 대신 RadialView를 수행 하도록 변경 하려면 추적 대상 유형 옵션 옆에 있는 드롭다운 메뉴를 선택 하 고 메뉴에서 핸드 조인트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-147">To change the RadialView to follow a hand instead of the head, select the dropdown menu next to the Tracked Target Type option and select Hand Joint from the menu.</span></span>

    ![mrlearning-base-ch3-3-step2](images/mrlearning-base-ch3-3-step2a.png)

    <span data-ttu-id="f9368-149">이제 두 가지 새 옵션인 추적 된 수동 유형 및 추적 된 손을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-149">You will now see two new options, Tracked Handness Type and Tracked Hand Joint.</span></span> <span data-ttu-id="f9368-150">이 예에서는 아래 이미지에 표시 된 것 처럼 RadialView가 왼쪽의 손목을 따르도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-150">For this example, you will have the RadialView follow the wrist of the left hand as shown in the image below.</span></span>

    ![mrlearning-base-ch3-3-step2b](images/mrlearning-base-ch3-3-step2b.png)

3. <span data-ttu-id="f9368-152">방사형 보기의 최대 및 최소 거리를 0으로 설정 하 여 큐브에이와 사용자의 손목 사이에 거리가 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-152">Set the maximum and minimum distances of the Radial View to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="f9368-153">일단 설정하면 큐브는 손목에 완벽하게 맞춰집니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-153">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="f9368-154">참조 방향을 개체 지향으로 설정 하 여 개체를 사용자의 손목로 회전할 수 있도록 하려는 경우와 같이 큐브 지향 방법의 동작을 조정 하도록 참조 방향 필드를 조정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-154">You might also adjust the Reference Direction field to adjust the behavior of how the cube is oriented, such as if you want to allow the object to rotate with the user's wrist by setting the Reference Direction to Object Oriented.</span></span>

    ![mrlearning-base-ch3-3-step3](images/mrlearning-base-ch3-3-step3.png)

## <a name="congratulations"></a><span data-ttu-id="f9368-156">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-156">Congratulations</span></span>

<span data-ttu-id="f9368-157">이 자습서에서는 MRTK의 solvers를 사용 하 여 UI가 사용자를 직관적으로 따르도록 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-157">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="f9368-158">또한 해결기를 게임 개체(예: 큐브)에 연결하여 사용자의 추적된 손을 따르도록 하는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="f9368-158">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="f9368-159">이러한 해결기 및 MRTK에 포함된 다른 해결기에 대한 자세한 내용은 [MRTK 해결기 설명서 페이지](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f9368-159">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="f9368-160">다음 단원: 5.3D 개체와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="f9368-160">Next Lesson: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
