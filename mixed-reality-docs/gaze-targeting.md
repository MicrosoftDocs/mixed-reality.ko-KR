---
title: 대상으로 응시
description: 모든 상호 작용은 입력된 형식에 관계 없이 상호 작용 하려는 요소를 대상 하는 사용자의 기능을 기반으로 합니다.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 실제로, 게이즈 상호 작용을 대상으로 응시 mixed 디자인
ms.openlocfilehash: 1ac4f06208a7574fced0a7e27e93469ec93bf6e0
ms.sourcegitcommit: 90ce9415889e7121dd2fd76a893dc3734672881b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64873921"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="c1ea3-104">응시 및 유지</span><span class="sxs-lookup"><span data-stu-id="c1ea3-104">Gaze and dwell</span></span>
<span data-ttu-id="c1ea3-105">확인 하는 다양 한 방법의 많은 _커밋_ 사용 하 여 게이즈를 조합 하는 등 _음성_ 또는 _제스처를 전달_합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-105">There are lots of different ways to confirm a _commit_ such as combining gaze with _voice_ or _hand gestures_.</span></span>
<span data-ttu-id="c1ea3-106">일부의 사용자 시나리오가 있습니다 하지만 사용자에 게 사용 중인 숫자일 수 또는 추적할 수 없습니다 (예: 너무 큰된 대량의 gloves 사용 하 여 팩터리 근로자).</span><span class="sxs-lookup"><span data-stu-id="c1ea3-106">There are several user scenarios though, in which users' hands may either be busy or cannot be tracked (e.g., factory workers with oversized heavy duty gloves).</span></span> <span data-ttu-id="c1ea3-107">음성 입력 하지 사용자 기본 설정, 소셜 컨텍스트 또는 클라우드 환경으로 인해 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-107">Voice input may also not be available due to user preferences, social context or loud environments.</span></span>
<span data-ttu-id="c1ea3-108">대체 (fallback) 솔루션으로 다른 옵션을 수행을 _커밋_ 으로 참조 하는 UI 요소에 적절히 유지 하는 것 _타이_합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-108">As a fallback solution another option to perform a _commit_ is simply to keep staring at a UI element which we refer to as _dwell_.</span></span>
<span data-ttu-id="c1ea3-109">A _타이_ head 또는 눈 게이즈를 사용 하 여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-109">A _dwell_ can be performed with either head or eye gaze.</span></span> <span data-ttu-id="c1ea3-110">개념은 간단 하며 다음과 같은 단계로 세분화 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-110">The idea is simple and can be broken down in the following phases:</span></span> 
1. <span data-ttu-id="c1ea3-111">사용자가 gazing holographic 단추에서 시작</span><span class="sxs-lookup"><span data-stu-id="c1ea3-111">User starts gazing at a holographic button</span></span>

2. <span data-ttu-id="c1ea3-112">간략 한 발병 지연 (예: 150 밀리초) 후에 몇 가지 시각적 피드백 애니메이션 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-112">After a brief onset delay (e.g., 150 ms) some visual feedback animation is started.</span></span> <span data-ttu-id="c1ea3-113">발병 지연 즉시 표시 하 여 피드백 항상 사용자 과부하를 피하기 위해 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-113">The onset delay is used to avoid overwhelming the user by immediately popping up feedback all the time.</span></span>
    - <span data-ttu-id="c1ea3-114">에 대 한 _응시_, 시각적 개체의 디자인에 대해 다음 피드백을 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-114">For _eye gaze_, we recommend the following for the design of the visual dwell feedback:</span></span>
      - <span data-ttu-id="c1ea3-115">**이 blend**: 완전 불투명 처음에 약간만 표시에서 사용자 의견에 혼합 원활 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-115">**Blend it**: Smoothly blend in the feedback from barely visible at first to fully opaque.</span></span> <span data-ttu-id="c1ea3-116">이 피드백을 사용 하면 덜 방해 고 overwhleming과 원활 하 게 하려면이 단추를 사용 하 여 참여 하려는 사용자는 시스템에는 신뢰도 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-116">This makes the feedback less distracting and overwhleming and nicely aligns with the confidence that the system has that the user really wants to engage with this button.</span></span>
      - <span data-ttu-id="c1ea3-117">**끌어오기**: 크기가 감소 하 고 사용자의 visual 이목을 끌어오는 대상의 중심 쪽으로 이동 하는 보다 시각적 피드백을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-117">**Pull it in**: Create a visual feedback than decreases in size and moves towards the center of the target, pulling in the user's visual attention.</span></span> 

3. <span data-ttu-id="c1ea3-118">미리 정의 된 지속 기간 (예: 800 밀리초) 후 완료 되는 유지 하 고 연결된 된 이벤트가 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-118">After a pre-defined dwell duration (e.g., 800 ms), the dwell completes and an associated event is triggered.</span></span>
    - <span data-ttu-id="c1ea3-119">청각 종료 일부 제공 또는 시각적 피드백을 실제로 홈 하는 항목이 이제 선택 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-119">Provide some finalizing auditory or visual feedback to really bring home that the item got selected now.</span></span>

![상태를 유지 합니다.](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a><span data-ttu-id="c1ea3-121">대상으로 응시</span><span class="sxs-lookup"><span data-stu-id="c1ea3-121">Gaze targeting</span></span>

<span data-ttu-id="c1ea3-122">모든 상호 작용은 입력된 형식에 관계 없이 상호 작용 하려는 요소를 대상 하는 사용자의 기능을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-122">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="c1ea3-123">Windows Mixed Reality에서 일반적으로 이렇게 사용자 게이즈를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-123">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="c1ea3-124">사용자는 환경에서 성공적으로 작업할 수 있도록 사용자의 의도 한 사용자의 실제 의도 시스템의 계산된 이해 최대한 가깝게 정렬 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-124">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="c1ea3-125">수준에 해당 하는 시스템에서 사용자의 의도 한 동작을 해석 하는 올바르게 만족도 증가 하 고 성능 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-125">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="c1ea3-126">장치 지원</span><span class="sxs-lookup"><span data-stu-id="c1ea3-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c1ea3-127">기능</span><span class="sxs-lookup"><span data-stu-id="c1ea3-127">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="c1ea3-128"><a href="hololens-hardware-details.md">HoloLens (첫 번째 범용)</a></span><span class="sxs-lookup"><span data-stu-id="c1ea3-128"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="c1ea3-129">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c1ea3-129">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="c1ea3-130"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="c1ea3-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c1ea3-131">대상으로 응시</span><span class="sxs-lookup"><span data-stu-id="c1ea3-131">Gaze targeting</span></span></td><td style="text-align: center;"> <span data-ttu-id="c1ea3-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c1ea3-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c1ea3-133">✔️</span><span class="sxs-lookup"><span data-stu-id="c1ea3-133">✔️</span></span></td><td style="text-align: center;"><span data-ttu-id="c1ea3-134">✔️</span><span class="sxs-lookup"><span data-stu-id="c1ea3-134">✔️</span></span> </td>
</tr><tr>
<td> <span data-ttu-id="c1ea3-135">모니터링 대상</span><span class="sxs-lookup"><span data-stu-id="c1ea3-135">Eye targeting</span></span></td><td style="text-align: center;"></td><td style="text-align: center;"> <span data-ttu-id="c1ea3-136">✔️</span><span class="sxs-lookup"><span data-stu-id="c1ea3-136">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="c1ea3-137">HoloLens 2 관련 된 자세한 지침 [예정](index.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-137">More guidance specific to HoloLens 2 [coming soon](index.md).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="c1ea3-138">대상 크기 조정 및 피드백</span><span class="sxs-lookup"><span data-stu-id="c1ea3-138">Target sizing and feedback</span></span>

<span data-ttu-id="c1ea3-139">응시 벡터 세밀 하 게 대상에 대 한 사용 가능 하도록 반복적으로 표시 된 있지만 gross 타기 팅 (획득 크며 대상)에 대 한 가장 잘 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-139">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="c1ea3-140">1 ~ 1.5도 최소 대상 크기 3도의 대상을 더 크거나 속도가 종종 허용 하지만 대부분의 시나리오에서 사용자 작업을 허용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-140">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="c1ea3-141">참고는 3D 요소에 대 한도 2D 영역이 효과적으로 사용자 대상 크기 어떤 프로젝션은 연결 하는 대상 지정이 가능 영역 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-141">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="c1ea3-142">요소는 "활성" (사용자가 대상으로 하는지 것)는 몇 가지 두드러진 큐는 매우 유용한-포함 될 수 있습니다이 제공 처리가 표시 "가리키기" 효과, 오디오 강조 표시 하거나 클릭 또는 요소를 사용 하 여 커서의 맞춤을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-142">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="c1ea3-143">![2 개의 미터 거리에 최적의 대상 크기](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c1ea3-143">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="c1ea3-144">*2 개의 미터 거리에 최적의 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="c1ea3-144">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="c1ea3-145">![응시 대상된 개체를 강조 표시의 예](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c1ea3-145">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="c1ea3-146">*응시 대상된 개체를 강조 표시의 예*</span><span class="sxs-lookup"><span data-stu-id="c1ea3-146">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="c1ea3-147">대상 배치</span><span class="sxs-lookup"><span data-stu-id="c1ea3-147">Target placement</span></span>

<span data-ttu-id="c1ea3-148">사용자가 해당 필드의 뷰에서 매우 높음 또는 매우 낮은 배치 되는 UI 요소를 찾을 수 없습니다 종종 대부분의 영역 (일반적으로 약 눈 수준) 주요 초점 주위에 주의가 집중 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-148">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="c1ea3-149">일부 적절 한 밴드 눈 모양 수준에서 대부분의 대상과 배치 하면 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-149">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="c1ea3-150">경향이 많기 사용자에 대 한 지정 된 상대적으로 적은 visual 영역에 언제 든 지 (비전 attentional 원뿔 약 10도), 그룹화 UI 요소 수준 개념적으로 관련는 초점을 활용할 수 있습니다에서 주의 연결 동작 사용자로 항목을 영역을 통해 해당 게이즈를 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-150">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="c1ea3-151">UI를 디자인할 때 염두 HoloLens 및 몰입 형 헤드셋 간에 뷰 필드의에서 잠재적인 대규모 변형 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-151">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="c1ea3-152">![그룹화 된 UI 요소에 대해 쉽게 게이즈 Galaxy 탐색기에서 대상으로 하는 예제](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c1ea3-152">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="c1ea3-153">*그룹화 된 UI 요소에 대해 쉽게 게이즈 Galaxy 탐색기에서 대상으로 하는 예제*</span><span class="sxs-lookup"><span data-stu-id="c1ea3-153">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="c1ea3-154">대상 동작 개선</span><span class="sxs-lookup"><span data-stu-id="c1ea3-154">Improving targeting behaviors</span></span>

<span data-ttu-id="c1ea3-155">대상 작업으로 사용자의 의도 또는 수 있으면 결정 (밀접 하 게 근사화), "near miss" 올바르게 대상 지정 된 것 처럼 상호 작용에서 시도 허용 하도록 하는 데 매우 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-155">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="c1ea3-156">혼합된 현실 환경에 통합할 수 있는 성공적인 방법 중 몇 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-156">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="c1ea3-157">응시 안정화 ("중력 웰")</span><span class="sxs-lookup"><span data-stu-id="c1ea3-157">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="c1ea3-158">이 켤 것인지 대부분 또는 모든 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-158">This should be turned on most/all of the time.</span></span> <span data-ttu-id="c1ea3-159">이 기술은 사용자가 있을 수 있는 자연 스러운 head/목 jitter를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-159">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="c1ea3-160">또한 이동 사용 하 여 확인 하 고 말하기 동작으로 인해입니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-160">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="c1ea3-161">가장 가까운 링크 알고리즘</span><span class="sxs-lookup"><span data-stu-id="c1ea3-161">Closest link algorithms</span></span>

<span data-ttu-id="c1ea3-162">이러한 스파스 대화형 콘텐츠를 사용 하 여 영역에서 가장 잘 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-162">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="c1ea3-163">사용 하 여 상호 작용을 시도 하는 사용자가 결정할 수 있도록 가능성이 높은 경우 단순히 일정 수준의 의도 가정 하 여 해당 타기 팅 기능을 보완할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-163">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="c1ea3-164">Backdating postdating 작업</span><span class="sxs-lookup"><span data-stu-id="c1ea3-164">Backdating/postdating actions</span></span>

<span data-ttu-id="c1ea3-165">이 메커니즘은 속도 요구 하는 작업에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-165">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="c1ea3-166">사용자가 일련의 속도로 활성화 대상으로 사용 하는 전략을 통해 이동 인 경우 몇 가지 의도 가정 하 고 유용할 수 있습니다 *단계를 누락* 대상 있던 사용자 포커스가 약간 전후 약간 tap (작업을 적용할 50ms 앞/뒤은 유효 초기 테스트에서).</span><span class="sxs-lookup"><span data-stu-id="c1ea3-166">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="c1ea3-167">다듬기</span><span class="sxs-lookup"><span data-stu-id="c1ea3-167">Smoothing</span></span>

<span data-ttu-id="c1ea3-168">이 메커니즘은 경로 지정 이동을 줄이는 약간의 지터/비틀 거리 면 서 자연 스러운 헤드 이동 특성 때문에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-168">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="c1ea3-169">경로 동작을 통해 다듬기, 하는 경우 이동이 아닌 시간에 따른 크기/간격 만큼 부드러운</span><span class="sxs-lookup"><span data-stu-id="c1ea3-169">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="c1ea3-170">자기</span><span class="sxs-lookup"><span data-stu-id="c1ea3-170">Magnetism</span></span>

<span data-ttu-id="c1ea3-171">이 메커니즘 "link 가장 가까운" 알고리즘-대상 방향으로 커서를 도출 하거나 (할지 여부) 여부 hitboxes 단순히 증가의 보다 일반적인 버전으로 간주할 수 가능성이 대상으로 하는 방법을 사용자에 대화형 레이아웃에 대 한 지식을 사용 더 나은 방법은 사용자의 의도.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-171">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="c1ea3-172">특히 작은 대상에 대 한 강력한 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-172">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="c1ea3-173">포커스 연결 유지</span><span class="sxs-lookup"><span data-stu-id="c1ea3-173">Focus stickiness</span></span>

<span data-ttu-id="c1ea3-174">근처의 대화형 요소에 포커스를 결정 하는 경우에 바이어스는 현재 포커스가 있는 요소를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-174">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="c1ea3-175">이 자연 스러운 노이즈를 사용 하 여 두 요소 사이의 중간점에서 부동 때 동작을 전환 하는 불규칙 포커스를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-175">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1ea3-176">참조</span><span class="sxs-lookup"><span data-stu-id="c1ea3-176">See also</span></span>
* [<span data-ttu-id="c1ea3-177">제스처</span><span class="sxs-lookup"><span data-stu-id="c1ea3-177">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="c1ea3-178">음성 디자인</span><span class="sxs-lookup"><span data-stu-id="c1ea3-178">Voice design</span></span>](voice-design.md)
* [<span data-ttu-id="c1ea3-179">커서</span><span class="sxs-lookup"><span data-stu-id="c1ea3-179">Cursors</span></span>](cursors.md)
