---
title: 자습서 시작-6. 고급 입력 옵션 탐색
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: aaa02ce118fd051d94311e837b143affc96ff72b
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554255"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="23967-105">6. 고급 입력 옵션 탐색</span><span class="sxs-lookup"><span data-stu-id="23967-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="23967-106">이 자습서에서는 음성 명령, 패닝 제스처 및 눈 추적 사용을 포함 하 여 HoloLens 2에 대 한 몇 가지 고급 입력 옵션을 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="23967-107">목표</span><span class="sxs-lookup"><span data-stu-id="23967-107">Objectives</span></span>

* <span data-ttu-id="23967-108">음성 명령 및 키워드를 사용 하 여 이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="23967-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="23967-109">추적 된 손을 사용 하 여 추적 된 손으로 텍스처 및 3D 개체를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="23967-110">HoloLens 2 눈동자 추적 기능을 활용 하 여 개체 선택</span><span class="sxs-lookup"><span data-stu-id="23967-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="23967-111">음성 명령 사용</span><span class="sxs-lookup"><span data-stu-id="23967-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="23967-112">이 섹션에서는 사용자가 Octa 개체에서 소리를 재생할 수 있도록 음성 명령을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="23967-113">이렇게 하려면 새 음성 명령을 만든 다음 speech command 키워드를 말할 때 원하는 작업을 트리거하기 위해 이벤트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="23967-114">이를 위해 수행 하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="23967-115">기본 입력 시스템 프로필을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="23967-116">기본 음성 명령 프로필을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="23967-117">새 음성 명령 만들기</span><span class="sxs-lookup"><span data-stu-id="23967-117">Create a new speech command</span></span>
4. <span data-ttu-id="23967-118">음성 입력 처리기 (스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="23967-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="23967-119">Speech 명령에 대 한 응답 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="23967-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="23967-120">1. 기본 입력 시스템 프로필을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="23967-121">계층 구조 창에서 **MixedRealityToolkit** 개체를 선택한 다음, 검사기 창에서 **입력** 탭을 선택 하 고 **DefaultHoloLens2InputSystemProfile** 을 복제 하 여 사용자 지정 가능한 **입력 시스템 프로필로**바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="23967-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="23967-123">MRTK 프로필을 복제 하는 방법에 대 한 미리 알림은 [Mixed Reality Toolkit 프로필을 구성](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 하는 방법 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="23967-124">2. 기본 음성 명령 프로필을 복제 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="23967-125">**음성** 섹션을 확장 하 고 **DefaultMixedRealitySpeechCommandsProfile** 를 복제 하 여 사용자 지정 가능한 **음성 명령 프로필로**바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="23967-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="23967-127">3. 새 음성 명령 만들기</span><span class="sxs-lookup"><span data-stu-id="23967-127">3. Create a new speech command</span></span>

<span data-ttu-id="23967-128">**음성 명령** 섹션에서 **+ 새 음성 명령 추가** 단추를 클릭 하 여 기존 음성 명령 목록의 맨 아래에 새 음성 명령을 추가 하 고, **키워드** 필드에 적절 한 단어나 구를 입력 합니다 (예: **음악 재생**:</span><span class="sxs-lookup"><span data-stu-id="23967-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="23967-130">컴퓨터에 마이크가 없고 편집기에서 시뮬레이션을 사용 하 여 음성 명령을 테스트 하려는 경우 해당 키를 누를 때 트리거할 수 있도록 음성 명령에 KeyCode를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="23967-131">4. 음성 입력 처리기 (스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="23967-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="23967-132">계층 창에서 **Octa** 개체를 선택 하 고 Octa 개체에 **음성 입력 처리기 (스크립트)** 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="23967-133">그런 다음 사용자가 Octa 개체를 확인 하 여 음성 명령을 트리거할 필요가 없도록 **포커스 필요** 확인란의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="23967-135">5. 음성 명령에 대 한 응답 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="23967-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="23967-136">음성 입력 처리기 (스크립트) 구성 요소에서 작은 **+** 단추를 클릭 하 여 키워드 목록에 키워드 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="23967-138">새로 만든 **요소 0** 을 클릭 하 여 확장 한 다음 **키워드** 드롭다운에서 이전에 만든 **음악 재생** 키워드를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-138">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="23967-140">키워드 드롭다운의 키워드는 음성 명령 프로필의 음성 명령 목록에 정의 된 키워드를 기준으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="23967-140">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="23967-141">새 **응답 ()** 이벤트를 만들고, 이벤트를 받도록 **Octa** 개체를 구성 하 고, 트리거할 작업으로 **PlayOneShot** 를 정의 하 고, 오디오 **클립** 필드에 적합 한 오디오 클립을 할당 합니다 (예: MRTK_Gem 오디오 클립).</span><span class="sxs-lookup"><span data-stu-id="23967-141">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="23967-143">이벤트를 구현 하 고 오디오 클립을 할당 하는 방법에 대 한 미리 알림은 [터치 시작 시의 구현 이벤트](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-143">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="23967-144">이동 제스처</span><span class="sxs-lookup"><span data-stu-id="23967-144">The Pan Gesture</span></span>

<span data-ttu-id="23967-145">이동 제스처는 손가락을 사용 하 여 스크롤 하거나 콘텐츠를 스크롤 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-145">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="23967-146">이 예제에서는 먼저 2D UI를 스크롤한 다음 3D 개체의 컬렉션을 스크롤할 수 있도록이를 확장 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="23967-146">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="23967-147">이를 위해 수행 하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="23967-148">패닝에 사용할 수 있는 쿼드 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="23967-148">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="23967-149">Near 인터랙션 Touchable (스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="23967-149">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="23967-150">직접 상호 작용 팬 확대/축소 (스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="23967-150">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="23967-151">스크롤할 2D 콘텐츠 추가</span><span class="sxs-lookup"><span data-stu-id="23967-151">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="23967-152">스크롤할 3D 콘텐츠 추가</span><span class="sxs-lookup"><span data-stu-id="23967-152">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="23967-153">이동 (스크립트) 구성 요소를 사용 하 여 이동 추가</span><span class="sxs-lookup"><span data-stu-id="23967-153">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="23967-154">이동 이동 (스크립트) 구성 요소가 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="23967-154">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="23967-155">이 자습서의 자산과 함께 제공 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-155">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="23967-156">1. 패닝에 사용할 수 있는 쿼드 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="23967-156">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="23967-157">계층 창에서 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 **3D 개체** > **4** 를 선택 하 여 장면에 쿼드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-157">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="23967-158">적절 한 이름 (예: **Pangesture**)을 지정 하 고 적절 한 위치에 배치 합니다 (예: X = 0, Y =-0.2, Z = 2).</span><span class="sxs-lookup"><span data-stu-id="23967-158">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="23967-160">3D 쿼드와 같은 Unity 기본 형식을 장면에 추가 하는 방법에 대 한 미리 알림은 [장면에 큐브 추가](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-160">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="23967-161">다른 모든 상호 작용 에서처럼 이동 제스처에는 collider도 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-161">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="23967-162">기본적으로 쿼드에는 메시 collider가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-162">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="23967-163">그러나 메시 collider는 매우 씬 이기 때문에 이상적이 지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-163">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="23967-164">사용자가 collider와 쉽게 상호 작용할 수 있도록 메시 collider를 box collider로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="23967-164">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="23967-165">PanGesture 개체를 선택한 상태에서 **메시 collider** Component의 **설정** 아이콘을 클릭 하 고 **구성 요소 제거** 를 선택 하 여 메시 collider를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-165">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="23967-167">검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 **상자 collider**를 추가한 다음 collider **Size** Z 상자를 0.15으로 변경 하 여 상자 collider의 두께를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="23967-167">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="23967-169">2. Near 인터랙션 Touchable (스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="23967-169">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="23967-170">**Pangesture** 개체를 선택한 상태에서 **near 인터랙션 Touchable (스크립트)** 구성 요소를 pangestoutobject에 추가 하 고 **범위 수정** 및 **수정 센터** 단추를 클릭 하 여 near Touchable (스크립트)의 로컬 센터 및 범위 속성을 boxcollider와 일치 하도록 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-170">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="23967-172">3. 직접 상호 작용 팬 확대/축소 (스크립트) 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-172">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="23967-173">**Pangesture** 개체를 선택 하 고 나 서 **상호 작용 이동 확대/축소 (스크립트)** 구성 요소를 pangesture 개체에 추가한 다음 **가로 잠금** 확인란을 선택 하 여 세로 스크롤만 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-173">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="23967-175">4. 스크롤할 2D 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-175">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="23967-176">프로젝트 패널에서 창 **콘텐츠** 자료를 검색 한 다음,이를 클릭 하 여 **pangesture** 의 메시 렌더러 **재질** 요소 0 속성으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-176">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="23967-178">검사기 창에서 새로 추가 된 창 **콘텐츠** 재질 구성 요소를 확장 한 다음 X 값과 일치 하 고 타일이 사각형으로 표시 되도록 **바둑판식 배열** Y 값을 0.5로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-178">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="23967-180">이제 게임 모드를 입력 하는 경우 편집기 내 시뮬레이션의 이동 제스처를 사용 하 여 2D 콘텐츠 스크롤을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-180">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="23967-182">5. 스크롤할 3D 콘텐츠를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-182">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="23967-183">계층 창에서 **4 개의 큐브** 를 **pangesture** 개체의 자식 개체로 만들고 해당 변환 **배율을** X = 0.15, Y = 0.15, Z = 0.15로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-183">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="23967-185">큐브를 균등 하 게 공간을 절약 하 고 일정 시간을 절약 하려면 **표 개체 컬렉션 (스크립트)** 구성 요소를 큐브의 부모 개체 (예: **pangestlaobject** )에 추가 하 고 다음과 같이 그리드 개체 컬렉션 (스크립트)을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-185">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="23967-186">**행** 수를 1로 변경 하 여 모든 큐브를 하나의 단일 행에 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-186">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="23967-187">**셀 너비** 를 0.25으로 변경 하 여 행 내의 큐브 공간을 확보 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-187">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="23967-188">그런 다음 **컬렉션 업데이트** 단추를 클릭 하 여 새 구성을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-188">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="23967-190">6. 패닝 (스크립트) 구성 요소를 사용 하 여 이동 추가</span><span class="sxs-lookup"><span data-stu-id="23967-190">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="23967-191">계층 창에서 모든 **큐브 자식 개체**를 선택한 다음, 검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 **위아래로 이동 (스크립트)** 구성 요소를 모든 큐브에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-191">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="23967-193">계층 창에서 여러 개체를 선택 하는 방법에 대 한 미리 알림은 [모든 개체에 조작 처리기 (스크립트) 구성 요소 추가](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) 명령을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-193">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="23967-194">모든 큐브를 선택 하 고 나 서 다음을 클릭 하 여 **Pangesture** 개체를 **이동 입력 원본** 필드에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-194">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="23967-196">각 큐브의 이동 이동 (스크립트) 구성 요소는 HandInteractionPanZoom (스크립트) 구성 요소에서 보낸 팬 업데이트 이벤트를 위 단계에서 이동 입력 원본으로 할당 한 후 각 큐브의 위치를 업데이트 하는 것을 수신 합니다. 올바르게.</span><span class="sxs-lookup"><span data-stu-id="23967-196">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="23967-197">계층 창에서 **Pangestkeobject** 를 선택 하 고 검사기에서 메시 **렌더러** **확인 취소** 확인란을 선택 취소 하 여 메시 렌더러 구성 요소를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-197">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="23967-199">이제 게임 모드를 입력 하는 경우 편집기 내 시뮬레이션의 이동 제스처를 사용 하 여 3D 콘텐츠 스크롤을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-199">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="23967-201">시선 추적</span><span class="sxs-lookup"><span data-stu-id="23967-201">Eye Tracking</span></span>

<span data-ttu-id="23967-202">이 섹션에서는 프로젝트에서 눈 추적을 사용 하도록 설정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-202">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="23967-203">이 예에서는 사용자의 눈 응시에서 확인 하는 동안 3DObjectCollection의 각 개체를 천천히 회전 하는 기능을 구현 하 고, 선택 하는 개체가 공중 탭 또는 음성 명령에 의해 선택 되는 경우에는 블 립 효과를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-203">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="23967-204">이를 위해 수행 하는 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-204">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="23967-205">모든 대상 개체에 눈동자 추적 대상 (스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="23967-205">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="23967-206">모든 대상 개체에 눈동자 추적 자습서 데모 (스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="23967-206">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="23967-207">대상 이벤트를 찾는 동안을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-207">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="23967-208">선택한 이벤트에 대해를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-208">Implement the On Selected event</span></span>
5. <span data-ttu-id="23967-209">편집기 내 시뮬레이션에 대해 시뮬레이션 된 눈 추적 사용</span><span class="sxs-lookup"><span data-stu-id="23967-209">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="23967-210">Visual Studio 프로젝트의 앱 기능에서 응시 입력 사용</span><span class="sxs-lookup"><span data-stu-id="23967-210">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="23967-211">1. 모든 대상 개체에 눈 추적 대상 (스크립트) 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-211">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="23967-212">계층 구조 창에서 **3DObjectCollection** 개체를 확장 하 고 모든 **자식 개체**를 선택한 다음, 검사기 창에서 **구성 요소 추가** 단추를 사용 하 여 모든 자식 개체에 **눈 추적 대상 (스크립트)** 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-212">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="23967-214">모든 **자식 개체가** 선택 된 상태에서 다음과 같이 **눈 추적 대상 (스크립트)** 구성 요소를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-214">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="23967-215">선택 **작업** **선택을 선택**하 여이 개체에 대 한 공기 탭 작업을 선택으로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-215">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="23967-216">**음성 선택** 을 확장 하 고 음성 명령 목록 **크기** 를 1로 설정한 다음 나타나는 새 요소 목록에서 **요소 0** 을 **선택**으로 변경 하 여이 개체에 대 한 음성 명령 작업을 select로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-216">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="23967-218">2. 모든 대상 개체에 눈동자 추적 자습서 데모 (스크립트) 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-218">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="23967-219">모든 **자식 개체** 를 선택 하 고 나 서 **구성 요소 추가** 단추를 사용 하 여 모든 자식 개체에 **눈동자 추적 자습서 데모 (스크립트)** 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-219">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="23967-221">아이 추적 대상 (스크립트) 구성 요소가 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="23967-221">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="23967-222">이 자습서의 자산과 함께 제공 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-222">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="23967-223">3. 대상 이벤트를 찾는 동안을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-223">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="23967-224">계층 창에서 **치즈** 개체를 선택한 다음 **Target () 이벤트를 찾는 동안** 새를 만들고, 이벤트를 받도록 **치즈** 개체를 구성 하 고, 트리거할 작업으로 RotateTarget를 정의 **합니다** .</span><span class="sxs-lookup"><span data-stu-id="23967-224">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="23967-226">3DObjectCollection의 각 자식 개체에 대해 **반복** 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-226">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="23967-227">이벤트를 구현 하는 방법에 대 한 미리 알림은 [손 추적 제스처 및 interactable 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-227">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="23967-228">4. 선택한 이벤트에 대해를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-228">4. Implement the On Selected event</span></span>

<span data-ttu-id="23967-229">계층 구조 창에서 **치즈** 개체를 선택 하 고, **선택 된 () 이벤트에** 새 이벤트를 만들고, 이벤트를 받도록 **치즈** 개체를 구성 하 고, 트리거할 액션으로 BlipTarget를 정의 **합니다** .</span><span class="sxs-lookup"><span data-stu-id="23967-229">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="23967-231">3DObjectCollection의 각 자식 개체에 대해 **반복** 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-231">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="23967-232">5. 편집기 내 시뮬레이션에 대해 시뮬레이션 된 눈동자 추적 사용</span><span class="sxs-lookup"><span data-stu-id="23967-232">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="23967-233">계층 구조 창에서 **MixedRealityToolkit** 개체를 선택한 다음, 검사기 창에서 입력 탭을 선택 하 **고 입력** **데이터 공급자** 섹션을 확장 한 다음 입력 **시뮬레이션 서비스** 섹션을 확장 하 고 **DefaultMixedRealityInputSimulationProfile** 을 복제 하 여 사용자 지정 가능한 **입력 시뮬레이션 프로필로**바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="23967-233">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="23967-235">MRTK 프로필을 복제 하는 방법에 대 한 미리 알림은 [Mixed Reality Toolkit 프로필을 구성](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 하는 방법 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-235">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="23967-236">눈 **시뮬레이션** 섹션에서 눈 **위치 시뮬레이트** 확인란을 선택 하 여 눈동자 추적 시뮬레이션을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-236">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="23967-238">이제 게임 모드를 입력 하는 경우 커서가 개체 중 하나에 적중 하도록 뷰를 조정 하 고 직접 상호 작용 또는 음성 명령을 사용 하 여 개체를 선택 하 여 구현 된 회전 및 나선 효과를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-238">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="23967-240">[혼합 현실 도구 키트 구성](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) 에 설명 된 대로 DefaultHoloLens2ConfigurationProfile를 사용 하 여 사용자 지정 가능한 MRTK 구성 프로필을 복제 하지 않은 경우 프로젝트에서 눈 추적을 사용 하도록 설정할 수 없으며 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-240">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="23967-241">이를 위해 [MRTK의 눈동자 추적 시작](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-241">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="23967-242">6. Visual Studio 프로젝트의 앱 기능에서 응시 입력 사용</span><span class="sxs-lookup"><span data-stu-id="23967-242">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="23967-243">Visual Studio에서 장치로 앱을 빌드하고 배포 하기 전에 프로젝트의 앱 기능에서 응시 입력을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-243">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="23967-244">이를 위해 [HoloLens 2 지침에서 Unity 앱 테스트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) 를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-244">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="23967-245">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-245">Congratulations</span></span>

<span data-ttu-id="23967-246">응용 프로그램에 기본 눈 추적 기능을 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-246">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="23967-247">이러한 작업은 시선 추적 기능 활용의 시작에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="23967-247">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="23967-248">이 자습서에서는 음성 명령 및 패닝 제스처와 같은 기타 고급 입력 기능에 대해서도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="23967-248">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="23967-249">다음 단원: 7. 음력 모듈 샘플 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="23967-249">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
