---
title: 자습서 시작-7. 음력 모듈 샘플 응용 프로그램 만들기
description: 이 단원에서는 이전 단원에서 배운 여러 개념을 결합 하 여 고유한 샘플 환경을 만듭니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: b033e4f9a379fb1778da3d94da70262e073d141b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926515"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="6d629-105">7. 음력 모듈 샘플 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="6d629-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="6d629-106">이 자습서에서는 다양 한 개념을 이전 단원에서 결합 하 여 고유한 샘플 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="6d629-107">사용자가 추적 된 손을 사용 하 여 음력 모듈 부분을 선택 하 고 음력 모듈을 조합 하 여 사용 해야 하는 음력 모듈 어셈블리 응용 프로그램을 만드는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-107">You will learn how to create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="6d629-108">Pressable 단추를 사용 하 여 배치 힌트를 전환 하 고, 경험을 다시 설정 하 고, 음력 모듈을 공간으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="6d629-109">이후 자습서에서는 공간 맞춤을 위해 Azure 공간 앵커를 활용 하는 강력한 다중 사용자 사용 사례를 포함 하 여이 환경을 계속 빌드할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="6d629-110">목표</span><span class="sxs-lookup"><span data-stu-id="6d629-110">Objectives</span></span>

- <span data-ttu-id="6d629-111">이전 단원의 여러 개념을 결합하여 고유한 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="6d629-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="6d629-112">개체를 설정/해제하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="6d629-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="6d629-113">누를 수 있는 단추를 사용하여 복합 이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="6d629-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="6d629-114">강체 물리학 및 힘 사용</span><span class="sxs-lookup"><span data-stu-id="6d629-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="6d629-115">도구 설명 사용 살펴보기</span><span class="sxs-lookup"><span data-stu-id="6d629-115">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="6d629-116">지침</span><span class="sxs-lookup"><span data-stu-id="6d629-116">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="6d629-117">달탐사선 구성</span><span class="sxs-lookup"><span data-stu-id="6d629-117">Configuring the Lunar Module</span></span>

<span data-ttu-id="6d629-118">이 섹션에서는 샘플 환경을 만드는 데 필요한 다양 한 구성 요소를 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-118">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="6d629-119">기본 장면에 prefab 음력 모듈 어셈블리를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-119">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="6d629-120">이 작업을 수행 하려면 프로젝트 탭에서 자산 > BasemodulPrefabs Sets > .로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-120">To do this, in the Project tab navigate to Assets > BaseModuleAssets > Prefabs.</span></span> <span data-ttu-id="6d629-121">두 개의 로켓 시작 관리자 prefabs이 표시 되 고, 로켓 Launcher_Tutorial prefab를 장면으로 끌고, 원하는 대로 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-121">You will see two rocket launcher prefabs, drag the Rocket Launcher_Tutorial prefab into your scene, and position as you wish.</span></span>

    >[!NOTE]
    ><span data-ttu-id="6d629-122">로켓 Launcher_Complete prefab는 참조용으로 제공 되는 완성 된 시작 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-122">The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span>

    ![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

    <span data-ttu-id="6d629-124">계층에서 로켓 Launcher_Tutorial 게임 개체를 확장 하 고 음력 Module 개체를 추가로 확장 하는 경우 "x-레이" 라는 재질을 포함 하는 여러 자식 개체를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-124">If you expand the Rocket Launcher_Tutorial game object in your hierarchy and further expand the Lunar Module object, you find several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="6d629-125">"X-y" 재질은 사용자에 대 한 배치 힌트로 사용 되는 약간 반투명 색을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-125">The "x-ray" material allows for a slightly translucent color that will be used as placement hints for the user.</span></span> 

    ![6 단원에서는 Chapter1.txt 참고 목표](images/Lesson6_Chapter1_noteaim.PNG)

    <span data-ttu-id="6d629-127">아래 이미지에 표시 된 것 처럼 사용자가 상호 작용 하는 음력 모듈은 5 부분으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-127">There are five parts to the lunar module that the user will interact with, as shown in the image below:</span></span>

    1. <span data-ttu-id="6d629-128">탐사선 인클로저</span><span class="sxs-lookup"><span data-stu-id="6d629-128">The Rover Enclosure</span></span>
    2. <span data-ttu-id="6d629-129">연료 탱크</span><span class="sxs-lookup"><span data-stu-id="6d629-129">The Fuel Tank</span></span>
    3. <span data-ttu-id="6d629-130">에너지 셀</span><span class="sxs-lookup"><span data-stu-id="6d629-130">The Energy Cell</span></span>
    4. <span data-ttu-id="6d629-131">도킹 포털</span><span class="sxs-lookup"><span data-stu-id="6d629-131">The Docking Portal</span></span>
    5. <span data-ttu-id="6d629-132">외부 센서</span><span class="sxs-lookup"><span data-stu-id="6d629-132">The External sensor</span></span>

    ![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

    >[!NOTE]
    ><span data-ttu-id="6d629-134">기본 장면에 표시되는 게임 개체 이름은 장면의 개체 이름과 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-134">The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

2. <span data-ttu-id="6d629-135">오디오 원본을 LunarModule game 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-135">Add an audio source to the LunarModule game object.</span></span> <span data-ttu-id="6d629-136">장면 계층 구조에서 LunarModule이 선택 되어 있는지 확인 하 고 구성 요소 추가를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-136">Make sure the LunarModule is selected in your scene hierarchy and click Add Component.</span></span> <span data-ttu-id="6d629-137">오디오 소스를 검색 하 고 게임 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-137">Search for Audio Source and add it to the game object.</span></span> <span data-ttu-id="6d629-138">지금은 오디오 클립 필드를 비워 두거나, 특수 Blend 설정을 0에서 1로 변경 하 여 공간 오디오를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-138">Leave the AudioClip field blank for now, but change the Special Blend setting from 0 to 1 so to enable spatial audio.</span></span> <span data-ttu-id="6d629-139">이 오디오 소스는 나중에 시작 하는 소리를 재생 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-139">You will use this audio source to play the launching sound later.</span></span>

    ![6 단원에서는 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)

3. <span data-ttu-id="6d629-141">스크립트를 추가 합니다. 배치 힌트를 설정/해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-141">Add the script Toggle Placement Hints.</span></span> <span data-ttu-id="6d629-142">구성 요소 추가를 클릭 하 고 배치 힌트 설정/해제를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-142">Click Add Component and search for Toggle Placement Hints.</span></span> <span data-ttu-id="6d629-143">앞에서 설명한 것 처럼 반투명 힌트 (x-레이 재료를 사용 하는 개체)를 설정 및 해제할 수 있는 사용자 지정 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-143">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material), as mentioned earlier.</span></span>

    ![6 단원에서는 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)

4. <span data-ttu-id="6d629-145">5 개의 개체가 있으므로 게임 개체 배열 크기에 대해 "5"를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-145">Since we have five objects, type "5" for the game object array size.</span></span> <span data-ttu-id="6d629-146">그러면 5 개의 새 요소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-146">You will then see five new elements appear.</span></span>

    ![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

    <span data-ttu-id="6d629-148">각 투명 개체를 모든 이름 (게임 개체) 상자로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-148">Drag each of the translucent objects into all the Name (Game Object) boxes.</span></span> <span data-ttu-id="6d629-149">위의 이미지에 표시 된 것 처럼 장면의 음력 모듈에서 개체 배열 필드로 다음 개체를 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-149">Drag the following objects from the lunar module in your scene into the object array fields as shown in the image above:</span></span>

    ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

    <span data-ttu-id="6d629-151">이제 배치 힌트 설정/해제 스크립트가 구성 되어 힌트를 켜고 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-151">The Toggle Placement Hints script is now configured, which allows us to turn hints on and off.</span></span>

5. <span data-ttu-id="6d629-152">시작 음력 모듈 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-152">Add the Launch Lunar Module script.</span></span> <span data-ttu-id="6d629-153">구성 요소 추가 단추를 클릭 하 고 "음력 모듈 시작"을 검색 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-153">Click the Add Component button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="6d629-154">이 스크립트는 음력 모듈을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-154">This script launches the lunar module.</span></span> <span data-ttu-id="6d629-155">구성 된 단추를 누르면 음력 모듈의 고정 본문 구성 요소에 상향 force가 추가 되 고 모듈이 위쪽으로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-155">When we press a configured button, it adds an upward force to the lunar module's rigid body component and causes the module to launch upwards.</span></span> <span data-ttu-id="6d629-156">실내에 있다면 달탐사선이 천장 메시에 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-156">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="6d629-157">최대값이이 많거나 최대값이 없는 영역에 있는 경우 음력 모듈은 무기한으로 공간을 확보 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-157">If you are in an area with high ceilings or no ceilings, the lunar module will fly into space indefinitely.</span></span>

    ![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

6. <span data-ttu-id="6d629-159">추진력을 조정하여 달탐사선이 정상적으로 비행할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-159">Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="6d629-160">값 0.01을 시도해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-160">Try a value of 0.01.</span></span> <span data-ttu-id="6d629-161">"Rb" 필드는 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-161">Leave the "Rb" field blank.</span></span> <span data-ttu-id="6d629-162">Rb는 고정 본문을 나타내며 런타임 중에이 필드가 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-162">Rb stands for Rigid body and this field will be automatically populated during runtime.</span></span>

    ![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="6d629-164">음력 모듈 부분 개요</span><span class="sxs-lookup"><span data-stu-id="6d629-164">Lunar Module Parts overview</span></span>

<span data-ttu-id="6d629-165">음력 모듈 파트 부모 개체는 사용자가 상호 작용 하는 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-165">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="6d629-166">괄호 안에 이름이 지정 된 장면이 있는 게임 개체 이름은 아래 목록에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-166">The Game object names with scene labeled names in parentheses, are provided in the list below:</span></span>

- <span data-ttu-id="6d629-167">백팩 (에너지 셀)</span><span class="sxs-lookup"><span data-stu-id="6d629-167">Backpack (Energy Cell)</span></span>
- <span data-ttu-id="6d629-168">GasTank (연료 탱크)</span><span class="sxs-lookup"><span data-stu-id="6d629-168">GasTank (Fuel Tank)</span></span>
- <span data-ttu-id="6d629-169">TopLeftBody(탐사선 인클로저)</span><span class="sxs-lookup"><span data-stu-id="6d629-169">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="6d629-170">Nose(도킹 포트)</span><span class="sxs-lookup"><span data-stu-id="6d629-170">Nose (Docking Portal)</span></span>
- <span data-ttu-id="6d629-171">LeftTwirler(외부 센서)</span><span class="sxs-lookup"><span data-stu-id="6d629-171">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="6d629-172">이러한 각 개체에는 4 단원에서 설명한 대로 조작 처리기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-172">Notice that each of these objects has a manipulation handler, as explained in Lesson 4.</span></span> <span data-ttu-id="6d629-173">이 기능을 사용 하면 사용자가 개체를 가져오고 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-173">This feature enables users to grab and manipulate the object.</span></span> <span data-ttu-id="6d629-174">또한 두 번의 이동 조작 유형인 설정은 이동 및 회전으로 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-174">Also note that the setting, Two Handed Manipulation Type, is set to Move and Rotate.</span></span> <span data-ttu-id="6d629-175">이 옵션은 사용자가 개체를 이동 하 고 해당 크기를 변경 하지 않도록 허용 합니다 .이는 어셈블리 응용 프로그램에 대해 원하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-175">This option only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="6d629-176">또한 모듈 파트의 직접 상호 작용에 대해서만 허용 하도록 Far 조작이 선택 취소 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-176">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="6d629-178">파트 어셈블리 데모 스크립트 (위에 표시 됨)는 사용자가 음력 모듈에 저장 하는 개체를 관리 하는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-178">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span>

<span data-ttu-id="6d629-179">필드를 놓을 개체는 위의 이미지에 표시 된 것 처럼 선택한 변환 이며, 연결 된 개체와 연결 된 백팩/연료 탱크입니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-179">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span>

<span data-ttu-id="6d629-180">근거리 거리 및 원거리 거리 설정에 따라 부품이 제자리에 스냅 되거나 출시 될 수 있는 근접성이 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-180">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="6d629-181">예를 들어 백팩/연료 탱크는 한 곳에 맞추기 전에 음력 모듈에서 0.1 단위 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-181">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="6d629-182">먼 거리 설정은 개체가 음력 모듈에서 분리 될 수 있는 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-182">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="6d629-183">이 경우 사용자의 손이 백팩/연료 탱크를 쥐고 달탐사선에서 0.2단위 떨어지게 끌어 위치에서 분리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-183">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="6d629-184">도구 설명 개체는 장면의 도구 설명 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-184">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="6d629-185">개체를 제자리에 물릴 때 레이블은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-185">When the objects are snapped in place, the label is disabled.</span></span>

<span data-ttu-id="6d629-186">오디오 소스가 자동으로 grabbed 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-186">The Audio Source is automatically grabbed.</span></span>

### <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="6d629-187">배치 힌트 단추 구성</span><span class="sxs-lookup"><span data-stu-id="6d629-187">Configuring the Placement Hints button</span></span>

<span data-ttu-id="6d629-188">[2 단원](mrlearning-base-ch2.md)에서는 항목의 색을 변경 하거나 푸시 될 때 소리를 재생 하는 등의 작업을 수행 하는 단추를 설정 하 고 구성 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-188">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when pushed.</span></span> <span data-ttu-id="6d629-189">이제 이 원칙을 사용하여 배치 힌트를 설정/해제하는 단추를 구성해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-189">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span>

<span data-ttu-id="6d629-190">목표는 사용자가 배치 힌트 단추를 누를 때마다 투명 한 배치 힌트의 표시 유형을 전환 하도록 단추를 구성 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-190">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span>

1. <span data-ttu-id="6d629-191">기본 장면 계층 구조에서 배치 힌트 개체가 선택 되어 있는 동안에는 inspector 패널의 빈 런타임 전용 슬롯으로 음력 모듈을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-191">Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span>

    ![6 단원에서는 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG)

2. <span data-ttu-id="6d629-193">함수 없음 드롭다운 목록을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-193">Click the No Function dropdown list.</span></span> <span data-ttu-id="6d629-194">TogglePlacementHints로 이동 하 고 해당 메뉴 아래에서 ToggleGameObjects ()를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-194">Go down to TogglePlacementHints and select ToggleGameObjects () under that menu.</span></span> <span data-ttu-id="6d629-195">ToggleGameObjects ()는 단추를 누를 때마다 표시 되거나 표시 되지 않도록 배치 힌트를 설정 및 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-195">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>

    ![6 단원에서는 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)

### <a name="configuring-the-reset-button"></a><span data-ttu-id="6d629-197">다시 설정 단추 구성</span><span class="sxs-lookup"><span data-stu-id="6d629-197">Configuring the Reset button</span></span>

<span data-ttu-id="6d629-198">사용자가 실수를 하는 경우가 있으며, 실수로 개체를 실수로 throw 하거나 환경을 다시 설정 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-198">There will be situations where the user makes a mistake, accidentally throws the object away or just wants to reset the experience.</span></span> <span data-ttu-id="6d629-199">다시 설정 단추는 환경을 다시 시작 하는 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-199">The Reset button adds the ability to restart the experience.</span></span>

1. <span data-ttu-id="6d629-200">다시 설정 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-200">Select the Reset button.</span></span> <span data-ttu-id="6d629-201">기본 장면에서는 이름이 ResetRoundButton입니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-201">In the base scene, it’s named ResetRoundButton.</span></span>

2. <span data-ttu-id="6d629-202">기본 장면 계층에서 음력 모듈을 검사기 패널의 단추 아래에 있는 빈 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-202">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed on the inspector panel.</span></span>

    ![6 단원에서는 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)

3. <span data-ttu-id="6d629-204">함수 없음 드롭다운 메뉴를 선택 하 고 LaunchLunarModule를 마우스로 가리킨 다음 resetModule ()을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-204">Select the No Function dropdown menu and hover over LaunchLunarModule, then select resetModule ().</span></span>

    ![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

    >[!NOTE]
    ><span data-ttu-id="6d629-206">기본적으로 GameObject BroadcastMessage는 배치를 ResetPlacement 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-206">Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="6d629-207">그러면 RocketLauncher_Tutorial의 모든 자식 개체에 대해 ResetPlacement 라는 메시지가 브로드캐스트합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-207">This broadcasts a message named ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="6d629-208">ResetPlacement ()에 대 한 메서드가 있는 개체는 위치를 다시 설정 하 여 해당 메시지에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-208">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span>

### <a name="configuring-the-launch-button"></a><span data-ttu-id="6d629-209">시작 단추 구성</span><span class="sxs-lookup"><span data-stu-id="6d629-209">Configuring the Launch button</span></span>

<span data-ttu-id="6d629-210">이 섹션에서는 시작 단추를 구성 하는 방법에 대해 설명 합니다 .이 단추를 사용 하면 사용자가 단추를 누르고 음력 모듈을 공간으로 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-210">This section explains how to configure the Launch button, which permits the user to press the button and launch the lunar module into space.</span></span>

1. <span data-ttu-id="6d629-211">시작 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-211">Select the Launch button.</span></span> <span data-ttu-id="6d629-212">기본 장면에서는 LaunchRoundButton 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-212">In the base scene, it’s called LaunchRoundButton.</span></span> <span data-ttu-id="6d629-213">Inspector 패널의 Touch End 아래에 있는 빈 슬롯으로 음력 모듈을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-213">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>

    ![6 단원에서는 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG)

2. <span data-ttu-id="6d629-215">함수 없음 드롭다운 메뉴를 선택 하 고 LaunchLunarModule를 마우스로 가리킨 다음 StopThruster ()를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-215">Select the No Function dropdown menu and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="6d629-216">이는 사용자가 음력 모듈에 제공할 위한 것 크기를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-216">This controls how much thrust the user wants to give to the lunar module.</span></span>

    ![6 단원에서는 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)

3. <span data-ttu-id="6d629-218">기본 장면 계층에서 음력 모듈을 검사기 패널의 단추 아래에 있는 빈 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-218">Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed in the inspector panel.</span></span>

4. <span data-ttu-id="6d629-219">함수 없음 드롭다운 메뉴를 클릭 한 다음 LaunchLunarModule에서 StartThruster ()를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-219">Click the No function dropdown menu and then on LaunchLunarModule and select StartThruster ().</span></span>

    ![6 단원에서는 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)

5. <span data-ttu-id="6d629-221">로켓이 꺼진 경우 음악이 재생 되도록 음력 모듈에 음악을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-221">Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="6d629-222">이렇게 하려면 음력 모듈을 단추 누름 () 아래의 빈 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-222">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

6. <span data-ttu-id="6d629-223">함수 없음 드롭다운 메뉴를 선택 하 고 오디오 원본 위에 마우스를 놓고 PlayOneShot (오디오 클립)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-223">Select the No Function dropdown menu, hover over AudioSource and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="6d629-224">MRTK에 포함된 여러 사운드를 원하는 대로 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-224">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="6d629-225">이 예제에서는 "MRTK_Gem"을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-225">In this example, we'll use "MRTK_Gem."</span></span>

    ![6 단원에서는 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)

### <a name="congratulations"></a><span data-ttu-id="6d629-227">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-227">Congratulations</span></span>

<span data-ttu-id="6d629-228">이 응용 프로그램을 완전히 구성 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-228">You have fully configured this application.</span></span> <span data-ttu-id="6d629-229">이제 play를 누르면 음력 모듈을 완전히 조합 하 고, 힌트를 전환 하 고, 음력 모듈을 시작 하 고 다시 시작 하도록 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6d629-229">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module and reset it to start again.</span></span>
