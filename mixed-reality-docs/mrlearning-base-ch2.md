---
title: 자습서를 시작 합니다. 3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 067832a130f130ffbaa8d455007b8e77e1b13671
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130535"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="b7e04-105">3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성</span><span class="sxs-lookup"><span data-stu-id="b7e04-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="b7e04-106">이전 자습서에서는 HoloLens 2에 대 한 첫 번째 응용 프로그램을 시작 하 여 혼합 현실 도구 키트 (MRTK)가 제공 해야 하는 기능 중 일부에 대해 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="b7e04-107">이 자습서에서는 UI 텍스트 패널과 함께 단추를 만들고 구성 하 고, 터치 (기본 상호 작용)를 사용 하 여 각 단추와 상호 작용 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="b7e04-108">개체의 크기, 사운드 및 색상 변경과 같은 간단한 작업과 효과도 추가로 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="b7e04-109">이 모듈에서는 [공간 매핑](spatial-mapping.md) 메시 시각화를 해제 하는 것부터 MRTK 프로필 수정에 대 한 기본 개념을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="b7e04-110">목표</span><span class="sxs-lookup"><span data-stu-id="b7e04-110">Objectives</span></span>

* <span data-ttu-id="b7e04-111">Mixed Reality Toolkit 프로필 사용자 지정 및 구성</span><span class="sxs-lookup"><span data-stu-id="b7e04-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="b7e04-112">UI 요소 및 단추를 사용 하 여 holograms와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="b7e04-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="b7e04-113">기본적인 손 추적 입력 및 상호 작용</span><span class="sxs-lookup"><span data-stu-id="b7e04-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="b7e04-114">Mixed Reality Toolkit 프로필을 구성 하는 방법 (공간 인식 표시 옵션 변경)</span><span class="sxs-lookup"><span data-stu-id="b7e04-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="b7e04-115">이 섹션에서는 기본 MRTK 프로필을 사용자 지정 하 고 구성 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="b7e04-116">이 특정 예제에서는 공간 메시 관찰자의 설정을 변경 하 여 공간 인식 메시를 숨기는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="b7e04-117">그러나이 동일한 원칙에 따라 MRTK 프로필의 설정 또는 값을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="b7e04-118">공간 인식 메시를 숨기기 위해 수행 하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="b7e04-119">기본 구성 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="b7e04-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="b7e04-120">공간 인식 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="b7e04-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="b7e04-121">기본 공간 인식 시스템 프로필을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="b7e04-122">기본 공간 인식 메시 관찰자 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="b7e04-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="b7e04-123">공간 인식 메시의 표시 유형 변경</span><span class="sxs-lookup"><span data-stu-id="b7e04-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="b7e04-124">기본적으로 MRTK 프로필은 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="b7e04-125">이러한 템플릿은 편집 하기 전에 복제 해야 하는 기본 프로필 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="b7e04-126">여러 개의 중첩 된 프로필 계층이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="b7e04-127">따라서 하나 이상의 설정을 구성할 때 여러 프로필을 복제 하 고 편집 하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="b7e04-128">1. 기본 구성 프로필을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="b7e04-129">구성 프로필은 최상위 수준 프로필입니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="b7e04-130">따라서 다른 프로필을 편집할 수 있으려면 먼저 구성 프로필을 복제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="b7e04-131">계층 창에서 **MixedRealityToolkit** 개체를 선택한 상태에서 검사기 창에서 **복사 & 사용자 지정** 단추를 클릭 하 여 복제 프로필 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="b7e04-133">복제 프로필 창에서 **복제** 단추를 클릭 하 여 **DefaultHololens2ConfigurationProfile**의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-133">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="b7e04-135">이제 새로 만든 구성 프로필이 장면의 구성 프로필로 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-135">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="b7e04-137">Unity 메뉴에서 **파일** > **저장** 을 선택 하 여 장면을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-137">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="b7e04-138">자습서 전체에서 작업을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-138">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="b7e04-139">2. 공간 인식 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="b7e04-139">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="b7e04-140">계층 창에서 **MixedRealityToolkit** 개체를 선택 하 고 검사기 창에서 **공간 인식** 탭을 선택한 후 **공간 인식 시스템 사용** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-140">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="b7e04-142">3. 기본 공간 인식 시스템 프로필을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-142">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="b7e04-143">**공간 인식** 탭에서 **복제** 단추를 클릭 하 여 복제 프로필 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-143">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="b7e04-145">복제 프로필 창에서 **복제** 단추를 클릭 하 여 **DefaultMixedRealitySpatialAwarenessSystemProfile**의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-145">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="b7e04-147">이제 새로 만든 공간 인식 시스템 프로필이 구성 프로필에 자동으로 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-147">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="b7e04-149">4. 기본 공간 인식 메시 관찰자 프로필을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-149">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="b7e04-150">**공간 인식** 탭을 선택한 상태에서 **Windows Mixed Reality 공간 메시 관찰자** 섹션을 확장 한 다음 **복제** 단추를 클릭 하 여 복제 프로필 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-150">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="b7e04-152">복제 프로필 창에서 **복제** 단추를 클릭 하 여 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-152">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="b7e04-154">새로 만든 공간 인식 메시 관찰자 프로필은 이제 공간 인식 시스템 프로필에 자동으로 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-154">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="b7e04-156">5. 공간 인식 메시의 표시 여부를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-156">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="b7e04-157">**공간 메시 관찰자 설정**에서 **표시 옵션** 을 **폐색** 로 변경 하 여 공간 매핑 메시를 계속 작동 하는 동안 표시 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-157">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="b7e04-159">공간 매핑 메시는 표시 되지 않지만 여전히 존재 하 고 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-159">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="b7e04-160">예를 들어 실제 벽 뒤의 홀로그램 처럼 공간 매핑 메시 뒤의 holograms은 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-160">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="b7e04-161">MRTK 프로필에서 설정을 수정하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-161">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="b7e04-162">여기서 볼 수 있듯이 MRTK 설정을 사용자 지정 하려면 먼저 기본 프로필의 복사본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-162">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="b7e04-163">기본 프로필을 편집할 수 없기 때문에 기본 설정으로 되돌리려면 항상 해당 프로필을 참조로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-163">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="b7e04-164">MRTK 프로필 및 해당 아키텍처에 대해 자세히 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [Mixed Reality Toolkit 프로필 구성 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b7e04-164">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="b7e04-165">제스처 및 interactable 단추 수동 추적</span><span class="sxs-lookup"><span data-stu-id="b7e04-165">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="b7e04-166">이 섹션에서는 단추를 누를 때 작업을 발생 시키는 단추를 누르고 이벤트를 트리거하는 데 수동 추적을 사용 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-166">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="b7e04-167">이 특정 예제에서는 단추를 누를 때 큐브의 색을 변경 하 고 단추가 해제 될 때 원래의 색으로 다시 변경 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-167">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="b7e04-168">그러나 이러한 동일한 원칙에 따라 다른 이벤트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-168">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="b7e04-169">큐브의 색을 변경 하기 위해 수행 하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-169">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="b7e04-170">장면에 pressable 단추 prefab 추가</span><span class="sxs-lookup"><span data-stu-id="b7e04-170">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="b7e04-171">장면에 큐브 추가</span><span class="sxs-lookup"><span data-stu-id="b7e04-171">Add a cube to the scene</span></span>
3. <span data-ttu-id="b7e04-172">InteractableOnPressReceiver 이벤트 유형 구성</span><span class="sxs-lookup"><span data-stu-id="b7e04-172">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="b7e04-173">On Press 이벤트를 받도록 큐브 구성</span><span class="sxs-lookup"><span data-stu-id="b7e04-173">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="b7e04-174">On Press 이벤트에서 트리거할 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-174">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="b7e04-175">On Release 이벤트를 받도록 큐브 구성</span><span class="sxs-lookup"><span data-stu-id="b7e04-175">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="b7e04-176">On Release 이벤트에서 트리거할 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-176">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="b7e04-177">편집기 내 시뮬레이션을 사용 하 여 단추 테스트</span><span class="sxs-lookup"><span data-stu-id="b7e04-177">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="b7e04-178">1. 장면에 pressable 단추 prefab 추가</span><span class="sxs-lookup"><span data-stu-id="b7e04-178">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="b7e04-179"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">Prefab</a> 는 Unity 자산으로 저장 되 고 프로젝트 전체에서 다시 사용할 수 있는 미리 구성 된 GameObject입니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-179">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="b7e04-180">**프로젝트 창**에서 **PressableButtonHoloLens2** 를 검색 하 여이 예제에 사용할 prefab를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-180">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="b7e04-182">**검색** 결과에서 **PressableButtonHoloLens2** prefab를 선택 하 고 **계층** 창으로 **끌어** 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-182">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="b7e04-184">아래 이미지에 표시 된 것 처럼 장면을 표시 하려면 계층 창에서 PressableButtonHoloLens2 개체를 두 번 클릭 하 여 포커스를 가져온 다음 장면 창의 오른쪽 위 모퉁이에 있는 <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Gizmo 장면을</a>사용 하 여 보기 각도를 앞으로 Z 축을 따라 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-184">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="b7e04-185">PressableButtonHoloLens2 개체가 선택 된 상태에서 **검사기** 창에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-185">With the PressableButtonHoloLens2 object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="b7e04-186">원본에 위치 하는 카메라 앞에 배치 되도록 변환 **위치** 를 변경 합니다 (예: x = 0, y = 0 및 z = 0.5).</span><span class="sxs-lookup"><span data-stu-id="b7e04-186">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="b7e04-188">일반적으로 Unity에서 1 위치 단위는 물리적 세계에서 1 미터와 거의 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-188">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="b7e04-189">그러나 개체가 크기 조정 된 개체의 자식인 경우와 같이이에 대 한 예외도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-189">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="b7e04-190">2. 장면에 큐브 추가</span><span class="sxs-lookup"><span data-stu-id="b7e04-190">2. Add a cube to the scene</span></span>

<span data-ttu-id="b7e04-191">계층 창 내부의 빈 지점을 마우스 오른쪽 단추로 클릭 하 고 **3D 개체** > **큐브** 를 선택 하 여 큐브를 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-191">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="b7e04-193">선택한 큐브 개체를 사용 하 여 **검사기** 창에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-193">With the Cube object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="b7e04-194">Pressable 단추 근처에 있지만 (예: x = 0, y = 0.04 및 z = 0.5)와 겹치지 않도록 변환 **위치** 를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-194">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="b7e04-195">변환 **배율을** 적절 한 크기로 변경 합니다 (예: x = 0.02, y = 0.02 및 z = 0.02).</span><span class="sxs-lookup"><span data-stu-id="b7e04-195">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="b7e04-197">3. Interactableon보도 Sreceiver 이벤트 유형 구성</span><span class="sxs-lookup"><span data-stu-id="b7e04-197">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="b7e04-198">계층 창에서 선택한 PressableButtonHoloLens2 개체를 사용 하 여 **검사기** 창 **햄버거 메뉴**에서 **Collaps 모든 구성 요소** 를 선택 하 여이 개체의 모든 구성 요소에 대 한 개요를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-198">With the PressableButtonHoloLens2 object selected in the Hierarchy window, in the **Inspector** window **hamburger menu**, select **Collaps All Components** to get an overview of all components on this object:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="b7e04-200">**Interactable (스크립트)** 구성 요소를 확장 한 다음 **이벤트** > **수신자** 섹션을 찾아 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-200">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="b7e04-202">이벤트 수신기 유형 **Interactableonpressreceiver**에서 **상호 작용 필터** 를 **Near 및 Far**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-202">For the Event Receiver Type **InteractableOnPressReceiver**, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="b7e04-204">Interactableon보도 Sreceiver 이라는 이벤트 수신기 유형을 사용 하면 추적 된 손을 단추를 누를 때 눌린 이벤트에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-204">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="b7e04-205">4. On Press 이벤트를 받도록 큐브 구성</span><span class="sxs-lookup"><span data-stu-id="b7e04-205">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="b7e04-206">계층 창에서 **큐브** 를 **클릭 하 고** **on press ()** 이벤트에 대 한 **이벤트 속성** 개체 필드로 끌어 큐브를 on press () 이벤트의 받는 사람으로 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-206">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="b7e04-208">5. On Press 이벤트에서 트리거할 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-208">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="b7e04-209">작업 드롭다운 (현재 **함수 없음**)을 클릭 하 고 **MeshRenderer** > **자재 자료** 를 선택 하 여 On Press () 이벤트가 트리거될 때 변경할 큐브의 재질 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-209">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="b7e04-211">재질 필드 옆에 있는 작은 **원** 아이콘 **(재질)** 을 클릭 하 여 재질 선택 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-211">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="b7e04-213">재질 선택 창에서 **MRTK_Standard** 을 **검색** 하 고 적절 한 재질을 선택 합니다. 예를 들어, 단추를 누르면 큐브의 색이 녹청으로 변경 되도록 **MRTK_Standard_Cyan** .</span><span class="sxs-lookup"><span data-stu-id="b7e04-213">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="b7e04-215">6. On Release 이벤트를 받도록 큐브 구성</span><span class="sxs-lookup"><span data-stu-id="b7e04-215">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="b7e04-216">**반복** On Release 이벤트의 경우 4 단계를 통해 릴리스 () 이벤트의 받는 사람으로 큐브를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-216">**Repeat** Step 4 for the On Release event to assign the Cube as a receiver of the On Release () event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="b7e04-217">7. On Release 이벤트에서 트리거할 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-217">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="b7e04-218">**반복** On Release 이벤트에 대해 5 단계 이지만, 단추가 해제 될 때 큐브의 색이 원래의 밝은 회색 색으로 반환 되도록 **MRTK_Standard_LightGray** 재질을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-218">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="b7e04-220">8. 편집기 내 시뮬레이션을 사용 하 여 단추 테스트</span><span class="sxs-lookup"><span data-stu-id="b7e04-220">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="b7e04-221">**재생** 단추를 눌러 게임 모드로 전환 하 고 편집기 내 입력 시뮬레이션을 사용 하 여 새로 구성 된 단추를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-221">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="b7e04-222">단추를 누르지 않음 (스페이스바 + 마우스 스크롤 휠):</span><span class="sxs-lookup"><span data-stu-id="b7e04-222">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="b7e04-224">단추 누름 (스페이스바 + 마우스 스크롤 휠을 앞으로):</span><span class="sxs-lookup"><span data-stu-id="b7e04-224">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="b7e04-226">편집기에서 입력 시뮬레이션을 사용 하는 방법을 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)에서 [편집기 내 입력 시뮬레이션을 사용](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) 하 여 장면 가이드를 테스트 하는 방법을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-226">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="b7e04-227">MRTK의 Grid Object Collection을 사용하여 버튼 패널 만들기</span><span class="sxs-lookup"><span data-stu-id="b7e04-227">Creating a panel of buttons using MRTK’s Grid Object Collection</span></span>

<span data-ttu-id="b7e04-228">이 섹션에서는 MRTK의 Grid 개체 수집 도구를 사용 하 여 자동으로 여러 단추를 깔끔한 사용자 인터페이스로 맞추는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-228">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK’s Grid Object Collection tool.</span></span>

<span data-ttu-id="b7e04-229">이 특정 예제에서는 5 개의 단추가 가로로 맞춰진 패널을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-229">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="b7e04-230">그러나 이러한 동일한 원칙에 따라 다른 레이아웃을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-230">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="b7e04-231">이를 위해 수행 하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-231">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="b7e04-232">부모 개체에 대 한 단추 개체의 부모</span><span class="sxs-lookup"><span data-stu-id="b7e04-232">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="b7e04-233">Grid 개체 컬렉션 (스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="b7e04-233">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="b7e04-234">편집기에서 시뮬레이션을 사용 하 여 단추 테스트</span><span class="sxs-lookup"><span data-stu-id="b7e04-234">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="b7e04-235">1. 부모 개체에 대 한 단추 개체의 부모</span><span class="sxs-lookup"><span data-stu-id="b7e04-235">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="b7e04-236">계층 창 내부에서 빈 지점을 마우스 오른쪽 단추로 클릭 하 고 **빈 만들기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-236">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="b7e04-238">새로 만든 개체를 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 선택 하 여 적절 한 이름을 지정 합니다 (예: **buttoncollection**).</span><span class="sxs-lookup"><span data-stu-id="b7e04-238">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="b7e04-240">**PressableButtonHoloLens2** 개체를 선택 하 고 **buttoncollection** 개체의 위쪽 **으로 끌어** buttoncollection 개체의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-240">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="b7e04-242">**PressableButtonHoloLens2** 개체를 마우스 오른쪽 단추로 클릭 하 고 **복제** 를 선택 하 여 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-242">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="b7e04-244">총 5 개의 PressableButtonHoloLens2 개체가 나올 때까지이 단계를 4 번 더 **반복** 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-244">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="b7e04-245">2. 그리드 개체 컬렉션 (스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="b7e04-245">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="b7e04-246">계층 창에서 ButtonCollection 개체를 선택 하 고 검사기 창에서 **구성 요소 추가** 단추를 클릭 한 다음 **표 개체 컬렉션** 을 검색 하 고 선택 하 여 Buttoncollection 개체에 그리드 개체 컬렉션 (스크립트) 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-246">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="b7e04-248">다음과 같이 그리드 개체 컬렉션 (스크립트)을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-248">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="b7e04-249">단일 행에 모든 단추가 정렬 되도록 **Num 행** 을 1로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-249">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="b7e04-250">**셀 너비** 를 0.05으로 변경 하 여 행 내의 단추를 공백으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-250">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="b7e04-251">그런 다음 **컬렉션 업데이트** 단추를 클릭 하 여 새 구성을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-251">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="b7e04-253">방금 적용 한 구성 변경 내용은 단추를 단일 행에 배치 하는 목표를 달성 하는 데 필요한 최소 변경 내용을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-253">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="b7e04-254">그러나 이후 프로젝트에서 부모 개체와 자식 개체의 방향 등의 요소에 따라 방향 유형과 같은 다른 설정을 조정 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-254">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="b7e04-255">MRTK의 그리드 개체 컬렉션에 대해 자세히 알아보려면 [Mrtk 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [개체 컬렉션 스크립트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) 가이드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b7e04-255">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="b7e04-256">계층 창에서 ButtonCollection 개체를 선택한 상태에서 Inspector 창에서 ButtonCollection 개체의 변환 **위치** 를 변경 하 여 자식 단추 개체가 카메라 앞에 배치 되도록 합니다. 즉, x = 0, y = 0, z = 0.5과 같이 원점에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-256">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="b7e04-258">위의 [손을 tracking 제스처 및 interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 섹션의 장면에 PressableButtonHoloLens2 prefab를 처음 추가 하면 카메라 앞에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-258">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="b7e04-259">그러나 Grid 개체 컬렉션은 직계 자식 개체의 위치를 제어 하기 때문에 PressableButtonHoloLens2 자식 개체의 Z 위치는 부모 값 0의 기본 거리에 따라 0으로 다시 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-259">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="b7e04-260">부모/자식 위치 관계를 구성 하기 위해 부모 값에서 거리를 구성 하는 대신 부모 ButtonCollection 개체의 위치를 앞으로 이동 하는 이유는 PressableButtonHoloLens2 자식 개체를 앞으로 이동 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-260">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="b7e04-261">3. 편집기 내 시뮬레이션을 사용 하 여 단추 테스트</span><span class="sxs-lookup"><span data-stu-id="b7e04-261">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="b7e04-262">재생 단추를 눌러 게임 모드로 전환 하 고 편집기 내 입력 시뮬레이션을 사용 하 여 새로 만든 단추 패널의 각 단추를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-262">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="b7e04-264">현재 5 개 단추 중 하나를 누르면 큐브 색이 녹청로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-264">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="b7e04-265">더 흥미로운 환경을 만들려면 각 단추를 구성 하 여 큐브를 다른 색으로 변경 하는 방법에 대해 배운 내용을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-265">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="b7e04-266">장면에 텍스트 추가</span><span class="sxs-lookup"><span data-stu-id="b7e04-266">Adding text into your scene</span></span>

<span data-ttu-id="b7e04-267">이 섹션에서는 이전 자습서의 [Textmesh Pro 필수 리소스 가져오기](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) 섹션에서 준비한 Unity의 Textmesh pro를 사용 하 여 혼합 현실 환경에 텍스트를 추가 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-267">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="b7e04-268">이 특정 예제에서는 이전 섹션에서 만든 단추 컬렉션 아래에 간단한 레이블을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-268">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="b7e04-269">ButtonCollection 개체를 마우스 오른쪽 단추로 클릭 하 고 **3D 개체** > **선택 하 여 TextMeshPro** 개체를 buttoncollection 개체의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-269">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="b7e04-271">검사기 창에서 새로 만든 TextMeshPro 개체 (TMP) 라는 텍스트 (TMP)를 사용 하 여 해당 위치와 크기를 변경 하면 레이블이 단추 컬렉션 아래에 깔끔하게 배치 됩니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-271">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="b7e04-272">Rect Transform **Pos Y** 를-0.0425로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-272">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="b7e04-273">Rect 변환 **너비** 를 0.24으로 변경</span><span class="sxs-lookup"><span data-stu-id="b7e04-273">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="b7e04-274">Rect 변환 **높이** 를 0.024으로 변경</span><span class="sxs-lookup"><span data-stu-id="b7e04-274">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="b7e04-275">그런 다음 레이블을 반영 하도록 텍스트를 업데이트 하 고 텍스트를 레이블 내에 맞추기 위해 글꼴 속성을 선택 합니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-275">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="b7e04-276">텍스트 메시 Pro (스크립트) **텍스트** 를 단추 컬렉션으로 변경</span><span class="sxs-lookup"><span data-stu-id="b7e04-276">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="b7e04-277">텍스트 메시 Pro (스크립트) **글꼴 스타일** 을 굵게 변경</span><span class="sxs-lookup"><span data-stu-id="b7e04-277">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="b7e04-278">텍스트 메시 Pro (스크립트) **글꼴 크기** 를 0.2으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-278">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="b7e04-279">텍스트 메시 Pro (스크립트) **맞춤** 을 가운데 및 중간으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-279">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-기본](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="b7e04-281">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-281">Congratulations</span></span>

<span data-ttu-id="b7e04-282">이 자습서에서는 MRTK 프로필 설정을 복제, 사용자 지정 및 구성 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-282">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="b7e04-283">또한 HoloLens 2에서 추적 된 실습을 사용 하 여 이벤트를 트리거하는 단추와 상호 작용 하는 방법도 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-283">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="b7e04-284">마지막으로, MRTK의 그리드 개체 컬렉션 구성 요소 및 Unity의 텍스트 메시 Pro를 사용 하 여 간단한 UI 인터페이스를 만드는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="b7e04-284">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="b7e04-285">다음 자습서: 4. 동적 콘텐츠 배치 및 solvers 사용</span><span class="sxs-lookup"><span data-stu-id="b7e04-285">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
