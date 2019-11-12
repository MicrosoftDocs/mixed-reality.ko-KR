---
title: 자습서 시작-5. 3D 개체와 상호 작용
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 07bcce2ab9ab3bda035f7f2b39a90753cf45358d
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913775"
---
# <a name="5-interacting-with-3d-objects"></a><span data-ttu-id="f2e6a-104">5.3D 개체와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="f2e6a-104">5. Interacting with 3D objects</span></span>

<span data-ttu-id="f2e6a-105">이 자습서에서는 다음과 같은 기본 3D 콘텐츠 및 사용자 환경에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-105">In this tutorial, you will learn about basic 3D content and user experience, such as:</span></span>

* <span data-ttu-id="f2e6a-106">3D 개체를 컬렉션의 일부로 구성</span><span class="sxs-lookup"><span data-stu-id="f2e6a-106">Organizing 3D objects as part of a collection</span></span>
* <span data-ttu-id="f2e6a-107">기본 조작을 위한 경계 상자</span><span class="sxs-lookup"><span data-stu-id="f2e6a-107">Bounding boxes for basic manipulation</span></span>
* <span data-ttu-id="f2e6a-108">근거리 및 원거리 상호 작용</span><span class="sxs-lookup"><span data-stu-id="f2e6a-108">Near and far interaction</span></span>
* <span data-ttu-id="f2e6a-109">손으로 직접 추적 하는 터치 및 잡기 제스처</span><span class="sxs-lookup"><span data-stu-id="f2e6a-109">Touch and grab gestures with hand tracking</span></span>

## <a name="objectives"></a><span data-ttu-id="f2e6a-110">목표</span><span class="sxs-lookup"><span data-stu-id="f2e6a-110">Objectives</span></span>

* <span data-ttu-id="f2e6a-111">MRTK의 grid 개체 컬렉션을 사용 하 여 3D 콘텐츠를 구성 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-111">Learn how to organize 3D content with MRTK's grid object collection</span></span>
* <span data-ttu-id="f2e6a-112">경계 상자 구현</span><span class="sxs-lookup"><span data-stu-id="f2e6a-112">Implement bounding boxes</span></span>
* <span data-ttu-id="f2e6a-113">기본 조작을 위한 3D 개체 구성-이동, 회전 및 크기 조정</span><span class="sxs-lookup"><span data-stu-id="f2e6a-113">Configure 3D objects for basic manipulation--move, rotate, and scale</span></span>
* <span data-ttu-id="f2e6a-114">근거리 및 원거리 조작 살펴보기</span><span class="sxs-lookup"><span data-stu-id="f2e6a-114">Explore near and far interaction</span></span>
* <span data-ttu-id="f2e6a-115">잡기, 터치 등의 추가 수동 추적 제스처에 대해 알아보기</span><span class="sxs-lookup"><span data-stu-id="f2e6a-115">Learn about additional hand tracking gestures, such as grab and touch</span></span>

## <a name="instructions"></a><span data-ttu-id="f2e6a-116">지침</span><span class="sxs-lookup"><span data-stu-id="f2e6a-116">Instructions</span></span>

### <a name="organizing-3d-objects-in-a-collection"></a><span data-ttu-id="f2e6a-117">컬렉션에서 3D 개체 구성</span><span class="sxs-lookup"><span data-stu-id="f2e6a-117">Organizing 3D Objects in a Collection</span></span>

1. <span data-ttu-id="f2e6a-118">계층 구조를 마우스 오른쪽 단추로 클릭 하 고 비어 있음 만들기를 선택 하 여 빈 게임 개체를 만들고 3DObjectCollection로 이름을 바꾼 다음 x = 0, y = 0 및 z = 0에 배치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-118">Right-click on your hierarchy and select Create Empty to create an empty game object, rename it to 3DObjectCollection, and make sure it is positioned at x = 0, y = 0, and z = 0.</span></span>

    ![mrlearning-base-ch4-1-step1](images/mrlearning-base-ch4-1-step1.png)

2. <span data-ttu-id="f2e6a-120">Unity [패키지를 다운로드 하 고](https://github.com/Developer-OI/MixedRealityLearning/releases/download/1.2.1/BaseModuleAssets-1.2.1.unitypackage) , 동일한 지침을 사용 하 여 [1 단원](mrlearning-base-ch1.md)에 설명 된 사용자 지정 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-120">Download the Unity package [BaseModuleAssets version 1.2.1](https://github.com/Developer-OI/MixedRealityLearning/releases/download/1.2.1/BaseModuleAssets-1.2.1.unitypackage) and import it using the same instructions to import custom packages outlined in [Lesson1](mrlearning-base-ch1.md).</span></span> <span data-ttu-id="f2e6a-121">이 패키지는이 자습서 전체에서 사용 되는 3D 모델 및 기타 유용한 자산을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-121">This package includes 3D models and other useful assets that are used throughout this tutorial.</span></span>

3. <span data-ttu-id="f2e6a-122">프로젝트 패널에서 asset > BasemodulPrefabs Sets > 기본 모듈 Prefabs로 이동 하 고 "불완전"을 검색 하 여 이러한 중 일부를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-122">In the Project panel, navigate to Assets > BaseModuleAssets > Base Module Prefabs and search for "incomplete", we will use some of these prefabs.</span></span>

    ![mrlearning-base-ch4-1-step3](images/mrlearning-base-ch4-1-step3.png)

4. <span data-ttu-id="f2e6a-124">커피 컵을 1 단계의 3DObjectCollection game 개체로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-124">Drag the coffee cup into the 3DObjectCollection game object from Step 1.</span></span> <span data-ttu-id="f2e6a-125">이제 커피 컵이 컬렉션의 자식이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-125">The coffee cup is now a child of the collection.</span></span>

    ![mrlearning-base-ch4-1-step4](images/mrlearning-base-ch4-1-step4.png)

5. <span data-ttu-id="f2e6a-127">다음으로 이전 단계와 동일한 프로세스를 수행 하 여 더 많은 3D 개체를 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-127">Next, you'll add more 3D objects into our scene by following the same process as in the previous step.</span></span> <span data-ttu-id="f2e6a-128">다음은이 예제에서 추가할 개체의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-128">Below is a list of objects to add in this example.</span></span> <span data-ttu-id="f2e6a-129">개체를 추가 하면 여러 크기의 장면에 표시 되는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-129">As you add the objects, you might find they appear in your scene in various sizes.</span></span> <span data-ttu-id="f2e6a-130">검사기 패널의 변환 설정에서 각 3D 모델의 배율을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-130">Adjust the scale of each 3D model under Transform settings in the Inspector panel.</span></span> <span data-ttu-id="f2e6a-131">이 예제에서 권장되는 조정은 아래 개체를 사용하여 나열됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-131">Recommended adjustments for this example are listed with the objects below.</span></span>

    * <span data-ttu-id="f2e6a-132">Cheese_BaseModuleIncomplete.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-132">Cheese_BaseModuleIncomplete.</span></span> <span data-ttu-id="f2e6a-133">크기 조정: x = 0.05, y = 0.05, z = 0.05.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-133">Scale: x = 0.05, y = 0.05, z = 0.05.</span></span>
    * <span data-ttu-id="f2e6a-134">CoffeeCup_BaseModuleIncomplete.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-134">CoffeeCup_BaseModuleIncomplete.</span></span> <span data-ttu-id="f2e6a-135">크기 조정: x = 0.1, y = 0.1, z = 0.1.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-135">Scale: x = 0.1, y = 0.1, z = 0.1.</span></span>
    * <span data-ttu-id="f2e6a-136">EarthCore_BaseModuleIncomplete.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-136">EarthCore_BaseModuleIncomplete.</span></span> <span data-ttu-id="f2e6a-137">크기 조정: x = 50.0 y = 50.0, z = 50.0.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-137">Scale: x = 50.0 y = 50.0, z = 50.0.</span></span>
    * <span data-ttu-id="f2e6a-138">Model_Platonic_BaseModuleIncomplete.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-138">Model_Platonic_BaseModuleIncomplete.</span></span> <span data-ttu-id="f2e6a-139">크기 조정: x = 0.13, y = 0.13, z = 0.13.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-139">Scale: x = 0.13, y = 0.13, z = 0.13.</span></span>
    * <span data-ttu-id="f2e6a-140">Octa_BaseModuleIncomplete.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-140">Octa_BaseModuleIncomplete.</span></span> <span data-ttu-id="f2e6a-141">크기 조정: x = 0.13.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-141">Scale: x = 0.13.</span></span> <span data-ttu-id="f2e6a-142">y = 0.13, z =0.13으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-142">y = 0.13, z =0.13.</span></span>
    * <span data-ttu-id="f2e6a-143">TheModule_BaseModuleIncomplete.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-143">TheModule_BaseModuleIncomplete.</span></span> <span data-ttu-id="f2e6a-144">크기 조정: x = 0.03, y = 0.03, z = 0.03.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-144">Scale: x = 0.03, y = 0.03, z = 0.03.</span></span>

    ![mrlearning-base-ch4-1-step5](images/mrlearning-base-ch4-1-step5.png)

6. <span data-ttu-id="f2e6a-146">장면에 세 개의 큐브를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-146">Add three cubes into your scene.</span></span> <span data-ttu-id="f2e6a-147">3DObjectCollection 개체를 마우스 오른쪽 단추로 클릭 하 고 3D 개체를 선택한 다음 큐브를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-147">Right-click the 3DObjectCollection object, select 3D Object, then select Cube.</span></span> <span data-ttu-id="f2e6a-148">배율을 x = 0.14, y = 0.14 및 z = 0.14로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-148">Set the scale to x = 0.14, y = 0.14, and z = 0.14.</span></span> <span data-ttu-id="f2e6a-149">이 단계를 두 번 더 반복 하 여 총 세 개의 큐브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-149">Repeat this step two additional times to create a total of three cubes.</span></span> <span data-ttu-id="f2e6a-150">또는 큐브를 두 번 복제 하 여 총 3 개 큐브를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-150">Alternatively, you can duplicate the cube twice for a total of three cubes.</span></span> <span data-ttu-id="f2e6a-151">또한 자산>BaseModuleAssets>기본 모듈 프리팹에서 세 개의 준비된 큐브 프리팹을 선택하고, GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete 및 OrangeCube_BaseModuleIncomplete를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-151">You may also choose to use the three prepared cube prefabs from Assets>BaseModuleAssets>Base Module Prefabs and select GreenCube_BaseModuleIncomplete, BlueCube_BaseModuleIncomplete and OrangeCube_BaseModuleIncomplete.</span></span>

    ![mrlearning-base-ch4-1-step6](images/mrlearning-base-ch4-1-step6.png)

7. <span data-ttu-id="f2e6a-153">[2 단원](mrlearning-base-ch2.md)에 설명 된 절차를 통해 MRTK의 Grid 개체 컬렉션을 사용 하 여 표 형태를 구성 하는 개체의 컬렉션을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-153">Organize your collection of objects to form a grid, via the procedure described in [Lesson 2](mrlearning-base-ch2.md), using the MRTK’s Grid Object Collection.</span></span> <span data-ttu-id="f2e6a-154">3x3 모눈에서 개체를 구성 하는 예는 아래 이미지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-154">Refer to the image below, for an example of configuring the objects in a 3x3 grid.</span></span>

    ![mrlearning-base-ch4-1-step7](images/mrlearning-base-ch4-1-step7.png)

    >[!NOTE]
    ><span data-ttu-id="f2e6a-156">위의 이미지에 있는 개체와 같이 일부 개체는 외부에서 분리 된 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-156">You might notice that some of the objects are off-center, such as the objects in the image above.</span></span> <span data-ttu-id="f2e6a-157">이는 프리팹 또는 개체에 정렬되지 않은 자식 개체가 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-157">This is because prefabs or objects may have child objects that are not aligned.</span></span> <span data-ttu-id="f2e6a-158">자유롭게 개체 위치 또는 자식 개체 위치를 조정하여 잘 정렬된 그리드를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-158">Feel free to make any necessary adjustments to object positions or child object positions to achieve a well-aligned grid.</span></span>

### <a name="manipulating-3d-objects"></a><span data-ttu-id="f2e6a-159">3D 개체 조작</span><span class="sxs-lookup"><span data-stu-id="f2e6a-159">Manipulating 3D Objects</span></span>

1. <span data-ttu-id="f2e6a-160">큐브를 조작하는 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-160">Add the ability to manipulate a cube.</span></span> <span data-ttu-id="f2e6a-161">3D 개체를 조작 하는 기능을 추가 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-161">To add the ability to manipulate 3D objects, do the following:</span></span>
    * <span data-ttu-id="f2e6a-162">계층 구조에서 조작할 3D 개체 (즉, 큐브 중 하나)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-162">Select the 3D object you want to manipulate in your hierarchy (i.e. one of your cubes).</span></span>
    * <span data-ttu-id="f2e6a-163">구성 요소 추가를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-163">Click Add Component</span></span>
    * <span data-ttu-id="f2e6a-164">"조작" 검색</span><span class="sxs-lookup"><span data-stu-id="f2e6a-164">Search for "manipulation"</span></span>
    * <span data-ttu-id="f2e6a-165">조작 처리기 선택</span><span class="sxs-lookup"><span data-stu-id="f2e6a-165">Select Manipulation Handler</span></span>
    * <span data-ttu-id="f2e6a-166">3DObjectCollection 개체 아래의 모든 3D 개체에 대해 반복 하지만 3DObjectCollection 자체는 반복 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-166">Repeat for all 3D objects under the 3DObjectCollection object, but not the 3DObjectCollection itself.</span></span>
    * <span data-ttu-id="f2e6a-167">모든 3D 개체에 collider 또는 box collider (구성 요소 추가 > 상자 Collider)가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-167">Ensure that all 3D objects have a collider or box collider (Add Component>Box Collider).</span></span>

    ![Lesson4 Chapter2 Step1im](images/Lesson4_chapter2_step1im.PNG)

    >[!NOTE]
    ><span data-ttu-id="f2e6a-169">조작 처리기는 조작할 때 개체가 동작 하는 방법에 대 한 설정을 조정할 수 있도록 하는 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-169">The manipulation handler is a component that lets you adjust settings for how objects behave when manipulated.</span></span> <span data-ttu-id="f2e6a-170">여기에는 특정 축의 회전, 크기 조정, 이동 및 제한 이동이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-170">This includes rotation, scaling, moving, and constraining movement on a specific axis.</span></span>

2. <span data-ttu-id="f2e6a-171">확장만 가능하도록 큐브 하나를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-171">Restrict one cube so that it can only be scaled.</span></span> <span data-ttu-id="f2e6a-172">3DObjectCollection 개체에서 큐브 하나를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-172">Select one cube in the 3DObjectCollection object.</span></span> <span data-ttu-id="f2e6a-173">검사기 패널에서 두 개의 왼손 조작 유형 옆에 있는 드롭다운 메뉴를 클릭 하 고 Scale을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-173">In the Inspector panel, next to Two Handed Manipulation Type, click the drop-down menu and select Scale.</span></span> <span data-ttu-id="f2e6a-174">이렇게 하면 사용자가 큐브의 크기만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-174">This makes it so that the user can only change the cube’s size.</span></span>

    ![Lesson4 Chapter2 Step2im](images/Lesson4_Chapter2_step2im.PNG)

3. <span data-ttu-id="f2e6a-176">서로 구별할 수 있도록 각 큐브의 색을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-176">Change the color of each cube so that we can differentiate between them.</span></span>
    * <span data-ttu-id="f2e6a-177">프로젝트 패널로 이동 하 고 MixedRealityToolkit가 표시 될 때까지 아래로 스크롤한 다음 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-177">Go to the Project panel and scroll down until you see MixedRealityToolkit.SDK, then select it.</span></span>
    * <span data-ttu-id="f2e6a-178">표준 자산 폴더를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-178">Select the Standard Assets folder.</span></span>
    * <span data-ttu-id="f2e6a-179">재질 폴더를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-179">Click the Materials folder.</span></span>
    * <span data-ttu-id="f2e6a-180">각 큐브에 다른 재료를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-180">Drag a different material onto each of your cubes.</span></span>

    >[!NOTE]
    ><span data-ttu-id="f2e6a-181">큐브에 대한 색을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-181">You can choose any color for your cubes.</span></span> <span data-ttu-id="f2e6a-182">이 예에서는 glowingcyan, glowingcyan 및 green이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-182">For this example, glowingcyan, glowingorange and green are used.</span></span> <span data-ttu-id="f2e6a-183">자유롭게 다른 색을 시도해 보세요.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-183">Feel free to experiment with different colors.</span></span> <span data-ttu-id="f2e6a-184">큐브에 색을 추가 하려면 변경할 큐브를 클릭 한 다음 큐브의 검사기 패널에서 재질을 메시 렌더러의 재질 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-184">To add the color to the cube, click the cube you want to change, then drag the material to the mesh renderer's material field in the cube's Inspector panel.</span></span>

    ![Lesson4 Chapter2 Step3im](images/Lesson4_Chapter2_step3im.PNG)

4. <span data-ttu-id="f2e6a-186">3DObjectCollection 개체에서 다른 큐브를 선택 하 고 이동 하 여 head에서 고정 거리 만큼 이동 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-186">Select another cube in the 3DObjectCollection object and make it so that its movement is constrained to a fixed distance from the head.</span></span> <span data-ttu-id="f2e6a-187">이렇게 하려면 이동 레이블의 제약 조건 오른쪽에 있는 드롭다운 메뉴를 클릭 하 고 Head에서 거리 수정을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-187">To do this, to the right of Constraint on Movement label, click the drop-down menu and select Fix Distance from the Head.</span></span> <span data-ttu-id="f2e6a-188">이는 큐브를 비전의 해당 필드 내에 포함 하도록 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-188">This adjusts the cube to be within their field of vision.</span></span>

    ![Lesson4 Chapter2 Step4im](images/Lesson4_chapter2_step4im.PNG)

    <span data-ttu-id="f2e6a-190">다음 몇 단계의 목표는 3D 개체를 가져오고 상호 작용 하 고 다른 조작 설정을 적용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-190">The goal of the following few steps is to enable grabbing and interacting with our 3D objects and applying different manipulation settings.</span></span>

5. <span data-ttu-id="f2e6a-191">치즈 개체를 선택한 다음, 검사기 패널에서 구성 요소 추가를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-191">Select the Cheese object, then click Add Component from the Inspector panel.</span></span>

6. <span data-ttu-id="f2e6a-192">근접 한 상호 작용 Grabbable 검색 상자에서 검색 하 고 스크립트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-192">Search in the search box for Near Interaction Grabbable and select the script.</span></span> <span data-ttu-id="f2e6a-193">이 구성 요소를 통해 사용자는 추적 된 손으로 개체를 연결 하 고 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-193">This component enables users to reach out and grab objects with tracked hands.</span></span> <span data-ttu-id="f2e6a-194">아래 이미지에서 녹색 원으로 표시 되는 경우에도 개체를 거리에서 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-194">Objects can also be manipulated from a distance, unless the Allow Far Manipulation checkbox is unchecked as denoted by a green circle in the image below.</span></span>

    ![Lesson4 Chapter2 Step6im](images/Lesson4_Chapter2_step6im.PNG)

7. <span data-ttu-id="f2e6a-196">해당 개체에 대해 5 단계와 6 단계를 반복 하 여 근거리 상호 작용 Grabbable을 Octa 개체, Platonic 개체, 지구 코어, 음력 모듈 및 커피 컵에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-196">Add Near Interaction Grabbable to the Octa object, Platonic object, Earth Core, Lunar Module, and Coffee Cup by repeating Steps 5 and 6 on those objects.</span></span>

8. <span data-ttu-id="f2e6a-197">Octa 개체에서 원거리 조작 기능을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-197">Remove the ability of far manipulation from the Octa object.</span></span> <span data-ttu-id="f2e6a-198">이렇게 하려면 계층에서 Octa를 선택 하 고 far 조작 허용 확인란의 선택을 취소 합니다 (녹색 원으로 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="f2e6a-198">To do this, select the Octa in the hierarchy and uncheck the Allow far Manipulation checkbox (marked by a green circle).</span></span> <span data-ttu-id="f2e6a-199">이렇게 하면 사용자가 추적 된 손을 사용 하 여 직접 octa와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-199">This makes it so users can only interact with the octa directly using tracked hands.</span></span>

    >[!NOTE]
    ><span data-ttu-id="f2e6a-200">조작 처리기 구성 요소 및 연결 된 설정에 대 한 전체 설명서는 [Mrtk 설명서](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-200">For the full documentation of the manipulation handler component and it's associated settings, refer to the [MRTK Documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html).</span></span>

9. <span data-ttu-id="f2e6a-201">근접 한 상호 작용 Grabbable 구성 요소가 지구 코어, 음력 모듈 및 커피 컵에 추가 되었는지 확인 합니다 (7 단계 참조).</span><span class="sxs-lookup"><span data-stu-id="f2e6a-201">Ensure that the Near Interaction Grabbable component has been added to the earth core, the lunar module and the coffee cup (see Step 7).</span></span>

10. <span data-ttu-id="f2e6a-202">음력 모듈의 경우 아래 이미지에 나와 있는 것 처럼 거의 상호 작용에 대 한 개체의 중심을 중심으로 회전 하도록 조작 처리기 설정을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-202">For the lunar module, change the Manipulation Handler settings so that it rotates around the object's center for both near and far interaction, as shown in the image below.</span></span>

    ![Lesson4 Chapter2 Step10im](images/Lesson4_chapter2_step10im.PNG)

11. <span data-ttu-id="f2e6a-204">지구 코어의 경우 릴리스 동작을 nothing으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-204">For the earth core, change the release behavior to nothing.</span></span> <span data-ttu-id="f2e6a-205">이렇게 하면 사용자의 이해를 통해 지구 코어가 릴리스되는 경우 계속 해 서 이동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-205">This makes it so that once the earth core is released from the user's grasp, it doesn’t continue to move.</span></span>

    ![Lesson4 Chapter2 Step11im](images/Lesson4_Chapter2_step11im.PNG)

    >[!NOTE]
    ><span data-ttu-id="f2e6a-207">이 설정은 throw 할 수 있는 공을 만드는 등의 시나리오에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-207">This setting is useful for scenarios, such as creating a ball that you can throw.</span></span> <span data-ttu-id="f2e6a-208">적절 한 속도 및 각도의 속도를 유지 하 여 해골을 릴리스한 후에는 릴리스되는 속도로 계속 이동 합니다. 물리적 공이 동작 하는 방식과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-208">Keeping the appropriate velocity and angular velocity to ensure that once the ball is released, it will continue to move at the velocity it was released at; similar to how a physical ball would behave.</span></span>

### <a name="adding-bounding-boxes"></a><span data-ttu-id="f2e6a-209">경계 상자 추가</span><span class="sxs-lookup"><span data-stu-id="f2e6a-209">Adding Bounding Boxes</span></span>

<span data-ttu-id="f2e6a-210">경계 상자를 사용 하면 직접 조작 (근거리 상호 작용)과 광선 기반 조작 (먼 상호 작용)에 대해 한 손으로 개체를 보다 쉽고 직관적으로 조작할 수 있습니다. 경계 상자는 특정 축을 따라 개체의 크기를 조정 하 고 회전 하는 데 grabbed 수 있는 핸들을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-210">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both direct manipulation (near interaction) and ray-based manipulation (far interaction.) Bounding boxes provide handles that can be grabbed for scaling and rotating objects along a specific axis.</span></span>

>[!NOTE]
><span data-ttu-id="f2e6a-211">개체에 경계 상자를 추가 하려면 먼저이 단원의 앞에서 설명한 것 처럼 개체 (예: 상자 collider)에 collider가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-211">Before you can add a bounding box to an object, you first need to have a collider on the object (e.g., a box collider), as was covered previously in this lesson.</span></span> <span data-ttu-id="f2e6a-212">Colliders 개체를 선택 하 고 개체의 검사자 패널에서 구성 요소 추가 > 상자 Collider를 선택 하 여 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-212">Colliders can be added by selecting the object and in the object's inspector panel selecting Add Component>Box Collider.</span></span>

1. <span data-ttu-id="f2e6a-213">상자 collider가 아직 없는 경우 지구 코어 개체에 상자 collider를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-213">Add a box collider to the Earth Core object if one does not already exist.</span></span> <span data-ttu-id="f2e6a-214">지정 된 지침에 따라 기본 모듈 자산 폴더에 제공 된 prefab를 사용 하는 경우에는 box collider 및 setup이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-214">The box collider and setup are not required, if using the prefab provided in the Base Module Assets folder per the instructions given.</span></span> <span data-ttu-id="f2e6a-215">지구 코어의 경우 아래 이미지에 나와 있는 것 처럼 지구 코어 아래의 node_id30 개체에 collider 상자를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-215">In the case of the earth core, we added the box collider to the, node_id30, object underneath the earth core, as shown in the image below.</span></span> <span data-ttu-id="f2e6a-216">개체의 검사자 탭에서 node_id30를 선택 하 고 구성 요소 추가를 클릭 한 다음 box collider를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-216">Select node_id30 from the object's Inspector tab, click Add Component, and search for box collider.</span></span>

    ![Lesson4 Chapter3 Step1im](images/Lesson4_Chapter3_step1im.PNG)

    ![Lesson4 Chapter3 Step2im](images/Lesson4_chapter3_step2im.PNG)

    >[!NOTE]
    ><span data-ttu-id="f2e6a-219">상자를 크기가 너무 크거나 너무 작게 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-219">Make sure that you size the box collider so that it’s not too big or too small.</span></span> <span data-ttu-id="f2e6a-220">둘러싸고 있는 개체(이 예제에서는 지구 코어)와 대략 동일한 크기여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-220">It should be roughly the same size as the object it’s surrounding (in this example, the earth core).</span></span> <span data-ttu-id="f2e6a-221">Collider 상자에서 Collider 편집 옵션을 선택 하 여 필요에 따라 상자를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-221">Adjust the box collider as needed by selecting the Edit Collider option in the box collider.</span></span> <span data-ttu-id="f2e6a-222">X, y 및 z 값을 변경 하거나 편집기 장면 창에서 경계 상자 처리기를 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-222">You can either changing the x, y, and z values or drag the bounding box handlers in the Editor Scene window.</span></span>

    ![Lesson4 Chapter3 Noteim](images/Lesson4_Chapter3_noteim.PNG)

2. <span data-ttu-id="f2e6a-224">지구 코어의 node_id30 개체에 경계 상자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-224">Add a bounding box to the earth core's node_id30 object.</span></span> <span data-ttu-id="f2e6a-225">이렇게 하려면 3DObjectCollection에서 node_id30 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-225">To do this, select the node_id30 object from the 3DObjectCollection.</span></span> <span data-ttu-id="f2e6a-226">검사기 탭에서 구성 요소 추가를 클릭 하 고 경계 상자를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-226">In the inspector tab, click Add Component, and search for bounding box.</span></span> <span data-ttu-id="f2e6a-227">경계 상자, 상자 충돌체 및 조작 스크립트(조작 처리기, 근거리 잡기형 상호 작용)가 모두 동일한 게임 개체에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-227">Ensure that the bounding box, box collider, and manipulation scripts (manipulation handler, near interaction grabbable) are all on the same game object.</span></span>

3. <span data-ttu-id="f2e6a-228">경계 상자의 동작 섹션에 있는 활성화 드롭다운 목록에서 시작 시 활성화를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-228">In the bounding box's Behavior section, select Activate on Start from the Activation drop-down list.</span></span> <span data-ttu-id="f2e6a-229">다양 한 활성화 옵션 및 기타 경계 상자 옵션에 대 한 추가 정보를 검토 하려면 [Mrtk의 경계 상자 설명서](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-229">To review additional details regarding the various activation options and other bounding box options, see the [MRTK's bounding box documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html>)</span></span>

    <span data-ttu-id="f2e6a-230">*다음 몇 단계에서는 기본 상자 자료를 조정 하 고, grabbed 하는 동안 재질을 조정 하 고, 모퉁이 및 측 핸들의 시각화를 조정 하 여 경계 상자를 어떻게 표시 하는 방법도 변경 합니다. MRTK에는 경계 상자를 사용자 지정 하기 위한 몇 가지 옵션이 포함 되어 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="f2e6a-230">*In the next few steps, we will also change how the bounding box looks by adjusting the default box material, the material while it’s being grabbed as well as the visualization of the corner and side handles. The MRTK contains several options to customize the bounding box.*</span></span>

4. <span data-ttu-id="f2e6a-231">프로젝트 패널에서 "boundingbox"를 검색 하면 아래 이미지와 같이 검색 결과에서 파란색 구로 표시 된 자료 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-231">In the Project panel, search for "boundingbox" and you’ll see a list of materials denoted by a blue sphere in the search results as shown in the image below.</span></span>

5. <span data-ttu-id="f2e6a-232">경계 상자 구성 요소에서 boundingbox 재질을 box 재질 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-232">Drag the boundingbox material into the box material slot on the bounding box component.</span></span> <span data-ttu-id="f2e6a-233">또한 boundingboxgrabbed 재질을 잡고 경계 상자 구성 요소의 box grabbed 재질 슬롯에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-233">Also grab the boundingboxgrabbed material and put that in the box grabbed material slot on the bounding box component.</span></span>

    ![mrlearning-base-ch4-3-step5](images/mrlearning-base-ch4-3-step5.png)

6. <span data-ttu-id="f2e6a-235">MRTK_BoundingBox_ScaleHandle prefab를 크기 조정 핸들 prefab 슬롯으로 끌고 MRTK_BoundingBox_RotateHandle를 결합 상자 구성 요소의 회전 핸들 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-235">Drag the MRTK_BoundingBox_ScaleHandle prefab into the scale handle prefab slot and the MRTK_BoundingBox_RotateHandle prefab into the rotation handle slot on the bonding box component.</span></span>

    ![mrlearning-base-ch4-3-step6](images/mrlearning-base-ch4-3-step6.png)

7. <span data-ttu-id="f2e6a-237">경계 상자가 오른쪽 개체를 대상으로 하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-237">Make sure the bounding box is targeting the right object.</span></span> <span data-ttu-id="f2e6a-238">경계 상자 구성 요소에는 대상 개체 및 경계 재정의 스크립트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-238">In the bounding box component, there is the target object and bounds override scripts.</span></span> <span data-ttu-id="f2e6a-239">경계 상자를 포함 하는 개체를 두 슬롯 모두로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-239">Drag the object that has the bounding box around it to both of these slots.</span></span> <span data-ttu-id="f2e6a-240">이 예제에서는 아래 이미지에 나와 있는 것 처럼 node_id30 개체를 두 슬롯으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-240">In this example, drag the node_id30 object to both of these slots, as shown in the image below.</span></span>

    ![mrlearning-base-ch4-3-step7](images/mrlearning-base-ch4-3-step7.png)

    >[!NOTE]
    ><span data-ttu-id="f2e6a-242">응용 프로그램을 시작 하거나 재생할 때 개체는 파란색 프레임으로 둘러싸여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-242">When you start or play the application, your object will be surrounded by a blue frame.</span></span> <span data-ttu-id="f2e6a-243">개체의 크기를 조정하려면 해당 프레임의 모서리를 끌면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-243">You’re welcome to drag the corners of that frame to resize the object.</span></span> <span data-ttu-id="f2e6a-244">크기 조정 핸들 및 회전 핸들이 더 크고 더 표시 되도록 하려면 기본 경계 상자 설정 (4 ~ 6 단계를 방지)을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-244">If you want the scaling handles and the rotation handles to be larger and more visible, it is recommend using the default bounding box settings (avoiding Steps 4 -through 6.)</span></span>

8. <span data-ttu-id="f2e6a-245">기본 경계 상자 시각화로 돌아가려면 경계 상자의 개체에 대 한 검사기 패널에서 회전 핸들 prefab을 선택 하 고 delete 키를 눌러 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-245">To return to the default bounding box visualization, in the Inspector panel of the bounding box's object, select the rotation handle prefab and press delete to remove it.</span></span> <span data-ttu-id="f2e6a-246">재생 모드로 전환 하면 wou에 아래 이미지와 비슷한 경계 상자 시각화가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-246">When you enter play mode, wou will see a bounding box visualization similar to the image below.</span></span>

    ![mrlearning-base-ch4-3-step8](images/mrlearning-base-ch4-3-step8.png)

    >[!NOTE]
    ><span data-ttu-id="f2e6a-248">경계 상자 시각화는 재생 모드에 있을 때만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-248">The bounding box visualizations only appear when in play mode.</span></span>

### <a name="adding-touch-effects"></a><span data-ttu-id="f2e6a-249">터치 효과 추가</span><span class="sxs-lookup"><span data-stu-id="f2e6a-249">Adding touch effects</span></span>

<span data-ttu-id="f2e6a-250">이 예제에서는 손으로 개체를 터치할 때 사운드 효과를 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-250">In this example, we are going to play a sound effect when you touch an object with your hand.</span></span>

1. <span data-ttu-id="f2e6a-251">오디오 원본 구성 요소를 게임 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-251">Add an audio source component to your game object.</span></span> <span data-ttu-id="f2e6a-252">장면 계층 구조에서 Octa 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-252">Select the Octa object in your scene hierarchy.</span></span> <span data-ttu-id="f2e6a-253">검사기 패널에서 구성 요소 추가 단추를 클릭 하 고 오디오 원본을 검색 한 다음 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-253">In the inspector panel, click the Add Component button, search for and select audio source.</span></span> <span data-ttu-id="f2e6a-254">이 오디오 원본을 사용하여 이후 단계에서 사운드 효과를 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-254">We’ll use this audio source to play a sound effect in a later step.</span></span>

    >[!NOTE]
    ><span data-ttu-id="f2e6a-255">Octa 개체에 collider box가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-255">Ensure that the Octa object has a box collider on it.</span></span>

2. <span data-ttu-id="f2e6a-256">Near 인터랙션 Touchable 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-256">Add the Near Interaction Touchable component.</span></span> <span data-ttu-id="f2e6a-257">검사기 패널에서 구성 요소 추가 단추를 클릭 하 고 거의 상호 작용 touchable를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-257">Click the Add Component button in the Inspector panel and search for near interaction touchable.</span></span> <span data-ttu-id="f2e6a-258">선택하여 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-258">Select it to add the component.</span></span>

    >[!NOTE]
    ><span data-ttu-id="f2e6a-259">이전에는 거의 상호 작용 grabbable를 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-259">Previously, we added near interaction grabbable.</span></span> <span data-ttu-id="f2e6a-260">이와 거의 상호 작용 touchable의 차이점은 grabbable 상호 작용은 개체를 grabbed 하 고 상호 작용 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-260">The difference between this and near interaction touchable is that the grabbable interaction is intended for an object to be grabbed and interacted with.</span></span> <span data-ttu-id="f2e6a-261">Touchable 구성 요소는 개체에 대 한 작업을 수행 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-261">The touchable component is intended for the object to be touched.</span></span> <span data-ttu-id="f2e6a-262">두 구성 요소 모두 상호 작용의 조합을 위해 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-262">Both components can be used together for a combination of interactions.</span></span>

    ![Lesson4 Chapter4 Step1 2Im](images/Lesson4_chapter4_step1-2im.PNG)

3. <span data-ttu-id="f2e6a-264">직접 상호 작용 터치 스크립트에를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-264">Add in the Hand Interaction Touch script.</span></span> <span data-ttu-id="f2e6a-265">이전 단계와 마찬가지로 구성 요소 추가를 클릭 하 고 직접 상호 작용 터치를 검색 하 여 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-265">Just like the previous step, click Add Component and search for hand interaction touch to add it.</span></span>

    <span data-ttu-id="f2e6a-266">스크립트에는 세 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-266">Notice that you have three options with the script:</span></span>
    * <span data-ttu-id="f2e6a-267">터치 완료 시: 개체를 터치 하 고 해제할 때 트리거</span><span class="sxs-lookup"><span data-stu-id="f2e6a-267">On Touch Completed: Triggers when you touch and release the object</span></span>
    * <span data-ttu-id="f2e6a-268">터치 시작 시: 개체가 작업 될 때 트리거</span><span class="sxs-lookup"><span data-stu-id="f2e6a-268">On Touch Started: Triggers when the object is touched</span></span>
    * <span data-ttu-id="f2e6a-269">터치 업데이트 시: 손을 개체와 접촉 하는 동안 주기적으로 트리거</span><span class="sxs-lookup"><span data-stu-id="f2e6a-269">On Touch Updated: Triggers periodically while your hand is touching the object</span></span>

    <span data-ttu-id="f2e6a-270">이 예에서는 Touch 시작 설정으로 작업 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-270">For this example, we will be working with the On Touch Started setting.</span></span>

    >[!NOTE]
    ><span data-ttu-id="f2e6a-271">이 스크립트는이 자습서의 시작 부분에서 가져온 BaseModuleAssets Unity 패키지에 포함 되어 있으며 원래 MRTK에는 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-271">This script is included with the BaseModuleAssets Unity package that you imported as at the beginning of this tutorial and it is not included in the original MRTK.</span></span>

4. <span data-ttu-id="f2e6a-272">터치 시작 옵션에서 + 단추를 클릭 하 고 Octa 개체를 빈 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-272">Click the + button on the On Touch Started option and drag the Octa object into the empty field.</span></span>

    ![mrlearning-base-ch4-4-step4](images/mrlearning-base-ch4-4-step4.png)

5. <span data-ttu-id="f2e6a-274">함수가 없는 드롭다운에서 PlayOneShot를 > 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-274">In the drop-down that says No Function, select AudioSource > PlayOneShot.</span></span> <span data-ttu-id="f2e6a-275">아래 개념을 사용하여 오디오 클립을 이 필드에 추가하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-275">We will add an audio clip to this field using the concepts below:</span></span>

    * <span data-ttu-id="f2e6a-276">MRTK는 오디오 클립의 작은 목록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-276">The MRTK does provide a small list of audio clips.</span></span> <span data-ttu-id="f2e6a-277">프로젝트 패널에서 자유롭게 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-277">Feel free to explore these in your Project panel.</span></span> <span data-ttu-id="f2e6a-278">MixedRealityToolkit > 표준 자산 > 오디오 폴더 > 자산 아래에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-278">You will find them under the Assets > MixedRealityToolkit.SDK > Standard Assets > Audio folder.</span></span>
    * <span data-ttu-id="f2e6a-279">이 예에서는 MRTK_Gem 오디오 클립을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-279">For this example, we are going to use the MRTK_Gem audio clip.</span></span>
    * <span data-ttu-id="f2e6a-280">오디오 클립을 추가 하려면 프로젝트 패널에서 원하는 클립을 PlayOneShot 필드로 끌기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-280">To add an audio clip, simply drag the clip you want from the project panel into the AudioSource.PlayOneShot field.</span></span>

    ![mrlearning-base-ch4-4-step5](images/mrlearning-base-ch4-4-step5.png)

   <span data-ttu-id="f2e6a-282">이제 사용자가 Octa 개체에 도달 하 여 접촉 하면 MRTK_Gem 오디오 트랙이 재생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-282">Now, when the user reaches out and touches the Octa object, the audio track MRTK_Gem will play.</span></span> <span data-ttu-id="f2e6a-283">또한 직접 상호 작용 터치 스크립트는 개체의 색을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-283">The Hand Interaction Touch script will also adjust the color of the object, when touched.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f2e6a-284">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-284">Congratulations</span></span>

<span data-ttu-id="f2e6a-285">이 자습서에서는 그리드 컬렉션에서 3D 개체를 구성 하는 방법 및 거의 상호 작용 (추적 된 손으로 직접 이동) 및 먼 상호 작용 (응시 광선 또는 핸드 광선 사용)을 사용 하 여 이러한 개체를 조작 하는 방법 (크기 조정, 회전 및 이동)을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-285">In this tutorial, you learned how to organize 3D objects in a grid collection and how to manipulate these objects (scaling, rotating, and moving) using near interaction (directly grabbing with tracked hands) and far interaction (using gaze rays or hand rays).</span></span> <span data-ttu-id="f2e6a-286">3D 개체 주위에 경계 상자를 배치 하는 방법 및 경계 상자에서 gizmo 그리려면를 사용 하 고 사용자 지정 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-286">You also learned how to put bounding boxes around 3D objects, and learned how to use and customize the gizmos on the bounding boxes.</span></span> <span data-ttu-id="f2e6a-287">마지막으로 개체를 터치할 때 이벤트를 트리거하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="f2e6a-287">Finally, you learned how to trigger events when touching an object.</span></span>

[<span data-ttu-id="f2e6a-288">다음 단원: 6. 고급 입력 옵션 탐색</span><span class="sxs-lookup"><span data-stu-id="f2e6a-288">Next Lesson: 6. Exploring advanced input options</span></span>](mrlearning-base-ch5.md)
