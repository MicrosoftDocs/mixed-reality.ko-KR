---
title: 응시 및 커밋
description: 눈길 또는 head 입력을 사용 하는 "응시 및 커밋" 입력 모델의 일반 개요입니다.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: 혼합 현실, 응시, 응시 대상 지정, 상호 작용, 디자인, 눈 추적, head 추적
ms.openlocfilehash: df152f6a3a6e4ae2d6c32a0c56fbb615bcfa7aa8
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375850"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="428b4-104">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="428b4-104">Gaze and commit</span></span>

<span data-ttu-id="428b4-105">_응시 및 commit_ 은 마우스를 사용 하 여 컴퓨터와 상호 작용 하는 방법과 밀접 하 게 관련 된 기본적인 입력 모델입니다. _& 클릭_합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-105">_Gaze and commit_ is a fundamental input model that is closely related with the way we're interacting with our computers using the mouse: _Point & click_.</span></span>
<span data-ttu-id="428b4-106">이 페이지에서는 두 가지 유형의 응시 입력 (헤드 및 눈에 해당)과 다양 한 커밋 작업 유형을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> 
<span data-ttu-id="428b4-107">_응시 및 commit_ 은 간접 조작이 있는 far 입력 모델로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span>
<span data-ttu-id="428b4-108">즉, 도달 하지 않은 holographic 콘텐츠와 상호 작용 하는 데 가장 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-108">This means it is best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="428b4-109">혼합 현실 헤드셋은 사용자 헤드의 위치와 방향을 사용 하 여 헤드 벡터를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="428b4-110">사용자의 눈 사이에서 앞을 똑바로 가리키는 레이저라고 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-110">You can think of this as a laser that points straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="428b4-111">이것은 사용자가 보고 있는 위치에 대한 대략적인 근사치입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="428b4-112">응용 프로그램은 가상 또는 실제 개체와이 광선을 교차 하 고 해당 위치에 커서를 그려 사용자에 게 현재 대상으로 지정 된 항목을 알 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they are currently targeting.</span></span>

<span data-ttu-id="428b4-113">헤드 응시 외에도 HoloLens 2와 같은 일부 혼합 현실 헤드셋은 눈에 잘 맞는 벡터를 생성 하는 눈 추적 시스템을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="428b4-114">이를 통해 사용자가 보는 위치를 세밀하게 측정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="428b4-115">두 경우 모두, 응시는 사용자의 의도에 대 한 중요 한 신호를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="428b4-116">시스템에서 사용자의 의도 된 작업을 해석 하 고 예측할 수 있으므로 사용자 만족도가 향상 되 고 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-116">The better the system can interpret and predict the user's intended actions, user satisfaction increases and performance improves.</span></span>

<span data-ttu-id="428b4-117">다음은 혼합 현실 개발자가 헤드 또는 눈에 잘 응시 할 수 있는 방법에 대 한 몇 가지 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="428b4-118">앱은 장면의 holograms와 교차 하 여 사용자의 주의가 되는 위치를 확인할 수 있습니다 (눈에 띄게 더 정확 하 게).</span><span class="sxs-lookup"><span data-stu-id="428b4-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="428b4-119">앱은 사용자의 응시를 바탕으로 채널 제스처와 컨트롤러를 누르면 사용자가 원활 하 게 선택, 활성화, 잡기, 스크롤 또는 holograms과 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-119">Your app can channel gestures and controller presses based on the user's gaze, letting the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="428b4-120">앱을 사용 하면 사용자가 holograms 표면에 해당 응시 광선과 공간 매핑 메시를 교차 하 여 실제 표면에 놓을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="428b4-121">앱은 사용자가 중요 한 개체의 방향을 확인 *하지 않는* 경우를 알 수 있습니다. 그러면 응용 프로그램에서 시각적 개체와 오디오 신호를 제공 하 여 해당 개체를 가리킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-121">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>


## <a name="device-support"></a><span data-ttu-id="428b4-122">장치 지원</span><span class="sxs-lookup"><span data-stu-id="428b4-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="428b4-123"><strong>입력 모델</strong></span><span class="sxs-lookup"><span data-stu-id="428b4-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="428b4-124"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="428b4-124"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="428b4-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="428b4-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="428b4-126"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="428b4-126"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="428b4-127">헤드 게이즈(head-gaze) 및 커밋</span><span class="sxs-lookup"><span data-stu-id="428b4-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="428b4-128">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="428b4-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="428b4-129">✔️ 권장(세 번째 선택 - <a href="interaction-fundamentals.md">다른 옵션 보기</a>)</span><span class="sxs-lookup"><span data-stu-id="428b4-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="428b4-130">➕ 대체 옵션</span><span class="sxs-lookup"><span data-stu-id="428b4-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="428b4-131">시선 응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="428b4-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="428b4-132">❌ 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="428b4-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="428b4-133">✔️ 권장(세 번째 선택 - <a href="interaction-fundamentals.md">다른 옵션 보기</a>)</span><span class="sxs-lookup"><span data-stu-id="428b4-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="428b4-134">❌ 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="428b4-134">❌ Not available</span></span></td>
    </tr>
</table>


## <a name="gaze"></a><span data-ttu-id="428b4-135">응시</span><span class="sxs-lookup"><span data-stu-id="428b4-135">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="428b4-136">눈 또는 헤드-응시?</span><span class="sxs-lookup"><span data-stu-id="428b4-136">Eye- or head-gaze?</span></span>
<span data-ttu-id="428b4-137">"눈에 응시 하 고 커밋" 또는 "헤드-응시 및 커밋" 입력 모델을 사용 해야 하는지 여부와 관련 하 여 고려해 야 할 몇 가지 고려 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-137">There are several considerations to take into account when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="428b4-138">몰입 형 헤드셋 또는 HoloLens 용으로 개발 하는 경우 (첫 번째 gen) 선택은 간단 합니다. 헤드-응시 및 커밋입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-138">If you're developing for an immersive headset or for HoloLens (1st gen) then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="428b4-139">HoloLens 2 용으로 개발 하는 경우이를 선택 하는 것이 약간 더 어렵습니다. 이러한 이유로 각 항목에서 제공 하는 장점과 문제를 이해 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-139">If you're developing for HoloLens 2, the choice becomes a little harder which is why it's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="428b4-140">아래 표에서 광범위 한 pro 및 con을 컴파일하여 헤드와 눈동자 대상 지정을 대조 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-140">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="428b4-141">이것은 완료 된 것이 아니므로 여기에서 혼합 현실에서 눈에 잘 못 한 대상 지정에 대해 자세히 알아보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-141">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="428b4-142">[Hololens의 눈동자 추적 2](eye-tracking.md): 몇 가지 개발자 지침을 포함 하 여 hololens 2에 대 한 새로운 눈 추적 기능을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-142">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="428b4-143">[눈동자-응시 상호 작용](eye-gaze-interaction.md): 입력으로 눈동자 추적을 사용할 계획인 경우 디자인 고려 사항 및 권장 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-143">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="428b4-144"><strong>눈동자-응시 대상 지정</strong></span><span class="sxs-lookup"><span data-stu-id="428b4-144"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="428b4-145"><strong>헤드-응시 대상 지정</strong></span><span class="sxs-lookup"><span data-stu-id="428b4-145"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="428b4-146">빠르지!</span><span class="sxs-lookup"><span data-stu-id="428b4-146">Fast!</span></span></td>
        <td><span data-ttu-id="428b4-147">느리다는</span><span class="sxs-lookup"><span data-stu-id="428b4-147">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="428b4-148">낮은 노력 (거의 모든 본문 이동 필요)</span><span class="sxs-lookup"><span data-stu-id="428b4-148">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="428b4-149">Fatiguing 수 있습니다 (예: discomfort).</span><span class="sxs-lookup"><span data-stu-id="428b4-149">Can be fatiguing - Possible discomfort (e.g., neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="428b4-150">에는 커서가 필요 하지 않지만 미묘한 피드백을 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-150">Does not require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="428b4-151">커서를 표시 해야 함</span><span class="sxs-lookup"><span data-stu-id="428b4-151">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="428b4-152">부드러운 눈 이동 없음 – 예: 그리기에 적합 하지 않음</span><span class="sxs-lookup"><span data-stu-id="428b4-152">No smooth eye movements – e.g., not good for drawing</span></span></td>
        <td><span data-ttu-id="428b4-153">추가 제어 및 명시적</span><span class="sxs-lookup"><span data-stu-id="428b4-153">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="428b4-154">매우 작은 대상 (예: 작은 단추 또는 weblinks)에 대해 어려움</span><span class="sxs-lookup"><span data-stu-id="428b4-154">Difficult for very small targets (e.g., tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="428b4-155">높고!</span><span class="sxs-lookup"><span data-stu-id="428b4-155">Reliable!</span></span> <span data-ttu-id="428b4-156">뛰어난 대체</span><span class="sxs-lookup"><span data-stu-id="428b4-156">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="428b4-157">...</span><span class="sxs-lookup"><span data-stu-id="428b4-157">...</span></span></td>
        <td><span data-ttu-id="428b4-158">...</span><span class="sxs-lookup"><span data-stu-id="428b4-158">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="428b4-159">사용자의 응시 [및 커밋 입력](gaze-and-commit-head.md) 모델에 대해 head-응시 또는 눈동자를 사용 하는 [것은 각각](gaze-and-commit-eyes.md) 다른 디자인 제약 조건 집합과 함께 제공 됩니다 .이 제약 조건은 다른 디자인 제약 조건으로 제공 됩니다</span><span class="sxs-lookup"><span data-stu-id="428b4-159">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model comes with different sets of design constraints, which will be covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="428b4-160">Cursor</span><span class="sxs-lookup"><span data-stu-id="428b4-160">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="428b4-161">헤드 응시의 경우 대부분의 앱은 [커서](cursors.md) (또는 기타 청각/시각적 표시)를 사용 하 여 사용자가 상호 작용 하려는 항목을 사용자에 게 확실 하 게 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-161">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="428b4-162">일반적으로 헤드 응시 광선이 먼저 개체와 교차 하는 위치에이 커서를 배치 합니다 .이는 홀로그램 또는 실제 표면이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-162">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="428b4-163">아이 응시의 경우 일반적으로 사용자에 게 혼란을 줄 수 있으므로 커서를 표시 *하지 않는* 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-163">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="428b4-164">대신 시각적 대상을 미세 하 게 강조 표시 하거나 매우 희미 한 눈 커서를 사용 하 여 사용자가 상호 작용할 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-164">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="428b4-165">자세한 내용은 HoloLens 2의 [눈동자 기반 입력에 대 한 디자인 지침](eye-tracking.md) 을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="428b4-165">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="428b4-166">응시를 표시 하는 예제 시각적 커서 ![](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="428b4-166">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="428b4-167">*이미지: 응시를 표시 하는 예제 시각적 커서*</span><span class="sxs-lookup"><span data-stu-id="428b4-167">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="428b4-168">커밋</span><span class="sxs-lookup"><span data-stu-id="428b4-168">Commit</span></span>
<span data-ttu-id="428b4-169">대상 _에 참여 하는_ 다양 한 방법에 대해 이야기 한 후에는 _응시 및 commit_의 _커밋_ 부분에 대해 좀 더 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-169">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="428b4-170">개체 또는 UI 요소를 대상으로 지정한 후에는 사용자가 보조 입력을 사용 하 여 상호 작용 하거나 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-170">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="428b4-171">이를 입력 모델의 커밋 단계 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-171">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="428b4-172">지원되는 커밋 메서드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-172">The following commit methods are supported:</span></span>
- <span data-ttu-id="428b4-173">공기 탭 제스처 (즉, 사용자의 앞에 손을 올리고 인덱스 손가락 및 엄지 단추를 통합)</span><span class="sxs-lookup"><span data-stu-id="428b4-173">Air tap hand gesture (i.e., raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="428b4-174">_"Select"_ 또는 대상 음성 명령 중 하나를 말합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-174">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="428b4-175">[HoloLens Clicker](hardware-accessories.md#hololens-clicker) 에서 단일 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-175">Press a single button on a [HoloLens Clicker](hardware-accessories.md#hololens-clicker)</span></span>
- <span data-ttu-id="428b4-176">Xbox 게임 패드에서 ' A ' 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-176">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="428b4-177">Xbox 적응 컨트롤러에서 ' A ' 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-177">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="428b4-178">응시 및 air 탭 제스처</span><span class="sxs-lookup"><span data-stu-id="428b4-178">Gaze and air tap gesture</span></span>
<span data-ttu-id="428b4-179">에어 탭은 손을 똑바로 세워서 탭하는 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-179">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="428b4-180">공중 탭을 수행 하려면 인덱스 손가락을 준비 위치로 올리고 엄지 단추를 누른 후 인덱스 손가락을 다시 릴리스로 올립니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-180">To perform an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="428b4-181">HoloLens (첫 번째 gen)에서 air 탭은 가장 일반적인 보조 입력입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-181">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="428b4-182">준비 위치에 손가락을 ![](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="428b4-182">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="428b4-183">**준비 위치의 핑거**</span><span class="sxs-lookup"><span data-stu-id="428b4-183">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="428b4-184">손가락 아래로 ![눌러 탭 하거나 클릭](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="428b4-184">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="428b4-185">**손가락 아래로를 눌러 탭 하거나 클릭 합니다.**</span><span class="sxs-lookup"><span data-stu-id="428b4-185">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="428b4-186">항공기 탭은 HoloLens 2 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-186">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="428b4-187">원래 버전에서 완화 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-187">It has been relaxed from the original version.</span></span> <span data-ttu-id="428b4-188">이제는 손을 수직이 고 그대로 유지 되는 동안 거의 모든 유형의 pinches이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-188">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="428b4-189">따라서 사용자가 동작을 배우고 수행하기 훨씬 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-189">This makes it much easier for users to learn and perform the gesture.</span></span> <span data-ttu-id="428b4-190">새 공중 탭은 동일한 API를 통해 이전 항목을 대체 하므로 HoloLens 2를 다시 컴파일한 후 기존 응용 프로그램에서 자동으로 새 동작을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-190">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="428b4-191">응시 및 "선택" 음성 명령</span><span class="sxs-lookup"><span data-stu-id="428b4-191">Gaze and "Select" voice command</span></span>
<span data-ttu-id="428b4-192">음성 명령은 혼합 현실에서 기본 상호 작용 방법 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-192">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="428b4-193">시스템을 제어 하는 매우 강력한 수동 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-193">It provides a very powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="428b4-194">음성 상호 작용 모델에는 다음과 같은 다양 한 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-194">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="428b4-195">클릭 actuation를 수행 하거나 보조 입력으로 커밋하는 일반 "Select" 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-195">The generic "Select" command that performs a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="428b4-196">개체 명령 (예: "Close" 또는 "더 크게 설정")은 작업을 수행 하 고 보조 입력으로 작업을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-196">Object commands (e.g., "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="428b4-197">전역 명령 (예: "시작으로 이동")은 대상이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-197">Global commands (e.g., "Go to start") don't require a target.</span></span>
- <span data-ttu-id="428b4-198">대화 사용자 인터페이스 또는 Cortana와 같은 엔터티는 AI 자연어 기능을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-198">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="428b4-199">사용자 지정 음성 명령</span><span class="sxs-lookup"><span data-stu-id="428b4-199">Custom voice commands</span></span>

<span data-ttu-id="428b4-200">사용 가능한 음성 명령의 포괄적인 목록과 사용 방법에 대 한 자세한 내용을 보려면 [음성 명령](voice-design.md) 지침을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="428b4-200">To find out more details as well as a comprehensive list of available voice commands and how to use them, check out our [voice commanding](voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="428b4-201">응시 및 HoloLens Clicker</span><span class="sxs-lookup"><span data-stu-id="428b4-201">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="428b4-202">HoloLens Clicker는 HoloLens 용으로 특별히 구축 된 첫 번째 주변 장치입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-202">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="428b4-203">HoloLens (첫 번째 gen) 개발 버전에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-203">It is included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="428b4-204">HoloLens Clicker를 사용 하면 사용자가 최소한의 손 동작을 클릭 하 고 보조 입력으로 커밋할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-204">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="428b4-205">HoloLens Clicker는 Bluetooth 저 에너지 (BTLE)를 사용 하 여 HoloLens (첫 번째 gen) 또는 HoloLens 2에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-205">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="428b4-206">장치를 페어링 하는 방법에 대 한 자세한 내용 및 지침</span><span class="sxs-lookup"><span data-stu-id="428b4-206">More information and instructions to pair the device</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="428b4-207">*이미지: HoloLens Clicker*</span><span class="sxs-lookup"><span data-stu-id="428b4-207">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="428b4-209">응시 및 Xbox 무선 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="428b4-209">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="428b4-210">Xbox 무선 컨트롤러는 ' A ' 단추를 사용 하 여 클릭 actuation를 보조 입력으로 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-210">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="428b4-211">장치는 시스템을 탐색 하 고 제어 하는 데 도움이 되는 기본 작업 집합에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-211">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="428b4-212">컨트롤러를 사용자 지정 하려면 Xbox 액세서리 응용 프로그램을 사용 하 여 Xbox 무선 컨트롤러를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-212">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="428b4-213">Xbox 컨트롤러와 PC를 페어링 하는 방법</span><span class="sxs-lookup"><span data-stu-id="428b4-213">How to pair an Xbox controller with your PC</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="428b4-214">*이미지: Xbox 무선 컨트롤러*</span><span class="sxs-lookup"><span data-stu-id="428b4-214">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Xbox 무선 컨트롤러](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="428b4-216">응시 및 Xbox 적응 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="428b4-216">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="428b4-217">주로 모바일 기능이 제한 된 게이머의 요구 사항을 충족 하기 위해 설계 된 Xbox 적응 컨트롤러는 혼합 현실에 더 쉽게 액세스할 수 있도록 지 원하는 장치에 대 한 통합 허브입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-217">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="428b4-218">Xbox 적응 컨트롤러는 ' A ' 단추를 사용 하 여 클릭 actuation를 보조 입력으로 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-218">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="428b4-219">장치는 시스템을 탐색 하 고 제어 하는 데 도움이 되는 기본 작업 집합에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-219">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="428b4-220">컨트롤러를 사용자 지정 하려면 Xbox 액세서리 응용 프로그램을 사용 하 여 Xbox 적응 컨트롤러를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-220">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="428b4-221">![Xbox 적응형 컨트롤러](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="428b4-221">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="428b4-222">*Xbox 적응형 컨트롤러*</span><span class="sxs-lookup"><span data-stu-id="428b4-222">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="428b4-223">스위치, 단추, 탈것, 조이스틱 등의 외부 장치를 연결 하 여 고유한 사용자 지정 컨트롤러 환경을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-223">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="428b4-224">단추, 엄지 스틱 및 트리거 입력은 3.5 mm 잭 및 USB 포트를 통해 연결 된 보조 장치를 사용 하 여 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-224">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5mm jacks and USB ports.</span></span>

<span data-ttu-id="428b4-225">![Xbox 적응형 컨트롤러 포트](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="428b4-225">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="428b4-226">*Xbox 적응형 컨트롤러 포트*</span><span class="sxs-lookup"><span data-stu-id="428b4-226">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="428b4-227">디바이스 페어링 지침</span><span class="sxs-lookup"><span data-stu-id="428b4-227">Instructions to pair the device</span></span>](hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="428b4-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Xbox 사이트의 더 많은 정보</a></span><span class="sxs-lookup"><span data-stu-id="428b4-228"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="428b4-229">복합 제스처</span><span class="sxs-lookup"><span data-stu-id="428b4-229">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="428b4-230">에어 탭</span><span class="sxs-lookup"><span data-stu-id="428b4-230">Air tap</span></span>
<span data-ttu-id="428b4-231">아래에 있는 다른 제스처 뿐만 아니라 공기 탭 제스처는 특정 탭에만 반응 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-231">The air tap gesture (as well as the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="428b4-232">메뉴 또는와 같은 다른 탭을 검색 하려면 응용 프로그램에서 위의 두 키 구성 요소 제스처 섹션에 설명 된 하위 수준 상호 작용을 직접 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-232">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="428b4-233">길게 누르기</span><span class="sxs-lookup"><span data-stu-id="428b4-233">Tap and hold</span></span>
<span data-ttu-id="428b4-234">홀드(hold)는 에어 탭의 아래쪽 손가락 위치를 유지하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-234">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="428b4-235">공기 탭 및 유지의 조합을 사용 하면 개체를 활성화 하는 대신 개체를 선택 하거나 상황에 맞는 메뉴를 표시 하는 것과 같이 개체를 선택 하는 것과 같이 arm 이동과 결합 하 여 복잡 한 "클릭 및 끌기" 상호 작용을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-235">The combination of air tap and hold allows for a variety of more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="428b4-236">단, 이러한 제스처를 디자인할 때는 주의가 필요합니다. 확장된 동작을 하는 동안 사용자가 손의 자세를 푸는 경향이 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-236">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during the course of any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="428b4-237">조작</span><span class="sxs-lookup"><span data-stu-id="428b4-237">Manipulation</span></span>
<span data-ttu-id="428b4-238">사용자의 손을 이동 하 여 홀로그램에서 1:1에 반응할 수 있도록 하려면 조작 제스처를 사용 하 여 홀로그램을 이동, 크기 조정 또는 회전할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-238">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="428b4-239">이러한 1:1 움직임을 사용하는 한 가지 방식은 실제로 선을 긋거나 그릴 수 있도록 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-239">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="428b4-240">조작 제스처에 대한 초기 타기팅은 응시 또는 포인팅을 통해 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-240">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="428b4-241">탭 하 여 보류가 시작 되 면 개체 조작을 직접 이동 하 여 조작 하는 동안 사용자가 쉽게 볼 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-241">Once the tap and hold starts, any manipulation of the object is handled by hand movements, freeing the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="428b4-242">탐색</span><span class="sxs-lookup"><span data-stu-id="428b4-242">Navigation</span></span>
<span data-ttu-id="428b4-243">탐색 제스처는 가상 조이스틱처럼 작동하며 방사형 메뉴와 같은 UI 위젯을 탐색하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-243">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="428b4-244">길게 눌러서 제스처를 시작한 후 초기에 누른 부분을 중심으로 정규화된 3D 큐브 안에서 손을 움직입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-244">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="428b4-245">X, Y, Z 축을 따라 -1에서 1로 손을 움직일 수 있고, 시작점은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-245">You can move your hand along the X, Y or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="428b4-246">탐색은 속도 기반 연속 스크롤 또는 확대/축소 제스처를 빌드하는 데 사용할 수 있으며, 마우스 가운데 단추를 클릭한 다음, 마우스를 위아래로 움직여서 2D UI를 스크롤하는 것과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-246">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="428b4-247">레일을 사용한 탐색은 특정 임계값에 도달할 때까지 특정 축의 움직임을 인식 하는 기능을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-247">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="428b4-248">이는 응용 프로그램이 X, Y 축의 탐색 제스처를 인식 하도록 구성 되어 있지만 레일을 사용 하 여 X 축도 지정 하는 경우와 같이 개발자가 응용 프로그램에서 둘 이상의 축으로 이동 하는 경우에만 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-248">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="428b4-249">이 경우 Y 축에서 직접 이동이 발생 하는 경우 시스템은 x 축에서 허수 레일 (가이드) 내에 유지 되는 동안 X 축에서 직접 이동 하는 것을 인식 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-249">In this case the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="428b4-250">2D 앱에서는 사용자가 세로 탐색 제스처를 사용하여 앱 내에서 스크롤, 확대/축소 또는 끌기를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-250">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="428b4-251">그러면 앱에 가상 손가락 터치가 삽입되어 같은 유형의 터치 제스처가 시뮬레이션됩니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-251">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="428b4-252">사용자는 단추를 선택 하거나 ' < 스크롤/끌기/확대/축소 > 도구 '를 사용 하 여 응용 프로그램 위에 있는 막대의 도구 사이를 전환 하 여 수행할 작업을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-252">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="428b4-253">복합 제스처에 대한 추가 정보</span><span class="sxs-lookup"><span data-stu-id="428b4-253">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="428b4-254">제스처 인식기</span><span class="sxs-lookup"><span data-stu-id="428b4-254">Gesture recognizers</span></span>

<span data-ttu-id="428b4-255">제스처 인식 기능을 사용 하는 경우의 한 가지 장점 중 하나는 현재 대상 홀로그램에서 수락할 수 있는 제스처에 대해서만 제스처 인식기를 구성할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-255">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="428b4-256">플랫폼은 지원 되는 특정 제스처를 구분 하기 위해 필요에 따라 명확성을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-256">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="428b4-257">이러한 방식으로, 살짝 누르기를 지 원하는 홀로그램은 press와 release 사이에 모든 시간을 허용할 수 있는 반면, 탭 및 유지를 모두 지 원하는 홀로그램은 대기 시간 임계값 후에 탭을 보류 중으로 승격할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-257">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="428b4-258">손 인식</span><span class="sxs-lookup"><span data-stu-id="428b4-258">Hand recognition</span></span>
<span data-ttu-id="428b4-259">HoloLens는 디바이스에 보이는 한쪽 또는 양쪽 손의 위치를 추적하여 손 제스처를 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-259">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="428b4-260">HoloLens는 손이 준비 상태(집게손가락을 올리고 손등을 마주보고 있는 상태)이거나 눌린 상태(집게손가락을 내리고 손등을 마주보고 있는 상태)일 때 손을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-260">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="428b4-261">손이 다른 포즈에 있는 경우 HoloLens는이를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-261">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="428b4-262">HoloLens가 검색 하는 각 손으로는 방향 및 눌린 상태 없이 해당 위치에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-262">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="428b4-263">손이 제스처 프레임의 가장자리에 가까워지면, 방향 벡터가 제공됩니다. 이것을 사용자에게 표시하면, HoloLens에게 보이는 위치로 손을 다시 이동하려면 손을 어떻게 움직여야 하는지를 사용자가 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-263">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="428b4-264">제스처 프레임</span><span class="sxs-lookup"><span data-stu-id="428b4-264">Gesture frame</span></span>
<span data-ttu-id="428b4-265">HoloLens의 제스처의 경우이 손을 제스처 프레임 내에 있어야 합니다. 제스처는 제스처-감지 카메라에서 적절 하 게 볼 수 있는 범위에서 접근 waist와 사이에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-265">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="428b4-266">사용자는 작업 성공 및 자신에 게 편안 하 게 사용할 수 있도록이 영역에 대 한 교육을 받아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-266">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="428b4-267">대부분의 사용자는 처음에는 HoloLens를 통해 제스처 프레임이 보기 내에 있어야 하 고 상호 작용 하기 위해 편안 하 게 유지 하는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-267">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold their arms up uncomfortably in order to interact.</span></span> <span data-ttu-id="428b4-268">HoloLens Clicker를 사용 하는 경우에는 손을 제스처 프레임 안에 포함 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-268">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="428b4-269">특히 연속 제스처의 경우 holographic 개체를 이동 하는 경우 중간 제스처를 사용 하 고 의도 하지 않은 결과를 잃지 못하도록 제스처 프레임 외부에서 손을 이동할 위험이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-269">In the case of continuous gestures in particular, there is some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="428b4-270">다음 세 가지 사항을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-270">There are three things that you should consider:</span></span>

- <span data-ttu-id="428b4-271">제스처 프레임의 존재 및 근사치 범위에 대 한 사용자 교육입니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-271">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="428b4-272">HoloLens를 설정 하는 동안이를 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-272">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="428b4-273">응용 프로그램 내의 제스처 프레임 경계에 도달 하거나 해당 제스처가 원치 않는 결과로 이어질 수 있는 수준까지 사용자에 게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-273">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="428b4-274">Research는 이러한 알림 시스템의 주요 품질을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-274">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="428b4-275">HoloLens shell은 경계가 교차 하는 방향을 나타내는 중앙 커서에 이러한 유형의 알림 (시각적 개체)에 대 한 좋은 예를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-275">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="428b4-276">제스처 프레임 경계를 벗어난 결과는 최소화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-276">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="428b4-277">일반적으로이는 제스처의 결과가 경계에서 중지 되 고 반전 되지 않음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-277">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="428b4-278">예를 들어 사용자가 실내에서 일부 holographic 개체를 이동 하는 경우 제스처 프레임이 위반 되 면 이동이 중지 되 고 시작 지점으로 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-278">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="428b4-279">사용자에 게 몇 가지 문제가 발생할 수 있지만, 경계를 보다 신속 하 게 이해 하 고 매번 원하는 작업을 다시 시작 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="428b4-279">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="428b4-280">참고 항목</span><span class="sxs-lookup"><span data-stu-id="428b4-280">See also</span></span>
* [<span data-ttu-id="428b4-281">시선 기반 상호 작용</span><span class="sxs-lookup"><span data-stu-id="428b4-281">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="428b4-282">HoloLens 2의 시선 추적</span><span class="sxs-lookup"><span data-stu-id="428b4-282">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="428b4-283">응시 및 유지</span><span class="sxs-lookup"><span data-stu-id="428b4-283">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="428b4-284">손 - 직접 조작</span><span class="sxs-lookup"><span data-stu-id="428b4-284">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="428b4-285">손 - 제스처</span><span class="sxs-lookup"><span data-stu-id="428b4-285">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="428b4-286">손 - 가리키기 및 커밋</span><span class="sxs-lookup"><span data-stu-id="428b4-286">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="428b4-287">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="428b4-287">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="428b4-288">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="428b4-288">Voice input</span></span>](voice-input.md)

