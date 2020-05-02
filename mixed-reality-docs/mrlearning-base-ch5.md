---
title: 시작 자습서 - 6. 고급 입력 옵션 탐색
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: ec078015304e1cddc9b042fb5e94cf1904a302cb
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376090"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="bf15d-105">6. 고급 입력 옵션 탐색</span><span class="sxs-lookup"><span data-stu-id="bf15d-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="bf15d-106">이 자습서에서는 음성 명령, 이동 제스처 및 시선 추적을 비롯한 HoloLens 2의 몇 가지 고급 입력 옵션을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-106">In this tutorial, you will explore a few advanced input options for HoloLens 2, including the use of voice commands, panning gesture, and eye tracking.</span></span>

## <a name="objectives"></a><span data-ttu-id="bf15d-107">목표</span><span class="sxs-lookup"><span data-stu-id="bf15d-107">Objectives</span></span>

* <span data-ttu-id="bf15d-108">음성 명령 및 키워드를 사용하여 이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="bf15d-108">Trigger events using voice commands and keywords</span></span>
* <span data-ttu-id="bf15d-109">추적 손을 사용하여 추적 손으로 텍스처 및 3D 개체 이동</span><span class="sxs-lookup"><span data-stu-id="bf15d-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
* <span data-ttu-id="bf15d-110">HoloLens 2 시선 추적 기능을 활용하여 개체 선택</span><span class="sxs-lookup"><span data-stu-id="bf15d-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="enabling-voice-commands"></a><span data-ttu-id="bf15d-111">음성 명령 사용</span><span class="sxs-lookup"><span data-stu-id="bf15d-111">Enabling Voice Commands</span></span>
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

<span data-ttu-id="bf15d-112">이 섹션에서는 사용자가 Octa 개체에서 소리를 재생할 수 있도록 음성 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-112">In this section, you will implement a speech command to let the user play a sound on the Octa object.</span></span> <span data-ttu-id="bf15d-113">이를 위해 새 음성 명령을 생성한 다음, 음성 명령 키워드가 사용될 때 원하는 동작을 트리거하도록 이벤트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-113">For this, you will create a new speech command and then configure the event so it triggers the desired action when the speech command keyword is spoken.</span></span>

<span data-ttu-id="bf15d-114">이를 위해 수행할 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-114">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="bf15d-115">기본 입력 시스템 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="bf15d-115">Clone the default Input System Profile</span></span>
2. <span data-ttu-id="bf15d-116">기본 음성 명령 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="bf15d-116">Clone the default Speech Commands Profile</span></span>
3. <span data-ttu-id="bf15d-117">새 음성 명령 만들기</span><span class="sxs-lookup"><span data-stu-id="bf15d-117">Create a new speech command</span></span>
4. <span data-ttu-id="bf15d-118">음성 입력 처리기(스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="bf15d-118">Add and configure the Speech Input Handler (Script) component</span></span>
5. <span data-ttu-id="bf15d-119">음성 명령에 대한 응답 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="bf15d-119">Implement the Response event for the speech command</span></span>

### <a name="1-clone-the-default-input-system-profile"></a><span data-ttu-id="bf15d-120">1. 기본 입력 시스템 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="bf15d-120">1. Clone the default Input System Profile</span></span>

<span data-ttu-id="bf15d-121">[계층 구조] 창에서 **MixedRealityToolkit** 개체를 선택하고 [검사기] 창에서 **입력** 탭을 선택한 다음, **DefaultHoloLens2InputSystemProfile**을 복제하여 개발자의 사용자 지정 가능한 **입력 시스템 프로필**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-121">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab and clone the **DefaultHoloLens2InputSystemProfile** to replace it with your own customizable **Input System Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="bf15d-123">MRTK 프로필을 복제하는 방법에 대한 자세한 내용은 [Mixed Reality Toolkit 프로필을 구성하는 방법](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf15d-123">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

### <a name="2-clone-the-default-speech-commands-profile"></a><span data-ttu-id="bf15d-124">2. 기본 음성 명령 프로필 복제</span><span class="sxs-lookup"><span data-stu-id="bf15d-124">2. Clone the default Speech Commands Profile</span></span>

<span data-ttu-id="bf15d-125">**음성** 섹션을 확장하고, **DefaultMixedRealitySpeechCommandsProfile**을 복제하여 개발자의 사용자 지정 가능한 **음성 명령 프로필**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-125">Expand the **Speech** section and clone the **DefaultMixedRealitySpeechCommandsProfile** to replace it with your own customizable **Speech Commands Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a><span data-ttu-id="bf15d-127">3. 새 음성 명령 만들기</span><span class="sxs-lookup"><span data-stu-id="bf15d-127">3. Create a new speech command</span></span>

<span data-ttu-id="bf15d-128">**음성 명령** 섹션에서 **+새 음성 명령 추가** 단추를 클릭하여 기존 음성 명령 목록의 맨 아래에 새 음성 명령을 추가한 다음, **키워드** 필드에 적절한 단어 또는 구(예: **음악 재생**)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-128">In the **Speech Commands** section, click the **+ Add a New Speech Command** button to add a new speech command to the bottom of the list of existing speech commands, then in the **Keyword** field enter a suitable word or phrase, for example **Play Music**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> <span data-ttu-id="bf15d-130">컴퓨터에 마이크가 없고 편집기 내 시뮬레이션을 사용하여 음성 명령을 테스트하려는 경우 해당 키를 누를 때 트리거할 수 있는 음성 명령에 KeyCode를 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-130">If your computer doesn't have a microphone and you would like to test the speech command using the in-editor simulation, you can assign a KeyCode to the speech command which will let you trigger it when the corresponding key is pressed.</span></span>

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a><span data-ttu-id="bf15d-131">4. 음성 입력 처리기(스크립트) 구성 요소 추가 및 구성</span><span class="sxs-lookup"><span data-stu-id="bf15d-131">4. Add and configure the Speech Input Handler (Script) component</span></span>

<span data-ttu-id="bf15d-132">[계층 구조] 창에서 **Octa** 개체를 선택하고 **음성 입력 처리기(스크립트)** 구성 요소를 Octa 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-132">In the Hierarchy window, select the **Octa** object and add the **Speech Input Handler (Script)** component to the Octa object.</span></span> <span data-ttu-id="bf15d-133">그런 다음, 사용자가 음성 명령을 트리거하기 위해 Octa 개체를 볼 필요가 없도록 **Is Focus Required** 확인란의 선택을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-133">Then uncheck the **Is Focus Required** checkbox so the user is not required to look at the Octa object to trigger the speech command:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a><span data-ttu-id="bf15d-135">5. 음성 명령에 대한 응답 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="bf15d-135">5. Implement the Response event for the speech command</span></span>

<span data-ttu-id="bf15d-136">음성 입력 처리기(스크립트) 구성 요소에서 작은 **+** 단추를 클릭하여 키워드 목록에 키워드 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-136">On the Speech Input Handler (Script) component, click the small **+** button to add a keyword element to the list of keywords:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

<span data-ttu-id="bf15d-138">새로 생성한 **요소 0**을 클릭하여 확장한 다음, **키워드** 드롭다운에서 이전에 만든 **음악 재생** 키워드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-138">Click the newly created **Element 0** to expand it, and then, from the **Keyword** dropdown, choose the **Play Music** keyword you created earlier:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> <span data-ttu-id="bf15d-140">키워드 드롭다운의 키워드는 음성 명령 프로필의 음성 명령 목록에 정의된 키워드에 따라 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-140">The keywords in the Keyword dropdown are populated based on the keywords defined in the Speech Commands list in the Speech Commands Profile.</span></span>

<span data-ttu-id="bf15d-141">새 **Response ()** 이벤트를 만들고, 이벤트를 수신하도록 **Octa** 개체를 구성하고, **AudioSource.PlayOneShot**를 트리거할 작업으로 정의하고, 적절한 오디오 클립(예: MRTK_Gem 오디오 클립)을 **오디오 클립** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-141">Create a new **Response ()** event, configure the **Octa** object to receive the event, define **AudioSource.PlayOneShot** as the action to be triggered, and assign a suitable audio clip to the **Audio Clip** field, for example, the MRTK_Gem audio clip:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> <span data-ttu-id="bf15d-143">이벤트를 구현하고 오디오 클립을 할당하는 방법에 대한 자세한 내용은 [On Touch Started 이벤트 구현](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf15d-143">For a reminder on how to implement events and assign an audio clip, you can refer to the [Implement the On Touch Started event](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) instructions.</span></span>

## <a name="the-pan-gesture"></a><span data-ttu-id="bf15d-144">이동 제스처</span><span class="sxs-lookup"><span data-stu-id="bf15d-144">The Pan Gesture</span></span>

<span data-ttu-id="bf15d-145">이동 제스처는 손가락이나 손을 사용하여 내용을 스크롤하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-145">The pan gesture is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="bf15d-146">이 예제에서는 먼저 2D UI를 스크롤한 다음, 이 UI를 확장하여 3D 개체 컬렉션을 스크롤하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-146">In this example, you will first learn how to scroll a 2D UI and then expand on that to be able to scroll through a collection of 3D objects.</span></span>

<span data-ttu-id="bf15d-147">이를 위해 수행할 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-147">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="bf15d-148">상하좌우 이동에 사용할 수 있는 쿼드 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="bf15d-148">Create a Quad object that can be used for panning</span></span>
2. <span data-ttu-id="bf15d-149">근거리 터치형 상호 작용(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-149">Add the Near Interaction Touchable (Script) component</span></span>
3. <span data-ttu-id="bf15d-150">직접 상호 작용 팬 확대/축소(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-150">Add the Hand Interaction Pan Zoom (Script) component</span></span>
4. <span data-ttu-id="bf15d-151">스크롤할 2D 콘텐츠 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-151">Add 2D content to be scrolled</span></span>
5. <span data-ttu-id="bf15d-152">스크롤할 3D 콘텐츠 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-152">Add 3D content to be scrolled</span></span>
6. <span data-ttu-id="bf15d-153">팬으로 이동(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-153">Add the Move With Pan (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="bf15d-154">팬을 사용하여 이동(스크립트) 구성 요소는 MRTK에 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-154">The Move With Pan (Script) component is not part of MRTK.</span></span> <span data-ttu-id="bf15d-155">이 자습서의 자산과 함께 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-155">It was provided with this tutorial's assets.</span></span>

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a><span data-ttu-id="bf15d-156">1. 상하좌우 이동에 사용할 수 있는 쿼드 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="bf15d-156">1. Create a Quad object that can be used for panning</span></span>

<span data-ttu-id="bf15d-157">[계층 구조] 창에서 마우스 오른쪽 단추로 빈 영역을 클릭하고, **3D 개체** > **쿼드**를 선택하여 장면에 쿼드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-157">In the Hierarchy window, right-click at an empty area and select **3D Object** > **Quad** to add a quad to your scene.</span></span> <span data-ttu-id="bf15d-158">적절한 이름(예: **PanGesture**)을 지정하고, 적절한 위치(예: X = 0, Y = -0.2, Z = 2)에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-158">Give it a suitable name, for example, **PanGesture**, and position it in a suitable location, for example, X = 0, Y = -0.2, Z = 2.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="bf15d-160">3D 쿼드와 같은 유니티 기본값을 장면에 추가하는 방법에 대한 자세한 내용은 [장면에 큐브 추가](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf15d-160">For a reminder on how to add Unity primitives, such as a 3D quad, to your scene, you can refer to the [Add a cube to the scene](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) instructions.</span></span>

<span data-ttu-id="bf15d-161">다른 모든 상호 작용과 마찬가지로, 팬 제스처에도 충돌체가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-161">As with any other interaction, the the pan gesture also requires a collider.</span></span> <span data-ttu-id="bf15d-162">기본적으로 쿼드에는 메시 충돌체가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-162">By default, a Quad has a mesh collider.</span></span> <span data-ttu-id="bf15d-163">그러나 메시 충돌체는 너무 얇아서 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-163">However, the mesh collider is not ideal because it is extremely thin.</span></span> <span data-ttu-id="bf15d-164">사용자가 충돌체와 보다 쉽게 상호작용할 수 있도록 메시 충돌체를 박스 충돌체로 교체하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-164">To make it easier for the user to interact with the collider, we will replace the mesh collider with a box collider.</span></span>

<span data-ttu-id="bf15d-165">다음과 같이 PanGesture 개체를 선택한 상태에서 **메시 충돌체** 구성 요소의 **설정** 아이콘을 클릭하고, **구성 요소 제거**를 선택하여 메시 충돌체를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-165">With the PanGesture object still selected, click the **Mesh Collider** component's **Settings** icon and select **Remove Component** to remove the Mesh Collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

<span data-ttu-id="bf15d-167">다음과 같이 [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **상자 충돌체**를 추가한 다음, 상자 충돌체 **크기** Z를 0.15로 변경하여 상자 충돌체의 두께를 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-167">In the Inspector window, use the **Add Component** button to add a **Box Collider**, then change the Box Collider **Size** Z to 0.15 to increase the thickness of the box collider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a><span data-ttu-id="bf15d-169">2. 근거리 터치형 상호 작용(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-169">2. Add the Near Interaction Touchable (Script) component</span></span>

<span data-ttu-id="bf15d-170">다음과 같이 **PanGesture** 개체를 선택한 상태에서 **근거리 터치형 상호 작용(스크립트)** 구성 요소를 PanGesture 개체에 추가한 다음, **경계 고정** 및 **중심 고정** 단추를 클릭하여 근거리 터치형 상호 작용(스크립트)의 로컬 중심 및 경계 속성을 BoxCollider에 맞게 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-170">With the **PanGesture** object still selected, add the **Near Interaction Touchable (Script)** component to the PanGesture object, and then click the **Fix Bounds** and **Fix Center** buttons to update the Local Center and Bounds properties of the Near Interaction Touchable (Script) to match the BoxCollider:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a><span data-ttu-id="bf15d-172">3. 직접 상호 작용 팬 확대/축소(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-172">3. Add the Hand Interaction Pan Zoom (Script) component</span></span>

<span data-ttu-id="bf15d-173">다음과 같이 **PanGesture** 개체를 선택한 상태에서 **직접 상호 작용 팬 확대/축소(스크립트)** 구성 요소를 PanGesture 개체에 추가한 다음, **가로 잠금** 확인란을 선택하여 세로 스크롤만 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-173">With the **PanGesture** object still selected, add the **Hand Interaction Pan Zoom (Script)** component to the PanGesture object, and then check the **Lock Horizontal** checkbox to allow vertical scrolling only:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a><span data-ttu-id="bf15d-175">4. 스크롤할 2D 콘텐츠 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-175">4. Add 2D content to be scrolled</span></span>

<span data-ttu-id="bf15d-176">다음과 같이 [프로젝트] 패널에서 **PanContent** 자료를 검색한 다음, 클릭하여 **PanGesture** 개체의 메시 렌더러 **재질** 요소 0 속성으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-176">In the Project panel, search for the **PanContent** material and then click-and-drag it on to the **PanGesture** object's Mesh Renderer **Material** Element 0 property:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

<span data-ttu-id="bf15d-178">다음과 같이 [검사기] 창에서 새로 추가된 **PanContent** 재질 구성 요소를 확장한 다음, X 값과 일치하고 타일이 사각형으로 표시되도록 **바둑판식 배열** Y 값을 0.5로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-178">In the Inspector window, expand the newly added **PanContent** material component, and then change it's **Tiling** Y value to 0.5 so it matches the X value and the tiles appear square:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

<span data-ttu-id="bf15d-180">이제 다음과 같이 게임 모드로 전환하면 편집기 내 시뮬레이션의 이동 제스처를 사용하여 2D 콘텐츠 스크롤을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-180">If you now enter Game mode, you can test scrolling the 2D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a><span data-ttu-id="bf15d-182">5. 스크롤할 3D 콘텐츠 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-182">5. Add 3D content to be scrolled</span></span>

<span data-ttu-id="bf15d-183">다음과 같이 [계층 구조] 창에서 **PanGesture** 개체의 자식 개체로 **4개 큐브를 만들고** 변환 **배율**을 X = 0.15, Y = 0.15, Z = 0.15로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-183">In the Hierarchy window, **create four cubes** as a child objects of the **PanGesture** object and set their Transform **Scale** to X = 0.15, Y = 0.15, Z = 0.15:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

<span data-ttu-id="bf15d-185">큐브를 균등하게 분할하고 일정 시간을 절약하려면 다음과 같이 큐브의 부모 개체(즉, **PanGesture** 개체)에 **Grid 개체 컬렉션(스크립트)** 구성 요소를 추가하고 Grid Object Collection(스크립트)을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-185">To space the cubes out evenly, and save some time, add the **Grid Object Collection (Script)** component, to the cubes' parent object, i.e. the **PanGesture** object, and configure the Grid Object Collection (Script) as follows:</span></span>

* <span data-ttu-id="bf15d-186">모든 큐브가 단일 행에 정렬되도록 **숫자 행**을 1로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-186">Change **Num Rows** to 1 to have all the cubes aligned on one single row</span></span>
* <span data-ttu-id="bf15d-187">큐브가 행 내부에 있도록 **셀 너비**를 0.25로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-187">Change **Cell Width** to 0.25 to space out the cubes within the row</span></span>

<span data-ttu-id="bf15d-188">그런 다음, 다음과 같이 **컬렉션 업데이트** 단추를 클릭하여 새 구성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-188">Then click the **Update Collection** button to apply the new configuration:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a><span data-ttu-id="bf15d-190">6. 팬으로 이동(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-190">6. Add the Move With Pan (Script) component</span></span>

<span data-ttu-id="bf15d-191">다음과 같이 [계층 구조] 창에서 모든 **큐브 자식 개체**을 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 모든 큐브에 **팬으로 이동(스크립트)** 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-191">In the Hierarchy window, select all the **Cube child objects**, then in the Inspector window, use the **Add Component** button to add the **Move With Pan (Script)** component to all the cubes:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> <span data-ttu-id="bf15d-193">[계층 구조] 창에서 여러 개체를 선택하는 방법에 대한 내용은 [모든 개체에 조작 처리기(스크립트) 구성 요소 추가](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf15d-193">For a reminder on how to select multiple objects in the Hierarchy window, tou can refer to the [Add the Manipulation Handler (Script) component to all the objects](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instructions.</span></span>

<span data-ttu-id="bf15d-194">다음과 같이 모든 큐브를 선택한 상태에서 **PanGesture** 개체를 클릭하여 **팬 입력 원본** 필드로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-194">With all the cubes still selected, click-and-drag the **PanGesture** object to the **Pan Input Source** field:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> <span data-ttu-id="bf15d-196">각 큐브의 팬으로 이동(스크립트) 구성 요소는 위의 단계에서 팬 입력 원본으로 할당한 PanGesture 개체의 HandInteractionPanZoom(스크립트) 구성 요소에서 보낸 팬 업데이트 이벤트를 수신 대기하다가 각 큐브의 위치를 적절하게 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-196">The Move With Pan (Script) component on each cube listens for the Pan Updated event sent by the HandInteractionPanZoom (Script) component on the PanGesture object, which you assigned as the Pan Input Source in the step above, and updates each cube's position accordingly.</span></span>

<span data-ttu-id="bf15d-197">다음과 같이 [계층 구조] 창에서 **PanGesture** 개체를 선택한 다음, [검사기] 창에서 **메시 렌더러** 확인란을 **선택 취소**하여 메시 렌더러 구성 요소를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-197">In the Hierarchy window, select the **PanGesture** object, then in the inspector **un-check** the **Mesh Renderer** checkbox to disable the Mesh Renderer component:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

<span data-ttu-id="bf15d-199">이제 다음과 같이 게임 모드로 전환하면 편집기 내 시뮬레이션의 이동 제스처를 사용하여 3D 콘텐츠 스크롤을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-199">If you now enter Game mode, you can test scrolling the 3D content using the pan gesture in the in-editor simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a><span data-ttu-id="bf15d-201">시선 추적</span><span class="sxs-lookup"><span data-stu-id="bf15d-201">Eye Tracking</span></span>

<span data-ttu-id="bf15d-202">이 섹션에서는 프로젝트에서 시선 추적을 사용하도록 설정하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-202">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="bf15d-203">이 예에서는 사용자가 응시하는 동안 3DObjectCollection의 각 개체를 천천히 회전하고, 응시 중인 개체를 에어 탭 또는 음성 명령으로 선택하면 블립 효과를 트리거하는 기능을 구현하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-203">For this example, you will implement functionality to make each object in the 3DObjectCollection spin slowly while being looked at by the user's eye gaze, as well as, trigger a blip effect when the object being looked at is selected by air-tap or speech command.</span></span>

<span data-ttu-id="bf15d-204">이를 위해 수행할 주요 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-204">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="bf15d-205">모든 대상 개체에 시선 추적 대상(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-205">Add the Eye Tracking Target (Script) component to all target objects</span></span>
2. <span data-ttu-id="bf15d-206">모든 대상 개체에 시선 추적 자습서 데모(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-206">Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>
3. <span data-ttu-id="bf15d-207">While Looking At Target 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="bf15d-207">Implement the While Looking At Target event</span></span>
4. <span data-ttu-id="bf15d-208">On Selected 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="bf15d-208">Implement the On Selected event</span></span>
5. <span data-ttu-id="bf15d-209">편집기 내 시뮬레이션에 시뮬레이션된 눈 추적 사용</span><span class="sxs-lookup"><span data-stu-id="bf15d-209">Enable simulated eye tracking for in-editor simulations</span></span>
6. <span data-ttu-id="bf15d-210">Visual Studio 프로젝트의 앱 기능에서 응시 입력 사용</span><span class="sxs-lookup"><span data-stu-id="bf15d-210">Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a><span data-ttu-id="bf15d-211">1. 모든 대상 개체에 시선 추적 대상(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-211">1. Add the Eye Tracking Target (Script) component to all target objects</span></span>

<span data-ttu-id="bf15d-212">다음과 같이 [계층 구조] 창에서 **3DObjectCollection**을 확장하고 모든 **자식 개체**를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 모든 자식 개체에 **시선 추적 대상(스크립트)** 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-212">In the Hierarchy window, expand the **3DObjectCollection** object and select all the **child objects**, then in the Inspector window, use the **Add Component** button to add the **Eye Tracking Target (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

<span data-ttu-id="bf15d-214">다음과 같이 모든 **자식 개체**를 선택한 상태에서 **시선 추적 대상(스크립트)** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-214">With all the **child objects** still selected, configure the **Eye Tracking Target (Script)** component as follows:</span></span>

* <span data-ttu-id="bf15d-215">**동작 선택**을 **선택**으로 변경하여 이 개체의 에어 탭 동작을 [선택]으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-215">Change **Select Action** to **Select**, to define the air-tap action for this object as Select</span></span>
* <span data-ttu-id="bf15d-216">**음성 선택**을 확장하고 음성 명령 목록 **크기**를 1로 설정한 다음, 나타나는 새 요소 목록에서 **요소 0**을 **선택**으로 변경하여 이 개체의 음성 명령 동작을 [선택]으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-216">Expand **Voice Select** and set the voice command list **Size** to 1, and then, in the new element list that appear, change **Element 0** to **Select**, to define the speech command action for this object as Select</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a><span data-ttu-id="bf15d-218">2. 모든 대상 개체에 시선 추적 자습서 데모(스크립트) 구성 요소 추가</span><span class="sxs-lookup"><span data-stu-id="bf15d-218">2. Add the Eye Tracking Tutorial Demo (Script) component  to all target objects</span></span>

<span data-ttu-id="bf15d-219">다음과 같이 모든 **자식 개체**를 선택한 상태에서 **구성 요소 추가** 단추를 사용하여 모든 자식 개체에 **시선 추적 자습서 데모(스크립트)** 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-219">With all the **child objects** still selected, use the **Add Component** button to add the **Eye Tracking Tutorial Demo (Script)** component to all the child objects:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> <span data-ttu-id="bf15d-221">시선 추적 대상(스크립트) 구성 요소는 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-221">The Eye Tracking Target (Script) component is not part of MRTK.</span></span> <span data-ttu-id="bf15d-222">이 자습서의 자산과 함께 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-222">It was provided with this tutorial's assets.</span></span>

### <a name="3-implement-the-while-looking-at-target-event"></a><span data-ttu-id="bf15d-223">3. While Looking At Target 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="bf15d-223">3. Implement the While Looking At Target event</span></span>

<span data-ttu-id="bf15d-224">[계층 구조] 창에서 **Cheese** 개체를 선택한 다음, 새 **While Looking At Target ()** 이벤트를 만들고, 이벤트를 수신하도록 **Cheese** 개체를 구성하고, 트리거할 동작으로 **EyeTrackingTutorialDemo.RotateTarget**을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-224">In the Hierarchy window, select the **Cheese** object, then create a new **While Looking At Target ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.RotateTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

<span data-ttu-id="bf15d-226">3DObjectCollection의 자식 개체마다 이 과정을 **반복**합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-226">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

> [!TIP]
> <span data-ttu-id="bf15d-227">이벤트를 구현하는 방법에 대한 내용은 [손 추적 제스처 및 상호 작용 가능 단추](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf15d-227">For a reminder on how to implement events, you can refer to the [Hand tracking gestures and interactable buttons](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) instructions.</span></span>

### <a name="4-implement-the-on-selected-event"></a><span data-ttu-id="bf15d-228">4. On Selected 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="bf15d-228">4. Implement the On Selected event</span></span>

<span data-ttu-id="bf15d-229">다음과 같이 [계층 구조] 창에서 **Cheese** 개체를 선택한 다음, 새 **On Selected ()** 이벤트를 만들고, 이벤트를 수신하도록 **Cheese** 개체를 구성하고, 트리거할 동작으로 **EyeTrackingTutorialDemo.BlipTarget**을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-229">In the Hierarchy window, select the **Cheese** object, then create a new **On Selected ()** event, configure the **Cheese** object to receive the event, and define **EyeTrackingTutorialDemo.BlipTarget** as the action to be triggered:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

<span data-ttu-id="bf15d-231">3DObjectCollection의 자식 개체마다 이 과정을 **반복**합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-231">**Repeat** for each of the child objects in the 3DObjectCollection.</span></span>

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a><span data-ttu-id="bf15d-232">5. 편집기 내 시뮬레이션에 시뮬레이션된 눈 추적 사용</span><span class="sxs-lookup"><span data-stu-id="bf15d-232">5. Enable simulated eye tracking for in-editor simulations</span></span>

<span data-ttu-id="bf15d-233">다음과 같이 [계층 구조] 창에서 **MixedRealityToolkit** 개체를 선택한 다음, [검사기] 창에서 **입력** 탭을 선택하고, **입력 데이터 공급자** 섹션을 확장하고, **입력 시뮬레이션 서비스** 섹션을 확장하고, **DefaultMixedRealityInputSimulationProfile**을 복제하여 개발자의 사용자 지정 가능한 **입력 시뮬레이션 프로필**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-233">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Input** tab, expand the **Input Data Providers** section and then the **Input Simulation Service** section, and clone the **DefaultMixedRealityInputSimulationProfile** to replace it with your own customizable **Input Simulation Profile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> <span data-ttu-id="bf15d-235">MRTK 프로필을 복제하는 방법에 대한 자세한 내용은 [Mixed Reality Toolkit 프로필을 구성하는 방법](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf15d-235">For a reminder on how to clone MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="bf15d-236">**시선 시뮬레이션** 섹션에서 **시선 위치 시뮬레이션** 확인란을 선택하여 시선 추적 시뮬레이션을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-236">In the **Eye Simulation** section, check the **Simulate Eye Position** checkbox to enable eye tracking simulation:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

<span data-ttu-id="bf15d-238">게임 모드로 전환하면 다음과 같이 커서가 개체 중 하나를 가리키도록 조정하고 손 상호 작용 또는 음성 명령으로 개체를 선택하여 앞에서 구현한 회전 및 블립 효과를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-238">If you now enter Game mode, you can test the spin and blip effects you implemented by adjusting the view so the cursor hits one of the objects and using hand interaction or speech command to select the object:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> <span data-ttu-id="bf15d-240">[Mixed Reality Toolkit 구성](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) 지침에 설명된 대로 DefaultHoloLens2ConfigurationProfile을 사용하여 사용자 지정 가능 MRTK 구성 프로필을 복제하지 않은 경우 프로젝트에서 시선 추적을 사용하도록 설정되지 않았을 수 있으며, 이 경우 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-240">If you did not use the DefaultHoloLens2ConfigurationProfile to clone your customizable MRTK configuration profile, as instructed in the [Configure the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) instructions, eye tracking may not be enable in your project and will need to be enabled.</span></span> <span data-ttu-id="bf15d-241">설정 방법은 [MRTK에서 시선 추적 시작](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf15d-241">For that, you can refer to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions.</span></span>

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a><span data-ttu-id="bf15d-242">6. Visual Studio 프로젝트의 앱 기능에서 응시 입력 사용</span><span class="sxs-lookup"><span data-stu-id="bf15d-242">6. Enable Gaze Input in the Visual Studio project's app capabilities</span></span>

<span data-ttu-id="bf15d-243">Visual Studio에서 앱을 빌드하여 디바이스에 배포하기 전에, 프로젝트의 앱 기능에서 응시 입력을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-243">Before building and deploying your app from Visual Studio to your device, Gaze Input has to been enabled in the project's app capabilities.</span></span> <span data-ttu-id="bf15d-244">이렇게 하려면 [HoloLens 2에서 Unity 앱 테스트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="bf15d-244">For this, you can follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="bf15d-245">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-245">Congratulations</span></span>

<span data-ttu-id="bf15d-246">애플리케이션에 기본적인 시선 추적 기능을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-246">You have successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="bf15d-247">이러한 작업은 시선 추적 기능 활용의 시작에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-247">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="bf15d-248">이 자습서에서는 음성 명령 및 이동 제스처와 같은 기타 고급 입력 기능에 대해서도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="bf15d-248">In this tutorial, you also learned about other advanced input features, such as voice commands and panning gestures.</span></span>

[<span data-ttu-id="bf15d-249">다음 단원: 7. 달착륙선 샘플 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="bf15d-249">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
