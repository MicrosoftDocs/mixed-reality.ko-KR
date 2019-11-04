---
title: 음성 명령
description: GGV(응시, 제스처 및 음성)는 HoloLens에서 상호 작용을 수행하는 기본적인 수단입니다. 이 문서에서는 음성 디자인에 대한 상세한 지침을 제공합니다.
author: shengkait
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
keywords: Windows Mixed Reality, design, interaction, voice
ms.openlocfilehash: bfcaef787b22f17da9627a53c92c43f5cb1e1d9b
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437221"
---
# <a name="voice-commanding"></a><span data-ttu-id="c2c73-105">음성 명령</span><span class="sxs-lookup"><span data-stu-id="c2c73-105">Voice commanding</span></span>

<span data-ttu-id="c2c73-106">음성 명령을 사용하는 경우 응시는 일반적으로 타기팅 메커니즘, 즉 포인터("선택")로서 또는 애플리케이션으로 명령을 보내기 위해("보기, 말하기") 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-106">When using voice commands, gaze is typically used as the targeting mechaninism, whether as a pointer ("select") or to direct your command to an application ("see it, say it").</span></span> <span data-ttu-id="c2c73-107">물론, 일부 음성 명령은 "go to start" 또는 "Hey, Cortana"와 같이 대상이 전혀 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-107">Of course, some voice commands don't require a target at all, like "go to start" or "Hey, Cortana."</span></span>


## <a name="device-support"></a><span data-ttu-id="c2c73-108">장치 지원</span><span class="sxs-lookup"><span data-stu-id="c2c73-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c2c73-109"><strong>기능과</strong></span><span class="sxs-lookup"><span data-stu-id="c2c73-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="c2c73-110"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c2c73-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="c2c73-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="c2c73-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="c2c73-112"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="c2c73-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c2c73-113">음성 명령</span><span class="sxs-lookup"><span data-stu-id="c2c73-113">Voice commanding</span></span></td>
        <td><span data-ttu-id="c2c73-114">✔️</span><span class="sxs-lookup"><span data-stu-id="c2c73-114">✔️</span></span></td>
        <td><span data-ttu-id="c2c73-115">✔️</span><span class="sxs-lookup"><span data-stu-id="c2c73-115">✔️</span></span></td>
        <td><span data-ttu-id="c2c73-116">✔️(헤드셋이 연결됨)</span><span class="sxs-lookup"><span data-stu-id="c2c73-116">✔️ (with headset attached)</span></span></td>
    </tr>
</table>



## <a name="how-to-use-voice"></a><span data-ttu-id="c2c73-117">음성을 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="c2c73-117">How to use voice</span></span>

<span data-ttu-id="c2c73-118">빌드하는 모든 환경에 음성 명령을 추가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-118">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="c2c73-119">음성은 강력하고 편리한 방식으로 시스템 및 앱을 제어할 수 있는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-119">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="c2c73-120">사용자는 다양한 언어 및 악센트를 사용하기 때문에 음성 키워드를 적절히 선택하면 사용자의 명령이 명확하게 해석될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-120">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="c2c73-121">모범 사례</span><span class="sxs-lookup"><span data-stu-id="c2c73-121">Best practices</span></span>

<span data-ttu-id="c2c73-122">다음은 매끄러운 음성 인식에 도움이 될 수 있는 몇 가지 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-122">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="c2c73-123">**간결한 명령 사용** - 가능한 경우 두 개 이상의 음절로 이루어진 키워드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-123">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="c2c73-124">1음절 단어는 악센트가 다른 사람이 말할 경우 다른 모음 소리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-124">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="c2c73-125">예: "비디오 재생"은 "현재 선택한 비디오 재생" 보다 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-125">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="c2c73-126">**간단한 어휘 사용** -예: "show note"는 "show 카드" 보다 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-126">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="c2c73-127">**비파괴적인 명령 사용** - 음성 명령으로 수행할 수 있는 모든 작업은 비파괴적이어야 하며, 사용자 근처에서 말하는 다른 사람이 실수로 명령을 트리거하는 경우 쉽게 실행 취소할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-127">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="c2c73-128">**유사하게 들리는 명령 사용 금지** - 매우 비슷하게 들리는 여러 음성 명령을 등록하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-128">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="c2c73-129">예: "자세히 표시" 및 "저장소 표시"는 매우 유사 하 게 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-129">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="c2c73-130">**사용하지 않을 경우 앱 등록 취소** - 앱에서 특정 음성 명령이 유효한 상태가 아닐 경우에는 다른 명령과 혼동되지 않도록 등록을 취소하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-130">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="c2c73-131">**다른 악센트로 테스트** - 다른 악센트의 사용자와 앱을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-131">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="c2c73-132">**음성 명령 일관성 유지** - "Go back"이라고 말할 경우 이전 페이지로 이동되면 애플리케이션에서 이 동작을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-132">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="c2c73-133">**시스템 명령 사용 방지** - 다음 음성 명령은 시스템용으로 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-133">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="c2c73-134">따라서 애플리케이션에서 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-134">These should not be used by applications.</span></span>
   * <span data-ttu-id="c2c73-135">"Hey Cortana"</span><span class="sxs-lookup"><span data-stu-id="c2c73-135">"Hey Cortana"</span></span>
   * <span data-ttu-id="c2c73-136">"Select"</span><span class="sxs-lookup"><span data-stu-id="c2c73-136">"Select"</span></span>

### <a name="select"></a><span data-ttu-id="c2c73-137">"Select"</span><span class="sxs-lookup"><span data-stu-id="c2c73-137">"Select"</span></span>

<span data-ttu-id="c2c73-138">언제든지 "select"라고 말하면 응시 커서가 가리키고 있는 대상이 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-138">Saying "select" at any time will activate whatever the gaze cursor is pointing at.</span></span> 

><span data-ttu-id="c2c73-139">참고: HoloLens 2에서는 먼저 "select" 라는 단어를 말하여 응시 커서를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-139">Note: In HoloLens 2, the gaze cursor needs to first be invoked by saying the word "select".</span></span> <span data-ttu-id="c2c73-140">활성화하려면 "select"라고 다시 말합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-140">Say, "select" again to activate.</span></span> <span data-ttu-id="c2c73-141">응시 커서를 숨기려면 손으로 에어 탭하거나 개체를 터치하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-141">To hide the gaze cursor, simply use your hands -- airtap or touch an object.</span></span> 

### <a name="see-it-say-it"></a><span data-ttu-id="c2c73-142">보기, 말하기</span><span class="sxs-lookup"><span data-stu-id="c2c73-142">See it, say it</span></span>

<span data-ttu-id="c2c73-143">Windows Mixed Reality는 **단추의 레이블이 연결된 음성 명령과 동일**한 “보기, 말하기” 음성 모델을 채택했습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-143">Windows Mixed Reality has employed a "see it, say it" voice model where **labels on buttons are identical to the associated voice commands**.</span></span> <span data-ttu-id="c2c73-144">레이블 및 음성 명령 간에 충돌이 없으므로 사용자는 시스템을 제어하기 위해 어떤 말을 해야 할지를 보다 잘 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-144">Because there isn’t any dissonance between the label and the voice command, users can better understand what to say to control the system.</span></span> <span data-ttu-id="c2c73-145">이를 보완하기 위해 단추를 계속 바라보면 음성이 지원되는 단추임을 나타내기 위해 **"음성 바라보기 팁"** 이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-145">To reinforce this, while dwelling on a button, a **"voice dwell tip"** appears to communicate which buttons are voice enabled.</span></span>


![보기, 말하기 예제 1](images/voice-seeitsayit1-640px.jpg)

<span data-ttu-id="c2c73-147">![보기, 말하기 예제 2](images/voice-seeitsayit2-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2c73-147">![See it say it example 2](images/voice-seeitsayit2-640px.jpg)</span></span><br>
<span data-ttu-id="c2c73-148">*"보기, 말하기" 예제*</span><span class="sxs-lookup"><span data-stu-id="c2c73-148">*Examples of "see it, say it"*</span></span>

### <a name="voices-strengths"></a><span data-ttu-id="c2c73-149">음성의 장점</span><span class="sxs-lookup"><span data-stu-id="c2c73-149">Voice's strengths</span></span>

<span data-ttu-id="c2c73-150">음성 입력은 의도를 전달하는 자연스러운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-150">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="c2c73-151">음성은 사용자가 인터페이스의 여러 단계를 구분하는 데 도움이 되므로 인터페이스 **이동** 시 특히 유용합니다(사용자는 위로 올라가서 앱의 뒤로 단추를 누르는 대신, 웹 페이지를 바라보면서 "go back"이라고 말할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="c2c73-151">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at Web page, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="c2c73-152">이러한 약간의 시간 절약 효과가 사용자에게는 **정서적으로 강력한 효과**를 주며 약간의 초능력을 주는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-152">This small time savings has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="c2c73-153">팔에 무언가를 잔뜩 들고 있거나 **멀티태스킹** 중일 때도 음성을 사용하는 것이 편리한 입력 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-153">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="c2c73-154">키보드에서 입력하는 것이 어려운 디바이스에서는 **음성 받아쓰기**가 효율적인 대체 입력 방법이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-154">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input.</span></span> <span data-ttu-id="c2c73-155">마지막으로 응시 및 제스처의 **정확도 범위**가 제한된 경우 음성이 사용자가 유일하게 신뢰할 수 있는 입력 방법일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-155">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, Voice might be a user’s only trusted method input.</span></span>

<span data-ttu-id="c2c73-156">**사용자에게 도움이 될 수 있는 음성 사용 방법**</span><span class="sxs-lookup"><span data-stu-id="c2c73-156">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="c2c73-157">시간 단축 - 보다 효율적으로 최종 목표에 도달할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-157">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="c2c73-158">최소의 노력 - 보다 유연하고 편리하게 작업할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-158">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="c2c73-159">인지 부담 감소 - 직관적이며 배우고 기억하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-159">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="c2c73-160">사회적으로 용인 가능 - 사회 규범을 벗어나지 않는 행동을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-160">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="c2c73-161">일상적임 - 음성이 습관적인 동작이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-161">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="voices-weaknesses"></a><span data-ttu-id="c2c73-162">음성의 단점</span><span class="sxs-lookup"><span data-stu-id="c2c73-162">Voice's weaknesses</span></span>

<span data-ttu-id="c2c73-163">음성에는 몇 가지 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-163">Voice also has some weaknesses.</span></span> <span data-ttu-id="c2c73-164">세밀한 제어가 어렵다는 것이 그중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-164">Fine-grained control is one of them.</span></span> <span data-ttu-id="c2c73-165">예를 들어, "louder"라고 말할 수 있지만 어느 정도인지는 말할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-165">(for example a user might say "louder," but can’t say how much.</span></span> <span data-ttu-id="c2c73-166">"A little"을 수량화하기는 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-166">"A little" is hard to quantify.</span></span> <span data-ttu-id="c2c73-167">음성을 사용하여 이동하거나 크기를 조정하는 것도 어렵습니다. 음성은 세밀한 제어 기능을 제공하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-167">Moving or scaling things with voice is also difficult (voice does not offer the granularity of control).</span></span> <span data-ttu-id="c2c73-168">또한 음성은 완벽하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-168">Voice can also be imperfect.</span></span> <span data-ttu-id="c2c73-169">경우에 따라 음성 시스템이 명령을 잘못 듣거나 명령을 듣지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-169">Sometimes a voice system incorrectly hears a command or fails to hear a command.</span></span> <span data-ttu-id="c2c73-170">어떤 인터페이스에서도 이러한 오류에서 복구하는 것은 어려운 일입니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-170">Recovering from such errors is a challenge in any interface.</span></span> <span data-ttu-id="c2c73-171">마지막으로, 공공 장소에서는 음성이 허용되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-171">Lastly, voice may not be socially acceptable in public places.</span></span> <span data-ttu-id="c2c73-172">사용자가 말할 수 없거나 말하지 않아야 하는 내용도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-172">There are some things that users can’t or shouldn’t say.</span></span> <span data-ttu-id="c2c73-173">따라서 가장 적합한 경우에 음성을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-173">These cliffs allow speech to be used for what it is best at.</span></span>

### <a name="voice-feedback-states"></a><span data-ttu-id="c2c73-174">음성 피드백 상태</span><span class="sxs-lookup"><span data-stu-id="c2c73-174">Voice feedback states</span></span>

<span data-ttu-id="c2c73-175">음성이 제대로 적용되면 사용자는 **말할 수 있는 사항**을 이해하고 시스템이 **올바르게 알아 들었다는 명확한 피드백을 받게 됩니다**.</span><span class="sxs-lookup"><span data-stu-id="c2c73-175">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="c2c73-176">이러한 두 신호를 통해 사용자는 음성을 기본 입력으로 사용할 때 안심할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-176">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="c2c73-177">다음은 음성 입력이 인식될 때 커서에 나타나는 결과와 사용자에게 이러한 사실을 전달하는 방법을 보여 주는 다이어그램입니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-177">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>

<span data-ttu-id="c2c73-178">![커서에 대한 음성 피드백 상태](images/voicefeedbackstates.png)</span><span class="sxs-lookup"><span data-stu-id="c2c73-178">![Voice feedback states for cursor](images/voicefeedbackstates.png)</span></span><br>
<span data-ttu-id="c2c73-179">*커서에 대한 음성 피드백 상태*</span><span class="sxs-lookup"><span data-stu-id="c2c73-179">*Voice feedback states for cursor*</span></span>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="c2c73-180">혼합 현실에서 "음성"에 대해 알아야 할 주요 사항</span><span class="sxs-lookup"><span data-stu-id="c2c73-180">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="c2c73-181">단추를 타기팅할 때 **"Select"** 라고 말합니다(단추를 클릭하기 위해 어디에서나 사용할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="c2c73-181">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="c2c73-182">일부 앱에서는 작업을 수행하기 위해 **label name of an app bar button**이라고 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-182">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="c2c73-183">예를 들어, 앱을 바라보면서 명령 "Remove"라고 말하여 작업 환경에서 해당 앱을 제거할 수 있습니다(손으로 클릭할 때모다 시간이 절감됨).</span><span class="sxs-lookup"><span data-stu-id="c2c73-183">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="c2c73-184">**"Hey Cortana"** 라고 말하여 Cortana가 청취를 시작하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-184">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="c2c73-185">질문을 하거나("Hey Cortana, how tall is the Eiffel tower"), 앱을 열도록 말하거나("Hey Cortana, open Netflix"), 시작 메뉴를 불러오도록 말할 수 있습니다("Hey Cortana, take me home").</span><span class="sxs-lookup"><span data-stu-id="c2c73-185">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="c2c73-186">음성에 대한 사용자의 일반적인 질문 및 어려움</span><span class="sxs-lookup"><span data-stu-id="c2c73-186">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="c2c73-187">무엇을 말할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="c2c73-187">What can I say?</span></span>
* <span data-ttu-id="c2c73-188">시스템이 내 말을 제대로 알아듣는지 어떻게 알 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="c2c73-188">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="c2c73-189">시스템이 내 음성 명령을 계속 잘못 알아듣습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-189">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="c2c73-190">음성 명령을 받아도 반응하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-190">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="c2c73-191">음성 명령을 제공할 때 잘못된 방식으로 반응합니다.</span><span class="sxs-lookup"><span data-stu-id="c2c73-191">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="c2c73-192">특정 앱이나 앱 명령을 대상으로 음성 명령을 내리려면 어떻게 하나요?</span><span class="sxs-lookup"><span data-stu-id="c2c73-192">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="c2c73-193">음성을 사용해서 항목을 HoloLens의 홀로그래픽 프레임 밖으로 보낼 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="c2c73-193">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="see-also"></a><span data-ttu-id="c2c73-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c2c73-194">See also</span></span>
* [<span data-ttu-id="c2c73-195">제스처</span><span class="sxs-lookup"><span data-stu-id="c2c73-195">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="c2c73-196">헤드 게이즈 및 유지</span><span class="sxs-lookup"><span data-stu-id="c2c73-196">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
