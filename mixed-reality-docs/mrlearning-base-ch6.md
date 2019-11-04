---
title: 자습서 시작-7. 음력 모듈 샘플 응용 프로그램 만들기
description: 이 단원에서는 이전 단원에서 배운 여러 개념을 결합 하 여 고유한 샘플 환경을 만듭니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: a4f405b29ac87945a8585beeed83c1beb450eb0e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437759"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="23185-105">7. 음력 모듈 샘플 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="23185-105">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="23185-106">이 자습서에서는 다양 한 개념을 이전 단원에서 결합 하 여 고유한 샘플 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="23185-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="23185-107">사용자가 추적 된 손을 사용 하 여 음력 모듈 부분을 선택 하 고 음력 모듈을 조합 하 여 사용 해야 하는 음력 모듈 어셈블리 응용 프로그램을 만드는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-107">You will learn how to create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="23185-108">Pressable 단추를 사용 하 여 배치 힌트를 전환 하 고, 경험을 다시 설정 하 고, 음력 모듈을 공간으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-108">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="23185-109">이후 자습서에서는 공간 맞춤을 위해 Azure 공간 앵커를 활용 하는 강력한 다중 사용자 사용 사례를 포함 하 여이 환경을 계속 빌드할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="23185-109">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="23185-110">목표</span><span class="sxs-lookup"><span data-stu-id="23185-110">Objectives</span></span>

- <span data-ttu-id="23185-111">이전 단원의 여러 개념을 결합하여 고유한 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="23185-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="23185-112">개체를 설정/해제하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="23185-112">Learn how to toggle objects</span></span>
- <span data-ttu-id="23185-113">누를 수 있는 단추를 사용하여 복합 이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="23185-113">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="23185-114">강체 물리학 및 힘 사용</span><span class="sxs-lookup"><span data-stu-id="23185-114">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="23185-115">도구 설명 사용 살펴보기</span><span class="sxs-lookup"><span data-stu-id="23185-115">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="23185-116">지침</span><span class="sxs-lookup"><span data-stu-id="23185-116">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="23185-117">달탐사선 구성</span><span class="sxs-lookup"><span data-stu-id="23185-117">Configuring the Lunar Module</span></span>

<span data-ttu-id="23185-118">이 섹션에서는 샘플 환경을 만드는 데 필요한 다양 한 구성 요소를 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-118">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="23185-119">기본 장면에 prefab 음력 모듈 어셈블리를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-119">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="23185-120">이렇게 하려면 프로젝트 탭에서 로켓 Launcher_Tutorial을 검색 합니다. prefab에서 Prefabs를 찾습니다. > ></span><span class="sxs-lookup"><span data-stu-id="23185-120">To do this, search for the Rocket Launcher_Tutorial in the Project tab. Find the prefab in Assets->BaseModuleAssets->Prefabs.</span></span> <span data-ttu-id="23185-121">또한 두 개의 로켓 시작 관리자 prefabs이 표시 됩니다. 이름이 "tutorial"이 고 다른 하나는 "complete"입니다.</span><span class="sxs-lookup"><span data-stu-id="23185-121">You'll also see two rocket launcher prefabs; one with the name "tutorial" and the other with the name "complete".</span></span> <span data-ttu-id="23185-122">로켓 Launcher_Tutorial prefab를 기본 장면으로 끌고 원하는 대로 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-122">Drag the Rocket Launcher_Tutorial prefab to your base scene, and position as you wish.</span></span>
<span data-ttu-id="23185-123">참고: 로켓 Launcher_Complete prefab는 참조를 위해 제공 되는 완성 된 시작 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="23185-123">Note: The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="23185-125">계층에서 로켓 Launcher_Tutorial game 개체를 확장 하 고 음력 Module 개체를 추가로 확장 하는 경우 "x-레이" 라는 재질을 포함 하는 여러 자식 개체를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-125">If you expand the Rocket Launcher_Tutorial game object in your hierarchy and further expand the Lunar Module object, you find several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="23185-126">"X-y" 재질은 사용자에 대 한 배치 힌트로 사용 되는 약간 반투명 색을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-126">The "x-ray" material allows for a slightly translucent color that will be used as placement hints for the user.</span></span> 

<span data-ttu-id="23185-127">![6 단원에서는](images/Lesson6_Chapter1_noteaim.PNG) Chapter1.txt 5는 아래 이미지에 나와 있는 것 처럼 사용자가 상호 작용 하는 음력 모듈의 5 부분으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23185-127">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user will interact with, as shown in the image below:</span></span>

1.  <span data-ttu-id="23185-128">탐사선 인클로저</span><span class="sxs-lookup"><span data-stu-id="23185-128">The Rover Enclosure</span></span>
2.  <span data-ttu-id="23185-129">연료 탱크</span><span class="sxs-lookup"><span data-stu-id="23185-129">The Fuel Tank</span></span>
3.  <span data-ttu-id="23185-130">에너지 셀</span><span class="sxs-lookup"><span data-stu-id="23185-130">The Energy Cell</span></span>
4.  <span data-ttu-id="23185-131">도킹 포털</span><span class="sxs-lookup"><span data-stu-id="23185-131">The Docking Portal</span></span> 
5.  <span data-ttu-id="23185-132">외부 센서</span><span class="sxs-lookup"><span data-stu-id="23185-132">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="23185-134">참고: 기본 장면 계층 구조에 표시 되는 게임 개체 이름은 장면에 있는 개체의 이름과 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-134">Note: The Game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="23185-135">2 단계: 음력 모듈에 오디오 소스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-135">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="23185-136">기본 장면 계층 구조에서 음력 모듈이 선택 되어 있는지 확인 하 고 구성 요소 추가를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-136">Make sure the lunar module is selected in your base scene hierarchy and click Add Component.</span></span> <span data-ttu-id="23185-137">오디오 소스를 검색 하 여 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-137">Search for Audio Source and add it to the object.</span></span> <span data-ttu-id="23185-138">지금은 비워 두고 "Spatialize" 확인란을 클릭 하 여 공간 오디오를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-138">Leave it blank for now, but click the "Spatialize" checkbox to enable spatial audio.</span></span> <span data-ttu-id="23185-139">나중에 시작 하는 소리를 재생 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-139">You will use this to play the launching sound later.</span></span>

 ![6 단원에서는 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)  
<span data-ttu-id="23185-141">3 단계: 배치 힌트 설정/해제 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-141">Step 3: Add the script Toggle Placement Hints.</span></span> <span data-ttu-id="23185-142">구성 요소 추가를 클릭 하 고 배치 힌트 설정/해제를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-142">Click Add Component and search for Toggle Placement Hints.</span></span> <span data-ttu-id="23185-143">앞에서 설명한 것 처럼 반투명 힌트 (x-레이 재료를 사용 하는 개체)를 설정 및 해제할 수 있는 사용자 지정 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="23185-143">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material), as mentioned earlier.</span></span>  
![6 단원에서는 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)  
<span data-ttu-id="23185-145">4 단계: 5 개의 개체가 있으므로 게임 개체 배열 크기에 "5"를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-145">Step 4: Since we have five objects, type "5" for the game object array size.</span></span> <span data-ttu-id="23185-146">그러면 5 개의 새 요소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23185-146">You'll then see five new elements appear.</span></span>  


![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="23185-148">각 투명 개체를 모든 이름 (Game 개체) 상자로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="23185-148">Drag each of the translucent objects into all the Name (Game Obect) boxes.</span></span>
<span data-ttu-id="23185-149">기본 장면에서 달탐사선으로부터 다음 개체를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="23185-149">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="23185-150">•   Backpack</span><span class="sxs-lookup"><span data-stu-id="23185-150">•   Backpack</span></span>

<span data-ttu-id="23185-151">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="23185-151">•   GasTank</span></span>

<span data-ttu-id="23185-152">•   Topleftbody</span><span class="sxs-lookup"><span data-stu-id="23185-152">•   Topleftbody</span></span>

<span data-ttu-id="23185-153">•   Nose</span><span class="sxs-lookup"><span data-stu-id="23185-153">•   Nose</span></span>

<span data-ttu-id="23185-154">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="23185-154">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="23185-156">이제 배치 힌트 설정/해제 스크립트가 구성 되어 힌트를 켜고 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-156">The Toggle Placement Hints script is now configured, which allows us to turn hints on and off.</span></span>

<span data-ttu-id="23185-157">5 단계: 시작 음력 모듈 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-157">Step 5: Add the Launch Lunar Module script.</span></span> <span data-ttu-id="23185-158">구성 요소 추가 단추를 클릭 하 고 "음력 모듈 시작"을 검색 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-158">Click the Add Component button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="23185-159">이 스크립트는 음력 모듈을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-159">This script launches the lunar module.</span></span> <span data-ttu-id="23185-160">구성 된 단추를 누르면 음력 모듈의 고정 본문 구성 요소에 상향 force가 추가 되 고 모듈이 위쪽으로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23185-160">When we press a configured button, it adds an upward force to the lunar module's rigid body component and causes the module to launch upwards.</span></span> <span data-ttu-id="23185-161">실내에 있다면 달탐사선이 천장 메시에 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-161">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="23185-162">최대값이이 많거나 최대값이 없는 영역에 있는 경우 음력 모듈은 무기한으로 공간을 확보 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23185-162">If you are in an area with high ceilings or no ceilings, the lunar module will fly into space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="23185-164">6 단계: 음력 모듈이 정상적으로 작동 하도록 위한 것 조정</span><span class="sxs-lookup"><span data-stu-id="23185-164">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="23185-165">값 0.01을 시도해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="23185-165">Try a value of 0.01.</span></span> <span data-ttu-id="23185-166">"Rb" 필드는 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="23185-166">Leave the "Rb" field blank.</span></span> <span data-ttu-id="23185-167">Rb는 고정 본문을 나타내며 런타임 중에이 필드가 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="23185-167">Rb stands for Rigid body and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="23185-169">음력 모듈 부분 개요</span><span class="sxs-lookup"><span data-stu-id="23185-169">Lunar Module Parts overview</span></span>
<span data-ttu-id="23185-170">음력 모듈 파트 부모 개체는 사용자가 상호 작용 하는 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="23185-170">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="23185-171">Paretheses에 이름이 지정 된 장면이 있는 게임 개체 이름이 아래 목록에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23185-171">The Game object names with scene labeled names in paretheses, are provided in the list below:</span></span>

- <span data-ttu-id="23185-172">Backpack(연료 탱크)</span><span class="sxs-lookup"><span data-stu-id="23185-172">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="23185-173">GasTank(에너지 셀)</span><span class="sxs-lookup"><span data-stu-id="23185-173">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="23185-174">TopLeftBody(탐사선 인클로저)</span><span class="sxs-lookup"><span data-stu-id="23185-174">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="23185-175">Nose(도킹 포트)</span><span class="sxs-lookup"><span data-stu-id="23185-175">Nose (Docking Portal)</span></span>
- <span data-ttu-id="23185-176">LeftTwirler(외부 센서)</span><span class="sxs-lookup"><span data-stu-id="23185-176">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="23185-177">이러한 각 개체에는 4 단원에서 설명한 대로 조작 처리기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-177">Notice that each of these objects has a manipulation handler, as explained in Lesson 4.</span></span> <span data-ttu-id="23185-178">이 기능을 사용 하면 사용자가 개체를 가져오고 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-178">This feature enables users to grab and manipulate the object.</span></span> <span data-ttu-id="23185-179">또한 두 번의 이동 조작 유형인 설정은 이동 및 회전으로 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-179">Also note that the setting, Two Handed Manipulation Type, is set to Move and Rotate.</span></span> <span data-ttu-id="23185-180">이 옵션은 사용자가 개체를 이동 하 고 해당 크기를 변경 하지 않도록 허용 합니다 .이는 어셈블리 응용 프로그램에 대해 원하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="23185-180">This option only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="23185-181">또한 모듈 파트의 직접 상호 작용에 대해서만 허용 하도록 Far 조작이 선택 취소 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-181">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="23185-183">파트 어셈블리 데모 스크립트 (위에 표시 됨)는 사용자가 음력 모듈에 저장 하는 개체를 관리 하는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="23185-183">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span> 

<span data-ttu-id="23185-184">필드를 놓을 개체는 위의 이미지에 표시 된 것 처럼 선택한 변환 이며, 연결 된 개체와 연결 된 백팩/연료 탱크입니다.</span><span class="sxs-lookup"><span data-stu-id="23185-184">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span> 

<span data-ttu-id="23185-185">근거리 거리 및 원거리 거리 설정에 따라 부품이 제자리에 스냅 되거나 출시 될 수 있는 근접성이 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23185-185">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="23185-186">예를 들어 백팩/연료 탱크는 한 곳에 맞추기 전에 음력 모듈에서 0.1 단위 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-186">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="23185-187">먼 거리 설정은 개체가 음력 모듈에서 분리 될 수 있는 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-187">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="23185-188">이 경우 사용자의 손이 백팩/연료 탱크를 쥐고 달탐사선에서 0.2단위 떨어지게 끌어 위치에서 분리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-188">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="23185-189">도구 설명 개체는 장면의 도구 설명 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="23185-189">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="23185-190">개체를 제자리에 물릴 때 레이블은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-190">When the objects are snapped in place, the label is disabled.</span></span> 

<span data-ttu-id="23185-191">오디오 소스가 자동으로 grabbed 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23185-191">The Audio Source is automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="23185-192">배치 힌트 단추</span><span class="sxs-lookup"><span data-stu-id="23185-192">Placement Hints buttons</span></span>
<span data-ttu-id="23185-193">[2 단원](mrlearning-base-ch2.md)에서는 항목의 색을 변경 하거나 푸시 될 때 소리를 재생 하는 등의 작업을 수행 하는 단추를 설정 하 고 구성 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-193">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when pushed.</span></span> <span data-ttu-id="23185-194">이제 이 원칙을 사용하여 배치 힌트를 설정/해제하는 단추를 구성해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-194">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="23185-195">목표는 사용자가 배치 힌트 단추를 누를 때마다 투명 한 배치 힌트의 표시 유형을 전환 하도록 단추를 구성 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="23185-195">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="23185-196">1 단계: 기본 장면 계층 구조에서 배치 힌트 개체가 선택 되어 있는 동안에는 inspector 패널의 빈 런타임 전용 슬롯으로 음력 모듈을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-196">Step 1: Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="23185-197">![6 단원에서는 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 2 단계: 함수 없음 드롭다운 목록을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Click the No Function dropdown list.</span></span> <span data-ttu-id="23185-198">TogglePlacementHints로 이동 하 고 해당 메뉴 아래에서 ToggleGameObjects ()를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-198">Go down to TogglePlacementHints and select ToggleGameObjects () under that menu.</span></span> <span data-ttu-id="23185-199">ToggleGameObjects ()는 단추를 누를 때마다 표시 되거나 표시 되지 않도록 배치 힌트를 설정 및 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-199">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>  
 <span data-ttu-id="23185-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="23185-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="23185-201">다시 설정 단추 구성</span><span class="sxs-lookup"><span data-stu-id="23185-201">Configuring the Reset button</span></span>

<span data-ttu-id="23185-202">사용자가 실수를 하 여 실수로 개체를 다시 throw 하거나 환경을 다시 설정 하려는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-202">There will be situations where the user makes a mistake, accidently throws the object away or just wants to reset the experience.</span></span> <span data-ttu-id="23185-203">다시 설정 단추는 환경을 다시 시작 하는 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-203">The Reset button adds the ability to restart the experience.</span></span> 

<span data-ttu-id="23185-204">1 단계: 다시 설정 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-204">Step 1: Select the Reset button.</span></span> <span data-ttu-id="23185-205">기본 장면에서는 이름이 ResetRoundButton입니다.</span><span class="sxs-lookup"><span data-stu-id="23185-205">In the base scene, it’s named ResetRoundButton.</span></span> 

<span data-ttu-id="23185-206">2 단계: 검사기 패널의 단추를 누른 상태에서 기본 장면 계층 구조에서 음력 모듈을 빈 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="23185-206">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed on the inspector panel.</span></span>
 <span data-ttu-id="23185-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="23185-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="23185-208">3 단계: 함수 없음 드롭다운 메뉴를 선택 하 고 LaunchLunarModule를 가리킨 다음 resetModule ()을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-208">Step 3: Select the No Function dropdown menu and hover over LaunchLunarModule, then select resetModule ().</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="23185-210">참고: 기본적으로 GameObject BroadcastMessage는 배치를 ResetPlacement 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-210">Note: Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="23185-211">그러면 RocketLauncher_Tutorial의 모든 자식 개체에 대해 ResetPlacement 라는 메시지가 브로드캐스트합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-211">This broadcasts a message called ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="23185-212">ResetPlacement ()에 대 한 메서드가 있는 개체는 해당 위치를 다시 설정 하 여 해당 메시지에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-212">Any object that has a method for ResetPlacement() responds to that message by resetting its position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="23185-213">음력 모듈 시작</span><span class="sxs-lookup"><span data-stu-id="23185-213">Launching the lunar module</span></span>
<span data-ttu-id="23185-214">이 섹션에서는 시작 단추를 구성 하는 방법에 대해 설명 합니다 .이 단추를 사용 하면 사용자가 단추를 누르고 음력 모듈을 공간으로 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-214">This section explains how to configure the Launch button, which permits the user to press the button and launch the lunar module into space.</span></span>

<span data-ttu-id="23185-215">1 단계: 시작 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-215">Step 1: Select the Launch button.</span></span> <span data-ttu-id="23185-216">기본 장면에서는 LaunchRoundButton 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-216">In the base scene, it’s called LaunchRoundButton.</span></span> <span data-ttu-id="23185-217">Inspector 패널의 Touch End 아래에 있는 빈 슬롯으로 음력 모듈을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="23185-217">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>
 <span data-ttu-id="23185-218">![6 단원에서는 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 2 단계: 함수 없음 드롭다운 메뉴를 선택 하 고 LaunchLunarModule를 마우스로 가리킨 다음 StopThruster ()를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-218">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the No Function dropdown menu and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="23185-219">이는 사용자가 음력 모듈에 제공할 위한 것 크기를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-219">This controls how much thrust the user wants to give to the lunar module.</span></span> 
 <span data-ttu-id="23185-220">![6 단원에서는 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="23185-220">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span></span>  
<span data-ttu-id="23185-221">3 단계: ButtonPressed ()에서 음력 모듈을 추가 합니다 (클릭 하 고 누르고 끌어 놓기).</span><span class="sxs-lookup"><span data-stu-id="23185-221">Step 3: Under ButtonPressed(), add the lunar module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="23185-222">4 단계: 함수 없음 드롭다운 메뉴를 클릭 하 고 LaunchLunarModule를 가리킨 다음 StartThruster ()를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-222">Step 4: Click the No function dropdown menu, hover over LaunchLunarModule and select StartThruster ().</span></span> 
 <span data-ttu-id="23185-223">![6 단원에서는 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span><span class="sxs-lookup"><span data-stu-id="23185-223">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span></span>  
<span data-ttu-id="23185-224">5 단계: 로켓이 꺼진 경우 음악이 재생 되도록 음력 모듈에 음악을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-224">Step 5: Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="23185-225">이렇게 하려면 음력 모듈을 단추 누름 () 아래의 빈 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="23185-225">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

<span data-ttu-id="23185-226">6 단계: 함수 없음 드롭다운 메뉴를 선택 하 고 오디오 원본 위에 마우스를 놓고 PlayOneShot (오디오 클립)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-226">Step 6: Select the No Function dropdown menu, hover over AudioSource and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="23185-227">MRTK에 포함된 여러 사운드를 원하는 대로 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="23185-227">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="23185-228">이 예에서는 "MRTK_Gem"를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-228">In this example, we'll use "MRTK_Gem."</span></span>
 <span data-ttu-id="23185-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="23185-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="23185-230">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="23185-230">Congratulations</span></span> 
<span data-ttu-id="23185-231">이 응용 프로그램을 완전히 구성 했습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-231">You have fully configured this application.</span></span> <span data-ttu-id="23185-232">이제 play를 누르면 음력 모듈을 완전히 조합 하 고, 힌트를 전환 하 고, 음력 모듈을 시작 하 고 다시 시작 하도록 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23185-232">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module and reset it to start again.</span></span>
