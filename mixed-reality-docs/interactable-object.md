---
title: 상호 작용할 수 없는 개체
description: 2D 추상 전 세계에서 이벤트를 트리거하는 데 사용 하는 비유를 오랫동안 단추입니다. 3 차원 혼합된 현실 세계에서 추상화를 더 이상이 환경으로 제한 될 필요가 없습니다.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 혼합된 현실 "," 컨트롤 "," 상호 작용 "," ui "," ux
ms.openlocfilehash: f349d21707375690e00b0f7e465634c62be1537e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601180"
---
# <a name="interactable-object"></a><span data-ttu-id="5670a-105">상호 작용할 수 없는 개체</span><span class="sxs-lookup"><span data-stu-id="5670a-105">Interactable object</span></span>

<span data-ttu-id="5670a-106">2D 추상 전 세계에서 이벤트를 트리거하는 데 사용 하는 비유를 오랫동안 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="5670a-107">3 차원 혼합된 현실 세계에서 추상화를 더 이상이 환경으로 제한 될 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="5670a-108">항목 수를 **상호 작용할 수 없는 개체** 이벤트를 트리거하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-108">Anything can be an **Interactable object** that triggers an event.</span></span> <span data-ttu-id="5670a-109">상호 작용할 수 없는 개체로 나타낼 수 있습니다 것과 테이블에는 커피 cup에서 공중에서 부동 풍선으로.</span><span class="sxs-lookup"><span data-stu-id="5670a-109">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="5670a-110">여전히 확인 수행 대화 상자 UI와 같이 이러한 특정 상황에서 기존 단추를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="5670a-111">단추의 시각적 표시는 컨텍스트에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-111">The visual representation of the button depends on the context.</span></span>

![영웅 이미지 interactible 개체](images/640px-interactibleobject-hero-640px.jpg)


<span data-ttu-id="5670a-113">에  **[혼합 현실 Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, 일련의 Unity 스크립트를 만들어 놓은 및 prefabs 도움이 되는 상호 작용할 수 없는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-113">In the **[Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, we have created a series of Unity scripts and prefabs that will help you create Interactable objects.</span></span> <span data-ttu-id="5670a-114">이러한 표준 상호 작용 상태를 사용 하 여 사용자를 상호 작용할 수 있는 개체의 모든 형식을 만드는 데 사용할 수 있습니다: 관찰을 대상으로 하 고 누르면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-114">You can use these to create any type of object that the user can interact with, using these standard interaction states: observation, targeted and pressed.</span></span> <span data-ttu-id="5670a-115">자신의 자산을 사용 하 여 시각적 디자인을 쉽게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-115">You can easily customize the visual design with your own assets.</span></span> <span data-ttu-id="5670a-116">자세한 애니메이션 만들기 및 할당 Unity의 애니메이션 컨트롤러의 상호 작용 상태에 대 한 해당 애니메이션 클립 또는 offset 및 배율을 사용 하 여 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-116">Detailed animations can be customized by either creating and assigning corresponding animation clips for the interaction states in the Unity's animation controller or using offset and scale.</span></span> 


## <a name="visual-feedback-for-the-different-input-interaction-states"></a><span data-ttu-id="5670a-117">다른 입력된 상호 작용 상태에 대 한 시각적 피드백</span><span class="sxs-lookup"><span data-stu-id="5670a-117">Visual feedback for the different input interaction states</span></span>

<span data-ttu-id="5670a-118">혼합된 현실에서 실제 환경과 holographic 개체 혼합 되어 있으므로 수 있습니다 상호 작용할 수 없는 개체는 이해 하기가 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-118">In mixed reality, since the holographic objects are mixed with the real-world environment, it could be difficult to understand which objects are interactable.</span></span> <span data-ttu-id="5670a-119">환경에서 상호 작용할 수 없는 개체에 대 한 상태 각 입력에 대해 차별화 된 시각적 피드백을 제공 하는 것이 반드시 합니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-119">For any interactable objects in your experience, it is important to provide differentiated visual feedback for each input state.</span></span> <span data-ttu-id="5670a-120">이렇게 하면 사용자 이해 사용자 경험의 어느 부분이 상호 작용할 수 없는 이며 일관성 있는 상호 작용 메서드를 사용 하 여 사용자를 확신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-120">This helps the user understand which part of your experience is interactable and makes the user confident with consistent interaction method.</span></span>

<span data-ttu-id="5670a-121">모든 개체에 대 한 해당 사용자와 상호 작용할 수, 것이 좋습니다 이러한 세 개의 입력 상태에 대 한 다양 한 시각적 피드백을 할:</span><span class="sxs-lookup"><span data-stu-id="5670a-121">For any objects that user can interact with, we recommended to have different visual feedback for these three input states:</span></span>
* <span data-ttu-id="5670a-122">**관찰**: 개체의 기본 유휴 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-122">**Observation**: Default idle state of the object.</span></span>
* <span data-ttu-id="5670a-123">**대상**: 개체를 응시 커서를 사용 하 여 대상으로 하는 경우에 근접 또는 동영상 컨트롤러의 포인터 손가락으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-123">**Targeted**: When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
* <span data-ttu-id="5670a-124">**누른**: 어 탭 제스처, 손가락 누르거나 동작 컨트롤러의 선택 단추를 사용 하 여 개체를 누를 때 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-124">**Pressed**: When the object is pressed with air-tap gesture, finger press or motion controller's select button.</span></span>

<span data-ttu-id="5670a-125">![Holographic 단추](images/640px-interactibleobject-holographicbutton-650px.jpg)</span><span class="sxs-lookup"><span data-stu-id="5670a-125">![Holographic button](images/640px-interactibleobject-holographicbutton-650px.jpg)</span></span><br>
<span data-ttu-id="5670a-126">*상태 대상 상태 및 상태를 누르면 관찰*</span><span class="sxs-lookup"><span data-stu-id="5670a-126">*Observation state, targeted state, and pressed state*</span></span>

<span data-ttu-id="5670a-127">Windows Mixed Reality 시작 메뉴 및 앱 바 단추 입력된 상태를 다른 시각화의 예제를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-127">In Windows Mixed Reality, you can find the examples of visualizing different input states on Start menu and App Bar buttons.</span></span> <span data-ttu-id="5670a-128">사용자의 입력된 상태에 대 한 시각적 피드백을 제공할 강조 표시 하거나 확장 하는 기법을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-128">You can use techniques such as highlighting or scaling to provide visual feedback to the user’s input states.</span></span>

<span data-ttu-id="5670a-129">입력을 추적 하는 완전히 표시 된 직접 지원 하기 때문 HoloLens 2에서는 바늘 근접도에 따라 추가 affordances를 제공할 수 있습니다 했습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-129">In HoloLens 2, since it supports fully articulated hand tracking input, we can provide additional affordances based on the proximity to the hands.</span></span> <span data-ttu-id="5670a-130">합니다 [HoloLens 2 단추](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) 이 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-130">The [Button in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) shows this example.</span></span>

![Pressable 단추](images/640px-interactibleobject-pressablebutton-650px.jpg)<br>




## <a name="interactable-object-samples"></a><span data-ttu-id="5670a-132">상호 작용할 수 없는 개체 샘플</span><span class="sxs-lookup"><span data-stu-id="5670a-132">Interactable object samples</span></span>

### <a name="mesh-button"></a><span data-ttu-id="5670a-133">메시 단추</span><span class="sxs-lookup"><span data-stu-id="5670a-133">Mesh button</span></span>

![메시 단추](images/640px-interactibleobject-meshbutton.jpg)

<span data-ttu-id="5670a-135">이들은 상호 작용할 수 없는 개체로 기본 형식 및 가져온된 3D 메시를 사용 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-135">These are examples using primitives and imported 3D meshes as Interactable objects.</span></span> <span data-ttu-id="5670a-136">각 입력된 상호 작용 상태를 응답에 서로 다른 규모, 오프셋 및 색 값을 쉽게 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-136">You can easily assign different scale, offset and color values to respond to each input interaction state.</span></span>

### <a name="toolbar"></a><span data-ttu-id="5670a-137">도구 모음</span><span class="sxs-lookup"><span data-stu-id="5670a-137">Toolbar</span></span>

![도구 모음](images/640px-interactibleobject-toolbar.jpg)

<span data-ttu-id="5670a-139">도구 모음에는 혼합된 현실 환경에서 널리 사용 되는 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-139">A toolbar is a widely used pattern in mixed reality experiences.</span></span> <span data-ttu-id="5670a-140">와 같은 추가 동작을 사용 하 여 단추의 간단한 모음입니다 [Billboarding 및 tag-along](billboarding-and-tag-along.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-140">It is a simple collection of buttons with additional behaviors such as [Billboarding and tag-along](billboarding-and-tag-along.md).</span></span> <span data-ttu-id="5670a-141">이 예제는 MixedRealityToolkit에서 Billboarding 및 tag-along 스크립트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-141">This example uses a Billboarding and tag-along script from the MixedRealityToolkit.</span></span> <span data-ttu-id="5670a-142">속도 및 임계값 값 이동 거리를 포함 하 여 자세한 동작 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-142">You can control detailed behaviors including distance, moving speed and threshold values.</span></span>

### <a name="traditional-button"></a><span data-ttu-id="5670a-143">전통적인 단추</span><span class="sxs-lookup"><span data-stu-id="5670a-143">Traditional button</span></span>

![전통적인 단추](images/640px-interactibleobject-traditionalbutton.jpg)

<span data-ttu-id="5670a-145">이 예제에서는 일반적인 2D 스타일 단추를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-145">This example shows a traditional 2D style button.</span></span> <span data-ttu-id="5670a-146">각 입력된 상태는 약간 다른 깊이 애니메이션 속성에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-146">Each input state has a slightly different depth and animation property.</span></span>

### <a name="other-examples"></a><span data-ttu-id="5670a-147">다른 예제</span><span class="sxs-lookup"><span data-stu-id="5670a-147">Other examples</span></span>

<span data-ttu-id="5670a-148">![푸시 단추](images/640px-interactibleobject-pushbutton.jpg)</span><span class="sxs-lookup"><span data-stu-id="5670a-148">![Push button](images/640px-interactibleobject-pushbutton.jpg)</span></span><br>
<span data-ttu-id="5670a-149">*푸시 단추*</span><span class="sxs-lookup"><span data-stu-id="5670a-149">*Push button*</span></span>
<br>
<span data-ttu-id="5670a-150">![실제 수명 개체](images/640px-interactibleobject-reallifeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="5670a-150">![Real Life object](images/640px-interactibleobject-reallifeobject.jpg)</span></span><br>
<span data-ttu-id="5670a-151">*실제 개체*</span><span class="sxs-lookup"><span data-stu-id="5670a-151">*Real life object*</span></span>

<span data-ttu-id="5670a-152">HoloLens를 사용 하 여 물리적 공간을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-152">With HoloLens, you can leverage physical space.</span></span> <span data-ttu-id="5670a-153">실제 벽 holographic 누름 단추를 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-153">Imagine a holographic push button on a physical wall.</span></span> <span data-ttu-id="5670a-154">또는 실제 테이블에서 coffee cup 어떤가요?</span><span class="sxs-lookup"><span data-stu-id="5670a-154">Or how about a coffee cup on a real table?</span></span> <span data-ttu-id="5670a-155">소프트웨어 모델링에서 가져온 3D 모델을 사용 하 여 실제 개체와 유사 하는 상호 작용할 수 없는 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-155">Using 3D models imported from modeling software, we can create an Interactable object that resembles real life object.</span></span> <span data-ttu-id="5670a-156">디지털 개체 이므로 마법 상호 작용을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5670a-156">Since it's a digital object, we can add magical interactions to it.</span></span>

## <a name="interactable-object-in-mixed-reality-toolkit"></a><span data-ttu-id="5670a-157">혼합 현실 도구 키트의 상호 작용할 수 없는 개체</span><span class="sxs-lookup"><span data-stu-id="5670a-157">Interactable object in Mixed Reality Toolkit</span></span>
<span data-ttu-id="5670a-158">찾을 수 있습니다는 [Interactable의 예는 혼합 현실 도구 키트의 개체](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span><span class="sxs-lookup"><span data-stu-id="5670a-158">You can find the [examples of Interactable object in Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)</span></span>


## <a name="see-also"></a><span data-ttu-id="5670a-159">참조</span><span class="sxs-lookup"><span data-stu-id="5670a-159">See also</span></span>
* [<span data-ttu-id="5670a-160">혼합된 현실 도구 키트-Unity pressable 단추</span><span class="sxs-lookup"><span data-stu-id="5670a-160">Pressable Button on Mixed Reality Toolkit-Unity</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="5670a-161">개체 컬렉션</span><span class="sxs-lookup"><span data-stu-id="5670a-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="5670a-162">빌보드 및 tag-along</span><span class="sxs-lookup"><span data-stu-id="5670a-162">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
