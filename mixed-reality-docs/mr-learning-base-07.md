---
title: 시작 자습서 - 7. 3D 개체와 상호 작용
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 8920b35d1583777b86bc82868bb90338e25298e2
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305996"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="4d38a-105">7. 3D 개체와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="4d38a-105">7. Interacting with 3D objects</span></span>

<span data-ttu-id="4d38a-106">이 자습서에서는 3D 개체의 근거리 및 원거리 조작을 사용하도록 설정하고 허용되는 조작 유형을 제한하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-106">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="4d38a-107">개체 조작을 보다 쉽게 제어할 수 있도록 3D 개체 주위에 경계 상자를 추가하는 방법도 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-107">You will also learn how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="4d38a-108">목표</span><span class="sxs-lookup"><span data-stu-id="4d38a-108">Objectives</span></span>

* <span data-ttu-id="4d38a-109">3D 개체가 상호 작용할 수 있도록 구성하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="4d38a-109">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="4d38a-110">3D 개체에 경계 상자를 추가하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="4d38a-110">Learn how to add bounding boxes to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="4d38a-111">3D 개체 조작</span><span class="sxs-lookup"><span data-stu-id="4d38a-111">Manipulating 3D objects</span></span>

<span data-ttu-id="4d38a-112">이 섹션에서는 [장면에서 개체 위치 지정](mr-learning-base-04.md) 자습서를 진행하는 동안 테이블에서 구성한 모든 Rover 파트를 조작하는 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-112">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="4d38a-113">이를 위해 수행할 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-113">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="4d38a-114">모든 파트 개체에 Object Manipulator(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="4d38a-114">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="4d38a-115">모든 파트 개체에 NearInteractionGrabbable 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="4d38a-115">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="4d38a-116">Object Manipulator(스크립트) 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="4d38a-116">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="4d38a-117">**개체를 조작**하려면 개체에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-117">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="4d38a-118">**충돌체** 구성 요소(예: 상자 충돌체)</span><span class="sxs-lookup"><span data-stu-id="4d38a-118">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="4d38a-119">**Object Manipulator(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4d38a-119">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="4d38a-120">추적 손으로 개체에 대한 **조작** 및 **잡기**를 수행하려면 개체에 다음 구성 요소가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-120">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="4d38a-121">**충돌체** 구성 요소(예: 상자 충돌체)</span><span class="sxs-lookup"><span data-stu-id="4d38a-121">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="4d38a-122">**Object Manipulator(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4d38a-122">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="4d38a-123">**NearInteractionGrabbable** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4d38a-123">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="4d38a-124">또한 Rover 파트를 Rover에 배치하여 완전한 Rover 어셈블리로 만들 수 있도록 Rover Explorer를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-124">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="4d38a-125">Hierarchy(계층 구조) 창에서 RoverExplorer > **RoverParts** 개체를 펼치고, 자식 Rover 파트 개체와 **RoverAssembly** 개체를 모두 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 다음 구성 요소를 선택한 모든 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-125">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="4d38a-126">**Object Manipulator(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4d38a-126">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="4d38a-127">**NearInteractionGrabbable** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4d38a-127">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="4d38a-128">**Part Assembly Controller(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4d38a-128">**Part Assembly Controller (Script)** component</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="4d38a-130">서로 인접하지 않은 여러 개체를 선택하려면 Ctrl 키를 누른 채 마우스를 사용하여 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-130">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="4d38a-131">이 자습서의 학습 목표를 달성하기 위해 Rover 파트에 충돌체가 이미 추가되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="4d38a-132">충돌체에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">충돌체</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d38a-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="4d38a-133">Part Assembly Controller(스크립트)는 MRTK의 일부는 아니지만 자습서 자산에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="4d38a-134">Rover 파트 개체와 RoverAssembly 개체를 선택한 상태로, Inspector(인스펙터) 창에서 **Object Manipulator(스크립트)** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="4d38a-135">**Two Handed Manipulation Type**(양손 조작 유형) 드롭다운에서 Scale(크기 조정) 선택을 취소하고 **Move**(이동) 및 **Rotate**(회전)만 가능하도록 설정</span><span class="sxs-lookup"><span data-stu-id="4d38a-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="4d38a-137">이제 모든 Rover 파트 개체와 RoverAssembly 개체에 대해 개체 조작이 가능하도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="4d38a-138">프로젝트 창에서 **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** 폴더로 이동하여 오디오 클립을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-138">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** folder to locate the audio clips:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="4d38a-140">Hierarchy(계층 구조) 창에서 **Rover 파트 개체**를 다시 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **Audio Sources**(오디오 소스) 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="4d38a-141">**MRTK_Scale_Start** 오디오 클립을 **AudioClip** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="4d38a-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="4d38a-142">**Play On Awake**(활성 상태일 때 재생) 확인란의 선택을 취소</span><span class="sxs-lookup"><span data-stu-id="4d38a-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="4d38a-143">**Spatial Blend**(공간 블렌드)를 1로 변경</span><span class="sxs-lookup"><span data-stu-id="4d38a-143">Change **Spatial Blend** to 1</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="4d38a-145">Hierarchy(계층 구조) 창에서 RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** 개체를 펼쳐서 모든 배치 힌트 개체를 표시한 다음, 첫 번째 Rover 파트 RoverParts > **Camera_Part**를 선택하고 **Part Assembly Controller(스크립트)** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="4d38a-146">**Camera_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="4d38a-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="4d38a-148">나머지 Rover 파트 개체와 RoverAssembly 개체 각각에 대해 이 단계를 **반복**하여 **Part Assembly Controller(스크립트)** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="4d38a-149">**Generator_Part**의 경우 **Generator_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="4d38a-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="4d38a-150">**Lights_Part**의 경우 **Lights_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="4d38a-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="4d38a-151">**UHFAntenna_Part**의 경우 **UHFAntenna_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="4d38a-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="4d38a-152">**Spectrometer_Part**의 경우 **Spectrometer_PlacementHint** 개체를 **Location To Place**(배치할 위치) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="4d38a-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="4d38a-153">**RoverAssembly**의 경우 개체 자체(즉, 동일한 **RoverAssembly** 개체)를 **Location To Place**(배치할 위치) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="4d38a-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="4d38a-154">Hierarchy(계층 구조) 창에서 RoverExplorer > Buttons > **Reset**(초기화) 단추 개체를 선택한 다음, Inspector(인스펙터) 창에서 상호작용 가능 **OnClick ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="4d38a-155">**RoverAssembly** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="4d38a-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="4d38a-156">**No Function**(함수 없음) 드롭다운에서 **PartAssemblyController** > **ResetPlacement ()** 를 선택하여 이 함수를 이벤트가 트리거될 때 실행할 작업으로 설정</span><span class="sxs-lookup"><span data-stu-id="4d38a-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="4d38a-158">이제 게임 모드로 전환하면 근거리 또는 원거리 상호 작용을 사용하여 Rover 파트를 Rover에 놓을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="4d38a-159">파트가 해당하는 배치 힌트에 가까워지면 위치로 맞춰져서 Rover의 일부가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="4d38a-160">배치를 다시 설정하려면 Reset(초기화) 단추를 누르면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-160">To reset the placements, you can press the Reset button:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="4d38a-162">Object Manipulator 구성 요소 및 관련 속성에 대해 자세히 알아보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d38a-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="4d38a-163">경계 상자 추가</span><span class="sxs-lookup"><span data-stu-id="4d38a-163">Adding bounding boxes</span></span>

<span data-ttu-id="4d38a-164">경계 상자를 사용하면 크기 조정 및 회전에 사용할 수 있는 핸들을 제공하여 근거리 및 원거리 상호 작용 모두에서 한 손으로 개체를 보다 쉽고 직관적으로 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-164">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="4d38a-165">이 예제에서는 전체 환경을 쉽게 이동, 회전, 확장할 수 있도록 RoverExplorer 개체에 경계 상자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-165">In this example, you will add a bounding box to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="4d38a-166">또한 경계 상자를 켜고 끌 수 있도록 메뉴를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-166">Additionally, you will configure the Menu so you can turn the Bounding Box on and off.</span></span>

<span data-ttu-id="4d38a-167">Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 다음 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="4d38a-168">**BoundingBox** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4d38a-168">**BoundingBox** component</span></span>
* <span data-ttu-id="4d38a-169">**Object Manipulator(스크립트)** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4d38a-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="4d38a-170">그런 다음, 두 구성 요소 옆에 있는 확인란을 **선택 취소**하여 기본적으로 **사용하지 않도록 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-170">Then **uncheck** the checkbox next to both components to make them **disabled** by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="4d38a-172">경계 상자 시각화는 런타임에 생성되므로 게임 모드로 전환하기 전에는 보이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-172">The Bounding Box visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
> <span data-ttu-id="4d38a-173">BoundingBox 구성 요소는 런타임에 NearInteractionGrabbable 구성 요소를 자동으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-173">The BoundingBox component will automatically add the NearInteractionGrabbable component at runtime.</span></span> <span data-ttu-id="4d38a-174">따라서 추적 손으로 감싼 개체를 잡기 위해 이 구성 요소를 추가할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-174">Therefore, we do not need to add this component to grab the enclosed objects with tracked hands.</span></span>

<span data-ttu-id="4d38a-175">Hierarchy(계층 구조) 창에서 메뉴 > **ButtonCollection** 개체를 펼쳐서 단추 4개를 표시하고 3번째 단추의 이름을 **BoundingBox_Enable**로 변경한 다음, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-175">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundingBox_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="4d38a-176">**Main Label Text**(기본 레이블 텍스트)를 **Enable**(사용)로 변경</span><span class="sxs-lookup"><span data-stu-id="4d38a-176">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="4d38a-177">**RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="4d38a-177">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="4d38a-178">**No Function**(함수 없음) 드롭다운에서 **BoundingBox** > **bool Enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="4d38a-178">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="4d38a-179">인수 확인란이 **선택**되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="4d38a-179">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="4d38a-180">작은 **+** 아이콘을 클릭하여 또 다른 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="4d38a-180">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="4d38a-181">**RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="4d38a-181">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="4d38a-182">**No Function**(함수 없음) 드롭다운에서 **ObjectManipulator** > **bool Enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="4d38a-182">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="4d38a-183">인수 확인란이 **선택**되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="4d38a-183">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="4d38a-184">**아이콘**을 'cube with bounding box'(경계 상자와 큐브) 아이콘으로 유지</span><span class="sxs-lookup"><span data-stu-id="4d38a-184">Leave the **Icon** as the 'cube with bounding box' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="4d38a-186">네 번째와 마지막 단추의 이름을 **BoundingBox_Disable**로 바꾼 다음, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-186">Rename the forth and last button to **BoundingBox_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="4d38a-187">**Main Label Text**(기본 레이블 텍스트)를 **Disable**(사용 안 함)로 변경</span><span class="sxs-lookup"><span data-stu-id="4d38a-187">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="4d38a-188">**RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="4d38a-188">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="4d38a-189">**No Function**(함수 없음) 드롭다운에서 **BoundingBox** > **bool Enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="4d38a-189">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="4d38a-190">인수 확인란이 **선택 취소**되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="4d38a-190">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="4d38a-191">작은 **+** 아이콘을 클릭하여 또 다른 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="4d38a-191">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="4d38a-192">**RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="4d38a-192">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="4d38a-193">**No Function**(함수 없음) 드롭다운에서 **ObjectManipulator** > **bool Enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="4d38a-193">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="4d38a-194">인수 확인란이 **선택 취소**되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="4d38a-194">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="4d38a-195">**아이콘**을 'cube with bounding box'(경계 상자와 큐브) 아이콘으로 변경</span><span class="sxs-lookup"><span data-stu-id="4d38a-195">Change the **Icon** to the 'cube with bounding box" icon</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="4d38a-197">이제 게임 모드로 전환하여 Enable(사용) 단추를 클릭하여 경계 상자를 사용하도록 설정하면, 근거리나 원거리 상호 작용을 사용하여 경계 상자를 이동 및 회전하고 크기를 조정할 수 있으며 Disable(사용 안 함) 단추를 사용하여 경계 상자를 다시 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-197">If you now enter Game mode and enable the Bounding Box by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounding Box, and use the Disable button to disable the Bounding Box again:</span></span>

![mr-learning-base](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="4d38a-199">경계 상자 구성 요소 및 관련 속성에 대한 자세한 내용을 보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [조작 처리기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d38a-199">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="4d38a-200">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-200">Congratulations</span></span>

<span data-ttu-id="4d38a-201">이 자습서에서는 3D 개체에 대한 근거리 및 원거리 조작을 사용하도록 설정하는 방법과 허용되는 조작 유형을 제한하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-201">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="4d38a-202">개체 조작을 보다 쉽게 제어할 수 있도록 3D 개체 주위에 경계 상자를 추가하는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="4d38a-202">You also learned how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

[<span data-ttu-id="4d38a-203">다음 자습서: 8. 시선 추적 사용</span><span class="sxs-lookup"><span data-stu-id="4d38a-203">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
