---
title: 시작 자습서 - 7. 달착륙선 샘플 애플리케이션 만들기
description: 이 단원에서는 이전 단원에서 학습한 여러 개념을 결합하여 고유한 샘플 환경을 만듭니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "79031554"
---
# <a name="7-creating-a-lunar-module-sample-application"></a><span data-ttu-id="86fb9-105">7. 달착륙선 샘플 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="86fb9-105">7. Creating a Lunar Module sample application</span></span>
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

<span data-ttu-id="86fb9-106">이 자습서에서는 이전 단원에서 학습한 여러 개념을 결합하여 고유한 샘플 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-106">In this tutorial, multiple concepts are combined from previous lessons to create a unique sample experience.</span></span> <span data-ttu-id="86fb9-107">사용자가 추적 손을 사용하여 달착륙선 부품을 선택하고 조립을 시도하는 데 사용할 부품 어셈블리 애플리케이션을 만드는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-107">You will learn how to create a part assembly application whereby a user needs to use tracked hands to pick up parts and attempt to assemble a lunar module.</span></span> <span data-ttu-id="86fb9-108">누를 수 있는 단추를 사용하여 배치 힌트를 설정/해제하고, 환경을 다시 설정하고, 달착륙선을 우주로 발사합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-108">You will use pressable buttons to toggle placement hints on and off, to reset the experience, and to launch the lunar module into space!</span></span>

<span data-ttu-id="86fb9-109">향후 자습서에서는 공간 맞춤을 위해 Azure Spatial Anchors를 사용하는 강력한 다중 사용자 사용 사례를 포함하여 이 환경을 지속적으로 구축해 나갈 것입니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-109">In future tutorials, you will continue to build upon this experience, which includes powerful multi-user use cases that leverage Azure Spatial Anchors for spatial alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="86fb9-110">목표</span><span class="sxs-lookup"><span data-stu-id="86fb9-110">Objectives</span></span>

* <span data-ttu-id="86fb9-111">이전 단원의 여러 개념을 결합하여 고유한 환경 만들기</span><span class="sxs-lookup"><span data-stu-id="86fb9-111">Combine multiple concepts from previous lessons to create a unique experience</span></span>
* <span data-ttu-id="86fb9-112">개체를 설정/해제하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="86fb9-112">Learn how to toggle objects</span></span>
* <span data-ttu-id="86fb9-113">누를 수 있는 단추를 사용하여 복합 이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="86fb9-113">Trigger complex events using pressable buttons</span></span>
* <span data-ttu-id="86fb9-114">강체 물리학 및 힘 사용</span><span class="sxs-lookup"><span data-stu-id="86fb9-114">Use rigidbody physics and forces</span></span>
* <span data-ttu-id="86fb9-115">도구 설명 사용 살펴보기</span><span class="sxs-lookup"><span data-stu-id="86fb9-115">Explore the use of tool tips</span></span>

## <a name="lunar-module-parts-overview"></a><span data-ttu-id="86fb9-116">달착륙선 부품 개요</span><span class="sxs-lookup"><span data-stu-id="86fb9-116">Lunar Module Parts overview</span></span>
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

<span data-ttu-id="86fb9-117">이 섹션에서는 간단한 부품 어셈블리 챌린지를 만듭니다. 여기서 사용자의 목표는 테이블 위에 흩어져 있는 부품 5개를 달착륙선의 올바른 위치에 배치하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-117">In this section, you will create a simple part assembly challenge where the user's goal is to place five parts that are spread out on the table at the correct location on the Lunar Module.</span></span>

<span data-ttu-id="86fb9-118">이를 위해 수행할 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-118">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="86fb9-119">장면에 로켓 발사대 프리팹 추가</span><span class="sxs-lookup"><span data-stu-id="86fb9-119">Add the Rocket Launcher prefab to the scene</span></span>
2. <span data-ttu-id="86fb9-120">모든 부품에 개체 조작 사용</span><span class="sxs-lookup"><span data-stu-id="86fb9-120">Enable object manipulation for all the parts</span></span>
3. <span data-ttu-id="86fb9-121">부품 어셈블리 데모(스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="86fb9-121">Add and configure the Part Assembly Demo (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="86fb9-122">부품 어셈블리 데모(스크립트) 구성 요소는 MRTK에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-122">The Part Assembly Demo (Script) component is not part of MRTK.</span></span> <span data-ttu-id="86fb9-123">이 자습서의 자산과 함께 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-123">It was provided with this tutorial's assets.</span></span>

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a><span data-ttu-id="86fb9-124">1. 장면에 로켓 발사대 프리팹 추가</span><span class="sxs-lookup"><span data-stu-id="86fb9-124">1. Add the Rocket Launcher prefab to the scene</span></span>

<span data-ttu-id="86fb9-125">[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** 폴더로 이동하여 **RocketLauncher** 프리팹을 [계층 구조] 창으로 끌어 장면에 추가한 다음, 적절한 위치에 배치합니다. 예를 들어 다음 위치에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-125">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder, drag the **RocketLauncher** prefab into the Hierarchy window to add it to your scene, and then position it at a suitable location, for example:</span></span>

* <span data-ttu-id="86fb9-126">변환 위치 X = 1.5, Y =-0.4, Z = 0. 사용자의 오른쪽에 허리 높이로 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-126">Transform Position X = 1.5, Y = -0.4, Z = 0, so it is positioned to the right of the user at waist height</span></span>
* <span data-ttu-id="86fb9-127">변환 회전 X = 0, Y = 180, Z = 0. 환경의 주요 부분이 사용자를 향합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-127">Transform Rotation X = 0, Y = 180, Z = 0, so the main features of the experience faces the user</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a><span data-ttu-id="86fb9-129">2. 모든 부품에 개체 조작 사용</span><span class="sxs-lookup"><span data-stu-id="86fb9-129">2. Enable object manipulation for all the parts</span></span>

<span data-ttu-id="86fb9-130">다음과 같이 [계층 구조] 창에서 RocketLauncher > **LunarModuleParts** 개체를 찾아 모든 **하위 개체**를 선택하고, **조작 처리기(스크립트)** 구성 요소와 **근거리 잡기형 상호 작용(스크립트)** 구성 요소를 추가한 다음, 조작 처리기(스크립트)를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-130">In the Hierarchy window, locate the RocketLauncher > **LunarModuleParts** object and select all the **child objects**, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="86fb9-131">근거리 상호 작용만 허용하도록 **원거리 조작 허용** 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-131">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="86fb9-132">크기 조정을 사용하지 않도록 **양손 조작 유형**을 **이동 회전**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-132">Change **Two Handed Manipulation Type** to **Move Rotate** so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="86fb9-134">다시 말씀드리지만, 개체 조작을 구현하는 방법에 대한 단계별 지침은 [3D 개체 조작](mrlearning-base-ch4.md#manipulating-3d-objects) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86fb9-134">For a reminder, with step by step instructions, on how to implement object manipulation, you can refer to the [Manipulating 3D Objects](mrlearning-base-ch4.md#manipulating-3d-objects) instructions.</span></span>

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a><span data-ttu-id="86fb9-135">3. 부품 어셈블리 데모(스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="86fb9-135">3. Add and configure the Part Assembly Demo (Script) component</span></span>

<span data-ttu-id="86fb9-136">모든 LunarModuleParts 자식 개체를 선택한 상태에서 **오디오 원본** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-136">With all the LunarModuleParts child objects still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="86fb9-137">**오디오 클립** 필드에 적절한 오디오 클립(예: MRKT_Scale_Start)을 할당합니다</span><span class="sxs-lookup"><span data-stu-id="86fb9-137">Assign a suitable audio clip to the **AudioClip** field, for example, MRKT_Scale_Start</span></span>
* <span data-ttu-id="86fb9-138">장면이 로드될 때 오디오 클립이 자동으로 재생되지 않도록 **Play On Awake(절전 모드 해제 시 재생)** 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-138">Un-check the **Play On Awake** checkbox, so the audio clip does not automatically play when the scene loads</span></span>
* <span data-ttu-id="86fb9-139">**공간 블렌드**를 1로 변경하여 공간 오디오를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-139">Change **Spatial Blend** to 1, to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

<span data-ttu-id="86fb9-141">다음과 같이 모든 LunarModuleParts 자식 개체를 선택한 상태에서 **부품 어셈블리 데모(스크립트)** 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-141">With all the LunarModuleParts child objects still selected, add the **Part Assembly Demo  (Script)** component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

<span data-ttu-id="86fb9-143">다음과 같이 [계층 구조] 창에서 **RoverEnclosure** 개체를 선택하고 해당 **부품 어셈블리 데모(스크립트)** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-143">In the Hierarchy window, select the **RoverEnclosure** object and configure its **Part Assembly Demo (Script)** component as follows:</span></span>

* <span data-ttu-id="86fb9-144">**Object To Place(배치할 개체)** 필드에 개체 **자체**를 할당합니다. 여기서는 RoverEnclosure 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-144">To the **Object To Place** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>
* <span data-ttu-id="86fb9-145">**Location To Place(배치할 위치)** 필드에 해당하는 **PlacementHints** 개체를 할당합니다. 여기서는 RoverEnclosure_PlacementHint 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-145">To the **Location To Place** field, assign the corresponding **PlacementHints** object, in this case, the RoverEnclosure_PlacementHint object</span></span>
* <span data-ttu-id="86fb9-146">**Tool Tip Object(도구 설명 개체)** 필드에 해당하는 **도구 설명**을 할당합니다. 여기서는 RoverEnclosure_ToolTip 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-146">To the **Tool Tip Object** field, assign the corresponding **ToolTip**, in this case, the RoverEnclosure_ToolTip object</span></span>
* <span data-ttu-id="86fb9-147">**오디오 원본** 필드에 개체 **자체**를 할당합니다. 여기서는 RoverEnclosure 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-147">To the **Audio Source** field, assign the object **itself**, in this case, the RoverEnclosure object</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

<span data-ttu-id="86fb9-149">FuelTank, EnergyCell, DockingPortal, ExternalSensor 등의 다른 LunarModuleParts 자식 개체에도 같은 과정을 **반복**합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-149">**Repeat** for each of the other LunarModuleParts child objects, i.e. FuelTank, EnergyCell, DockingPortal, and ExternalSensor.</span></span>

<span data-ttu-id="86fb9-150">이제 게임 모드로 전환하여 '배치할 개체'를 해당하는 '배치할 위치'에 가깝게 이동하면 다음과 같은 현상을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-150">If you now enter Game mode and move an 'Object To Place' close to it's corresponding 'Location To Place' you will notice:</span></span>

* <span data-ttu-id="86fb9-151">개체가 제 위치에 배치되고 LunarModule 개체 아래에 부모 개체로 지정되므로 달착륙선의 부품이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-151">The object will snap into place and be parented under the LunarModule object so it becomes part of the Lunar Module</span></span>
* <span data-ttu-id="86fb9-152">개체의 오디오 원본이 개체의 위치에서 할당된 오디오 클립을 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-152">The Audio Source on the object will play the assigned Audio Clip at the location of the object</span></span>
* <span data-ttu-id="86fb9-153">해당하는 도구 설명 개체는 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-153">The corresponding Tool Tip object will be hidden</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> <span data-ttu-id="86fb9-155">편집기 내 입력 시뮬레이션을 사용하는 방법을 다시 보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [편집기 내 손 입력 시뮬레이션을 사용하여 장면 테스트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86fb9-155">For a reminder on how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="configuring-the-lunar-module"></a><span data-ttu-id="86fb9-156">달탐사선 구성</span><span class="sxs-lookup"><span data-stu-id="86fb9-156">Configuring the Lunar Module</span></span>

<span data-ttu-id="86fb9-157">이 섹션에서는 사용자가 다음을 수행할 수 있도록 로켓 발사대 애플리케이션에 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-157">In this section, you will add additional features to the Rocket Launcher application so the user can:</span></span>

* <span data-ttu-id="86fb9-158">달착륙선과 상호 작용</span><span class="sxs-lookup"><span data-stu-id="86fb9-158">Interact with the Lunar Module</span></span>
* <span data-ttu-id="86fb9-159">달착륙선을 우주로 발사하고, 발사할 때 소리 재생</span><span class="sxs-lookup"><span data-stu-id="86fb9-159">Launch the Lunar Module into space and play a sound when it is launched</span></span>
* <span data-ttu-id="86fb9-160">달착륙선과 모든 부품이 다시 원래 위치에 배치되도록 애플리케이션을 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-160">Reset the application so the Lunar Module and all the parts are placed back to their original position</span></span>
* <span data-ttu-id="86fb9-161">부품 어셈블리 챌린지의 난이도를 높이기 위해 배치 힌트를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-161">Hide the placement hints to make the part assembly challenge more difficult.</span></span>

<span data-ttu-id="86fb9-162">이를 위해 수행할 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-162">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="86fb9-163">개체 조작 사용</span><span class="sxs-lookup"><span data-stu-id="86fb9-163">Enable object manipulation</span></span>
2. <span data-ttu-id="86fb9-164">물리학 사용</span><span class="sxs-lookup"><span data-stu-id="86fb9-164">Enable physics</span></span>
3. <span data-ttu-id="86fb9-165">오디오 원본 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="86fb9-165">Add an Audio Source component</span></span>
4. <span data-ttu-id="86fb9-166">달착륙선 발사(스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="86fb9-166">Add and configure the Launch Lunar Module (Script) component</span></span>
5. <span data-ttu-id="86fb9-167">배치 힌트 설정/해제(스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="86fb9-167">Add and configure the Toggle Placement Hints (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="86fb9-168">달착륙선 발사(스크립트) 구성 요소와 배치 힌트 설정/해제(스크립트) 구성 요소는 MRTK에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-168">The Launch Lunar Module (Script) component and the Toggle Placement Hints (Script) component are not part of MRTK.</span></span> <span data-ttu-id="86fb9-169">이 자습서의 자산과 함께 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-169">They were provided with this tutorial's assets.</span></span>

### <a name="1-enable-object-manipulation"></a><span data-ttu-id="86fb9-170">1. 개체 조작 사용</span><span class="sxs-lookup"><span data-stu-id="86fb9-170">1. Enable object manipulation</span></span>

<span data-ttu-id="86fb9-171">다음과 같이 [계층 구조] 창에서 RocketLauncher > **LunarModule** 개체를 선택하고, **조작 처리기(스크립트)** 구성 요소 및 **근거리 잡기형 상호 작용(스크립트)** 구성 요소를 추가한 다음, 조작 처리기(스크립트)를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-171">In the Hierarchy window, select the RocketLauncher > **LunarModule** object, add the **Manipulation Handler (Script)** component and the **Near Interaction Grabbable (Script)** component, and then configure the Manipulation Handler (Script) as follows:</span></span>

* <span data-ttu-id="86fb9-172">근거리 상호 작용만 허용하도록 **원거리 조작 허용** 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-172">Un-check the **Allow Far Manipulation** checkbox to only allow near interaction</span></span>
* <span data-ttu-id="86fb9-173">크기 조정을 사용하지 않도록 **양손 조작 유형**을 [이동 회전]으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-173">Change **Two Handed Manipulation Type** to Move Rotate so scaling is disabled</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a><span data-ttu-id="86fb9-175">2. 물리학 사용</span><span class="sxs-lookup"><span data-stu-id="86fb9-175">2. Enable physics</span></span>

<span data-ttu-id="86fb9-176">RocketLauncher > **LunarModule** 개체를 선택한 상태에서 **Rigidbody** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-176">With the RocketLauncher > **LunarModule** object still selected, add a **Rigidbody** component and then configure it as follows:</span></span>

* <span data-ttu-id="86fb9-177">달착륙선이 중력의 영향을 받지 않도록 **중력 사용** 확인란을 선택 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-177">Un-check the **Use Gravity** checkbox so the Lunar Module is not affected by gravity</span></span>
* <span data-ttu-id="86fb9-178">달착륙선이 처음에는 물리력의 영향을 받지 않도록 **Is Kinematic(운동학 적용)** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-178">Check the **Is Kinematic** checkbox so the Lunar Module initially isn't affected by physic forces</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a><span data-ttu-id="86fb9-180">3. 오디오 원본 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="86fb9-180">3. Add an Audio Source component</span></span>

<span data-ttu-id="86fb9-181">RocketLauncher > **LunarModule** 개체를 선택한 상태에서 **오디오 원본** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-181">With the RocketLauncher > **LunarModule** object still selected, add an **Audio Source** component and then configure it as follows:</span></span>

* <span data-ttu-id="86fb9-182">**공간 블렌드**를 1로 변경하여 공간 오디오를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-182">Change **Spatial Blend** to 1 to enable spatial audio</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a><span data-ttu-id="86fb9-184">4. 달착륙선 발사(스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="86fb9-184">4. Add and configure the Launch Lunar Module (Script) component</span></span>

<span data-ttu-id="86fb9-185">RocketLauncher > **LunarModule** 개체를 선택한 상태에서 **달착륙선 발사(스크립트)** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-185">With the RocketLauncher > **LunarModule** object still selected, add the **Launch Lunar Module (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="86fb9-186">발사된 달 착륙선이 정상적으로 비행하도록 **Thrust(추진력)** 값을 변경합니다(예: 0.01로 변경).</span><span class="sxs-lookup"><span data-stu-id="86fb9-186">Change **Thrust** value so the Lunar Module will fly up gracefully when launched, for example, to 0.01</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a><span data-ttu-id="86fb9-188">5. 배치 힌트 설정/해제(스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="86fb9-188">5. Add and configure the Toggle Placement Hints (Script) component</span></span>

<span data-ttu-id="86fb9-189">RocketLauncher > **LunarModule** 개체를 선택한 상태에서 **배치 힌트 설정/해제(스크립트)** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-189">With the RocketLauncher > **LunarModule** object still selected, add the **Toggle Placement Hints (Script)** component and then configure it as follows:</span></span>

* <span data-ttu-id="86fb9-190">게임 개체 배열 **크기** 속성을 5로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-190">Set the Game Object Array **Size** property to 5</span></span>
* <span data-ttu-id="86fb9-191">다음과 같이 각 RocketLauncher > LunarModule > **PlacementHints** 개체의 **자식 개체**를 게임 개체 배열의 **요소** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-191">Assign each of the RocketLauncher > LunarModule > **PlacementHints** object's **child objects** to the an **Element** field in the Game Object Array:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a><span data-ttu-id="86fb9-193">발사 단추 구성</span><span class="sxs-lookup"><span data-stu-id="86fb9-193">Configuring the Launch button</span></span>

<span data-ttu-id="86fb9-194">다음과 같이 [계층 구조] 창에서 RocketLauncher > 단추 > **LaunchButton** 개체를 선택하고, **누를 수 있는 단추(스크립트)** 구성 요소에서 새 **Button Pressed ()** 이벤트를 만들고, 이벤트를 수신하도록 **LunarModule** 개체를 구성하고, 트리거할 동작으로 **LaunchLunarModule. StartThruster**를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-194">In the Hierarchy window, select the RocketLauncher > Buttons > **LaunchButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StartThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="86fb9-196">이벤트를 구현하는 방법에 대한 내용은 [손 추적 제스처 및 상호 작용 가능 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="86fb9-196">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

<span data-ttu-id="86fb9-197">다음과 같이 RocketLauncher > 단추 > **LaunchButton** 개체를 선택한 상태로 **누를 수 있는 단추(스크립트)** 구성 요소에서 새 **Button Pressed ()** 이벤트를 만들고, 이벤트를 수신하도록 **LunarModule** 개체를 구성하고, 트리거할 동작으로 **AudioSource.PlayOneShot**을 정의하고, **오디오 클립** 필드에 적절한 오디오 클립(예: MRTK_Gem 오디오 클립)을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-197">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

<span data-ttu-id="86fb9-199">다음과 같이 RocketLauncher > 단추 > **LaunchButton** 개체를 선택한 상태로 **누를 수 있는 단추(스크립트)** 구성 요소에서 새 **Touch End ()** 이벤트를 만들고, 이벤트를 수신하도록 **LunarModule** 개체를 구성하고, 트리거할 동작으로 **LaunchLunarModule.StopThruster**를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-199">With the RocketLauncher > Buttons > **LaunchButton** object still selected, on the **Pressable Button (Script)** component, create a new **Touch End ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.StopThruster** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

<span data-ttu-id="86fb9-201">이제 게임 모드로 전환하여 [발사] 단추를 누르면 오디오 클립이 재생되며, [발사] 단추를 1초 이상 누르고 있으면 달착륙선이 우주로 발사됩니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-201">If you now enter Game mode and press the Launch button, you will hear the audio clip play, and if you hold the Launch button down for about a second or longer, you will see the Lunar Module launch into space:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a><span data-ttu-id="86fb9-203">[초기화] 단추 구성</span><span class="sxs-lookup"><span data-stu-id="86fb9-203">Configuring the Reset button</span></span>

<span data-ttu-id="86fb9-204">다음과 같이 [계층 구조] 창에서 RocketLauncher > 단추 > **ResetButton** 개체를 선택하고, **누를 수 있는 단추(스크립트)** 구성 요소에서 새 **Button Pressed ()** 이벤트를 만들고, 이벤트를 수신하도록 **LunarModule** 개체를 구성하고, 트리거할 동작으로 **LaunchLunarModule.ResetModule**을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-204">In the Hierarchy window, select the RocketLauncher > Buttons > **ResetButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **LaunchLunarModule.ResetModule** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

<span data-ttu-id="86fb9-206">다음과 같이 RocketLauncher > 단추 > **ResetButton** 개체를 선택한 상태로 **누를 수 있는 단추(스크립트)** 구성 요소에서 새 **Button Pressed ()** 이벤트를 만들고, 이벤트를 수신하도록 **RocketLauncher** 개체를 구성하고, 트리거할 동작으로 **GameObject.BroadcastMessage**를 정의하고, 메시지 필드에 **ResetPlacement**를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-206">With the RocketLauncher > Buttons > **ResetButton** object still selected, on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **RocketLauncher** object to receive the event, define **GameObject.BroadcastMessage** as the action to be triggered, and enter **ResetPlacement** in message field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="86fb9-208">GameObject BroadcastMessage 동작은 RocketLauncher 개체의 ResetPlacement 메시지를 모든 자식 개체에게 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-208">The GameObject.BroadcastMessage action sends the ResetPlacement message from the RocketLauncher object to all its child object.</span></span> <span data-ttu-id="86fb9-209">모든 LunarModuleParts 자식 개체에 추가한 부품 어셈블리 데모(스크립트) 구성 요소에 정의된 ResetPlacement 함수를 포함하고 있는 자식 개체는 자식 개체의 배치를 초기화하는 ResetPlacement 함수를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-209">Any child object that has the ResetPlacement function, which is defined in the Part Assembly Demo (Script) component you added to all the LunarModuleParts child object, will invoke the ResetPlacement function which resets that child object's placement.</span></span>

<span data-ttu-id="86fb9-210">이제 게임 모드로 전환하여 일부 부품을 이동하고/이동하거나 [초기화] 단추를 누르면 부품 및/또는 달착륙선이 원래 위치로 초기화되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-210">If you now enter Game mode, move some parts and/or launch the Lunar Module, and then press the Reset button you will see the parts and/or the Lunar Module being reset to their original position:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a><span data-ttu-id="86fb9-212">배치 힌트 단추 구성</span><span class="sxs-lookup"><span data-stu-id="86fb9-212">Configuring the Placement Hints button</span></span>
<!-- TODO: Rename to 'Configuring the Hints button'-->

<span data-ttu-id="86fb9-213">다음과 같이 [계층 구조] 창에서 RocketLauncher > 단추 > **HintsButton** 개체를 선택하고, **누를 수 있는 단추(스크립트)** 구성 요소에서 새 **Button Pressed ()** 이벤트를 만들고, 이벤트를 수신하도록 **LunarModule** 개체를 구성하고, 트리거할 동작으로 **TogglePlacementHints.ToggleGameObjects**를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-213">In the Hierarchy window, select the RocketLauncher > Buttons > **HintsButton** object, then on the **Pressable Button (Script)** component, create a new **Button Pressed ()** event, configure the **LunarModule** object to receive the event, and define **TogglePlacementHints.ToggleGameObjects** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

<span data-ttu-id="86fb9-215">이제 게임 모드로 전환하면 반투명 배치 힌트가 기본적으로 사용되지 않습니다. 하지만 다음과 같이 [힌트] 단추를 눌러 켜고 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-215">If you now enter Game mode you will notice that the translucent placement hints are disabled by default, but that you can toggle them on and off by pressing the Hints button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="86fb9-217">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-217">Congratulations</span></span>

<span data-ttu-id="86fb9-218">이 애플리케이션의 구성을 마쳤습니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-218">You have fully configured this application.</span></span> <span data-ttu-id="86fb9-219">이제 사용자들이 이 애플리케이션을 사용하여 달착륙선을 완전히 조립하고, 달착륙선을 발사하고, 힌트를 설정/해제하고, 애플리케이션을 초기화하여 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86fb9-219">Now, your application allows users to fully assemble the Lunar Module, launch the Lunar Module, toggle hints, and reset the application to start again.</span></span>
