---
title: 시작 자습서 - 9. 음성 명령 사용
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: ed31c3b11497a0adc91b7ddc1c09b3fb4ca1c573
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306117"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="726f8-105">9. 음성 명령 사용</span><span class="sxs-lookup"><span data-stu-id="726f8-105">9. Using speech commands</span></span>

## <a name="overview"></a><span data-ttu-id="726f8-106">개요</span><span class="sxs-lookup"><span data-stu-id="726f8-106">Overview</span></span>

<span data-ttu-id="726f8-107">이 자습서에서는 음성 명령을 만드는 방법과 전역적으로 제어하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-107">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="726f8-108">음성 명령을 제어하는 개체를 사용자가 쳐다봐야 하는 로컬 음성 명령을 제어하는 방법에 대해서도 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-108">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="726f8-109">목표</span><span class="sxs-lookup"><span data-stu-id="726f8-109">Objectives</span></span>

* <span data-ttu-id="726f8-110">음성 명령을 만드는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="726f8-110">Learn how to create speech commands</span></span>
* <span data-ttu-id="726f8-111">전역적으로 및 로컬에서 음성 명령을 제어하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="726f8-111">Learn how to control speech commands globally and locally</span></span>

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="726f8-112">마이크 기능을 사용하도록 설정되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="726f8-112">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="726f8-113">Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > **Unity 프로젝트 구성**을 선택하여 **MRTK Project Configurator** 창을 열고 **UWP 기능** 섹션에서 **Enable Microphone Capability**(마이크 기능 사용)가 회색으로 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-113">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="726f8-115">이 자습서 시리즈의 시작 부분에서 Unity 프로젝트를 구성할 때 [MRTK Project Configurator 설정 적용](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) 지침을 진행하는 동안 마이크 기능을 사용하도록 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-115">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#1-apply-the-mrtk-project-configurator-settings) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="726f8-116">하지만 사용하도록 설정되지 않으면 지금 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-116">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="creating-speech-commands"></a><span data-ttu-id="726f8-117">음성 명령 만들기</span><span class="sxs-lookup"><span data-stu-id="726f8-117">Creating speech commands</span></span>

<span data-ttu-id="726f8-118">Hierarchy(계층 구조) 창에서 **MixedRealityToolkit** 개체를 선택한 다음, Inspector(인스펙터) 창에서 MixedRealityToolkit > **입력** 탭을 선택하고 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-118">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="726f8-119">**Speech**(음성) 섹션 펼치기</span><span class="sxs-lookup"><span data-stu-id="726f8-119">Expand the **Speech** section</span></span>
* <span data-ttu-id="726f8-120">**DefaultMixedRealitySpeechCommandsProfile**을 복제하여 적절한 이름(예: _GettingStarted_MixedRealitySpeechCommandsProfile_)을 지정</span><span class="sxs-lookup"><span data-stu-id="726f8-120">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="726f8-121">**Start Behaviour**(동작 시작)가 **Auto Start**(자동 시작)로 설정되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="726f8-121">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="726f8-123">MRTK 프로필을 복제하는 방법은 [MRTK 프로필 구성](mr-learning-base-03.md) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="726f8-123">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="726f8-124">Speech(음성) > **Speech Commands**(음성 명령) 섹션에서 **+ Add a New Speech Command**(새 음성 명령 추가) 단추를 4번 클릭하여 새 음성 명령 4개를 기존 음성 명령 목록에 추가한 다음, **키워드** 필드에 다음 문구를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-124">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="726f8-125">Enable Indicator(표시기 사용)</span><span class="sxs-lookup"><span data-stu-id="726f8-125">Enable Indicator</span></span>
* <span data-ttu-id="726f8-126">Enable Tap to Place(탭하여 위치 지정 사용)</span><span class="sxs-lookup"><span data-stu-id="726f8-126">Enable Tap to Place</span></span>
* <span data-ttu-id="726f8-127">Enable Bounding Box(경계 상자 사용)</span><span class="sxs-lookup"><span data-stu-id="726f8-127">Enable Bounding Box</span></span>
* <span data-ttu-id="726f8-128">Disable Bounding Box(경계 상자 사용 안 함)</span><span class="sxs-lookup"><span data-stu-id="726f8-128">Disable Bounding Box</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="726f8-130">컴퓨터에 마이크가 없는 경우 음성 명령에 KeyCode를 할당하면 해당 키를 누를 때 명령을 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-130">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="726f8-131">음성 명령 제어</span><span class="sxs-lookup"><span data-stu-id="726f8-131">Controlling speech commands</span></span>

<span data-ttu-id="726f8-132">프로젝트 창에서 **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** 폴더로 이동하여 도구 설명 프리팹을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-132">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="726f8-134">Hierarchy(계층 구조) 창에서 빈 지점을 마우스 오른쪽 단추로 클릭하고, **Create Empty**(빈 개체 생성)를 선택하여 빈 개체를 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-134">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="726f8-135">개체 이름을 **SpeechInputHandler_Global**로 지정한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **SpeechInputHandler** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-135">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="726f8-136">음성 명령을 트리거하기 위해 SpeechInputHandler 구성 요소가 있는 개체를 사용자가 쳐다보지 않아도 되도록, **Is Focus Required**(포커스 필요) 확인란을 **선택 취소**</span><span class="sxs-lookup"><span data-stu-id="726f8-136">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="726f8-137">음성 명령이 인식될 때 프리팹이 나타나도록, 프로젝트 창에서 **SpeechConfirmation Tooltip** 프리팹을 **Speech Confirmation Tooltip Prefab**(음성 확인 도구 설명 프리팹) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="726f8-137">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="726f8-139">SpeechInputHandler 구성 요소에서 작은 **+** 아이콘을 3번 클릭하여 키워드 요소를 3개 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-139">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="726f8-141">**Element 0**(요소 0)을 펼치고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-141">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="726f8-142">이전 섹션에서 만든 Enable Indicator(표시기 사용) 음성 명령을 참조하도록 **키워드** 필드에 **Enable Indicator**(표시기 사용)를 입력</span><span class="sxs-lookup"><span data-stu-id="726f8-142">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="726f8-143">작은 **+** 아이콘을 클릭하여 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="726f8-143">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="726f8-144">Hierarchy(계층 구조) 창에서 **Indicator**(표시기) 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="726f8-144">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="726f8-145">**No Function**(함수 없음) 드롭다운에서 **GameObject** > **SetActive (bool)** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="726f8-145">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="726f8-146">인수 확인란이 **선택**되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="726f8-146">Check the argument checkbox, so it is **checked**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="726f8-148">**Element 1**(요소 1)을 펼치고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-148">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="726f8-149">이전 섹션에서 만든 Enable Bounding Box(경계 상자 사용) 명령을 참조하도록 **키워드** 필드에 **Enable Bounding Box**(경계 상자 사용)를 입력</span><span class="sxs-lookup"><span data-stu-id="726f8-149">In the **Keyword** field, enter **Enable Bounding Box**, to reference the Enable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="726f8-150">작은 **+** 아이콘을 클릭하여 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="726f8-150">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="726f8-151">Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="726f8-151">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="726f8-152">**No Function**(함수 없음) 드롭다운에서 **BoundingBox** > **bool enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="726f8-152">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="726f8-153">인수 확인란이 **선택**되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="726f8-153">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="726f8-154">작은 **+** 아이콘을 클릭하여 또 다른 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="726f8-154">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="726f8-155">Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="726f8-155">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="726f8-156">**No Function**(함수 없음) 드롭다운에서 **ObjectManipulator** > **bool enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="726f8-156">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="726f8-157">인수 확인란이 **선택**되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="726f8-157">Check the argument checkbox, so it is **checked**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="726f8-159">**Element 2**(요소 2)를 펼치고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-159">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="726f8-160">이전 섹션에서 만든 Disable Bounding Box(경계 상자 사용 안 함) 명령을 참조하도록 **키워드** 필드에 **Disable Bounding Box**(경계 상자 사용 안 함)를 입력</span><span class="sxs-lookup"><span data-stu-id="726f8-160">In the **Keyword** field, enter **Disable Bounding Box**, to reference the Disable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="726f8-161">작은 **+** 아이콘을 클릭하여 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="726f8-161">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="726f8-162">Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="726f8-162">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="726f8-163">**No Function**(함수 없음) 드롭다운에서 **BoundingBox** > **bool enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="726f8-163">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="726f8-164">인수 확인란이 **선택 취소**되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="726f8-164">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="726f8-165">작은 **+** 아이콘을 클릭하여 또 다른 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="726f8-165">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="726f8-166">Hierarchy(계층 구조) 창에서 **RoverExplorer** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="726f8-166">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="726f8-167">**No Function**(함수 없음) 드롭다운에서 **ObjectManipulator** > **bool enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="726f8-167">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="726f8-168">인수 확인란이 **선택 취소**되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="726f8-168">Verify that the argument checkbox is **unchecked**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="726f8-170">Hierarchy(계층 구조) 창에서 RoverExplorer > **RoverAssembly** 개체를 선택한 다음, Inspector(인스펙터) 창에서 **Add Component**(구성 요소 추가) 단추를 사용하여 **SpeechInputHandler** 구성 요소를 추가하고 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-170">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="726f8-171">음성 명령을 트리거하기 위해 SpeechInputHandler 구성 요소(예: RoverAssembly)가 있는 개체를 사용자가 쳐다봐야 하도록, **Is Focus Required**(포커스 필요) 확인란을 **선택**</span><span class="sxs-lookup"><span data-stu-id="726f8-171">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="726f8-172">음성 명령이 인식될 때 프리팹이 나타나도록, 프로젝트 창에서 **SpeechConfirmation Tooltip** 프리팹을 **Speech Confirmation Tooltip Prefab**(음성 확인 도구 설명 프리팹) 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="726f8-172">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="726f8-174">SpeechInputHandler 구성 요소에서 작은 **+** 아이콘을 클릭하여 키워드 요소를 추가하고 새로 만든 요소를 펼친 후, 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-174">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="726f8-175">이전 섹션에서 만든 Enable Tap to Place(탭하여 위치 지정 사용) 명령을 참조하도록 **키워드** 필드에 **Enable Tap to Place**(탭하여 위치 지정 사용)를 입력</span><span class="sxs-lookup"><span data-stu-id="726f8-175">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="726f8-176">작은 **+** 아이콘을 클릭하여 이벤트를 추가</span><span class="sxs-lookup"><span data-stu-id="726f8-176">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="726f8-177">Hierarchy(계층 구조) 창에서 개체 자체(즉, 동일한 **RoverAssembly** 개체)를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="726f8-177">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="726f8-178">**No Function**(함수 없음) 드롭다운에서 **TapToPlace** > **bool enabled**를 선택하여 이벤트가 트리거될 때 이 속성 값을 업데이트</span><span class="sxs-lookup"><span data-stu-id="726f8-178">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="726f8-179">인수 확인란이 **선택**되어 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="726f8-179">Check the argument checkbox, so it is **checked**</span></span>

![mr-learning-base](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="726f8-181">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-181">Congratulations</span></span>

<span data-ttu-id="726f8-182">이 자습서에서는 음성 명령을 만드는 방법과 전역적으로 제어하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-182">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="726f8-183">음성 명령을 제어하는 개체를 사용자가 쳐다봐야 하는 로컬 음성 명령을 제어하는 방법에 대해서도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-183">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="726f8-184">이것으로 [시작 자습서](mr-learning-base-01.md) 시리즈를 마칩니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-184">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="726f8-185">이 자습서를 통해 MRTK를 사용하여 처음부터 완전 혼합 현실 경험을 성공적으로 구축했습니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-185">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="726f8-186">다음 두 가지 자습서 시리즈인 [Azure Spatial Anchors 자습서](mr-learning-asa-01.md) 및 [다중 사용자 기능 자습서](mr-learning-sharing-01.md)에서는 먼저 Azure Spatial Anchors를 프로젝트에 통합하여 직접 만든 Rover Explorer 경험을 실제 세계에서 고정하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-186">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="726f8-187">그런 다음, 다중 사용자 기능을 프로젝트에 추가하여 사용자와 개체 움직임을 실시간으로 공유하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="726f8-187">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>
