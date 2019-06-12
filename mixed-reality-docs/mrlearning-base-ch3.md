---
title: MR 학습 기본 모듈 - 동적 콘텐츠 배치 및 해결기
description: 혼합 현실 애플리케이션에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 6f05b2cecd388b1b2f13e7e5228bc90091eee3bd
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270407"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a><span data-ttu-id="5a0cf-104">MR 학습 기본 모듈 - 동적 콘텐츠 배치 및 해결기</span><span class="sxs-lookup"><span data-stu-id="5a0cf-104">MR Learning Base Module - Dynamic Content Placement and Solvers</span></span>

<span data-ttu-id="5a0cf-105">HoloLens 2에서 홀로그램은 사용자를 직관적으로 따르며, 원활하고 세련된 상호 작용을 지원하는 방식으로 실제 환경에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-105">Holograms come to life in the HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="5a0cf-106">3단원에서는 “해결기”라고 하는 MRTK의 사용 가능한 배치 도구를 사용하여 홀로그램을 동적으로 배치하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-106">In Lesson 3, we will explore ways to dynamically place holograms using the MRTK’s available placement tools, known as "solvers."</span></span> <span data-ttu-id="5a0cf-107">복잡한 공간 배치 알고리즘을 해결하는 방식 때문에 "해결기"로 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-107">They are known as "solvers" for the way they solve complex spatial placement algorithms.</span></span> <span data-ttu-id="5a0cf-108">MRTK에서 해결기는 UI 요소가 장면에서 사용자 또는 다른 게임 개체를 따르도록 하는 데 사용할 수 있는 스크립트 및 동작 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-108">In the MRTK, solvers are a system of scripts and behaviors that we use to be able to allow UI elements to follow you, the user or other game objects in the scene.</span></span> <span data-ttu-id="5a0cf-109">특정 위치로 빠르게 스냅하여 애플리케이션을 보다 직관적인 만드는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="5a0cf-110">목표</span><span class="sxs-lookup"><span data-stu-id="5a0cf-110">Objectives</span></span>

* <span data-ttu-id="5a0cf-111">MRTK 해결기 소개</span><span class="sxs-lookup"><span data-stu-id="5a0cf-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="5a0cf-112">해결기를 사용하여 단추 컬렉션이 사용자를 따르도록 하기</span><span class="sxs-lookup"><span data-stu-id="5a0cf-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="5a0cf-113">해결기를 사용하여 게임 개체가 사용자의 추적된 손을 따르도록 하기</span><span class="sxs-lookup"><span data-stu-id="5a0cf-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="5a0cf-114">지침</span><span class="sxs-lookup"><span data-stu-id="5a0cf-114">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="5a0cf-115">MRTK에서 해결기의 위치</span><span class="sxs-lookup"><span data-stu-id="5a0cf-115">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="5a0cf-116">프로젝트에서 사용 가능한 해결기를 찾으려면 MRTK SDK 폴더(MixedRealityToolkit.SDK 폴더)를 살펴봅니다. 그러면 아래 이미지와 같이 Utilites 폴더 아래에 Solvers 폴더가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-116">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder), then under the utilities folder you will see the solvers folder, as shown in the image below.</span></span>

![해결기](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="5a0cf-118">참고: 이 단원에서는 "Orbital" 해결기 및 "RadialView" 해결기만 구현해봅니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-118">Note: In this lesson we will only go over implementation of the "Orbital" solver and the "RadialView" solver.</span></span> <span data-ttu-id="5a0cf-119">MRTK에서 사용할 수 있는 전체 해결기 범위에 대한 자세한 내용은 https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-119">To learn more about the full range of solvers available in the MRTK, please visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="5a0cf-120">해결기를 사용하여 사용자 따르기</span><span class="sxs-lookup"><span data-stu-id="5a0cf-120">Use a Solver to Follow the User</span></span>
<span data-ttu-id="5a0cf-121">이 장의 목표는 이전에 만든 단추 컬렉션이 사용자의 응시 방향을 따르도록 개선하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-121">The goal of this chapter is to enhance the button collection we previously created such that it follows the user’s gaze direction.</span></span> <span data-ttu-id="5a0cf-122">MRTK 및 HoloToolkit 이전 버전에서는 이 기능을 "taglong"이라고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-122">In previous version of the MRTK and HoloToolkit, this was referred to as a "taglong" functionality.</span></span>

1. <span data-ttu-id="5a0cf-123">이전 단원의 Button Collection 부모 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-123">Select the Button Collection parent object from the previous lesson.</span></span>

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="5a0cf-125">inspector 패널에서 "add component" 단추를 클릭하고 "orbital"을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-125">In the inspector panel, click the "add component" button and search for "orbital."</span></span> <span data-ttu-id="5a0cf-126">orbital 구성 요소가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-126">The orbital component should appear.</span></span> <span data-ttu-id="5a0cf-127">이를 선택하여 Button Collection 게임 개체에 orbital 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-127">Select it to add the orbital component to the Button Collection game object.</span></span>

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="5a0cf-129">참고: 이 구성 요소를 추가하면 inspector 탭에서 필수 구성 요소인 solver handler 스크립트와 orbital 스크립트가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-129">Note: When you add the component you will notice that the system adds the orbital script and the solver handler script in the inspector tab, which is a required component.</span></span> 

3. <span data-ttu-id="5a0cf-130">단추 컬렉션이 사용자를 따르도록 구성하려면 다음과 같이 조정해야 합니다(아래 이미지 참조).</span><span class="sxs-lookup"><span data-stu-id="5a0cf-130">In order to configure the button collection to follow the user, we need to implement the following adjustments (please also refer to the image below):</span></span>
- <span data-ttu-id="5a0cf-131">Orbital 스크립트에서 "orientation type" 드롭다운 목록을 "Yaw Only"로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-131">In the Orbital script, set the "orientation type" drop-down list to "Yaw Only."</span></span> <span data-ttu-id="5a0cf-132">이렇게 하면 사용자를 따를 때 개체의 축 하나만 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-132">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="5a0cf-133">모든 축에서 Local Offset을 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-133">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="5a0cf-134">World Offset을 x = 0, y = -0.1 및 z = 0.6으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-134">Set the World Offset to x = 0, y = -0.1 and z = 0.6.</span></span> <span data-ttu-id="5a0cf-135">이렇게 하면 개체 이동이 잠기므로, 사용자가 작업 환경에서 이동할 때 사용자를 따를 수 있지만, 사용자가 높이를 변경해도 실제 환경에서 개체는 고정된 높이를 유지하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-135">This locks movement of the object such that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="5a0cf-136">다양한 범위의 동작을 달성하기 위해 이러한 값을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-136">These values may be adjusted to achieve a wide range of behaviors.</span></span>
- <span data-ttu-id="5a0cf-137">사용자가 머리를 충분히 멀리 돌린 후에만 단추가 사용자의 관점을 따르게 되는 따르기 동작에서는 "Use Angle Stepping for world offset" 확인란을 선택할 수 있습니다(참고: 이 제목은 아래 이미지와 같이 일부 화면에서는 잘릴 수 있습니다.) 예를 들어, 개체가 사용자를 90도 간격으로만 따르도록 하려면 단계 수를 4로 설정합니다(왼쪽 예제에서 녹색 화살표로 표시됨).</span><span class="sxs-lookup"><span data-stu-id="5a0cf-137">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the "Use Angle Stepping for world offset" checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example to the left).</span></span> 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="5a0cf-139">개체가 추적된 손을 따르도록 설정</span><span class="sxs-lookup"><span data-stu-id="5a0cf-139">Enabling Objects to Follow Tracked Hands</span></span>

<span data-ttu-id="5a0cf-140">이 섹션에서는 이전에 만든 큐브 게임 개체가 RadialView 해결기를 사용하여 사용자의 추적된 손을 따르도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-140">In this section, we will configure the cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="5a0cf-141">BaseScene 계층 구조에서 큐브 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-141">Select the cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="5a0cf-142">inspector 패널에서 "add component"를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-142">Click "add component" in the inspector panel.</span></span> 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="5a0cf-144">검색 상자에 "RadialView"를 입력하고 RadialView 구성 요소를 선택하여 큐브에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-144">Type in "RadialView" in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="5a0cf-145">해결기 처리기 구성 요소도 큐브에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-145">The solver handler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="5a0cf-146">머리는 따르지만 왼손은 따르지 않도록 방사형 뷰를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-146">Change the radial view to not follow the head but follow the left hand.</span></span> <span data-ttu-id="5a0cf-147">"tracked object to reference" 옵션 옆의 드롭다운 메뉴를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-147">Select the dropdown menu next to the "tracked object to reference" option.</span></span> <span data-ttu-id="5a0cf-148">그런 다음, 메뉴에서 "hand joint left"를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-148">Then select "hand joint left" from the menu.</span></span>

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="5a0cf-150">손 관절을 선택하고 나면, 큐브가 따르도록 하려는 손 부분을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-150">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="5a0cf-151">이 예제에서는 손목을 사용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-151">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="5a0cf-152">"tracked hand joint" 옵션 옆의 드롭다운 메뉴를 선택하고 wrist를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-152">Next to the option "tracked hand joint" select the dropdown menu and select wrist.</span></span> 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="5a0cf-154">큐브와 사용자의 손목 사이에 거리가 없도록 최대 및 최소 거리를 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-154">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="5a0cf-155">일단 설정하면 큐브는 손목에 완벽하게 맞춰집니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-155">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="5a0cf-156">또한 "Reference Direction" 필드를 조정하여 큐브 방향을 조정하는 동작을 조정할 수도 있습니다(예를 들어, 사용자의 손목에 따라 개체가 회전하도록 하려면 참조 방향을 "Orient with Tracked Object"로 설정).</span><span class="sxs-lookup"><span data-stu-id="5a0cf-156">You may also adjust the "Reference Direction" field to adjust the behavior of how the cube is oriented (e.g., if you would like to allow the object to rotate with the user's wrist, set the reference direction to "Orient with Tracked Object")</span></span>

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a><span data-ttu-id="5a0cf-158">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-158">Congratulations</span></span>
<span data-ttu-id="5a0cf-159">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-159">Congratulations!</span></span> <span data-ttu-id="5a0cf-160">이 단원에서는 MRTK의 해결기를 사용하여 UI가 사용자를 직관적으로 따르도록 하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-160">In this lesson, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="5a0cf-161">또한 해결기를 게임 개체(예: 큐브)에 연결하여 사용자의 추적된 손을 따르도록 하는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-161">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="5a0cf-162">이러한 해결기 및 MRTK에 포함된 다른 해결기에 대한 자세한 내용은 [MRTK 해결기 설명서 페이지](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5a0cf-162">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="5a0cf-163">다음 단원: 3D 개체 상호 작용</span><span class="sxs-lookup"><span data-stu-id="5a0cf-163">Next Lesson: 3D Object Interaction</span></span>](mrlearning-base-ch4.md)

