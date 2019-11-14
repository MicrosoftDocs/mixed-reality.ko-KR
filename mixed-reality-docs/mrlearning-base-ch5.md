---
title: 자습서 시작-6. 고급 입력 옵션 탐색
description: 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: b740c463e3d73d5df9b996562e9ff0a1952703f0
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064312"
---
# <a name="6-exploring-advanced-input-options"></a><span data-ttu-id="768a8-105">6. 고급 입력 옵션 탐색</span><span class="sxs-lookup"><span data-stu-id="768a8-105">6. Exploring advanced input options</span></span>

<span data-ttu-id="768a8-106">이 자습서에서는 음성 명령, 패닝 제스처 및 눈 추적 사용을 포함 하 여 HoloLens 2에 대 한 몇 가지 고급 입력 옵션을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-106">In this tutorial, several advanced input options for HoloLens 2 are explored, including the use of voice commands, panning gesture, and eye tracking.</span></span> 

## <a name="objectives"></a><span data-ttu-id="768a8-107">목표</span><span class="sxs-lookup"><span data-stu-id="768a8-107">Objectives</span></span>

- <span data-ttu-id="768a8-108">음성 명령 및 키워드를 사용 하 여 이벤트 트리거</span><span class="sxs-lookup"><span data-stu-id="768a8-108">Trigger events using voice commands and keywords</span></span>
- <span data-ttu-id="768a8-109">추적 된 손을 사용 하 여 추적 된 손으로 텍스처 및 3D 개체를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-109">Use tracked hands to pan textures and 3D objects with tracked hands</span></span>
- <span data-ttu-id="768a8-110">HoloLens 2 눈동자 추적 기능을 활용 하 여 개체 선택</span><span class="sxs-lookup"><span data-stu-id="768a8-110">Leverage HoloLens 2 eye tracking capabilities to select objects</span></span>

## <a name="instructions"></a><span data-ttu-id="768a8-111">지침</span><span class="sxs-lookup"><span data-stu-id="768a8-111">Instructions</span></span>

### <a name="enabling-voice-commands"></a><span data-ttu-id="768a8-112">음성 명령 사용</span><span class="sxs-lookup"><span data-stu-id="768a8-112">Enabling Voice Commands</span></span>

<span data-ttu-id="768a8-113">이 섹션에는 두 개의 음성 명령이 구현 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-113">In this section, two voice commands are implemented.</span></span> <span data-ttu-id="768a8-114">먼저 "진단 설정/해제"를 말하여 프레임 주기 진단 패널을 전환 하는 기능이 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-114">First, the ability to toggle the frame rate diagnostics panel is introduced by saying "toggle diagnostics".</span></span> <span data-ttu-id="768a8-115">둘째, 음성 명령으로 소리를 재생 하는 기능을 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-115">Second, the ability to play a sound with a voice command is explored.</span></span> <span data-ttu-id="768a8-116">음성 명령 구성을 담당 하는 MRTK 프로필 및 설정이 먼저 검토 됩니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-116">The MRTK profiles and settings responsible for configuring voice commands is reviewed first.</span></span>

1. <span data-ttu-id="768a8-117">BaseScene 계층 구조에서 MixedRealityToolkit을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-117">In the BaseScene hierarchy, select MixedRealityToolkit.</span></span> <span data-ttu-id="768a8-118">그런 다음 검사기 패널에서 입력을 선택 하 고 DefaultMixedRealityInputSystemProfile 왼쪽의 작은 복제 단추를 클릭 하 여 프로필 복제 팝업을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-118">Then, in the Inspector panel, select Input and click the small Clone button to the left of the DefaultMixedRealityInputSystemProfile to open the Clone Profile popup.</span></span> <span data-ttu-id="768a8-119">팝업에서 복제를 클릭 하 여 새 프로필 MixedRealityInputSystemProfile를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-119">In the popup click Clone to create a new profile MixedRealityInputSystemProfile.</span></span>

    ![mrlearning-base-ch5-1-step1a](images/mrlearning-base-ch5-1-step1a.png)

    <span data-ttu-id="768a8-121">그러면 새로 만든 MixedRealityInputSystemProfile로 MixedRealityToolkitConfigurationProfile 자동으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-121">This will also auto-populate the MixedRealityToolkitConfigurationProfile with the newly created MixedRealityInputSystemProfile.</span></span>

    ![mrlearning-base-ch5-1-step1b](images/mrlearning-base-ch5-1-step1b.png)

2. <span data-ttu-id="768a8-123">입력 시스템 프로필에는 다양 한 설정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-123">In the input system profile, there are a variety of settings.</span></span> <span data-ttu-id="768a8-124">음성 명령의 경우 음성 섹션을 확장 하 고 이전 단계와 동일한 프로세스를 수행 하 여 DefaultMixedRealitySpeechCommandsProfile를 복제 하 고 편집 가능한 고유한 복사본으로 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-124">For voice commands, expand the Speech section and follow the same process as in the previous step to clone the DefaultMixedRealitySpeechCommandsProfile and replace it with your own editable copy.</span></span>

    ![mrlearning-base-ch5-1-step2](images/mrlearning-base-ch5-1-step2.png)

    <span data-ttu-id="768a8-126">음성 명령 프로필에서 설정 범위를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-126">In the speech command profile, you’ll notice a range of settings.</span></span> <span data-ttu-id="768a8-127">이러한 설정에 대 한 자세한 내용은 [Mrtk speech 설명서](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="768a8-127">For a full description of these settings, refer to the [MRTK speech documentation](<https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html>).</span></span>

    <span data-ttu-id="768a8-128">기본적으로 일반 동작은 자동 시작입니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-128">By default, the general behavior is auto-start.</span></span> <span data-ttu-id="768a8-129">원하는 경우 수동 시작으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-129">This can be changed to manual-start, if desired.</span></span> <span data-ttu-id="768a8-130">그러나이 예에서는이를 자동 시작으로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-130">But for this example, keep it on auto-start.</span></span> <span data-ttu-id="768a8-131">MRTK는 메뉴, 진단 설정/해제, 프로파일러 전환 등의 몇 가지 기본 음성 명령과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-131">The MRTK comes with several default voice commands, such as menu, toggle diagnostics and toggle profiler.</span></span> <span data-ttu-id="768a8-132">진단 프레임 속도 카운터를 설정 및 해제 하기 위해 "진단 설정/해제" 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-132">We will use the keyword “toggle diagnostics,” in order to turn on and off the diagnostics framerate counter.</span></span> <span data-ttu-id="768a8-133">또한 아래 단계에서는 새 음성 명령을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-133">We will also add a new voice command in the steps below.</span></span>

3. <span data-ttu-id="768a8-134">새 음성 명령을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-134">Add a new voice command.</span></span> <span data-ttu-id="768a8-135">이렇게 하려면 + 새 음성 추가 명령 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-135">To do this, click the + Add a New Speech Command button.</span></span> <span data-ttu-id="768a8-136">기존 음성 명령 목록 아래에 새 줄이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-136">You'll see a new line that appears below the list of existing voice commands.</span></span> <span data-ttu-id="768a8-137">사용할 음성 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-137">Type the voice command you want to use.</span></span> <span data-ttu-id="768a8-138">이 예제에서는 "음악 재생" 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-138">In this example, use the command “play music".</span></span>

    ![mrlearning-base-ch5-1-step3](images/mrlearning-base-ch5-1-step3.png)

    >[!NOTE]
    ><span data-ttu-id="768a8-140">또한 음성 명령의 키코드도 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-140">You can also set a keycode for speech commands.</span></span> <span data-ttu-id="768a8-141">그러면 음성 명령이 키보드 키를 누를 때 이벤트를 트리거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-141">This allows for voice commands to trigger events upon the press of a keyboard key.</span></span>

4. <span data-ttu-id="768a8-142">음성 명령에 응답하는 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-142">Add the ability to respond to voice commands.</span></span> <span data-ttu-id="768a8-143">BaseScene 계층에서 다른 입력 스크립트가 연결 되지 않은 개체 (예: MixedRealityPlayspace game 개체)를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-143">Select any object in the BaseScene hierarchy that does not have any other input scripts attached to it, for example, the MixedRealityPlayspace game object.</span></span> <span data-ttu-id="768a8-144">검사기 패널에서 구성 요소 추가를 클릭 하 고, "speech"를 검색 하 고, 음성 입력 처리기 스크립트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-144">In the Inspector panel, click Add Component, search for "speech", and select the Speech Input Handler script.</span></span>

    ![mrlearning-base-ch5-1-step4](images/mrlearning-base-ch5-1-step4.png)

    <span data-ttu-id="768a8-146">기본적으로 두 개의 확인란이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-146">By default, you will see two checkboxes.</span></span> <span data-ttu-id="768a8-147">하나는 포커스 필요 확인란입니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-147">One is the Is Focus Required checkbox.</span></span> <span data-ttu-id="768a8-148">따라서 광선-응시, 헤드-응시, 컨트롤러-응시 또는 핸드 응시를 사용 하 여 개체를 가리키면 음성 명령이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-148">So, as long as you are pointing at the object with a ray-eye-gaze, head-gaze, controller-gaze, or hand-gaze, the voice command will be triggered.</span></span> <span data-ttu-id="768a8-149">사용자가 개체를 확인 하 여 음성 명령을 사용할 필요가 없도록 하려면이 확인란의 선택을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-149">Uncheck this checkbox so that the user does not have to look at the object to use the voice command.</span></span>

5. <span data-ttu-id="768a8-150">음성 명령에 응답하는 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-150">Add the ability to respond to a voice command.</span></span> <span data-ttu-id="768a8-151">이렇게 하려면 음성 입력 처리기에 있는 + 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-151">To do this, click the + button that’s in the Speech Input Handler.</span></span>

    ![mrlearning-base-ch5-1-step5](images/mrlearning-base-ch5-1-step5.png)

6. <span data-ttu-id="768a8-153">키워드 옆에 드롭다운 메뉴가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-153">Next to Keyword, you'll see a dropdown menu.</span></span> <span data-ttu-id="768a8-154">사용자에 게 "진단 설정/해제" 라는 구가 표시 될 때마다 작업을 트리거하면 진단 설정/해제를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-154">Select Toggle Diagnostics so that whenever the user says the phrase “toggle diagnostics”, it triggers an action.</span></span> <span data-ttu-id="768a8-155">옆의 화살표를 눌러 요소 0을 확장 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-155">Note that you might need to expand Element 0 by pressing the arrow next to it.</span></span>

    ![mrlearning-base-ch5-1-step6](images/mrlearning-base-ch5-1-step6.png)

    >[!NOTE]
    ><span data-ttu-id="768a8-157">이러한 키워드는 3 단계에서 편집한 프로필을 기반으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-157">These keywords are populated, based on the profile you edited in the step 3.</span></span>

7. <span data-ttu-id="768a8-158">진단 시스템 음성 컨트롤 스크립트를 추가 하 여 프레임 속도 카운터 진단을 설정/해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-158">Add the Diagnostics System Voice Controls script to toggle the framerate counter diagnostic on and off.</span></span> <span data-ttu-id="768a8-159">이렇게 하려면 구성 요소 추가를 누르고 진단 시스템 음성 컨트롤 스크립트를 검색 한 다음 메뉴에서 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-159">To do this, press Add Component, search for Diagnostics System Voice Controls script and add it from the menu.</span></span> <span data-ttu-id="768a8-160">이 스크립트를 어떤 개체에도 추가할 수 있지만 편의상, 음성 입력 처리기와 동일한 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-160">This script can be added to any object, but for simplicity, we will add it to the same object as the speech input handler.</span></span>

    ![mrlearning-base-ch5-1-step7](images/mrlearning-base-ch5-1-step7.png)

8. <span data-ttu-id="768a8-162">음성 입력 처리기에 새 응답을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-162">Add a new response in the speech input handler.</span></span> <span data-ttu-id="768a8-163">이렇게 하려면 "+" 아이콘을 클릭 하 여 응답 목록에 새 응답을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-163">To do this, click the "+" icon to add a new response to the response list.</span></span>

    ![mrlearning-base-ch5-1-step8](images/mrlearning-base-ch5-1-step8.png)

9. <span data-ttu-id="768a8-165">진단 시스템 음성 컨트롤 스크립트를 포함 하는 개체를 이전 단계에서 방금 만든 새 응답으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-165">Drag the object that has the Diagnostics System Voice Controls script to the new response you just created in the previous step.</span></span>

    ![mrlearning-base-ch5-1-step9](images/mrlearning-base-ch5-1-step9.png)

10. <span data-ttu-id="768a8-167">함수 드롭다운 (함수 없음), 진단 시스템 음성 컨트롤을 차례로 클릭 하 고 진단을 설정/해제 하는 ToggleDiagnostics () 함수를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-167">Click the function dropdown (where it says No Function), then Diagnostics System Voice Controls, and select the ToggleDiagnostics () function which toggles your diagnostics on and off.</span></span>

    ![mrlearning-base-ch5-1-step10](images/mrlearning-base-ch5-1-step10.png)

    >[!IMPORTANT]
    > <span data-ttu-id="768a8-169">장치를 빌드하기 전에 mic 설정을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-169">Before building to your device, you need to enable mic settings.</span></span> <span data-ttu-id="768a8-170">이렇게 하려면 파일을 클릭 하 고 빌드 설정, 플레이어 설정으로 이동 하 여 마이크 기능이 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-170">To do this, click File and go to Build Settings, Player Settings and ensure that the microphone capability is set.</span></span>

    <span data-ttu-id="768a8-171">다음으로, Octa 개체를 사용 하 여 음성 명령에서 오디오 파일을 재생 하는 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-171">Next, add the ability to play an audio file from voice command using the Octa object.</span></span> <span data-ttu-id="768a8-172">[4 단원](mrlearning-base-ch4.md) 에서 Octa 개체를 터치 하 여 오디오 클립을 재생 하는 기능이 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-172">Recall from [lesson 4](mrlearning-base-ch4.md) that the ability to play an audio clip from touching the Octa object was added.</span></span> <span data-ttu-id="768a8-173">음악 음성 명령에 대해서도 이 동일한 오디오 원본을 활용합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-173">We will leverage this same audio source for our music voice command.</span></span>

11. <span data-ttu-id="768a8-174">BaseScene 계층 구조에서 Octa 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-174">Select the Octa object in the BaseScene hierarchy.</span></span>

12. <span data-ttu-id="768a8-175">Octa 개체를 사용 하 여 다른 음성 입력 처리기를 추가 합니다 (4 단계와 5 단계 반복).</span><span class="sxs-lookup"><span data-stu-id="768a8-175">Add another speech input handler (repeat Steps 4 and 5), but with the octa object.</span></span>

13. <span data-ttu-id="768a8-176">6 단계에서 진단 음성 전환 명령을 추가 하는 대신 아래 이미지에 표시 된 것 처럼 음악 재생 음성 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-176">Instead of adding the Toggle Diagnostics voice command from step 6, add the Play Music voice command as shown in the image below.</span></span>

    ![mrlearning-base-ch5-1-step13](images/mrlearning-base-ch5-1-step13.png)

14. <span data-ttu-id="768a8-178">8 단계와 9 단계에서와 같이 새 응답을 추가 하 고 Octa 개체, 진단 시스템의 Voice Controls 스크립트를 포함 하는 개체를 빈 응답 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-178">As with Steps 8 and 9, add a new response and drag the Octa object, the object that has the Diagnostics System Voice Controls script on it, to the empty response slot.</span></span>

15. <span data-ttu-id="768a8-179">함수 없음 이라는 드롭다운 메뉴를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-179">Select the dropdown menu that says No Function.</span></span> <span data-ttu-id="768a8-180">그런 다음 오디오 원본과 PlayOneShot (오디오 클립)를 차례로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-180">Then select Audio Source, followed by PlayOneShot (AudioClip).</span></span>

    ![Lesson5 Chapter1 Step15im](images/Lesson5_chapter1_step15im.PNG)

16. <span data-ttu-id="768a8-182">이 예에서는 [4 단원](mrlearning-base-ch4.md)에서와 동일한 오디오 클립을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-182">For this example, we are going to use the same audio clip from [Lesson 4](mrlearning-base-ch4.md).</span></span> <span data-ttu-id="768a8-183">프로젝트 패널로 이동 하 여 "MRTK_Gem" 오디오 클립을 검색 하 고 아래 이미지에 표시 된 것 처럼 오디오 원본 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-183">Go into your Project panel, search for “MRTK_Gem” audio clip and drag it into the audio source slot as shown in the image below.</span></span> <span data-ttu-id="768a8-184">이제 응용 프로그램은 "진단 설정/해제" 음성 명령에 응답 하 여 프레임 전송률 카운터 패널을 전환 하 고 음악을 재생 하 여 MRTK_Gem 노래를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-184">Now your application will respond to the voice commands “toggle diagnostics” to toggle the Frame Rate Counter panel and Play Music to play the MRTK_Gem song.</span></span>

    ![Lesson5 Chapter1.txt Step16im](images/Lesson5_chapter1_step16im.PNG)

### <a name="the-pan-gesture"></a><span data-ttu-id="768a8-186">이동 제스처</span><span class="sxs-lookup"><span data-stu-id="768a8-186">The Pan Gesture</span></span>

<span data-ttu-id="768a8-187">이 섹션에서는 이동 제스처를 사용 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-187">In this section, you will learn how to use the pan gesture.</span></span> <span data-ttu-id="768a8-188">이 기능은 손가락 또는 손 모양으로 스크롤 하 여 콘텐츠를 스크롤 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-188">This is useful for scrolling by using your finger or hand to scroll through content.</span></span> <span data-ttu-id="768a8-189">이동 제스처를 사용 하 여 개체를 회전 하거나, 3D 개체의 컬렉션을 순환 하거나, 2D UI를 스크롤할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-189">You can also use the pan gesture to rotate objects, cycle through a collection of 3D objects, or even to scroll a 2D UI.</span></span>

1. <span data-ttu-id="768a8-190">쿼드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-190">Create a quad.</span></span> <span data-ttu-id="768a8-191">BaseScene 계층 구조에서를 마우스 오른쪽 단추로 클릭 하 고 "3D 개체"를 선택한 다음 4를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-191">In your BaseScene hierarchy, right-click, select "3D Object" followed by Quad.</span></span>

    ![Lesson5 Chapter2 Step2im](images/Lesson5_chapter2_step2im.PNG)

2. <span data-ttu-id="768a8-193">필요에 따라 쿼드의 위치를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-193">Reposition the quad, as appropriate.</span></span> <span data-ttu-id="768a8-194">이 예에서는 HoloLens 2에서 편안 하 게 배치 하기 위해 카메라에서 x = 0, y = 0 및 z = 1.5을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-194">For our example, we set the x = 0, the y = 0 and the z = 1.5 away from the camera for a comfortable position from HoloLens 2.</span></span>

    >[!NOTE]
    ><span data-ttu-id="768a8-195">이전 단원에서 4 개의 블록이 나 이전 단원에서 가져온 내용 앞에 있는 경우 다른 개체를 차단 하지 않도록 이동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-195">If the quad blocks or is in front of any content from the previous lessons, be sure to move it so that it doesn’t block any of the other objects.</span></span>

3. <span data-ttu-id="768a8-196">쿼드에 재질을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-196">Apply a material to the quad.</span></span> <span data-ttu-id="768a8-197">이 자료는 이동 제스처로 스크롤할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-197">This material will be what we will be scrolling through with the pan gesture.</span></span>

    ![Lesson5 Chapter2 Step3im](images/Lesson5_chapter2_step3im.PNG)

4. <span data-ttu-id="768a8-199">프로젝트 패널에서 검색 상자에 "이동 콘텐츠"를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-199">In your Projects panel, type “pan content” in the Search box.</span></span> <span data-ttu-id="768a8-200">해당 자료를 장면에서 쿼드로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-200">Drag that material onto the quad in your scene.</span></span>

    >[!NOTE]
    ><span data-ttu-id="768a8-201">이 판 콘텐츠 자료는 MRTK의 일부가 아니지만 이전 단원에서 가져온 BaseModuleAssets 자산에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-201">The PanContent material is not part of MRTK but included with the BaseModuleAssets asset imported in the previous lesson.</span></span>

    <span data-ttu-id="768a8-202">이동 제스처를 사용하려면 개체에 충돌체(collider)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-202">To use the pan gesture, you will need a collider on your object.</span></span> <span data-ttu-id="768a8-203">쿼드에 이미 메시 충돌체(collider)가 있는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-203">You may see the quad already has a mesh collider.</span></span> <span data-ttu-id="768a8-204">그러나 메시 충돌체(collider)는 너무 얇아서 선택하기 어려우므로 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-204">However, the mesh collider is not ideal, because it is extremely thin and difficult to select.</span></span> <span data-ttu-id="768a8-205">메시 충돌체(collider)를 상자 충돌체(collider)와 바꾸는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-205">We suggest replacing the mesh collider with a box collider.</span></span>

5. <span data-ttu-id="768a8-206">검사기 패널에서 쿼드에 있는 메시 collider를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-206">Right-click the mesh collider that’s on the quad from the Inspector panel.</span></span> <span data-ttu-id="768a8-207">그런 다음 구성 요소 제거를 클릭 하 여 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-207">Then remove it by clicking Remove Component.</span></span>

    ![Lesson5 Chapter2 Step5im](images/Lesson5_chapter2_step5im.PNG)

6. <span data-ttu-id="768a8-209">이제 구성 요소 추가를 클릭 하 고 "box collider"를 검색 하 여 상자 collider를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-209">Now add the box collider by clicking Add Component and searching “box collider”.</span></span> <span data-ttu-id="768a8-210">기본 추가 된 상자 collider는 여전히 너무 씬 이므로 클릭 하 여 편집 하려면 Collider 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-210">The default added box collider is still too thin, so click the Edit Collider button to edit.</span></span> <span data-ttu-id="768a8-211">이 단추를 눌러 장면 편집기에서 x, y 및 z 값이나 요소를 사용하여 크기를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-211">When it’s pressed in, you can adjust the size using the x, y and z values or the elements in the scene editor.</span></span> <span data-ttu-id="768a8-212">이 예제에서는 쿼드 약간 뒤로 상자 충돌체(collider)를 확장하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-212">For our example, we want to extend the box collider a little behind the quad.</span></span> <span data-ttu-id="768a8-213">장면 편집기에서 뒤쪽의 상자 충돌체(collider)를 바깥쪽으로 끕니다(아래 이미지 참조).</span><span class="sxs-lookup"><span data-stu-id="768a8-213">In the scene editor, drag the box collider from the back, outwards (see the image below).</span></span> <span data-ttu-id="768a8-214">이렇게 하면 사용자가 손가락을 사용할 수 있을 뿐 아니라 스크롤 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-214">This lets the user not only use their finger, but their entire hand to scroll.</span></span>

    ![Lesson5 Chapter2 Step6im](images/Lesson5_chapter2_step6im.PNG)

7. <span data-ttu-id="768a8-216">대화형으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-216">Make it interactive.</span></span> <span data-ttu-id="768a8-217">쿼드와 직접 상호 작용 하려고 하므로 4 단원에서 사용 했던 거의 상호 작용 Touchable 구성 요소를 사용 하 여 Octa 개체에서 음악을 재생 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-217">Since we want to interact with the quad directly, we want to use the Near Interaction Touchable component that we used this in Lesson 4 for playing music from the Octa object.</span></span> <span data-ttu-id="768a8-218">구성 요소 추가를 클릭 하 고, "near 인터랙션 touchable"를 검색 하 여 아래 이미지에 표시 된 것 처럼 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-218">Click Add Component, search for “near interaction touchable” and select it as shown in the images below.</span></span>

    ![mrlearning-base-ch5-2-step7a](images/mrlearning-base-ch5-2-step7a.png)

    <span data-ttu-id="768a8-220">상자 Collider의 크기 및/또는 가운데와 일치 하지 않는 범위 및/또는 가운데에 대 한 노란색 경고가 표시 되 면 범위 고정 및/또는 수정 센터 단추를 클릭 하 여 중심과 범위 값을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-220">If you see a yellow warning about bounds and/or center not matching the BoxCollider's size and/or center, click the Fix Bounds and/or Fix Center buttons to update the center and bounds values.</span></span>

    ![mrlearning-base-ch5-2-step7b](images/mrlearning-base-ch5-2-step7b.png)

8. <span data-ttu-id="768a8-222">이동 제스처를 인식하는 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-222">Add the ability to recognize the pan gesture.</span></span> <span data-ttu-id="768a8-223">구성 요소 추가를 클릭 하 고 검색 필드에 "직접 상호 작용"을 입력 한 다음 직접 상호 작용 팬 확대/축소 스크립트 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-223">Click Add Component, type “hand interaction” in the search field and add the Hand Interaction Pan Zoom script component.</span></span>

    ![mrlearning-base-ch5-2-step8a](images/mrlearning-base-ch5-2-step8a.png)

    <span data-ttu-id="768a8-225">그리고이를 사용 하는 경우에는 팬 사용 쿼드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-225">And with that, you have a pan-enabled quad.</span></span>

    <span data-ttu-id="768a8-226">여기에서 볼 수 있듯이 수동 상호 작용 이동 확대/축소 스크립트 구성 요소에는 다양 한 설정이 포함 되어 있습니다 (선택 사항).</span><span class="sxs-lookup"><span data-stu-id="768a8-226">As you can see, the Hand Interaction Pan Zoom script component has various settings, as an optional exercise, feel free to play around with them.</span></span>

    ![mrlearning-base-ch5-2-step8b](images/mrlearning-base-ch5-2-step8b.png)

9. <span data-ttu-id="768a8-228">다음으로, 3D 개체를 이동하는 방법을 알아보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-228">Next, we will learn how to pan 3D objects.</span></span>

    <span data-ttu-id="768a8-229">계층에서 4 개의 개체를 마우스 오른쪽 단추로 클릭 하 여 상황별 팝업 메뉴를 열고 **3D 개체** > **큐브** 를 선택 하 여 장면에 큐브를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-229">In the Hierarchy, right-click the Quad object, to open the contextual popup menu, then select **3D Object** > **Cube** to add a cube to your scene.</span></span>

    <span data-ttu-id="768a8-230">큐브의 **위치가** _0, 0, 0_ 으로 설정 되어 있는지 확인 합니다 .이는 쿼드에서 깔끔하게 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-230">Ensure the Cube's **Position** is set to  _0, 0, 0_ so it's positioned neatly within the Quad.</span></span> <span data-ttu-id="768a8-231">큐브를 _0.1, 0.1, 0.1_의 **배율로** 축소 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-231">Scale the Cube down to a **Scale** of _0.1, 0.1, 0.1_.</span></span>

    ![mrlearning-base-ch5-2-step9](images/mrlearning-base-ch5-2-step9.png)

    <span data-ttu-id="768a8-233">큐브를 마우스 오른쪽 단추로 클릭 하 여 큐브를 세 번 복제 하 고, 상황별 팝업 메뉴를 열고, **복제**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-233">Duplicate the Cube three times by right-clicking the Cube, to open the contextual popup menu, and selecting **Duplicate**.</span></span>

    <span data-ttu-id="768a8-234">큐브를 균등 하 게 분할 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-234">Space the cubes out evenly.</span></span> <span data-ttu-id="768a8-235">장면이 아래 이미지와 유사 하 게 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-235">Your scene should look similar to the image below.</span></span>

10. <span data-ttu-id="768a8-236">CTRL 키를 누른 채 계층 패널에서 각 **큐브** 개체를 선택 하 여 모든 큐브에 MoveWithPan 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-236">Add the MoveWithPan script to all the cubes by holding down the CTRL key while selecting each **Cube** object in the Hierarchy panel.</span></span> <span data-ttu-id="768a8-237">검사기 패널에서 구성 요소 추가를 클릭 하 고, 이동 하 여 **이동** 스크립트를 검색 하 고 선택 하 여 모든 큐브에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-237">In the Inspector panel, click Add Component, and search for and select the **Move With Pan** script to add it to all the cubes.</span></span>

    ![mrlearning-base-ch5-2-step10a](images/mrlearning-base-ch5-2-step10a.png)

    >[!NOTE]
    ><span data-ttu-id="768a8-239">MoveWithPan 스크립트는 MRTK의 일부가 아니지만 이전 단원에서 가져온 BaseModuleAssets 자산에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-239">The MoveWithPan script is not part of MRTK but included with the BaseModuleAssets asset imported in the previous lesson.</span></span>

    <span data-ttu-id="768a8-240">큐브를 선택한 상태에서 계층 패널의 **네** 번째 개체를 이동 **하 여 이동** 스크립트 구성 요소의 이동 **입력 원본** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-240">With the cubes still selected, drag the **Quad** object from the Hierarchy panel into the **Pan Input Source** field of the **Move With Pan** script component.</span></span>

    ![mrlearning-base-ch5-2-step10b](images/mrlearning-base-ch5-2-step10b.png)

    <span data-ttu-id="768a8-242">이제 큐브는 이동 제스처로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-242">Now, the cubes will move with your pan gesture.</span></span>

    >[!TIP]
    ><span data-ttu-id="768a8-243">각 큐브의 MoveWithPan 인스턴스는 각 큐브의 이동 입력 원본 필드에 추가 되 고 해당 큐브 개체의 위치를 적절 하 게 업데이트 하는 쿼드 개체의 HandInteractionPanZoom 인스턴스에서 보낸가 중 업데이트 된 이벤트를 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-243">The MoveWithPan instance on each cube listens for the PanUpdated event sent from the HandInteractionPanZoom instance on the Quad object, that we added to the Pan Input Source field on each of the cubes, and updates the respective cube object's position accordingly.</span></span>

    <span data-ttu-id="768a8-244">큐브를 선택한 상태에서 z 축을 따라 앞으로 이동 하면 **z** 값을 _0.7_로 변경 하 여 각 큐브의 메쉬가 **4** **상자 Collider** 안에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-244">With the cubes still selected, move them forward along their Z axis so each cube's mesh is inside the **Quad**'s **Box Collider** by changing their **Position Z** values to _0.7_.</span></span>

    ![mrlearning-base-ch5-2-step10c](images/mrlearning-base-ch5-2-step10c.png)

    <span data-ttu-id="768a8-246">이제 검사기 패널에서 검사를 취소 하 여 **쿼드**의 **메시 렌더러** 구성 요소를 사용 하지 않도록 설정 하면 3d 개체 목록을 통해 이동할 수 있는 보이지 않는 쿼드이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-246">Now, if you disable the **Quad**'s **Mesh Renderer** component by un-checking it in the Inspector panel, you will have an invisible quad where you can pan through a list of 3D objects.</span></span>

    ![mrlearning-base-ch5-2-step10d](images/mrlearning-base-ch5-2-step10d.png)

### <a name="eye-tracking"></a><span data-ttu-id="768a8-248">시선 추적</span><span class="sxs-lookup"><span data-stu-id="768a8-248">Eye Tracking</span></span>

<span data-ttu-id="768a8-249">이 섹션에서는 데모에서 눈 추적을 사용 하도록 설정 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-249">In this section, we will explore how to enable eye tracking in our demo.</span></span> <span data-ttu-id="768a8-250">눈에 gazed 때 3D 메뉴 항목을 천천히 회전 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-250">We will slowly spin our 3D menu items when they are being gazed upon with your eye gaze.</span></span> <span data-ttu-id="768a8-251">또한 응시된 항목을 선택하면 재미있는 효과가 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-251">We will also trigger a fun effect when the gazed-upon item is selected.</span></span>

1. <span data-ttu-id="768a8-252">아이 추적에 대해 MRTK 프로필이 제대로 구성 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-252">Ensure the MRTK profiles are properly configured for eye tracking.</span></span> <span data-ttu-id="768a8-253">이렇게 하려면 [MRTK의 눈동자 추적 시작](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) 지침으로 이동 하 여 눈동자 추적 [설정 단계별](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step) 섹션의 단계를 검토 하 여 눈동자 추적이 제대로 구성 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-253">To do this, go to the [Getting started with eye tracking in MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) instructions and verify that eye tracking is properly configured by reviewing the steps in the [Setting up eye tracking step-by-step](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#setting-up-eye-tracking-step-by-step) section.</span></span> <span data-ttu-id="768a8-254">설명서의 나머지 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-254">Complete any remaining steps in the documentation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="768a8-255">[혼합 현실 도구 키트 구성](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit) 단원에 설명 된 대로 DefaultHoloLens2InputSystemProfile를 사용 하 여 사용자 지정 MRTK 구성 프로필을 복제 하는 경우 unity 프로젝트에서 기본적으로 눈 추적을 사용 하도록 설정 하지만 unity 편집기에 대 한 눈 추적 시뮬레이션을 설정 하 고 빌드에 대 한 시각 추적을 허용 하도록 Visual Studio를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-255">If you used the DefaultHoloLens2InputSystemProfile, as instructed in the [Configure the Mixed Reality Toolkit](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1#configure-the-mixed-reality-toolkit) lesson, to clone your custom MRTK configuration profile, eye tracking is enabled by default in the Unity project but you will still have to set up eye tracking simulation for the Unity editor and configure Visual Studio to allow eye tracking for the build.</span></span>

    <span data-ttu-id="768a8-256">위의 링크에서는 다음에 대한 간단한 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-256">The link above provides brief instructions for:</span></span>

    - <span data-ttu-id="768a8-257">MRTK 프로필에서 사용할 Windows Mixed Reality 눈동자 응시 Data Provider 만들기</span><span class="sxs-lookup"><span data-stu-id="768a8-257">Creating the Windows Mixed Reality Eye Gaze Data Provider for use in the MRTK profile</span></span>
    - <span data-ttu-id="768a8-258">카메라에 연결 된 응시 공급자에서 눈 추적 사용</span><span class="sxs-lookup"><span data-stu-id="768a8-258">Enabling eye tracking in the Gaze Provider attached to the camera</span></span>
    - <span data-ttu-id="768a8-259">Unity 편집기에서 눈 추적 시뮬레이션 설정</span><span class="sxs-lookup"><span data-stu-id="768a8-259">Setting up an eye tracking simulation in the Unity editor</span></span>
    - <span data-ttu-id="768a8-260">빌드한 애플리케이션에서 시선 추적을 허용하도록 Visual Studio 솔루션 기능 편집</span><span class="sxs-lookup"><span data-stu-id="768a8-260">Editing the Visual Studio solution's capabilities to allow eye tracking in the built application</span></span>

2. <span data-ttu-id="768a8-261">대상 개체에 시선 추적 대상 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-261">Add the Eye Tracking Target component to target objects.</span></span> <span data-ttu-id="768a8-262">개체가 눈동자 응시 이벤트에 응답할 수 있도록 하려면 눈에 EyeTrackingTarget 구성 요소를 사용 하 여 상호 작용 하려는 각 개체에 대 한 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-262">To allow an object to respond to eye gaze events, we'll need to add the EyeTrackingTarget component on each object that we want to interact with by using eye gaze.</span></span> <span data-ttu-id="768a8-263">그리드 컬렉션에 속하는 9개의 3D 개체 각각에 이 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-263">Add this component to each of the nine 3D objects that are part of the grid collection.</span></span>

    >[!TIP]
    ><span data-ttu-id="768a8-264">Shift 및/또는 CTRL 키를 사용 하 여 계층에서 여러 항목을 선택한 다음 EyeTrackingTarget 구성 요소를 대량 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-264">You can use the Shift and/or CRTL keys to select multiple items in the Hierarchy and then bulk-add the EyeTrackingTarget component.</span></span>

    ![Lesson5 Chapter3 2 단계](images/Lesson5Chapter3Step2.JPG)

3. <span data-ttu-id="768a8-266">다음에는 몇 가지 흥미로운 상호 작용을 위해 EyeTrackingTutorialDemo 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-266">Next, we will add the EyeTrackingTutorialDemo script for some exciting interactions.</span></span> <span data-ttu-id="768a8-267">그리드 컬렉션의 각 3D 개체에 대해 구성 요소 추가 메뉴에서 구성 요소를 검색 하 여 EyeTrackingTutorialDemo 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-267">For each 3D object in the grid collection, add the EyeTrackingTutorialDemo script by searching for the component in the Add Component menu.</span></span>

    ![Lesson5 Chapter3 3 단계](images/Lesson5Chapter3Step3.JPG)

    >[!NOTE]
    ><span data-ttu-id="768a8-269">EyeTrackingTutorialDemo 스크립트 자료는 MRTK의 일부가 아니지만 이전 단원에서 가져온 BaseModuleAssets 자산에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-269">The EyeTrackingTutorialDemo script material is not part of MRTK but included with the BaseModuleAssets asset imported in the previous lesson.</span></span>

4. <span data-ttu-id="768a8-270">대상를 보고 있는 동안 개체가 회전합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-270">Spin the object while looking at the target.</span></span> <span data-ttu-id="768a8-271">3D 개체를 확인 하는 동안 회전 하도록 구성 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-271">We want to configure our 3D objects to spin while we are looking at them.</span></span> <span data-ttu-id="768a8-272">이렇게 하려면 아래 이미지에 표시 된 것 처럼 EyeTrackingTarget 구성 요소의 Target ()을 찾는 중 () 섹션에 새 필드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-272">To do this, insert a new field in the While Looking At Target() section of the EyeTrackingTarget component, as shown in the image below.</span></span>

    ![Lesson5 Chapter3 Step4a](images/Lesson5Chapter3Step4a.JPG)

    <span data-ttu-id="768a8-274">아래 이미지에 표시 된 것 처럼 새로 만든 필드에서 빈 필드에 현재 게임 개체를 추가 하 고 EyeTrackingTutorialDemo > RotateTarget ()를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-274">In the newly-created field, add the current Game Object to the empty field, and select EyeTrackingTutorialDemo>RotateTarget(), as shown in the image below.</span></span> <span data-ttu-id="768a8-275">이제 3D 개체는 시선 추적 시 응시될 때 회전하도록 구성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-275">Now the 3D object is configured to spin when it is being gazed upon with eye tracking.</span></span>

    ![Lesson5 Chapter3 Step4b](images/Lesson5Chapter3Step4b.JPG)

5. <span data-ttu-id="768a8-277">Gazed 하는 기능을 "선택" 하는 기능을 추가 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-277">Add in the ability to “blip target” that is being gazed at upon select by air-tap or saying “select”.</span></span> <span data-ttu-id="768a8-278">4 단계와 마찬가지로 아래 그림에 표시 된 것 처럼 EyeTrackingTarget 구성 요소의 game 개체의 Select () 필드에 할당 하 여 EyeTrackingTutorialDemo > BlipTarget ()를 트리거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-278">Similar to Step 4, we want to trigger EyeTrackingTutorialDemo>BlipTarget() by assigning it to the game object’s Select() field of the EyeTrackingTarget component, as shown in the figure below.</span></span> <span data-ttu-id="768a8-279">이제 구성 된 상태에서 선택 작업 (예: 공중 탭 또는 음성 명령 "선택")을 트리거할 때마다 게임 개체가 약간 나는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-279">With this now configured, you will notice a slight blip in the game object whenever you trigger a select action, such as air-tap or the voice command “select”.</span></span>

    ![Lesson5 Chapter3 5 단계](images/Lesson5Chapter3Step5.JPG)

6. <span data-ttu-id="768a8-281">HoloLens 2로 빌드하기 전에 시선 추적 기능이 제대로 구성되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-281">Ensure eye tracking capabilities are properly configured before building to HoloLens 2.</span></span> <span data-ttu-id="768a8-282">이 문서를 작성할 당시에는 Unity에 눈길 추적 기능에 대 한 응시 입력을 설정 하는 기능이 아직 없습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-282">As of this writing, Unity does not yet have the ability to set the gaze input for eye tracking capabilities.</span></span> <span data-ttu-id="768a8-283">이 기능을 설정 하는 것은 HoloLens 2에서의 아이 추적이 작동 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-283">Setting this capability is required for eye tracking to work in HoloLens 2.</span></span> <span data-ttu-id="768a8-284">[HoloLens 2 지침에서 Unity 앱 테스트](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) 를 수행 하 여 응시 입력 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-284">Follow the [Testing your Unity app on a HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) instructions to enable the gaze input capability.</span></span>

## <a name="congratulations"></a><span data-ttu-id="768a8-285">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-285">Congratulations</span></span>

<span data-ttu-id="768a8-286">응용 프로그램에 기본 눈 추적 기능을 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-286">You’ve successfully added basic eye tracking capabilities to your application.</span></span> <span data-ttu-id="768a8-287">이러한 작업은 시선 추적 기능 활용의 시작에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-287">These actions are only the beginning of a world of possibilities with eye tracking.</span></span> <span data-ttu-id="768a8-288">이 장에서는 음성 명령, 패닝 제스처 및 눈 추적 등 고급 입력 기능에 대해 배운 5 단원도 마무리 합니다.</span><span class="sxs-lookup"><span data-stu-id="768a8-288">This chapter also concludes Lesson 5, where we learned about advanced input functionality, such as voice commands, panning gestures, and eye tracking.</span></span>

[<span data-ttu-id="768a8-289">다음 단원: 7. 음력 모듈 샘플 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="768a8-289">Next Lesson: 7. Creating a Lunar Module sample application</span></span>](mrlearning-base-ch6.md)
