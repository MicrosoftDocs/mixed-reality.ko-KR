---
title: 수동으로 직접 조작
description: 직접 조작 입력 모델의 개요
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, Gaze, gaze targeting, interaction, design, hands near, HoloLens
ms.openlocfilehash: e0b0e6273917df071f49eb0108039ebe204bbc12
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105946"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="8466e-104">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="8466e-104">Direct manipulation with hands</span></span>

![Button](images/UX/UX_Hero_Manipulation.jpg)

<span data-ttu-id="8466e-106">직접 조작은 홀로그램을 손으로 직접 터치하게 되는 입력 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="8466e-107">이 개념의 기본 아이디어는 개체가 실제 세계에서처럼 작동하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="8466e-108">단추는 간단히 눌러서 활성화하고, 개체는 잡아서 선택할 수 있으며, 2D 콘텐츠는 가상의 터치 스크린처럼 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="8466e-109">이렇게 하면 사용자가 직접 조작하면서 쉽고 재미있게 학습할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-109">This makes direct manipulation easy for users to learn, and fun.</span></span> <span data-ttu-id="8466e-110">팔을 뻗어 닿을 수 있는 콘텐츠와 상호 작용하는 데 가장 적합하다는 점에서 “근거리” 입력 모델로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-110">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

<span data-ttu-id="8466e-111">직접 조작은 어포던스를 기준으로 합니다. 즉, 사용자 친화적입니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-111">Direct manipulation is affordance-based, meaning it's user friendly.</span></span> <span data-ttu-id="8466e-112">사용자를 교육하기 위한 기호화된 제스처는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-112">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="8466e-113">모든 상호 작용은 사용자가 터치하거나 잡을 수 있는 시각적 요소를 중심으로 구축됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-113">All interactions are built around a visual element that you can touch or grab.</span></span>

## <a name="device-support"></a><span data-ttu-id="8466e-114">장치 지원</span><span class="sxs-lookup"><span data-stu-id="8466e-114">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="8466e-115"><strong>입력 모델</strong></span><span class="sxs-lookup"><span data-stu-id="8466e-115"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="8466e-116"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8466e-116"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="8466e-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="8466e-117"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="8466e-118"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="8466e-118"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="8466e-119">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="8466e-119">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="8466e-120">❌ 지원 안 됨</span><span class="sxs-lookup"><span data-stu-id="8466e-120">❌ Not supported</span></span></td>
     <td><span data-ttu-id="8466e-121">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="8466e-121">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="8466e-122">➕ 대안으로 <a href="point-and-commit.md">손으로 가리키고 커밋</a>이 권장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-122">➕ An alternative, <a href="point-and-commit.md">point and commit with hands</a> is recommended.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="8466e-123">직접 조작은 HoloLens 2의 기본 입력 모델이며, 새로운 연결형 손 추적 시스템을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="8466e-124">이 입력 모델은 모션 컨트롤러를 사용하여 몰입형 헤드셋에서도 사용할 수 있지만 개체 조작 이외의 상호 작용을 위한 기본 수단으로는 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-124">The input model is also available on immersive headsets through the use of motion controllers, but is not recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="8466e-125">HoloLens(1세대)에는 직접 조작을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-125">Direct manipulation is not available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="8466e-126">충돌 가능한 손끝</span><span class="sxs-lookup"><span data-stu-id="8466e-126">Collidable fingertip</span></span>

<span data-ttu-id="8466e-127">HoloLens 2에서 사용자의 실제 손은 왼손 및 오른손 골격 모델로 인식 및 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-127">On HoloLens 2, the user's hands are recognized and interpreted as left and right hand skeletal models.</span></span> <span data-ttu-id="8466e-128">손으로 홀로그램을 직접 터치한다는 개념을 적절히 구현하기 위해 각 손 골격 모델의 5개 손끝에 5개의 충돌체(collider)를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-128">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="8466e-129">그러나 촉각 피드백이 부족하기 때문에 10개의 충돌 가능한 손끝이 홀로그램과 예기치 않은 충돌을 유발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-129">However, due to the lack of tactile feedback, ten collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="8466e-130">따라서 각 집게 손가락에만 충돌체(collider)를 놓는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-130">Hence, we suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="8466e-131">아래 이미지와 같이, 충돌 가능한 집게 손끝은 여전히 다른 손가락과 관련된 다양한 터치 제스처(예: 한 손가락으로 누르기, 한 손가락으로 탭하기, 두 손가락으로 누르기, 다섯 손가락으로 누르기)를 위한 활성 터치 포인트 역할을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-131">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers, such as One-finger press, One-finger tap, Two-finger press and Five-finger press, as shown in the image below.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8466e-132">![충돌 가능한 손끝](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-132">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="8466e-133">**충돌 가능한 손끝**</span><span class="sxs-lookup"><span data-stu-id="8466e-133">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-134">![한 손가락으로 누르기](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-134">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="8466e-135">**한 손가락으로 누르기**</span><span class="sxs-lookup"><span data-stu-id="8466e-135">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-136">![한 손가락으로 탭하기](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-136">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="8466e-137">**한 손가락으로 탭하기**</span><span class="sxs-lookup"><span data-stu-id="8466e-137">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-138">![다섯 손가락으로 누르기](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-138">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="8466e-139">**다섯 손가락으로 누르기**</span><span class="sxs-lookup"><span data-stu-id="8466e-139">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="8466e-140">구형 충돌체(collider)</span><span class="sxs-lookup"><span data-stu-id="8466e-140">Sphere collider</span></span>

<span data-ttu-id="8466e-141">임의의 일반 셰이프를 사용하는 대신, 구형 충돌체(collider)를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-141">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="8466e-142">그러면, 시각적 렌더링을 통해 근거리 대상 지정에 더 나은 단서를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-142">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="8466e-143">터치 정확도를 높이려면 구의 지름이 집게 손가락의 두께와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-143">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="8466e-144">손 API를 호출하여 손가락 두께 변수를 쉽게 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-144">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="8466e-145">손끝 커서</span><span class="sxs-lookup"><span data-stu-id="8466e-145">Fingertip cursor</span></span>

<span data-ttu-id="8466e-146">집게 손끝에 충돌 가능한 구형을 렌더링하는 것 외에, 더 나은 근거리 대상 지정 환경을 얻기 위해 고급 손끝 커서를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-146">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to interactively achieve a better near-targeting experience.</span></span> <span data-ttu-id="8466e-147">집게 손끝에 연결된 도넛형 커서입니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-147">It is a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="8466e-148">아래에 설명된 것처럼, 근접성에 따라 대상의 방향 및 크기 변화에 동적으로 반응합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-148">According to proximity, it dynamically reacts to a target in terms of orientation and size as detailed below:</span></span>

* <span data-ttu-id="8466e-149">집게 손가락을 홀로그램 쪽으로 움직이면 커서는 항상 홀로그램 표면에 평행하게 움직이며 크기가 서서히 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-149">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size accordingly.</span></span>
* <span data-ttu-id="8466e-150">손가락으로 표면을 터치하는 즉시, 커서가 점으로 축소되고 터치 이벤트를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-150">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="8466e-151">대화형 피드백을 사용하면 사용자는 아래와 같이 하이퍼링크 트리거 또는 단추 누르기와 같은 높은 정확도의 근거리 대상 지정 작업을 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-151">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="8466e-152">![손끝 커서 멀리](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-152">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="8466e-153">**손끝 커서 멀리**</span><span class="sxs-lookup"><span data-stu-id="8466e-153">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-154">![손끝 커서 가까이](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-154">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="8466e-155">**손끝 커서 가까이**</span><span class="sxs-lookup"><span data-stu-id="8466e-155">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-156">![손끝 커서 접촉](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-156">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="8466e-157">**손끝 커서 접촉**</span><span class="sxs-lookup"><span data-stu-id="8466e-157">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="8466e-158">근접 셰이더가 있는 경계 상자</span><span class="sxs-lookup"><span data-stu-id="8466e-158">Bounding box with proximity shader</span></span>

<span data-ttu-id="8466e-159">홀로그램 자체에는 촉각 피드백 부족을 보정하기 위해 시각적 및 청각적 피드백을 둘 다 제공하는 기능도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-159">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="8466e-160">이를 위해 근접 셰이더를 포함하는 경계 상자 개념을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-160">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="8466e-161">경계 상자는 3D 개체를 둘러싸는 최소 체적 영역입니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-161">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="8466e-162">경계 상자에는 근접 셰이더라는 대화형 렌더링 메커니즘이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-162">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="8466e-163">근접 셰이더는 다음과 같이 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-163">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8466e-164">![시각적 피드백이 있는 가리키기(멀리)](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-164">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="8466e-165">**가리키기(멀리)**</span><span class="sxs-lookup"><span data-stu-id="8466e-165">**Hover (far)**</span></span><br>
       <span data-ttu-id="8466e-166">집게 손가락이 범위 내에 있는 경우 손끝 스포트라이트가 경계 상자 표면에 캐스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-166">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-167">![시각적 피드백이 있는 가리키기(가까이)](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-167">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="8466e-168">**가리키기(가까이)**</span><span class="sxs-lookup"><span data-stu-id="8466e-168">**Hover (near)**</span></span><br>
        <span data-ttu-id="8466e-169">손끝이 화면에 가까워질수록, 스포트라이트도 그에 따라 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-169">When the fingertip gets closer to the surface, the spotlight shrinks accordingly.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-170">![접촉 시작](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-170">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="8466e-171">**접촉 시작**</span><span class="sxs-lookup"><span data-stu-id="8466e-171">**Contact begins**</span></span><br>
       <span data-ttu-id="8466e-172">손끝이 표면을 터치하는 즉시, 전체 경계 상자의 색상이 바뀌거나 터치 상태를 반영하는 시각적 효과가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-172">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-173">![접촉 끝](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-173">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="8466e-174">**접촉 끝**</span><span class="sxs-lookup"><span data-stu-id="8466e-174">**Contact ends**</span></span><br>
       <span data-ttu-id="8466e-175">또한 시각적 터치 피드백을 향상시키기 위해 음향 효과를 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-175">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="8466e-176">누를 수 있는 단추</span><span class="sxs-lookup"><span data-stu-id="8466e-176">Pressable button</span></span>

<span data-ttu-id="8466e-177">충돌 가능한 손끝을 사용하면 사용자가 기본적인 홀로그래픽 UI 구성 요소(예: 누를 수 있는 단추)와 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-177">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="8466e-178">누를 수 있는 단추는 직접적인 손가락 누르기에 맞게 조정된 홀로그래픽 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-178">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="8466e-179">다시 말하지만, 촉각 피드백이 부족하기 때문에 누를 수 있는 단추에는 촉각 피드백 관련 이슈를 해결하기 위한 몇 가지 메커니즘이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-179">Again, due to the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="8466e-180">첫 번째 메커니즘은 근접 셰이더가 있는 경계 상자이며, 이전 섹션에 자세히 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-180">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="8466e-181">이 메커니즘은 사용자가 단추에 접근하여 접촉할 때 더 근접한 느낌을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-181">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="8466e-182">두 번째 메커니즘은 누르기입니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-182">The second mechanism is depression.</span></span> <span data-ttu-id="8466e-183">누르기는 손끝이 단추에 닿은 후 아래쪽을 누르는 감각을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-183">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="8466e-184">이 메커니즘은 단추가 손끝에 맞춰 깊이 축을 따라 움직이도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-184">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="8466e-185">단추는 지정된 깊이(누를 때)에 도달하거나 해당 깊이를 통과한 후 떠나면(뗄 때) 트리거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-185">The button can be triggered when it reaches a designated depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="8466e-186">단추가 트리거될 때 피드백을 향상시키기 위해 음향 효과를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-186">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8466e-187">![누를 수 있는 단추 멀리](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-187">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="8466e-188">**멀리 있는 손가락**</span><span class="sxs-lookup"><span data-stu-id="8466e-188">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-189">![누를 수 있는 단추 가까이](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-189">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="8466e-190">**접근하는 손가락**</span><span class="sxs-lookup"><span data-stu-id="8466e-190">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-191">![누를 수 있는 단추 접촉 시작](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-191">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="8466e-192">**접촉 시작**</span><span class="sxs-lookup"><span data-stu-id="8466e-192">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-193">![누를 수 있는 단추 누르기](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-193">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="8466e-194">**아래로 누르기**</span><span class="sxs-lookup"><span data-stu-id="8466e-194">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="8466e-195">2D 슬레이트 상호 작용</span><span class="sxs-lookup"><span data-stu-id="8466e-195">2D slate interaction</span></span>

<span data-ttu-id="8466e-196">2D 슬레이트는 웹 브라우저와 같은 2D 앱 콘텐츠를 호스트하는 홀로그램 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-196">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="8466e-197">직접 조작을 통해 2D 슬레이트와 상호 작용하기 위한 디자인 개념은 실제 터치 스크린과 상호 작용하는 상상 모델을 활용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-197">The design concept for interacting with a 2D slate via direct manipulation is to leverage the mental model of interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="8466e-198">슬레이트 접촉 부분과 상호 작용하려면</span><span class="sxs-lookup"><span data-stu-id="8466e-198">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8466e-199">![터치](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-199">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="8466e-200">**터치**</span><span class="sxs-lookup"><span data-stu-id="8466e-200">**Touch**</span></span><br>
       <span data-ttu-id="8466e-201">집게 손가락으로 하이퍼링크 또는 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-201">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-202">![스크롤](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-202">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="8466e-203">**스크롤**</span><span class="sxs-lookup"><span data-stu-id="8466e-203">**Scroll**</span></span><br>
        <span data-ttu-id="8466e-204">집게 손가락으로 슬레이트 콘텐츠 위/아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-204">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-205">![확대/축소](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-205">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="8466e-206">**확대/축소**</span><span class="sxs-lookup"><span data-stu-id="8466e-206">**Zoom**</span></span><br>
       <span data-ttu-id="8466e-207">사용자는 2개의 집게 손가락을 사용하여 손가락의 상대적 모션에 따라 슬레이트 콘텐츠를 확대 및 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-207">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="8466e-208">2D 슬레이트 자체를 조작하려면</span><span class="sxs-lookup"><span data-stu-id="8466e-208">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="8466e-209">![이동](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-209">![Move](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="8466e-210">**이동**</span><span class="sxs-lookup"><span data-stu-id="8466e-210">**Move**</span></span><br>
       <span data-ttu-id="8466e-211">손을 모서리와 가장자리 쪽으로 이동하여 가장 가까운 조작 어포던스를 드러냅니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-211">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="8466e-212">2D 슬레이트의 맨 위에 있는 홀로바를 잡으면, 슬레이트 전체를 옮길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-212">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-213">![배율](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-213">![Scale](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="8466e-214">**배율**</span><span class="sxs-lookup"><span data-stu-id="8466e-214">**Scale**</span></span><br>
        <span data-ttu-id="8466e-215">조작 어포던스를 잡고, 모서리 어포던스를 통해 균일하게 크기를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-215">Grab the manipulation affordances and perform uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-216">![재배치](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-216">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="8466e-217">**재배치**</span><span class="sxs-lookup"><span data-stu-id="8466e-217">**Reflow**</span></span><br>
       <span data-ttu-id="8466e-218">조작 어포던스를 잡고, 모서리 어포던스를 통해 재배치를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-218">Grab the manipulation affordances and perform reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="8466e-219">3D 개체 조작</span><span class="sxs-lookup"><span data-stu-id="8466e-219">3D object manipulation</span></span>

<span data-ttu-id="8466e-220">HoloLens 2에서는 사용자가 3D 개체마다 경계 상자를 적용하여 손으로 3D 홀로그래픽 개체를 겨냥하고 조작할 수 잇습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-220">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="8466e-221">경계 상자는 근접 셰이더를 통해 더 나은 깊이 인식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-221">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="8466e-222">경계 상자를 사용하면 3D 개체 조작을 위해 두 가지 디자인 방식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-222">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="8466e-223">어포던스 기반 조작</span><span class="sxs-lookup"><span data-stu-id="8466e-223">Affordance-based manipulation</span></span>

<span data-ttu-id="8466e-224">어포던스 기반 조작에서는 경계 상자와 주변의 조작 어포던스를 통해 3D 개체를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-224">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="8466e-225">![이동](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-225">![Move](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="8466e-226">**이동**</span><span class="sxs-lookup"><span data-stu-id="8466e-226">**Move**</span></span><br>
       <span data-ttu-id="8466e-227">사용자의 손이 3D 개체에 가까워지는 즉시, 경계 상자와 가장 가까운 어포던스가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-227">As soon as a user's hand is close to a 3D object, the bounding box and the nearest affordance are revealed.</span></span> <span data-ttu-id="8466e-228">사용자가 경계 상자를 잡고 전체 개체를 옮길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-228">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-229">![회전](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-229">![Rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="8466e-230">**회전**</span><span class="sxs-lookup"><span data-stu-id="8466e-230">**Rotate**</span></span><br>
        <span data-ttu-id="8466e-231">사용자가 가장자리 어포던스를 잡아서 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-231">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-232">![배율](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-232">![Scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="8466e-233">**배율**</span><span class="sxs-lookup"><span data-stu-id="8466e-233">**Scale**</span></span><br>
       <span data-ttu-id="8466e-234">사용자가 모서리 어포던스를 잡아서 균일하게 크기를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-234">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="8466e-235">비어포던스 기반 조작</span><span class="sxs-lookup"><span data-stu-id="8466e-235">Non-affordance based manipulation</span></span>

<span data-ttu-id="8466e-236">비어포던스 기반 조작은 경계 상자에 어포던스를 연결하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-236">Non-affordance-based manipulation does not attach affordance to the bounding box.</span></span> <span data-ttu-id="8466e-237">사용자는 경계 상자만 표시한 후 직접 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-237">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="8466e-238">한 손으로 경계 상자를 잡을 경우 개체의 변환 및 회전은 손의 동작 및 방향과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-238">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="8466e-239">두 손으로 경계 상자를 잡을 경우 두 손의 상대적 동작에 따라 변환, 크기 조정 및 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-239">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="8466e-240">특정 조작에는 정밀도가 요구됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-240">Specific manipulation requires precision.</span></span> <span data-ttu-id="8466e-241">따라서 더 높은 세분성을 제공하는 **어포던스 기반 조작**을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-241">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="8466e-242">유연한 조작을 위해서는 즉각적이면서 유용한 환경을 지원하는 **비어포던스 조작**을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-242">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="8466e-243">직관적 제스처</span><span class="sxs-lookup"><span data-stu-id="8466e-243">Instinctual gestures</span></span>

<span data-ttu-id="8466e-244">HoloLens(1세대)에서는 미리 정의된 몇 가지 제스처(예: 블룸 및 에어 탭)를 사용자에게 학습시켰습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-244">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="8466e-245">HoloLens 2에서는 사용자에게 기호화된 제스처를 기억하도록 요구하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-245">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="8466e-246">사용자가 홀로그램 및 콘텐츠와 상호 작용하는 데 필요한 모든 제스처는 직관적입니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-246">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="8466e-247">직관적 제스처를 달성하는 방법은 사용자가 UI 어포던스의 디자인을 통해 제스처를 수행하도록 돕는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-247">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="8466e-248">예를 들어, 사용자가 두 손가락 모으기로 개체나 제어점을 잡도록 하려면 개체나 제어점이 작아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-248">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="8466e-249">사용자가 5개 손가락으로 잡기를 수행하도록 하려면 개체 또는 제어점이 비교적 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-249">If we want the user to perform five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="8466e-250">단추의 경우도 마찬가지로, 단추 크기가 작으면 사용자는 한 손가락으로 누르게 되지만, 단추 크기가 크면 손바닥으로 누르게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-250">Similar to buttons, a tiny button would limit users to press it with a single finger; a large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="8466e-251">![이동](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-251">![Move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="8466e-252">**소형 개체**</span><span class="sxs-lookup"><span data-stu-id="8466e-252">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-253">![회전](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-253">![Rotate](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="8466e-254">**중형 개체**</span><span class="sxs-lookup"><span data-stu-id="8466e-254">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="8466e-255">![배율](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="8466e-255">![Scale](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="8466e-256">**대형 개체**</span><span class="sxs-lookup"><span data-stu-id="8466e-256">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="8466e-257">손과 6 DoF 컨트롤러 간의 대칭 디자인</span><span class="sxs-lookup"><span data-stu-id="8466e-257">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="8466e-258">AR의 손과 VR의 모션 컨트롤러 간에는 상호 작용 평행 이론이 작용한다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-258">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="8466e-259">두 입력은 모두 해당 환경에서 직접 조작을 트리거하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-259">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="8466e-260">HoloLens 2의 근거리에서 손으로 잡아 끄는 동작은 WMR 모션 컨트롤러에 있는 잡기 단추로 작동하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-260">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="8466e-261">따라서 사용자는 두 플랫폼에서 유사하게 조작할 수 있기 때문에, 애플리케이션을 한 플랫폼에서 다른 플랫폼으로 이식하는 경우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-261">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application from one to the other.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="8466e-262">시선 추적으로 최적화</span><span class="sxs-lookup"><span data-stu-id="8466e-262">Optimize with eye tracking</span></span>

<span data-ttu-id="8466e-263">직접 조작은 의도한 대로 작동한다면 마법과 같이 느껴질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-263">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="8466e-264">하지만 손을 움직일 때마다 홀로그램이 의도와 다르게 트리거되면 당황할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-264">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="8466e-265">시선 추적은 사용자의 의도를 더 잘 식별하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-265">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="8466e-266">**사용할 때**: 조작 대응을 잘못 트리거하는 경우를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-266">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="8466e-267">시선 추적은 사용자가 현재 진행 중인 작업을 더 잘 이해할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-267">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="8466e-268">예를 들어, 실제 작업 공구를 잡기 위해 팔을 뻗으면서 홀로그래픽(지침) 텍스트를 읽는 경우를 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-268">For example, imagine you are reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="8466e-269">이렇게 하여 이전에 알아채지 못했던(예: 사용자의 FoV(시야각) 밖에 있을 수도 있음) 일부 대화형 홀로그래픽 단추 사이에서 실수로 손을 움직이게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-269">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before (e.g. it  may be outside the user's field-of-view (FoV)).</span></span>

  <span data-ttu-id="8466e-270">요약: 사용자가 한참 동안 홀로그램을 보지 않았는데도 터치 또는 잡기 이벤트가 감지된 경우, 사용자가 해당 홀로그램과 상호 작용하려는 의도가 실제로 없었을 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-270">Long story short: If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, it is likely that the user wasn't actually intending to interact with that hologram.</span></span>

* <span data-ttu-id="8466e-271">**선택한 대상**:  또 다른 예로 가양성 활성화를 처리하는 것 외에, 여러 개의 홀로그램이 서로 가깝게 배치된 경우 특히, 사용자 관점에서 정확한 교차점을 알 수 없으므로 잡거나 찌를 홀로그램을 더 잘 식별하는 경우를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-271">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="8466e-272">HoloLens 2의 시선 추적은 시선 응시를 정확하게 확인할 수 있는 정도에 따라 제한이 있지만, 손 입력으로 조작할 때는 깊이 차이가 있으므로 근거리 조작에 매우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-272">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be very helpful for near interactions due to depth disparity when interacting with hand input.</span></span> <span data-ttu-id="8466e-273">즉, 경우에 따라 조작 위젯을 정확히 잡기 위해 손을 홀로그램 뒤에 둘지 아니면 앞에 둘지를 결정하는 것이 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-273">This means that it is sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="8466e-274">**대상 위치**: 빨리 던지기 제스처에서 사용자가 바라보는 대상에 대한 정보를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-274">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="8466e-275">홀로그램을 잡은 후 의도한 대상 쪽으로 대충 던집니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-275">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="8466e-276">이러한 조작은 일반적으로 잘 작동하지만, 손 제스처를 빠르게 수행할 경우 대상이 부정확할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-276">While this sometimes works, quickly performing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="8466e-277">하지만 시선 추적은 제스처의 정확도를 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-277">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="8466e-278">Unity용 MRTK(Mixed Reality Toolkit)의 조작</span><span class="sxs-lookup"><span data-stu-id="8466e-278">Manipulation in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="8466e-279">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 를 사용하면 **ManipulationHandler** 스크립트를 사용하여 일반적인 조작 동작을 쉽게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-279">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ManipulationHandler**.</span></span> <span data-ttu-id="8466e-280">ManipulationHandler를 사용하면 직접 손이나 손 광선으로 직접 개체를 잡아 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-280">With ManipulationHandler, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="8466e-281">또한 개체의 크기 조정 및 회전을 위해 양손 조작도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8466e-281">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="8466e-282">MRTK - 조작</span><span class="sxs-lookup"><span data-stu-id="8466e-282">MRTK - Manipulation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)


---

## <a name="see-also"></a><span data-ttu-id="8466e-283">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8466e-283">See also</span></span>

* [<span data-ttu-id="8466e-284">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="8466e-284">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="8466e-285">수동으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="8466e-285">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="8466e-286">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="8466e-286">Instinctual interactions</span></span>](interaction-fundamentals.md)
