---
title: 시작 자습서 - 6. 사용자 인터페이스 만들기
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여 줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: a7c4ea140a9c27f1a92680da6bbe1fb3a4bdc233
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306249"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="56679-105">6. 사용자 인터페이스 만들기</span><span class="sxs-lookup"><span data-stu-id="56679-105">6. Creating user interfaces</span></span>

## <a name="overview"></a><span data-ttu-id="56679-106">개요</span><span class="sxs-lookup"><span data-stu-id="56679-106">Overview</span></span>

<span data-ttu-id="56679-107">이 자습서에서는 Unity의 TextMeshPro 구성 요소와 함께 MRTK의 단추와 메뉴 프리팹을 사용하여 간단한 사용자 인터페이스를 만드는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="56679-107">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="56679-108">또한 이벤트를 트리거하도록 단추를 구성하고, 사용자에게 추가 정보를 제공하기 위해 동적 도구 설명 UI 요소를 추가하는 방법에 대해서도 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="56679-108">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="56679-109">목표</span><span class="sxs-lookup"><span data-stu-id="56679-109">Objectives</span></span>

* <span data-ttu-id="56679-110">컬렉션에서 단추를 구성하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="56679-110">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="56679-111">MRTK의 메뉴 프리팹을 사용하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="56679-111">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="56679-112">UI 요소 및 단추를 사용하여 홀로그램과 상호 작용하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="56679-112">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="56679-113">텍스트 요소를 추가하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="56679-113">Learn how to add text elements</span></span>
* <span data-ttu-id="56679-114">개체에 대한 도구 설명을 동적으로 생성하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="56679-114">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="56679-115">정적 단추 패널 만들기</span><span class="sxs-lookup"><span data-stu-id="56679-115">Creating a static panel of buttons</span></span>

<span data-ttu-id="56679-116">[계층 구조] 창에서 마우스 오른쪽 단추로 **RoverExplorer** 개체를 클릭하고, **빈 항목 만들기**를 선택하여 빈 개체를 RoverExplorer의 자식으로 추가하고, 개체 이름을 **Buttons**로 지정하고, **변환** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-116">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="56679-117">**위치**: X = -0.6, Y = 0.036, Z = -0.5</span><span class="sxs-lookup"><span data-stu-id="56679-117">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="56679-118">**회전**: X = 90, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="56679-118">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="56679-119">**배율**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="56679-119">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="56679-121">[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** 폴더로 차례로 이동하고, **PressableRoundButton** 프리팹을 클릭하여 **Buttons** 개체로 끈 다음, 마우스 오른쪽 단추로 PressableRoundButton을 클릭하고, **중복**을 선택하여 복사본을 만듭니다. 총 세 개의 PressableRoundButton 개체 복사본을 만들 때까지 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="56679-123">[계층 구조] 창에서 **Buttons** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **GridObjectCollection** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-123">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="56679-124">**정렬 유형**: 자식 순서</span><span class="sxs-lookup"><span data-stu-id="56679-124">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="56679-125">**레이아웃**: 수평</span><span class="sxs-lookup"><span data-stu-id="56679-125">**Layout**: Horizontal</span></span>
* <span data-ttu-id="56679-126">**셀 너비**: 0.2</span><span class="sxs-lookup"><span data-stu-id="56679-126">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="56679-127">**앵커**: 왼쪽 가운데</span><span class="sxs-lookup"><span data-stu-id="56679-127">**Anchor**: Middle Left</span></span>

<span data-ttu-id="56679-128">그런 다음, **컬렉션 업데이트** 단추를 클릭하여 Buttons 개체의 자식 개체에 대한 위치를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-128">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="56679-130">[계층 구조] 창에서 단추 이름을 **Hints**, **Explode** 및 **Reset**으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-130">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="56679-131">각 단추에 대해 **SeeItSayItLabel** > **TextMeshPro** 자식 개체를 차례로 선택한 다음, [검사기] 창에서 각 **TextMeshPro - 텍스트** 구성 요소 텍스트를 단추 이름과 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-131">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="56679-133">완료되면 Buttons 개체의 자식 개체를 접습니다.</span><span class="sxs-lookup"><span data-stu-id="56679-133">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="56679-134">[계층 구조] 창에서 **Hints** 단추 개체를 선택한 다음, [검사기] 창에서 Interactable **OnClick ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-134">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="56679-135">**RoverAssembly** 개체를 **없음(개체)** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-135">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="56679-136">**함수 없음** 드롭다운에서 **PlacementHintsController** > **TogglePlacementHints ()** 를 차례로 선택하여 이 함수를 이벤트가 트리거될 때 실행할 작업으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-136">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-5.png)

<span data-ttu-id="56679-138">[계층 구조] 창에서 **Explode** 단추 개체를 선택한 다음, [검사기] 창에서 Interactable **OnClick ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-138">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="56679-139">**RoverAssembly** 개체를 **없음(개체)** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-139">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="56679-140">**함수 없음** 드롭다운에서 **ExplodedViewController** > **ToggleExplodedView ()** 를 차례로 선택하여 이 함수를 이벤트가 트리거될 때 실행할 작업으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-140">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="56679-142">[재생] 단추를 눌러 게임 모드를 시작한 다음, 스페이스 바 단추를 길게 눌러 손을 활성화하고, 마우스를 사용하여 **Hints** 단추를 눌러 배치 힌트 개체의 표시 유형을 설정/해제합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-142">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="56679-144">그리고 **Explode** 단추를 눌러 분해된 보기를 설정/해제합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-144">and the **Explode** button to toggle the exploded view on and off:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="56679-146">사용자를 따르는 동적 메뉴 만들기</span><span class="sxs-lookup"><span data-stu-id="56679-146">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="56679-147">[프로젝트] 창에서 **Assets** > **MRTK** > **SDK** > **UX** > **Prefabs** > **Menus** 폴더로 차례로 이동하고, **NearMenu4x1** 프리팹을 클릭하여 [계층 구조] 창으로 끈 다음, 해당 변환 **위치**를 X = 0, Y = -0.4, Z = 0으로 설정하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-147">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="56679-148">**SolverHandler** 구성 요소의 **추적 대상 형식**이 **Head**로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-148">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="56679-149">**RadialView** 해결기 구성 요소 옆에 있는 확인란을 선택하여 기본적으로 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-149">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="56679-151">[계층 구조] 창에서 개체 이름을 **Menu**로 바꾼 다음, 해당 **ButtonCollection** 자식 개체를 펼쳐서 4개의 단추를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-151">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="56679-153">첫 번째 단추의 이름을 **Indicator**로 바꾼 다음, [검사기] 창에서 **단추 구성 도우미(스크립트)** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-153">Rename the first button to **Indicator**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="56679-154">**기본 레이블 텍스트**를 단추 이름과 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-154">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="56679-155">**Indicator** 개체를 **없음(개체)** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-155">Assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="56679-156">**함수 없음** 드롭다운에서 **GameObject** > **SetActive(부울)** 를 차례로 선택하여 이 함수를 이벤트가 트리거될 때 실행할 작업으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-156">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="56679-157">인수 확인란이 **선택되어** 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-157">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="56679-158">**아이콘**을 '검색' 아이콘으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-158">Change the **Icon** to the 'search' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="56679-160">[계층 구조] 창에서 **Indicator** 개체를 선택한 다음, [검사기] 창에서 이름 옆에 있는 확인란을 선택 취소하여 기본적으로 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-160">In the Hierarchy window, select the **Indicator** object, then in the Inspector window, uncheck the checkbox next to its name to make it inactive by default:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="56679-162">이제 앱이 시작되면 Indicator가 기본적으로 사용하지 않도록 설정되며, Indicator 단추를 눌러 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56679-162">Now, when the app starts, the Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="56679-163">두 번째 단추의 이름을 **TapToPlace**로 바꾼 다음, [검사기] 창에서 **단추 구성 도우미(스크립트)** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-163">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="56679-164">**기본 레이블 텍스트**를 단추 이름과 일치하도록 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-164">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="56679-165">RoverExplorer > **RoverAssembly** 개체를 **없음(개체)** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-165">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="56679-166">**함수 없음** 드롭다운에서 **TapToPlace** > **부울 사용**을 차례로 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-166">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="56679-167">인수 확인란이 **선택되어** 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-167">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="56679-168">**아이콘**을 '광선이 있는 손' 아이콘으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-168">Change the **Icon** to the 'hand with ray' icon</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="56679-170">[계층 구조] 창에서 **RoverAssembly** 개체를 선택한 다음, [검사기] 창에서 다음과 같이 **탭하여 위치 지정(스크립트)** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-170">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="56679-171">이름 옆에 있는 확인란을 선택 취소하여 기본적으로 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-171">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="56679-172">**On Placing Started ()** 이벤트 섹션에서 **+** 아이콘을 클릭하여 새 이벤트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-172">In the **On Placing Started ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="56679-173">RoverExplorer > **RoverAssembly** 개체를 **없음(개체)** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-173">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="56679-174">**함수 없음** 드롭다운에서 **TapToPlace** > **부울 사용**을 차례로 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-174">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="56679-175">인수 확인란이 **선택 취소되어** 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-175">Verify that the argument checkbox is **unchecked**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="56679-177">이제 앱이 시작되면 Tap to Place(탭하여 위치 지정) 기능이 기본적으로 사용하지 않도록 설정되며, Tap to Place 단추를 눌러 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56679-177">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="56679-178">또한 탭하여 위치 지정이 완료되면 자체적으로 사용하지 않도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="56679-178">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="56679-179">장면에 텍스트 추가</span><span class="sxs-lookup"><span data-stu-id="56679-179">Adding text to the scene</span></span>

<span data-ttu-id="56679-180">[계층 구조] 창에서 마우스 오른쪽 단추로 **Table** 개체를 클릭하고, **3D 개체** > **텍스트 - TextMeshPro**를 차례로 선택하여 텍스트 개체를 Table 개체의 자식으로 추가한 다음, [검사기] 창에서 **사각형 변환** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-180">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="56679-181">**세로 위치**를 1로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-181">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="56679-182">**너비**를 1로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-182">Change **Width** to 1</span></span>
* <span data-ttu-id="56679-183">**높이**를 1로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-183">Change **Height** to 1</span></span>
* <span data-ttu-id="56679-184">**회전 X**를 90으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-184">Change **Rotation X** to 90</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="56679-186">그런 다음, **TextMeshPro - 텍스트** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-186">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="56679-187">**텍스트**를 Rover Explorer로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-187">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="56679-188">**글꼴 스타일**을 [굵게]로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-188">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="56679-189">**글꼴 크기**를 1로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-189">Change **Font Size** to 1</span></span>
* <span data-ttu-id="56679-190">추가 설정 > **여백**을 0.03으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-190">Change Extra Settings > **Margins** to 0.03</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="56679-192">도구 설명 추가</span><span class="sxs-lookup"><span data-stu-id="56679-192">Adding tooltips</span></span>

<span data-ttu-id="56679-193">[프로젝트] 창에서 **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** 폴더로 차례로 이동하여 도구 설명 프리팹을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="56679-193">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="56679-195">[계층 구조] 창에서 RoverExplorer > **RoverParts** 개체를 차례로 펼치고, 해당 자식 로버 부품 개체를 모두 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **ToolTipSpawner** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-195">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="56679-196">사용자가 도구 설명이 표시되는 부품을 살펴볼 수 있도록 하려면 **포커스 사용** 확인란이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-196">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="56679-197">[프로젝트] 창에서 **한 줄 도구 설명** 프리팹을 **도구 설명 프리팹** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-197">Assign the **Simple Line ToolTip** prefab from the Project window to the **Tool Tip Prefab** field</span></span>
* <span data-ttu-id="56679-198">도구 설명 재정의 설정 > **설정 모드**를 **재정의**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-198">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="56679-199">도구 설명 재정의 설정 > **수동 피벗 위치 Y 위치**를 **1.5**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-199">Change the ToolTip Override Settings > **Manual Pivot Location Position Y** to **1.5**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="56679-201">[계층 구조] 창에서 첫 번째 로버 부품인 RoverParts > **Camera_Part**를 차례로 선택하고, **ToolTipSpawner** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-201">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="56679-202">부품 이름(예: **Camera**)을 반영하도록 **도구 설명 텍스트**를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-202">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="56679-204">각 로버 부품 개체에 대해 이 단계를 **반복**하여 **ToolTipSpawner** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-204">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="56679-205">**Generator_Part**에 대한 **도구 설명 텍스트**를 **발전기**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-205">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="56679-206">**Lights_Part**에 대한 **도구 설명 텍스트**를 **조명**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-206">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="56679-207">**UHFAntenna_Part**에 대한 **도구 설명 텍스트**를 **UHF 안테나** 필드로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-207">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="56679-208">**Spectrometer_Part**에 대한 **도구 설명 텍스트**를 **분광계**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-208">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="56679-209">[재생] 단추를 눌러 게임 모드를 시작한 다음, 시선이 부품 중 하나에 적중하여 해당 부품에 대한 도구 설명이 표시될 때까지 마우스 오른쪽 단추를 누른 채 마우스를 움직입니다.</span><span class="sxs-lookup"><span data-stu-id="56679-209">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![mr-learning-base](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="56679-211">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="56679-211">Congratulations</span></span>

<span data-ttu-id="56679-212">이 자습서에서는 Unity의 TextMeshPro 구성 요소와 함께 MRTK에서 제공하는 단추 및 메뉴 프리팹을 사용하여 간단한 사용자 인터페이스를 만드는 방법 및 눌렀을 때 이벤트를 트리거하도록 단추를 구성하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="56679-212">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="56679-213">또한 동적 도구 설명 UI 요소를 추가하여 사용자에게 추가 정보를 제공하는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="56679-213">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

[<span data-ttu-id="56679-214">다음 자습서: 7. 3D 개체와 상호 작용</span><span class="sxs-lookup"><span data-stu-id="56679-214">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)
