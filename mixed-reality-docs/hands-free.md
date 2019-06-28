---
title: 핸즈프리
description: 핸 즈 프리에 대 한 앱 최적화
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: 핸 즈 프리, gaze, 대상, 상호 작용 디자인 gaze 혼합 현실
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414390"
---
# <a name="hands-free"></a><span data-ttu-id="8791b-104">핸즈프리</span><span class="sxs-lookup"><span data-stu-id="8791b-104">Hands-free</span></span>



## <a name="scenarios"></a><span data-ttu-id="8791b-105">시나리오</span><span class="sxs-lookup"><span data-stu-id="8791b-105">Scenarios</span></span>

<span data-ttu-id="8791b-106">에 설명 된 대로 합니다 [상호 작용 모델 개요](interaction-fundamentals.md)식별 하 고 나면 사용자 및 사용자 목표, 자신에 게 해당 작업을 수행 하려면 작업 하면서 발생할 환경 또는 상황에 따른 문제를 질문 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-106">As outlined in the [Interaction model overview](interaction-fundamentals.md), once you have identified the users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="8791b-107">많은 사용자가 해당 실제 목표를 달성 하 알아내기란을 사용 해야 하는 예를 들어, 실습 및 컨트롤러 기반된 인터페이스와 상호 작용 하는 데 어려움을 겪 및 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-107">For example, many users need to use their hands to accomplish their real-world goals, and will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="8791b-108">일부 특정 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-108">Some specific scenarios might be:</span></span> 
* <span data-ttu-id="8791b-109">사용 중인 동안 작업을 안내 되 고</span><span class="sxs-lookup"><span data-stu-id="8791b-109">Being guided through a task, while hands are busy</span></span>
* <span data-ttu-id="8791b-110">사용 중인는 손이 자료를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-110">Referencing materials while your hands are busy</span></span>
* <span data-ttu-id="8791b-111">직접 피로</span><span class="sxs-lookup"><span data-stu-id="8791b-111">Hand fatigue</span></span>
* <span data-ttu-id="8791b-112">Gloves 추적할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="8791b-113">작업 수행</span><span class="sxs-lookup"><span data-stu-id="8791b-113">Carrying something</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="8791b-114">핸 즈 프리 형식</span><span class="sxs-lookup"><span data-stu-id="8791b-114">Hands-free modalities</span></span>

### <a name="voice-commandingvoice-designmd"></a>[<span data-ttu-id="8791b-115">음성 명령</span><span class="sxs-lookup"><span data-stu-id="8791b-115">Voice commanding</span></span>](voice-design.md)

<span data-ttu-id="8791b-116">사용자 handsfree, 작동 하지만 또한 여러 단계를 건너뛸 수 있도록 뿐 아니라 명령 및 컨트롤 인터페이스 수에 음성을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-116">Using your voice to command and control an interface can not only allow the user to operate handsfree, but also skip multiple steps.</span></span> <span data-ttu-id="8791b-117">이 형식 사용 모든 단추의 이름을 참조-it-예를 들어-it와 같이 수에 대 한 작업을 수행할 수 있는 에이전트를 사용 하 여 대화에 활성화를 소리내어 읽을 수 있도록에서 까지입니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-117">The usage of this modality can range from allowing the user to simply read any button's name out loud to activate it, as in See-it-say-it, to conversing with an agent who can accomplish tasks for you.</span></span>



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[<span data-ttu-id="8791b-118">헤드 게이즈 및 유지</span><span class="sxs-lookup"><span data-stu-id="8791b-118">Head-gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="8791b-119">핸 즈 프리 경우도 음성을 사용 하 여 없는 이상적인 또는 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-119">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="8791b-120">큰 팩터리 환경, 개인 정보 보호 또는 소셜 표준 모든 제약 조건을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-120">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="8791b-121">헤드 gaze + 자세히 다루지는 모델 가리키도록, 느린을 하는 동안 해당 헤드 벡터를 사용 하 여 앱을 이동할 수 있도록 하거나 생각 단추에 잠기거나 그럴를 활성화 합니다. 특정 시간 후 시간, 일반적으로 약 1 초 정도입니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-121">The head gaze + dwell model allows the user to navigate the app by using their head vector to point, while lingering, or dwelling on a button will activate it after a certain amount of time, typically around 1 second or so.</span></span> 


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="8791b-122">핸 즈 프리 내부 및 외부로 전환</span><span class="sxs-lookup"><span data-stu-id="8791b-122">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="8791b-123">이러한 시나리오에 대 한 응용 프로그램에 종단 간 사용자와의 모든 전환 편의를 운영 하는 절대 요구 사항을 없도록 범위 수 홀로그램 명령 및 탐색에 대 한 상호 작용 하지는 손이 해제 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-123">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="8791b-124">응용 프로그램의 요구 사항을 유지, 음성 명령, 또는 단일 음성 명령을 사용 하 여 여부를 항상 사용 되도록 핸 즈 프리가, "select" 경우 UI에 적절 한 객실을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-124">If the requirement of the application is that it will always be used hands-free, whether by using dwell, voice commands, or the single voice command, "select", then make sure to make the appropriate accomodations in your UI.</span></span> 

<span data-ttu-id="8791b-125">대상 사용자를 재량에 핸 즈 프리를 손에서 전환할 수 해야 하는 경우 다음 반드시 다음 원칙을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-125">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="8791b-126">사용자가 이미 전환 하고자 하는 모드를 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-126">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="8791b-127">예를 들어 사용자 공장 현장에서 자신의 Hololens에 참조를 비디오를 시청 고 작업을 시작 하는 렌치 선택 하기로 결정 하는 경우 자신이 가능성이 것에서 작업을 시작 handsfree는 단추를 눌러 렌치 작성 하지 않고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-127">For instance, if the user is on the factory floor, watching a video reference on her Hololens, and decides to pick up a wrench to start working, she most likely would start working in handsfree without having to put down the wrench to press a button.</span></span> <span data-ttu-id="8791b-128">예를 들어는 "선택" 또는 자신이 호출 음성 명령 사용 하 여 음성 세션 지속을 시작 하는 이미 표시 되는 UI에 자세히 설명 하지을 수 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-128">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="8791b-129">사용자 수가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-129">The user should have the ability to:</span></span> 
* <span data-ttu-id="8791b-130">핸 즈 프리 하지만 핸 즈 프리로 전환</span><span class="sxs-lookup"><span data-stu-id="8791b-130">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="8791b-131">손으로 바늘으로 전환</span><span class="sxs-lookup"><span data-stu-id="8791b-131">Switch to hands with your hands</span></span>
* <span data-ttu-id="8791b-132">컨트롤러를 사용 하는 컨트롤러 전환</span><span class="sxs-lookup"><span data-stu-id="8791b-132">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="8791b-133">만들기 모드를 전환 하는 중복 방법</span><span class="sxs-lookup"><span data-stu-id="8791b-133">Create redundant ways to switch modes</span></span>
<span data-ttu-id="8791b-134">액세스에 대 한 첫 번째 원칙은 상태인 동안 가용성에 대 한 두 번째는 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-134">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="8791b-135">해야만 있어야 모드 내부 및 외부로 전환 하는 한 가지 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-135">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="8791b-136">몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-136">Some examples would be:</span></span> 
* <span data-ttu-id="8791b-137">음성 상호 작용을 시작 하는 단추</span><span class="sxs-lookup"><span data-stu-id="8791b-137">A button to begin voice interactions</span></span>
* <span data-ttu-id="8791b-138">응시 + 유지를 사용 하 여 음성 명령을 전환</span><span class="sxs-lookup"><span data-stu-id="8791b-138">A voice command to transition to using gaze + dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="8791b-139">드라마의 대시를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-139">Add a dash of drama</span></span>
<span data-ttu-id="8791b-140">모드 스위치는 정말로-것이 수 하는 이러한 전환을 수행 하는 경우는 명시적도 크게 스위치의 경우 사용자에 게 알리는 내용에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-140">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="8791b-141">가용성 검사 목록</span><span class="sxs-lookup"><span data-stu-id="8791b-141">Usability checklist</span></span>

<span data-ttu-id="8791b-142">**사용자가 모든 및 핸 즈 프리, 종단 간 작업 수행할 수 있습니다?**</span><span class="sxs-lookup"><span data-stu-id="8791b-142">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="8791b-143">모든 interactible 액세스할 수 있어야 핸 즈 프리</span><span class="sxs-lookup"><span data-stu-id="8791b-143">Every interactible should be accessible hands-free</span></span>
* <span data-ttu-id="8791b-144">크기 조정, 배치, 천공 기와, 탭 등과 같은 모든 사용자 지정 제스처에 대 한 대체 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-144">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="8791b-145">항상 사용자 UI 현재 상태, 배치 및 자세한 정도 확신할 제어에 있는지 확인</span><span class="sxs-lookup"><span data-stu-id="8791b-145">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="8791b-146">방해가 ui</span><span class="sxs-lookup"><span data-stu-id="8791b-146">Getting UI out of the way</span></span>
    * <span data-ttu-id="8791b-147">필드의 보기 (FOV) 되는 UI를 주소 지정</span><span class="sxs-lookup"><span data-stu-id="8791b-147">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="8791b-148">표시 크기, 위치 때</span><span class="sxs-lookup"><span data-stu-id="8791b-148">How much I see, where, when</span></span>

<span data-ttu-id="8791b-149">**상호 작용에 대 한 메커니즘 제공 되 고 오른쪽 affordances를 사용 하 여 보강?**</span><span class="sxs-lookup"><span data-stu-id="8791b-149">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="8791b-150">사용자가 인식 하는 중...</span><span class="sxs-lookup"><span data-stu-id="8791b-150">Does the user understand ...</span></span>
* <span data-ttu-id="8791b-151">... 모드에 있기?</span><span class="sxs-lookup"><span data-stu-id="8791b-151">... What mode they are in?</span></span>
* <span data-ttu-id="8791b-152">... 수행할 수 있는이 모드에서?</span><span class="sxs-lookup"><span data-stu-id="8791b-152">... What they can do in this mode?</span></span>
* <span data-ttu-id="8791b-153">... 현재 상태는 무엇입니까?</span><span class="sxs-lookup"><span data-stu-id="8791b-153">... What is the current state?</span></span>
* <span data-ttu-id="8791b-154">... 전환 수 방식?</span><span class="sxs-lookup"><span data-stu-id="8791b-154">... How they can transition out?</span></span>
    
<span data-ttu-id="8791b-155">**UI에 최적화 된 핸 즈 프리?**</span><span class="sxs-lookup"><span data-stu-id="8791b-155">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="8791b-156">예: 지속 affordances 일반적인 2D 패턴에 기본 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8791b-156">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="8791b-157">예: 음성 대상으로 하는 것이 좋습니다 개체 강조</span><span class="sxs-lookup"><span data-stu-id="8791b-157">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="8791b-158">예: 음성 상호 작용 켜져 있는 캡션이 있는 좋음</span><span class="sxs-lookup"><span data-stu-id="8791b-158">Example: Voice interactions are better with captions that have to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="8791b-159">참조</span><span class="sxs-lookup"><span data-stu-id="8791b-159">See also</span></span>
* [<span data-ttu-id="8791b-160">헤드 게이즈 및 커밋</span><span class="sxs-lookup"><span data-stu-id="8791b-160">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="8791b-161">수동으로 직접 조작</span><span class="sxs-lookup"><span data-stu-id="8791b-161">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8791b-162">수동으로 가리키고 커밋</span><span class="sxs-lookup"><span data-stu-id="8791b-162">Point and commit with hands</span></span>](point-and-commit.md)
