---
title: 헤드 게이즈(head-gaze) 및 드웰(dwell)
description: 헤드 게이즈(head-gaze) 및 드웰(dwell) 입력 모델에 대한 개요
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: 혼합 현실, 응시, 유지, 상호 작용, 디자인
ms.openlocfilehash: d522ca3a6f36995959e8e6e87482279d05bf0aa3
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387533"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="0ce93-104">헤드 게이즈(head-gaze) 및 드웰(dwell)</span><span class="sxs-lookup"><span data-stu-id="0ce93-104">Head-gaze and dwell</span></span>

<span data-ttu-id="0ce93-105">손에 도구와 파트가 있으면 제스처가 어렵거나 불가능할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="0ce93-106">제스처와 같은 음성 명령은 특정 상황(예: 과도하게 소리가 큰 상황)에서 불안정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="0ce93-107">또한 음성을 사용하여 컴퓨터를 제어하는 것이 전체적으로 일반적이지는 않지만 보편화되고 있는 것은 확실합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="0ce93-108">헤드 게이즈(head-gaze) 및 드웰(dwell)은 HoloLens에서 헤드업 및 핸즈프리 작업을 수행하기에 가장 친숙하고 마스터하기 편한 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="0ce93-109">또한 헤드 게이즈(head-gaze) 및 드웰(dwell)은 운영 환경에서 소음 간섭이나 무음 제약과 상관없이 100% 안정적입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="0ce93-110">시나리오</span><span class="sxs-lookup"><span data-stu-id="0ce93-110">Scenarios</span></span>

<span data-ttu-id="0ce93-111">헤드 게이즈(head-gaze) 및 드웰(dwell)은 손으로 다른 작업을 하고 있으면서 환경이나 주변의 제약 때문에 음성을 100% 안정적으로 사용할 수 없는 경우에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or availible due to environmental or social constraints.</span></span> <span data-ttu-id="0ce93-112">HoloLens를 착용하고 자동차 엔진을 수리하는 동안 참조 정보를 오버레이하는 경우가 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="0ce93-113">엔진 칸에 기대고 있는 몸을 지탱하거나 도구를 다루느라 손을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="0ce93-114">차고 공간에서는 연장이 계속 윙윙거리면서 소리를 내기 때문에 시끄러워서 음성 명령을 실행하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="0ce93-115">헤드 게이즈(head-gaze) 및 드웰(dwell)을 사용하면 워크플로를 방해하지 않으면서 HoloLens를 착용하고 있는 사람이 참조 자료를 자신 있게 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-115">Head-gaze and dwell allows the person in the HoloLens to confidently navigate their reference material without interupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="0ce93-116">장치 지원</span><span class="sxs-lookup"><span data-stu-id="0ce93-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="0ce93-117"><strong>입력 모델</strong></span><span class="sxs-lookup"><span data-stu-id="0ce93-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="0ce93-118"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="0ce93-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="0ce93-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="0ce93-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="0ce93-120"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="0ce93-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="0ce93-121">헤드 게이즈(head-gaze) 및 드웰(dwell)</span><span class="sxs-lookup"><span data-stu-id="0ce93-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="0ce93-122">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="0ce93-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="0ce93-123">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="0ce93-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="0ce93-124">✔️ 권장</span><span class="sxs-lookup"><span data-stu-id="0ce93-124">✔️ Recommended</span></span></td>
    </tr>
</table>

## <a name="goals"></a><span data-ttu-id="0ce93-125">목표</span><span class="sxs-lookup"><span data-stu-id="0ce93-125">Goals</span></span>

<span data-ttu-id="0ce93-126">음성을 사용하지 않는, 완전한 핸즈프리 상호 작용 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-126">Provide a mechanism for fully hands-free interactions, without using voice.</span></span>

## <a name="design-principles"></a><span data-ttu-id="0ce93-127">디자인 원칙</span><span class="sxs-lookup"><span data-stu-id="0ce93-127">Design principles</span></span>

1. <span data-ttu-id="0ce93-128">“과도한 응시” 방지</span><span class="sxs-lookup"><span data-stu-id="0ce93-128">Avoid "Gaze as a weapon"</span></span>

    <span data-ttu-id="0ce93-129">헤드 게이즈(head-gaze) 및 드웰(dwell)에는 직관적인 시각 피드백이 필요하지만 피드백이 너무 많으면 불안정한 상태를 유발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-129">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="0ce93-130">피드백은 사용자가 무엇을 타기팅하는지 파악하는 데 도움이 되어야 하지만 사용자의 의도에 반하여 자동으로 선택되어서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-130">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="0ce93-131">텍스트, 아이콘 및 레이블을 읽으려면 선택하기 전에 정보를 흡수할 여지를 사람에게 제공하기 위한 고려가 추가로 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-131">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
2. <span data-ttu-id="0ce93-132">최적의 속도 구하기</span><span class="sxs-lookup"><span data-stu-id="0ce93-132">Seek Goldilocks speed</span></span>
    
    <span data-ttu-id="0ce93-133">드웰(dwell) 상호 작용은 탐색의 영향력에 따라 타이머가 다를 수 있습니다. 사용 빈도가 높은 함수는 일반적으로 채우기 시간이 빠른 것이 유용하고 중대한 함수는 채우기 시간이 긴 것이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-133">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="0ce93-134">채우기 효과를 사용하여 타이머를 표시하면, 채우기 색상의 애니메이션 곡선이 채우기 시간이 빠른 느낌에 긍정적인 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-134">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="0ce93-135">빠른/중간/느린 채우기 속도 재정의 중에서 사용자가 결정할 수 있도록 고려하는 것이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-135">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
3. <span data-ttu-id="0ce93-136">요요 효과 절대 금지</span><span class="sxs-lookup"><span data-stu-id="0ce93-136">Say no-no to yo-yo effect</span></span>

    <span data-ttu-id="0ce93-137">요요 효과는 불편한 머리 움직임 패턴이며, 콘텐츠 배치와 헤드 게이즈(head-gaze) 및 드웰(dwell) 컨트롤 때문에 사람들이 반복적으로 위아래를 봐야 하는 경우에 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-137">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="0ce93-138">예를 들어, 목록 탐색 아래쪽에 헤드 게이즈(head-gaze) 및 드웰(dwell) 단추가 있으면, 내려다보고 멈추기, 결과 올려다보기, 내려다보고 멈추기를 반복해야 하는 상태를 유발합니다. 이러한 패턴은 불편하기 때문에 왔다 갔다 할 필요가 줄어들도록 탐색 컨트롤을 가운데에 배치하여 피해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-138">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="0ce93-139">쾌적함을 위해 효과에 기반하여 드웰(dwell) 단추를 배치하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-139">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="0ce93-140">UX 지침 및 모범 사례</span><span class="sxs-lookup"><span data-stu-id="0ce93-140">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="0ce93-141">대상 크기</span><span class="sxs-lookup"><span data-stu-id="0ce93-141">Target sizes</span></span>
  <span data-ttu-id="0ce93-142">편리한 액세스를 위해서는, 헤드 게이즈(head-gaze) 및 드웰(dwell) 대상의 크기가 원활하게 대상을 지정할 수 있을 만큼 커야 하며, 지정된 시간 동안 머리가 안정적으로 대상을 향하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-142">To be easily accessible, head-gaze and dwell targets need to be large enough to comforatably target, and hold one's head stabily on the target for the prescribed time.</span></span> <span data-ttu-id="0ce93-143">편리한 사용을 위해서는 대상의 크기가 최소 2도 이상인 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-143">We reccomend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="0ce93-144">시각적 피드백</span><span class="sxs-lookup"><span data-stu-id="0ce93-144">Visual feedback</span></span>

<span data-ttu-id="0ce93-145">드웰(dwell) 타이머를 나타내기 위해 방사형 채우기를 사용하는 경우에는 단추 가운데에서 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-145">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="0ce93-146">일관된 응답이 서로 다른 단추의 모두 다른 방향보다는 덜 혼란스럽습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-146">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="0ce93-147">이 규칙은 방향 상호 작용에 대해 달리 적용될 수도 있습니다(예: 위/아래/왼쪽/오른쪽으로 이동 등)</span><span class="sxs-lookup"><span data-stu-id="0ce93-147">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="0ce93-148">예를 들어, Microsoft Dynamics 365 가이드의 경우 예외적으로 다음/뒤로가 왼쪽에서 오른쪽으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-148">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="0ce93-149">토글 단추를 해제하는 등의 시나리오에서는 바깥쪽에서 방사형 채우기로 반전하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-149">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="0ce93-150">단추 누르기와 반대되는 느낌은 유지하기 좋은 시각 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-150">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="0ce93-151">점진적 공개</span><span class="sxs-lookup"><span data-stu-id="0ce93-151">Progressive disclosure</span></span>

<span data-ttu-id="0ce93-152">점진적인 공개란 상호 작용의 각 단계에 해당하는 세부 정보만 표시하는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-152">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="0ce93-153">드웰(dwell)의 경우, 드웰 대상이 강조 표시로(예: 목록 컨트롤에서) 드러납니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-153">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="0ce93-154">너무 큰 대상</span><span class="sxs-lookup"><span data-stu-id="0ce93-154">Oversized targets</span></span>
<span data-ttu-id="0ce93-155">드웰(dwell) 지역은 Microsoft Dynamics 365 가이드의 뒤로 단추처럼, 사용하기 쉽도록 비활성 아이콘보다 클 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-155">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="0ce93-156">피드백 지연으로 인한 깜박임 방지</span><span class="sxs-lookup"><span data-stu-id="0ce93-156">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="0ce93-157">다른 사람이 드웰(dwell) 대상을 지나칠 때 깜박이지 않도록, 시각 피드백을 시작하기 전에 짧은 지연을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-157">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="0ce93-158">자주 사용하는 단추는 애플리케이션이 반응을 느끼도록 지연을 매우 짧게 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-158">For buttons inteacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="0ce93-159">자주 사용하지 않는 단추는 인터페이스가 불안정해지지 않도록 지연을 길게 하는 것이 더 적절할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-159">For buttons that are interacted with infrequenctly a longer delay can be approprate to avoid the interface feeling twitchy.</span></span>

## <a name="ui-patterns"></a><span data-ttu-id="0ce93-160">UI 패턴</span><span class="sxs-lookup"><span data-stu-id="0ce93-160">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="0ce93-161">높은 빈도 단추</span><span class="sxs-lookup"><span data-stu-id="0ce93-161">High frequency buttons</span></span>
<span data-ttu-id="0ce93-162">![Microsoft Dynamics 365 가이드 다음 단추](images/GuideNextButton.png "Microsoft Dynamics 365 가이드 다음 단추")</span><span class="sxs-lookup"><span data-stu-id="0ce93-162">![Microsoft Dynamics 365 Guides Next Button](images/GuideNextButton.png "Microsoft Dynamics 365 Guides Next Button")</span></span><br>
<span data-ttu-id="0ce93-163">*높은 빈도 단추는 응용 프로그램 전체에서 일반적으로 사용 되는 단추입니다. 이에 대 한 좋은 예로 Microsoft Dynamics 365 가이드의 다음 및 뒤로 단추가 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="0ce93-163">*High frequency buttons are buttons that are used commonly throughout an application. A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.*</span></span>

<span data-ttu-id="0ce93-164">높은 빈도 단추는...</span><span class="sxs-lookup"><span data-stu-id="0ce93-164">High frequency buttons should...</span></span>
* <span data-ttu-id="0ce93-165">크기가 커야 하고, 헤드 게이즈(head-gaze)로 겨냥하기 쉬워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-165">be larger buttons, easier to hit with head-gaze</span></span>
* <span data-ttu-id="0ce93-166">인체의 긴장을 피하기 위해 눈 높이 근처에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-166">stay near eye height to avoid ergonomic straining.</span></span>

### <a name="low-frequency-buttons"></a><span data-ttu-id="0ce93-167">낮은 빈도 단추</span><span class="sxs-lookup"><span data-stu-id="0ce93-167">Low frequency buttons</span></span>
<span data-ttu-id="0ce93-168">낮은 빈도 단추는 애플리케이션 전반에서 정기적으로 상호 작용하지 않는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="0ce93-169">설정 메뉴에 액세스하는 단추 또는 모든 작업을 지우는 단추가 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="0ce93-170">이러한 단추는 우발적인 활성화를 피하기 위해 빈번한 헤드 게이즈(head-gaze) 경로에서 멀리 두는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

### <a name="confirmations"></a><span data-ttu-id="0ce93-171">확인</span><span class="sxs-lookup"><span data-stu-id="0ce93-171">Confirmations</span></span>
<span data-ttu-id="0ce93-172">![Microsoft Dynamics 365 가이드 확인 대화 상자](images/GuidesConfirmation.png "Microsoft Dynamics 365 가이드 확인 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="0ce93-172">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesConfirmation.png "Microsoft Dynamics 365 Guides Confirmation Dialog")</span></span>

<span data-ttu-id="0ce93-173">돈을 청구하거나, 작업을 삭제하거나, 긴 프로세스를 시작하는 등 중대한 영향을 미치는 작업의 경우, 사람이 단추를 선택하도록 하는 것이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-173">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span> <span data-ttu-id="0ce93-174">헤드 게이즈(head-gaze) 및 드웰(dwell) UI의 경우 확인 대화 상자에 대한 몇 가지 패턴과 고려 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-174">For head-gaze and dwell UIs there are some patterns and considerations for confirmation dialogs:</span></span>

  * <span data-ttu-id="0ce93-175">주요 단추의 선택을 강조 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-175">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="0ce93-176">선택 강조 표시와 동시에 드웰(dwell) 대상을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-176">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="0ce93-177">보조 단추의 경우 헤드 게이즈(head-gaze) 시 드웰(dwell) 대상을 드러납니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-177">For the secondary button, reveal the dwell target on head-gaze.</span></span>
        
### <a name="toggle-buttons"></a><span data-ttu-id="0ce93-178">토글 단추</span><span class="sxs-lookup"><span data-stu-id="0ce93-178">Toggle buttons</span></span>
<span data-ttu-id="0ce93-179">토글 단추를 사용하려면 다소 미묘한 논리가 제대로 작동해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-179">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="0ce93-180">사람이 토글 단추를 드웰(dwell)하고 활성화하면 단추를 종료했다가 돌아와서 드웰(dwell) 논리를 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-180">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="0ce93-181">토글 가능한 단추는 활성 대비 비활성 상태가 명확해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-181">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

### <a name="list-views"></a><span data-ttu-id="0ce93-182">목록 보기</span><span class="sxs-lookup"><span data-stu-id="0ce93-182">List views</span></span>
<span data-ttu-id="0ce93-183">![Microsoft Dynamics 365 가이드 확인 대화 상자](images/GuidesListView.png "Microsoft Dynamics 365 가이드 확인 대화 상자")</span><span class="sxs-lookup"><span data-stu-id="0ce93-183">![Microsoft Dynamics 365 Guides Confirmation Dialog](images/GuidesListView.png "Microsoft Dynamics 365 Guides Confirmation Dialog")</span></span><br>
<span data-ttu-id="0ce93-184">*목록 뷰는 헤드-응시 및 지속 입력에 대 한 특정 챌린지를 제공 합니다. 사용자는 유지 목표를 tiptoe 해야 하는 것과 같은 느낌 없이 콘텐츠를 스캔할 수 있어야 합니다.*</span><span class="sxs-lookup"><span data-stu-id="0ce93-184">*List views present a particular challenge for head-gaze and dwell input. People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.*</span></span>

<span data-ttu-id="0ce93-185">목록 보기 디자인을 위한 팁:</span><span class="sxs-lookup"><span data-stu-id="0ce93-185">Some tips for designing list views:</span></span>
* <span data-ttu-id="0ce93-186">헤드 게이즈(head-gaze) 시 전체 행을 강조 표시하되 헤드 게이즈(head-gaze)가 특정한 드웰(dwell) 대상에 있지 않으면 드웰(dwell)을 시작하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-186">have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
* <span data-ttu-id="0ce93-187">시각적 노이즈를 줄이기 위해 행이 강조 표시될 때 드웰(dwell) 대상을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-187">only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
* <span data-ttu-id="0ce93-188">드웰(dwell) 대상의 위치가 명확하고 일관적이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-188">be clear and consistent with the position of dwell targets.</span></span>
* <span data-ttu-id="0ce93-189">반복 UI를 피하기 위해 드웰(dwell) 대상을 한 번에 모두 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-189">don't show all dwell targets at once to avoid repetitive UI</span></span>
* <span data-ttu-id="0ce93-190">UX에 친숙해질 수 있도록 동일한 패턴을 되도록 자주 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0ce93-190">re-use the same pattern as often as possible to establish UX familiarity</span></span>
 
 ## <a name="see-also"></a><span data-ttu-id="0ce93-191">참조</span><span class="sxs-lookup"><span data-stu-id="0ce93-191">See also</span></span>
* [<span data-ttu-id="0ce93-192">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="0ce93-192">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="0ce93-193">수동으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="0ce93-193">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="0ce93-194">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="0ce93-194">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="0ce93-195">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="0ce93-195">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="0ce93-196">음성 명령</span><span class="sxs-lookup"><span data-stu-id="0ce93-196">Voice commanding</span></span>](voice-design.md)
