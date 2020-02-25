---
title: 자습서-4를 시작 합니다. 동적 콘텐츠 배치 및 solvers 사용
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 5463f363291790fd5e5d76ffa322a61ca7bf8e31
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77553896"
---
# <a name="4-placing-dynamic-content-and-using-solvers"></a><span data-ttu-id="10118-105">4. 동적 콘텐츠 배치 및 Solvers 사용</span><span class="sxs-lookup"><span data-stu-id="10118-105">4. Placing dynamic content and using Solvers</span></span>
<!-- Consider renaming to 'Placing dynamic content using Solvers' -->

<span data-ttu-id="10118-106">Holograms은 사용자가 직관적이 고 원활 하 게 상호 작용 하는 방식으로 실제 환경에 배치 되는 경우 HoloLens 2를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-106">Holograms come to life in HoloLens 2 when they intuitively follow the user and are placed in the physical environment in a way that makes interaction seamless and elegant.</span></span> <span data-ttu-id="10118-107">이 자습서에서는 Solvers 이라고 하는 MRTK의 사용 가능한 배치 도구를 사용 하 여 동적으로 holograms을 배치 하 여 복잡 한 공간 배치 시나리오를 해결 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="10118-107">In this tutorial, we explore ways to dynamically place holograms using the MRTK’s available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="10118-108">MRTK에서 Solvers는 UI 요소에서 사용자, 사용자 또는 장면의 기타 게임 개체를 팔 로우 하는 데 사용 되는 스크립트 및 동작의 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="10118-108">In the MRTK, Solvers are a system of scripts and behaviors that are used to allow UI elements to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="10118-109">특정 위치로 빠르게 스냅하여 애플리케이션을 보다 직관적인 만드는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10118-109">They can also be used to snap to certain positions quickly, making your application more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="10118-110">목표</span><span class="sxs-lookup"><span data-stu-id="10118-110">Objectives</span></span>

* <span data-ttu-id="10118-111">MRTK의 Solvers 소개</span><span class="sxs-lookup"><span data-stu-id="10118-111">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="10118-112">Solvers를 사용 하 여 단추 컬렉션을 사용자에 게 따름</span><span class="sxs-lookup"><span data-stu-id="10118-112">Use Solvers to have a collection of buttons follow the user</span></span>
* <span data-ttu-id="10118-113">Solvers를 사용 하 여 게임 개체가 사용자의 추적 된 손을 따름</span><span class="sxs-lookup"><span data-stu-id="10118-113">Use Solvers to have a game object follow the user's tracked hands</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="10118-114">MRTK의 Solvers 위치</span><span class="sxs-lookup"><span data-stu-id="10118-114">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="10118-115">MRTK의 Solvers는 MRTK SDK 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10118-115">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="10118-116">프로젝트에서 사용 가능한 Solvers를 보려면 프로젝트 창에서 **자산** > **MixedRealityToolkit** > **기능** > **유틸리티** > **Solvers**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-116">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MixedRealityToolkit.SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section1-step1-1.png)

<span data-ttu-id="10118-118">이 자습서에서는 궤도 해 찾기 및 방사형 보기 해 찾기의 구현을 검토 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-118">In this tutorial, we will review the implementation of the Orbital Solver and the Radial View Solver.</span></span> <span data-ttu-id="10118-119">MRTK에서 사용할 수 있는 Solvers의 전체 범위에 대해 자세히 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) 가이드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="10118-119">To learn more about the full range of Solvers available in the MRTK, you can visit the the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="use-a-solver-to-follow-the-user"></a><span data-ttu-id="10118-120">사용자를 팔 로우 하는 데 사용할 수 있는 해 찾기</span><span class="sxs-lookup"><span data-stu-id="10118-120">Use a Solver to follow the user</span></span>
<!-- Consider renaming to 'Use a Solver to have an object follow the user' -->

<span data-ttu-id="10118-121">이 섹션에서는 사용자의 응시 방향을 따라 이전 자습서에서 만든 단추 컬렉션을 개선 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-121">In this section, you will enhance the button collection you created in the previous tutorial so it follows the user’s gaze direction.</span></span> <span data-ttu-id="10118-122">또한 단추 컬렉션이 항상이 되도록 해 찾기를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-122">Additionally, you will also configure the Solver so the button collection is always:</span></span>

* <span data-ttu-id="10118-123">왼쪽에서 오른쪽으로 읽도록 사용자의 읽기 방향에 평행 하 게 회전</span><span class="sxs-lookup"><span data-stu-id="10118-123">Rotated parallel to the user's reading direction, for natural left to right reading</span></span>
* <span data-ttu-id="10118-124">사용자 수평 응시 방향 아래에 배치 되므로이 자습서의 뒷부분에서 추가 하는 다른 개체를 방해 하지 않는지 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10118-124">Positioned slightly below the user horizontal gaze direction, so it's not obstructing the other objects you will add later in this tutorial</span></span>
* <span data-ttu-id="10118-125">사용자 로부터 약 1/2 arm의 길이에 배치 하므로 단추를 쉽게 누를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10118-125">Positioned approximately a half arm's-length from the user, so the buttons can easily be pressed</span></span>

<span data-ttu-id="10118-126">이 경우 개체를 참조 된 개체에서 지정 된 위치 및 오프셋으로 잠그는 **궤도 해** 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-126">For this, you will use the **Orbital Solver** which locks the object to a specified position and offset from the referenced object.</span></span>

### <a name="1-add-the-orbital-solver"></a><span data-ttu-id="10118-127">1. 궤도 해 찾기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-127">1. Add the Orbital Solver</span></span>

<span data-ttu-id="10118-128">계층 창에서 **buttoncollection** 개체를 선택한 다음 검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 **궤도 (스크립트)** 구성 요소를 buttoncollection 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-128">In the Hierarchy window, select the **ButtonCollection** object, then in the Inspector window, use the **Add Component** button to add the **Orbital (Script)** component to the ButtonCollection object.</span></span>

> [!NOTE]
> <span data-ttu-id="10118-129">해 찾기를 추가 하는 경우 (이 경우에는 궤도 (스크립트) 구성 요소) 해 찾기에 필요 하기 때문에 해결 프로그램 처리기 (스크립트) 구성 요소가 자동으로 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10118-129">When you add a Solver, in this case the Orbital (Script) component, the Solver Handler (Script) component is automatically added because it is required by the Solver.</span></span>

### <a name="2-configure-the-orbital-solver"></a><span data-ttu-id="10118-130">2. 궤도 해 찾기를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-130">2. Configure the Orbital Solver</span></span>

<span data-ttu-id="10118-131">**해 찾기 처리기 (스크립트)** 구성 요소를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-131">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="10118-132">**추적 대상 형식이** **Head** 로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-132">Verify that **Tracked Target Type** is set to **Head**</span></span>

<span data-ttu-id="10118-133">**궤도 (스크립트)** 구성 요소를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-133">Configure the **Orbital (Script)** component:</span></span>

* <span data-ttu-id="10118-134">**방향 유형** 이 **추적 된 개체 따르기** 로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-134">Verify that **Orientation Type** is set to **Follow Tracked Object**</span></span>
* <span data-ttu-id="10118-135">**로컬 오프셋** 을 X = 0, Y = 0, Z = 0으로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-135">Reset **Local Offset** to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="10118-136">**전역 오프셋** 을 X = 0, Y =-0.4, Z = 0.3로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-136">Change **World Offset** to X = 0, Y = -0.4, Z = 0.3</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step2-1.png)

### <a name="3-test-the-orbital-solver-using-the-in-editor-simulation"></a><span data-ttu-id="10118-138">3. 편집기 내 시뮬레이션을 사용 하 여 궤도 해 찾기 테스트</span><span class="sxs-lookup"><span data-stu-id="10118-138">3. Test the Orbital Solver using the in-editor simulation</span></span>

<span data-ttu-id="10118-139">재생 단추를 눌러 게임 모드로 전환 하 고 마우스 오른쪽 단추를 누른 채 마우스 오른쪽 단추를 눌러 응시 방향을 회전 하 고 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-139">Press the Play button to enter Game mode and press and hold the right mouse button to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="10118-140">이제 ButtonCollection의 변환 위치는 해 찾기 설정에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10118-140">The ButtonCollection's Transform Position is now driven by the Solver settings</span></span>
* <span data-ttu-id="10118-141">해 찾기의 영향을 받지 않는 큐브는 동일한 위치에 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10118-141">The Cube, which is not affected by the Solver, remains in the same position</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section2-step3-1.png)

> [!TIP]
> <span data-ttu-id="10118-143">장면 창에 카메라 광선이 표시 되지 않으면 Gizmo 그리려면 메뉴가 활성화 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-143">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled.</span></span> <span data-ttu-id="10118-144">Gizmo 그리려면 메뉴와이 메뉴를 사용 하 여 장면 보기를 최적화 하는 방법에 대 한 자세한 내용은 Unity의 <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">gizmo 그리려면 메뉴</a> 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="10118-144">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can visit Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>
>
> <span data-ttu-id="10118-145">위의 이미지에 표시 된 대로 장면 및 게임 창을 나란히 표시 하려면 게임 창을 장면 창의 오른쪽으로 끌기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10118-145">To display your Scene and Game window side by side as shown in the image above, simply drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="10118-146">작업 영역을 사용자 지정 하는 방법에 대해 자세히 알아보려면 Unity의 <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">작업 영역 사용자 지정</a> 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="10118-146">To learn more about customizing your workspace, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

## <a name="enabling-objects-to-follow-tracked-hands"></a><span data-ttu-id="10118-147">추적 된 손을 따르도록 개체 활성화</span><span class="sxs-lookup"><span data-stu-id="10118-147">Enabling objects to follow tracked hands</span></span>

<span data-ttu-id="10118-148">이 섹션에서는 이전 자습서에서 만든 큐브 개체를 구성 하 여 사용자의 추적 된 실습, 특히 오른쪽 손목를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="10118-148">In this section, you will configure the Cube object you created in the previous tutorial so it follows the user’s tracked hands, specifically the right hand wrist.</span></span> <span data-ttu-id="10118-149">또한 다음과 같이 큐브를 구성 해 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10118-149">Additionally, you will also configure the Solver so the cube:</span></span>

* <span data-ttu-id="10118-150">사용자의 손을 회전 하 여 방향을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-150">Changes it's orientation with the user's hand rotation</span></span>
* <span data-ttu-id="10118-151">사용자의 손목 위치</span><span class="sxs-lookup"><span data-stu-id="10118-151">Positioned on the user's wrist</span></span>

<span data-ttu-id="10118-152">이 경우 참조 된 개체에의 한 뷰 원추 내에서 개체를 유지 하는 **방사형 보기 해 찾기를** 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-152">For this, you will use the **Radial View Solver** which keeps the object within a view cone cast by the referenced object.</span></span>

### <a name="1-add-the-radial-view-solver"></a><span data-ttu-id="10118-153">1. 방사형 보기 해 찾기 추가</span><span class="sxs-lookup"><span data-stu-id="10118-153">1. Add the Radial View Solver</span></span>

<span data-ttu-id="10118-154">계층 창에서 **큐브** 개체를 선택한 다음, 검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 **방사형 보기 (스크립트)** 구성 요소 큐브 개체를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-154">In the Hierarchy window, select the **Cube** object, then in the Inspector window, use the **Add Component** button to add the **Radial View (Script)** component Cube object.</span></span>

### <a name="2-configure-the-radial-view-solver"></a><span data-ttu-id="10118-155">2. 방사형 보기 해결 기 구성</span><span class="sxs-lookup"><span data-stu-id="10118-155">2. Configure the Radial View Solver</span></span>

<span data-ttu-id="10118-156">**해 찾기 처리기 (스크립트)** 구성 요소를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-156">Configure the **Solver Handler (Script)** component:</span></span>

* <span data-ttu-id="10118-157">**추적 대상 유형을** **직접 조인트** 로 변경</span><span class="sxs-lookup"><span data-stu-id="10118-157">Change **Tracked Target Type** to **Hand Joint**</span></span>
* <span data-ttu-id="10118-158">**추적** 을 **오른쪽** 으로 변경</span><span class="sxs-lookup"><span data-stu-id="10118-158">Change **Tracked Handness** to **Right**</span></span>
* <span data-ttu-id="10118-159">**추적 된 손을** **손목** 으로 변경</span><span class="sxs-lookup"><span data-stu-id="10118-159">Change **Tracked Hand Joint** to **Wrist**</span></span>

<span data-ttu-id="10118-160">**방사형 보기 (스크립트)** 구성 요소를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-160">Configure the **Radial View (Script)** component:</span></span>

* <span data-ttu-id="10118-161">**참조 방향을** **개체 지향**으로 변경한 다음 방향 **참조 방향** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-161">Change **Reference Direction** to **Object Oriented**, then check the **Orient To Reference Direction** checkbox</span></span>
* <span data-ttu-id="10118-162">**최소 거리** 및 **최대 거리** 를 0으로 변경</span><span class="sxs-lookup"><span data-stu-id="10118-162">Change **Min Distance** and **Max Distance** to 0</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step2-1.png)

### <a name="3-test-the-radial-view-solver-using-the-in-editor-simulation"></a><span data-ttu-id="10118-164">3. 편집기 내 시뮬레이션을 사용 하 여 방사형 보기 해 찾기를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-164">3. Test the Radial View Solver using the in-editor simulation</span></span>

<span data-ttu-id="10118-165">게임 모드로 전환 하려면 재생 단추를 누르고 스페이스바를 누르고 있으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10118-165">Press the Play button to enter Game mode and then press and hold the spacebar to bring up the hand.</span></span> <span data-ttu-id="10118-166">마우스 커서를 이동 하 여 손 모양으로 이동 하 고 마우스 왼쪽 단추를 클릭 하 여 손을 회전 합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-166">Move the mouse cursor around to move the hand, and click and hold the left mouse button to rotate the hand:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial3-section3-step3-1.png)

## <a name="congratulations"></a><span data-ttu-id="10118-168">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="10118-168">Congratulations</span></span>

<span data-ttu-id="10118-169">이 자습서에서는 MRTK의 solvers를 사용 하 여 UI가 사용자를 직관적으로 따르도록 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="10118-169">In this tutorial, you learned how to use the MRTK’s solvers to have a UI intuitively follow the user.</span></span> <span data-ttu-id="10118-170">또한 사용자의 추적 된 작업을 수행 하기 위해 개체 (예: 큐브)에 해 찾기를 첨부 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="10118-170">You also learned how to attach a Solver to an object (i.e., cube) to follow the user’s tracked hands.</span></span> <span data-ttu-id="10118-171">이에 대 한 자세한 내용 및 MRTK에 포함 된 다른 solvers에 대 한 자세한 내용은 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) 가이드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="10118-171">To learn more about these and other solvers included with the MRTK,  you can visit the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="10118-172">다음 자습서: 5.3D 개체와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="10118-172">Next Tutorial: 5. Interacting with 3D objects</span></span>](mrlearning-base-ch4.md)
