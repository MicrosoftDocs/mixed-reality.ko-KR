---
title: 시작 자습서 - 3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376140"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a><span data-ttu-id="46470-105">3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성</span><span class="sxs-lookup"><span data-stu-id="46470-105">3. Creating user interface and configure Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

<span data-ttu-id="46470-106">이전 자습서에서는 HoloLens 2의 첫 번째 애플리케이션을 시작으로 MRTK(Mixed Reality Toolkit)에 제공되는 몇 가지 기능을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-106">In the previous tutorial, you learned about some of the capabilities the Mixed Reality Toolkit (MRTK) has to offer by starting your first application for the HoloLens 2.</span></span> <span data-ttu-id="46470-107">이 자습서에서는 UI 텍스트 패널에서 단추를 만들고 구성하는 방법과 기본 상호 작용(터치)을 사용하여 각 단추와 상호 작용하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="46470-107">In this tutorial you will learn how to create and organize buttons along with UI text panels, and use default interaction (touch) to interact with each button.</span></span> <span data-ttu-id="46470-108">개체의 크기, 사운드 및 색상 변경과 같은 간단한 작업과 효과도 추가로 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="46470-108">You will also explore the addition of simple actions and effects, such as changing the size, sound and color of objects.</span></span> <span data-ttu-id="46470-109">이 모듈에서는 [공간 매핑](spatial-mapping.md) 메시 시각화를 해제하는 것으로 시작하여 MRTK 프로필을 수정하는 방법에 대한 기본 개념을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-109">This module will introduce basic concepts about modifying MRTK profiles, starting with turning off the [spatial mapping](spatial-mapping.md) mesh visualization.</span></span>

## <a name="objectives"></a><span data-ttu-id="46470-110">목표</span><span class="sxs-lookup"><span data-stu-id="46470-110">Objectives</span></span>

* <span data-ttu-id="46470-111">Mixed Reality Toolkit 프로필 사용자 지정 및 구성</span><span class="sxs-lookup"><span data-stu-id="46470-111">Customize and configure Mixed Reality Toolkit profiles</span></span>
* <span data-ttu-id="46470-112">UI 요소 및 단추를 사용하여 홀로그램과 상호 작용</span><span class="sxs-lookup"><span data-stu-id="46470-112">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="46470-113">기본적인 손 추적 입력 및 상호 작용</span><span class="sxs-lookup"><span data-stu-id="46470-113">Basic hand-tracking input and interactions</span></span>

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a><span data-ttu-id="46470-114">Mixed-Reality Toolkit 프로필을 구성하는 방법(공간 인식 변경 표시 옵션)</span><span class="sxs-lookup"><span data-stu-id="46470-114">How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)</span></span>
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

<span data-ttu-id="46470-115">이 섹션에서는 기본 MRTK 프로필을 사용자 지정하고 구성하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="46470-115">In this section, you will learn how to customize and configure the default MRTK profiles.</span></span>

<span data-ttu-id="46470-116">이 예제에서는 공간 메시 관찰자의 설정을 변경하여 공간 인식 메시를 숨기는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="46470-116">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="46470-117">그러나 MRTK 프로필의 설정 또는 값을 사용자 지정할 때 이러한 원칙을 그대로 적용해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46470-117">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="46470-118">공간 인식 메시를 숨기기 위해 수행하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-118">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="46470-119">기본 구성 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="46470-119">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="46470-120">공간 인식 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="46470-120">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="46470-121">기본 공간 인식 시스템 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="46470-121">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="46470-122">기본 공간 인식 메시 관찰자 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="46470-122">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="46470-123">공간 인식 메시의 표시 유형 변경</span><span class="sxs-lookup"><span data-stu-id="46470-123">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="46470-124">기본적으로 MRTK 프로필은 편집할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-124">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="46470-125">이러한 기본 프로필 템플릿을 편집하려면 먼저 복제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-125">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="46470-126">중첩된 여러 프로필 레이어가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-126">There are several nested layers of profiles.</span></span> <span data-ttu-id="46470-127">따라서 하나 이상의 설정을 구성할 때 여러 프로필을 복제하여 편집하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="46470-127">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="46470-128">1. 기본 구성 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="46470-128">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="46470-129">구성 프로필은 최상위 수준 프로필입니다.</span><span class="sxs-lookup"><span data-stu-id="46470-129">The Configuration Profile is the top level profile.</span></span> <span data-ttu-id="46470-130">따라서 다른 프로필을 편집하려면 먼저 구성 프로필을 복제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-130">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="46470-131">다음과 같이 [계층 구조] 창에서 **MixedRealityToolkit** 개체를 선택한 상태로, [검사기] 창에서 Mixed Reality Toolkit **구성 프로필**을 **DefaultHoloLens2ConfigurationProfile**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-131">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, change the Mixed Reality Toolkit **Configuration Profile** to **DefaultHoloLens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

<span data-ttu-id="46470-133">다음과 같이 **MixedRealityToolkit** 개체를 선택한 상태로, [검사기] 창에서 **복제 및 사용자 지정** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46470-133">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

<span data-ttu-id="46470-135">다음과 같이 [프로필 복제] 창에서 **복제** 단추를 클릭하여 **DefaultHololens2ConfigurationProfile**의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46470-135">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

<span data-ttu-id="46470-137">이제 새로 만든 구성 프로필이 다음과 같이 장면의 구성 프로필로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="46470-137">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

<span data-ttu-id="46470-139">Unity 메뉴에서 **파일** > **저장**을 선택하여 장면을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-139">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="46470-140">자습서를 진행하는 동안 항상 작업을 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-140">Remember to save your work throughout the tutorial.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="46470-141">2. 공간 인식 시스템 사용</span><span class="sxs-lookup"><span data-stu-id="46470-141">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="46470-142">다음과 같이 [계층 구조] 창에서 **MixedRealityToolkit** 개체를 선택한 상태로, [검사기] 창에서 **공간 인식** 탭을 선택한 다음, **공간 인식 시스템 사용** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-142">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="46470-144">3. 기본 공간 인식 시스템 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="46470-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="46470-145">다음과 같이 **공간 인식** 탭에서 **복제** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46470-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

<span data-ttu-id="46470-147">다음과 같이 [프로필 복제] 창에서 **복제** 단추를 클릭하여 **DefaultMixedRealitySpatialAwarenessSystemProfile**의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46470-147">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

<span data-ttu-id="46470-149">이제 새로 만든 공간 인식 시스템 프로필이 다음과 같이 구성 프로필에 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="46470-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="46470-151">4. 기본 공간 인식 메시 관찰자 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="46470-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="46470-152">다음과 같이 **공간 인식** 탭을 선택한 상태로 **Windows Mixed Reality 공간 메시 관찰자** 섹션을 확장한 다음, **복제** 단추를 클릭하여 [프로필 복제] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="46470-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

<span data-ttu-id="46470-154">다음과 같이 [프로필 복제] 창에서 **복제** 단추를 클릭하여 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**의 편집 가능한 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46470-154">In the Clone Profile window, click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

<span data-ttu-id="46470-156">이제 새로 만든 공간 인식 메시 관찰자 프로필이 다음과 같이 공간 인식 시스템 프로필에 자동으로 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="46470-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="46470-158">5. 공간 인식 메시의 표시 유형 변경</span><span class="sxs-lookup"><span data-stu-id="46470-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="46470-159">다음과 같이 **공간 메시 관찰자 설정**에서 **표시 옵션**을 **폐색**으로 변경하여 공간 매핑 메시가 계속 작동하는 동안에도 보이지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still being functional:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="46470-161">공간 매핑 메시가 보이지 않더라도 여전히 존재하며 작동 중입니다.</span><span class="sxs-lookup"><span data-stu-id="46470-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="46470-162">예를 들어 실제 벽 뒤의 홀로그램처럼 공간 매핑 메시 뒤의 홀로그램은 보이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="46470-163">MRTK 프로필에서 설정을 수정하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="46470-164">보시는 것처럼, MRTK 설정을 사용자 지정하려면 먼저 기본 프로필의 복사본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-164">As you can see, in order to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="46470-165">기본 프로필은 편집이 불가능하므로, 기본 설정으로 되돌리고 싶을 때 항상 기본 프로필을 참조로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-165">Because the default profiles are not editable, you will always have them as reference if you want revert back to the default settings.</span></span> <span data-ttu-id="46470-166">MRTK 프로필 및 해당 아키텍처에 대한 자세한 내용은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [Mixed Reality Toolkit 프로필 구성 가이드](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46470-166">To learn more about MRTK profiles and their architecture, you can visit the [Mixed Reality Toolkit profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="hand-tracking-gestures-and-interactable-buttons"></a><span data-ttu-id="46470-167">손 추적 제스처 및 상호 작용 가능 단추</span><span class="sxs-lookup"><span data-stu-id="46470-167">Hand tracking gestures and interactable buttons</span></span>

<span data-ttu-id="46470-168">이 섹션에서는 손 추적을 사용하여 단추를 누르고 단추가 눌리면 동작을 발생시키는 이벤트를 트리거하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="46470-168">In this section, you will learn how to use hand tracking to press a button and trigger events to cause an action when the button is pressed.</span></span>

<span data-ttu-id="46470-169">이 예제에서는 단추가 눌리면 큐브의 색을 변경하고 단추 누르기가 해제되면 원래 색으로 되돌리는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="46470-169">This particular example will show you how to change the color of a cube when the button is pressed and change it back to it's original color when the button is released.</span></span> <span data-ttu-id="46470-170">다른 이벤트를 만들 때 이 원칙을 그대로 적용해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46470-170">However, you may follow these same principles to create other events.</span></span>

<span data-ttu-id="46470-171">큐브의 색을 변경하기 위해 수행하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-171">The main steps you will take to change the color of the cube are:</span></span>

1. <span data-ttu-id="46470-172">장면에 누를 수 있는 단추 프리팹 추가</span><span class="sxs-lookup"><span data-stu-id="46470-172">Add a pressable button prefab to the scene</span></span>
2. <span data-ttu-id="46470-173">장면에 큐브 추가</span><span class="sxs-lookup"><span data-stu-id="46470-173">Add a cube to the scene</span></span>
3. <span data-ttu-id="46470-174">InteractableOnPressReceiver 이벤트 형식 구성</span><span class="sxs-lookup"><span data-stu-id="46470-174">Configure the InteractableOnPressReceiver event type</span></span>
4. <span data-ttu-id="46470-175">On Press 이벤트를 수신하는 큐브 구성</span><span class="sxs-lookup"><span data-stu-id="46470-175">Configure the cube to receive the On Press event</span></span>
5. <span data-ttu-id="46470-176">On Press 이벤트에 의해 트리거되는 동작 정의</span><span class="sxs-lookup"><span data-stu-id="46470-176">Define the action to be triggered by the On Press event</span></span>
6. <span data-ttu-id="46470-177">On Release 이벤트를 수신하는 큐브 구성</span><span class="sxs-lookup"><span data-stu-id="46470-177">Configure the cube to receive the On Release event</span></span>
7. <span data-ttu-id="46470-178">On Release 이벤트에 의해 트리거되는 동작 정의</span><span class="sxs-lookup"><span data-stu-id="46470-178">Define the action to be triggered by the On Release event</span></span>
8. <span data-ttu-id="46470-179">편집기 내 시뮬레이션을 사용하여 단추 테스트</span><span class="sxs-lookup"><span data-stu-id="46470-179">Test the button using the in-editor simulation</span></span>

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a><span data-ttu-id="46470-180">1. 장면에 누를 수 있는 단추 프리팹 추가</span><span class="sxs-lookup"><span data-stu-id="46470-180">1. Add a pressable button prefab to the scene</span></span>

> [!TIP]
> <span data-ttu-id="46470-181"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">프리팹</a>은 Unity로 저장된 미리 구성된 GameObject이며 프로젝트 전체에서 재사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-181">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="46470-182">다음과 같이 **프로젝트 창**에서 **PressableButtonHoloLens2**를 검색하여 이 예제에 사용할 프리팹을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-182">In the **Project window**, search for **PressableButtonHoloLens2** to locate the prefab you will use for this example:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

<span data-ttu-id="46470-184">다음과 같이 **검색** 결과에서 **PressableButtonHoloLens2** 프리팹을 선택하고 **계층 구조** 창으로 **끌어** 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-184">In the **Search** result, select the **PressableButtonHoloLens2** prefab and **drag** it into the **Hierarchy** window to add it to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="46470-186">아래 이미지처럼 장면을 표시하려면 [계층 구조] 창에서 PressableButtonHoloLens2 개체를 두 번 클릭하여 포커스를 가져온 다음, 장면 창의 오른쪽 위 모서리에 있는 <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">장면 Gizmo</a>를 사용하여 시야각이 전방 Z 축을 따라 이동하도록 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-186">To display your scene as shown in the image below, double-click the PressableButtonHoloLens2 object in the Hierarchy window to bring it into focus, then use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis.</span></span>

<span data-ttu-id="46470-187">**PressableButtonHoloLens2** 개체를 선택한 상태로 **검사기** 창에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-187">With the **PressableButtonHoloLens2** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="46470-188">카메라 앞에 배치되도록, 즉, 원점에 배치되도록 변환 **위치**를 변경합니다(예: x = 0, y = 0, z = 0.5).</span><span class="sxs-lookup"><span data-stu-id="46470-188">Change its Transform **Position** so it's positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="46470-190">일반적으로 Unity의 1 위치 단위는 실제 세계의 1미터와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-190">In general, 1 position unit in Unity is roughly equivalent to 1 meter in the physical world.</span></span> <span data-ttu-id="46470-191">하지만 여기에는 예외가 있습니다. 예를 들어 개체가 크기 조정된 개체의 자식인 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="46470-191">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span>

### <a name="2-add-a-cube-to-the-scene"></a><span data-ttu-id="46470-192">2. 장면에 큐브 추가</span><span class="sxs-lookup"><span data-stu-id="46470-192">2. Add a cube to the scene</span></span>

<span data-ttu-id="46470-193">다음과 같이 [계층 구조] 창 내부의 빈 지점을 마우스 오른쪽 단추로 클릭하고 **3D 개체** > **큐브**를 선택하여 장면에 큐브를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-193">Right-click on an empty spot inside the Hierarchy window and select **3D Object** > **Cube** to add a cube to your scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

<span data-ttu-id="46470-195">**Cube** 개체를 선택한 상태로 **검사기** 창에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-195">With the **Cube** object still selected, in the **Inspector** window:</span></span>

* <span data-ttu-id="46470-196">누를 수 있는 단추 근처에 있지만 겹치지는 않도록 **변환** 위치를 변경합니다(예: x = 0, y = 0.04, z = 0.5).</span><span class="sxs-lookup"><span data-stu-id="46470-196">Change its Transform **Position** so its located near the pressable button, but not overlapping with it, for example, x = 0, y = 0.04, and z = 0.5</span></span>
* <span data-ttu-id="46470-197">변환 **배율**을 적절한 크기로 변경합니다(예: x = 0.02, y = 0.02, z = 0.02).</span><span class="sxs-lookup"><span data-stu-id="46470-197">Change its Transform **Scale** to a suitable size, for example, x = 0.02, y = 0.02, and z = 0.02</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a><span data-ttu-id="46470-199">3. InteractableOnPressReceiver 이벤트 형식 구성</span><span class="sxs-lookup"><span data-stu-id="46470-199">3. Configure the InteractableOnPressReceiver event type</span></span>

<span data-ttu-id="46470-200">다음과 같이 [계층 구조] 창에서 **PressableButtonHoloLens2** 개체를 선택하고, **검사기** 창 **햄버거 메뉴**에서 **모든 구성 요소 축소**를 선택하여 이 개체의 모든 구성 요소에 대한 개요를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="46470-200">In the Hierarchy window, select the **PressableButtonHoloLens2** object, then in the **Inspector** window **hamburger menu**, select **Collapse All Components** to get an overview of all components on this object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

<span data-ttu-id="46470-202">다음과 같이 **Interactable(스크립트)** 구성 요소를 확장하고, **이벤트** > **수신기** 섹션을 찾아 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-202">Expand the **Interactable (Script)** component, then locate and expand the **Events** > **Receivers** section:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

<span data-ttu-id="46470-204">다음과 같이 **이벤트 추가** 단추를 클릭하여 이벤트 수신기 형식 **InteractableOnPressReceiver**의 새 이벤트 수신기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46470-204">Click the **Add Event** button, to create a new event receiver of Event Receiver Type **InteractableOnPressReceiver**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> <span data-ttu-id="46470-206">InteractableOnPressReceiver라는 이벤트 수신기 형식을 사용하면 추적 손이 단추를 누를 때 누름 이벤트에 대해 단추가 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-206">The Event Receiver Type named InteractableOnPressReceiver allows the button to respond to a pressed event when a tracked hand presses the button.</span></span>

<span data-ttu-id="46470-207">새로 만든 이벤트 수신기의 **상호 작용 필터**를 **근거리 및 원거리**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-207">For the newly created event receiver, change the **Interaction Filter** to **Near and Far**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a><span data-ttu-id="46470-209">4. On Press 이벤트를 수신하는 큐브 구성</span><span class="sxs-lookup"><span data-stu-id="46470-209">4. Configure the cube to receive the On Press event</span></span>

<span data-ttu-id="46470-210">다음과 같이 [계층 구조] 창에서 **큐브**를 **클릭**하여 **On Press ()** 이벤트의 **이벤트 속성** 개체 필드로 끌어 놓아 큐브를 On Press () 이벤트의 수신기로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-210">From the Hierarchy window, **click-and-drag** the **Cube** into the **Event Properties** object field for the **On Press ()** event to assign the Cube as a receiver of the On Press () event:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a><span data-ttu-id="46470-212">5. On Press 이벤트에 의해 트리거되는 동작 정의</span><span class="sxs-lookup"><span data-stu-id="46470-212">5. Define the action to be triggered by the On Press event</span></span>

<span data-ttu-id="46470-213">다음과 같이 동작 드롭다운을 클릭합니다. 현재는 **함수 없음**이 할당되었습니다. 그리고 **MeshRenderer** > **재질 재질**을 선택하여 On Press () 이벤트가 트리거될 때 큐브의 재질 속성을 변경하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-213">Click the action dropdown, currently assigned **No Function**, and select **MeshRenderer** > **Material material** to set the Cube's material property to be changed when the On Press () event is triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

<span data-ttu-id="46470-215">다음과 같이 재질 필드 옆에 있는 작은 **원** 아이콘을 클릭하여 [재질 선택] 창을 엽니다. 현재 이 필드는 **없음(재질)** 으로 채워져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-215">Click the small **circle** icon next to the material field, currently populated with **None (Material)**, to open the Select Material window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

<span data-ttu-id="46470-217">다음과 같이 [재질 선택] 창에서 **MRTK_Standard**를 **검색**하여 적절한 재질을 선택합니다. 예를 들어 **MRTK_Standard_Cyan**을 선택할 경우 단추를 누르면 큐브의 색이 녹청으로 변합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-217">In the Select Material window, **search** for **MRTK_Standard** and select a suitable material, for example, **MRTK_Standard_Cyan** so the Cube's color changes to cyan when the button is pressed:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a><span data-ttu-id="46470-219">6. On Release 이벤트를 수신하는 큐브 구성</span><span class="sxs-lookup"><span data-stu-id="46470-219">6. Configure the cube to receive the On Release event</span></span>

<span data-ttu-id="46470-220">On Release 이벤트에 대해 4단계를 **반복**하여 **큐브**를 **On Release ()** 이벤트의 수신자로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-220">**Repeat** Step 4 for the On Release event to assign the **Cube** as a receiver of the **On Release ()** event.</span></span>

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a><span data-ttu-id="46470-221">7. On Release 이벤트에 의해 트리거되는 동작 정의</span><span class="sxs-lookup"><span data-stu-id="46470-221">7. Define the action to be triggered by the On Release event</span></span>

<span data-ttu-id="46470-222">다음과 같이 On Release 이벤트에 대해 5단계를 **반복**하되, 단추 누르기가 해제되면 큐브의 색이 원래의 밝은 회색으로 돌아가도록 **MRTK_Standard_LightGray** 재질을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-222">**Repeat** Step 5 for the On Release event, but choose the **MRTK_Standard_LightGray** material so the Cube's color returns to its original light gray color when the button is released:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a><span data-ttu-id="46470-224">8. 편집기 내 시뮬레이션을 사용하여 단추 테스트</span><span class="sxs-lookup"><span data-stu-id="46470-224">8. Test the button using the in-editor simulation</span></span>

<span data-ttu-id="46470-225">**재생** 단추를 눌러 게임 모드로 전환한 다음, 편집기 내 입력 시뮬레이션을 사용하여 새로 구성된 단추를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-225">Press the **Play** button to enter Game mode and use the in-editor input simulation to test your newly configured button.</span></span>

<span data-ttu-id="46470-226">단추를 누르지 않음(스페이스바 + 마우스 스크롤 휠 뒤로):</span><span class="sxs-lookup"><span data-stu-id="46470-226">Button not pressed (spacebar + mouse scroll wheel backward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

<span data-ttu-id="46470-228">단추를 누름(스페이스바 + 마우스 스크롤 휠 앞으로):</span><span class="sxs-lookup"><span data-stu-id="46470-228">Button pressed (spacebar + mouse scroll wheel forward):</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> <span data-ttu-id="46470-230">편집기 내 입력 시뮬레이션을 사용하는 방법은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [편집기 내 손 입력 시뮬레이션을 사용하여 장면 테스트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46470-230">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a><span data-ttu-id="46470-231">MRTK의 Grid Object Collection을 사용하여 단추 패널 만들기</span><span class="sxs-lookup"><span data-stu-id="46470-231">Creating a panel of buttons using MRTK's Grid Object Collection</span></span>

<span data-ttu-id="46470-232">이 섹션에서는 MRTK의 Grid Object Collection 도구를 사용하여 여러 단추를 깔끔한 사용자 인터페이스로 자동 정렬하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="46470-232">In this section, you will learn how to automatically align multiple buttons into a neat user interface by using the MRTK's Grid Object Collection tool.</span></span>

<span data-ttu-id="46470-233">이 예제에서는 단추 5개가 가로로 정렬된 패널을 만드는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="46470-233">This particular example will show you how to a create a panel with five buttons aligned horizontally.</span></span> <span data-ttu-id="46470-234">다른 레이아웃을 만들 때 이 원칙을 그대로 적용해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46470-234">However, you may follow these same principles to create other layouts.</span></span>

<span data-ttu-id="46470-235">이를 위해 수행할 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-235">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="46470-236">단추 개체를 부모 개체의 부모로 지정</span><span class="sxs-lookup"><span data-stu-id="46470-236">Parent the button objects to a parent object</span></span>
2. <span data-ttu-id="46470-237">Grid Object Collection(스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="46470-237">Add and configure the Grid Object Collection (Script) component</span></span>
3. <span data-ttu-id="46470-238">편집기 내 시뮬레이션을 사용하여 단추 테스트</span><span class="sxs-lookup"><span data-stu-id="46470-238">Test the buttons using the in-editor simulation</span></span>

### <a name="1-parent-the-button-objects-to-a-parent-object"></a><span data-ttu-id="46470-239">1. 단추 개체를 부모 개체의 부모로 지정</span><span class="sxs-lookup"><span data-stu-id="46470-239">1. Parent the button objects to a parent object</span></span>

<span data-ttu-id="46470-240">다음과 같이 [계층 구조] 창 내부의 빈 지점을 마우스 오른쪽 단추로 클릭하고 **빈 항목 만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-240">Right-click on an empty spot inside the Hierarchy window and select **Create Empty**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

<span data-ttu-id="46470-242">다음과 같이 새로 만든 개체를 마우스 오른쪽 단추로 클릭하고, **이름 바꾸기**를 선택하여 적절한 이름(예: **ButtonCollection**)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-242">Right-click on the newly created object, select **Rename**, and give it a suitable name, for example, **ButtonCollection**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

<span data-ttu-id="46470-244">다음과 같이 **PressableButtonHoloLens2** 개체를 선택하고 **ButtonCollection** 개체 위로 **끌어 놓아** ButtonCollection 개체의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46470-244">Select the **PressableButtonHoloLens2** object and **drag** it on top of the **ButtonCollection** object to make it a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

<span data-ttu-id="46470-246">다음과 같이 **PressableButtonHoloLens2** 개체를 마우스 오른쪽 단추로 클릭하고 **복제**를 선택하여 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46470-246">Right-click the **PressableButtonHoloLens2** object and select **Duplicate** to create a copy of it:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

<span data-ttu-id="46470-248">총 5개의 PressableButtonHoloLens2 개체가 생길 때까지 이 단계를 4회 더 **반복**합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-248">**Repeat** this step four more times until you have a total of five PressableButtonHoloLens2 objects.</span></span>

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a><span data-ttu-id="46470-249">2. Grid Object Collection(스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="46470-249">2. Add and configure the Grid Object Collection (Script) component</span></span>

<span data-ttu-id="46470-250">다음과 같이 [계층 구조] 창에서 ButtonCollection 개체를 선택하고 [검사기] 창에서 **구성 요소 추가** 단추를 클릭한 다음, **Grid Object Collection**을 검색하고 선택하여 ButtonCollection 개체에 Grid Object Collection(스크립트) 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-250">With the ButtonCollection object selected in the Hierarchy window, in the Inspector window, click the **Add Component** button, then search for and select **Grid Object Collection** to add a Grid Object Collection (Script) component to the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

<span data-ttu-id="46470-252">다음과 같이 Grid Object Collection(스크립트)을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-252">Configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="46470-253">모든 단추가 단일 행에 정렬되도록 **숫자 행**을 1로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-253">Change **Num Rows** to 1 to have all buttons aligned on one single row</span></span>
* <span data-ttu-id="46470-254">단추가 행 내부에 있도록 **셀 너비**를 0.05로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-254">Change **Cell Width** to 0.05 to space out the buttons within the row</span></span>

<span data-ttu-id="46470-255">그런 다음, 다음과 같이 **컬렉션 업데이트** 단추를 클릭하여 새 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-255">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> <span data-ttu-id="46470-257">방금 적용한 구성 변경 내용은 단추를 단일 행에 배치하려는 목표를 달성하는 데 필요한 최소한의 변경 내용을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="46470-257">The configuration changes you just applied represent the minimum changes required to achieve the objective of placing the buttons in a single row.</span></span> <span data-ttu-id="46470-258">그러나 이후 프로젝트에서 부모 개체와 자식 개체의 방향 등의 요소에 따라 방향 유형과 같은 다른 설정을 조정해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-258">However, in future projects, depending on factors such as, for example, the orientation of the parent and child objects, you might need to adjust other settings such as, for example, the Orient Type.</span></span> <span data-ttu-id="46470-259">MRTK의 Grid Object Collection에 대한 자세한 내용은 [MRTK 설명서 포털](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)의 [개체 컬렉션 스크립트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) 가이드를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="46470-259">To learn more about MRTK's Grid Object Collection, you can visit the [Object collection scripts](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

<span data-ttu-id="46470-260">[계층 구조] 창에서 ButtonCollection 개체를 선택한 상태로, 자식 단추 개체가 카메라 앞에 배치되도록, 즉, 원점에 배치되도록 [검사기] 창에서 ButtonCollection 개체의 변환 **위치**를 변경합니다(예: x = 0, y = 0, z = 0.5).</span><span class="sxs-lookup"><span data-stu-id="46470-260">With the ButtonCollection object still selected in the Hierarchy window, in the Inspector window, change the ButtonCollection object's Transform **Position** so its child button objects are positioned in front of the camera, which is positioned at origin, for example, x = 0, y = 0, and z = 0.5:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> <span data-ttu-id="46470-262">위의 [손 추적 제스처 및 상호 작용 가능 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 섹션에서 장면에 PressableButtonHoloLens2 프리팹을 처음 추가할 때 프리팹을 카메라 앞에 배치한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="46470-262">When you first added the PressableButtonHoloLens2 prefab to the scene in the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) section above, you positioned it in front of the camera.</span></span> <span data-ttu-id="46470-263">그러나 Grid Object Collection은 직계 자식 개체의 위치를 제어하기 때문에 PressableButtonHoloLens2 자식 개체의 Z 위치는 부모 값이 0일 때 Grid Object Collection의 기본 거리에 따라 0으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="46470-263">However, because the Grid Object Collection controls its immediate child objects' position, the PressableButtonHoloLens2 child objects' Z Position were reset to 0 according to the Grid Object Collection's default Distance from parent value of 0.</span></span> <span data-ttu-id="46470-264">이러한 이유로, 그리고 부모/자식 위치 관계를 체계적으로 관리하기 위해, PressableButtonHoloLens2 자식 개체를 앞으로 이동하도록 부모 값으로부터의 거리를 구성하는 대신 부모 ButtonCollection 개체의 위치를 앞으로 이동했습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-264">This, and to keep the parent/child positional relationship organized, is why we moved the parent ButtonCollection object's position forward instead of configuring the Distance from parent value to move the PressableButtonHoloLens2 child objects forward.</span></span>

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a><span data-ttu-id="46470-265">3. 편집기 내 시뮬레이션을 사용하여 단추 테스트</span><span class="sxs-lookup"><span data-stu-id="46470-265">3. Test the buttons using the in-editor simulation</span></span>

<span data-ttu-id="46470-266">다음과 같이 [재생] 단추를 눌러 게임 모드로 전환한 다음, 편집기 내 입력 시뮬레이션을 사용하여 새로 만든 단추 패널에서 각 단추를 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-266">Press the Play button to enter Game mode and use the in-editor input simulation to test each of the buttons in in your newly created panel of buttons:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> <span data-ttu-id="46470-268">현재는 5개 단추 중 하나를 누르면 큐브 색이 녹청으로 변합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-268">Currently, when your press any of the five buttons, the cube color changes to cyan.</span></span> <span data-ttu-id="46470-269">보다 흥미로운 환경을 만들려면 방금 배운 내용을 사용하여 큐브를 다른 색으로 변경하도록 각 단추를 구성해 보세요.</span><span class="sxs-lookup"><span data-stu-id="46470-269">To make the experience more interesting, use what you just learn to configure each button to change the cube to a different color.</span></span>

## <a name="adding-text-into-your-scene"></a><span data-ttu-id="46470-270">장면에 텍스트 추가</span><span class="sxs-lookup"><span data-stu-id="46470-270">Adding text into your scene</span></span>

<span data-ttu-id="46470-271">이 섹션에서는 이전 자습서의 [TextMesh Pro 필수 리소스 가져오기](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) 섹션에서 준비한 Unity의 TextMesh Pro를 사용하여 혼합 현실 환경에 텍스트를 추가하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="46470-271">In this section, you will learn how to add text to your mixed reality experiences using Unity's TextMesh Pro, which you prepared in the [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) section of the previous tutorial.</span></span>

<span data-ttu-id="46470-272">이 예제에서는 이전 섹션에서 만든 단추 컬렉션 아래에 간단한 레이블을 추가할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="46470-272">In this particular example, you will add a simple label underneath the button collection you created in the previous section.</span></span>

<span data-ttu-id="46470-273">다음과 같이 ButtonCollection 개체를 마우스 오른쪽 단추로 클릭하고 **3D 개체** > **텍스트 - TextMeshPro**를 선택하여 TextMeshPro 개체를 ButtonCollection 개체의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46470-273">Right-click on the ButtonCollection object and select **3D Object** > **Text - TextMeshPro** to create a TextMeshPro object as a child of the ButtonCollection object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

<span data-ttu-id="46470-275">새로 만든 텍스트(TMP)라는 TextMeshPro 개체를 선택한 상태로, 레이블이 깔끔하게 단추 컬렉션 아래에 배치되도록 다음 예제처럼 [검사기] 창에서 위치와 크기를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-275">With the newly created TextMeshPro object, named Text (TMP), still selected, in the Inspector window change its position and size so the label is placed neatly underneath the button collection, for example:</span></span>

* <span data-ttu-id="46470-276">사각형 변환 **세로 위치**를 -0.0425로 변경</span><span class="sxs-lookup"><span data-stu-id="46470-276">Change the Rect Transform **Pos Y** to -0.0425</span></span>
* <span data-ttu-id="46470-277">사각형 변환 **너비**를 0.24로 변경</span><span class="sxs-lookup"><span data-stu-id="46470-277">Change the Rect Transform **Width** to 0.24</span></span>
* <span data-ttu-id="46470-278">사각형 변환 **높이**를 0.024로 변경</span><span class="sxs-lookup"><span data-stu-id="46470-278">Change the Rect Transform **Height** to 0.024</span></span>

<span data-ttu-id="46470-279">그리고 다음 예제처럼 레이블의 내용을 반영하도록 텍스트를 업데이트하고, 텍스트가 레이블 내에서 잘 어울리도록 글꼴 속성을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-279">Then update the text to reflect what the label is for and choose font properties so the text fits within the label, for example:</span></span>

* <span data-ttu-id="46470-280">Text Mesh Pro(스크립트) **텍스트**를 단추 컬렉션으로 변경</span><span class="sxs-lookup"><span data-stu-id="46470-280">Change the Text Mesh Pro (Script) **Text** to Button Collection</span></span>
* <span data-ttu-id="46470-281">Text Mesh Pro(스크립트) **글꼴 스타일**을 [굵게]로 변경</span><span class="sxs-lookup"><span data-stu-id="46470-281">Change the Text Mesh Pro (Script) **Font Style** to Bold</span></span>
* <span data-ttu-id="46470-282">Text Mesh Pro(스크립트) **글꼴 크기**를 0.2로 변경</span><span class="sxs-lookup"><span data-stu-id="46470-282">Change the Text Mesh Pro (Script) **Font Size** to 0.2</span></span>
* <span data-ttu-id="46470-283">Text Mesh Pro(스크립트) **맞춤**을 [가운데] 및 [중간]으로 변경</span><span class="sxs-lookup"><span data-stu-id="46470-283">Change the Text Mesh Pro (Script) **Alignment** to Center and Middle</span></span>

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a><span data-ttu-id="46470-285">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="46470-285">Congratulations</span></span>

<span data-ttu-id="46470-286">이 자습서에서는 MRTK 프로필 설정을 복제, 사용자 지정 및 구성하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-286">In this tutorial, you learned how to clone, customize, and configure an MRTK profile setting.</span></span> <span data-ttu-id="46470-287">HoloLens 2에서 추적 손을 사용하여 단추와 상호 작용하여 이벤트를 트리거하는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-287">You also learned how to interact with buttons to trigger events using tracked hands on the HoloLens 2.</span></span> <span data-ttu-id="46470-288">마지막으로 MRTK의 Grid Object Collection 구성 요소와 Unity의 Text Mesh Pro를 사용하여 간단한 UI 인터페이스를 만드는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="46470-288">Finally, you learned how to create a simple UI interface using the MRTK's Grid Object Collection component and Unity's Text Mesh Pro.</span></span>

[<span data-ttu-id="46470-289">다음 자습서: 4. 동적 콘텐츠 배치 및 해결기 사용</span><span class="sxs-lookup"><span data-stu-id="46470-289">Next Tutorial: 4. Placing dynamic content and using solvers</span></span>](mrlearning-base-ch3.md)
