---
title: 응시 대상 지정
description: 모든 상호 작용은 입력 형식에 관계없이 상호 작용하려는 요소를 타기팅하는 사용자의 역량에 기반합니다.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: 혼합 현실, 응시, 응시 대상 지정, 상호 작용, 디자인
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829842"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="a5f6b-104">응시 및 지속</span><span class="sxs-lookup"><span data-stu-id="a5f6b-104">Gaze and dwell</span></span>
<span data-ttu-id="a5f6b-105">응시를 _음성_ 또는 _핸드 제스처_와 결합 하는 것과 같이 _커밋을_ 확인 하는 다양 한 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-105">There are lots of different ways to confirm a _commit_ such as combining gaze with _voice_ or _hand gestures_.</span></span>
<span data-ttu-id="a5f6b-106">그러나 사용자의 손을 사용 중이거나 추적할 수 없는 경우 (예: 과도 한 고급 글러브를 사용 하는 팩터리 작업자)에는 여러 가지 사용자 시나리오가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-106">There are several user scenarios though, in which users' hands may either be busy or cannot be tracked (e.g., factory workers with oversized heavy duty gloves).</span></span> <span data-ttu-id="a5f6b-107">사용자 기본 설정, 소셜 컨텍스트 또는 큰 환경으로 인해 음성 입력을 사용 하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-107">Voice input may also not be available due to user preferences, social context or loud environments.</span></span>
<span data-ttu-id="a5f6b-108">대체 솔루션인 _커밋을_ 수행 하는 또 다른 옵션은 단순히 유지로 참조 하는 UI 요소에 바랄을 유지 하는 것 _입니다._</span><span class="sxs-lookup"><span data-stu-id="a5f6b-108">As a fallback solution another option to perform a _commit_ is simply to keep staring at a UI element which we refer to as _dwell_.</span></span>
<span data-ttu-id="a5f6b-109">헤드 또는 눈동자 응시를 사용 하 여 _지속_ 을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-109">A _dwell_ can be performed with either head or eye gaze.</span></span> <span data-ttu-id="a5f6b-110">아이디어는 간단 하며 다음 단계로 나눌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-110">The idea is simple and can be broken down in the following phases:</span></span> 
1. <span data-ttu-id="a5f6b-111">사용자가 holographic 단추에서 gazing 시작</span><span class="sxs-lookup"><span data-stu-id="a5f6b-111">User starts gazing at a holographic button</span></span>

2. <span data-ttu-id="a5f6b-112">짧은 하기 시작 하면 지연 (예: 150 밀리초) 후에 일부 시각적 피드백 애니메이션이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-112">After a brief onset delay (e.g., 150 ms) some visual feedback animation is started.</span></span> <span data-ttu-id="a5f6b-113">하기 시작 하면 지연은 항상 피드백을 즉시 팝 하 여 사용자의 부담을 방지 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-113">The onset delay is used to avoid overwhelming the user by immediately popping up feedback all the time.</span></span>
    - <span data-ttu-id="a5f6b-114">_아이 응시_의 경우 시각적 유지 피드백의 디자인에 다음을 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-114">For _eye gaze_, we recommend the following for the design of the visual dwell feedback:</span></span>
      - <span data-ttu-id="a5f6b-115">**Blend it**: 처음에는 완전히 불투명 하 게 표시 되는 피드백을 원활 하 게 혼합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-115">**Blend it**: Smoothly blend in the feedback from barely visible at first to fully opaque.</span></span> <span data-ttu-id="a5f6b-116">이렇게 하면 피드백이 혼란을 overwhleming 하 고 사용자가이 단추를 사용 하는 것이 사용자의 확신에 맞게 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-116">This makes the feedback less distracting and overwhleming and nicely aligns with the confidence that the system has that the user really wants to engage with this button.</span></span>
      - <span data-ttu-id="a5f6b-117">다음 **에서 가져오기**: 크기를 줄이고 대상의 중심을 향해 이동 하 여 사용자의 시각적 주의를 당겨 시각적 피드백을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-117">**Pull it in**: Create a visual feedback than decreases in size and moves towards the center of the target, pulling in the user's visual attention.</span></span> 

3. <span data-ttu-id="a5f6b-118">미리 정의 된 유지 기간 (예: 800 밀리초) 후에는 지속이 완료 되 고 연결 된 이벤트가 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-118">After a pre-defined dwell duration (e.g., 800 ms), the dwell completes and an associated event is triggered.</span></span>
    - <span data-ttu-id="a5f6b-119">현재 항목이 선택 된 것으로 홈을 가져올 수 있는 몇 가지 청각 또는 시각적 피드백을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-119">Provide some finalizing auditory or visual feedback to really bring home that the item got selected now.</span></span>

![지속 상태](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a><span data-ttu-id="a5f6b-121">응시 대상 지정</span><span class="sxs-lookup"><span data-stu-id="a5f6b-121">Gaze targeting</span></span>

<span data-ttu-id="a5f6b-122">모든 상호 작용은 입력 형식에 관계없이 상호 작용하려는 요소를 타기팅하는 사용자의 역량에 기반합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-122">All interactions are built upon the ability of a user to target the element they want to interact with, regardless of the input modality.</span></span> <span data-ttu-id="a5f6b-123">Windows Mixed Reality에서는 일반적으로 사용자의 응시를 사용하여 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-123">In Windows Mixed Reality, this is generally done using the user's gaze.</span></span>

<span data-ttu-id="a5f6b-124">사용자가 환경을 성공적으로 사용하도록 하려면, 시스템에서 계산된 사용자의 의도에 대한 이해와 사용자의 실제 의도가 최대한 가깝게 맞춰져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-124">To enable a user to work with an experience successfully, the system's calculated understanding of a user's intent, and the user's actual intent, must align as closely as possible.</span></span> <span data-ttu-id="a5f6b-125">사용자가 의도한 동작을 시스템이 제대로 해석하는 정도만큼, 만족도는 높아지고 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-125">To the degree that the system interprets the user's intended actions correctly, satisfaction increases and performance improves.</span></span>

## <a name="device-support"></a><span data-ttu-id="a5f6b-126">장치 지원</span><span class="sxs-lookup"><span data-stu-id="a5f6b-126">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a5f6b-127"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="a5f6b-127"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a5f6b-128"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="a5f6b-128"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="a5f6b-129"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="a5f6b-129"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="a5f6b-130"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="a5f6b-130"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a5f6b-131">응시 대상 지정</span><span class="sxs-lookup"><span data-stu-id="a5f6b-131">Gaze targeting</span></span></td>
        <td><span data-ttu-id="a5f6b-132">✔️</span><span class="sxs-lookup"><span data-stu-id="a5f6b-132">✔️</span></span></td>
        <td><span data-ttu-id="a5f6b-133">✔️</span><span class="sxs-lookup"><span data-stu-id="a5f6b-133">✔️</span></span></td>
        <td><span data-ttu-id="a5f6b-134">✔️</span><span class="sxs-lookup"><span data-stu-id="a5f6b-134">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a5f6b-135">눈동자 대상</span><span class="sxs-lookup"><span data-stu-id="a5f6b-135">Eye targeting</span></span></td>
        <td><span data-ttu-id="a5f6b-136">❌</span><span class="sxs-lookup"><span data-stu-id="a5f6b-136">❌</span></span></td>
        <td><span data-ttu-id="a5f6b-137">✔️</span><span class="sxs-lookup"><span data-stu-id="a5f6b-137">✔️</span></span></td>
        <td><span data-ttu-id="a5f6b-138">❌</span><span class="sxs-lookup"><span data-stu-id="a5f6b-138">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="a5f6b-139">HoloLens 2에 대 한 추가 지침은 [곧](index.md)제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-139">More guidance specific to HoloLens 2 [coming soon](index.md).</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="a5f6b-140">대상 크기 조정 및 피드백</span><span class="sxs-lookup"><span data-stu-id="a5f6b-140">Target sizing and feedback</span></span>

<span data-ttu-id="a5f6b-141">응시 벡터는 미세 타기팅에 사용할 수 있도록 반복적으로 표시되지만 전체 타기팅(다소 큰 대상 확보)에 가장 적합한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-141">The gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting (acquiring somewhat larger targets).</span></span> <span data-ttu-id="a5f6b-142">최소 대상 크기가 1~1.5도이면 대부분의 시나리오에서 사용자의 동작이 성공해야 하지만 크기가 3도인 대상이 속도가 더 빠른 경우가 가끔 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-142">Minimum target sizes of 1 to 1.5 degrees should allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="a5f6b-143">사용자가 타기팅하는 크기는 3D 요소인 경우에도 사실상 2D 영역입니다. 즉, 어떤 투영을 사용하든 타기킹이 가능한 영역이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-143">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="a5f6b-144">요소가 "활성"(사용자가 요소를 타기팅하고 있음)이라는 핵심적인 단서를 제공하면 매우 유용합니다. 이러한 단서에는 눈에 보이는 "호버(hover)" 효과, 오디오 하이라이트나 클릭과 같은 처리 또는 요소와 커서의 명확한 맞춤이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-144">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful - this can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="a5f6b-145">![2m 거리에서 최적 대상 크기](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a5f6b-145">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="a5f6b-146">*2m 거리에서 최적 대상 크기*</span><span class="sxs-lookup"><span data-stu-id="a5f6b-146">*Optimal target size at 2 meter distance*</span></span>

<span data-ttu-id="a5f6b-147">![응시 대상 개체를 강조 표시한 예](images/gazetargeting-highlighting-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a5f6b-147">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-640px.jpg)</span></span><br>
<span data-ttu-id="a5f6b-148">*응시 대상 개체를 강조 표시한 예*</span><span class="sxs-lookup"><span data-stu-id="a5f6b-148">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="a5f6b-149">대상 배치</span><span class="sxs-lookup"><span data-stu-id="a5f6b-149">Target placement</span></span>

<span data-ttu-id="a5f6b-150">사용자는 주요 초점(보통 대략 눈 높이) 주변 영역에 대부분의 관심을 집중하기 때문에 시야에서 매우 높거나 낮게 배치된 UI 요소를 사용자가 찾지 못하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-150">Users will often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus (usually roughly eye level).</span></span> <span data-ttu-id="a5f6b-151">대부분의 대상을 눈 높이 주변의 적당한 구간에 두면 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-151">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="a5f6b-152">사용자는 상대적으로 작은 시각 영역에 집중한다는 일반적인 경향을 감안하여(시력이 집중되는 원뿔 영역은 10도 정도임), UI 요소를 개념적으로 관련된 정도만큼 그룹화하면 사용자가 영역에서 응시 시선을 옮길 때 항목 간의 관심 연결 동작을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-152">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="a5f6b-153">UI를 디자인할 때는 HoloLens와 몰입형 헤드셋의 시야가 크게 달라질 수 있다는 점을 감안해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-153">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="a5f6b-154">![Galaxy Explorer에서 응시 타기팅하기 편리하게 그룹화된 UI 요소의 예](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a5f6b-154">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="a5f6b-155">*Galaxy Explorer에서 응시 타기팅하기 편리하게 그룹화된 UI 요소의 예*</span><span class="sxs-lookup"><span data-stu-id="a5f6b-155">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="a5f6b-156">타기팅 동작 개선</span><span class="sxs-lookup"><span data-stu-id="a5f6b-156">Improving targeting behaviors</span></span>

<span data-ttu-id="a5f6b-157">대상을 타기팅하려는 사용자의 의도를 파악(또는 근사치에 가깝게 처리)할 수 있다면 상호 작용 시 "아깝게 놓친"시도를 마치 정확하게 타기팅한 것처럼 수락하는 데 큰 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-157">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept "near miss" attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="a5f6b-158">혼합 현실 환경에 통합할 수 있는 유용한 메서드는 매우 다양합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-158">There are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="gaze-stabilization-gravity-wells"></a><span data-ttu-id="a5f6b-159">응시 ("중력 웰")</span><span class="sxs-lookup"><span data-stu-id="a5f6b-159">Gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="a5f6b-160">이 기능은 거의 항상 켜져 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-160">This should be turned on most/all of the time.</span></span> <span data-ttu-id="a5f6b-161">이 기법은 사용자에게 있을 수 있는 자연스러운 머리/목 떨림을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-161">This technique removes the natural head/neck jitters that users may have.</span></span> <span data-ttu-id="a5f6b-162">보기/말하기 동작 때문에 발생하는 움직임도 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-162">Also movement due to looking/speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="a5f6b-163">가장 가까운 링크 알고리즘</span><span class="sxs-lookup"><span data-stu-id="a5f6b-163">Closest link algorithms</span></span>

<span data-ttu-id="a5f6b-164">이 기법은 상호 작용이 희소한 영역에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-164">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="a5f6b-165">사용자가 어떤 상호 작용을 시도하는지 파악할 수 있는 가능성이 높으면, 일정 수준의 의도를 가정하여 타기팅 역량을 보완할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-165">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by simply assuming some level of intent.</span></span>

### <a name="backdatingpostdating-actions"></a><span data-ttu-id="a5f6b-166">Backdating/postdating 조치</span><span class="sxs-lookup"><span data-stu-id="a5f6b-166">Backdating/postdating actions</span></span>

<span data-ttu-id="a5f6b-167">이 메커니즘은 속도가 필요한 작업에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-167">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="a5f6b-168">사용자가 속도에 따라 일련의 대상 지정/활성화 연습를 이동 하는 경우에는 몇 가지 의도를 가정 하 고 사용자가 탭 하기 전후에 약간의 포커스에 있는 대상에 대 한 *작업을 수행할* 수 있도록 하는 것이 유용할 수 있습니다 (전/후의 50ms 초기 테스트에서 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-168">When a user is moving through a series of targeting/activation maneuvers at speed, it can be useful to assume some intent and allow *missed steps* to act upon targets which the user had in focus slightly before or slightly after the tap (50ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="a5f6b-169">다듬기</span><span class="sxs-lookup"><span data-stu-id="a5f6b-169">Smoothing</span></span>

<span data-ttu-id="a5f6b-170">이 메커니즘은 경로 이동에 유용하며, 자연스러운 머리 움직임 특성 때문에 발생하는 약간의 떨림/흔들림을 줄여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-170">This mechanism is useful for pathing movements, reducing the slight jitter/wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="a5f6b-171">경로 생성 동작에 다듬기가 적용될 때, 시간보다는 크기/이동 거리에 따라 다듬기가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-171">When smoothing over pathing motions, smooth by size/distance of movements rather than over time</span></span>

### <a name="magnetism"></a><span data-ttu-id="a5f6b-172">자성</span><span class="sxs-lookup"><span data-stu-id="a5f6b-172">Magnetism</span></span>

<span data-ttu-id="a5f6b-173">이 메커니즘은 "가장 가까운 링크" 알고리즘보다 일반적인 버전으로 생각할 수 있습니다. 사용자의 의도에 더 잘 접근하기 위해 대화형 레이아웃에 대한 지식을 사용하여 사용자가 잠재적인 대상에 접근하면 대상 쪽으로 커서를 그리거나 hitbox(표시 여부와 상관 없이)를 키웁니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-173">This mechanism can be thought of as a more general version of "Closest link" algorithms - drawing a cursor toward a target, or simply increasing hitboxes (whether visibly or not) as users approach likely targets, using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="a5f6b-174">특히 작은 대상에 강력한 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-174">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="a5f6b-175">포커스 고착</span><span class="sxs-lookup"><span data-stu-id="a5f6b-175">Focus stickiness</span></span>

<span data-ttu-id="a5f6b-176">주변 상호 작용 요소 중 어디에 포커스를 둬야 할 지 결정할 때, 현재 포커스가 있는 요소에 바이어스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-176">When determining which nearby interactive elements to give focus to, provide a bias to the element that is currently focused.</span></span> <span data-ttu-id="a5f6b-177">자연 소음이 있는 두 요소 사이의 중간 지점에서 부동 상태인 경우, 불규칙한 포커스 전환 동작을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5f6b-177">This will help reduce erratic focus switching behaviours when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5f6b-178">참조</span><span class="sxs-lookup"><span data-stu-id="a5f6b-178">See also</span></span>
* [<span data-ttu-id="a5f6b-179">제스처</span><span class="sxs-lookup"><span data-stu-id="a5f6b-179">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="a5f6b-180">음성 명령</span><span class="sxs-lookup"><span data-stu-id="a5f6b-180">Voice commanding</span></span>](voice-design.md)
* [<span data-ttu-id="a5f6b-181">커서</span><span class="sxs-lookup"><span data-stu-id="a5f6b-181">Cursors</span></span>](cursors.md)
