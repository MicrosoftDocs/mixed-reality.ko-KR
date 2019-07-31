---
title: 손으로 가리키고 커밋
description: 가리키고 커밋 입력 모델 개요
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, interaction, design, hololens, hands, far, point and commit
ms.openlocfilehash: 4e19a7fd95bac42283ce3e3176a1363afda8f220
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414546"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="75577-104">손으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="75577-104">Point and commit with hands</span></span>
<span data-ttu-id="75577-105">손으로 가리키고 커밋은 멀리 떨어져 있는 2D 콘텐츠 및 3D 개체를 타기팅, 선택 및 조작할 수 있는 입력 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="75577-105">Point and commit with hands is an input model that enables users to target, select and manipulate 2D content and 3D objects in the distance.</span></span> <span data-ttu-id="75577-106">이 “먼 거리” 상호 작용 기술은 혼합 현실에만 해당되며, 인간이 실제 세상과 자연스럽게 상호 작용하는 방식은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="75577-106">This "far" interaction technique is unique to mixed reality, and is not a way humans naturally intereact with the real world.</span></span> <span data-ttu-id="75577-107">예를 들어, 슈퍼 영웅 영화인 *엑스맨*에서 등장 인물 [매그니토](https://en.wikipedia.org/wiki/Magneto_(comics))는 멀리 떨어져 있는 물체를 손으로 뻗어 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-107">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) is capable of reaching out and manipulating a far object in the distance with his hands.</span></span> <span data-ttu-id="75577-108">이것은 사람들이 실제로 할 수 있는 일이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="75577-108">This is not something humans can do in reality.</span></span> <span data-ttu-id="75577-109">HoloLens(AR) 및 혼합 현실(MR)에서는 사용자에게 이러한 마법의 힘을 제공하여 실제 세상의 물리적 제약을 극복함으로써 홀로그램 콘텐츠로 신나는 경험을 해볼 수 있을 뿐만 아니라 더 효과적이고 효율적인 방식으로 상호 작용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="75577-109">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power, breaking the physical constraint of the real world, not only to have a fun experience with holographic contents but also to make user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="75577-110">장치 지원</span><span class="sxs-lookup"><span data-stu-id="75577-110">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="75577-111"><strong>입력 모델</strong></span><span class="sxs-lookup"><span data-stu-id="75577-111"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="75577-112"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="75577-112"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="75577-113"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="75577-113"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="75577-114"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="75577-114"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="75577-115">손으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="75577-115">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="75577-116">❌ 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="75577-116">❌ Not supported</span></span></td>
     <td><span data-ttu-id="75577-117">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="75577-117">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="75577-118">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="75577-118">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="75577-119">먼 거리 손 조작이라고도 하는 가리키고 커밋 기능은 새롭게 연결된 손 추적 시스템을 활용하는 새로운 기능 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="75577-119">Point and commit, also known as hands far, is one of the new features that utilizes the new articulated hand-tracking system.</span></span> <span data-ttu-id="75577-120">이 입력 모델은 모션 컨트롤러를 사용한 몰입형 헤드셋의 기본 입력 모델이기도합니다.</span><span class="sxs-lookup"><span data-stu-id="75577-120">This input model is also the primary input model on immersive headsets through the use of motion controllers.</span></span>

## <a name="hand-rays"></a><span data-ttu-id="75577-121">손 레이</span><span class="sxs-lookup"><span data-stu-id="75577-121">Hand rays</span></span>

<span data-ttu-id="75577-122">HoloLens 2에서 사용자의 손바닥 중앙에서 나오는 손 레이를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-122">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="75577-123">이 레이는 손의 연장선으로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="75577-123">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="75577-124">도넛 모양의 커서가 레이 끝에 연결되어 레이가 대상 개체와 교차하는 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="75577-124">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="75577-125">그런 다음, 커서가 닿는 개체는 손에서 제스처 명령을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-125">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="75577-126">엄지 손가락과 집게 손가락을 통해 기본적인 제스처 명령이 트리거되면서 에어 탭 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="75577-126">This basic gestural command is triggered by using the thumb and index finger to perform the air-tap action.</span></span> <span data-ttu-id="75577-127">손 레이를 사용하여 가리키고 에어 탭을 사용하여 커밋함으로써, 사용자는 단추 또는 하이퍼링크를 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-127">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="75577-128">좀 더 복잡한 제스처의 경우, 떨어진 위치에서 웹 콘텐츠를 탐색하고 3D 개체를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-128">With more composite gestures, users are capable of navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="75577-129">손 레이의 시각적 디자인은 아래 설명된 것처럼 이러한 가리키기 및 커밋 상태에도 대응해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75577-129">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

* <span data-ttu-id="75577-130">*가리키기* 상태에서 레이는 대시이고 커서는 도넛 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="75577-130">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
* <span data-ttu-id="75577-131">*커밋* 상태에서 레이는 실선으로 바뀌고 커서는 점으로 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="75577-131">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>

<span data-ttu-id="75577-132">![손 레이의 가리키기 및 커밋 상태](images/Hand-Rays-720px.jpg)</span><span class="sxs-lookup"><span data-stu-id="75577-132">![Pointing and commit states for hand rays](images/Hand-Rays-720px.jpg)</span></span><br>
<span data-ttu-id="75577-133">*손 레이의 가리키기(왼쪽) 및 커밋(오른쪽) 상태*</span><span class="sxs-lookup"><span data-stu-id="75577-133">*Pointing (left) and commit (right) states for hand rays*</span></span>

## <a name="transition-between-near-and-far"></a><span data-ttu-id="75577-134">근거리 및 원거리 간 전환</span><span class="sxs-lookup"><span data-stu-id="75577-134">Transition between near and far</span></span>

<span data-ttu-id="75577-135">“집게 손가락으로 가리키기”와 같은 특정 제스처를 사용하여 레이 방향을 지정하는 대신, 손바닥 중앙에서 나오고, 손가락 모으기 및 잡기와 같은 좀 더 정교한 제스처를 위해 5개의 손가락을 자유롭게 사용하고 예약하는 방법을 고안했습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-135">Instead of using specific gestures, such as "pointing with index finger", to direct the ray, we designed the ray coming out from the center of the palm, releasing and reserving the five fingers for more manipulative gestures, such as pinch and grab.</span></span> <span data-ttu-id="75577-136">이 디자인에서는 근거리 및 원거리 상호 작용에 정확히 동일한 손 제스처 세트를 사용하는 한 가지의 상상 모델만 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75577-136">With this design, we create only one mental model, supporting exactly the same set of hand gestures for both near and far interaction.</span></span> <span data-ttu-id="75577-137">즉, 다른 거리에 있는 개체를 조작하는 데 동일한 잡기 제스처를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-137">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="75577-138">레이 호출은 다음과 같이 자동으로 진행되며 근접성을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="75577-138">The invocation of the rays is automatic and proximity based as follows:</span></span>

*  <span data-ttu-id="75577-139">개체가 팔을 뻗어 닿을 수 있는 거리(약 50cm) 안에 있는 경우 근거리 상호 작용을 위해 레이가 자동으로 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="75577-139">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
*  <span data-ttu-id="75577-140">개체가 50cm보다 더 멀리 떨어져 있으면 레이가 켜집니다.</span><span class="sxs-lookup"><span data-stu-id="75577-140">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="75577-141">이러한 전환은 원활하고 매끄럽게 진행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75577-141">The transition should be smooth and seamless.</span></span>

<span data-ttu-id="75577-142">![근거리 및 원거리 상호 작용 모두에 동일한 손 제스처 세트가 사용됩니다.](images/Transition-Between-Near-And-Far-720px.jpg)</span><span class="sxs-lookup"><span data-stu-id="75577-142">![The same set of hand gestures are used for both near and far interaction](images/Transition-Between-Near-And-Far-720px.jpg)</span></span><br>
<span data-ttu-id="75577-143">*근거리 및 원거리 상호 작용 모두에 동일한 손 제스처 세트가 사용됩니다.*</span><span class="sxs-lookup"><span data-stu-id="75577-143">*The same set of hand gestures are used for both near and far interaction.*</span></span>

## <a name="2d-slate-interaction"></a><span data-ttu-id="75577-144">2D 슬레이트 상호 작용</span><span class="sxs-lookup"><span data-stu-id="75577-144">2D slate interaction</span></span>

<span data-ttu-id="75577-145">2D 슬레이트는 웹 브라우저와 같은 2D 앱 콘텐츠를 호스트하는 홀로그램 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="75577-145">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="75577-146">2D 슬레이트와 먼 거리에서 상호 작용할 경우의 기본적인 개념은 손 레이를 사용하여 타기팅하고 에어 탭을 사용하여 선택하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="75577-146">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="75577-147">손 레이로 타기팅한 후에는 에어 탭을 수행하여 하이퍼링크 또는 단추를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-147">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="75577-148">한 손으로 “에어 탭하고 끌기”를 수행하여 슬레이트 콘텐츠를 위아래로 스크롤할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-148">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="75577-149">두 손으로 에어 탭을 수행하고 끄는 상대적 동작으로 슬레이트 콘텐츠를 확대 및 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-149">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="75577-150">손 레이가 모서리와 가장자리를 직접 향하게 하면 가장 가까운 조작 어포던스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="75577-150">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="75577-151">“잡기 및 끌기” 조작 어포던스에서 사용자는 모서리 어포던스를 통해 균일하게 크기를 조정하고, 가장자리 어포던스를 통해 슬레이트를 재배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-151">By "grab and drag" manipulation affordances, users can perform uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="75577-152">2D 슬레이트의 맨 위에 있는 홀로바를 잡아서 끌면 전체 슬레이트를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-152">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

![2D 슬레이트 상호 작용](images/2D-Slate-Interaction-Far-720px.jpg)

<span data-ttu-id="75577-154">2D 슬레이트 조작:</span><span class="sxs-lookup"><span data-stu-id="75577-154">For manipulating the 2D slate:</span></span><br>

* <span data-ttu-id="75577-155">사용자는 모서리 또는 가장자리를 손 레이로 가리켜 가장 가까운 조작 어포던스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="75577-155">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="75577-156">사용자는 어포던스에 조작 제스처를 적용하여 모서리 어포던스를 통해 균일하게 크기를 조정하고, 가장자리 어포던스를 통해 슬레이트를 재배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-156">By applying a manipulation gesture on the affordance, users can perform uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="75577-157">2D 슬레이트의 맨 위에 있는 홀로바에 조작 제스처를 적용하여 전체 슬레이트를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-157">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>

<br>

## <a name="3d-object-manipulation"></a><span data-ttu-id="75577-158">3D 개체 조작</span><span class="sxs-lookup"><span data-stu-id="75577-158">3D object manipulation</span></span>

<span data-ttu-id="75577-159">직접 조작에서 사용자는 어포던스 기반 조작 및 비어포던스 기반 조작의 두 가지 방법으로 3D 개체를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-159">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="75577-160">가리키기 및 커밋 모델에서 사용자는 손 레이를 통해 정확히 동일한 작업을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-160">In the point and commit model, users are capable of achieving exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="75577-161">추가 학습은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-161">No additional learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="75577-162">어포던스 기반 조작</span><span class="sxs-lookup"><span data-stu-id="75577-162">Affordance-based manipulation</span></span>
<span data-ttu-id="75577-163">사용자는 손 레이를 사용하여 경계 상자 및 조작 어포던스를 가리키고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="75577-163">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="75577-164">사용자는 경계 상자에 조작 제스처를 적용하여 전체 개체를 이동하고, 가장자리 어포던스를 적용하여 회전하고, 모서리 어포던스를 적용하여 균일하게 크기를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-164">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

![어포던스 기반 조작](images/3D-Object-Manipulation-Far-720px.jpg) <br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="75577-166">비어포던스 기반 조작</span><span class="sxs-lookup"><span data-stu-id="75577-166">Non-affordance based manipulation</span></span>
<span data-ttu-id="75577-167">사용자가 직접 손 레이로 가리켜 경계 상자를 표시한 다음, 조작 제스처를 직접 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="75577-167">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="75577-168">한 손을 사용할 경우 개체의 변환 및 회전은 손의 동작 및 방향과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="75577-168">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="75577-169">두 손을 사용할 경우 두 손의 상대적 동작에 따라 변환, 크기 조정 및 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-169">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

## <a name="instinctual-gestures"></a><span data-ttu-id="75577-170">직관적 제스처</span><span class="sxs-lookup"><span data-stu-id="75577-170">Instinctual gestures</span></span>
<span data-ttu-id="75577-171">가리키기 및 커밋을 위한 직관적 제스처 개념은 [손을 사용한 직접 조작](direct-manipulation.md)의 개념과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="75577-171">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="75577-172">사용자가 3D 개체에 대해 수행해야 하는 제스처는 UI 어포던스의 디자인에 따라 유도됩니다.</span><span class="sxs-lookup"><span data-stu-id="75577-172">The gestures users perform on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="75577-173">예를 들어, 사용자는 5개의 손가락을 모두 사용해서 더 큰 개체를 잡을 수도 있지만, 작은 제어점이 사용자가 엄지 손가락과 집게 손가락으로 손가락을 모으도록 유도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75577-173">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to grab a larger object using all five fingers.</span></span>

![직관적 제스처](images/Instinctual-Gestures-Far-720px.jpg)<br>

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="75577-175">손과 6 DoF 컨트롤러 간의 대칭 디자인</span><span class="sxs-lookup"><span data-stu-id="75577-175">Symmetric design between hands and 6 DoF controller</span></span> 
<span data-ttu-id="75577-176">원거리 상호 작용을 위한 가리키기 및 커밋 개념은 처음에는 MRP(Mixed Reality 포털)를 위해 만들어지고 정의되었습니다. 이 포털에서 사용자는 몰입형 헤드셋을 착용하고 모션 컨트롤러를 통해 3D 개체와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="75577-176">The concept of point and commit for far interaction was initially created and defined for the Mixed Reality Portal (MRP) where a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="75577-177">모션 컨트롤러는 멀리 떨어진 개체를 가리키고 조작하기 위해 레이를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="75577-177">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="75577-178">다른 작업을 추가로 커밋하기 위한 단추가 컨트롤러에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="75577-178">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="75577-179">레이의 상호 작용 모델을 활용하고 양손에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="75577-179">We leverage the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="75577-180">이 대칭 디자인에서 MRP에 친숙한 사용자는 HoloLen 2를 사용할 때 먼 거리 가리키기 및 조작을 위해 다른 상호 작용 모델을 학습할 필요가 없으며, 그 반대의 경우도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="75577-180">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLen 2, and vice versa.</span></span>    

![손과 6 DoF 컨트롤러 간의 대칭 디자인](images/Symmetric-Design-For-Rays-720px.jpg)<br>


## <a name="see-also"></a><span data-ttu-id="75577-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75577-182">See also</span></span>
* [<span data-ttu-id="75577-183">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="75577-183">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="75577-184">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="75577-184">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="75577-185">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="75577-185">Instinctual interactions</span></span>](interaction-fundamentals.md)

