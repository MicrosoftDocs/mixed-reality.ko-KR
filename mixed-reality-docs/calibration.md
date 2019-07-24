---
title: 보정
description: IPD (interpupillary distance)를 보정 하면 시각적 개체의 품질을 향상 시킬 수 있습니다. HoloLens와 Windows Mixed Reality 모던 헤드셋은 IPD를 사용자 지정 하는 방법을 제공 합니다.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 보정, 편안 함, 시각적 개체, 품질, ipd
ms.openlocfilehash: 5f8e6aef1df0efe4c64c807e627f69c7949363f2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974810"
---
# <a name="improve-visual-quality-and-comfort"></a><span data-ttu-id="b4249-105">시각적 품질 및 편안 함 개선</span><span class="sxs-lookup"><span data-stu-id="b4249-105">Improve visual quality and comfort</span></span>
<span data-ttu-id="b4249-106">HoloLens, HoloLens 2 및 Windows Mixed Reality 몰입 형 헤드셋은 시각적 효과의 품질을 향상 시키는 다양 한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-106">HoloLens, HoloLens 2 and Windows Mixed Reality immersive headsets offer different ways to improve quality of visual experience.</span></span> 

## <a name="hololens"></a><span data-ttu-id="b4249-107">HoloLens</span><span class="sxs-lookup"><span data-stu-id="b4249-107">HoloLens</span></span>

<span data-ttu-id="b4249-108">IPD (interpupillary distance)를 보정 하면 시각적 개체의 품질을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-108">Calibrating your IPD (interpupillary distance) can improve the quality of your visuals.</span></span>

### <a name="during-setup"></a><span data-ttu-id="b4249-109">설치 하는 동안</span><span class="sxs-lookup"><span data-stu-id="b4249-109">During setup</span></span>

![두 번째 단계의 IPD 손가락 맞춤 화면](images/ipd-finger-alignment-300px.jpg)<br>

<span data-ttu-id="b4249-111">*두 번째 단계의 IPD 손가락 맞춤 화면*</span><span class="sxs-lookup"><span data-stu-id="b4249-111">*IPD finger-alignment screen at second step*</span></span>

<span data-ttu-id="b4249-112">HoloLens에는 설치 중에 시각적 개체를 보정 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-112">On HoloLens, you'll be prompted to calibrate your visuals during setup.</span></span> <span data-ttu-id="b4249-113">이를 통해 장치는 사용자의 [interpupillary 거리](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD)에 따라 홀로그램 표시를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-113">This allows the device to adjust hologram display according to the user's [interpupillary distance](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD).</span></span> <span data-ttu-id="b4249-114">잘못 된 IPD를 사용 하는 경우 holograms는 불안정 하거나 잘못 된 거리에 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-114">With an incorrect IPD, holograms may appear unstable or at an incorrect distance.</span></span>

<span data-ttu-id="b4249-115">Cortana가 자신을 도입 하면 첫 번째 설정 단계는 보정입니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-115">After Cortana introduces herself, the first setup step is calibration.</span></span> <span data-ttu-id="b4249-116">이 설정 단계에서 보정 단계를 완료 하는 것이 좋지만 Cortana가 "건너뛰기"로 이동 하 라는 메시지가 표시 될 때까지 대기 하 여이 단계를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-116">It's recommended that you complete the calibration step during this setup phase, but it can be skipped by waiting until Cortana prompts you to say "Skip" to move on.</span></span>

<span data-ttu-id="b4249-117">사용자는 자신의 손가락을 눈에 관계 없이 6 개의 대상과 맞추고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-117">Users are asked to align their finger with a series of six targets per eye.</span></span> <span data-ttu-id="b4249-118">이 프로세스를 통해 HoloLens는 사용자에 대 한 올바른 IPD를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-118">Through this process, HoloLens sets the correct IPD for the user.</span></span> <span data-ttu-id="b4249-119">새 사용자에 대해 보정을 업데이트 하거나 조정 해야 하는 경우 보정 앱을 사용 하 여 설치 프로그램 외부에서 해당 보정을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-119">If the calibration needs to be updated or adjusted for a new user, it can be run outside of setup using the Calibration app.</span></span>

### <a name="calibration-app"></a><span data-ttu-id="b4249-120">보정 앱</span><span class="sxs-lookup"><span data-stu-id="b4249-120">Calibration app</span></span>

<span data-ttu-id="b4249-121">보정 앱을 통해 언제 든 지 보정을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-121">Calibration can be performed any time through the Calibration app.</span></span> <span data-ttu-id="b4249-122">보정 앱은 기본적으로 설치 되며, 시작 메뉴 또는 설정 앱을 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-122">The Calibration app is installed by default and may be accessed from the Start menu, or through the Settings app.</span></span> <span data-ttu-id="b4249-123">시각적 개체의 품질을 개선 하거나 새 사용자에 대 한 시각적 개체를 보정 하려면 보정을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-123">Calibration is recommended if you'd like to improve the quality of your visuals or calibrate visuals for a new user.</span></span>

<span data-ttu-id="b4249-124">**시작에서 앱 시작**</span><span class="sxs-lookup"><span data-stu-id="b4249-124">**Launching the app from Start**</span></span>
1. <span data-ttu-id="b4249-125">[블 룸](gestures.md#bloom) 를 사용 하 여 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-125">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="b4249-126">모든 **+** 앱을 보려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-126">Select **+** to view all apps.</span></span>
3. <span data-ttu-id="b4249-127">**보정**을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-127">Launch **Calibration**.</span></span>

![셸에서 보정 앱에 액세스](images/calibration-shell.png)

![시작 된 후에 라이브 큐브로 표시 되는 보정 앱](images/calibration-livecube-200px.png)

<span data-ttu-id="b4249-130">**설정에서 앱 시작**</span><span class="sxs-lookup"><span data-stu-id="b4249-130">**Launching the app from Settings**</span></span>
1. <span data-ttu-id="b4249-131">[블 룸](gestures.md#bloom) 를 사용 하 여 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-131">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="b4249-132">설정이 **+** 시작에 고정 되지 않은  경우 모든 앱을 보려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-132">Select **+** to view all apps if **Settings** isn't pinned to Start.</span></span>
3. <span data-ttu-id="b4249-133">시작 **설정**입니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-133">Launch **Settings**.</span></span>
4. <span data-ttu-id="b4249-134">**시스템** > **유틸리티** 로 이동 하 여 **보정 열기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-134">Navigate to **System** > **Utilities** and select **Open Calibration**.</span></span>

![설정 앱에서 보정 앱 시작](images/calibration-settings-500px.jpg)

## <a name="hololens-2"></a><span data-ttu-id="b4249-136">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b4249-136">HoloLens 2</span></span>

### <a name="calibration"></a><span data-ttu-id="b4249-137">보정</span><span class="sxs-lookup"><span data-stu-id="b4249-137">Calibration</span></span> 

<span data-ttu-id="b4249-138">HoloLens 2에서는 장치를 설치 하는 동안 시각적 개체를 보정 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-138">On HoloLens 2, you'll be prompted to calibrate your visuals during device setup.</span></span> <span data-ttu-id="b4249-139">사용자에 게는 고정 대상 집합을 확인 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-139">Users are asked to look at the set of fixation targets.</span></span> <span data-ttu-id="b4249-140">이를 통해 장치는 holograms를 정확 하 게 배치 하 고 더 편안한 3D 보기 환경을 개선 하 고 디스플레이 품질을 개선 하도록 사용자에 게 홀로그램 렌더링을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-140">This allows the device to adjust hologram rendering for the user to ensure accurately positioned holograms, more comfortable 3D viewing experience and improved display quality.</span></span> <span data-ttu-id="b4249-141">모든 조정은 수동 조정을 수행할 필요 없이 즉시 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-141">All adjustments happen on the fly without a need for manual tuning.</span></span> 

### <a name="calibration-when-sharing-a-device"></a><span data-ttu-id="b4249-142">장치를 공유 하는 경우의 보정</span><span class="sxs-lookup"><span data-stu-id="b4249-142">Calibration when sharing a device</span></span> 

<span data-ttu-id="b4249-143">Hololens 2 장치를 사용할 필요 없이 사용자 간에 장치를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-143">Hololens 2 device can be shared between people, without a need for each person to go through device setup.</span></span> <span data-ttu-id="b4249-144">사용자가 장치를 처음 사용 하는 경우 Hololens 2는 사용자에 게 장치를 배치할 때 시각적 개체를 보정할 지 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-144">Hololens 2 will prompt the user to calibrate visuals when the device is put on the head, if the user is new to the device.</span></span> <span data-ttu-id="b4249-145">사용자가 이미 장치에서 시각적 개체를 보정 한 경우 사용자가 헤드에 장치를 배치할 때 품질 및 편안한 보기 환경을 위해 디스플레이가 원활 하 게 조정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-145">If the user has already calibrated visuals on the device, display will be seamlessly adjusted for quality and comfortable viewing experience when the user puts the device on the head.</span></span>  

### <a name="launching-the-calibration-app-from-settings"></a><span data-ttu-id="b4249-146">설정에서 보정 앱 시작</span><span class="sxs-lookup"><span data-stu-id="b4249-146">Launching the Calibration app from Settings</span></span>
1. <span data-ttu-id="b4249-147">시작 제스처를 사용 하 여 시작 메뉴를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-147">Use Start Gesture to get to Start Menu.</span></span>
2. <span data-ttu-id="b4249-148">설정이 **+** 시작에 고정 되지 않은  경우 모든 앱을 보려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-148">Select **+** to view all apps if **Settings** isn't pinned to Start.</span></span>
3. <span data-ttu-id="b4249-149">시작 **설정**입니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-149">Launch **Settings**.</span></span>
4. <span data-ttu-id="b4249-150">**시스템** > **유틸리티** 로 이동 하 여 **보정 열기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-150">Navigate to **System** > **Utilities** and select **Open Calibration**.</span></span>

## <a name="immersive-headsets"></a><span data-ttu-id="b4249-151">몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="b4249-151">Immersive headsets</span></span>

<span data-ttu-id="b4249-152">헤드셋 내에서 IPD를 변경 하려면 설정 앱을 열고 **Mixed reality** > **헤드셋 표시** 로 이동 하 여 슬라이더 컨트롤을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-152">To change IPD within your headset, open the Settings app and navigate to **Mixed reality** > **Headset display** and move the slider control.</span></span> <span data-ttu-id="b4249-153">헤드셋에서 실시간으로 변경 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-153">You’ll see the changes in real time in your headset.</span></span> <span data-ttu-id="b4249-154">IPD을 알고 있는 경우 optometrist에 대 한 방문에서 직접 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-154">If you know your IPD, maybe from a visit to the optometrist, you can enter it directly as well.</span></span>

<span data-ttu-id="b4249-155">PC에 **설정** > **혼합 현실** > **헤드셋 표시** 로 이동 하 여이 설정을 조정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-155">You can also adjust this setting by going to **Settings** > **Mixed reality** > **Headset display** on your PC.</span></span>

<span data-ttu-id="b4249-156">헤드셋에서 IPD 사용자 지정을 지원 하지 않는 경우이 설정이 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4249-156">If your headset does not support IPD customization, this setting will be disabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4249-157">참조</span><span class="sxs-lookup"><span data-stu-id="b4249-157">See also</span></span>
* [<span data-ttu-id="b4249-158">HoloLens의 환경 고려 사항</span><span class="sxs-lookup"><span data-stu-id="b4249-158">Environment considerations for HoloLens</span></span>](environment-considerations-for-hololens.md)
