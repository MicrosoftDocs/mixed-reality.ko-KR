---
title: 자습서 시작-7. 음력 모듈 샘플 응용 프로그램 만들기
description: 이 단원에서는 이전 단원에서 배운 여러 개념을 결합 하 여 고유한 샘플 환경을 만듭니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 3a557be91bee9b98e750ae1546ea1c4b3103298e
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555282"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="1ae19-105">7. 음력 모듈 샘플 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="1ae19-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="1ae19-106">이 자습서에서는 다양 한 개념을 이전 단원에서 결합 하 여 고유한 샘플 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="1ae19-107">사용자가 추적 된 손을 사용 하 여 파트를 선택 하 고 음력 모듈을 조합 하 여 구성 해야 하는 파트 어셈블리 응용 프로그램을 만드는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="1ae19-108">Pressable 단추를 사용 하 여 배치 힌트를 설정/해제 하 고, 환경을 다시 설정 하 고, 음력 모듈을 공간으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="1ae19-109">이후 자습서에서는 공간 맞춤을 위해 Azure 공간 앵커를 활용 하는 강력한 다중 사용자 사용 사례를 포함 하 여이 환경을 계속 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="1ae19-110">목표</span><span class="sxs-lookup"><span data-stu-id="1ae19-110">Objectives</span></span>

* <span data-ttu-id="1ae19-111">이전 단원의 여러 개념을 결합하여 고유한 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="1ae19-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="1ae19-112">개체를 설정/해제하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="1ae19-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="1ae19-113">누를 수 있는 단추를 사용하여 복합 이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="1ae19-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="1ae19-114">강체 물리학 및 힘 사용</span><span class="sxs-lookup"><span data-stu-id="1ae19-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="1ae19-115">도구 설명 사용 살펴보기</span><span class="sxs-lookup"><span data-stu-id="1ae19-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="1ae19-116">음력 모듈 부분 개요</span><span class="sxs-lookup"><span data-stu-id="1ae19-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="1ae19-117">이 섹션에서는 간단한 파트 어셈블리 챌린지를 만듭니다. 여기서 사용자의 목표는 테이블에 분산 된 5 개의 파트를 음력 모듈의 올바른 위치에 배치 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="1ae19-118">이를 위해 수행 하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="1ae19-119">장면에 로켓 시작 관리자 prefab 추가</span><span class="sxs-lookup"><span data-stu-id="1ae19-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="1ae19-120">모든 파트에 대 한 개체 조작 사용</span><span class="sxs-lookup"><span data-stu-id="1ae19-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="1ae19-121">파트 어셈블리 데모 (스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="1ae19-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="1ae19-122">파트 어셈블리 데모 (스크립트) 구성 요소는 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="1ae19-123">이 자습서의 자산과 함께 제공 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="1ae19-124">1. prefab에 로켓 시작 관리자를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="1ae19-125">프로젝트 창에서 **자산** > \*\*mrtk로 이동 합니다. 자습서. Get > \*\* **Prefabs** 가 시작 > **RocketLauncher** 폴더에서 **RocketLauncher** prefab를 계층 창으로 끌어 장면에 추가 하 고 적절 한 위치에 배치 합니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="1ae19-126">X = 1.5, Y =-0.4, Z = 0 위치를 변환 합니다. 그러면 waist height에서 사용자의 오른쪽에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="1ae19-127">변환 회전 X = 0, Y = 180, Z = 0. 따라서 환경의 주요 기능은 사용자에 게 직면 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="1ae19-129">2. 모든 파트에 대 한 개체 조작 사용</span><span class="sxs-lookup"><span data-stu-id="1ae19-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="1ae19-130">계층 구조 창에서 RocketLauncher > **LunarModuleParts** 개체를 찾고 모든 **자식 개체**를 선택한 다음 **조작 처리기 (스크립트)** 구성 요소 및 **Near 인터랙션 Grabbable (스크립트)** 구성 요소를 추가 하 고 조작 처리기 (스크립트)를 다음과 같이 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="1ae19-131">거의 **조작** 가능 확인란의 선택을 취소 하 여 거의 상호 작용이 가능 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-131">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="1ae19-132">크기 조정 기능을 사용 하지 않도록 **회전을 이동** 하도록 **두 손 조작 유형을** 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-132">Change **Two Handed Manipulation Type** to **Move Rotate** so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="1ae19-134">개체 조작을 구현 하는 방법에 대 한 단계별 지침이 포함 된 미리 알림은 [3D 개체 조작](mrlearning-base-ch4.md#manipulating-3d-objects) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="1ae19-135">3. 파트 어셈블리 데모 (스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="1ae19-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="1ae19-136">LunarModuleParts 자식 개체가 모두 선택 된 상태에서 **오디오 원본** 구성 요소를 추가 하 고 다음과 같이 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="1ae19-137">오디오 **클립** 필드에 적합 한 오디오 클립을 할당 합니다 (예: MRKT_Scale_Start</span><span class="sxs-lookup"><span data-stu-id="1ae19-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="1ae19-138">**재생이 재생** 되 면 재생 확인란을 선택 취소 하 여 장면이 로드 될 때 오디오 클립을 자동으로 재생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="1ae19-139">공간 **Blend** 를 1로 변경 하 여 공간 오디오 사용</span><span class="sxs-lookup"><span data-stu-id="1ae19-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="1ae19-141">LunarModuleParts 자식 개체가 모두 선택 된 상태에서 **파트 어셈블리 데모 (스크립트)** 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="1ae19-143">계층 창에서 **Roverenclosure** 개체를 선택 하 고 다음과 같이 **파트 어셈블리 데모 (스크립트)** 구성 요소를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="1ae19-144">개체를 **놓을 개체** 에 대해 개체 **자체**(이 경우 roverenclosure 개체)를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-144">To the **Object To Place** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>
* <span data-ttu-id="1ae19-145">**배치 위치** 필드에 해당 **PlacementHints** 개체를 할당 합니다 .이 경우에는 RoverEnclosure_PlacementHint 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-145">To the **Location To Place** field, assign the corresponding **PlacementHints** object, in this case, the RoverEnclosure_PlacementHint object</span></span>
* <span data-ttu-id="1ae19-146">도구 설명 **개체** 필드에 해당 하는 **도구 설명**(이 경우에는 RoverEnclosure_ToolTip 개체)을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-146">To the **Tool Tip Object** field, assign the corresponding **ToolTip**, in this case, the RoverEnclosure_ToolTip object</span></span>
* <span data-ttu-id="1ae19-147">**오디오 원본** 필드에 개체 **자체**(이 경우 roverenclosure 개체)를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-147">To the **Audio Source** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="1ae19-149">FuelTank, EnergyCell, DockingPortal 및 ExternalSensor와 같은 다른 LunarModuleParts 자식 개체 각각에 대해 **반복** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="1ae19-150">이제 게임 모드를 입력 하 고 ' 개체를 ' 위치 '에 가깝게 이동 하려면 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="1ae19-151">개체는 LunarModule 개체 아래에 위치 하 고 부모로 되어 있으므로 음력 모듈의 일부가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="1ae19-152">개체의 오디오 소스가 개체의 위치에서 할당 된 오디오 클립을 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="1ae19-153">해당 하는 도구 설명 개체는 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="1ae19-155">편집기에서 입력 시뮬레이션을 사용 하는 방법에 대 한 미리 알림은 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [편집기 내 입력 시뮬레이션을 사용](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) 하 여 장면 가이드를 테스트 하는 방법을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="1ae19-156">달탐사선 구성</span><span class="sxs-lookup"><span data-stu-id="1ae19-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="1ae19-157">이 섹션에서는 사용자가 다음을 수행할 수 있도록 로켓 시작 관리자 응용 프로그램에 추가 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="1ae19-158">음력 모듈과 상호 작용</span><span class="sxs-lookup"><span data-stu-id="1ae19-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="1ae19-159">공간으로 음력 모듈을 시작 하 고 시작 시 소리 재생</span><span class="sxs-lookup"><span data-stu-id="1ae19-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="1ae19-160">음력 모듈과 모든 부분이 원래 위치에 다시 배치 되도록 응용 프로그램을 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-160">Reset the application so the Lunar Module and all the parts are placed back to their original position</span></span>
* <span data-ttu-id="1ae19-161">파트 어셈블리 챌린지를 더 어렵게 만들기 위해 배치 힌트를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="1ae19-162">이를 위해 수행 하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="1ae19-163">개체 조작 사용</span><span class="sxs-lookup"><span data-stu-id="1ae19-163">Enable object manipulation</span></span>
2. <span data-ttu-id="1ae19-164">물리 사용</span><span class="sxs-lookup"><span data-stu-id="1ae19-164">Enable physics</span></span>
3. <span data-ttu-id="1ae19-165">오디오 원본 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="1ae19-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="1ae19-166">시작 음력 모듈 (스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="1ae19-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="1ae19-167">배치 힌트 (스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="1ae19-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="1ae19-168">시작 음력 모듈 (스크립트) 구성 요소와 전환 배치 힌트 (스크립트) 구성 요소는 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="1ae19-169">이 자습서의 자산과 함께 제공 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="1ae19-170">1. 개체 조작 사용</span><span class="sxs-lookup"><span data-stu-id="1ae19-170">1. Enable object manipulation</span></span>

<span data-ttu-id="1ae19-171">계층 구조 창에서 RocketLauncher > **LunarModule** 개체를 선택 하 고 **조작 처리기 (스크립트)** 구성 요소 및 **Near 인터랙션 Grabbable (스크립트)** 구성 요소를 추가한 다음 조작 처리기 (스크립트)를 다음과 같이 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="1ae19-172">거의 **조작** 가능 확인란의 선택을 취소 하 여 거의 상호 작용이 가능 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-172">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="1ae19-173">크기 조정 기능을 사용 하지 않도록 회전을 이동 하도록 **두 손 조작 유형을** 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-173">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="1ae19-175">2. 물리학 사용</span><span class="sxs-lookup"><span data-stu-id="1ae19-175">2. Enable physics</span></span>

<span data-ttu-id="1ae19-176">RocketLauncher > **LunarModule** 개체가 선택 된 상태에서 **Rigidbody** 구성 요소를 추가 하 고 다음과 같이 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-176">With the RocketLauncher > **LunarModule** object still selected, add a **Rigidbody** component and then configure it as follows:</span></span>

* <span data-ttu-id="1ae19-177">음력의 영향을 받지 않도록 **중력 사용** 확인란을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="1ae19-178">처음에는 음력 모듈이 physic의 영향을 받지 않도록 하려면 **기구학** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="1ae19-180">3. 오디오 원본 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="1ae19-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="1ae19-181">RocketLauncher > **LunarModule** 개체가 선택 된 상태에서 **오디오 원본** 구성 요소를 추가 하 고 다음과 같이 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="1ae19-182">공간 **Blend** 를 1로 변경 하 여 공간 오디오 사용</span><span class="sxs-lookup"><span data-stu-id="1ae19-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="1ae19-184">4. Launch 음력 모듈 (스크립트) 구성 요소를 추가 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="1ae19-185">RocketLauncher > **LunarModule** 개체를 선택한 상태에서 **시작 음력 모듈 (스크립트)** 구성 요소를 추가 하 고 다음과 같이 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="1ae19-186">**위한 것** 값을 변경 하 여 음력 모듈이 시작 될 때 정상적으로 실행 되도록 합니다 (예: 0.01).</span><span class="sxs-lookup"><span data-stu-id="1ae19-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="1ae19-188">5. 배치 힌트 (스크립트) 구성 요소를 추가 하 고 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="1ae19-189">RocketLauncher > **LunarModule** 개체가 선택 된 상태에서 **설정/해제 배치 힌트 (스크립트)** 구성 요소를 추가 하 고 다음과 같이 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="1ae19-190">Game 개체 배열 **크기** 속성을 5로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="1ae19-191">각 RocketLauncher > LunarModule > **PlacementHints** 개체의 **자식 개체** 를 Game 개체 배열의 **요소** 필드에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-191">Assign each of the RocketLauncher > LunarModule > **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="1ae19-193">시작 단추 구성</span><span class="sxs-lookup"><span data-stu-id="1ae19-193">Configuring the Launch button</span></span>

<span data-ttu-id="1ae19-194">계층 창에서 RocketLauncher > 단추 > **launchbutton** 개체를 선택한 다음 **Pressable 단추 (스크립트)** 구성 요소에서 새 **단추 누름 ()** 이벤트를 만들고, 이벤트를 받도록 **LunarModule** 개체를 구성 하 고, 트리거할 작업으로 **LaunchLunarModule** 를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="1ae19-196">이벤트를 구현 하는 방법에 대 한 미리 알림은 [손 추적 제스처 및 interactable 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="1ae19-197">RocketLauncher > 단추 > **launchbutton** 개체를 선택 하 고 **Pressable 단추 (스크립트)** 구성 요소에서 새 **단추 누름 ()** 이벤트를 만들고, 이벤트를 받도록 **LunarModule** 개체를 구성 하 고, 트리거할 작업으로 **PlayOneShot** 을 정의 하 고, 오디오 **클립** 필드 (예: MRTK_Gem 오디오 클립)에 적절 한 오디오 클립을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="1ae19-199">RocketLauncher > 단추 > **launchbutton** 개체를 선택한 상태에서 **Pressable 단추 (스크립트)** 구성 요소에서 새 **Touch End ()** 이벤트를 만들고, 이벤트를 받도록 **LunarModule** 개체를 구성 하 고, 트리거할 작업으로 **LaunchLunarModule** 를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch End ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="1ae19-201">이제 게임 모드를 입력 하 고 시작 단추를 누르면 오디오 클립이 재생 되 고, 두 번째 이상에 대해 시작 단추를 누르고 있는 경우 음력 모듈이 다음 공간에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="1ae19-203">다시 설정 단추 구성</span><span class="sxs-lookup"><span data-stu-id="1ae19-203">Configuring the Reset button</span></span>

<span data-ttu-id="1ae19-204">계층 창에서 RocketLauncher > 단추 > **resetbutton** 개체를 선택 하 고, **Pressable 단추 (스크립트)** 구성 요소에서 새 **단추 누름 ()** 이벤트를 만들고, 이벤트를 받도록 **LunarModule** 개체를 구성 하 고, 트리거할 작업으로 **LaunchLunarModule 모듈** 을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="1ae19-206">RocketLauncher > 단추 > **resetbutton** 개체를 선택 하 고 **Pressable 단추 (스크립트)** 구성 요소에서 새 **단추 누름 ()** 이벤트를 만들고, 이벤트를 받도록 **RocketLauncher** 개체를 구성 하 고, 트리거할 작업으로 **GameObject** 를 정의 하 고, 메시지 필드에 **resetbutton** 를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="1ae19-208">GameObject BroadcastMessage 작업은 RocketLauncher 개체에서 모든 자식 개체에 ResetPlacement 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="1ae19-209">모든 LunarModuleParts 자식 개체에 추가한 파트 어셈블리 데모 (스크립트) 구성 요소에 정의 된 ResetPlacement 함수를 포함 하는 자식 개체는 자식 개체의 배치를 다시 설정 하는 ResetPlacement 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="1ae19-210">이제 게임 모드를 입력 하 고, 일부 부분을 이동 하거나, 음력 모듈을 시작 하 고 다시 설정 단추를 누르면 파트 및/또는 음력 모듈이 원래 위치로 다시 설정 되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-210">If you now enter Game mode, move some parts and/or launch the Lunar Module, and then press the Reset button you will see the parts and/or the Lunar Module being reset to their original position:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="1ae19-212">배치 힌트 단추 구성</span><span class="sxs-lookup"><span data-stu-id="1ae19-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="1ae19-213">계층 창에서 RocketLauncher > 단추 > **Hintsbutton** 개체를 선택한 다음 **Pressable 단추 (스크립트)** 구성 요소에서 새 **단추 누름 ()** 이벤트를 만들고, 이벤트를 받도록 **LunarModule** 개체를 구성 하 고, 트리거할 동작으로 **TogglePlacementHints** 를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="1ae19-215">이제 게임 모드를 입력 하면 반투명 배치 힌트가 기본적으로 사용 하지 않도록 설정 되어 있지만 힌트 단추를 눌러 설정 및 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="1ae19-217">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-217">Congratulations</span></span>

<span data-ttu-id="1ae19-218">이 응용 프로그램을 완전히 구성 했습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-218">You have fully configured this application.</span></span> <span data-ttu-id="1ae19-219">이제 응용 프로그램을 통해 사용자는 음력 모듈을 완전히 조합 하 고, 음력 모듈을 시작 하 고, 힌트를 설정/해제 하 고, 응용 프로그램을 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ae19-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
