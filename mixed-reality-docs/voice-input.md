---
title: 음성 입력
description: 음성 입력은 HoloLens 및 Windows Mixed Reality 모던 헤드셋의 핵심 입력입니다. 음성은 명령, 받아쓰기, Cortana 등에 사용할 수 있습니다.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv, 음성, cortana, 음성, 입력
ms.openlocfilehash: e21310b940e4a4c3019f61edea695b452e74ab62
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829952"
---
# <a name="voice-input"></a><span data-ttu-id="8d488-105">음성 입력</span><span class="sxs-lookup"><span data-stu-id="8d488-105">Voice input</span></span>

<span data-ttu-id="8d488-106">음성은 HoloLens에서 입력 하는 세 가지 주요 형태 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="8d488-107">[제스처](gestures.md)를 사용 하지 않고도 홀로그램을 직접 명령을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="8d488-108">홀로그램을 [응시](gaze.md) 하 고 명령을 말하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="8d488-109">음성 입력은 의도를 전달 하는 자연 스러운 방법이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="8d488-110">음성은 사용자가 하나의 명령을 사용 하 여 중첩 된 메뉴를 잘라낼 수 있으므로 특히 복잡 한 인터페이스를 트래버스하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="8d488-111">음성 입력은 다른 모든 유니버설 Windows 앱의 음성을 지 원하는 [동일한 엔진](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) 에 의해 구동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="8d488-112">장치 지원</span><span class="sxs-lookup"><span data-stu-id="8d488-112">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8d488-113"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="8d488-113"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="8d488-114"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8d488-114"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="8d488-115"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="8d488-115"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="8d488-116"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="8d488-116"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8d488-117">음성 입력</span><span class="sxs-lookup"><span data-stu-id="8d488-117">Voice input</span></span></td>
        <td><span data-ttu-id="8d488-118">✔️</span><span class="sxs-lookup"><span data-stu-id="8d488-118">✔️</span></span></td>
        <td><span data-ttu-id="8d488-119">✔️</span><span class="sxs-lookup"><span data-stu-id="8d488-119">✔️</span></span></td>
        <td><span data-ttu-id="8d488-120">✔️ (마이크 포함)</span><span class="sxs-lookup"><span data-stu-id="8d488-120">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="8d488-121">"Select" 명령</span><span class="sxs-lookup"><span data-stu-id="8d488-121">The "select" command</span></span>

<span data-ttu-id="8d488-122">앱에 음성 지원을 특별히 추가 하지 않은 경우에도 사용자는 "선택" 이라는 간단한 방법으로 holograms을 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="8d488-123">이는 HoloLens의 [공기 탭](gestures.md#air-tap) , [hololens clicker](hardware-accessories.md#hololens-clicker)의 선택 단추 누르기 또는 [Windows Mixed Reality 동작 컨트롤러](motion-controllers.md)에서 트리거 누르기와 동일 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="8d488-124">소리가 들리고 "선택"이 확인으로 표시 된 도구 설명이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="8d488-125">"선택"은 낮은 파워 키워드 검색 알고리즘에서 사용 하도록 설정 되므로 사용자가 손을 사용 하더라도 배터리 수명에 영향을 최소화 하면서 언제 든 지 항상 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="8d488-126">HoloLens 2에 대 한 추가 지침은 [곧](index.md#news-and-notes)제공 될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="8d488-127">![선택 영역에 음성 명령을 사용 하려면 "선택" 이라고 표시 합니다.](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="8d488-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="8d488-128">*선택 영역에 음성 명령을 사용 하려면 "선택" 이라고 표시 합니다.*</span><span class="sxs-lookup"><span data-stu-id="8d488-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="8d488-129">안녕 코타나</span><span class="sxs-lookup"><span data-stu-id="8d488-129">Hey Cortana</span></span>

<span data-ttu-id="8d488-130">또한 언제 든 지 Cortana를 표시 하는 "안녕하세요" Cortana를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="8d488-131">사용자의 질문을 계속 하거나 명령을 제공 하기 위해 사용자가 표시 될 때까지 기다릴 필요가 없습니다. 예를 들어 "안녕하세요?</span><span class="sxs-lookup"><span data-stu-id="8d488-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="8d488-132">단일 문장으로</span><span class="sxs-lookup"><span data-stu-id="8d488-132">as a single sentence.</span></span> <span data-ttu-id="8d488-133">Cortana 및 수행할 수 있는 작업에 대 한 자세한 내용은 사용자에 게 문의 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d488-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="8d488-134">"Cortana는 어떻게 해야 하나요?" 라고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="8d488-135">그리고 작업 및 제안 된 명령 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="8d488-136">Cortana 앱에 이미 있는 경우 **다음을 클릭** 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="8d488-137">동일한 메뉴를 끌어올 수 있는 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="8d488-138">**HoloLens 관련 명령**</span><span class="sxs-lookup"><span data-stu-id="8d488-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="8d488-139">"이렇게 말 하세요~"</span><span class="sxs-lookup"><span data-stu-id="8d488-139">"What can I say?"</span></span>
* <span data-ttu-id="8d488-140">[시작 메뉴로](navigating-the-windows-mixed-reality-home.md#start-menu) 이동 하려면 "홈으로 이동" 또는 "시작으로 이동"을 [블 룸](gestures.md#bloom) .</span><span class="sxs-lookup"><span data-stu-id="8d488-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="8d488-141">"Launch <app>"</span><span class="sxs-lookup"><span data-stu-id="8d488-141">"Launch <app>"</span></span>
* <span data-ttu-id="8d488-142">"여기 <app> 로 이동"</span><span class="sxs-lookup"><span data-stu-id="8d488-142">"Move <app> here"</span></span>
* <span data-ttu-id="8d488-143">"사진 찍기"</span><span class="sxs-lookup"><span data-stu-id="8d488-143">"Take a picture"</span></span>
* <span data-ttu-id="8d488-144">"기록 시작"</span><span class="sxs-lookup"><span data-stu-id="8d488-144">"Start recording"</span></span>
* <span data-ttu-id="8d488-145">"기록 중지"</span><span class="sxs-lookup"><span data-stu-id="8d488-145">"Stop recording"</span></span>
* <span data-ttu-id="8d488-146">"밝기 늘리기"</span><span class="sxs-lookup"><span data-stu-id="8d488-146">"Increase the brightness"</span></span>
* <span data-ttu-id="8d488-147">"밝기 낮추기"</span><span class="sxs-lookup"><span data-stu-id="8d488-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="8d488-148">"볼륨 증가"</span><span class="sxs-lookup"><span data-stu-id="8d488-148">"Increase the volume"</span></span>
* <span data-ttu-id="8d488-149">"볼륨 낮추기"</span><span class="sxs-lookup"><span data-stu-id="8d488-149">"Decrease the volume"</span></span>
* <span data-ttu-id="8d488-150">"음소거" 또는 "음소거 해제"</span><span class="sxs-lookup"><span data-stu-id="8d488-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="8d488-151">"장치 종료"</span><span class="sxs-lookup"><span data-stu-id="8d488-151">"Shut down the device"</span></span>
* <span data-ttu-id="8d488-152">"장치 다시 시작"</span><span class="sxs-lookup"><span data-stu-id="8d488-152">"Restart the device"</span></span>
* <span data-ttu-id="8d488-153">"절전 모드로 전환"</span><span class="sxs-lookup"><span data-stu-id="8d488-153">"Go to sleep"</span></span>
* <span data-ttu-id="8d488-154">"시간 이란?"</span><span class="sxs-lookup"><span data-stu-id="8d488-154">"What time is it?"</span></span>
* <span data-ttu-id="8d488-155">"얼마나 많은 배터리가 남아 있나요?"</span><span class="sxs-lookup"><span data-stu-id="8d488-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="8d488-156">"Call <contact>" (HoloLens를 위한 Skype 필요)</span><span class="sxs-lookup"><span data-stu-id="8d488-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="8d488-157">"이 항목을 참조 하세요."</span><span class="sxs-lookup"><span data-stu-id="8d488-157">"See It, Say It"</span></span>

<span data-ttu-id="8d488-158">HoloLens에는 음성 입력에 대 한 "이를 확인 하는 것이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="8d488-159">예를 들어 2D 앱을 볼 때 사용자는 앱 바에 표시 되는 "조정" 명령을 사용 하 여 전 세계의 앱 위치를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![2D 앱 또는 홀로그램을 볼 때 사용자는 앱 바에 표시 되는 "조정" 명령을 사용 하 여 전 세계의 앱 위치를 조정할 수 있습니다.](images/microphone-600px.png)

<span data-ttu-id="8d488-161">앱이이 규칙을 준수 하는 경우 사용자는 시스템을 제어 하는 내용을 쉽게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="8d488-162">이를 강화 하기 위해 단추를 gazing 하는 동안 단추를 음성으로 사용할 수 있는 경우 두 번째 "음성 유지" 도구 설명이 표시 되 고이를 통해 "press"로 말하는 명령이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="8d488-163">![단추 아래에 표시 되는 것을 확인 하세요.](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="8d488-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="8d488-164">*단추 아래에 "표시 됩니다." 라고 표시 되는 명령*</span><span class="sxs-lookup"><span data-stu-id="8d488-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="8d488-165">빠른 홀로그램 조작을 위한 음성 명령</span><span class="sxs-lookup"><span data-stu-id="8d488-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="8d488-166">또한 한 번에 조작 작업을 빠르게 수행 하기 위해 홀로그램에서 gazing 하는 동안 많은 음성 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="8d488-167">이러한 음성 명령은 전 세계에 배치한 3D 개체 뿐만 아니라 2D 앱 에서도 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="8d488-168">**홀로그램 조작 명령**</span><span class="sxs-lookup"><span data-stu-id="8d488-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="8d488-169">얼굴 얼굴</span><span class="sxs-lookup"><span data-stu-id="8d488-169">Face me</span></span>
* <span data-ttu-id="8d488-170">크게 | 보강</span><span class="sxs-lookup"><span data-stu-id="8d488-170">Bigger | Enhance</span></span>
* <span data-ttu-id="8d488-171">짧은</span><span class="sxs-lookup"><span data-stu-id="8d488-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="8d488-172">받아쓰기</span><span class="sxs-lookup"><span data-stu-id="8d488-172">Dictation</span></span>

<span data-ttu-id="8d488-173">음성 받아쓰기는 [공기 탭](gestures.md#air-tap)을 사용 하 여 입력 하는 대신 앱에 텍스트를 입력 하는 것이 더 효율적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="8d488-174">이렇게 하면 사용자에 대해 더 짧은 노력으로 입력 속도를 크게 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="8d488-175">![음성 받아쓰기는 마이크 단추를 선택 하 여 시작 합니다.](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="8d488-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="8d488-176">*음성 받아쓰기는 키보드에서 마이크 단추를 선택 하 여 시작 합니다.*</span><span class="sxs-lookup"><span data-stu-id="8d488-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="8d488-177">Holographic 키보드가 활성화 될 때마다 입력 하는 대신 받아쓰기 모드로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="8d488-178">텍스트 입력 상자의 측면에서 마이크를 선택 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="8d488-179">통신</span><span class="sxs-lookup"><span data-stu-id="8d488-179">Communication</span></span>

<span data-ttu-id="8d488-180">HoloLens에서 제공 하는 사용자 지정 된 오디오 입력 처리 옵션을 활용 하려는 응용 프로그램의 경우 앱에서 사용할 수 있는 다양 한 [오디오 스트림 범주](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) 를 이해 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="8d488-181">Windows 10은 몇 가지 다른 스트림 범주를 지원 하 고, HoloLens는 이러한 세 가지를 사용 하 여 음성, 통신 및 주변 환경 오디오에 사용 될 수 있는 마이크 오디오 품질을 최적화 하기 위해 사용자 지정 처리를 사용 하도록 설정 합니다. (즉, "캠코더") 시나리오를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="8d488-182">AudioCategory_Communications stream 범주는 통화 품질 및 내레이션 시나리오에 맞게 사용자 지정 되며 클라이언트에 사용자 음성의 16kHz 24bit mono 오디오 스트림을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="8d488-183">AudioCategory_Speech stream 범주는 HoloLens (Windows) 음성 엔진에 맞게 사용자 지정 되며 사용자 음성의 16kHz 24bit mono 스트림을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="8d488-184">이 범주는 필요한 경우 타사 음성 엔진에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="8d488-185">AudioCategory_Other stream 범주는 주변 환경 오디오 녹음에 맞게 사용자 지정 되며 클라이언트에 48kHz 24 비트 스테레오 오디오 스트림을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="8d488-186">이러한 오디오 처리는 모두 하드웨어 가속입니다. 즉, HoloLens CPU에서 동일한 처리가 수행 된 경우 보다 기능이 훨씬 더 많은 전력을 소모 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="8d488-187">시스템 배터리 수명을 최대화 하 고 오프 로드 된 기본 제공 오디오 입력 처리 기능을 활용 하기 위해 CPU에서 기타 오디오 입력 처리를 실행 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="8d488-188">문제 해결</span><span class="sxs-lookup"><span data-stu-id="8d488-188">Troubleshooting</span></span>

<span data-ttu-id="8d488-189">"Select" 및 "안녕하세요 Cortana"를 사용 하는 데 문제가 있는 경우 더 조용한 공간으로 이동 하거나, 소음의 원본에서 떨어진 곳으로 이동 하거나, 더 크게 말해 보세요.</span><span class="sxs-lookup"><span data-stu-id="8d488-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="8d488-190">지금은 HoloLens의 모든 음성 인식이 특별히 미국 영어의 기본 스피커로 조정 되 고 최적화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="8d488-191">Windows Mixed Reality Developer Edition 릴리스 2017에서는 초기 HMD 연결 후 PC 데스크톱에 로그 아웃 했다가 다시 로그인 한 후 오디오 끝점 관리 논리가 정상적으로 작동 합니다 (계속).</span><span class="sxs-lookup"><span data-stu-id="8d488-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="8d488-192">WMR OOBE를 통과 한 후 첫 번째 로그 아웃 이벤트 이전에는 사용자가 HMD를 처음으로 연결 하기 전에 설정 된 방법에 따라 오디오 없음에서 오디오 전환 없이 다양 한 오디오 기능 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d488-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d488-193">참조</span><span class="sxs-lookup"><span data-stu-id="8d488-193">See also</span></span>
* [<span data-ttu-id="8d488-194">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="8d488-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="8d488-195">Unity의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="8d488-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="8d488-196">MR 입력 212: 음성</span><span class="sxs-lookup"><span data-stu-id="8d488-196">MR Input 212: Voice</span></span>](holograms-212.md)
