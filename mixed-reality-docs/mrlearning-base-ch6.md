---
title: MR 학습 기본 모듈 - 달탐사선 어셈블리 샘플 환경
description: 이 단원에서는 이전 단원에서 학습한 여러 개념을 결합하여 고유한 샘플 환경을 만듭니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 8a2f388e842d521f991203916177e3dac15769eb
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730844"
---
# <a name="mr-learning-base-module---lunar-module-assembly-sample-experience"></a><span data-ttu-id="f1cd2-104">MR 학습 기본 모듈 - 달탐사선 어셈블리 샘플 환경</span><span class="sxs-lookup"><span data-stu-id="f1cd2-104">MR Learning Base Module - Lunar Module Assembly Sample Experience</span></span>

<span data-ttu-id="f1cd2-105">이 단원에서는 이전 단원에서 학습한 여러 개념을 결합하여 고유한 샘플 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-105">In this lesson, we will combine multiple concepts learned from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="f1cd2-106">사용자가 추적된 손을 사용하여 달탐사선 부품을 선택하고 달탐사선 조립을 시도하는 데 사용할 달탐사선 어셈블리 애플리케이션을 만들겠습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-106">We will create a lunar module assembly application whereby a user will need to use tracked hands to pick up lunar module parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="f1cd2-107">누를 수 있는 단추를 사용하여 배치 힌트를 설정/해제하고 환경을 다시 설정하며 달탐사선을 우주로 발사합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-107">We will use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="f1cd2-108">향후 자습서에서는 공간 맞춤을 위해 Azure Spatial Anchors를 사용하는 강력한 다중 사용자 사용 사례를 포함하여 이러한 경험을 지속적으로 구축해 나갈 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-108">In future tutorials, we will continue to build upon this experience, including powerful multi-user use-cases that leverages Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="f1cd2-109">목표</span><span class="sxs-lookup"><span data-stu-id="f1cd2-109">Objectives</span></span>

- <span data-ttu-id="f1cd2-110">이전 단원의 여러 개념을 결합하여 고유한 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="f1cd2-110">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="f1cd2-111">개체를 설정/해제하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="f1cd2-111">Learn how to toggle objects</span></span>
- <span data-ttu-id="f1cd2-112">누를 수 있는 단추를 사용하여 복합 이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="f1cd2-112">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="f1cd2-113">강체 물리학 및 힘 사용</span><span class="sxs-lookup"><span data-stu-id="f1cd2-113">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="f1cd2-114">도구 설명 사용 살펴보기</span><span class="sxs-lookup"><span data-stu-id="f1cd2-114">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="f1cd2-115">지침</span><span class="sxs-lookup"><span data-stu-id="f1cd2-115">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="f1cd2-116">달탐사선 구성</span><span class="sxs-lookup"><span data-stu-id="f1cd2-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="f1cd2-117">이 챕터에서는 샘플 환경을 만드는 데 필요한 다양한 구성 요소를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-117">In this chapter, we will be introduced to the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="f1cd2-118">달탐사선 어셈블리 프리팹을 기본 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-118">Add the lunar module assembly prefab to your Base Scene.</span></span> <span data-ttu-id="f1cd2-119">이를 위해 프로젝트 탭에서 "Rocket Launcher_Tutorial"을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-119">To do this, in your project tab, search for "Rocket Launcher_Tutorial."</span></span> <span data-ttu-id="f1cd2-120">이 프리팹은 Assets>BaseModuleAssets>Prefabs에서 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-120">You may also find the prefab in Assets>BaseModuleAssets>Prefabs.</span></span> <span data-ttu-id="f1cd2-121">로켓 발사대 프리팹은 이름이 "tutorial"인 것과 "complete"인 것 등, 두 개가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-121">You may see two rocket launcher prefabs; one with the name "tutorial" and another with the name "complete."</span></span> <span data-ttu-id="f1cd2-122">"Rocket Launcher_Tutorial" 프리팹을 기본 장면으로 끌어갑니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-122">Drag the "Rocket Launcher_Tutorial" prefab to your Base Scene.</span></span> <span data-ttu-id="f1cd2-123">장면의 원하는 위치에 프리팹을 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-123">Feel free to position the placement of the prefab in your scene.</span></span>
   <span data-ttu-id="f1cd2-124">참고: "Rocket Launcher_Complete" 프리팹은 완성된 발사대로, 참고를 위해 제공된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-124">Note: The "Rocket Launcher_Complete" prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="f1cd2-126">계층 구조에 "Rocket Launcher_Tutorial" 게임 개체를 펼친 다음, "Lunar Module" 개체를 펼치면 "x-ray"라는 재료가 있는 여러 하위 개체가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-126">If you expand the "Rocket Launcher_Tutorial" game object in your hierarchy, and further expand the "Lunar Module" object, you will see several child objects that have a material called "x-ray."</span></span> <span data-ttu-id="f1cd2-127">"x-ray" 재료는 사용자를 위한 배치 힌트로 사용할 약간 반투명 색상을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-127">The "x-ray" material allows for a slightly translucent color which we will use as placement hints for the user.</span></span> 

<span data-ttu-id="f1cd2-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) 사용자가 상호 작용하는 달탐사선에는 아래 그림과 같이 다섯 가지 부분이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-128">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user is going to interact with, as shown in the image below:</span></span>

1.  <span data-ttu-id="f1cd2-129">탐사선 인클로저</span><span class="sxs-lookup"><span data-stu-id="f1cd2-129">The Rover Enclosure</span></span>
2.  <span data-ttu-id="f1cd2-130">연료 탱크</span><span class="sxs-lookup"><span data-stu-id="f1cd2-130">The Fuel Tank</span></span>
3.  <span data-ttu-id="f1cd2-131">에너지 셀</span><span class="sxs-lookup"><span data-stu-id="f1cd2-131">The Energy Cell</span></span>
4.  <span data-ttu-id="f1cd2-132">도킹 포털</span><span class="sxs-lookup"><span data-stu-id="f1cd2-132">The Docking Portal</span></span> 
5.  <span data-ttu-id="f1cd2-133">외부 센서</span><span class="sxs-lookup"><span data-stu-id="f1cd2-133">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="f1cd2-135">참고: 기본 장면에 표시되는 게임 개체 이름은 장면의 개체 이름과 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-135">Note: The game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="f1cd2-136">2단계: 오디오 소스를 달탐사선에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-136">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="f1cd2-137">기본 장면 계층 구조에서 달탐사선을 선택하고 "구성 요소 추가"를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-137">Make sure the lunar module is selected in your base scene hierarchy and click "Add Component."</span></span> <span data-ttu-id="f1cd2-138">"Audio Source"를 검색하고 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-138">Search for "Audio Source" and add it to the object.</span></span> <span data-ttu-id="f1cd2-139">지금은 비워둡니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-139">Leave it blank for now.</span></span> <span data-ttu-id="f1cd2-140">나중에 발사음을 재생하는 데 사용할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-140">We will use this to play the launching sound later.</span></span>
 <span data-ttu-id="f1cd2-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) 3단계: "배치 힌트 설정/해제" 스크립트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-141">![Lesson6 Chapter1 Step2im](images/Lesson6_Chapter1_step2im.PNG) Step 3: Add the script "toggle placement hints."</span></span> <span data-ttu-id="f1cd2-142">"구성 요소 추가"를 클릭하고 "배치 힌트 설정/해제"를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-142">Click "Add Component" and search for "Toggle Placement Hints."</span></span> <span data-ttu-id="f1cd2-143">이것은 앞에서 언급한 반투명 힌트(x-ray 재료가 있는 개체)를 활성화 및 비활성화할 수 있는 사용자 지정 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-143">This is a custom script that allows you to turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span> 
<span data-ttu-id="f1cd2-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) 4단계: 5개의 개체가 있으므로 게임 개체 배열 크기에 "5"를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-144">![Lesson6 Chapter1 Step3im](images/Lesson6_Chapter1_step3im.PNG) Step 4: Since we have 5 objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="f1cd2-145">그러면 5개의 새 요소가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-145">Then you should see 5 new elements appear.</span></span> 

![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="f1cd2-147">각각의 반투명 개체를 이름이 “없음(게임 개체)”인 상자로 끌어갑니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-147">Drag each of the translucent objects into the boxes that say "None (Game Object)."</span></span> <span data-ttu-id="f1cd2-148">기본 장면에서 달탐사선으로부터 다음 개체를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-148">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="f1cd2-149">•   Backpack</span><span class="sxs-lookup"><span data-stu-id="f1cd2-149">•   Backpack</span></span>

<span data-ttu-id="f1cd2-150">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="f1cd2-150">•   GasTank</span></span>

<span data-ttu-id="f1cd2-151">•   Topleftbody</span><span class="sxs-lookup"><span data-stu-id="f1cd2-151">•   Topleftbody</span></span>

<span data-ttu-id="f1cd2-152">•   Nose</span><span class="sxs-lookup"><span data-stu-id="f1cd2-152">•   Nose</span></span>

<span data-ttu-id="f1cd2-153">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="f1cd2-153">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="f1cd2-155">이제 "배치 힌트 설정/해제" 스크립트가 구성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-155">Now the "toggle placement hints" script is configured.</span></span> <span data-ttu-id="f1cd2-156">이렇게 하면 힌트를 활성화하거나 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-156">This will allow us to turn the hints on and off.</span></span>

<span data-ttu-id="f1cd2-157">5단계: "달탐사선 발사" 스크립트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-157">Step 5: Add the "launch lunar module" script.</span></span> <span data-ttu-id="f1cd2-158">"구성 요소 추가" 단추를 클릭하고 “달탐사선 발사”를 검색하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-158">Click the "Add Component" button, search for "launch lunar module" and select it.</span></span> <span data-ttu-id="f1cd2-159">이 스크립트는 달탐사선 발사를 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-159">This script will be responsible for launching the lunar module.</span></span> <span data-ttu-id="f1cd2-160">구성된 단추를 누르면 달탐사선의 강체 구성 요소에 상승력을 더하여 탐사선이 위쪽으로 발사되게 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-160">When we press a configured button, it will add an upward force to the lunar module's rigid body component and will cause the module to launch upwards.</span></span> <span data-ttu-id="f1cd2-161">실내에 있다면 달탐사선이 천장 메시에 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-161">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="f1cd2-162">그러나 실외라면 우주로 무한 비행합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-162">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="f1cd2-164">6단계: 추진력을 조정하여 달탐사선이 정상적으로 비행할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-164">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="f1cd2-165">값 0.01을 시도해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-165">Try a value of 0.01.</span></span> <span data-ttu-id="f1cd2-166">"Rb" 필드는 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-166">Leave the "Rb" field blank.</span></span> <span data-ttu-id="f1cd2-167">Rb는 Rigid Body(강체)를 뜻하며 이 필드는 런타임 중에 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-167">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="f1cd2-169">달탐사선 부분 개요</span><span class="sxs-lookup"><span data-stu-id="f1cd2-169">Lunar Module Parts Overview</span></span>
<span data-ttu-id="f1cd2-170">달탐사선 부분 부모 개체는 사용자가 상호 작용하는 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-170">The Lunar Module parts parent object is the collection of the objects that the user will interact with.</span></span> <span data-ttu-id="f1cd2-171">게임 개체 이름(괄호 안의 이름으로 장면 레이블 붙임)은 아래 목록에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-171">The game object names (with scene labeled names in paretheses) are provided in the list below:</span></span>

- <span data-ttu-id="f1cd2-172">Backpack(연료 탱크)</span><span class="sxs-lookup"><span data-stu-id="f1cd2-172">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="f1cd2-173">GasTank(에너지 셀)</span><span class="sxs-lookup"><span data-stu-id="f1cd2-173">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="f1cd2-174">TopLeftBody(탐사선 인클로저)</span><span class="sxs-lookup"><span data-stu-id="f1cd2-174">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="f1cd2-175">Nose(도킹 포트)</span><span class="sxs-lookup"><span data-stu-id="f1cd2-175">Nose (Docking Portal)</span></span>
- <span data-ttu-id="f1cd2-176">LeftTwirler(외부 센서)</span><span class="sxs-lookup"><span data-stu-id="f1cd2-176">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="f1cd2-177">4단원에서 논의한 것처럼 각각의 개체에는 조작 처리기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-177">Notice that each of these objects has the manipulation handler, as discussed in lesson 4.</span></span> <span data-ttu-id="f1cd2-178">조작 처리기를 사용하여 사용자가 개체를 잡고 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-178">With the manipulation handler, users are able to grab and manipulate the object.</span></span> <span data-ttu-id="f1cd2-179">또한 “two handed manipulation type(양손 조작 설정)”이 “move and rotate(이동 및 회전)”로 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-179">Also note that the setting "two handed manipulation type" is set to "move and rotate."</span></span> <span data-ttu-id="f1cd2-180">즉 사용자는 개체를 이동할 수만 있고 크기를 변경할 수는 없습니다. 어셈블리 애플리케이션에서 필요한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-180">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="f1cd2-181">또한 모듈 부분의 직접 상호 작용만 허용하기 위해 먼 조작을 선택하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-181">In addition, far manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="f1cd2-183">파트 어셈블리 데모 스크립트(위에 표시)는 사용자가 달탐사선에 개체를 배치하는 것을 관리하는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-183">The part assembly demo script (shown above) is the scrip that manages the objects to be placed on to the lunar module by the user.</span></span> 

<span data-ttu-id="f1cd2-184">"Object To Place" 필드는 연결될 수 있는 개체와 함께 선택된 변환입니다(위의 이미지의 경우 백팩/연료 탱크).</span><span class="sxs-lookup"><span data-stu-id="f1cd2-184">The "Object To Place" field is the transform that is selected (n the case of the image above, the backpack/fuel tank) with the object that it can connect to.</span></span> 

<span data-ttu-id="f1cd2-185">"Near Distance" 및 "Far Distance" 설정은 부품이 제 위치에 고정되거나 위치에서 분리되는 근접도를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-185">The "Near Distance" and "Far Distance" settings are responsible for determining the proximity to which parts will snap in place or be released.</span></span> <span data-ttu-id="f1cd2-186">예를 들어, 백팩/연료 탱크가 위치에 고정되려면 달탐사선에서 0.1단위 떨어져 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-186">For example, the backpack/fuel tank would need to be 0.1 units away from the lunar module to snap into place.</span></span> <span data-ttu-id="f1cd2-187">"Far Distance"는 개체가 달탐사선에서 떨어져야 하는 위치를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-187">The "Far Distance" sets the location where the object needs to be to detach from the lunar module.</span></span> <span data-ttu-id="f1cd2-188">이 경우 사용자의 손이 백팩/연료 탱크를 쥐고 달탐사선에서 0.2단위 떨어지게 끌어 위치에서 분리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-188">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="f1cd2-189">"Tool Tip Object"는 장면의 도구 설명 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-189">The "Tool Tip Object" is the tool tip label in the scene.</span></span> <span data-ttu-id="f1cd2-190">개체가 위치에 잠기면 레이블이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-190">When the objects are snapped in place, the label will be disabled.</span></span> 

<span data-ttu-id="f1cd2-191">오디오 소스는 자동으로 잡힙니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-191">The Audio Source will be automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="f1cd2-192">배치 힌트 단추</span><span class="sxs-lookup"><span data-stu-id="f1cd2-192">Placement Hints Buttons</span></span>
<span data-ttu-id="f1cd2-193">[2단원](mrlearning-base-ch2.md)에서는 항목 색상 변경이나 눌렀을 때 사운드를 재생하는 등의 작업을 수행하는 단추를 배치 및 구성하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-193">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="f1cd2-194">이제 이 원칙을 사용하여 배치 힌트를 설정/해제하는 단추를 구성해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-194">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="f1cd2-195">사용자가 배치 힌트 단추를 누를 때마다 반투명 배치 힌트의 표시를 설정/해제하는 단추를 구성하려 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-195">The goal is to configure our button so that every time the user presses the placement hint button, it will toggle visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="f1cd2-196">1단계: 기본 장면 계층 구조에서 배치 힌트 개체를 선택한 상태에서 달탐사선을 검사기 창의 빈 “runtime only” 슬롯으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-196">Step 1: Move the Lunar Module to the empty "runtime only" slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="f1cd2-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 2단계: 이제 드롭다운 목록의 "no function" 부분을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-197">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the dropdown list where it says, "no function."</span></span> <span data-ttu-id="f1cd2-198">"TogglePlacementHints"까지 아래로 이동하고 이 메뉴에서 "ToggleGameObjects ()"를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-198">Go down to "TogglePlacementHints," and under that menu select "ToggleGameObjects ()."</span></span> <span data-ttu-id="f1cd2-199">ToggleGameObjects()는 배치 힌트를 설정/해제하여 단추를 누를 때마다 힌트가 표시되거나 표시되지 않게 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-199">ToggleGameObjects() will toggle the placement hints on and off so that they are visible or invisible every time the button is pressed.</span></span>
 <span data-ttu-id="f1cd2-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="f1cd2-200">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="f1cd2-201">다시 설정 단추 구성</span><span class="sxs-lookup"><span data-stu-id="f1cd2-201">Configuring the Reset Button</span></span>

<span data-ttu-id="f1cd2-202">사용자가 실수하거나, 우발적으로 개체를 버리거나, 단순히 작업을 중단하고 쉬고 싶은 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-202">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to rest the experience.</span></span> <span data-ttu-id="f1cd2-203">다시 설정 단추는 환경을 다시 시작하는 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-203">The reset button will add the ability to restart the experience.</span></span> 

<span data-ttu-id="f1cd2-204">1단계: 다시 설정 단추를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-204">Step 1: Select the reset button.</span></span> <span data-ttu-id="f1cd2-205">기본 장면에서 이름이 "ResetRoundButton"입니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-205">In the base scene, it’s named "ResetRoundButton."</span></span> 

<span data-ttu-id="f1cd2-206">2단계: 기본 장면 계층 구조에서 달탐사선을 검사기 창의 "button pressed" 아래 빈 슬롯으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-206">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under "button pressed" the inspector panel.</span></span>
 <span data-ttu-id="f1cd2-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="f1cd2-207">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="f1cd2-208">3단계: "no function"이라 적힌 드롭다운 메뉴를 선택하고 "LaunchLunarModule" 위에 커서를 올립니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-208">Step 3: Select the dropdown menu that says, "no function" and hover over "LaunchLunarModule."</span></span> <span data-ttu-id="f1cd2-209">이제 "resetModule ()"을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-209">Now select "resetModule ()."</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="f1cd2-211">참고: 기본적으로 "GameObject.BroadcastMessage"가 "ResetPlacement"로 구성되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-211">Note: You will notice that by default the "GameObject.BroadcastMessage" is configured to "ResetPlacement."</span></span> <span data-ttu-id="f1cd2-212">이것은 RocketLauncher_Tutorial의 모든 자식 개체에 대해 "ResetPlacement" 메시지를 브로드캐스트합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-212">This will broadcast a message called "ResetPlacement" for every child object of RocketLauncher_Tutorial.</span></span> <span data-ttu-id="f1cd2-213">"ResetPlacement()"에 대한 메서드를 갖는 모든 개체는 그 위치를 다시 설정하는 것으로 메시지에 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-213">Any object that has a method for "ResetPlacement()" will respond to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="f1cd2-214">달탐사선 발사</span><span class="sxs-lookup"><span data-stu-id="f1cd2-214">Launching the Lunar Module</span></span>
<span data-ttu-id="f1cd2-215">이 챕터에서는 발사 단추를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-215">This chapter we will be configuring the launch button.</span></span> <span data-ttu-id="f1cd2-216">이를 통해 사용자가 이 단추를 눌러 달탐사선을 우주로 발사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-216">This will permit the user to press the button and launch the Lunar Module into space.</span></span>

<span data-ttu-id="f1cd2-217">1단계: 발사 단추를 선택합니다(기본 장면에서 이름이 "LaunchRoundButton"임).</span><span class="sxs-lookup"><span data-stu-id="f1cd2-217">Step 1: Select the launch button (in the base scene it’s named "LaunchRoundButton").</span></span> <span data-ttu-id="f1cd2-218">달탐사선을 검사기 창의 "Touch End" 아래 빈 슬롯으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-218">Drag the Lunar Module to the empty slot under "Touch End" in the inspector panel.</span></span>
 <span data-ttu-id="f1cd2-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 2단계: "no function"이라는 드롭다운 메뉴를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-219">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the dropdown menu that says, "no function."</span></span> <span data-ttu-id="f1cd2-220">"LaunchLunarModule" 위에 커서를 올리고 "StopThruster ()"를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-220">Hover over "LaunchLunarModule" and select "StopThruster ()."</span></span> <span data-ttu-id="f1cd2-221">이것은 사용자가 달탐사선에 부여할 추진력 크기를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-221">This will control how much thrust the user wants to give to the Lunar Module.</span></span> 
 <span data-ttu-id="f1cd2-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) 3단계: "ButtonPressed()"에서 달탐사선을 빈 슬롯에 추가합니다(클릭하고 누른 상태에서 끌기).</span><span class="sxs-lookup"><span data-stu-id="f1cd2-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG) Step 3: Under "ButtonPressed()", add the Lunar Module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="f1cd2-223">4단계: "no function"이라 적힌 드롭다운 메뉴를 클릭하고 "LaunchLunarModule" 위에 커서를 올린 다음, "StartThruster ()"를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-223">Step 4: Click the dropdown menu that says, "no function" and hover over "LaunchLunarModule" and select "StartThruster ()."</span></span> 
 <span data-ttu-id="f1cd2-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) 5단계: 로켓이 발사되면 음악이 재생되도록 음악을 달탐사선에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-224">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG) Step 5: Add music to the Lunar Module so that when the rocket takes off, the music will play.</span></span> <span data-ttu-id="f1cd2-225">이를 위해 달탐사선을 "Button Pressed()" 아래 다음 빈 슬롯으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-225">To do this, drag the Lunar Module to the next empty slot under "Button Pressed()".</span></span>

<span data-ttu-id="f1cd2-226">6단계: "no function"이라는 드롭다운 메뉴를 선택하고 "AudioSource"에 커서를 놓은 다음, “PlayOneShot (AudioClip)”을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-226">Step 6: Select the dropdown menu that says, "no function" and hover over "AudioSource" and select "PlayOneShot (AudioClip)."</span></span> <span data-ttu-id="f1cd2-227">MRTK에 포함된 여러 사운드를 원하는 대로 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-227">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="f1cd2-228">이 예제에서는 “MRTK_Gem”을 사용하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-228">For this example, we are going to stick with "MRTK_Gem."</span></span>
 <span data-ttu-id="f1cd2-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="f1cd2-229">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="f1cd2-230">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-230">Congratulations</span></span> 
<span data-ttu-id="f1cd2-231">이 애플리케이션의 구성을 마쳤습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-231">You have fully configured this application!</span></span> <span data-ttu-id="f1cd2-232">이제 재생을 누르면 달탐사선을 완전히 조립하고, 힌트를 설정/해제하며, 달탐사선을 발사하고, 다시 설정하여 처음부터 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1cd2-232">Now when you press play, you can fully assemble the Lunar Module, toggle hints, launch the Lunar Module, and reset it to do it all over again.</span></span>
