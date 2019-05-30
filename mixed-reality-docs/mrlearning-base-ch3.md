---
title: 동적 콘텐츠 배치 하 고 적절 하 게 MR 학습 자료 모듈
description: 혼합된 현실 응용 프로그램에서 Azure Face recognition 얼굴 인식을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: unity, 자습서, hololens, 혼합된 현실
ms.openlocfilehash: 6f05b2cecd388b1b2f13e7e5228bc90091eee3bd
ms.sourcegitcommit: aba33a8ad1416f7598048ac35ae9ab1734bd5c37
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66270407"
---
# <a name="mr-learning-base-module---dynamic-content-placement-and-solvers"></a><span data-ttu-id="8ccbc-104">동적 콘텐츠 배치 하 고 적절 하 게 MR 학습 자료 모듈</span><span class="sxs-lookup"><span data-stu-id="8ccbc-104">MR Learning Base Module - Dynamic Content Placement and Solvers</span></span>

<span data-ttu-id="8ccbc-105">홀로그램은 직관적으로 사용자를 따라 하며 원활 하 고 세련 된 상호 작용 하는 방식으로 실제 환경에 배치 됩니다 때 HoloLens 2에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-105">Holograms come to life in the HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="8ccbc-106">3 단원에서는 살펴봅니다 "해결사." 라고 MRTK의 가능한 배치 도구를 사용 하 여 홀로그램을 동적으로 배치 하는 방법을</span><span class="sxs-lookup"><span data-stu-id="8ccbc-106">In Lesson 3, we will explore ways to dynamically place holograms using the MRTK’s available placement tools, known as "solvers."</span></span> <span data-ttu-id="8ccbc-107">복잡 한 공간 배치 알고리즘을 해결 하기 위해 방식에 대 한 "적절 하 게"으로 알려져 있습니다 이러한.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-107">They are known as "solvers" for the way they solve complex spatial placement algorithms.</span></span> <span data-ttu-id="8ccbc-108">MRTK를 적절 하 게에는 스크립트 및 동작을 따르도록, 사용자 또는 다른 게임 개체는 장면에서 UI 요소를 허용 하려면 사용 하는 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-108">In the MRTK, solvers are a system of scripts and behaviors that we use to be able to allow UI elements to follow you, the user or other game objects in the scene.</span></span> <span data-ttu-id="8ccbc-109">데도 사용할 수 있습니다 특정 위치로 신속 하 게 맞춤에 응용 프로그램을 보다 직관적인 만드는 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span> 

## <a name="objectives"></a><span data-ttu-id="8ccbc-110">목표</span><span class="sxs-lookup"><span data-stu-id="8ccbc-110">Objectives</span></span>

* <span data-ttu-id="8ccbc-111">MRTK의 적절 하 게 소개</span><span class="sxs-lookup"><span data-stu-id="8ccbc-111">Introduce the MRTK's solvers</span></span>
* <span data-ttu-id="8ccbc-112">단추의 컬렉션을 사용 하 여 적절 하 게 사용자를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-112">Use solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="8ccbc-113">게임 개체를 사용 하 여 적절 하 게 사용자의 추적된 실습을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-113">Use solvers to have a game object follow the user's tracked hands</span></span>

## <a name="instructions"></a><span data-ttu-id="8ccbc-114">지침</span><span class="sxs-lookup"><span data-stu-id="8ccbc-114">Instructions</span></span>

### <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="8ccbc-115">MRTK에 적절 하 게의 위치</span><span class="sxs-lookup"><span data-stu-id="8ccbc-115">Location of solvers in the MRTK</span></span>
 <span data-ttu-id="8ccbc-116">프로젝트에서 사용할 수 해결사, utilities 폴더 아래의 다음 MRTK SDK 폴더 (MixedRealityToolkit.SDK 폴더)에 표시를 표시 됩니다 적절 하 게 폴더 아래 이미지에 표시 된 대로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-116">To find the available solvers in your project, look in the MRTK SDK folder (MixedRealityToolkit.SDK folder), then under the utilities folder you will see the solvers folder, as shown in the image below.</span></span>

![해 찾기](images/lesson3_chapter1_step1im.PNG)

><span data-ttu-id="8ccbc-118">참고: 이 단원의 살펴보겠습니다 "궤도" solver "RadialView" solver을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-118">Note: In this lesson we will only go over implementation of the "Orbital" solver and the "RadialView" solver.</span></span> <span data-ttu-id="8ccbc-119">적절 하 게 된 MRTK에서 사용할 수 있는 전체 범위에 대 한 자세한 내용은 다음을 참조 하세요. https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span><span class="sxs-lookup"><span data-stu-id="8ccbc-119">To learn more about the full range of solvers available in the MRTK, please visit: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html</span></span>

### <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="8ccbc-120">사용자를 따라 해를 찾기 사용</span><span class="sxs-lookup"><span data-stu-id="8ccbc-120">Use a Solver to Follow the User</span></span>
<span data-ttu-id="8ccbc-121">이 장의 목표는 사용자의 게이즈 방향을 따릅니다 이전에 만든 단추 컬렉션을 향상 시키기 위해입니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-121">The goal of this chapter is to enhance the button collection we previously created such that it follows the user’s gaze direction.</span></span> <span data-ttu-id="8ccbc-122">HoloToolkit 고 MRTK의 이전 버전에서는이 라고 했습니다 "taglong" 기능을 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-122">In previous version of the MRTK and HoloToolkit, this was referred to as a "taglong" functionality.</span></span>

1. <span data-ttu-id="8ccbc-123">이전 단원에서 단추 컬렉션의 부모 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-123">Select the Button Collection parent object from the previous lesson.</span></span>

![Lesson3 Chapter2 Step1im](images/Lesson3_chapter2_step1im.PNG)

2. <span data-ttu-id="8ccbc-125">검사기 창에서 검색 "궤도." 고 "구성 요소 추가" 단추를 클릭</span><span class="sxs-lookup"><span data-stu-id="8ccbc-125">In the inspector panel, click the "add component" button and search for "orbital."</span></span> <span data-ttu-id="8ccbc-126">궤도 구성 요소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-126">The orbital component should appear.</span></span> <span data-ttu-id="8ccbc-127">단추 컬렉션 게임 개체 궤도 구성 요소를 추가 하려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-127">Select it to add the orbital component to the Button Collection game object.</span></span>

![Lesson3 Chapter2 Step2im](images/Lesson3_Chapter2_step2im.PNG)

><span data-ttu-id="8ccbc-129">참고: 구성 요소를 추가 하면 시스템 궤도 스크립트 및 solver 처리기 스크립트는 필수 구성 요소 검사기 탭에서 추가 함을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-129">Note: When you add the component you will notice that the system adds the orbital script and the solver handler script in the inspector tab, which is a required component.</span></span> 

3. <span data-ttu-id="8ccbc-130">사용자를 따라 단추 컬렉션을 구성 하려면 다음과 같이 조정 구현 해야 (자신을 아래 이미지).</span><span class="sxs-lookup"><span data-stu-id="8ccbc-130">In order to configure the button collection to follow the user, we need to implement the following adjustments (please also refer to the image below):</span></span>
- <span data-ttu-id="8ccbc-131">궤도 스크립트에서 "요에만 해당 합니다." "방향 유형" 드롭 다운 목록 설정</span><span class="sxs-lookup"><span data-stu-id="8ccbc-131">In the Orbital script, set the "orientation type" drop-down list to "Yaw Only."</span></span> <span data-ttu-id="8ccbc-132">이렇게 하면 사용자 같이 개체의 해당 하나의 축 회전 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-132">This makes it so that only one axis of the object rotates as it follows the user.</span></span>
- <span data-ttu-id="8ccbc-133">모든 축에서의 로컬 오프셋을 0으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-133">Set the local offset to 0 on all axes.</span></span> <span data-ttu-id="8ccbc-134">X로 세계 오프셋 = 0, y-0.1 및 z = 0.6 =.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-134">Set the World Offset to x = 0, y = -0.1 and z = 0.6.</span></span> <span data-ttu-id="8ccbc-135">사용자 환경에 대 한 이동함에 따라 사용자를 수행 하도록 허용 하면서 개체 실제 환경에서 높이가 고정된에 남아 사용자 높이 변경 하는 경우는 개체의 이동이 잠깁니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-135">This locks movement of the object such that when the user changes height, the object will remain at a fixed height in the physical environment, while still allowing it to follow the user as the user moves about the environment.</span></span> <span data-ttu-id="8ccbc-136">다양 한 범위의 동작을 달성 하기 위해 이러한 값을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-136">These values may be adjusted to achieve a wide range of behaviors.</span></span>
- <span data-ttu-id="8ccbc-137">가능해 집니다 단추에만 수행 사용자 관점에서 사용자가 자신의 헤드를 충분히 멀리 설정 후에 다음 동작에 대해 "world 오프셋에 대 한 단계별 실행 사용 하 여 각도" 확인란을 선택할 수 있습니다 (참고: 이 제목은 잘릴 수 있습니다 일부 화면에서 아래 이미지에서는.) 예를 들어 사용자 90도 간격에 따라 개체를 집합 단계의 수 (왼쪽 예제에서 녹색 화살표로 표시 됨) 4와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-137">For a follow behavior whereby the buttons only follow the user’s view after the user turns his or her head sufficiently far, you could select the "Use Angle Stepping for world offset" checkbox (Note: This title may be truncated on some screens, as it is in the image below.) For example, to have the object follow the user only every 90 degrees, set the number of steps equal to 4 (marked by a green arrow in the example to the left).</span></span> 

![Lesson3 Chapter2 Step3im](images/Lesson3_chapter2_step3im.PNG)

### <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="8ccbc-139">추적 된 실습을 수행 하려면 개체를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="8ccbc-139">Enabling Objects to Follow Tracked Hands</span></span>

<span data-ttu-id="8ccbc-140">이 섹션에서는 RadialView 해결 기를 사용 하 여 사용자의 추적된 실습을 수행 하려면 이전에 만든 큐브 게임 개체를 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-140">In this section, we will configure the cube game object previously created to follow the user’s tracked hands using the RadialView solver.</span></span>

1. <span data-ttu-id="8ccbc-141">BaseScene 계층의 큐브 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-141">Select the cube object in the BaseScene hierarchy.</span></span> <span data-ttu-id="8ccbc-142">[관리자] 패널에서 "구성 요소 추가"를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-142">Click "add component" in the inspector panel.</span></span> 

![Lesson3 Chapter3 Step1im](images/Lesson3_Chapter3_step1im.PNG)

2. <span data-ttu-id="8ccbc-144">검색 상자에 "RadialView"에 입력 하 고 큐브에 추가할 RadialView 구성 요소를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-144">Type in "RadialView" in the search box and select the RadialView component to add it to the cube.</span></span> <span data-ttu-id="8ccbc-145">Solver 처리기 구성 요소도 자동으로 추가 됩니다 큐브에 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-145">The solver handler component will also be automatically added to the cube.</span></span>

3. <span data-ttu-id="8ccbc-146">헤드 따르지 있지만 왼쪽을 따라 방사형 뷰를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-146">Change the radial view to not follow the head but follow the left hand.</span></span> <span data-ttu-id="8ccbc-147">"개체 참조를 추적" 옵션 옆의 드롭다운 메뉴를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-147">Select the dropdown menu next to the "tracked object to reference" option.</span></span> <span data-ttu-id="8ccbc-148">그런 다음 메뉴에서 "공동 왼쪽 전달"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-148">Then select "hand joint left" from the menu.</span></span>

![Lesson3 Chapter3 Step3im](images/Lesson3_chapter3_step3im.PNG)

4. <span data-ttu-id="8ccbc-150">직접 연결을 선택 하면 손 모양 아이콘이 부분 원하는 수행 하려면 큐브를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-150">Once you select the hand joint, you can choose which part of the hand you want the cube to follow.</span></span> <span data-ttu-id="8ccbc-151">예를 들어 다음 손목 사용 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-151">For this example, we are going to use the wrist.</span></span> <span data-ttu-id="8ccbc-152">옵션 옆의 "추적된 직접 공동" 드롭다운 메뉴를 선택 하 고 손목을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-152">Next to the option "tracked hand joint" select the dropdown menu and select wrist.</span></span> 

![Lesson3 Chapter3 Step4im](images/Lesson3_chapter3_step4im.PNG)

5. <span data-ttu-id="8ccbc-154">큐브는 사용자의 손목 사이 거리 필요가 없도록 0으로 최대 및 최소 거리를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-154">Set the maximum and minimum distances to 0 so that the cube will not have any distance between it and the user’s wrist.</span></span> <span data-ttu-id="8ccbc-155">설정 되 면 큐브 완벽 하 게 맞춰집니다 손목 합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-155">Once set, the cube will be perfectly aligned with the wrist.</span></span> <span data-ttu-id="8ccbc-156">또한 어떻게 큐브의 경우 방향 (예를 들어 사용자의 손목을 사용 하 여 회전, "방향으로 추적 한 개체" 참조 방향을 설정 개체를 허용 하려는)의 동작을 조정 하려면 "참조 방향" 필드를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-156">You may also adjust the "Reference Direction" field to adjust the behavior of how the cube is oriented (e.g., if you would like to allow the object to rotate with the user's wrist, set the reference direction to "Orient with Tracked Object")</span></span>

![Lesson3 Chapter3 Step5im](images/Lesson3_chapter3_step5im.PNG)

### <a name="congratulations"></a><span data-ttu-id="8ccbc-158">축 하.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-158">Congratulations</span></span>
<span data-ttu-id="8ccbc-159">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-159">Congratulations!</span></span> <span data-ttu-id="8ccbc-160">이 단원에서는 MRTK의 적절 하 게 직관적으로 사용자에 따라 ui를 사용 하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-160">In this lesson, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="8ccbc-161">또한 사용자의 추적된 실습을 수행 하는 게임 개체 (예: 큐브)를 찾기가 연결 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-161">You also learned how to attach a solver to a game object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="8ccbc-162">이러한 및는 MRTK 포함 된 다른 해 찾기에 대 한 자세한 내용은 자유롭게 방문 하는 [MRTK 적절 하 게 설명서 페이지](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="8ccbc-162">To learn more about these and other solvers included with the MRTK, feel free to visit the [MRTK solvers documentation page](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html).</span></span>

[<span data-ttu-id="8ccbc-163">다음 단원: 3D 개체 상호 작용</span><span class="sxs-lookup"><span data-stu-id="8ccbc-163">Next Lesson: 3D Object Interaction</span></span>](mrlearning-base-ch4.md)

