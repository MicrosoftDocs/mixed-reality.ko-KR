---
title: 핸즈프리
description: 앱을 직접 무료로 최적화
author: liamartinez
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 혼합 현실, 핸 즈 프리, 응시, 응시 대상 지정, 상호 작용, 디자인
ms.openlocfilehash: b2405f5dca19838271363f53ca377c4f90ca1b36
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435079"
---
# <a name="hands-free"></a><span data-ttu-id="db6bd-104">핸즈프리</span><span class="sxs-lookup"><span data-stu-id="db6bd-104">Hands-free</span></span>

## <a name="scenarios"></a><span data-ttu-id="db6bd-105">시나리오</span><span class="sxs-lookup"><span data-stu-id="db6bd-105">Scenarios</span></span>

<span data-ttu-id="db6bd-106">[상호 작용 모델 개요](interaction-fundamentals.md)에 설명 된 대로 사용자와 목표를 식별 한 후에는 작업을 수행 하는 데 직면 하 게 될 수 있는 환경적 또는 상황 과제를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified your users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="db6bd-107">예를 들어 대부분의 사용자는 실제 목표를 달성 하기 위해 자신의 손을 사용 해야 하며,이는 실습 및 컨트롤러 기반 인터페이스와 상호 작용 하는 데 어려움이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-107">For example, many users need to use their hands to accomplish their real-world goals, and they will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="db6bd-108">몇 가지 특정 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-108">Some specific scenarios include:</span></span> 
* <span data-ttu-id="db6bd-109">사용자의 손을 사용 하는 동안 작업을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-109">Being guided through a task, while the user's hands are busy</span></span>
* <span data-ttu-id="db6bd-110">사용자의 손을 사용 하는 동안 자료 참조</span><span class="sxs-lookup"><span data-stu-id="db6bd-110">Referencing materials while the user's hands are busy</span></span>
* <span data-ttu-id="db6bd-111">손 피로</span><span class="sxs-lookup"><span data-stu-id="db6bd-111">Hand fatigue</span></span>
* <span data-ttu-id="db6bd-112">추적할 수 없는 글러브</span><span class="sxs-lookup"><span data-stu-id="db6bd-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="db6bd-113">손으로 운반</span><span class="sxs-lookup"><span data-stu-id="db6bd-113">Carrying something in their hands</span></span>
* <span data-ttu-id="db6bd-114">대량 제스처를 수행 하는 소셜 awkwardness</span><span class="sxs-lookup"><span data-stu-id="db6bd-114">Social awkwardness to perform large hand gestures</span></span>
* <span data-ttu-id="db6bd-115">공간 좁게</span><span class="sxs-lookup"><span data-stu-id="db6bd-115">Tight spaces</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="db6bd-116">핸 즈 프리 소프트웨어나</span><span class="sxs-lookup"><span data-stu-id="db6bd-116">Hands-free modalities</span></span>

### <a name="voice-inputvoice-inputmd"></a>[<span data-ttu-id="db6bd-117">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="db6bd-117">Voice input</span></span>](voice-input.md)

<span data-ttu-id="db6bd-118">음성으로 명령을 사용 하 고 인터페이스를 제어 하면 편리 하 게 사용할 수 있는 편리한 방법을 제공 하 고, 원하는 경우 바로 가기를 사용 하 여 여러 단계를 유연 하 게 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-118">Using your voice to command and control an interface offers a convenient way to operate hands-free and to use shortcuts to flexibly skip multiple steps if desired.</span></span> <span data-ttu-id="db6bd-119">음성 입력을 사용 하면 사용자는 단추의 이름을 소리내어 읽어 활성화 하 여 활성화 하 고 _("표시" 라고 표시)_ , 작업을 수행할 수 있는 디지털 에이전트와 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-119">With voice input, the user can simply read any button's name out loud to activate it _("see it, say it")_ and converse with a digital agent who can accomplish tasks for you.</span></span>


### <a name="gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="db6bd-120">응시 및 유지</span><span class="sxs-lookup"><span data-stu-id="db6bd-120">Gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="db6bd-121">일부 실습 환경에서는 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-121">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="db6bd-122">큰 팩터리 환경, 개인 정보 또는 소셜 표준 모두 제약 조건이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-122">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="db6bd-123">사용자는 응시 + 유지 모델을 사용 하 여 눈 이나 헤드 응시 외에 추가 입력 없이 앱을 탐색할 수 있습니다. 사용자는 단순히 gazing (head 또는 눈동자 포함)를 대상에 유지 하 고 활성화 하는 순간에 lingers 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-123">The gaze + dwell model allows the user to navigate an app without any additional input aside from their eye or head gaze: The user simply keeps gazing (with their head or eyes) at the target and lingers there for a moment to activate it.</span></span> <span data-ttu-id="db6bd-124">응시 + 유지의 개별 디자인 고려 사항에 대 한 자세한 내용은 눈에 보기 [-응시 +](gaze-and-dwell-eyes.md) 유지 및 [헤드-응시 +](gaze-and-dwell-head.md)유지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="db6bd-124">To learn more about the individual design considerations for gaze + dwell, check out [eye-gaze + dwell](gaze-and-dwell-eyes.md) and [head-gaze + dwell](gaze-and-dwell-head.md).</span></span>


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="db6bd-125">직접 전환 및 직접 전환</span><span class="sxs-lookup"><span data-stu-id="db6bd-125">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="db6bd-126">이러한 시나리오의 경우 명령 및 탐색을 위해 holograms와 상호 작용 하는 것은 사용자가 응용 프로그램을 종단 간으로 운영 하는 데 필요한 절대 요구 사항이 아니라 사용자가 어디에서 든 전환할 수 있는지에 대 한 절대적인 요구 사항이 아닙니다. 런타임.</span><span class="sxs-lookup"><span data-stu-id="db6bd-126">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="db6bd-127">응용 프로그램의 요구 사항에 따라, 유지, 사용자 지정 음성 명령 또는 단일 음성 명령을 사용 하 여 언제 든 지 항상 사용이 가능 하다는 것을 확신 하는 경우에는 UI에서 적절 한 적절을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-127">If the requirement of the application is that it will always be used hands-free, whether by using dwell, custom voice commands, or the single voice command, "select", then make sure to make the appropriate accommodations in your UI.</span></span> 

<span data-ttu-id="db6bd-128">대상 사용자가 재량에 따라 직접 전환할 수 있어야 하는 경우 다음 원칙을 고려 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-128">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="db6bd-129">사용자가 전환 하려는 모드에 이미 있는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-129">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="db6bd-130">예를 들어 사용자가 공장 바닥에 있고, 자신의 HoloLens에서 비디오 참조를 감시 하 고, 작업을 시작 하는 렌치를 선택 하기로 결정 하는 경우 단추를 누르기 위해 렌치를 배치 하지 않고도 실습 작업을 시작할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-130">For instance, if the user is on the factory floor, watching a video reference on her HoloLens, and decides to pick up a wrench to start working, she most likely would start working in hands-free without having to put down the wrench to press a button.</span></span> <span data-ttu-id="db6bd-131">Alice는 음성 명령을 사용 하 여 음성 세션을 호출 하 고, 이미 표시 되는 UI를 유지 하 여 유지를 시작 하거나, "select" 라는 단어를 표시할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-131">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="db6bd-132">사용자는 다음을 수행할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-132">The user should have the ability to:</span></span> 
* <span data-ttu-id="db6bd-133">손을 무료로 전환</span><span class="sxs-lookup"><span data-stu-id="db6bd-133">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="db6bd-134">실습으로 전환</span><span class="sxs-lookup"><span data-stu-id="db6bd-134">Switch to hands with your hands</span></span>
* <span data-ttu-id="db6bd-135">컨트롤러를 사용 하 여 컨트롤러로 전환</span><span class="sxs-lookup"><span data-stu-id="db6bd-135">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="db6bd-136">모드를 전환 하는 중복 된 방법 만들기</span><span class="sxs-lookup"><span data-stu-id="db6bd-136">Create redundant ways to switch modes</span></span>
<span data-ttu-id="db6bd-137">첫 번째 원칙은 액세스를 위한 것이 고 두 번째 원칙은 가용성에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-137">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="db6bd-138">모드를 전환 하는 한 가지 방법으로 전환 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-138">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="db6bd-139">몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-139">Some examples would be:</span></span> 
* <span data-ttu-id="db6bd-140">음성 상호 작용을 시작 하는 단추</span><span class="sxs-lookup"><span data-stu-id="db6bd-140">A button to begin voice interactions</span></span>
* <span data-ttu-id="db6bd-141">헤드-응시 및 유지를 사용 하 여로 전환할 음성 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-141">A voice command to transition to, using head-gaze and dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="db6bd-142">드라마의 대시 추가</span><span class="sxs-lookup"><span data-stu-id="db6bd-142">Add a dash of drama</span></span>
<span data-ttu-id="db6bd-143">모드 스위치는 큰 문제입니다. 이러한 전환이 발생 하는 경우 사용자에 게 발생 한 상황을 알 수 있도록 명시적인 스위치를 사용 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-143">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even a dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="db6bd-144">유용성 검사 목록</span><span class="sxs-lookup"><span data-stu-id="db6bd-144">Usability checklist</span></span>

<span data-ttu-id="db6bd-145">**사용자는 모든 작업을 수행할 수 있으며, 종단 간 모든 작업은 가능 합니다.**</span><span class="sxs-lookup"><span data-stu-id="db6bd-145">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="db6bd-146">모든 interactable은 직접 액세스 가능 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-146">Every interactable should be accessible hands-free</span></span>
* <span data-ttu-id="db6bd-147">크기 조정, 배치, swipes, 탭 등의 모든 사용자 지정 제스처를 대체 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-147">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="db6bd-148">사용자가 UI의 현재 상태, 배치 및 자세한 정도를 항상 제어할 권한이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-148">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="db6bd-149">UI를 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="db6bd-149">Getting UI out of the way</span></span>
    * <span data-ttu-id="db6bd-150">뷰에서 벗어난 UI 주소 지정 (FOV)</span><span class="sxs-lookup"><span data-stu-id="db6bd-150">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="db6bd-151">표시 되는 크기, 위치, 시기</span><span class="sxs-lookup"><span data-stu-id="db6bd-151">How much I see, where, when</span></span>

<span data-ttu-id="db6bd-152">**올바른 affordances를 사용 하 여 상호 작용 하는 작업의 메커니즘은 무엇 인가요?**</span><span class="sxs-lookup"><span data-stu-id="db6bd-152">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="db6bd-153">사용자의 이해</span><span class="sxs-lookup"><span data-stu-id="db6bd-153">Does the user understand ...</span></span>
* <span data-ttu-id="db6bd-154">... 있는 모드</span><span class="sxs-lookup"><span data-stu-id="db6bd-154">... What mode they are in?</span></span>
* <span data-ttu-id="db6bd-155">... 이 모드에서 수행할 수 있는 작업은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="db6bd-155">... What they can do in this mode?</span></span>
* <span data-ttu-id="db6bd-156">... 현재 상태는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="db6bd-156">... What is the current state?</span></span>
* <span data-ttu-id="db6bd-157">... 어떻게 전환할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="db6bd-157">... How they can transition out?</span></span>
    
<span data-ttu-id="db6bd-158">**UI가 손을 무료로 최적화 되었습니까?**</span><span class="sxs-lookup"><span data-stu-id="db6bd-158">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="db6bd-159">예: 유지 affordances 일반적인 2D 패턴에 기본 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-159">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="db6bd-160">예: 개체 강조 표시로 음성 대상 지정이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-160">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="db6bd-161">예: 설정 해야 하는 캡션에 음성 상호 작용이 더 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="db6bd-161">Example: Voice interactions are better with captions that need to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="db6bd-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db6bd-162">See also</span></span>
* [<span data-ttu-id="db6bd-163">HoloLens의 눈동자 추적 2</span><span class="sxs-lookup"><span data-stu-id="db6bd-163">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="db6bd-164">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="db6bd-164">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="db6bd-165">응시 및 유지</span><span class="sxs-lookup"><span data-stu-id="db6bd-165">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="db6bd-166">직접 조작</span><span class="sxs-lookup"><span data-stu-id="db6bd-166">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="db6bd-167">손 제스처</span><span class="sxs-lookup"><span data-stu-id="db6bd-167">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="db6bd-168">손 지점 및 커밋</span><span class="sxs-lookup"><span data-stu-id="db6bd-168">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="db6bd-169">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="db6bd-169">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="db6bd-170">음성 입력 </span><span class="sxs-lookup"><span data-stu-id="db6bd-170">Voice input</span></span>](voice-input.md)
