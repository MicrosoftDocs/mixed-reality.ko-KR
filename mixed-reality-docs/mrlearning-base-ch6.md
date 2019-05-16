---
title: MR 학습 자료 모듈-음력 모듈 어셈블리 샘플 환경
description: 이 단원에서는 고유한 샘플 환경을 만들려면 이전 단원에서 학습 하는 여러 개념 결합 했습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: unity, 자습서, hololens, 혼합된 현실
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730844"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a><span data-ttu-id="64688-104">MR 학습 자료 모듈-음력 모듈 어셈블리 샘플 환경</span><span class="sxs-lookup"><span data-stu-id="64688-104">MR Learning Base Module - Lunar Module Assembly Sample Experience</span></span>

<span data-ttu-id="64688-105">이 단원에서는 고유한 샘플 환경을 만들려면 이전 단원에서 학습 하는 여러 개념 결합 했습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-105">In this lesson, we will combine multiple concepts learned from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="64688-106">추적된 손을 사용 하 여 음력 모듈 부분을 선택 하 고 음력 모듈을 조합 하는 사용자가 해야 하는 여기서 음력 모듈 어셈블리 응용 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="64688-106">We will create a lunar module assembly application whereby a user will need to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="64688-107">배치 힌트를 경험에 따르면 다시 설정 하는 데 공간으로 음력 모듈 시작을 설정/해제 하려면 pressable 단추 사용!</span><span class="sxs-lookup"><span data-stu-id="64688-107">We will use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="64688-108">나중에 자습서를 계속 예정 강력한 다중 사용자 사용 사례 공간 맞춤에 대 한 Azure 공간 앵커를 활용 하는 비롯 하 여이 환경을 구축 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-108">In future tutorials, we will continue to build upon this experience, including powerful multi-user use-cases that leverages Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="64688-109">목표</span><span class="sxs-lookup"><span data-stu-id="64688-109">Objectives</span></span>

- <span data-ttu-id="64688-110">고유한 환경을 만들려면 이전 단원에서 여러 개념을 결합</span><span class="sxs-lookup"><span data-stu-id="64688-110">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="64688-111">개체를 설정/해제 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="64688-111">Learn how to toggle objects</span></span>
- <span data-ttu-id="64688-112">Pressable 단추를 사용 하 여 복잡 한 이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="64688-112">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="64688-113">Rigidbody 물리 및 강제 사용</span><span class="sxs-lookup"><span data-stu-id="64688-113">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="64688-114">탐색 도구 설명 사용</span><span class="sxs-lookup"><span data-stu-id="64688-114">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="64688-115">지침</span><span class="sxs-lookup"><span data-stu-id="64688-115">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="64688-116">음력 모듈 구성</span><span class="sxs-lookup"><span data-stu-id="64688-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="64688-117">이 챕터에서는 샘플 경험을 만드는 데 필요한 다양 한 구성 요소를 도입 했습니다 것입니다.</span><span class="sxs-lookup"><span data-stu-id="64688-117">In this chapter, we will be introduced to the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="64688-118">음력 모듈 어셈블리 prefab 자료 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-118">Add the lunar module assembly prefab to your Base Scene.</span></span> <span data-ttu-id="64688-119">사용자 프로젝트 탭에서이 위해 "Rocket Launcher_Tutorial." 검색</span><span class="sxs-lookup"><span data-stu-id="64688-119">To do this, in your project tab, search for "Rocket Launcher_Tutorial."</span></span> <span data-ttu-id="64688-120">자산에는 prefab을 찾을 수 있습니다 > BaseModuleAssets > Prefabs 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-120">You may also find the prefab in Assets>BaseModuleAssets>Prefabs.</span></span> <span data-ttu-id="64688-121">두 rocket launcher prefabs; 표시 될 수 있습니다. 이름이 "자습서" 및 다른 이름으로 "완료합니다."</span><span class="sxs-lookup"><span data-stu-id="64688-121">You may see two rocket launcher prefabs; one with the name "tutorial" and another with the name "complete."</span></span> <span data-ttu-id="64688-122">"Rocket Launcher_Tutorial" prefab을 자료 장면 끕니다.</span><span class="sxs-lookup"><span data-stu-id="64688-122">Drag the "Rocket Launcher_Tutorial" prefab to your Base Scene.</span></span> <span data-ttu-id="64688-123">자유롭게 장면에 prefab의 배치를 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-123">Feel free to position the placement of the prefab in your scene.</span></span>
   <span data-ttu-id="64688-124">참고: "Rocket Launcher_Complete" prefab은 참조용으로 완료 된 시작 관리자를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-124">Note: The "Rocket Launcher_Complete" prefab is the completed launcher, provided for reference.</span></span> 

![6 단원 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="64688-126">재질 "x-ray." 라는 여러 자식 개체 표시는 계층의 "Rocket Launcher_Tutorial" 게임 개체를 확장 하 고 "음력 모듈" 개체를 더 확장</span><span class="sxs-lookup"><span data-stu-id="64688-126">If you expand the "Rocket Launcher_Tutorial" game object in your hierarchy, and further expand the "Lunar Module" object, you will see several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="64688-127">"X-레이" 자료 약간 반투명 색을 사용자에 대 한 배치 힌트로 사용 하는 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-127">The "x-ray" material allows for a slightly translucent color which we will use as placement hints for the user.</span></span> 

<span data-ttu-id="64688-128">![6 단원 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) 하려는 사용자 상호 작용 아래 이미지 에서처럼 음력 모듈에 5 개 부분이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user is going to interact with, as shown in the image below:</span></span>

1.  <span data-ttu-id="64688-129">Rover 인클로저</span><span class="sxs-lookup"><span data-stu-id="64688-129">The Rover Enclosure</span></span>
2.  <span data-ttu-id="64688-130">연료 탱크</span><span class="sxs-lookup"><span data-stu-id="64688-130">The Fuel Tank</span></span>
3.  <span data-ttu-id="64688-131">에너지 셀</span><span class="sxs-lookup"><span data-stu-id="64688-131">The Energy Cell</span></span>
4.  <span data-ttu-id="64688-132">도킹 포털</span><span class="sxs-lookup"><span data-stu-id="64688-132">The Docking Portal</span></span> 
5.  <span data-ttu-id="64688-133">외부 센서</span><span class="sxs-lookup"><span data-stu-id="64688-133">The External sensor</span></span>

![6 단원 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="64688-135">참고: 장면에 있는 개체의 이름에는 기본 장면 계층에 표시 되는 게임 개체 이름이 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-135">Note: The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="64688-136">2단계: 오디오 소스 음력 모듈에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-136">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="64688-137">음력 모듈 기본 장면 계층에서 선택 되어 있는지 확인 하 고 "구성 요소를 추가 합니다." 클릭</span><span class="sxs-lookup"><span data-stu-id="64688-137">Make sure the lunar module is selected in your base scene hierarchy and click "Add Component."</span></span> <span data-ttu-id="64688-138">"오디오 원본"에 대 한 검색 하 고 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-138">Search for "Audio Source" and add it to the object.</span></span> <span data-ttu-id="64688-139">비워 둠 지금은</span><span class="sxs-lookup"><span data-stu-id="64688-139">Leave it blank for now.</span></span> <span data-ttu-id="64688-140">나중에 시작 소리를 재생 하려면이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64688-140">We will use this to play the launching sound later.</span></span>
 <span data-ttu-id="64688-141">![6 단원 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) 3 단계: "설정/해제 배치 힌트입니다." 스크립트 추가</span><span class="sxs-lookup"><span data-stu-id="64688-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) Step 3: Add the script "toggle placement hints."</span></span> <span data-ttu-id="64688-142">"구성 요소 추가" 및 "설정/해제 배치 힌트입니다."에 대 한 검색을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-142">Click "Add Component" and search for "Toggle Placement Hints."</span></span> <span data-ttu-id="64688-143">이것이 앞에서 언급 한 반투명 힌트 (x-레이 자료를 사용 하 여 개체)를 켜거나 끌 수 있도록 사용자 지정 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="64688-143">This is a custom script that allows you to turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span> 
<span data-ttu-id="64688-144">![6 단원 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) 4 단계: 5 개의 개체가 있으므로 게임 개체 배열 크기에 대 한 "5"에 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) Step 4: Since we have 5 objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="64688-145">그런 다음 5 개의 새 요소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64688-145">Then you should see 5 new elements appear.</span></span> 

![6 단원 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="64688-147">"None (게임 개체)입니다."를 표시 하는 상자를 끌어 각 반투명 개체</span><span class="sxs-lookup"><span data-stu-id="64688-147">Drag each of the translucent objects into the boxes that say "None (Game Object)."</span></span> <span data-ttu-id="64688-148">기본 장면에 음력 모듈에서 다음 개체를 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="64688-148">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="64688-149">• 백팩</span><span class="sxs-lookup"><span data-stu-id="64688-149">•   Backpack</span></span>

<span data-ttu-id="64688-150">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="64688-150">•   GasTank</span></span>

<span data-ttu-id="64688-151">• Topleftbody</span><span class="sxs-lookup"><span data-stu-id="64688-151">•   Topleftbody</span></span>

<span data-ttu-id="64688-152">• 코</span><span class="sxs-lookup"><span data-stu-id="64688-152">•   Nose</span></span>

<span data-ttu-id="64688-153">• LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="64688-153">•   LeftTwirler</span></span>

 ![6 단원 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="64688-155">이제 "배치 힌트를 설정/해제" 스크립트 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64688-155">Now the "toggle placement hints" script is configured.</span></span> <span data-ttu-id="64688-156">이렇게 하면 힌트를 켜거나 끄고를 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-156">This will allow us to turn the hints on and off.</span></span>

<span data-ttu-id="64688-157">5단계: "음력 모듈 시작" 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-157">Step 5: Add the "launch lunar module" script.</span></span> <span data-ttu-id="64688-158">"구성 요소 추가" 단추를 클릭, "시작 음력 모듈"에 대 한 검색 하 고 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-158">Click the "Add Component" button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="64688-159">이 스크립트는 음력 모듈을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-159">This script will be responsible for launching the lunar module.</span></span> <span data-ttu-id="64688-160">구성된 단추를 누를 것 음력 모듈의 rigid 바디 구성 요소를 위쪽 force 추가 하 고 모듈을 위쪽으로 시작 하면 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-160">When we press a configured button, it will add an upward force to the lunar module's rigid body component and will cause the module to launch upwards.</span></span> <span data-ttu-id="64688-161">인 경우 실내 음력 모듈에 ceiling 메시에 대해 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-161">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="64688-162">하지만 옥외 있다면이 fly에서 공간에 무기한으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-162">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![6 단원 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="64688-164">6단계: 음력 모듈까지 정상적으로 비행 됩니다 있도록 위한 것을 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-164">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="64688-165">0.01의 값을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-165">Try a value of 0.01.</span></span> <span data-ttu-id="64688-166">"Rb" 필드를 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="64688-166">Leave the "Rb" field blank.</span></span> <span data-ttu-id="64688-167">Rb rigid 바디를 의미 하 고 런타임에이 필드를 자동으로 채워지지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="64688-167">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![6 단원 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="64688-169">음력 모듈 부분 개요</span><span class="sxs-lookup"><span data-stu-id="64688-169">Lunar Module Parts Overview</span></span>
<span data-ttu-id="64688-170">음력 모듈 부분 부모 개체에는 사용자와 상호 작용할 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="64688-170">The Lunar Module parts parent object is the collection of the objects that the user will interact with.</span></span> <span data-ttu-id="64688-171">장면 이름을 paretheses에서 레이블이 지정) (으로 게임 개체 이름은 아래 목록에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64688-171">The game object names (with scene labeled names in paretheses) are provided in the list below:</span></span>

- <span data-ttu-id="64688-172">백팩을 (연료 탱크가)</span><span class="sxs-lookup"><span data-stu-id="64688-172">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="64688-173">GasTank (에너지 셀)</span><span class="sxs-lookup"><span data-stu-id="64688-173">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="64688-174">TopLeftBody (Rover 인클로저)</span><span class="sxs-lookup"><span data-stu-id="64688-174">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="64688-175">코 (도킹 포털)</span><span class="sxs-lookup"><span data-stu-id="64688-175">Nose (Docking Portal)</span></span>
- <span data-ttu-id="64688-176">LeftTwirler (외부 센서)</span><span class="sxs-lookup"><span data-stu-id="64688-176">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="64688-177">4 단원에서 설명 했 듯이 이러한 각 개체에는 조작 처리기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-177">Notice that each of these objects has the manipulation handler, as discussed in lesson 4.</span></span> <span data-ttu-id="64688-178">조작 처리기를 사용 하 여 사용자 잡고 개체를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-178">With the manipulation handler, users are able to grab and manipulate the object.</span></span> <span data-ttu-id="64688-179">또한 "두 전달된 조작 유형" 설정 "이동 및 회전 합니다."로 설정 되어 있는지를 note합니다</span><span class="sxs-lookup"><span data-stu-id="64688-179">Also note that the setting "two handed manipulation type" is set to "move and rotate."</span></span> <span data-ttu-id="64688-180">이 개체를 이동 하 고 어셈블리 응용 프로그램에 대 한 원하는 기능에는 해당 크기를 변경 하지 사용자만 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-180">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="64688-181">또한 먼 조작 모듈 부분의 직접적인 상호 작용에 대해서만 허용 하도록 선택 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-181">In addition, far manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![6 단원 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="64688-183">파트 어셈블리 데모 스크립트 (위에 표시 됨)는 사용자가 음력 모듈에 배치 될 개체를 관리 하는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="64688-183">The part assembly demo script (shown above) is the scrip that manages the objects to be placed on to the lunar module by the user.</span></span> 

<span data-ttu-id="64688-184">"개체를 현재 위치" 필드 선택 (n 이미지 위의 백팩을/연료 탱크가의 경우)에 연결할 수 있는 개체와는 변환입니다.</span><span class="sxs-lookup"><span data-stu-id="64688-184">The "Object To Place" field is the transform that is selected (n the case of the image above, the backpack/fuel tank) with the object that it can connect to.</span></span> 

<span data-ttu-id="64688-185">"가까운 거리" 및 "훨씬 Distance" 설정 하려는 파트 진행에서 맞춰집니다 또는 릴리스될 근접도 확인 하는 것에 대 한 책임이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-185">The "Near Distance" and "Far Distance" settings are responsible for determining the proximity to which parts will snap in place or be released.</span></span> <span data-ttu-id="64688-186">예를 들어 백팩을/연료 탱크 제자리에 맞출 음력 모듈에서 0.1 단위 되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-186">For example, the backpack/fuel tank would need to be 0.1 units away from the lunar module to snap into place.</span></span> <span data-ttu-id="64688-187">"지금까지 거리" 개체 음력 모듈에서 분리 되도록 해야 하는 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-187">The "Far Distance" sets the location where the object needs to be to detach from the lunar module.</span></span> <span data-ttu-id="64688-188">이 경우 사용자의 직접 백팩을/연료 탱크를 잡고 위치로 다시 맞추기에서 제거할 음력 모듈에서 0.2 단위 이었기 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-188">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="64688-189">"도구 설명 개체"은 장면에서 도구 설명 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="64688-189">The "Tool Tip Object" is the tool tip label in the scene.</span></span> <span data-ttu-id="64688-190">개체 위치에 모눈을 레이블이 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64688-190">When the objects are snapped in place, the label will be disabled.</span></span> 

<span data-ttu-id="64688-191">오디오 소스 자동으로 잡을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-191">The Audio Source will be automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="64688-192">배치 힌트 단추</span><span class="sxs-lookup"><span data-stu-id="64688-192">Placement Hints Buttons</span></span>
<span data-ttu-id="64688-193">[단원 2](mrlearning-base-ch2.md)를 배치 하 고 항목의 색 변경 작업을 수행 하거나 푸시 될 때 소리를 재생 하는 단추를 구성 하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-193">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="64688-194">배치 힌트를 표시 하거나 숨기는 단추를 구성 하는 것을 이러한 원칙을 사용 하도록 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64688-194">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="64688-195">목표 반투명 배치 힌트의 표시 유형을 설정/해제는 배치 힌트 단추를 누를 때마다 있도록 단추가 구성 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="64688-195">The goal is to configure our button so that every time the user presses the placement hint button, it will toggle visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="64688-196">1단계: 배치 힌트 개체를 기본 장면 계층 구조에서 선택한 음력 모듈 검사기 창에서 빈 런타임은 슬롯으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-196">Step 1: Move the Lunar Module to the empty "runtime only" slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="64688-197">![6 단원 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 2 단계: 이제 드롭다운 목록을 라고 표시 된 부분, "function 없습니다."를 클릭</span><span class="sxs-lookup"><span data-stu-id="64688-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the dropdown list where it says, "no function."</span></span> <span data-ttu-id="64688-198">해당 메뉴 및 "TogglePlacementHints," 아래로 이동 "ToggleGameObjects ()"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-198">Go down to "TogglePlacementHints," and under that menu select "ToggleGameObjects ()."</span></span> <span data-ttu-id="64688-199">ToggleGameObjects()는 배치 힌트를 설정 / 해제 단추를 누를 때마다 표시 되거나 숨겨지도록 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-199">ToggleGameObjects() will toggle the placement hints on and off so that they are visible or invisible every time the button is pressed.</span></span>
 <span data-ttu-id="64688-200">![6 단원 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="64688-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="64688-201">구성 다시 설정 단추</span><span class="sxs-lookup"><span data-stu-id="64688-201">Configuring the Reset Button</span></span>

<span data-ttu-id="64688-202">사용자는 실수 또는 실수로 throw 하거나 제거 하려는 환경을 rest 경우가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64688-202">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to rest the experience.</span></span> <span data-ttu-id="64688-203">다시 설정 단추 환경을 다시 시작 하는 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-203">The reset button will add the ability to restart the experience.</span></span> 

<span data-ttu-id="64688-204">1단계: 다시 설정 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-204">Step 1: Select the reset button.</span></span> <span data-ttu-id="64688-205">기본 장면에서 라고 하는 "ResetRoundButton."</span><span class="sxs-lookup"><span data-stu-id="64688-205">In the base scene, it’s named "ResetRoundButton."</span></span> 

<span data-ttu-id="64688-206">2단계: 기본 장면 계층 음력 모듈 "단추가 눌림" 아래에서 빈 슬롯 끌어옵니다 [관리자] 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="64688-206">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under "button pressed" the inspector panel.</span></span>
 <span data-ttu-id="64688-207">![6 단원 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="64688-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="64688-208">3단계: "Function 없습니다" 라는 드롭다운 메뉴를 선택 하 고 "LaunchLunarModule." 위로</span><span class="sxs-lookup"><span data-stu-id="64688-208">Step 3: Select the dropdown menu that says, "no function" and hover over "LaunchLunarModule."</span></span> <span data-ttu-id="64688-209">이제 "resetModule ()"를 선택</span><span class="sxs-lookup"><span data-stu-id="64688-209">Now select "resetModule ()."</span></span>

![6 단원 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="64688-211">참고: 기본적으로 "GameObject.BroadcastMessage" 하도록 구성 되어 있는지 "ResetPlacement." 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-211">Note: You will notice that by default the "GameObject.BroadcastMessage" is configured to "ResetPlacement."</span></span> <span data-ttu-id="64688-212">이 메시지를 브로드캐스팅하는 RocketLauncher_Tutorial의 모든 자식 개체에 대 한 "ResetPlacement"를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-212">This will broadcast a message called "ResetPlacement" for every child object of RocketLauncher_Tutorial.</span></span> <span data-ttu-id="64688-213">"ResetPlacement()"에 대 한 메서드가 포함 된 모든 개체의 위치를 다시 설정 하 여 해당 메시지에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-213">Any object that has a method for "ResetPlacement()" will respond to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="64688-214">음력 모듈 시작</span><span class="sxs-lookup"><span data-stu-id="64688-214">Launching the Lunar Module</span></span>
<span data-ttu-id="64688-215">이 챕터 [시작] 단추를 구성 했습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-215">This chapter we will be configuring the launch button.</span></span> <span data-ttu-id="64688-216">이렇게 하면 사용자가 단추를 눌러를 공간으로 음력 모듈을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-216">This will permit the user to press the button and launch the Lunar Module into space.</span></span>

<span data-ttu-id="64688-217">1단계: [시작] 단추를 선택 합니다. (기본 장면에서 라고 하는 "LaunchRoundButton").</span><span class="sxs-lookup"><span data-stu-id="64688-217">Step 1: Select the launch button (in the base scene it’s named "LaunchRoundButton").</span></span> <span data-ttu-id="64688-218">검사기 창에서 "터치 End" 아래에서 빈 슬롯을 음력 모듈을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="64688-218">Drag the Lunar Module to the empty slot under "Touch End" in the inspector panel.</span></span>
 <span data-ttu-id="64688-219">![6 단원 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 2 단계: "Function 없습니다." 라는 드롭다운 메뉴를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the dropdown menu that says, "no function."</span></span> <span data-ttu-id="64688-220">"LaunchLunarModule" 위에 놓고 "StopThruster ()"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-220">Hover over "LaunchLunarModule" and select "StopThruster ()."</span></span> <span data-ttu-id="64688-221">이 얼마나 러스트 음력 모듈에 사용자가 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-221">This will control how much thrust the user wants to give to the Lunar Module.</span></span> 
 <span data-ttu-id="64688-222">![6 단원 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) 3 단계: "ButtonPressed()"에서 음력 모듈 (클릭, 대기 중 및 끌기) 빈 슬롯을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) Step 3: Under "ButtonPressed()", add the Lunar Module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="64688-223">4단계: "Function 없습니다" 라는 드롭다운 메뉴를 클릭 하 고 "LaunchLunarModule" 마우스로 "StartThruster ()"를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-223">Step 4: Click the dropdown menu that says, "no function" and hover over "LaunchLunarModule" and select "StartThruster ()."</span></span> 
 <span data-ttu-id="64688-224">![6 단원 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) 5 단계: 음악을 rocket이 시작 하는 경우 연동 되도록 음악 음력 모듈에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) Step 5: Add music to the Lunar Module so that when the rocket takes off, the music will play.</span></span> <span data-ttu-id="64688-225">이렇게 하려면 "단추 Pressed()" 아래에서 다음 빈 슬롯을 음력 모듈을 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="64688-225">To do this, drag the Lunar Module to the next empty slot under "Button Pressed()".</span></span>

<span data-ttu-id="64688-226">6단계: "Function 없습니다" 라는 드롭다운 메뉴를 선택 하 고 "AudioSource" 마우스로 "PlayOneShot (AudioClip)."를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-226">Step 6: Select the dropdown menu that says, "no function" and hover over "AudioSource" and select "PlayOneShot (AudioClip)."</span></span> <span data-ttu-id="64688-227">다양 한 소리를 MRTK 함께 살펴보시기 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="64688-227">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="64688-228">예를 들어 하겠습니다 "MRTK_Gem."를 사용 하 여 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-228">For this example, we are going to stick with "MRTK_Gem."</span></span>
 <span data-ttu-id="64688-229">![6 단원 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="64688-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="64688-230">축 하.</span><span class="sxs-lookup"><span data-stu-id="64688-230">Congratulations</span></span> 
<span data-ttu-id="64688-231">이 응용 프로그램을 완전히 구성한!</span><span class="sxs-lookup"><span data-stu-id="64688-231">You have fully configured this application!</span></span> <span data-ttu-id="64688-232">이제 play를 누르면 완벽 하 게 음력 모듈을 조합, 힌트를 설정/해제, 음력 모듈을 시작 하 수 것부터 다시 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64688-232">Now when you press play, you can fully assemble the Lunar Module, toggle hints, launch the Lunar Module, and reset it to do it all over again.</span></span>
