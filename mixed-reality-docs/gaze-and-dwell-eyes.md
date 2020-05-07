---
title: 시선 응시 및 유지(dwell)
description: 시선 응시 및 유지(dwell) 입력 모델에 대한 개요
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
ms.localizationpriority: high
keywords: 시선 추적, 혼합 현실, 입력, 시선 응시, 시선 겨냥, HoloLens 2, 시선 기반 선택, 유지(dwell)
ms.openlocfilehash: ba793f6b1a95fe4b95aa9a043d36823487886b5e
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604904"
---
# <a name="eye-gaze-and-dwell"></a><span data-ttu-id="535b0-104">시선 응시 및 유지(dwell)</span><span class="sxs-lookup"><span data-stu-id="535b0-104">Eye-gaze and dwell</span></span>

<span data-ttu-id="535b0-105">_"시선 응시 및 유지"_ 상호 작용 모델은 [시선 응시 및 커밋](gaze-and-commit.md) 상호 작용 모델의 특별한 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-105">The _"eye-gaze and dwell"_ interaction model is a special case of the [eye-gaze and commit](gaze-and-commit.md) interaction model:</span></span>
1. <span data-ttu-id="535b0-106">단순히 대상 바라보기</span><span class="sxs-lookup"><span data-stu-id="535b0-106">Simply look at a target and</span></span> 
2. <span data-ttu-id="535b0-107">대상을 선택하려는 의도를 확인하려면 명시적인 보조 입력을 수행합니다. 선택하려는 대상을 계속 보기만 하면 됩니다. </span><span class="sxs-lookup"><span data-stu-id="535b0-107">To confirm your intention to select the target, perform a secondary explicit input: _Simply keep looking at the target you would like to select_.</span></span>

## <a name="advantages-of-the-eye-gaze-and-dwell-interaction-model"></a><span data-ttu-id="535b0-108">"시선 응시 및 유지" 상호 작용 모델의 장점</span><span class="sxs-lookup"><span data-stu-id="535b0-108">Advantages of the "eye-gaze and dwell" interaction model</span></span> 
<span data-ttu-id="535b0-109">손으로 작업 중이나 도구를 잡고 있으면 홀로그램과 상호 작용하는 데 손을 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-109">When your hands are already occupied with a task or holding tools, using them for interacting with holograms may not be an option.</span></span>
<span data-ttu-id="535b0-110">"시선 응시 및 유지" 또는 다른 말로 : _"바라보기(look and stare)"_ 는 홀로그램을 선택할 수 있는 핸즈프리 상호 작용 대안입니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-110">A hands-free interaction alternative for selecting holograms is "eye-gaze and dwell" or in other words: _"look and stare"_.</span></span> <span data-ttu-id="535b0-111">이러한 접근 방식의 장점은 움직임이 심하게 제한되어 머리나 몸을 완전히 돌릴 수 없는 사용자라도 홀로그램과 상호 작용이 가능하다는 점입니다(예: 고도로 제한된 작업 환경).</span><span class="sxs-lookup"><span data-stu-id="535b0-111">The advantage of this approach is that even severely constrained users who may not be able to fully turn their heads or bodies can interact with holograms (e.g., in a highly confined work environment).</span></span>
<span data-ttu-id="535b0-112">사용자가 선택하고 싶은 대상을 계속 보기만 하면 프로세스를 나타내는 다른 유지(dwell) 피드백이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-112">The user simply keeps looking at the target they would like to select and different dwell feedback is displayed to indicate the process.</span></span>


## <a name="challenges-of-the-eye-gaze-and-dwell-interaction-model"></a><span data-ttu-id="535b0-113">"시선 응시 및 유지" 상호 작용 모델의 과제</span><span class="sxs-lookup"><span data-stu-id="535b0-113">Challenges of the "eye-gaze and dwell" interaction model</span></span>
<span data-ttu-id="535b0-114">일반적으로 유지(dwell) 기반 활성화는 음성 입력이나 손 입력을 모두 사용할 수 없는 경우에만 마지막 대체 수단으로 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-114">In general, we  recommend to only use dwell-based activations as a last fall-back if neither voice input nor hand input is available.</span></span> <span data-ttu-id="535b0-115">그 이유는 유지(dwell) 시간 선택이 까다로울 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-115">The reason is that the choice of dwell time can be pretty tricky.</span></span> <span data-ttu-id="535b0-116">초보 사용자의 경우 유지(dwell) 시간이 길어도 괜찮지만 숙련된 사용자는 자신의 환경을 빠르고 효율적으로 탐색하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-116">Novice users are ok with longer dwell times, while expert users want to quickly and efficiently navigate through their experiences.</span></span> <span data-ttu-id="535b0-117">따라서 유지(dwell) 시간을 사용자의 특정 요구에 맞게 조정하는 방법이 어려운 과제입니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-117">This leads to the challenge of how to adjust the dwell time to the specific needs of a user.</span></span>
<span data-ttu-id="535b0-118">유지(dwell) 시간이 너무 짧으면: 홀로그램이 항상 사용자의 시선 응시에 반응하기 때문에 사용자가 압도감을 느낄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-118">If the dwell time is too short: The user may feel overwhelmed by having holograms react to their eye-gaze all the time.</span></span> <span data-ttu-id="535b0-119">유지(dwell) 시간이 너무 길면: 사용자가 대상을 오랫동안 계속보고 있어야 해서 환경이 너무 느리고 방해가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-119">If the dwell time is too long: The experience may feel too slow and interruptive as the user has to keep looking at targets for a long time.</span></span>

## <a name="design-recommendations"></a><span data-ttu-id="535b0-120">디자인 권장 사항</span><span class="sxs-lookup"><span data-stu-id="535b0-120">Design recommendations</span></span>
<span data-ttu-id="535b0-121">유지(dwell) 피드백에 두 가지 상태 접근 방식을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-121">We recommend using a two-state approach for dwell feedback:</span></span>
1. <span data-ttu-id="535b0-122">*시작 지연*: 사용자가 대상을 보기 시작할 때는 아무 일도 일어나지 않아야 합니다. 불편하고 대응하기 어려운 환경이 될 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-122">*Onset delay*: When the user starts looking at a target, nothing should immediately happen as this may result in an unpleasant and overwhelming user experience.</span></span> <span data-ttu-id="535b0-123">그 대신 사용자가 대상을 의도적으로 응시하는지 아니면 그냥 훑어보고 있는지를 감지하기 위한 타이머를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-123">Instead start a timer to detect whether the user is intentionally staring at the target or merely glancing over it.</span></span>
<span data-ttu-id="535b0-124">지정된 근접성(사용자가 큰 대상을 주시하고 둘러본다는 의미)에서 시작 시간을 150-250ms 정도로 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-124">We recommend an onset time of 150-250 ms in a given proximity (meaning the user is fixating vs. looking around on a large target).</span></span>  
2. <span data-ttu-id="535b0-125">*유지(dwell) 시작 피드백:* 사용자가 대상을 의도적으로 보고 있는 것이 확인되면 유지(dwell) 피드백을 표시하여 유지(dwell) 활성화가 시작되고 있음을 사용자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-125">*Start dwell feedback:* After ensuring that the user is intentionally looking at the target, start showing dwell feedback to inform the user that the dwell activation is being initiated.</span></span> 
3. <span data-ttu-id="535b0-126">*지속적인 피드백:* 사용자가 대상을 계속 바라보는 동안, 연속 진행 표시기를 나타내서, 사용자가 목표를 계속 바라봐야 한다는 것을 알 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-126">*Continuous Feedback:* While the user keeps looking at the target, show a continuous progress indicator so that the user knows that they have to keep looking at the target.</span></span> <span data-ttu-id="535b0-127">특히 시선 응시 입력의 경우, 큰 원이나 구 모양이 작은 모양으로 줄어드는 효과를 사용하여 _사용자의 시각적 관심을 끄는_ 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-127">In particular for eye-gaze input, we recommend _pulling in the user's visual attention_ by starting out with a bigger circle or sphere that contracts into a smaller version.</span></span> <span data-ttu-id="535b0-128">최종 상태(작은 원)에 대한 지표를 표시하면, 유지(dwell)가 마무리될 때 사용자와 의사 소통하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-128">Showing an indicator for the final state (small circle) helps to communicate to the user when the dwell will be finished.</span></span> <span data-ttu-id="535b0-129">아래 그림은 예시입니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-129">An example illustration is shown below.</span></span> 
4. <span data-ttu-id="535b0-130">*마무리:* 사용자가 대상을 계속 주시하는 경우(650-850 ms 정도 더 오래), 유지(dwell) 활성화를 완료하고 바라본 대상을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="535b0-130">*Finish:* If the user kept fixating the target (for another 650-850 ms), complete the dwell activation and select the looked-at target.</span></span>

![유지(dwell) 상태](images/eyes_dwellstate_recommendation.png)<br>

## <a name="see-also"></a><span data-ttu-id="535b0-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="535b0-132">See also</span></span>
* [<span data-ttu-id="535b0-133">시선 추적</span><span class="sxs-lookup"><span data-stu-id="535b0-133">Eye tracking</span></span>](eye-tracking.md)
* [<span data-ttu-id="535b0-134">시선 응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="535b0-134">Eye-gaze and commit</span></span>](gaze-and-commit-eyes.md)
* [<span data-ttu-id="535b0-135">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="535b0-135">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="535b0-136">응시 및 유지</span><span class="sxs-lookup"><span data-stu-id="535b0-136">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="535b0-137">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="535b0-137">Voice input</span></span>](voice-design.md)
