---
title: 헤드 게이즈(head-gaze) 및 커밋
description: 헤드 게이즈(head-gaze) 및 커밋 입력 모델 개요
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: 혼합 현실, 응시, 응시 타기팅, 상호 작용, 디자인
ms.openlocfilehash: 5fef778dde6852222e098aeb1cbb41fe04e0b744
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441098"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="4feb2-104">헤드 게이즈(head-gaze) 및 커밋</span><span class="sxs-lookup"><span data-stu-id="4feb2-104">Head-gaze and commit</span></span>
<span data-ttu-id="4feb2-105">_헤드-응시 및 커밋은_ 전방의 방향 (head 방향)으로 개체를 대상으로 지정 하 고, 손 모양 제스처와 같은 보조 입력으로 작업을 수행 하는 [응시 및 커밋](gaze-and-commit.md) 입력 모델의 특별 한 경우입니다. 또는 음성 명령 "선택"을 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with the direction of your head pointing forward (head-direction), and then acting on it with a secondary input, such as the hand gesture air tap or the voice command "Select".</span></span> 

## <a name="device-support"></a><span data-ttu-id="4feb2-106">장치 지원</span><span class="sxs-lookup"><span data-stu-id="4feb2-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4feb2-107"><strong>입력 모델</strong></span><span class="sxs-lookup"><span data-stu-id="4feb2-107"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="4feb2-108"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="4feb2-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="4feb2-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="4feb2-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="4feb2-110"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="4feb2-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4feb2-111">헤드 게이즈(head-gaze) 및 커밋</span><span class="sxs-lookup"><span data-stu-id="4feb2-111">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="4feb2-112">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="4feb2-112">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="4feb2-113">✔️ 권장(세 번째 선택 - <a href="interaction-fundamentals.md">다른 옵션 보기</a>)</span><span class="sxs-lookup"><span data-stu-id="4feb2-113">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="4feb2-114">➕ 대체 옵션</span><span class="sxs-lookup"><span data-stu-id="4feb2-114">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="4feb2-115">대상 크기 조정 및 피드백</span><span class="sxs-lookup"><span data-stu-id="4feb2-115">Target sizing and feedback</span></span>
<span data-ttu-id="4feb2-116">헤드 응시 벡터는 세밀 하 게 대상 지정에 사용할 수 있도록 반복적으로 표시 되었지만, 일반적으로 더 큰 대상을 확보 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-116">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring somewhat larger targets.</span></span> <span data-ttu-id="4feb2-117">최소 대상 크기인 1 ~ 1.5도를 사용 하면 대부분의 시나리오에서 성공적인 사용자 작업을 수행할 수 있지만, 3도의 대상은 속도가 더 빨라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-117">Minimum target sizes of 1 to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="4feb2-118">사용자가 타기팅하는 크기는 3D 요소인 경우에도 사실상 2D 영역입니다. 즉, 어떤 투영을 사용하든 타기킹이 가능한 영역이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-118">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="4feb2-119">요소가 "활성" (사용자가 대상으로 하는) 인 두드러진 몇 가지 큐를 제공 하는 것은 매우 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-119">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful.</span></span> <span data-ttu-id="4feb2-120">여기에는 표시 되는 "가리키기" 효과, 오디오 하이라이트 또는 클릭 또는 요소와 커서의 처리가 같은 내용이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-120">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="4feb2-121">![2m 거리에서 최적 대상 크기](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4feb2-121">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="4feb2-122">*2m 거리에서 최적 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="4feb2-122">*Optimal target size at 2 meter distance*</span></span>

<br>

<span data-ttu-id="4feb2-123">![응시 대상 개체를 강조 표시한 예](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4feb2-123">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="4feb2-124">*응시 대상 개체를 강조 표시한 예*</span><span class="sxs-lookup"><span data-stu-id="4feb2-124">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="4feb2-125">대상 배치</span><span class="sxs-lookup"><span data-stu-id="4feb2-125">Target placement</span></span>
<span data-ttu-id="4feb2-126">사용자는 종종 보기의 해당 필드에서 매우 높은 또는 매우 낮은 UI 요소를 찾을 수 없기 때문에 주 포커스 주위의 영역에서 대부분의 주의를 기울일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-126">Users often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="4feb2-127">대부분의 대상을 눈 높이 주변의 적당한 구간에 두면 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-127">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="4feb2-128">사용자는 상대적으로 작은 시각 영역에 집중한다는 일반적인 경향을 감안하여(시력이 집중되는 원뿔 영역은 10도 정도임), UI 요소를 개념적으로 관련된 정도만큼 그룹화하면 사용자가 영역에서 응시 시선을 옮길 때 항목 간의 관심 연결 동작을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-128">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="4feb2-129">UI를 디자인할 때는 HoloLens와 몰입형 헤드셋의 시야가 크게 달라질 수 있다는 점을 감안해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-129">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="4feb2-130">![Galaxy Explorer에서 응시 타기팅하기 편리하게 그룹화된 UI 요소의 예](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4feb2-130">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="4feb2-131">*Galaxy Explorer에서 응시 타기팅하기 편리하게 그룹화된 UI 요소의 예*</span><span class="sxs-lookup"><span data-stu-id="4feb2-131">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="4feb2-132">타기팅 동작 개선</span><span class="sxs-lookup"><span data-stu-id="4feb2-132">Improving targeting behaviors</span></span>
<span data-ttu-id="4feb2-133">특정 항목을 대상으로 지정 하는 사용자 의도를 결정 (또는 매우 근접 하 게) 할 수 있는 경우 올바르게 대상으로 지정 된 것 처럼 상호 작용 시 거의 누락 된 시도를 허용 하는 것이 유용할 수 있습니다</span><span class="sxs-lookup"><span data-stu-id="4feb2-133">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept near miss attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="4feb2-134">다음은 혼합 현실 환경에서 통합할 수 있는 성공적인 몇 가지 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-134">Here are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="4feb2-135">헤드 게이즈(head-gaze) 안정화("중력 우물")</span><span class="sxs-lookup"><span data-stu-id="4feb2-135">Head-gaze stabilization ("gravity wells")</span></span>
<span data-ttu-id="4feb2-136">이는 대부분의 시간 동안 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-136">This should be turned on most or all of the time.</span></span> <span data-ttu-id="4feb2-137">이 기술은 사용자가 사용할 수 있는 자연 스런 head 및 목 jitter을 보고 동작으로 인해 이동 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-137">This technique removes the natural head and neck jitters that users might have as well movement due to looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="4feb2-138">가장 가까운 링크 알고리즘</span><span class="sxs-lookup"><span data-stu-id="4feb2-138">Closest link algorithms</span></span>
<span data-ttu-id="4feb2-139">이 기법은 상호 작용이 희소한 영역에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-139">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="4feb2-140">사용자가 상호 작용 하려고 했던 항목을 결정할 수 있을 확률이 높은 경우 특정 수준의 의도를 가정 하 여 대상 기능을 보완할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-140">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="4feb2-141">배경 및 postdating 작업</span><span class="sxs-lookup"><span data-stu-id="4feb2-141">Backdating and postdating actions</span></span>
<span data-ttu-id="4feb2-142">이 메커니즘은 속도가 필요한 작업에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-142">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="4feb2-143">사용자가 고속 대상 지정 및 활성화 연습을 통해 이동 하는 경우에는 몇 가지 의도를 가정 하 고, 사용자가 탭 하기 전후에 약간의 초점을 두고 (50 ms 이전/이후 rly 테스트).</span><span class="sxs-lookup"><span data-stu-id="4feb2-143">When a user is moving through a series of targeting and activation maneuvers at speed, it is useful to assume some intent, and allow missed steps to act upon targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="4feb2-144">다듬기</span><span class="sxs-lookup"><span data-stu-id="4feb2-144">Smoothing</span></span>
<span data-ttu-id="4feb2-145">이 메커니즘은 자연 스러운 헤드 이동 특성으로 인해 약간의 지터와 wobble 감소 하는 pathing 이동에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-145">This mechanism is useful for pathing movements, reducing the slight jitter and wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="4feb2-146">Pathing 동작을 매끄럽게 하는 경우 시간이 지남에 따라 부드러운 이동의 크기와 거리를 매끄럽게 합니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-146">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="4feb2-147">자성</span><span class="sxs-lookup"><span data-stu-id="4feb2-147">Magnetism</span></span>
<span data-ttu-id="4feb2-148">이 메커니즘은 가장 가까운 링크 알고리즘의 보다 일반적인 버전으로 간주할 수 있습니다. 즉, 사용자가 대화형 레이아웃에 대 한 몇 가지 정보를 사용 하 여 대상에 대 한 정보를 사용 하는 것이 가능 하기 때문에 사용자의 접근 방식이 hitboxes 수 있습니다. 사용자 의도에 접근 합니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-148">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="4feb2-149">특히 작은 대상에 강력한 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-149">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="4feb2-150">포커스 고착</span><span class="sxs-lookup"><span data-stu-id="4feb2-150">Focus stickiness</span></span>
<span data-ttu-id="4feb2-151">포커스를 제공할 근처 대화형 요소를 결정 하는 경우 포커스 유지는 현재 포커스가 있는 요소에 대 한 바이어스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-151">When determining which nearby interactive elements to give focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="4feb2-152">이렇게 하면 자연 노이즈가 있는 두 요소 간의 중간점에서 부동 상태에 있는 경우 비정상적인 포커스 전환 동작을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4feb2-152">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>


## <a name="see-also"></a><span data-ttu-id="4feb2-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4feb2-153">See also</span></span>
* [<span data-ttu-id="4feb2-154">눈에 잘 맞는 상호 작용</span><span class="sxs-lookup"><span data-stu-id="4feb2-154">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="4feb2-155">응시 및 유지</span><span class="sxs-lookup"><span data-stu-id="4feb2-155">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="4feb2-156">직접 조작</span><span class="sxs-lookup"><span data-stu-id="4feb2-156">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4feb2-157">손 제스처</span><span class="sxs-lookup"><span data-stu-id="4feb2-157">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="4feb2-158">손 지점 및 커밋</span><span class="sxs-lookup"><span data-stu-id="4feb2-158">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="4feb2-159">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="4feb2-159">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="4feb2-160">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="4feb2-160">Voice input</span></span>](voice-input.md)



