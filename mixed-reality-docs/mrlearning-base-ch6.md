---
title: MR 학습 기본 모듈 - 달탐사선 어셈블리 샘플 환경
description: 이 단원에서는 이전 단원에서 학습한 여러 개념을 결합하여 고유한 샘플 환경을 만듭니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 79f2d3a4a3224533761ea2e4a7e73dc3d4d5e53e
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387690"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="60ee2-104">7. 음력 모듈 샘플 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="60ee2-104">7. Creating a Lunar Module sample application</span></span>

<span data-ttu-id="60ee2-105">이 자습서에서는 이전 단원에서 설명한 여러 가지 개념을 결합 하 여 고유한 샘플 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-105">In this tutorial, we combine multiple concepts presented in the previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="60ee2-106">사용자가 추적 된 손을 사용 하 여 음력 모듈 부분을 선택 하 고 음력 모듈을 조합 하 여 수행 해야 하는 음력 모듈 어셈블리 응용 프로그램을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-106">We will create a lunar module assembly application whereby a user needs to use tracked hands to pick up lunar module parts, and attempt to assemble a lunar module.</span></span> <span data-ttu-id="60ee2-107">Pressable 단추를 사용 하 여 배치 힌트를 전환 하 고, 경험을 다시 설정 하 고, 음력 모듈을 공간으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-107">We use pressable buttons to toggle placement hints, to reset our experience, and to launch our lunar module into space!</span></span> <span data-ttu-id="60ee2-108">이후 자습서에서는 공간 맞춤을 위해 Azure 공간 앵커를 활용 하는 강력한 다중 사용자 사용 사례를 포함 하 여이 환경을 계속 빌드할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-108">In future tutorials, we will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="60ee2-109">목표</span><span class="sxs-lookup"><span data-stu-id="60ee2-109">Objectives</span></span>

- <span data-ttu-id="60ee2-110">이전 단원의 여러 개념을 결합하여 고유한 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="60ee2-110">Combine multiple concepts from previous lessons to create a unique experience</span></span>
- <span data-ttu-id="60ee2-111">개체를 설정/해제하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="60ee2-111">Learn how to toggle objects</span></span>
- <span data-ttu-id="60ee2-112">누를 수 있는 단추를 사용하여 복합 이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="60ee2-112">Trigger complex events using pressable buttons</span></span>
- <span data-ttu-id="60ee2-113">강체 물리학 및 힘 사용</span><span class="sxs-lookup"><span data-stu-id="60ee2-113">Use rigidbody physics and forces</span></span>
- <span data-ttu-id="60ee2-114">도구 설명 사용 살펴보기</span><span class="sxs-lookup"><span data-stu-id="60ee2-114">Explore the use of tool tips</span></span>

## <a name="instructions"></a><span data-ttu-id="60ee2-115">지침</span><span class="sxs-lookup"><span data-stu-id="60ee2-115">Instructions</span></span>

### <a name="configuring-the-lunar-module"></a><span data-ttu-id="60ee2-116">달탐사선 구성</span><span class="sxs-lookup"><span data-stu-id="60ee2-116">Configuring the Lunar Module</span></span>

<span data-ttu-id="60ee2-117">이 섹션에서는 샘플 환경을 만드는 데 필요한 다양 한 구성 요소를 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-117">In this section, we introduce the various components needed to create our sample experience.</span></span>

1. <span data-ttu-id="60ee2-118">기본 장면에 prefab 음력 모듈 어셈블리를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-118">Add the Lunar Module Assembly prefab to your base scene.</span></span> <span data-ttu-id="60ee2-119">이렇게 하려면 프로젝트 탭에서 로켓 Launcher_Tutorial을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-119">To do this, from the Project tab, search for Rocket Launcher_Tutorial.</span></span> 
<span data-ttu-id="60ee2-120">Prefab Prefabs에서 > > 자산의을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-120">Find the prefab in Assets->BaseModuleAssets->Prefabs.</span></span> <span data-ttu-id="60ee2-121">또한 두 개의 로켓 시작 관리자 prefabs이 표시 됩니다. 이름이 "tutorial"이 고 다른 하나는 "complete"입니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-121">You'll also see two rocket launcher prefabs; one with the name "tutorial" and the other with the name "complete".</span></span> <span data-ttu-id="60ee2-122">로켓 Launcher_Tutorial prefab를 기본 장면으로 끌고 원하는 대로 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-122">Drag the Rocket Launcher_Tutorial prefab to your base scene, and position as you wish.</span></span>
   <span data-ttu-id="60ee2-123">참고: 로켓 Launcher_Complete prefab는 참조를 위해 제공 되는 완성 된 시작 관리자입니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-123">Note: The Rocket Launcher_Complete prefab is the completed launcher, provided for reference.</span></span> 

![Lesson6 Chapter1 Step1im](images/Lesson6_Chapter1_step1im.PNG)

<span data-ttu-id="60ee2-125">계층에서 로켓 Launcher_Tutorial game 개체를 확장 하 고 음력 Module 개체를 추가로 확장 하는 경우 "x-레이" 라는 재질을 포함 하는 여러 자식 개체를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-125">If you expand the Rocket Launcher_Tutorial game object in your hierarchy, and further expand the Lunar Module object, you find several child objects that have a material called, "x-ray."</span></span> <span data-ttu-id="60ee2-126">"X-y" 재질을 사용 하면 사용자에 대 한 배치 힌트로 사용할 약간의 반투명 색을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-126">The "x-ray" material allows for a slightly translucent color that we will use as placement hints for the user.</span></span> 

<span data-ttu-id="60ee2-127">![6 단원에서는 chapter1.txt 참고 목표](images/Lesson6_Chapter1_noteaim.PNG) 는 아래 이미지에 표시 된 것 처럼 사용자가 상호 작용 하는 음력 모듈에 5 가지 부분이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-127">![Lesson6 Chapter1 Noteaim](images/Lesson6_Chapter1_noteaim.PNG) There are five parts to the lunar module that the user will interact with as shown in the image below:</span></span>

1.  <span data-ttu-id="60ee2-128">탐사선 인클로저</span><span class="sxs-lookup"><span data-stu-id="60ee2-128">The Rover Enclosure</span></span>
2.  <span data-ttu-id="60ee2-129">연료 탱크</span><span class="sxs-lookup"><span data-stu-id="60ee2-129">The Fuel Tank</span></span>
3.  <span data-ttu-id="60ee2-130">에너지 셀</span><span class="sxs-lookup"><span data-stu-id="60ee2-130">The Energy Cell</span></span>
4.  <span data-ttu-id="60ee2-131">도킹 포털</span><span class="sxs-lookup"><span data-stu-id="60ee2-131">The Docking Portal</span></span> 
5.  <span data-ttu-id="60ee2-132">외부 센서</span><span class="sxs-lookup"><span data-stu-id="60ee2-132">The External sensor</span></span>

![Lesson6 Chapter1 Notebim](images/Lesson6_Chapter1_notebim.PNG)

> <span data-ttu-id="60ee2-134">참고: 기본 장면 계층 구조에 표시 되는 게임 개체 이름이 장면의 개체 이름과 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-134">Note: The Game object names that you see in your base scene hierarchy do not correspond to the names of the objects in the scene.</span></span>

<span data-ttu-id="60ee2-135">2단계: 오디오 소스를 달탐사선에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-135">Step 2: Add an audio source to the lunar module.</span></span> <span data-ttu-id="60ee2-136">기본 장면 계층 구조에서 음력 모듈이 선택 되어 있는지 확인 하 고 구성 요소 추가를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-136">Make sure the lunar module is selected in your base scene hierarchy, and click Add Component.</span></span> <span data-ttu-id="60ee2-137">오디오 소스를 검색 하 고 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-137">Search for Audio Source, and add it to the object.</span></span> <span data-ttu-id="60ee2-138">지금은 비워둡니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-138">Leave it blank for now.</span></span> <span data-ttu-id="60ee2-139">나중에 발사음을 재생하는 데 사용할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-139">We will use this to play the launching sound later.</span></span>

 ![6 단원에서는 Chapter1.txt Step2im](images/Lesson6_Chapter1_step2im.PNG)  
<span data-ttu-id="60ee2-141">3단계: 스크립트를 추가 하 고 배치 힌트를 설정/해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-141">Step 3: Add the script, Toggle Placement Hints.</span></span> <span data-ttu-id="60ee2-142">구성 요소 추가를 클릭 하 고 배치 힌트 설정/해제를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-142">Click Add Component, and search for Toggle Placement Hints.</span></span> <span data-ttu-id="60ee2-143">이 스크립트는 앞에서 언급 한 반투명 힌트 (x-레이 재료를 사용 하는 개체)를 켜고 끌 수 있는 사용자 지정 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-143">This is a custom script that lets you turn on and off the translucent hints (objects with the x-ray material) mentioned earlier.</span></span>  
![6 단원에서는 Chapter1.txt Step3im](images/Lesson6_Chapter1_step3im.PNG)  
<span data-ttu-id="60ee2-145">4단계: 5 개의 개체가 있으므로 게임 개체 배열 크기에 대해 "5"를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-145">Step 4: Since we have five objects, type in "5" for the game object array size.</span></span> <span data-ttu-id="60ee2-146">그러면 5 개의 새 요소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-146">You'll then see five new elements appear.</span></span>  


![Lesson6 Chapter1 Step4bim](images/Lesson6_Chapter1_step4bim.PNG)

<span data-ttu-id="60ee2-148">각 투명 개체를 모든 이름 (Game 개체) 상자로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-148">Drag each of the translucent objects into all the Name (Game Obect) boxes.</span></span>
<span data-ttu-id="60ee2-149">기본 장면에서 달탐사선으로부터 다음 개체를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-149">Drag the following objects from the lunar module in your base scene:</span></span> 

<span data-ttu-id="60ee2-150">•   Backpack</span><span class="sxs-lookup"><span data-stu-id="60ee2-150">•   Backpack</span></span>

<span data-ttu-id="60ee2-151">•   GasTank</span><span class="sxs-lookup"><span data-stu-id="60ee2-151">•   GasTank</span></span>

<span data-ttu-id="60ee2-152">•   Topleftbody</span><span class="sxs-lookup"><span data-stu-id="60ee2-152">•   Topleftbody</span></span>

<span data-ttu-id="60ee2-153">•   Nose</span><span class="sxs-lookup"><span data-stu-id="60ee2-153">•   Nose</span></span>

<span data-ttu-id="60ee2-154">•   LeftTwirler</span><span class="sxs-lookup"><span data-stu-id="60ee2-154">•   LeftTwirler</span></span>

 ![Lesson6 Chapter1 Step4aim](images/Lesson6_Chapter1_step4aim.PNG)

<span data-ttu-id="60ee2-156">이제 배치 힌트 설정/해제 스크립트가 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-156">Now the Toggle Placement Hints script is configured.</span></span> <span data-ttu-id="60ee2-157">그러면 힌트를 켜고 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-157">This allow us to turn hints on and off.</span></span>

<span data-ttu-id="60ee2-158">5단계: 시작 음력 모듈 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-158">Step 5: Add the Launch Lunar Module script.</span></span> <span data-ttu-id="60ee2-159">구성 요소 추가 단추를 클릭 하 고 "시작 음력 모듈"을 검색 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-159">Click the Add Component button, search for "launch lunar module", and select it.</span></span> <span data-ttu-id="60ee2-160">이 스크립트는 음력 모듈을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-160">This script launches the lunar module.</span></span> <span data-ttu-id="60ee2-161">구성 된 단추를 누르면 음력 모듈의 고정 본문 구성 요소에 상향 force가 추가 되 고 모듈이 위쪽으로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-161">When we press a configured button, it adds an upward force to the lunar module's rigid body component, and causes the module to launch upwards.</span></span> <span data-ttu-id="60ee2-162">실내에 있다면 달탐사선이 천장 메시에 충돌할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-162">If you are indoors, the lunar module may crash against your ceiling mesh.</span></span> <span data-ttu-id="60ee2-163">그러나 실외라면 우주로 무한 비행합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-163">But if you are outdoors, it will fly in to space indefinitely.</span></span> 

![Lesson6 Chapter1 Step5im](images/Lesson6_Chapter1_step5im.PNG)

<span data-ttu-id="60ee2-165">6단계: 추진력을 조정하여 달탐사선이 정상적으로 비행할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-165">Step 6: Adjust the thrust so that the lunar module will fly up gracefully.</span></span> <span data-ttu-id="60ee2-166">값 0.01을 시도해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-166">Try a value of 0.01.</span></span> <span data-ttu-id="60ee2-167">"Rb" 필드는 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-167">Leave the "Rb" field blank.</span></span> <span data-ttu-id="60ee2-168">Rb는 Rigid Body(강체)를 뜻하며 이 필드는 런타임 중에 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-168">Rb stands for rigid body, and this field will be automatically populated during runtime.</span></span>

![Lesson6 Chapter1 Step6im](images/Lesson6_Chapter1_step6im.PNG)

### <a name="lunar-module-parts-overview"></a><span data-ttu-id="60ee2-170">음력 모듈 부분 개요</span><span class="sxs-lookup"><span data-stu-id="60ee2-170">Lunar Module Parts overview</span></span>
<span data-ttu-id="60ee2-171">음력 모듈 파트 부모 개체는 사용자가 상호 작용 하는 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-171">The Lunar Module Parts parent object is the collection of the objects that the user interacts with.</span></span> <span data-ttu-id="60ee2-172">Paretheses에 이름이 지정 된 장면이 있는 게임 개체 이름이 아래 목록에 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-172">The Game object names, with scene labeled names in paretheses, are provided in the list below:</span></span>

- <span data-ttu-id="60ee2-173">Backpack(연료 탱크)</span><span class="sxs-lookup"><span data-stu-id="60ee2-173">Backpack (Fuel Tank)</span></span>
- <span data-ttu-id="60ee2-174">GasTank(에너지 셀)</span><span class="sxs-lookup"><span data-stu-id="60ee2-174">GasTank (Energy Cell)</span></span>
- <span data-ttu-id="60ee2-175">TopLeftBody(탐사선 인클로저)</span><span class="sxs-lookup"><span data-stu-id="60ee2-175">TopLeftBody (Rover Enclosure)</span></span>
- <span data-ttu-id="60ee2-176">Nose(도킹 포트)</span><span class="sxs-lookup"><span data-stu-id="60ee2-176">Nose (Docking Portal)</span></span>
- <span data-ttu-id="60ee2-177">LeftTwirler(외부 센서)</span><span class="sxs-lookup"><span data-stu-id="60ee2-177">LeftTwirler (External Sensor)</span></span>

<span data-ttu-id="60ee2-178">이러한 각 개체에는 4 단원에 설명 된 조작 처리기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-178">Notice that each of these objects has a manipulation handler as discussed in Lesson 4.</span></span> <span data-ttu-id="60ee2-179">조작 처리기를 사용 하면 사용자가 개체를 잡아 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-179">With the manipulation handler, users can grab and manipulate the object.</span></span> <span data-ttu-id="60ee2-180">또한 두 개의 전달 조작 형식이 이동 및 회전으로 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-180">Also note that the setting, Two Handed Manipulation Type is set to Move and Rotate.</span></span> <span data-ttu-id="60ee2-181">즉 사용자는 개체를 이동할 수만 있고 크기를 변경할 수는 없습니다. 어셈블리 애플리케이션에서 필요한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-181">This only permits the user to move the object and not change its size, which is the desired functionality for an assembly application.</span></span>
<span data-ttu-id="60ee2-182">또한 모듈 파트의 직접 상호 작용에 대해서만 허용 하도록 Far 조작이 선택 취소 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-182">In addition, Far Manipulation is unchecked to allow only for direct interaction of module parts.</span></span>

![Lesson6 Chapter2im](images/Lesson6_Chapter2im.PNG)

<span data-ttu-id="60ee2-184">파트 어셈블리 데모 스크립트 (위에 표시 됨)는 사용자가 음력 모듈에 저장 하는 개체를 관리 하는 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-184">The Part Assembly Demo script (shown above) is the script that manages the objects that the user places on the lunar module by the user.</span></span> 

<span data-ttu-id="60ee2-185">필드를 놓을 개체는 위의 이미지에 표시 된 것 처럼 선택한 변환 이며, 연결 된 개체와 연결 된 백팩/연료 탱크입니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-185">The Object To Place field is the transform that is selected, as shown in the image above, the backpack/fuel tank associated with the object that it connects to.</span></span> 

<span data-ttu-id="60ee2-186">근거리 거리 및 원거리 거리 설정에 따라 부품이 제자리에 스냅 되거나 출시 될 수 있는 근접성이 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-186">The Near Distance and Far Distance settings determine the proximity to which parts snap in place or can be released.</span></span> <span data-ttu-id="60ee2-187">예를 들어 백팩/연료 탱크는 한 곳에 맞추기 전에 음력 모듈에서 0.1 단위 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-187">For example, the backpack/fuel tank needs to be 0.1 units away from the lunar module before it will snap into place.</span></span> <span data-ttu-id="60ee2-188">먼 거리 설정은 개체가 음력 모듈에서 분리 될 수 있는 위치를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-188">The Far Distance setting sets the location where the object can be before it can detach from the lunar module.</span></span> <span data-ttu-id="60ee2-189">이 경우 사용자의 손이 백팩/연료 탱크를 쥐고 달탐사선에서 0.2단위 떨어지게 끌어 위치에서 분리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-189">In this case, the user’s hand must grab the backpack/fuel tank and pull it 0.2 units away from the lunar module to remove it from snapping back into place.</span></span>

<span data-ttu-id="60ee2-190">도구 설명 개체는 장면의 도구 설명 레이블입니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-190">The Tool Tip Object is the tool tip label in the scene.</span></span> <span data-ttu-id="60ee2-191">개체를 제자리에 물릴 때 레이블은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-191">When the objects are snapped in place, the label is disabled.</span></span> 

<span data-ttu-id="60ee2-192">오디오 소스가 자동으로 grabbed 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-192">The Audio Source is automatically grabbed.</span></span> 

### <a name="placement-hints-buttons"></a><span data-ttu-id="60ee2-193">배치 힌트 단추</span><span class="sxs-lookup"><span data-stu-id="60ee2-193">Placement Hints buttons</span></span>
<span data-ttu-id="60ee2-194">[2단원](mrlearning-base-ch2.md)에서는 항목 색상 변경이나 눌렀을 때 사운드를 재생하는 등의 작업을 수행하는 단추를 배치 및 구성하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-194">In [Lesson 2](mrlearning-base-ch2.md), you learned how to place and configure buttons to do things like change the color of an item or make it play a sound when it is pushed.</span></span> <span data-ttu-id="60ee2-195">이제 이 원칙을 사용하여 배치 힌트를 설정/해제하는 단추를 구성해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-195">We will continue to use those principles as we configure our buttons for toggling placement hints.</span></span> 

<span data-ttu-id="60ee2-196">목표는 사용자가 배치 힌트 단추를 누를 때마다 투명 한 배치 힌트의 표시 유형을 전환 하도록 단추를 구성 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-196">The goal is to configure our button so that every time the user presses the Placement hint button, it toggles the visibility of the translucent placement hints.</span></span> 

<span data-ttu-id="60ee2-197">1단계: 기본 장면 계층 구조에서 배치 힌트 개체가 선택 되어 있는 동안에는 inspector 패널의 빈 런타임 전용 슬롯으로 음력 모듈을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-197">Step 1: Move the lunar module to the empty Runtime Only slot in the inspector panel while the Placement Hints object is selected in your base scene hierarchy.</span></span> 
 <span data-ttu-id="60ee2-198">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) 2단계: 이제 함수 없음 드롭다운 목록을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-198">![Lesson6 Chapter3 Step1im](images/Lesson6_Chapter3_step1im.PNG) Step 2: Now click the No Function dropdown list.</span></span> <span data-ttu-id="60ee2-199">TogglePlacementHints로 이동 하 고 해당 메뉴 아래에서 ToggleGameObjects ()를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-199">Go down to TogglePlacementHints, and under that menu select ToggleGameObjects ().</span></span> <span data-ttu-id="60ee2-200">ToggleGameObjects ()는 단추를 누를 때마다 표시 되거나 표시 되지 않도록 배치 힌트를 설정 및 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-200">ToggleGameObjects() toggles the placement hints on and off so that they are visible or invisible each time the button is pressed.</span></span>  
 <span data-ttu-id="60ee2-201">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="60ee2-201">![Lesson6 Chapter3 Step2im](images/Lesson6_Chapter3_step2im.PNG)</span></span>

### <a name="configuring-the-reset-button"></a><span data-ttu-id="60ee2-202">다시 설정 단추 구성</span><span class="sxs-lookup"><span data-stu-id="60ee2-202">Configuring the Reset button</span></span>

<span data-ttu-id="60ee2-203">사용자가 실수로 또는 실수로 개체를 throw 하거나 환경을 다시 설정 하려는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-203">There will be situations where the user makes a mistake, or accidently throws the object away, or just wants to reset the experience.</span></span> <span data-ttu-id="60ee2-204">다시 설정 단추는 환경을 다시 시작 하는 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-204">The Reset button adds the ability to restart the experience.</span></span> 

<span data-ttu-id="60ee2-205">1단계: 다시 설정 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-205">Step 1: Select the Reset button.</span></span> <span data-ttu-id="60ee2-206">기본 장면에는 이름이 ResetRoundButton입니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-206">In the base scene, it’s named, ResetRoundButton.</span></span> 

<span data-ttu-id="60ee2-207">2단계: 기본 장면 계층 구조에서 클릭 하 여 기본 장면 계층에서 빈 슬롯으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-207">Step 2: Drag the lunar module from the base scene hierarchy into the empty slot under Button Pressed the inspector panel.</span></span>
 <span data-ttu-id="60ee2-208">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="60ee2-208">![Lesson6 Chapter4 Step2im](images/Lesson6_Chapter4_step2im.PNG)</span></span>

<span data-ttu-id="60ee2-209">3단계: 함수 없음 드롭다운 메뉴를 선택 하 고 LaunchLunarModule를 마우스로 가리킨 다음 resetModule ()을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-209">Step 3: Select the No Function dropdown menu, and hover over LaunchLunarModule,  select resetModule ().</span></span>

![Lesson6 Chapter4 Step3im](images/Lesson6_Chapter4_step3im.PNG)

> <span data-ttu-id="60ee2-211">참고: 기본적으로 GameObject BroadcastMessage는 배치를 ResetPlacement 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-211">Note: Notice that by default, the GameObject.BroadcastMessage is configured to ResetPlacement.</span></span> <span data-ttu-id="60ee2-212">그러면 RocketLauncher_Tutorial의 모든 자식 개체에 대해 ResetPlacement 라는 메시지가 브로드캐스트합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-212">This broadcasts a message called, ResetPlacement for every child object of the RocketLauncher_Tutorial.</span></span> <span data-ttu-id="60ee2-213">ResetPlacement ()에 대 한 메서드가 있는 개체는 위치를 다시 설정 하 여 해당 메시지에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-213">Any object that has a method for ResetPlacement() responds to that message by resetting it's position.</span></span> 

### <a name="launching-the-lunar-module"></a><span data-ttu-id="60ee2-214">음력 모듈 시작</span><span class="sxs-lookup"><span data-stu-id="60ee2-214">Launching the lunar module</span></span>
<span data-ttu-id="60ee2-215">이 섹션에서는 시작 단추를 구성 하는 방법을 explaings.</span><span class="sxs-lookup"><span data-stu-id="60ee2-215">This section explaings how to configure the Launch button.</span></span> <span data-ttu-id="60ee2-216">이렇게 하면 사용자가 단추를 누르고 음력 모듈을 공간으로 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-216">This permits the user to press the button and launch the lunar module into space.</span></span>

<span data-ttu-id="60ee2-217">1단계: 시작 단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-217">Step 1: Select the Launch button.</span></span> <span data-ttu-id="60ee2-218">기본 장면에서 LaunchRoundButton가 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-218">In the base scene it’s called, LaunchRoundButton.</span></span> <span data-ttu-id="60ee2-219">Inspector 패널의 Touch End 아래에 있는 빈 슬롯으로 음력 모듈을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-219">Drag the lunar module to the empty slot under Touch End in the Inspector panel.</span></span>
 <span data-ttu-id="60ee2-220">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) 2단계: 함수 없음 드롭다운 메뉴를 선택 하 고 LaunchLunarModule를 마우스로 가리킨 다음 StopThruster ()를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-220">![Lesson6 Chapter5 Step1im](images/Lesson6_Chapter5_step1im.PNG) Step 2: Select the No Function dropdown menu, and hover over LaunchLunarModule, and select StopThruster ().</span></span> <span data-ttu-id="60ee2-221">이는 사용자가 음력 모듈에 제공할 위한 것 크기를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-221">This controls how much thrust the user wants to give to the lunar module.</span></span> 
 <span data-ttu-id="60ee2-222">![6 단원에서는 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span><span class="sxs-lookup"><span data-stu-id="60ee2-222">![Lesson6 Chapter5 Step2im](images/Lesson6_Chapter5_step2im.PNG)</span></span>  
<span data-ttu-id="60ee2-223">3단계: ButtonPressed () 아래에서 음력 모듈 (클릭, 길게 및 끌기)을 빈 슬롯에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-223">Step 3: Under ButtonPressed(), add the lunar module (click, hold, and drag) to the empty slot.</span></span> 

<span data-ttu-id="60ee2-224">4단계: 함수 없음 드롭다운 메뉴를 클릭 하 고 LaunchLunarModule를 마우스로 가리킨 다음 StartThruster ()를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-224">Step 4: Click the No function dropdown menu, and hover over LaunchLunarModule, and select StartThruster ().</span></span> 
 <span data-ttu-id="60ee2-225">![6 단원에서는 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span><span class="sxs-lookup"><span data-stu-id="60ee2-225">![Lesson6 Chapter5 Step4im](images/Lesson6_Chapter5_step4im.PNG)</span></span>  
<span data-ttu-id="60ee2-226">5단계: 로켓이 꺼진 경우 음악이 재생 되도록 음력 모듈에 음악을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-226">Step 5: Add music to the lunar module so that music plays when the rocket takes off.</span></span> <span data-ttu-id="60ee2-227">이렇게 하려면 음력 모듈을 단추 누름 () 아래의 빈 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-227">To do this, drag the lunar module to the next empty slot under Button Pressed().</span></span>

<span data-ttu-id="60ee2-228">6단계: 함수 없음 드롭다운 메뉴를 선택 하 고 오디오 소스를 마우스로 가리킨 다음 PlayOneShot (오디오 클립)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-228">Step 6: Select the No Function dropdown menu, hover over AudioSource, and select PlayOneShot (AudioClip).</span></span> <span data-ttu-id="60ee2-229">MRTK에 포함된 여러 사운드를 원하는 대로 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-229">Feel free to explore the variety of sounds included with the MRTK.</span></span> <span data-ttu-id="60ee2-230">이 예에서는 "MRTK_Gem"를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-230">For this example, we'll use "MRTK_Gem."</span></span>
 <span data-ttu-id="60ee2-231">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span><span class="sxs-lookup"><span data-stu-id="60ee2-231">![Lesson6 Chapter5 Step6im](images/Lesson6_Chapter5_step6im.PNG)</span></span>


### <a name="congratulations"></a><span data-ttu-id="60ee2-232">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-232">Congratulations</span></span> 
<span data-ttu-id="60ee2-233">이 응용 프로그램을 완전히 구성 했습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-233">You have fully configured this application.</span></span> <span data-ttu-id="60ee2-234">이제 play를 누르면 음력 모듈을 완전히 조합 하 고, 힌트를 전환 하 고, 음력 모듈을 시작 하 고 다시 시작 하도록 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60ee2-234">Now, when you press play, you can fully assemble the lunar module, toggle hints, launch the lunar module, and reset it to start all over again.</span></span>
