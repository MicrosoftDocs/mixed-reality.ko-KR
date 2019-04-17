---
title: 음성 입력
description: 음성 입력이 HoloLens 및 Windows Mixed Reality 몰입 형 헤드셋에 대 한 핵심 입력 합니다. 음성 명령, 받아쓰기, Cortana, 등에 대 한 사용할 수 있습니다.
author: Hak0n
ms.author: hakons
ms.date: 02/24/2019
ms.topic: article
keywords: ggv, 음성, cortana 음성 입력
ms.openlocfilehash: 7fb5618c13ff1ed446241f744b598cfe2484ea45
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604742"
---
# <a name="voice-input"></a><span data-ttu-id="8db0d-105">음성 입력</span><span class="sxs-lookup"><span data-stu-id="8db0d-105">Voice input</span></span>

<span data-ttu-id="8db0d-106">음성에 대 한 의견도 HoloLens의 세 가지 키 형식 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-106">Voice is one of the three key forms of input on HoloLens.</span></span> <span data-ttu-id="8db0d-107">직접 사용 하지 않고도 홀로그램 명령 할 수 있습니다 [제스처](gestures.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-107">It allows you to directly command a hologram without having to use [gestures](gestures.md).</span></span> <span data-ttu-id="8db0d-108">있습니다 단순히 [gaze](gaze.md) 를 홀로그램에서 말하고 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-108">You simply [gaze](gaze.md) at a hologram and speak your command.</span></span> <span data-ttu-id="8db0d-109">음성 입력 의도인 통신 하는 자연 스러운 방법이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="8db0d-110">음성은 사용자가 하나의 명령 사용 하 여 중첩 된 메뉴가 줄이는 수 있기 때문에 복잡 한 인터페이스를 트래버스에 특히 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-110">Voice is especially good at traversing complex interfaces because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="8db0d-111">음성 입력으로 구동 되며 합니다 [같은 엔진](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) 다른 모든 유니버설 Windows 앱에서 지 원하는 음성.</span><span class="sxs-lookup"><span data-stu-id="8db0d-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other Universal Windows Apps.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/eHMkOpNUtR8]

## <a name="device-support"></a><span data-ttu-id="8db0d-112">장치 지원</span><span class="sxs-lookup"><span data-stu-id="8db0d-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8db0d-113">기능</span><span class="sxs-lookup"><span data-stu-id="8db0d-113">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="8db0d-114"><a href="hololens-hardware-details.md">HoloLens (첫 번째 범용)</a></span><span class="sxs-lookup"><span data-stu-id="8db0d-114"><a href="hololens-hardware-details.md">HoloLens (1st gen)</a></span></span></th><th style="width:150px"><span data-ttu-id="8db0d-115">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8db0d-115">HoloLens 2</span></span></th><th style="width:150px"><span data-ttu-id="8db0d-116"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="8db0d-116"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="8db0d-117">음성 입력</span><span class="sxs-lookup"><span data-stu-id="8db0d-117">Voice input</span></span></td><td style="text-align: center;"> <span data-ttu-id="8db0d-118">✔️</span><span class="sxs-lookup"><span data-stu-id="8db0d-118">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8db0d-119">✔️</span><span class="sxs-lookup"><span data-stu-id="8db0d-119">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="8db0d-120">(사용 하 여 마이크) ✔️</span><span class="sxs-lookup"><span data-stu-id="8db0d-120">✔️ (with microphone)</span></span></td>
</tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="8db0d-121">"Select" 명령</span><span class="sxs-lookup"><span data-stu-id="8db0d-121">The "select" command</span></span>

<span data-ttu-id="8db0d-122">음성 지원 앱에 구체적으로 추가 하지 않고도 사용자가 "select" 라는 하면 홀로그램을 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-122">Even without specifically adding voice support to your app, your users can activate holograms simply by saying "select".</span></span> <span data-ttu-id="8db0d-123">이 동일 하 게 동작을 [어 탭](gestures.md#air-tap) HoloLens에서 선택 단추를 누르고 합니다 [HoloLens clicker](hardware-accessories.md#hololens-clicker), 트리거를 누르거나는 [Windows Mixed Reality 동작 컨트롤러](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="8db0d-123">This behaves the same as an [air tap](gestures.md#air-tap) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="8db0d-124">소리를 듣고 되며 확인 표시 "선택"을 사용 하 여 도구 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8db0d-124">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="8db0d-125">"Select" 항상 쪽에는 손이 최소 배터리 수명에 영향을 줍니다 서 언제 든 지 말할 수는 사용할 수 있도록 절전 키워드 검색 알고리즘으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-125">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

> [!NOTE]
> <span data-ttu-id="8db0d-126">HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-126">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

<span data-ttu-id="8db0d-127">!["Select" 명령을 사용 하 여 음성 선택](images/kma-voice-select-00170-800px.png)</span><span class="sxs-lookup"><span data-stu-id="8db0d-127">![Say "select" to use the voice command for selection](images/kma-voice-select-00170-800px.png)</span></span><br>
<span data-ttu-id="8db0d-128">*"Select" 명령을 사용 하 여 음성 선택*</span><span class="sxs-lookup"><span data-stu-id="8db0d-128">*Say "select" to use the voice command for selection*</span></span>

## <a name="hey-cortana"></a><span data-ttu-id="8db0d-129">안녕 코타나</span><span class="sxs-lookup"><span data-stu-id="8db0d-129">Hey Cortana</span></span>

<span data-ttu-id="8db0d-130">또한 언제 든 지 Cortana를 불러오려면 "Hey Cortana"를 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-130">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="8db0d-131">그녀에 질문 만듭니다 계속 하거나 라는 예를 들어, 명령-만듭니다 제공에 게 표시 될 때까지 기다리는 필요가 "Hey Cortana 날씨 란?"</span><span class="sxs-lookup"><span data-stu-id="8db0d-131">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana what's the weather?"</span></span> <span data-ttu-id="8db0d-132">와 문장 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-132">as a single sentence.</span></span> <span data-ttu-id="8db0d-133">Cortana 및 수행할 수 있는 작업에 대 한 자세한 내용은 단순히 요청할 만듭니다!</span><span class="sxs-lookup"><span data-stu-id="8db0d-133">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="8db0d-134">"Hey Cortana 어떻게 말할" 예를 들어합니다</span><span class="sxs-lookup"><span data-stu-id="8db0d-134">Say "Hey Cortana what can I say?"</span></span> <span data-ttu-id="8db0d-135">자신이 작업 및 제안 된 명령의 목록을 잡아당깁니다 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-135">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="8db0d-136">Cortana 앱에서 이미 있는 경우 클릭할 수도 있습니다는 **?**</span><span class="sxs-lookup"><span data-stu-id="8db0d-136">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="8db0d-137">이 동일한 메뉴를 세로 막대에서 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-137">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="8db0d-138">**HoloLens 관련 명령**</span><span class="sxs-lookup"><span data-stu-id="8db0d-138">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="8db0d-139">"이렇게 말 하세요~"</span><span class="sxs-lookup"><span data-stu-id="8db0d-139">"What can I say?"</span></span>
* <span data-ttu-id="8db0d-140">"Go home" 또는 "시작"-of [블 룸](gestures.md#bloom) 페이지로 이동 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="8db0d-140">"Go home" or "Go to Start" - instead of [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="8db0d-141">"Launch <app>"</span><span class="sxs-lookup"><span data-stu-id="8db0d-141">"Launch <app>"</span></span>
* <span data-ttu-id="8db0d-142">"이동 <app> 여기"</span><span class="sxs-lookup"><span data-stu-id="8db0d-142">"Move <app> here"</span></span>
* <span data-ttu-id="8db0d-143">"사진을 찍은"</span><span class="sxs-lookup"><span data-stu-id="8db0d-143">"Take a picture"</span></span>
* <span data-ttu-id="8db0d-144">"기록 시작"</span><span class="sxs-lookup"><span data-stu-id="8db0d-144">"Start recording"</span></span>
* <span data-ttu-id="8db0d-145">"기록을 중지"</span><span class="sxs-lookup"><span data-stu-id="8db0d-145">"Stop recording"</span></span>
* <span data-ttu-id="8db0d-146">"밝게"</span><span class="sxs-lookup"><span data-stu-id="8db0d-146">"Increase the brightness"</span></span>
* <span data-ttu-id="8db0d-147">"밝기 decrease"</span><span class="sxs-lookup"><span data-stu-id="8db0d-147">"Decrease the brightness"</span></span>
* <span data-ttu-id="8db0d-148">"볼륨 increase"</span><span class="sxs-lookup"><span data-stu-id="8db0d-148">"Increase the volume"</span></span>
* <span data-ttu-id="8db0d-149">"볼륨 decrease"</span><span class="sxs-lookup"><span data-stu-id="8db0d-149">"Decrease the volume"</span></span>
* <span data-ttu-id="8db0d-150">"Mute" 또는 "음소거 해제"</span><span class="sxs-lookup"><span data-stu-id="8db0d-150">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="8db0d-151">"장치 종료"</span><span class="sxs-lookup"><span data-stu-id="8db0d-151">"Shut down the device"</span></span>
* <span data-ttu-id="8db0d-152">"장치를 다시 시작"</span><span class="sxs-lookup"><span data-stu-id="8db0d-152">"Restart the device"</span></span>
* <span data-ttu-id="8db0d-153">"절전 모드로 이동"</span><span class="sxs-lookup"><span data-stu-id="8db0d-153">"Go to sleep"</span></span>
* <span data-ttu-id="8db0d-154">"언제 입니까"?</span><span class="sxs-lookup"><span data-stu-id="8db0d-154">"What time is it?"</span></span>
* <span data-ttu-id="8db0d-155">"남은 양을 배터리 do?"</span><span class="sxs-lookup"><span data-stu-id="8db0d-155">"How much battery do I have left?"</span></span>
* <span data-ttu-id="8db0d-156">"호출 <contact>" (HoloLens에 대 한 Skype 필요)</span><span class="sxs-lookup"><span data-stu-id="8db0d-156">"Call <contact>" (requires Skype for HoloLens)</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="8db0d-157">"표시, 말"</span><span class="sxs-lookup"><span data-stu-id="8db0d-157">"See It, Say It"</span></span>

<span data-ttu-id="8db0d-158">HoloLens에 음성 입력에 대 한 "표시, 말" 모델이 있는 단추에서 레이블을 사용자에 게 알려주기 어떤 음성 명령으로 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-158">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="8db0d-159">예를 들어, 2D 앱을 보면 사용자 환경에서 앱의 위치를 조정 하려면 앱 바에서 보는 "조정" 명령을 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-159">For example, when looking at a 2D app, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span>

![사용자 환경에서 앱의 위치를 조정 하려면 앱 바에서 보는 "조정" 명령 말할 수는 2D 앱 또는 홀로그램에 원하는 경우](images/microphone-600px.png)

<span data-ttu-id="8db0d-161">앱이이 규칙에 따라, 시스템을 제어 하에 사용자가 쉽게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-161">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="8db0d-162">단추에서 gazing 하는 동안이 보완을 하려면 단추 음성 지원 및 "누름"에 게 문의 하는 명령을 표시 하는 경우 잠시 후 표시 되는 "음성 지속" 도구 설명이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-162">To reinforce this, while gazing at a button, you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span>

<span data-ttu-id="8db0d-163">![표시, 말 명령 단추 아래에 나타납니다.](images/voice-seeitsayit-600px.png)</span><span class="sxs-lookup"><span data-stu-id="8db0d-163">![See it, say it commands appear below the buttons](images/voice-seeitsayit-600px.png)</span></span><br>
<span data-ttu-id="8db0d-164">*단추 아래에 표시 되는 명령 "말이 참조 하세요."*</span><span class="sxs-lookup"><span data-stu-id="8db0d-164">*"See it, say it" commands appear below the buttons*</span></span>

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="8db0d-165">빠른 홀로그램 조작에 대 한 음성 명령</span><span class="sxs-lookup"><span data-stu-id="8db0d-165">Voice commands for fast Hologram Manipulation</span></span>

<span data-ttu-id="8db0d-166">이 밖에도 다양 한 음성 명령에 신속 하 게 조작 작업을 수행 하는 홀로그램 gazing 하는 동안 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-166">There are also a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="8db0d-167">이러한 음성 명령은 2D 앱 뿐 아니라 전 세계에서 3D 개체에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-167">These voice commands work on 2D apps as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="8db0d-168">**홀로그램 조작 명령**</span><span class="sxs-lookup"><span data-stu-id="8db0d-168">**Hologram Manipulation Commands**</span></span>
* <span data-ttu-id="8db0d-169">Me 얼굴</span><span class="sxs-lookup"><span data-stu-id="8db0d-169">Face me</span></span>
* <span data-ttu-id="8db0d-170">더 큰 | 강화</span><span class="sxs-lookup"><span data-stu-id="8db0d-170">Bigger | Enhance</span></span>
* <span data-ttu-id="8db0d-171">더 작은</span><span class="sxs-lookup"><span data-stu-id="8db0d-171">Smaller</span></span>

## <a name="dictation"></a><span data-ttu-id="8db0d-172">받아쓰기</span><span class="sxs-lookup"><span data-stu-id="8db0d-172">Dictation</span></span>

<span data-ttu-id="8db0d-173">사용 하 여 입력 하지 않고도 [탭을 어](gestures.md#air-tap), 음성 받아쓰기를 앱에 텍스트를 입력 하는 것이 효율적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-173">Rather than typing with [air taps](gestures.md#air-tap), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="8db0d-174">매우 적은 노력으로 사용자를 사용 하 여 입력을 가속화할 수 있습니다이.</span><span class="sxs-lookup"><span data-stu-id="8db0d-174">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="8db0d-175">![음성 받아쓰기 마이크 단추를 선택 하 여 시작](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="8db0d-175">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="8db0d-176">*음성 받아쓰기 키보드에서 마이크 단추를 선택 하 여 시작*</span><span class="sxs-lookup"><span data-stu-id="8db0d-176">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="8db0d-177">Holographic 키보드가 활성 상태인 경우 언제 든 지를 입력 하는 대신 받아쓰기 모드로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-177">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="8db0d-178">시작 하려면 텍스트 입력된 상자 측면의 마이크를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-178">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="communication"></a><span data-ttu-id="8db0d-179">통신</span><span class="sxs-lookup"><span data-stu-id="8db0d-179">Communication</span></span>

<span data-ttu-id="8db0d-180">사용자 지정된 오디오 입력 처리 HoloLens에서 제공 하는 옵션을 활용 하고자 하는 응용 프로그램에 대 한 다양 한 알아야 할 것 [오디오 스트림 범주](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) 앱에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-180">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="8db0d-181">여러 개의 다른 스트림으로 범주 및 HoloLens를 사용 하면 Windows 10 지원을 사용 하 여 이러한 세 가지 음성, 통신 및 오디오 주변 환경에 대 한 사용할 수 있는 다른 맞게 마이크 오디오 품질을 최적화 하기 위해 사용자 지정 처리를 사용 하도록 설정 캡처 (즉, "camcorder") 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-181">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="8db0d-182">AudioCategory_Communications stream 범주 호출 품질 및 내레이션 시나리오에 대 한 사용자 지정 된 고 사용자의 음성의 16, 24 비트 kHz 모노 오디오 스트림을 사용 하 여 클라이언트에 제공</span><span class="sxs-lookup"><span data-stu-id="8db0d-182">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="8db0d-183">AudioCategory_Speech stream 범주 HoloLens (Windows) 음성 엔진에 대 한 사용자 지정 된와 사용자의 음성의 16, 24 비트 kHz mono 스트림을 사용 하 여 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-183">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="8db0d-184">필요한 경우 타사 파티 음성 엔진에서이 범주를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-184">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="8db0d-185">AudioCategory_Other stream 범주 오디오 녹음 주변 환경에 대 한 사용자 지정 된 고 48 kHz 24 비트 스테레오 오디오 스트림을 사용 하 여 클라이언트를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-185">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="8db0d-186">이 모든 오디오 처리가 하드웨어 가속 기능 드레이닝 HoloLens CPU에서 동일한 처리가 완료 된 경우 보다 훨씬 적습니다. power를 의미 하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-186">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="8db0d-187">다른 오디오 입력 시스템 배터리 수명을 최대화 하 여 기본 제공된을 활용 하기 위해 CPU에서 처리를 실행 하지 않습니다, 오디오 입력된 처리를 오프 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-187">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="8db0d-188">문제 해결</span><span class="sxs-lookup"><span data-stu-id="8db0d-188">Troubleshooting</span></span>

<span data-ttu-id="8db0d-189">그래도 모든 "선택"을 사용 하 여 문제 및 "Hey Cortana" 방문해봅니다 노이즈를 더 크게 통화 하 여 원본에서 설정, 조용한 공간으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-189">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="8db0d-190">이때 HoloLens에 모든 음성 인식 조정 이며의 미국 영어를 모국어에 맞게 최적화 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-190">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="8db0d-191">Windows Mixed Reality Developer Edition 2017 릴리스의 경우 오디오 끝점 관리 논리 작동 제대로 (영원히) HMD 한 초기 연결 후 PC 바탕 화면에서 로그 아웃 후 다시 로그인 한 후 합니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-191">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="8db0d-192">Out/WMR OOBE 통해 이동 후 이벤트에 해당 첫 번째 기호 하기 전에 사용자 오디오 없음에서 오디오를 HMD 처음으로 연결 하기 전에 시스템 설정 된 방식에 따라 전환 없는에 이르기까지 다양 한 오디오 기능 문제를 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8db0d-192">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8db0d-193">참조</span><span class="sxs-lookup"><span data-stu-id="8db0d-193">See also</span></span>
* [<span data-ttu-id="8db0d-194">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="8db0d-194">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="8db0d-195">Unity에서 음성 입력</span><span class="sxs-lookup"><span data-stu-id="8db0d-195">Voice input in Unity</span></span>](voice-input-in-unity.md)
* [<span data-ttu-id="8db0d-196">MR 입력 212: 음성</span><span class="sxs-lookup"><span data-stu-id="8db0d-196">MR Input 212: Voice</span></span>](holograms-212.md)
