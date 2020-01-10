---
title: 음성 입력
description: 음성 입력은 HoloLens 및 Windows Mixed Reality 모던 헤드셋의 핵심 입력입니다. 음성은 명령, 받아쓰기, Cortana 등에 사용할 수 있습니다.
author: Hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, 음성, cortana, 음성, 입력
ms.openlocfilehash: f2ae18d4063c7c4a63346a1202cacaa7fbbdf959
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723192"
---
# <a name="voice-input"></a><span data-ttu-id="4dffe-105">음성 입력</span><span class="sxs-lookup"><span data-stu-id="4dffe-105">Voice input</span></span>

![음성 입력](images/UX/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="4dffe-107">음성은 HoloLens의 주요 입력 형태 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="4dffe-108">직접 [제스처](gaze-and-commit.md#composite-gestures)를 사용 하지 않고도 홀로그램을 직접 명령을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="4dffe-109">음성 입력은 의도를 전달하는 자연스러운 방법일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="4dffe-110">음성은 복잡 한 인터페이스를 트래버스하는 데 특히 유용 합니다 .이를 통해 사용자는 단일 명령을 사용 하 여 중첩 된 메뉴를 잘라낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="4dffe-111">음성 입력은 다른 모든 _유니버설 Windows 앱_의 음성을 지 원하는 [동일한 엔진](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) 에 의해 구동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-111">Voice input is powered by the [same engine](https://msdn.microsoft.com/library/windows/apps/mt185615.aspx) that supports speech in all other _Universal Windows Apps_.</span></span> <span data-ttu-id="4dffe-112">HoloLens에서 음성 인식은 항상 설정에 구성 된 Windows 표시 언어로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-112">On HoloLens, speech recognition will always function in the Windows display language configured in Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="4dffe-113">음성 및 응시</span><span class="sxs-lookup"><span data-stu-id="4dffe-113">Voice and gaze</span></span>

<span data-ttu-id="4dffe-114">음성 명령을 사용 하는 경우 (head 또는 눈) 응시는 일반적으로 커서 ("select")를 사용 하 여 대상 메커니즘으로 사용 되거나 원하는 응용 프로그램에 명령을 암시적으로 채널 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-114">When using voice commands, (head or eye) gaze is typically used as the targeting mechanism, whether with a cursor ("select") or to implicitly channel your command to an application that you are looking at.</span></span> <span data-ttu-id="4dffe-115">이 경우에는 모든 응시 커서를 표시 하는 데 필요 하지 않을 수 있습니다 _("참조)_ .</span><span class="sxs-lookup"><span data-stu-id="4dffe-115">For this, it may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="4dffe-116">물론 일부 음성 명령에는 "시작으로 이동" 또는 "안녕하세요 Cortana"와 같은 대상이 전혀 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-116">Of course, some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="4dffe-117">장치 지원</span><span class="sxs-lookup"><span data-stu-id="4dffe-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4dffe-118"><strong>기능</strong></span><span class="sxs-lookup"><span data-stu-id="4dffe-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="4dffe-119"><a href="hololens-hardware-details.md"><strong>HoloLens(1세대)</strong></a></span><span class="sxs-lookup"><span data-stu-id="4dffe-119"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="4dffe-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="4dffe-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="4dffe-121"><a href="immersive-headset-hardware-details.md"><strong>몰입형 헤드셋</strong></a></span><span class="sxs-lookup"><span data-stu-id="4dffe-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4dffe-122">음성 입력</span><span class="sxs-lookup"><span data-stu-id="4dffe-122">Voice input</span></span></td>
        <td><span data-ttu-id="4dffe-123">✔️</span><span class="sxs-lookup"><span data-stu-id="4dffe-123">✔️</span></span></td>
        <td><span data-ttu-id="4dffe-124">✔️</span><span class="sxs-lookup"><span data-stu-id="4dffe-124">✔️</span></span></td>
        <td><span data-ttu-id="4dffe-125">✔️ (마이크 포함)</span><span class="sxs-lookup"><span data-stu-id="4dffe-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="4dffe-126">"Select" 명령</span><span class="sxs-lookup"><span data-stu-id="4dffe-126">The "select" command</span></span>

<span data-ttu-id="4dffe-127">**HoloLens(1세대)**</span><span class="sxs-lookup"><span data-stu-id="4dffe-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="4dffe-128">앱에 음성 지원을 특별히 추가 하지 않은 경우에도 사용자는 시스템 음성 명령 "select"를 통해 holograms을 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="4dffe-129">이는 HoloLens의 [공기 탭](gaze-and-commit.md#composite-gestures) , [hololens clicker](hardware-accessories.md#hololens-clicker)의 선택 단추 누르기 또는 [Windows Mixed Reality 동작 컨트롤러](motion-controllers.md)에서 트리거 누르기와 동일 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](hardware-accessories.md#hololens-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="4dffe-130">소리가 들리고 "선택"이 확인으로 표시 된 도구 설명이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-130">You will hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="4dffe-131">"선택"은 낮은 파워 키워드 검색 알고리즘에서 사용 하도록 설정 되므로 사용자가 손을 사용 하더라도 배터리 수명에 영향을 최소화 하면서 언제 든 지 항상 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-131">"Select" is enabled by a low power keyword detection algorithm so it is always available for you to say at any time with minimal battery life impact, even with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="4dffe-132">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="4dffe-132">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="4dffe-133">HoloLens 2에서 "select" 음성 명령을 사용 하려면 먼저 응시 커서를 사용 하 여 포인터로 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-133">In order to use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="4dffe-134">이를 가져오는 명령은 쉽게 기억할 수 있습니다. 예를 들어 "선택" 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-134">The command to bring it up is easy to remember -- just say, "select".</span></span><br><br>
        <span data-ttu-id="4dffe-135">모드를 종료 하려면 마우스를 사용 하 여 손가락을 다시 사용 하거나 손가락으로 단추에 근접 하거나 시스템 제스처를 사용 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-135">To exit the mode, simply use your hands again, either by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br>
        <span data-ttu-id="4dffe-136">*이미지: 선택 영역에 음성 명령을 사용 하려면 "선택"*</span><span class="sxs-lookup"><span data-stu-id="4dffe-136">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![사용자는 선택에 대해 음성 명령을 사용 하기 위해 "선택" 이라고 말할 수 있습니다.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="hey-cortana"></a><span data-ttu-id="4dffe-138">안녕 코타나</span><span class="sxs-lookup"><span data-stu-id="4dffe-138">Hey Cortana</span></span>

<span data-ttu-id="4dffe-139">또한 언제 든 지 Cortana를 표시 하는 "안녕하세요" Cortana를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-139">You can also say "Hey Cortana" to bring up Cortana at anytime.</span></span> <span data-ttu-id="4dffe-140">사용자의 질문을 계속 하거나 명령을 제공 하기 위해 사용자가 표시 될 때까지 기다릴 필요가 없습니다. 예를 들어 "안녕하세요?</span><span class="sxs-lookup"><span data-stu-id="4dffe-140">You don't have to wait for her to appear to continue asking her your question or giving her an instruction - for example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="4dffe-141">단일 문장으로</span><span class="sxs-lookup"><span data-stu-id="4dffe-141">as a single sentence.</span></span> <span data-ttu-id="4dffe-142">Cortana 및 수행할 수 있는 작업에 대 한 자세한 내용은 사용자에 게 문의 하세요.</span><span class="sxs-lookup"><span data-stu-id="4dffe-142">For more information about Cortana and what you can do, simply ask her!</span></span> <span data-ttu-id="4dffe-143">"안녕하세요?" 라고 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-143">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="4dffe-144">그리고 작업 및 제안 된 명령 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-144">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="4dffe-145">Cortana 앱에 이미 있는 경우 **다음을 클릭 하면 됩니다** .</span><span class="sxs-lookup"><span data-stu-id="4dffe-145">If you're already in the Cortana app you can also click the **?**</span></span> <span data-ttu-id="4dffe-146">동일한 메뉴를 끌어올 수 있는 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-146">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="4dffe-147">**HoloLens 관련 명령**</span><span class="sxs-lookup"><span data-stu-id="4dffe-147">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="4dffe-148">"이렇게 말 하세요~"</span><span class="sxs-lookup"><span data-stu-id="4dffe-148">"What can I say?"</span></span>
* <span data-ttu-id="4dffe-149">[시작 메뉴로](navigating-the-windows-mixed-reality-home.md#start-menu) 이동 하려면 [블 룸](system-gesture.md#bloom) 대신 "시작으로 이동"을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4dffe-149">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="4dffe-150">"시작 <app>"</span><span class="sxs-lookup"><span data-stu-id="4dffe-150">"Launch <app>"</span></span>
* <span data-ttu-id="4dffe-151">"여기 <app> 이동"</span><span class="sxs-lookup"><span data-stu-id="4dffe-151">"Move <app> here"</span></span>
* <span data-ttu-id="4dffe-152">"사진 찍기"</span><span class="sxs-lookup"><span data-stu-id="4dffe-152">"Take a picture"</span></span>
* <span data-ttu-id="4dffe-153">"기록 시작"</span><span class="sxs-lookup"><span data-stu-id="4dffe-153">"Start recording"</span></span>
* <span data-ttu-id="4dffe-154">"기록 중지"</span><span class="sxs-lookup"><span data-stu-id="4dffe-154">"Stop recording"</span></span>
* <span data-ttu-id="4dffe-155">"밝기 늘리기"</span><span class="sxs-lookup"><span data-stu-id="4dffe-155">"Increase the brightness"</span></span>
* <span data-ttu-id="4dffe-156">"밝기 낮추기"</span><span class="sxs-lookup"><span data-stu-id="4dffe-156">"Decrease the brightness"</span></span>
* <span data-ttu-id="4dffe-157">"볼륨 증가"</span><span class="sxs-lookup"><span data-stu-id="4dffe-157">"Increase the volume"</span></span>
* <span data-ttu-id="4dffe-158">"볼륨 낮추기"</span><span class="sxs-lookup"><span data-stu-id="4dffe-158">"Decrease the volume"</span></span>
* <span data-ttu-id="4dffe-159">"음소거" 또는 "음소거 해제"</span><span class="sxs-lookup"><span data-stu-id="4dffe-159">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="4dffe-160">"장치 종료"</span><span class="sxs-lookup"><span data-stu-id="4dffe-160">"Shut down the device"</span></span>
* <span data-ttu-id="4dffe-161">"장치 다시 시작"</span><span class="sxs-lookup"><span data-stu-id="4dffe-161">"Restart the device"</span></span>
* <span data-ttu-id="4dffe-162">"절전 모드로 전환"</span><span class="sxs-lookup"><span data-stu-id="4dffe-162">"Go to sleep"</span></span>
* <span data-ttu-id="4dffe-163">"시간 이란?"</span><span class="sxs-lookup"><span data-stu-id="4dffe-163">"What time is it?"</span></span>
* <span data-ttu-id="4dffe-164">"얼마나 많은 배터리가 남아 있나요?"</span><span class="sxs-lookup"><span data-stu-id="4dffe-164">"How much battery do I have left?"</span></span>



<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="4dffe-165">"이 항목을 참조 하세요."</span><span class="sxs-lookup"><span data-stu-id="4dffe-165">"See It, Say It"</span></span><br>
        <span data-ttu-id="4dffe-166">HoloLens에는 음성 입력에 대 한 "이를 확인 하는 것이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-166">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="4dffe-167">예를 들어 HoloLens (첫 번째 gen)에서 앱 창을 볼 때 사용자는 앱 바에 표시 되는 "조정" 명령을 사용 하 여 전 세계의 앱 위치를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-167">For example, when looking at an app window in HoloLens (1st gen), a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="4dffe-168">*이미지: 사용자가 앱 바에 표시 되는 "조정" 명령을 사용 하 여 앱의 위치를 조정할 수 있습니다.*</span><span class="sxs-lookup"><span data-stu-id="4dffe-168">*Image: A user can say the "Adjust" command which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="4dffe-169">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="4dffe-169">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="4dffe-170">![앱 창이 나 홀로그램을 볼 때 사용자가 앱 바에 표시 되는 "조정" 명령을 사용 하 여 전 세계의 앱 위치를 조정할 수 있습니다](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="4dffe-170">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::


<br>



:::row:::
    :::column:::
        <span data-ttu-id="4dffe-171">앱이이 규칙을 준수 하는 경우 사용자는 시스템을 제어 하는 내용을 쉽게 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-171">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="4dffe-172">이를 강화 하기 위해 HoloLens (첫 번째 gen)의 단추를 gazing 하는 동안 "음성 유지" 도구 설명이 표시 됩니다. 단추가 음성으로 사용 되는 경우 두 번째는 "음성 유지" 도구 설명이 표시 되 고이를 통해 "누르기"를 말하는 명령이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-172">To reinforce this, while gazing at a button in HoloLens (1st gen), you will see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="4dffe-173">HoloLens 2에서 음성 도구 설명을 표시 하려면 "선택" 또는 "설명 가능한 내용" (이미지 참조)을 설명 하 여 음성 커서를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-173">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="4dffe-174">*이미지: 단추 아래에 "표시 됩니다." 라고 표시 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="4dffe-174">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![단추 아래에 표시 되는 것을 확인 하세요.](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="4dffe-176">빠른 홀로그램 조작을 위한 음성 명령</span><span class="sxs-lookup"><span data-stu-id="4dffe-176">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="4dffe-177">한 번에 조작 작업을 빠르게 수행 하기 위해 홀로그램에서 gazing 하는 동안 많은 음성 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-177">There are a number of voice commands you can say while gazing at a hologram to quickly perform manipulation tasks.</span></span> <span data-ttu-id="4dffe-178">이러한 음성 명령은 응용 프로그램 창 뿐만 아니라 전 세계에 배치한 3D 개체에도 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-178">These voice commands work on app windows as well as 3D objects you have placed in the world.</span></span>

<span data-ttu-id="4dffe-179">**홀로그램 조작 명령**</span><span class="sxs-lookup"><span data-stu-id="4dffe-179">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="4dffe-180">얼굴 얼굴</span><span class="sxs-lookup"><span data-stu-id="4dffe-180">Face me</span></span>
* <span data-ttu-id="4dffe-181">크게 | 보강</span><span class="sxs-lookup"><span data-stu-id="4dffe-181">Bigger | Enhance</span></span>
* <span data-ttu-id="4dffe-182">짧은</span><span class="sxs-lookup"><span data-stu-id="4dffe-182">Smaller</span></span>

<span data-ttu-id="4dffe-183">HoloLens 2에서는 참조 하는 내용에 대 한 컨텍스트 정보를 암시적으로 제공 하는 눈에 잘 맞는 상호 작용을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-183">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="4dffe-184">예를 들어, 홀로그램을 확인 하 고 "배치" 라고 표시 한 다음 배치 하려는 위치를 확인 하 고 " _여기_ _에"를_표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-184">For example, you could simply look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="4dffe-185">또는 복잡 한 컴퓨터에서 holographic 파트를 살펴볼 수 있습니다. " _이_에 대 한 자세한 정보를 제공 합니다." 라고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-185">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>



## <a name="discovering-voice-commands"></a><span data-ttu-id="4dffe-186">음성 명령 검색</span><span class="sxs-lookup"><span data-stu-id="4dffe-186">Discovering voice commands</span></span>

<span data-ttu-id="4dffe-187">위의 빠른 조작을 위한 명령과 같은 일부 명령은 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-187">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="4dffe-188">사용할 수 있는 명령에 대 한 자세한 내용은 개체를 응시 하 고 "무엇을 할 수 있나요?" 라고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-188">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="4dffe-189">가능한 명령 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-189">A list of possible commands pops up.</span></span> <span data-ttu-id="4dffe-190">헤드 응시 커서를 사용 하 여 앞의 각 단추에 대 한 음성 도구 설명을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-190">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="4dffe-191">전체 목록을 원하는 경우 언제 든 지 "모든 명령 표시" 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-191">If you want a complete list, just say, "Show all commands" anytime.</span></span> 


## <a name="dictation"></a><span data-ttu-id="4dffe-192">받아쓰기</span><span class="sxs-lookup"><span data-stu-id="4dffe-192">Dictation</span></span>

<span data-ttu-id="4dffe-193">음성 받아쓰기는 [공기 탭](gaze-and-commit.md#composite-gestures)을 사용 하 여 입력 하는 대신 앱에 텍스트를 입력 하는 것이 더 효율적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-193">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="4dffe-194">이렇게 하면 사용자에 대해 더 짧은 노력으로 입력 속도를 크게 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-194">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="4dffe-195">음성 받아쓰기는 마이크 단추를 선택 하 여 시작 ![](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="4dffe-195">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="4dffe-196">*음성 받아쓰기는 키보드에서 마이크 단추를 선택 하 여 시작 합니다.*</span><span class="sxs-lookup"><span data-stu-id="4dffe-196">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="4dffe-197">Holographic 키보드가 활성화 될 때마다 입력 하는 대신 받아쓰기 모드로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-197">Any time the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="4dffe-198">텍스트 입력 상자의 측면에서 마이크를 선택 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-198">Select the microphone on the side of the text input box to get started.</span></span>


## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="4dffe-199">앱에 음성 명령 추가</span><span class="sxs-lookup"><span data-stu-id="4dffe-199">Adding voice commands to your app</span></span>

<span data-ttu-id="4dffe-200">빌드하는 모든 환경에 음성 명령을 추가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-200">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="4dffe-201">음성은 강력하고 편리한 방식으로 시스템 및 앱을 제어할 수 있는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-201">Voice is a powerful and convenient way control the system and apps.</span></span> <span data-ttu-id="4dffe-202">사용자는 다양한 언어 및 악센트를 사용하기 때문에 음성 키워드를 적절히 선택하면 사용자의 명령이 명확하게 해석될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-202">Because users speak with a variety of dialects and accents, proper choice of speech keywords will make sure that your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="4dffe-203">최선의 구현 방법</span><span class="sxs-lookup"><span data-stu-id="4dffe-203">Best practices</span></span>

<span data-ttu-id="4dffe-204">다음은 매끄러운 음성 인식에 도움이 될 수 있는 몇 가지 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-204">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="4dffe-205">**간결한 명령 사용** - 가능한 경우 두 개 이상의 음절로 이루어진 키워드를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-205">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="4dffe-206">1음절 단어는 악센트가 다른 사람이 말할 경우 다른 모음 소리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-206">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="4dffe-207">예: "비디오 재생"은 "현재 선택한 비디오 재생" 보다 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-207">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="4dffe-208">**간단한 어휘 사용** -예: "show note"는 "show 카드" 보다 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-208">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="4dffe-209">**비파괴적인 명령 사용** - 음성 명령으로 수행할 수 있는 모든 작업은 비파괴적이어야 하며, 사용자 근처에서 말하는 다른 사람이 실수로 명령을 트리거하는 경우 쉽게 실행 취소할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-209">**Make sure commands are non destructive** - Make sure any action that can be taken by a speech command is non destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="4dffe-210">**유사하게 들리는 명령 사용 금지** - 매우 비슷하게 들리는 여러 음성 명령을 등록하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-210">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound very similar.</span></span> <span data-ttu-id="4dffe-211">예: "자세히 표시" 및 "저장소 표시"는 매우 유사 하 게 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-211">Example: "Show more" and "Show store" can be very similar sounding.</span></span>
* <span data-ttu-id="4dffe-212">**사용하지 않을 경우 앱 등록 취소** - 앱에서 특정 음성 명령이 유효한 상태가 아닐 경우에는 다른 명령과 혼동되지 않도록 등록을 취소하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-212">**Unregister your app when not it use** - When your app is not in a state in which a particular speech command is valid, consider unregistering it so that other commands are not confused for that one.</span></span>
* <span data-ttu-id="4dffe-213">**다른 악센트로 테스트** - 다른 악센트의 사용자와 앱을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-213">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="4dffe-214">**음성 명령 일관성 유지** - "Go back"이라고 말할 경우 이전 페이지로 이동되면 애플리케이션에서 이 동작을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-214">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="4dffe-215">**시스템 명령 사용 방지** - 다음 음성 명령은 시스템용으로 예약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-215">**Avoid using system commands** - The following voice commands are reserved for the system.</span></span> <span data-ttu-id="4dffe-216">따라서 애플리케이션에서 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-216">These should not be used by applications.</span></span>
   * <span data-ttu-id="4dffe-217">"Hey Cortana"</span><span class="sxs-lookup"><span data-stu-id="4dffe-217">"Hey Cortana"</span></span>
   * <span data-ttu-id="4dffe-218">"Select"</span><span class="sxs-lookup"><span data-stu-id="4dffe-218">"Select"</span></span>
   * <span data-ttu-id="4dffe-219">"시작으로 이동"</span><span class="sxs-lookup"><span data-stu-id="4dffe-219">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="4dffe-220">음성 입력의 장점</span><span class="sxs-lookup"><span data-stu-id="4dffe-220">Advantages of voice input</span></span>

<span data-ttu-id="4dffe-221">음성 입력은 의도를 전달하는 자연스러운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-221">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="4dffe-222">음성 **은 인터페이스 탐색** 에 특히 유용 합니다. 사용자는 인터페이스의 여러 단계를 쉽게 수행할 수 있습니다 (사용자가 웹 페이지를 볼 때 응용 프로그램에서 뒤로 단추를 누르는 대신 "뒤로 이동" 이라고 말할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="4dffe-222">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface (a user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app).</span></span> <span data-ttu-id="4dffe-223">이러한 시간 절약은 사용자의 경험에 대 한 강력한 **감정적 효과** 를 제공 하 고 작은 양의 슈퍼 능력을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-223">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="4dffe-224">팔에 무언가를 잔뜩 들고 있거나 **멀티태스킹** 중일 때도 음성을 사용하는 것이 편리한 입력 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-224">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="4dffe-225">키보드에 입력 하는 것이 어려운 장치에서 **음성 받아쓰기** 는 텍스트를 입력 하는 효율적인 대체 방법이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-225">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="4dffe-226">마지막으로, 응시 및 제스처에 대 한 **정확도 범위가** 제한 되는 경우 음성은 사용자의 의도를 명확 하 게 구분 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-226">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="4dffe-227">**사용자에게 도움이 될 수 있는 음성 사용 방법**</span><span class="sxs-lookup"><span data-stu-id="4dffe-227">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="4dffe-228">시간 단축 - 보다 효율적으로 최종 목표에 도달할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-228">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="4dffe-229">최소의 노력 - 보다 유연하고 편리하게 작업할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-229">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="4dffe-230">인지 부담 감소 - 직관적이며 배우고 기억하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-230">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="4dffe-231">사회적으로 용인 가능 - 사회 규범을 벗어나지 않는 행동을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-231">It's socially acceptable - it should fit in with societal norms in terms of behavior.</span></span>
* <span data-ttu-id="4dffe-232">일상적임 - 음성이 습관적인 동작이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-232">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="4dffe-233">음성 입력에 대 한 문제</span><span class="sxs-lookup"><span data-stu-id="4dffe-233">Challenges for voice input</span></span>

<span data-ttu-id="4dffe-234">음성 입력은 다양 한 응용 프로그램에 적합 하지만 몇 가지 과제가 직면 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-234">While voice input is great for a lot of different applications, it also faces several challenges.</span></span> <span data-ttu-id="4dffe-235">음성 입력의 장점과 문제를 모두 이해 하면 앱 개발자가 음성 입력을 사용 하는 방법 및 시기를 보다 효율적으로 선택 하 고 사용자에 게 훌륭한 환경을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-235">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="4dffe-236">**연속 입력 컨트롤에 대 한 음성 입력** 세밀 한 제어가 그 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-236">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="4dffe-237">예를 들어 사용자가 음악 앱에서 볼륨을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-237">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="4dffe-238">단지 "큰" 라고 말할 수 있지만 시스템에서 볼륨을 만드는 것이 얼마나 큰 지는 확실 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-238">She can simply say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="4dffe-239">사용자는 "약간 더 크게 만들기" 라고 말할 수 있지만 "약간의"는 수량화 하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-239">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="4dffe-240">음성으로 holograms을 이동 하거나 크기를 조정 하는 것은 비슷하게 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-240">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="4dffe-241">**음성 입력 검색의 안정성** 음성 입력 시스템은 더 효과적이 고 더 나은 반면 음성 명령을 잘못 듣고 해석 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-241">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="4dffe-242">핵심은 시스템이 수신 대기 하는 경우 사용자에 게 피드백을 제공 하 여 응용 프로그램에서이 문제를 해결 하는 것이 고, 사용자를 올바르게 이해 하기 위해 잠재적인 문제를 명확 하 게 이해 하기 위해 시스템이 이해 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-242">The key is to address this challenge in your application by providing feedback to the user when the system is listening and what the system understood to create clarity on potential issues in correctly understanding the user.</span></span>  

<span data-ttu-id="4dffe-243">**공유 공간의 음성 입력** 음성은 다른 사용자와 공유 하는 공간에서 사회 공학적 허용 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-243">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="4dffe-244">다음은 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-244">Here are a few examples:</span></span>
* <span data-ttu-id="4dffe-245">사용자가 다른 사용자의 방해를 원하지 않을 수 있습니다 (예: 자동 라이브러리나 공유 사무실).</span><span class="sxs-lookup"><span data-stu-id="4dffe-245">The user may not want to disturb others (e.g., in a quiet library or shared office)</span></span>
* <span data-ttu-id="4dffe-246">사용자가 공개를 통해 자신에 게 표시 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-246">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="4dffe-247">사용자가 암호를 포함 하 여 개인 또는 기밀 메시지를 수신 하는 불편을 느낄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-247">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="4dffe-248">**고유 하거나 알 수 없는 단어의 음성 입력** 음성 입력의 어려움은 사용자가 시스템에서 알 수 없는 단어 (예: 애칭, 특정은 어 단어 또는 약어)를 받아쓰게 하는 경우에도 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-248">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words or abbreviations.</span></span> 

<span data-ttu-id="4dffe-249">**음성 명령 학습** 최종 목표는 시스템에서 자연스럽 게 자주 사용 되지만 앱이 미리 정의 된 특정 음성 명령을 계속 사용 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-249">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often times apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="4dffe-250">큰 음성 명령 집합과 관련 된 과제는 사용자를 오버 로드 하지 않고 사용자를 유지 하는 데 도움이 되는 방법을 설명 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-250">A challenge associated with a big set of voice commands is how to teach them without overloading the user and how to help the user to retain them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="4dffe-251">음성 피드백 상태</span><span class="sxs-lookup"><span data-stu-id="4dffe-251">Voice feedback states</span></span>

<span data-ttu-id="4dffe-252">음성이 제대로 적용되면 사용자는 **말할 수 있는 사항**을 이해하고 시스템이 **올바르게 알아 들었다는 명확한 피드백을 받게 됩니다**.</span><span class="sxs-lookup"><span data-stu-id="4dffe-252">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="4dffe-253">이러한 두 신호를 통해 사용자는 음성을 기본 입력으로 사용할 때 안심할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-253">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="4dffe-254">다음은 음성 입력이 인식될 때 커서에 나타나는 결과와 사용자에게 이러한 사실을 전달하는 방법을 보여 주는 다이어그램입니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-254">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="4dffe-255">1 ![합니다. 일반 커서 상태](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="4dffe-255">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="4dffe-256">**1. 일반 커서 상태**</span><span class="sxs-lookup"><span data-stu-id="4dffe-256">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="4dffe-257">![2. 음성 피드백을 전달 하 고 사라지면](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="4dffe-257">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="4dffe-258">**2. 음성 피드백을 전달 하 고 사라집니다.**</span><span class="sxs-lookup"><span data-stu-id="4dffe-258">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="4dffe-259">![\* 3입니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-259">![\*3.</span></span> <span data-ttu-id="4dffe-260">일반 커서 상태](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="4dffe-260">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="4dffe-261">**3. 일반 커서 상태로 돌아갑니다.**</span><span class="sxs-lookup"><span data-stu-id="4dffe-261">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="4dffe-262">혼합 현실에서 "음성"에 대해 알아야 할 주요 사항</span><span class="sxs-lookup"><span data-stu-id="4dffe-262">Top things users should know about "speech" in mixed reality</span></span>
* <span data-ttu-id="4dffe-263">단추를 타기팅할 때 **"Select"** 라고 말합니다(단추를 클릭하기 위해 어디에서나 사용할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="4dffe-263">Say **"Select"** while targeting a button (you can use this anywhere to click a button).</span></span>
* <span data-ttu-id="4dffe-264">일부 앱에서는 작업을 수행하기 위해 **label name of an app bar button**이라고 말할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-264">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="4dffe-265">예를 들어, 앱을 바라보면서 명령 "Remove"라고 말하여 작업 환경에서 해당 앱을 제거할 수 있습니다(손으로 클릭할 때모다 시간이 절감됨).</span><span class="sxs-lookup"><span data-stu-id="4dffe-265">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to click it with your hand).</span></span>
* <span data-ttu-id="4dffe-266">**"Hey Cortana"** 라고 말하여 Cortana가 청취를 시작하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-266">You can initiate Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="4dffe-267">질문을 하거나("Hey Cortana, how tall is the Eiffel tower"), 앱을 열도록 말하거나("Hey Cortana, open Netflix"), 시작 메뉴를 불러오도록 말할 수 있습니다("Hey Cortana, take me home").</span><span class="sxs-lookup"><span data-stu-id="4dffe-267">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="4dffe-268">음성에 대한 사용자의 일반적인 질문 및 어려움</span><span class="sxs-lookup"><span data-stu-id="4dffe-268">Common questions and concerns users have about voice</span></span>
* <span data-ttu-id="4dffe-269">무엇을 말할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="4dffe-269">What can I say?</span></span>
* <span data-ttu-id="4dffe-270">시스템이 내 말을 제대로 알아듣는지 어떻게 알 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="4dffe-270">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="4dffe-271">시스템이 내 음성 명령을 계속 잘못 알아듣습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-271">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="4dffe-272">음성 명령을 받아도 반응하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-272">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="4dffe-273">음성 명령을 제공할 때 잘못된 방식으로 반응합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-273">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="4dffe-274">특정 앱이나 앱 명령을 대상으로 음성 명령을 내리려면 어떻게 하나요?</span><span class="sxs-lookup"><span data-stu-id="4dffe-274">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="4dffe-275">음성을 사용해서 항목을 HoloLens의 홀로그래픽 프레임 밖으로 보낼 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="4dffe-275">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="4dffe-276">통신</span><span class="sxs-lookup"><span data-stu-id="4dffe-276">Communication</span></span>

<span data-ttu-id="4dffe-277">HoloLens에서 제공 하는 사용자 지정 된 오디오 입력 처리 옵션을 활용 하려는 응용 프로그램의 경우 앱에서 사용할 수 있는 다양 한 [오디오 스트림 범주](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) 를 이해 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-277">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it is important to understand the various [audio stream categories](https://msdn.microsoft.com/library/windows/desktop/hh404178(v=vs.85).aspx) your app can consume.</span></span> <span data-ttu-id="4dffe-278">Windows 10은 몇 가지 다른 스트림 범주를 지원 하 고, HoloLens는 이러한 세 가지를 사용 하 여 음성, 통신 및 주변 환경 오디오에 사용 될 수 있는 마이크 오디오 품질을 최적화 하기 위해 사용자 지정 처리를 사용 하도록 설정 합니다. (즉, "캠코더") 시나리오를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-278">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication and other which can be used for ambient environment audio capture (i.e. "camcorder") scenarios.</span></span>
* <span data-ttu-id="4dffe-279">AudioCategory_Communications stream 범주는 통화 품질 및 내레이션 시나리오에 맞게 사용자 지정 되며 클라이언트에 사용자 음성의 16kHz 24bit mono 오디오 스트림을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-279">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16kHz 24bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="4dffe-280">AudioCategory_Speech stream 범주는 HoloLens (Windows) 음성 엔진에 맞게 사용자 지정 되며 사용자 음성의 16kHz 24bit mono 스트림을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-280">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16kHz 24bit mono stream of the user's voice.</span></span> <span data-ttu-id="4dffe-281">이 범주는 필요한 경우 타사 음성 엔진에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-281">This category can be used by 3rd party speech engines if needed.</span></span>
* <span data-ttu-id="4dffe-282">AudioCategory_Other stream 범주는 주변 환경 오디오 녹음에 맞게 사용자 지정 되며 클라이언트에 48kHz 24 비트 스테레오 오디오 스트림을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-282">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48kHz 24 bit stereo audio stream.</span></span>

<span data-ttu-id="4dffe-283">이러한 오디오 처리는 모두 하드웨어 가속입니다. 즉, HoloLens CPU에서 동일한 처리가 수행 된 경우 보다 기능이 훨씬 더 많은 전력을 소모 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-283">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="4dffe-284">시스템 배터리 수명을 최대화 하 고 오프 로드 된 기본 제공 오디오 입력 처리 기능을 활용 하기 위해 CPU에서 기타 오디오 입력 처리를 실행 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-284">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="4dffe-285">언어</span><span class="sxs-lookup"><span data-stu-id="4dffe-285">Languages</span></span>

<span data-ttu-id="4dffe-286">HoloLens 2는 추가 언어도 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-286">HoloLens 2 also supports additional languages.</span></span> <span data-ttu-id="4dffe-287">음성 명령은 여러 키보드가 설치 되어 있거나 앱이 다른 언어로 음성 인식기를 만들려고 하는 경우에도 항상 시스템의 표시 언어로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-287">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="4dffe-288">문제 해결</span><span class="sxs-lookup"><span data-stu-id="4dffe-288">Troubleshooting</span></span>

<span data-ttu-id="4dffe-289">"Select" 및 "안녕하세요 Cortana"를 사용 하는 데 문제가 있는 경우 더 조용한 공간으로 이동 하거나, 소음의 원본에서 떨어진 곳으로 이동 하거나, 더 크게 말해 보세요.</span><span class="sxs-lookup"><span data-stu-id="4dffe-289">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="4dffe-290">지금은 HoloLens의 모든 음성 인식이 특별히 미국 영어의 기본 스피커로 조정 되 고 최적화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-290">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="4dffe-291">Windows Mixed Reality Developer Edition 릴리스 2017에서는 초기 HMD 연결 후 PC 데스크톱에 로그 아웃 했다가 다시 로그인 한 후 오디오 끝점 관리 논리가 정상적으로 작동 합니다 (계속).</span><span class="sxs-lookup"><span data-stu-id="4dffe-291">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="4dffe-292">WMR OOBE를 통과 한 후 첫 번째 로그 아웃 이벤트 이전에는 사용자가 HMD를 처음으로 연결 하기 전에 설정 된 방법에 따라 오디오 없음에서 오디오 전환 없이 다양 한 오디오 기능 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-292">Prior to that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up prior to connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="4dffe-293">Unity 용 MRTK (Mixed Reality Toolkit)의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="4dffe-293">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="4dffe-294">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** 를 사용 하면 개체에 음성 명령을 쉽게 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-294">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="4dffe-295">MRTK의 **음성 입력 프로필** 을 사용 하 여 키워드를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-295">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="4dffe-296">**SpeechInputHandler** 스크립트를 할당 하 여 음성 입력 프로필에 정의 된 키워드에 대 한 모든 개체 응답을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-296">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="4dffe-297">또한 SpeechInputHandler는 사용자의 신뢰도를 높이기 위해 음성 확인 레이블을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4dffe-297">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="4dffe-298">MRTK-음성 명령</span><span class="sxs-lookup"><span data-stu-id="4dffe-298">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)


---

## <a name="see-also"></a><span data-ttu-id="4dffe-299">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4dffe-299">See also</span></span>
* [<span data-ttu-id="4dffe-300">응시 및 커밋</span><span class="sxs-lookup"><span data-stu-id="4dffe-300">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="4dffe-301">Instinctual 상호 작용</span><span class="sxs-lookup"><span data-stu-id="4dffe-301">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="4dffe-302">MR 입력 212: 음성</span><span class="sxs-lookup"><span data-stu-id="4dffe-302">MR Input 212: Voice</span></span>](holograms-212.md)
* [<span data-ttu-id="4dffe-303">DirectX의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="4dffe-303">Voice input in DirectX</span></span>](voice-input-in-directx.md)
* [<span data-ttu-id="4dffe-304">Unity의 음성 입력</span><span class="sxs-lookup"><span data-stu-id="4dffe-304">Voice input in Unity</span></span>](voice-input-in-unity.md)
