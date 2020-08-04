---
title: 시작 자습서 - 8. 시선 추적 사용
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여 줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 31552cba9a68d1f1214395dbf4e4ed84ecd3f388
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376605"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="01887-105">8. 시선 추적 사용</span><span class="sxs-lookup"><span data-stu-id="01887-105">8. Using eye-tracking</span></span>

## <a name="overview"></a><span data-ttu-id="01887-106">개요</span><span class="sxs-lookup"><span data-stu-id="01887-106">Overview</span></span>

<span data-ttu-id="01887-107">이 자습서에서는 HoloLens 2에 대해 시선 추적을 사용하도록 설정하고 개체에 시선 추적을 추가하여 사용자가 개체를 볼 때 작업을 트리거하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="01887-107">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="01887-108">이 프로젝트를 HoloLens(첫 번째 세대)에 배포하는 경우에는 HoloLens 2에서만 시선 추적이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="01887-108">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="01887-109">목표</span><span class="sxs-lookup"><span data-stu-id="01887-109">Objectives</span></span>

* <span data-ttu-id="01887-110">HoleLens 2에 대한 시선 추적을 사용하도록 설정하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="01887-110">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="01887-111">시선 추적을 사용하여 작업을 트리거하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="01887-111">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="01887-112">시선 응시 입력 기능이 활성화되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="01887-112">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="01887-113">Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > **Unity 프로젝트 구성**을 선택하여 **MRTK Project Configurator** 창을 열고 **UWP 기능** 섹션에서 **시선 응시 입력 기능 사용**이 회색으로 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-113">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="01887-115">이 자습서 시리즈의 시작 부분에서 Unity 프로젝트를 구성한 경우 [MRTK Project Configurator 설정 적용](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) 동안에는 응시 입력 기능이 사용하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-115">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="01887-116">그러나 사용하도록 설정되지 않은 경우 지금 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-116">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="01887-117">응시 공급자에서 시선 기반 응시 사용</span><span class="sxs-lookup"><span data-stu-id="01887-117">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="01887-118">Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 MixedRealityToolkit > **입력** 탭을 선택하고 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-118">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="01887-119">**DefaultHoloLens2InputSystemProfile**을 복제하고 적절한 이름(예: _GettingStarted_HoloLens2InputSystemProfile_)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-119">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="01887-120">**포인터** 섹션을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-120">Expand the **Pointers** section</span></span>
* <span data-ttu-id="01887-121">**DefaultMixedRealityPointerProfile**을 복제하고 적절한 이름(예: _GettingStarted_MixedRealityPointerProfile_)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-121">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="01887-122">**응시 설정** 섹션을 찾고 **시선 추적 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-122">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="01887-124">MRTK 프로필을 복제하는 방법은 [MRTK 프로필 구성](mr-learning-base-03.md) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01887-124">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="01887-125">Unity 편집기에 대해 시뮬레이션된 시선 추적 사용</span><span class="sxs-lookup"><span data-stu-id="01887-125">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="01887-126">Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 **입력** 탭으로 이동한 다음, 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-126">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="01887-127">**입력 데이터 공급자** > **입력 시뮬레이션 서비스** 섹션을 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-127">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="01887-128">**DefaultMixedRealityInputSimulationProfile**을 복제하고 적절한 이름(예: _GettingStarted_MixedRealityInputSimulationProfile_)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-128">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="01887-129">**시선 시뮬레이션** 섹션을 찾아 **시선 위치 시뮬레이션** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-129">Locate the **Eye Simulation** section and check the **Simulate Eye Position** checkbox</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="01887-131">개체에 시선 추적 추가</span><span class="sxs-lookup"><span data-stu-id="01887-131">Adding eye-tracking to objects</span></span>

<span data-ttu-id="01887-132">Hierarchy 창에서 RoverExplorer > **Buttons** 개체를 확장한 다음, 세 개의 자식 단추 개체 각각에 대해 SeeItSayItLabel > **TextMeshPro** 개체를 확장하고 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-132">In the Hierarchy window, expand the RoverExplorer > **Buttons** object, then for each of the three child button objects, expand and select the SeeItSayItLabel > **TextMeshPro** object:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="01887-134">TextMeshPro 개체를 선택한 상태로 Inspector 창에서 **구성 요소 추가** 단추를 사용하여 다음 구성 요소를 선택한 모든 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-134">With the three TextMeshPro objects still selected, in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="01887-135">**Box Collider** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="01887-135">**Box Collider** component</span></span>
* <span data-ttu-id="01887-136">**EyeTrackingTarget** 구성 요소</span><span class="sxs-lookup"><span data-stu-id="01887-136">**EyeTrackingTarget** component</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="01887-138">Hierarchy 창에서 **Hints** > SeeItSayItLabel > **TextMeshPro** 개체를 선택한 다음, 다음과 같이 **EyeTrackingTarget** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-138">In the Hierarchy window, select the **Hints** > SeeItSayItLabel > **TextMeshPro** object, then configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="01887-139">**On Look At Start ()** 이벤트 섹션에서</span><span class="sxs-lookup"><span data-stu-id="01887-139">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="01887-140">작은 **+** 아이콘을 클릭하여 다른 이벤트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-140">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="01887-141">개체 자체(즉, 동일한 **TextMeshPro** 개체)를 **없음(개체)** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-141">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="01887-142">**함수 없음** 드롭다운에서 **TextMeshPro** > **float fontSize**를 차례로 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-142">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="01887-143">인수를 **0.06**으로 설정하여 현재 글꼴 크기인 0.04 x 50%를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="01887-143">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="01887-144">**On Look Away ()** 이벤트 섹션에서</span><span class="sxs-lookup"><span data-stu-id="01887-144">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="01887-145">작은 **+** 아이콘을 클릭하여 다른 이벤트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-145">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="01887-146">개체 자체(즉, 동일한 **TextMeshPro** 개체)를 **없음(개체)** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-146">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="01887-147">**함수 없음** 드롭다운에서 **TextMeshPro** > **float fontSize**를 차례로 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-147">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="01887-148">인수를 **0.04**로 설정하여 글꼴 크기를 0.04로 다시 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-148">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="01887-150">**Explode** > SeeItSayItLabel > **TextMeshPro** 개체 및 **Reset** > SeeItSayItLabel > **TextMeshPro** 개체에 대해 이 단계를 **반복**합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-150">**Repeat** this step for the **Explode** > SeeItSayItLabel > **TextMeshPro** object and the **Reset** > SeeItSayItLabel > **TextMeshPro** object.</span></span>

<span data-ttu-id="01887-151">이제 게임 모드로 들어간 다음, 마우스 오른쪽 버튼을 누른 채로 마우스를 이동하면서 응시가 레이블 중 하나를 적중할 때까지 누르면 글꼴 크기가 50%씩 증가하고 시선을 돌렸을 때 원래 크기로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="01887-151">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the labels, you will see the font size increase by 50% and reset back to its original size when looking away:</span></span>

![mr-learning-base](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="01887-153">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="01887-153">Congratulations</span></span>

<span data-ttu-id="01887-154">이 자습서에서는 HoloLens 2에 대해 시선 추적을 사용하도록 설정하고 개체에 시선 추적을 추가하여 사용자가 개체를 볼 때 작업을 트리거하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="01887-154">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

[<span data-ttu-id="01887-155">다음 자습서: 9. 음성 명령 사용</span><span class="sxs-lookup"><span data-stu-id="01887-155">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)