---
title: 핸즈프리
description: 앱을 직접 무료로 최적화
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 혼합 현실, 핸 즈 프리, 응시, 응시 대상 지정, 상호 작용, 디자인
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414390"
---
# <a name="hands-free"></a><span data-ttu-id="2f013-104">핸즈프리</span><span class="sxs-lookup"><span data-stu-id="2f013-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="2f013-105">시나리오</span><span class="sxs-lookup"><span data-stu-id="2f013-105">Scenarios</span></span>

<span data-ttu-id="2f013-106">[상호 작용 모델 개요](interaction-fundamentals.md)에 설명 된 대로 사용자와 해당 목표를 식별 한 후에는 작업을 수행 하는 데 직면 하 게 될 수 있는 환경적 또는 상황 과제를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="2f013-107">예를 들어 많은 사용자가 실제 목표를 달성 하는 데 자신의 손을 사용 해야 하며, 직접 및 컨트롤러 기반 인터페이스와 상호 작용 하는 데 어려움이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="2f013-108">몇 가지 특정 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="2f013-109">작업을 안내 하는 반면, 실습은 사용 중입니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="2f013-110">실습을 사용 하는 동안 자료 참조</span><span class="sxs-lookup"><span data-stu-id="2f013-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="2f013-111">손 피로</span><span class="sxs-lookup"><span data-stu-id="2f013-111">Hand fatigue</span></span>
* <span data-ttu-id="2f013-112">추적할 수 없는 글러브</span><span class="sxs-lookup"><span data-stu-id="2f013-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="2f013-113">항목 운반</span><span class="sxs-lookup"><span data-stu-id="2f013-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="2f013-114">핸 즈 프리 소프트웨어나</span><span class="sxs-lookup"><span data-stu-id="2f013-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="2f013-115">음성 명령</span><span class="sxs-lookup"><span data-stu-id="2f013-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="2f013-116">음성 명령과 인터페이스를 함께 사용 하면 사용자가 handsfree 작동할 수 있을 뿐만 아니라 여러 단계를 건너뛸 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="2f013-117">이 모달을 사용 하면 사용자가 작업을 수행할 수 있는 에이전트와 대화 하는 것 처럼 사용자가 단추의 이름을 소리내어 읽도록 하 여 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="2f013-118">헤드 게이즈 및 유지</span><span class="sxs-lookup"><span data-stu-id="2f013-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="2f013-119">일부 실습 환경에서는 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="2f013-120">큰 팩터리 환경, 개인 정보 또는 소셜 표준 모두 제약 조건이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="2f013-121">헤드 응시 + 유지 모델을 사용 하면 사용자는 헤드 벡터를 사용 하 여 응용 프로그램을 탐색할 수 있습니다. 반면에, 느린 또는 dwelling는 특정 시간 (일반적으로 약 1 초 정도) 후에 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, typically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="2f013-122">직접 전환 및 직접 전환</span><span class="sxs-lookup"><span data-stu-id="2f013-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="2f013-123">이러한 시나리오의 경우 명령 및 탐색을 위해 holograms와 상호 작용 하는 것은 사용자가 응용 프로그램을 종단 간으로 운영 하는 데 필요한 절대 요구 사항이 아니라 사용자가 어디에서 든 전환할 수 있는지에 대 한 절대적인 요구 사항이 아닙니다. 런타임.</span><span class="sxs-lookup"><span data-stu-id="2f013-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="2f013-124">응용 프로그램의 요구 사항에 따라, 유지, 음성 명령 또는 단일 음성 명령을 사용 하 여 언제 든 지 항상 사용이 가능 하다는 것을 확신 하는 경우에는 UI에서 적절 한 accomodations을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="2f013-125">대상 사용자가 재량에 따라 직접 전환할 수 있어야 하는 경우 다음 원칙을 고려 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="2f013-126">사용자가 전환 하려는 모드에 이미 있는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="2f013-127">예를 들어 사용자가 공장 바닥에 있고, 자신의 Hololens에서 비디오 참조를 감시 하 고, 작업을 시작 하는 렌치를 선택 하기로 결정 한 경우 단추를 누르기 위해 렌치를 배치 하지 않고도 handsfree에서 작업을 시작할 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="2f013-128">Alice는 음성 명령을 사용 하 여 음성 세션을 호출 하 고, 이미 표시 되는 UI를 유지 하 여 유지를 시작 하거나, "select" 라는 단어를 표시할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="2f013-129">사용자는 다음을 수행할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="2f013-130">손을 무료로 전환</span><span class="sxs-lookup"><span data-stu-id="2f013-130">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="2f013-131">실습으로 전환</span><span class="sxs-lookup"><span data-stu-id="2f013-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="2f013-132">컨트롤러를 사용 하 여 컨트롤러로 전환</span><span class="sxs-lookup"><span data-stu-id="2f013-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="2f013-133">모드를 전환 하는 중복 된 방법 만들기</span><span class="sxs-lookup"><span data-stu-id="2f013-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="2f013-134">첫 번째 원칙은 액세스를 위한 것이 고 두 번째 원칙은 가용성에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="2f013-135">모드를 전환 하는 한 가지 방법으로 전환 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="2f013-136">몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-136">Some examples would be:</span></span> 
* <span data-ttu-id="2f013-137">음성 상호 작용을 시작 하는 단추</span><span class="sxs-lookup"><span data-stu-id="2f013-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="2f013-138">응시 + 유지를 사용 하도록 전환 하는 음성 명령</span><span class="sxs-lookup"><span data-stu-id="2f013-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="2f013-139">드라마의 대시 추가</span><span class="sxs-lookup"><span data-stu-id="2f013-139">Add a dash of drama</span></span>
<span data-ttu-id="2f013-140">모드 스위치는 큰 문제입니다. 이러한 전환이 발생 하는 경우 사용자에 게 발생 한 상황을 알 수 있도록 명시적인 스위치를 사용 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="2f013-141">유용성 검사 목록</span><span class="sxs-lookup"><span data-stu-id="2f013-141">Usability checklist</span></span>

<span data-ttu-id="2f013-142">**사용자는 모든 작업을 수행할 수 있으며, 종단 간 모든 작업은 가능 합니다.**</span><span class="sxs-lookup"><span data-stu-id="2f013-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="2f013-143">모든 interactible은 직접 액세스 가능 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="2f013-144">크기 조정, 배치, swipes, 탭 등의 모든 사용자 지정 제스처를 대체 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="2f013-145">사용자가 UI의 현재 상태, 배치 및 자세한 정도를 항상 제어할 권한이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="2f013-146">UI를 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="2f013-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="2f013-147">뷰에서 벗어난 UI 주소 지정 (FOV)</span><span class="sxs-lookup"><span data-stu-id="2f013-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="2f013-148">표시 되는 크기, 위치, 시기</span><span class="sxs-lookup"><span data-stu-id="2f013-148">How much I see, where, when</span></span>

<span data-ttu-id="2f013-149">**올바른 affordances를 사용 하 여 상호 작용 하는 작업의 메커니즘은 무엇 인가요?**</span><span class="sxs-lookup"><span data-stu-id="2f013-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="2f013-150">사용자의 이해</span><span class="sxs-lookup"><span data-stu-id="2f013-150">Does the user understand ...</span></span>
* <span data-ttu-id="2f013-151">... 있는 모드</span><span class="sxs-lookup"><span data-stu-id="2f013-151">... What mode they are in?</span></span>
* <span data-ttu-id="2f013-152">... 이 모드에서 수행할 수 있는 작업은 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="2f013-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="2f013-153">... 현재 상태는 무엇 인가요?</span><span class="sxs-lookup"><span data-stu-id="2f013-153">... What is the current state?</span></span>
* <span data-ttu-id="2f013-154">... 어떻게 전환할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="2f013-154">... How they can transition out?</span></span>
    
<span data-ttu-id="2f013-155">**UI가 손을 무료로 최적화 되었습니까?**</span><span class="sxs-lookup"><span data-stu-id="2f013-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="2f013-156">예: 지속 affordances 일반적인 2D 패턴에 기본 제공 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="2f013-157">예: 개체 강조 표시에서 음성 대상 지정이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="2f013-158">예: 설정 해야 하는 캡션에 음성 상호 작용이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2f013-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="2f013-159">참조</span><span class="sxs-lookup"><span data-stu-id="2f013-159">See also</span></span>
* [<span data-ttu-id="2f013-160">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="2f013-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="2f013-161">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="2f013-161">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="2f013-162">수동으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="2f013-162">Point and commit with hands</span></span>](point-and-commit.md)
