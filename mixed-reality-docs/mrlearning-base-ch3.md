---
title: 시작 자습서 - 4. 동적 콘텐츠 배치 및 해결기 사용
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 8a85ab560d0e6b36b589970b4d5b8a441ed2bbe2
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "80362042"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="3b627-105">4. 동적 콘텐츠 배치 및 해결기 사용</span><span class="sxs-lookup"><span data-stu-id="3b627-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="3b627-106">HoloLens 2에서 홀로그램은 사용자를 직관적으로 따라다니며, 원활하고 세련된 상호 작용을 지원하는 방식으로 실제 환경에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="3b627-107">이 자습서에서는 MRTK에서 제공하는 복잡한 공간 배치 시나리오를 해결할 수 있는 해결기라고 하는 배치 도구를 사용하여 홀로그램을 동적으로 배치하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="3b627-108">MRTK에서 해결기는 UI 요소가 장면에서 사용자 또는 다른 게임 개체를 따라다니도록 만드는 데 사용되는 스크립트 및 동작 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="3b627-109">특정 위치로 빠르게 스냅하여 애플리케이션을 보다 직관적인 만드는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="3b627-110">목표</span><span class="sxs-lookup"><span data-stu-id="3b627-110">Objectives</span></span>

* <span data-ttu-id="3b627-111">MRTK 해결기 소개</span><span class="sxs-lookup"><span data-stu-id="3b627-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="3b627-112">해결기를 사용하여 단추 컬렉션이 사용자를 따라다니게 만들기</span><span class="sxs-lookup"><span data-stu-id="3b627-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="3b627-113">해결기를 사용하여 게임 개체가 사용자의 추적 손을 따라다니게 만들기</span><span class="sxs-lookup"><span data-stu-id="3b627-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="3b627-114">MRTK에서 해결기의 위치</span><span class="sxs-lookup"><span data-stu-id="3b627-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="3b627-115">MRTK의 해결기는 MRTK SDK 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="3b627-116">프로젝트에서 사용할 수 있는 해결기를 확인하려면 다음과 같이 프로젝트 창에서 **자산** > **MixedRealityToolkit.SDK** > **기능** > **유틸리티** > **해결기**로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="3b627-118">이 자습서에서는 궤도 해결기 및 방사형 보기 해결기가 어떻게 구현되는지 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="3b627-119">MRTK에서 사용할 수 있는 해결기의 전체 범위를 알아보려면 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [해결기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b627-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="3b627-120">해결기를 사용하여 사용자 따라다니기</span><span class="sxs-lookup"><span data-stu-id="3b627-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="3b627-121">이 섹션에서는 단추가 사용자의 응시 방향을 따라다니도록 이전 자습서에서 만든 단추 컬렉션을 개선합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user's gaze direction.</span></span> <span data-ttu-id="3b627-122">또한 단추 컬렉션이 항상 다음과 같이 표시되도록 해결기를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="3b627-123">자연스럽게 왼쪽에서 오른쪽으로 읽도록 사용자의 읽기 방향에 평행하게 회전</span><span class="sxs-lookup"><span data-stu-id="3b627-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="3b627-124">이 자습서의 뒷부분에서 추가할 다른 개체를 가리지 않도록 사용자 수평 응시 방향보다 아래에 배치</span><span class="sxs-lookup"><span data-stu-id="3b627-124">Positioned below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="3b627-125">단추를 쉽게 누를 수 있도록 사용자로부터 팔 절반 길이쯤 되는 위치에 배치</span><span class="sxs-lookup"><span data-stu-id="3b627-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="3b627-126">이렇게 하기 위해, 개체를 참조 개체로부터 지정된 위치와 오프셋에 잠그는 **궤도 해결기**를 사용하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="3b627-127">1. 궤도 해결기 추가</span><span class="sxs-lookup"><span data-stu-id="3b627-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="3b627-128">[계층 구조] 창에서 **ButtonCollection** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **궤도(스크립트)** 구성 요소를 ButtonCollection 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="3b627-129">해결기를 추가하면(여기서는 궤도(스크립트) 구성 요소) 해결기에 필요한 해결기 처리기(스크립트) 구성 요소가 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="3b627-130">2. 궤도 해결기 구성</span><span class="sxs-lookup"><span data-stu-id="3b627-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="3b627-131">다음과 같이 **해결기 처리기(스크립트)** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="3b627-132">**추적 대상 형식**이 **헤드**로 설정되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="3b627-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="3b627-133">다음과 같이 **궤도(스크립트)** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="3b627-134">**방향 유형**이 **Follow Tracked Object(추적되는 개체 따라다니기)** 로 설정되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="3b627-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="3b627-135">**로컬 오프셋**을 X = 0, Y = 0, Z = 0으로 초기화</span><span class="sxs-lookup"><span data-stu-id="3b627-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="3b627-136">**World Offset(월드 오프셋)** 을 X = 0, Y = -0.4, Z = 0.3으로 변경</span><span class="sxs-lookup"><span data-stu-id="3b627-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="3b627-138">3. 편집기 내 시뮬레이션을 사용하여 궤도 해결기 테스트</span><span class="sxs-lookup"><span data-stu-id="3b627-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="3b627-139">[재생] 단추를 눌러 게임 모드로 전환한 다음, 마우스 오른쪽 단추를 누른 채로 응시 방향을 회전하면서 다음 사항을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="3b627-140">이제 ButtonCollection의 변환 위치는 해결기 설정에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="3b627-141">해결기의 영향을 받지 않는 큐브는 동일한 위치에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="3b627-143">[장면] 창에 카메라 광선이 보이지 않으면 Gizmo 메뉴가 활성화되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="3b627-144">Gizmo 메뉴에 대한 내용 및 이 메뉴를 사용하여 장면 보기를 최적화하는 방법에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmo 메뉴</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b627-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="3b627-145">위의 이미지처럼 장면 및 게임 창을 나란히 표시하려면 간단하게 게임 창을 장면 창의 오른쪽으로 끌어다 놓으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="3b627-146">작업 영역을 사용자 지정하는 방법에 대한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b627-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="3b627-147">개체가 추적 손을 따라다니도록 설정</span><span class="sxs-lookup"><span data-stu-id="3b627-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="3b627-148">이 섹션에서는 이전 자습서에서 만든 큐브 개체가 사용자의 추적 손, 특히 오른쪽 손목을 따라다니도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user's tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="3b627-149">또한 큐브가 다음과 같이 되도록 해결기를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="3b627-150">사용자의 손이 회전하면 방향 변경</span><span class="sxs-lookup"><span data-stu-id="3b627-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="3b627-151">사용자의 손목에 배치</span><span class="sxs-lookup"><span data-stu-id="3b627-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="3b627-152">이렇게 하기 위해, 참조 개체가 캐스팅하는 보기 콘 내부에 개체를 유지 하는 **방사형 보기 해결기**를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="3b627-153">1. 방사형 보기 해결기 추가</span><span class="sxs-lookup"><span data-stu-id="3b627-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="3b627-154">[계층 구조] 창에서 **큐브** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 큐브 개체에 **방사형 보기(스크립트)** 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="3b627-155">2. 방사형 보기 해결기 구성</span><span class="sxs-lookup"><span data-stu-id="3b627-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="3b627-156">다음과 같이 **해결기 처리기(스크립트)** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="3b627-157">**추적 대상 형식**을 **Hand Joint(손 관절)** 로 변경</span><span class="sxs-lookup"><span data-stu-id="3b627-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="3b627-158">**Tracked Handness(추적 손)** 를 **오른쪽**으로 변경</span><span class="sxs-lookup"><span data-stu-id="3b627-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="3b627-159">**Tracked Hand Joint(추적 손 관절)** 를 **손목**으로 변경</span><span class="sxs-lookup"><span data-stu-id="3b627-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="3b627-160">다음과 같이 **방사형 보기(스크립트)** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="3b627-161">**참조 방향**을 **개체 지향**으로 변경한 다음, **Orient To Reference Direction(참조 방향으로 회전)** 확인란 선택</span><span class="sxs-lookup"><span data-stu-id="3b627-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="3b627-162">**최소 거리** 및 **최대 거리**를 0으로 변경</span><span class="sxs-lookup"><span data-stu-id="3b627-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="3b627-164">3. 편집기 내 시뮬레이션을 사용하여 방사형 보기 해결기 테스트</span><span class="sxs-lookup"><span data-stu-id="3b627-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="3b627-165">[재생] 단추를 눌러 게임 모드로 전환한 다음, 스페이스바를 길게 눌러 손을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="3b627-166">다음과 같이 마우스 커서를 이동하여 손을 움직이고, 마우스 왼쪽 단추를 누른 채로 손을 회전해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="3b627-168">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-168">Congratulations</span></span>

<span data-ttu-id="3b627-169">이 자습서에서는 MRTK의 해결기를 사용하여 UI가 사용자를 직관적으로 따라다니게 만드는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-169">In this tutorial, you learned how to use the MRTK's solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="3b627-170">또한 해결기를 개체(예: 큐브)에 연결하여 사용자의 추적 손을 따라다니게 만드는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="3b627-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user's tracked hands.</span></span> <span data-ttu-id="3b627-171">이러한 해결기와 MRTK에 포함된 다른 해결기에 대한 자세한 내용은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [해결기](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b627-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="3b627-172">다음 자습서: 5. 3D 개체와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="3b627-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
