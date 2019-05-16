---
title: 음성 명령 실행
description: 응시, 제스처 및 음성 (GGV)은 기본 HoloLens에서 상호 작용 합니다. 이 문서에서는 음성 디자인 상세한 지침을 제공합니다.
author: shentan
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality를 디자인, 상호 작용, 음성
ms.openlocfilehash: 49fa199b2656db95b15583ccfbee39f33942f180
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730795"
---
# <a name="voice-commanding"></a><span data-ttu-id="e0396-105">음성 명령 실행</span><span class="sxs-lookup"><span data-stu-id="e0396-105">Voice commanding</span></span>

<span data-ttu-id="e0396-106">음성 명령을 사용 하는 경우 게이즈는 일반적으로 대상 mechaninism,으로 여부를 포인터로 사용 ("select") 또는 응용 프로그램에 명령을 보내기 위해 ("표시, 말").</span><span class="sxs-lookup"><span data-stu-id="e0396-106">When using voice commands, gaze is typically used as the targeting mechaninism, whether as a pointer ("select") or to direct your command to an application ("see it, say it").</span></span> <span data-ttu-id="e0396-107">물론, 일부 음성 명령을 "시작"또는 "Hey, Cortana."와 같은 전혀 대상 필요가</span><span class="sxs-lookup"><span data-stu-id="e0396-107">Of course, some voice commands don't require a target at all, like "go to start" or "Hey, Cortana."</span></span>


## <a name="device-support"></a><span data-ttu-id="e0396-108">장치 지원</span><span class="sxs-lookup"><span data-stu-id="e0396-108">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e0396-109">기능</span><span class="sxs-lookup"><span data-stu-id="e0396-109">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="e0396-110"><a href="hololens-hardware-details.md">HoloLens (첫 번째 범용)</a></span><span class="sxs-lookup"><span data-stu-id="e0396-110"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="e0396-111">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="e0396-111">HoloLens 2</span></span></th><th style="width:150px"> <span data-ttu-id="e0396-112"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="e0396-112"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td></td><td style="text-align: center;"> <span data-ttu-id="e0396-113">✔️</span><span class="sxs-lookup"><span data-stu-id="e0396-113">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e0396-114">✔️</span><span class="sxs-lookup"><span data-stu-id="e0396-114">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e0396-115">(사용 하 여 연결 된 헤드셋) ✔️</span><span class="sxs-lookup"><span data-stu-id="e0396-115">✔️ (with headset attached)</span></span></td>
</tr>
</table>



## <a name="how-to-use-voice"></a><span data-ttu-id="e0396-116">음성을 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="e0396-116">How to use voice</span></span>

<span data-ttu-id="e0396-117">음성 명령을 작성 하는 모든 환경에 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-117">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="e0396-118">음성은 강력 하 고 편리한 방식으로 제어할 시스템 및 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-118">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="e0396-119">사용자가 다양 한 언어 및 악센트를 사용 하기 때문에 음성 키워드의 적절 한 선택 게 사용자의 명령을 명확 하 게 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-119">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="e0396-120">모범 사례</span><span class="sxs-lookup"><span data-stu-id="e0396-120">Best practices</span></span>

<span data-ttu-id="e0396-121">아래는 부드러운 음성 인식에 도움이 될 수 있는 몇 가지 사례가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-121">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="e0396-122">**간단한 명령을 사용 하 여** -가능 하면 두 개 이상의 음절 키워드를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-122">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="e0396-123">1 음절로 단어 다른 음 다른 악센트 사람이 말할 때 사용 하는 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-123">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="e0396-124">예: "현재 선택 된 비디오 재생" 보다는 "비디오 재생"</span><span class="sxs-lookup"><span data-stu-id="e0396-124">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="e0396-125">**간단한 어휘를 사용 하 여** -예제: "Show 카드" 보다는 "참고 보여 줍니다."</span><span class="sxs-lookup"><span data-stu-id="e0396-125">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="e0396-126">**명령이 아닌 삭제 되는지 확인** -음성 명령으로 수행할 수 있는 모든 작업은 비 삭제 되었는지 확인 하 고 쉽게 실행 취소할 수 있습니다 다른 사람이 실수로 사용자 근처 말하기 명령을 트리거하는 경우.</span><span class="sxs-lookup"><span data-stu-id="e0396-126">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="e0396-127">**유사한 발음이 명령을 방지** -매우 비슷하게 들리는 여러 음성 명령을 등록 되지 않게 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-127">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="e0396-128">예: "자세히 보기" 및 "Show store"와 매우 유사 발음이 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-128">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="e0396-129">**사용 하지 않는 경우 앱을 등록 취소** 앱 특정 음성 명령을 잘못의 상태에 없는 경우-다른 명령을 하나에 대 한 혼동 하지 되어 있도록 등록을 취소 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-129">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="e0396-130">**테스트와 다른** -다른 악센트의 사용자와 앱을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-130">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="e0396-131">**음성 명령 일관성을 유지** -이전 페이지에서 "돌아가서" 이동 하는 경우 응용 프로그램에서이 동작을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-131">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="e0396-132">**시스템 명령을 사용 하 여 방지** -시스템에 대 한 음성 명령을 예약 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-132">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="e0396-133">이러한 응용 프로그램에서 사용할 수 없습니다 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-133">These should not be used by applications.</span></span>
   * <span data-ttu-id="e0396-134">"Hey Cortana"</span><span class="sxs-lookup"><span data-stu-id="e0396-134">"Hey Cortana"</span></span>
   * <span data-ttu-id="e0396-135">[선택]</span><span class="sxs-lookup"><span data-stu-id="e0396-135">"Select"</span></span>

### <a name="select"></a><span data-ttu-id="e0396-136">[선택]</span><span class="sxs-lookup"><span data-stu-id="e0396-136">"Select"</span></span>

<span data-ttu-id="e0396-137">언제 든 지 "select" 라는 게이즈 커서가 가리키는 무엇이 든 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-137">Saying "select" at any time will activate whatever the gaze cursor is pointing at.</span></span> 

><span data-ttu-id="e0396-138">참고: HoloLens 2에서는 먼저 호출할 수는 마디 게이즈 커서 요구 사항 "select"입니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-138">Note: In HoloLens 2, the gaze cursor needs to first be invoked by saying the word "select".</span></span> <span data-ttu-id="e0396-139">예를 들어, "" 다시 활성화 하려면 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-139">Say, "select" again to activate.</span></span> <span data-ttu-id="e0396-140">응시 커서를 숨기려면 손으로-airtap 또는 개체를 터치 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-140">To hide the gaze cursor, simply use your hands -- airtap or touch an object.</span></span> 

### <a name="see-it-say-it"></a><span data-ttu-id="e0396-141">표시, 말</span><span class="sxs-lookup"><span data-stu-id="e0396-141">See it, say it</span></span>

<span data-ttu-id="e0396-142">Windows Mixed Reality "표시, 말" 음성 모델을 채택 했습니다 위치 **단추에서 레이블이 연결된 음성 명령에 동일**합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-142">Windows Mixed Reality has employed a "see it, say it" voice model where **labels on buttons are identical to the associated voice commands**.</span></span> <span data-ttu-id="e0396-143">레이블 및 음성 명령 간에 모든 dissonance 없는, 때문에 사용자가 더 잘 이해 하기 시스템을 제어 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-143">Because there isn’t any dissonance between the label and the voice command, users can better understand what to say to control the system.</span></span> <span data-ttu-id="e0396-144">생각을 단추에 잠기거나 그럴 하는 동안이 강화 하는 **"음성은 tip를 유지 하는 데 사용"** 단추는 사용 하도록 설정 하는 음성 통신에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-144">To reinforce this, while dwelling on a button, a **"voice dwell tip"** appears to communicate which buttons are voice enabled.</span></span>


![예제 1 말 표시](images/voice-seeitsayit1-640px.jpg)

<span data-ttu-id="e0396-146">![예제 2 말 표시](images/voice-seeitsayit2-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e0396-146">![See it say it example 2](images/voice-seeitsayit2-640px.jpg)</span></span><br>
<span data-ttu-id="e0396-147">*예의 "표시, 말"*</span><span class="sxs-lookup"><span data-stu-id="e0396-147">*Examples of "see it, say it"*</span></span>

### <a name="voices-strengths"></a><span data-ttu-id="e0396-148">음성의 장점</span><span class="sxs-lookup"><span data-stu-id="e0396-148">Voice's strengths</span></span>

<span data-ttu-id="e0396-149">음성 입력이이 의도 통신 하는 자연 스러운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-149">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="e0396-150">음성 인터페이스에서 특히 유용 **순회** 사용자 (사용자 한다고 여 "이동" 다시 확인 하는 동안 웹 페이지에서 설정 및 앱에서 뒤로 단추를 누르면 이동 하는 대신) 인터페이스의 여러 단계를 잘라낼 수 있으므로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-150">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at Web page, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="e0396-151">이 작은 시간 절약에는 강력한 **감정적인 효과** 사용자 환경의 인식 하며 약간 최강의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-151">This small time savings has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="e0396-152">음성을 사용 하 여 입력된 하는 편리한 방법을 때 이기도 중이거나 전체는 무기 했습니다 **멀티태스킹**합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-152">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="e0396-153">키보드에서 입력이 어렵고, 장치의 **받아쓰기 음성** 를 입력 하는 효율적인 대체 방법일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-153">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input.</span></span> <span data-ttu-id="e0396-154">마지막으로 일부의 경우이 시기는 **다양 한 정확도** 입력 메서드를 신뢰할 수 있는 게이즈 및 제스처를 제한에 대 한 음성 사용자의 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-154">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, Voice might be a user’s only trusted method input.</span></span>

<span data-ttu-id="e0396-155">**어떻게 음성을 사용 하 여 이점을 얻을 수는 사용자**</span><span class="sxs-lookup"><span data-stu-id="e0396-155">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="e0396-156">-시간을 단축 만들어야 최종 목표를 더 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-156">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="e0396-157">-노력을 최소화 더 유동적이 되며 간편 하 게 작업을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-157">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="e0396-158">-Cognitive 부하를 줄일 것이 직관적이 고 쉽게 배우고 기억 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-158">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="e0396-159">사회 적합-사회적 표준 동작 측면에서 적합 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-159">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="e0396-160">-루틴의 음성 habitual 동작을 쉽게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-160">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="voices-weaknesses"></a><span data-ttu-id="e0396-161">음성의 단점</span><span class="sxs-lookup"><span data-stu-id="e0396-161">Voice's weaknesses</span></span>

<span data-ttu-id="e0396-162">음성 몇 가지 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-162">Voice also has some weaknesses.</span></span> <span data-ttu-id="e0396-163">세분화 된 컨트롤은 그 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-163">Fine-grained control is one of them.</span></span> <span data-ttu-id="e0396-164">(예를 들어 사용자 "크게" 말할 수도 있지만 얼마나 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-164">(for example a user might say "louder," but can’t say how much.</span></span> <span data-ttu-id="e0396-165">"약간" 어렵습니다 수량화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-165">"A little" is hard to quantify.</span></span> <span data-ttu-id="e0396-166">이동 또는 음성으로 작업 크기 조정도 어렵습니다 (음성 제어의 세분성을 제공 하지 않습니다).</span><span class="sxs-lookup"><span data-stu-id="e0396-166">Moving or scaling things with voice is also difficult (voice does not offer the granularity of control).</span></span> <span data-ttu-id="e0396-167">음성 해제할 수도 있습니다 완벽 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-167">Voice can also be imperfect.</span></span> <span data-ttu-id="e0396-168">경우에 따라 음성 시스템을 잘못 명령을 시도해볼 또는 실패 명령 들을 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-168">Sometimes a voice system incorrectly hears a command or fails to hear a command.</span></span> <span data-ttu-id="e0396-169">이러한 오류에서 복구는 모든 인터페이스에는 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-169">Recovering from such errors is a challenge in any interface.</span></span> <span data-ttu-id="e0396-170">마지막으로, 음성 아닐 사회 공공 장소입니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-170">Lastly, voice may not be socially acceptable in public places.</span></span> <span data-ttu-id="e0396-171">사용자가 없거나 가정해 하지 않아야 하는 몇 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-171">There are some things that users can’t or shouldn’t say.</span></span> <span data-ttu-id="e0396-172">이러한 절벽 음성 것에서 가장에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-172">These cliffs allow speech to be used for what it is best at.</span></span>

### <a name="voice-feedback-states"></a><span data-ttu-id="e0396-173">음성 피드백 상태</span><span class="sxs-lookup"><span data-stu-id="e0396-173">Voice feedback states</span></span>

<span data-ttu-id="e0396-174">음성 제대로 적용 될 때 사용자에 대 한 이해 **어떤 수 가정해 하며 명확한 피드백을 받을** 시스템 **그렇습니다 하**합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-174">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="e0396-175">이러한 두 신호 느끼지 음성 기본 입력으로 사용 하 여 사용자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-175">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="e0396-176">항목을 보여 주는 다이어그램은 음성 입력을 인식 하는 경우 커서와 통신 하는 사용자에 게 수행 되는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-176">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>

<span data-ttu-id="e0396-177">![커서에 대 한 음성 피드백 상태](images/voicefeedbackstates.png)</span><span class="sxs-lookup"><span data-stu-id="e0396-177">![Voice feedback states for cursor](images/voicefeedbackstates.png)</span></span><br>
<span data-ttu-id="e0396-178">*커서에 대 한 음성 피드백 상태*</span><span class="sxs-lookup"><span data-stu-id="e0396-178">*Voice feedback states for cursor*</span></span>

## <a name="top-things-users-should-know-about-speech-on-windows-mixed-reality"></a><span data-ttu-id="e0396-179">사용자가 가장 중요 한 가지 "speech" Windows Mixed Reality를 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-179">Top things users should know about "speech" on Windows Mixed Reality</span></span>
* <span data-ttu-id="e0396-180">예를 들어 **"Select"** (사용할 수 있습니다이 어디서 나 단추를 클릭) 단추를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-180">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="e0396-181">말할 수는 **앱 모음 단추의 레이블 이름** 작업을 수행 하는 일부 앱에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-181">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="e0396-182">예를 들어, 앱을 보고 하는 동안 사용자 수 명령을 말합니다 "제거" 전 세계에서 앱을 제거 하려면 (손으로 클릭 하지 않아도이 저장 시간).</span><span class="sxs-lookup"><span data-stu-id="e0396-182">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="e0396-183">Cortana 하면 수신 대기를 시작할 수 있습니다 **"Hey Cortana"입니다.**</span><span class="sxs-lookup"><span data-stu-id="e0396-183">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="e0396-184">자신의 질문 ("Hey Cortana를 높이 Eiffel tower"), ("Hey Cortana를 열고 Netflix"), 앱을 열려면 테 또는 시작 메뉴 ("Hey Cortana, me 홈 수행")를 표시 한 테 등입니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-184">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="e0396-185">음성에 대 한 일반적인 질문 및 문제 사용자가</span><span class="sxs-lookup"><span data-stu-id="e0396-185">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="e0396-186">무어라 설명할 도리가 없어요?</span><span class="sxs-lookup"><span data-stu-id="e0396-186">What can I say?</span></span>
* <span data-ttu-id="e0396-187">시스템, 그렇습니다! 내가 어떻게 알 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="e0396-187">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="e0396-188">시스템 지속적 내 음성 명령을 잘못 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-188">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="e0396-189">음성 명령을 지정 하는 경우 반응 하지 않는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e0396-189">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="e0396-190">잘못 된 방식으로 반응 하는 음성 명령을 지정 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="e0396-190">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="e0396-191">특정 앱 또는 앱 명령 내 음성을 대상 하는 방법을 있습니까?</span><span class="sxs-lookup"><span data-stu-id="e0396-191">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="e0396-192">HoloLens에 음성 명령 holographic 프레임 것을 사용할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="e0396-192">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="see-also"></a><span data-ttu-id="e0396-193">참조</span><span class="sxs-lookup"><span data-stu-id="e0396-193">See also</span></span>
* [<span data-ttu-id="e0396-194">제스처</span><span class="sxs-lookup"><span data-stu-id="e0396-194">Gestures</span></span>](gestures.md)
* [<span data-ttu-id="e0396-195">응시 대상 지정</span><span class="sxs-lookup"><span data-stu-id="e0396-195">Gaze targeting</span></span>](gaze-targeting.md)
