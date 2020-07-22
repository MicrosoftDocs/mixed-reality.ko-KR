---
title: 시작 자습서 - 3. MRTK 프로필 구성
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여 줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 2c413964a435814275a1b908770ca977412f92be
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306728"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="a339f-105">3. MRTK 프로필 구성</span><span class="sxs-lookup"><span data-stu-id="a339f-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="a339f-106">개요</span><span class="sxs-lookup"><span data-stu-id="a339f-106">Overview</span></span>

<span data-ttu-id="a339f-107">이 자습서에서는 MRTK 프로필을 사용자 지정하고 구성하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="a339f-108">이 예제에서는 공간 메시 관찰자의 설정을 변경하여 공간 인식 메시를 숨기는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-108">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="a339f-109">그러나 MRTK 프로필의 설정 또는 값을 사용자 지정할 때 이러한 원칙을 그대로 적용해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-109">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

## <a name="objectives"></a><span data-ttu-id="a339f-110">목표</span><span class="sxs-lookup"><span data-stu-id="a339f-110">Objectives</span></span>

* <span data-ttu-id="a339f-111">MRTK 프로필을 사용자 지정 및 구성하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="a339f-111">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="a339f-112">공간 인식 메시 숨기기</span><span class="sxs-lookup"><span data-stu-id="a339f-112">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="a339f-113">공간 인식 표시 옵션 변경</span><span class="sxs-lookup"><span data-stu-id="a339f-113">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="a339f-114">공간 인식 메시를 숨기기 위해 수행하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-114">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="a339f-115">기본 구성 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="a339f-115">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="a339f-116">공간 인식 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="a339f-116">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="a339f-117">기본 공간 인식 시스템 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="a339f-117">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="a339f-118">기본 공간 인식 메시 관찰자 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="a339f-118">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="a339f-119">공간 인식 메시의 표시 유형 변경</span><span class="sxs-lookup"><span data-stu-id="a339f-119">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="a339f-120">기본적으로 MRTK 프로필은 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-120">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="a339f-121">이러한 기본 프로필 템플릿을 편집하려면 먼저 복제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-121">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="a339f-122">중첩된 여러 프로필 레이어가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-122">There are several nested layers of profiles.</span></span> <span data-ttu-id="a339f-123">따라서 하나 이상의 설정을 구성할 때 여러 프로필을 복제하여 편집하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-123">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="a339f-124">1. 기본 구성 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="a339f-124">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="a339f-125">구성 프로필은 최상위 수준 프로필입니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-125">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="a339f-126">따라서 다른 프로필을 편집하려면 먼저 구성 프로필을 복제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-126">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="a339f-127">Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 **MixedRealityToolkit** 구성 프로필을 **DefaultHoloLens2ConfigurationProfile**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-127">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="a339f-129">다음과 같이 **MixedRealityToolkit** 개체를 선택한 상태로, [검사기] 창에서 **복제 및 사용자 지정** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-129">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="a339f-131">Clone Profile 창에서 적절한 **프로필 이름**(예: _GettingStarted_HoloLens2ConfigurationProfile_)을 입력한 다음, **복제** 단추를 클릭하여 **DefaultHololens2ConfigurationProfile**의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-131">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="a339f-133">이제 새로 만든 구성 프로필이 다음과 같이 장면의 구성 프로필로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-133">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="a339f-135">Unity 메뉴에서 **파일** > **저장**을 선택하여 장면을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-135">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="a339f-136">자습서를 진행하는 동안 항상 작업을 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-136">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="a339f-137">2. 공간 인식 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="a339f-137">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="a339f-138">Hierarchy 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector 창에서 **공간 인식** 탭을 선택한 다음, **공간 인식 시스템 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-138">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="a339f-140">3. 기본 공간 인식 시스템 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="a339f-140">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="a339f-141">다음과 같이 **공간 인식** 탭에서 **복제** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-141">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="a339f-143">Clone Profile 창에서 적절한 **프로필 이름**(예: _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_)을 입력한 다음, **복제** 단추를 클릭하여 **DefaultMixedRealitySpatialAwarenessSystemProfile**의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-143">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="a339f-145">이제 새로 만든 공간 인식 시스템 프로필이 다음과 같이 구성 프로필에 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-145">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="a339f-147">4. 기본 공간 인식 메시 관찰자 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="a339f-147">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="a339f-148">다음과 같이 **공간 인식** 탭을 선택한 상태로 **Windows Mixed Reality 공간 메시 관찰자** 섹션을 확장한 다음, **복제** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-148">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="a339f-150">Clone Profile 창에서 적절한 **프로필 이름**(예: _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_)을 입력한 다음, **복제** 단추를 클릭하여 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="a339f-152">이제 새로 만든 공간 인식 메시 관찰자 프로필이 다음과 같이 공간 인식 시스템 프로필에 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-152">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="a339f-154">5. 공간 인식 메시의 표시 유형 변경</span><span class="sxs-lookup"><span data-stu-id="a339f-154">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="a339f-155">다음과 같이 **공간 메시 관찰자 설정**에서 **표시 옵션**을 **폐색**으로 변경하여 공간 매핑 메시가 계속 작동하는 동안에도 보이지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-155">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="a339f-157">공간 매핑 메시가 보이지 않더라도 여전히 존재하며 작동 중입니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-157">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="a339f-158">예를 들어 실제 벽 뒤의 홀로그램처럼 공간 매핑 메시 뒤의 홀로그램은 보이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-158">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="a339f-159">MRTK 프로필에서 설정을 수정하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-159">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="a339f-160">보시는 것처럼, MRTK 설정을 사용자 지정하려면 먼저 기본 프로필의 복사본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-160">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="a339f-161">기본 프로필은 편집이 불가능하므로, 기본 설정으로 되돌리고 싶을 때 항상 기본 프로필을 참조로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-161">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="a339f-162">MRTK 프로필 및 해당 아키텍처에 대한 자세한 내용은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [MRTK 프로필 구성 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a339f-162">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="a339f-163">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-163">Congratulations</span></span>

<span data-ttu-id="a339f-164">이 자습서에서는 MRTK 프로필 및 설정을 복제, 사용자 지정 및 구성하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="a339f-164">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

[<span data-ttu-id="a339f-165">다음 자습서: 4. 장면에서 개체 위치 지정</span><span class="sxs-lookup"><span data-stu-id="a339f-165">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
