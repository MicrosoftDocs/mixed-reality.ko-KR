---
title: 보정
description: 프로그램 IPD (interpupillary 거리) 보정 시각적 개체의 품질을 향상 시킬 수 있습니다. HoloLens와 Windows Mixed Reality 몰입 형 헤드셋 IPD 사용자 지정 하는 방법을 제공 합니다.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 보정, 쾌적, 시각적 개체, 품질, ipd
ms.openlocfilehash: 91af069bc4ae5e49d9eb9c529f0d0db7b1567fc8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604792"
---
# <a name="calibration"></a><span data-ttu-id="0389d-105">보정</span><span class="sxs-lookup"><span data-stu-id="0389d-105">Calibration</span></span>

<span data-ttu-id="0389d-106">프로그램 IPD (interpupillary 거리) 보정 시각적 개체의 품질을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-106">Calibrating your IPD (interpupillary distance) can improve the quality of your visuals.</span></span> <span data-ttu-id="0389d-107">HoloLens와 Windows Mixed Reality 몰입 형 헤드셋 IPD 사용자 지정 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-107">Both HoloLens and Windows Mixed Reality immersive headsets offer ways to customize IPD.</span></span>

## <a name="hololens"></a><span data-ttu-id="0389d-108">HoloLens</span><span class="sxs-lookup"><span data-stu-id="0389d-108">HoloLens</span></span>

### <a name="during-setup"></a><span data-ttu-id="0389d-109">설치 중</span><span class="sxs-lookup"><span data-stu-id="0389d-109">During setup</span></span>

![두 번째 단계에서 IPD 손가락 맞춤 화면](images/ipd-finger-alignment-300px.jpg)<br>

<span data-ttu-id="0389d-111">*두 번째 단계에서 IPD 손가락 맞춤 화면*</span><span class="sxs-lookup"><span data-stu-id="0389d-111">*IPD finger-alignment screen at second step*</span></span>

<span data-ttu-id="0389d-112">HoloLens에서 묻는를 설치 하는 동안 시각적 개체를 보정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-112">On HoloLens, you'll be prompted to calibrate your visuals during setup.</span></span> <span data-ttu-id="0389d-113">이렇게 하면 장치 사용자에 따라 홀로그램 표시를 조정 [interpupillary 거리](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD).</span><span class="sxs-lookup"><span data-stu-id="0389d-113">This allows the device to adjust hologram display according to the user's [interpupillary distance](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD).</span></span> <span data-ttu-id="0389d-114">잘못 된 IPD를 사용 하 여 홀로그램 불안정 하거나 잘못 된 거리에 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-114">With an incorrect IPD, holograms may appear unstable or at an incorrect distance.</span></span>

<span data-ttu-id="0389d-115">Cortana 자신를 도입 하는 후 첫 번째 설치 단계는 보정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-115">After Cortana introduces herself, the first setup step is calibration.</span></span> <span data-ttu-id="0389d-116">이 설치 단계에서 보정 단계를 완료 하는 Cortana를 "건너뛰지" 이동 하 라는 메시지가 표시 될 때까지 대기 하 여이 건너뛸 수 있습니다 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-116">It's recommended that you complete the calibration step during this setup phase, but it can be skipped by waiting until Cortana prompts you to say "Skip" to move on.</span></span>

<span data-ttu-id="0389d-117">사용자는 일련의 눈 모양 당 대상 수 6을 사용 하 여 해당 손가락을 정렬 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-117">Users are asked to align their finger with a series of six targets per eye.</span></span> <span data-ttu-id="0389d-118">이 프로세스를 통해 HoloLens 사용자에 대 한 올바른 IPD을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-118">Through this process, HoloLens sets the correct IPD for the user.</span></span> <span data-ttu-id="0389d-119">보정을 업데이트 하거나 새 사용자에 맞게 조정 하는 경우 보정 앱을 사용 하 여 설치 외부에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-119">If the calibration needs to be updated or adjusted for a new user, it can be run outside of setup using the Calibration app.</span></span>

### <a name="calibration-app"></a><span data-ttu-id="0389d-120">보정 앱</span><span class="sxs-lookup"><span data-stu-id="0389d-120">Calibration app</span></span>

<span data-ttu-id="0389d-121">보정은 보정 앱을 통해 언제 든 지 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-121">Calibration can be performed any time through the Calibration app.</span></span> <span data-ttu-id="0389d-122">보정 앱은 기본적으로 설치 하 고 설정 앱을 통해 또는 시작 메뉴에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-122">The Calibration app is installed by default and may be accessed from the Start menu, or through the Settings app.</span></span> <span data-ttu-id="0389d-123">시각적 개체의 품질을 향상 또는 새로운 사용자에 대 한 시각적 개체를 보정 하려고 하는 경우 보정을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-123">Calibration is recommended if you'd like to improve the quality of your visuals or calibrate visuals for a new user.</span></span>

<span data-ttu-id="0389d-124">**처음부터 앱을 시작**</span><span class="sxs-lookup"><span data-stu-id="0389d-124">**Launching the app from Start**</span></span>
1. <span data-ttu-id="0389d-125">사용 하 여 [블 룸](gestures.md#bloom) 으로 이동 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)합니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-125">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="0389d-126">선택 **+** 모든 앱을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-126">Select **+** to view all apps.</span></span>
3. <span data-ttu-id="0389d-127">시작할 **보정**합니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-127">Launch **Calibration**.</span></span>

![셸에서 보정 앱 액세스](images/calibration-shell.png)

![시작 된 후 실시간 큐브로 표시 보정 앱](images/calibration-livecube-200px.png)

<span data-ttu-id="0389d-130">**설정에서 앱을 시작**</span><span class="sxs-lookup"><span data-stu-id="0389d-130">**Launching the app from Settings**</span></span>
1. <span data-ttu-id="0389d-131">사용 하 여 [블 룸](gestures.md#bloom) 으로 이동 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)합니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-131">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="0389d-132">선택 **+** 하는 경우 모든 앱을 보려면 **설정을** 시작에 고정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-132">Select **+** to view all apps if **Settings** isn't pinned to Start.</span></span>
3. <span data-ttu-id="0389d-133">시작할 **설정을**합니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-133">Launch **Settings**.</span></span>
4. <span data-ttu-id="0389d-134">이동할 **시스템** > **유틸리티** 선택한 **열기 보정**합니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-134">Navigate to **System** > **Utilities** and select **Open Calibration**.</span></span>

![설정 앱에서 보정 앱 시작](images/calibration-settings-500px.jpg)

## <a name="hololens-2"></a><span data-ttu-id="0389d-136">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0389d-136">HoloLens 2</span></span>

> [!NOTE]
> <span data-ttu-id="0389d-137">HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-137">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="immersive-headsets"></a><span data-ttu-id="0389d-138">몰입 형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="0389d-138">Immersive headsets</span></span>

<span data-ttu-id="0389d-139">IPD 헤드셋 내를 변경 하려면 설정 앱 열고 이동할 **혼합 현실을** > **헤드셋 표시** 슬라이더 컨트롤을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-139">To change IPD within your headset, open the Settings app and navigate to **Mixed reality** > **Headset display** and move the slider control.</span></span> <span data-ttu-id="0389d-140">헤드셋에서 변경 내용을 실시간으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-140">You’ll see the changes in real time in your headset.</span></span> <span data-ttu-id="0389d-141">프로그램 IPD을 알고 있는 경우 아마도 optometrist, 방문에서 입력할 수 있습니다도 직접.</span><span class="sxs-lookup"><span data-stu-id="0389d-141">If you know your IPD, maybe from a visit to the optometrist, you can enter it directly as well.</span></span>

<span data-ttu-id="0389d-142">으로 이동 하 여이 설정을 조정할 수도 있습니다 **설정을** > **혼합 현실을** > **헤드셋 표시** PC에서.</span><span class="sxs-lookup"><span data-stu-id="0389d-142">You can also adjust this setting by going to **Settings** > **Mixed reality** > **Headset display** on your PC.</span></span>

<span data-ttu-id="0389d-143">헤드셋 IPD 사용자 지정을 지원 하지 않는 경우이 설정은 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0389d-143">If your headset does not support IPD customization, this setting will be disabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="0389d-144">참조</span><span class="sxs-lookup"><span data-stu-id="0389d-144">See also</span></span>
* [<span data-ttu-id="0389d-145">HoloLens에 대 한 환경 고려 사항</span><span class="sxs-lookup"><span data-stu-id="0389d-145">Environment considerations for HoloLens</span></span>](environment-considerations-for-hololens.md)
