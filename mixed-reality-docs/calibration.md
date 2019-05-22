---
title: 보정
description: 프로그램 IPD (interpupillary 거리) 보정 시각적 개체의 품질을 향상 시킬 수 있습니다. HoloLens와 Windows Mixed Reality 몰입 형 헤드셋 IPD 사용자 지정 하는 방법을 제공 합니다.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 보정, 쾌적, 시각적 개체, 품질, ipd
ms.openlocfilehash: 5f8e6aef1df0efe4c64c807e627f69c7949363f2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974810"
---
# <a name="improve-visual-quality-and-comfort"></a><span data-ttu-id="8fac3-105">시각적 품질 및 편안 하 게 개선</span><span class="sxs-lookup"><span data-stu-id="8fac3-105">Improve visual quality and comfort</span></span>
<span data-ttu-id="8fac3-106">HoloLens, HoloLens 2 및 Windows Mixed Reality 몰입 형 헤드셋 시각적 효과의 품질을 개선 하는 다양 한 방법 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-106">HoloLens, HoloLens 2 and Windows Mixed Reality immersive headsets offer different ways to improve quality of visual experience.</span></span> 

## <a name="hololens"></a><span data-ttu-id="8fac3-107">HoloLens</span><span class="sxs-lookup"><span data-stu-id="8fac3-107">HoloLens</span></span>

<span data-ttu-id="8fac3-108">프로그램 IPD (interpupillary 거리) 보정 시각적 개체의 품질을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-108">Calibrating your IPD (interpupillary distance) can improve the quality of your visuals.</span></span>

### <a name="during-setup"></a><span data-ttu-id="8fac3-109">설치 중</span><span class="sxs-lookup"><span data-stu-id="8fac3-109">During setup</span></span>

![두 번째 단계에서 IPD 손가락 맞춤 화면](images/ipd-finger-alignment-300px.jpg)<br>

<span data-ttu-id="8fac3-111">*두 번째 단계에서 IPD 손가락 맞춤 화면*</span><span class="sxs-lookup"><span data-stu-id="8fac3-111">*IPD finger-alignment screen at second step*</span></span>

<span data-ttu-id="8fac3-112">HoloLens에서 묻는를 설치 하는 동안 시각적 개체를 보정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-112">On HoloLens, you'll be prompted to calibrate your visuals during setup.</span></span> <span data-ttu-id="8fac3-113">이렇게 하면 장치 사용자에 따라 홀로그램 표시를 조정 [interpupillary 거리](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD).</span><span class="sxs-lookup"><span data-stu-id="8fac3-113">This allows the device to adjust hologram display according to the user's [interpupillary distance](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD).</span></span> <span data-ttu-id="8fac3-114">잘못 된 IPD를 사용 하 여 홀로그램 불안정 하거나 잘못 된 거리에 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-114">With an incorrect IPD, holograms may appear unstable or at an incorrect distance.</span></span>

<span data-ttu-id="8fac3-115">Cortana 자신를 도입 하는 후 첫 번째 설치 단계는 보정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-115">After Cortana introduces herself, the first setup step is calibration.</span></span> <span data-ttu-id="8fac3-116">이 설치 단계에서 보정 단계를 완료 하는 Cortana를 "건너뛰지" 이동 하 라는 메시지가 표시 될 때까지 대기 하 여이 건너뛸 수 있습니다 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-116">It's recommended that you complete the calibration step during this setup phase, but it can be skipped by waiting until Cortana prompts you to say "Skip" to move on.</span></span>

<span data-ttu-id="8fac3-117">사용자는 일련의 눈 모양 당 대상 수 6을 사용 하 여 해당 손가락을 정렬 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-117">Users are asked to align their finger with a series of six targets per eye.</span></span> <span data-ttu-id="8fac3-118">이 프로세스를 통해 HoloLens 사용자에 대 한 올바른 IPD을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-118">Through this process, HoloLens sets the correct IPD for the user.</span></span> <span data-ttu-id="8fac3-119">보정을 업데이트 하거나 새 사용자에 맞게 조정 하는 경우 보정 앱을 사용 하 여 설치 외부에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-119">If the calibration needs to be updated or adjusted for a new user, it can be run outside of setup using the Calibration app.</span></span>

### <a name="calibration-app"></a><span data-ttu-id="8fac3-120">보정 앱</span><span class="sxs-lookup"><span data-stu-id="8fac3-120">Calibration app</span></span>

<span data-ttu-id="8fac3-121">보정은 보정 앱을 통해 언제 든 지 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-121">Calibration can be performed any time through the Calibration app.</span></span> <span data-ttu-id="8fac3-122">보정 앱은 기본적으로 설치 하 고 설정 앱을 통해 또는 시작 메뉴에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-122">The Calibration app is installed by default and may be accessed from the Start menu, or through the Settings app.</span></span> <span data-ttu-id="8fac3-123">시각적 개체의 품질을 향상 또는 새로운 사용자에 대 한 시각적 개체를 보정 하려고 하는 경우 보정을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-123">Calibration is recommended if you'd like to improve the quality of your visuals or calibrate visuals for a new user.</span></span>

<span data-ttu-id="8fac3-124">**처음부터 앱을 시작**</span><span class="sxs-lookup"><span data-stu-id="8fac3-124">**Launching the app from Start**</span></span>
1. <span data-ttu-id="8fac3-125">사용 하 여 [블 룸](gestures.md#bloom) 으로 이동 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-125">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="8fac3-126">선택 **+** 모든 앱을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-126">Select **+** to view all apps.</span></span>
3. <span data-ttu-id="8fac3-127">시작할 **보정**합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-127">Launch **Calibration**.</span></span>

![셸에서 보정 앱 액세스](images/calibration-shell.png)

![시작 된 후 실시간 큐브로 표시 보정 앱](images/calibration-livecube-200px.png)

<span data-ttu-id="8fac3-130">**설정에서 앱을 시작**</span><span class="sxs-lookup"><span data-stu-id="8fac3-130">**Launching the app from Settings**</span></span>
1. <span data-ttu-id="8fac3-131">사용 하 여 [블 룸](gestures.md#bloom) 으로 이동 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-131">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="8fac3-132">선택 **+** 하는 경우 모든 앱을 보려면 **설정을** 시작에 고정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-132">Select **+** to view all apps if **Settings** isn't pinned to Start.</span></span>
3. <span data-ttu-id="8fac3-133">시작할 **설정을**합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-133">Launch **Settings**.</span></span>
4. <span data-ttu-id="8fac3-134">이동할 **시스템** > **유틸리티** 선택한 **열기 보정**합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-134">Navigate to **System** > **Utilities** and select **Open Calibration**.</span></span>

![설정 앱에서 보정 앱 시작](images/calibration-settings-500px.jpg)

## <a name="hololens-2"></a><span data-ttu-id="8fac3-136">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8fac3-136">HoloLens 2</span></span>

### <a name="calibration"></a><span data-ttu-id="8fac3-137">보정</span><span class="sxs-lookup"><span data-stu-id="8fac3-137">Calibration</span></span> 

<span data-ttu-id="8fac3-138">HoloLens 2에서 장치 설치 하는 동안 시각적 개체를 보정 하 라는 메시지가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-138">On HoloLens 2, you'll be prompted to calibrate your visuals during device setup.</span></span> <span data-ttu-id="8fac3-139">사용자는 고정 대상 집합 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-139">Users are asked to look at the set of fixation targets.</span></span> <span data-ttu-id="8fac3-140">이 정확 하 게 배치 홀로그램 보기 경험 하는 보다 편리한 3D 되도록 사용자에 대 한 홀로그램 렌더링에 맞게 장치를 통해 표시 품질 향상.</span><span class="sxs-lookup"><span data-stu-id="8fac3-140">This allows the device to adjust hologram rendering for the user to ensure accurately positioned holograms, more comfortable 3D viewing experience and improved display quality.</span></span> <span data-ttu-id="8fac3-141">모든 조정 수동 튜닝에 대 한 필요 없이 즉석에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-141">All adjustments happen on the fly without a need for manual tuning.</span></span> 

### <a name="calibration-when-sharing-a-device"></a><span data-ttu-id="8fac3-142">장치를 공유 하는 경우 보정</span><span class="sxs-lookup"><span data-stu-id="8fac3-142">Calibration when sharing a device</span></span> 

<span data-ttu-id="8fac3-143">Hololens 2 장치는 장치 설치 프로그램을 통해 이동 하는 각 사용자에 대 한 필요 없이 사용자 간에 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-143">Hololens 2 device can be shared between people, without a need for each person to go through device setup.</span></span> <span data-ttu-id="8fac3-144">Hololens 2에는 사용자가 장치에 새 장치는 head에 적용 되는 경우 시각적 개체를 보정 하 라는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-144">Hololens 2 will prompt the user to calibrate visuals when the device is put on the head, if the user is new to the device.</span></span> <span data-ttu-id="8fac3-145">사용자가 장치에서 시각적 개체를 보정 이미, 표시 원활 하 게 조정 됩니다 품질과 편안 하 게 시청할에 대 한 사용자 시작 부분에 장치를 배치 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="8fac3-145">If the user has already calibrated visuals on the device, display will be seamlessly adjusted for quality and comfortable viewing experience when the user puts the device on the head.</span></span>  

### <a name="launching-the-calibration-app-from-settings"></a><span data-ttu-id="8fac3-146">설정에서 보정 앱 시작</span><span class="sxs-lookup"><span data-stu-id="8fac3-146">Launching the Calibration app from Settings</span></span>
1. <span data-ttu-id="8fac3-147">시작 메뉴를 이동 하려면 시작 제스처를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-147">Use Start Gesture to get to Start Menu.</span></span>
2. <span data-ttu-id="8fac3-148">선택 **+** 하는 경우 모든 앱을 보려면 **설정을** 시작에 고정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-148">Select **+** to view all apps if **Settings** isn't pinned to Start.</span></span>
3. <span data-ttu-id="8fac3-149">시작할 **설정을**합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-149">Launch **Settings**.</span></span>
4. <span data-ttu-id="8fac3-150">이동할 **시스템** > **유틸리티** 선택한 **열기 보정**합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-150">Navigate to **System** > **Utilities** and select **Open Calibration**.</span></span>

## <a name="immersive-headsets"></a><span data-ttu-id="8fac3-151">몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="8fac3-151">Immersive headsets</span></span>

<span data-ttu-id="8fac3-152">IPD 헤드셋 내를 변경 하려면 설정 앱 열고 이동할 **혼합 현실을** > **헤드셋 표시** 슬라이더 컨트롤을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-152">To change IPD within your headset, open the Settings app and navigate to **Mixed reality** > **Headset display** and move the slider control.</span></span> <span data-ttu-id="8fac3-153">헤드셋에서 변경 내용을 실시간으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-153">You’ll see the changes in real time in your headset.</span></span> <span data-ttu-id="8fac3-154">프로그램 IPD을 알고 있는 경우 아마도 optometrist, 방문에서 입력할 수 있습니다도 직접.</span><span class="sxs-lookup"><span data-stu-id="8fac3-154">If you know your IPD, maybe from a visit to the optometrist, you can enter it directly as well.</span></span>

<span data-ttu-id="8fac3-155">으로 이동 하 여이 설정을 조정할 수도 있습니다 **설정을** > **혼합 현실을** > **헤드셋 표시** PC에서.</span><span class="sxs-lookup"><span data-stu-id="8fac3-155">You can also adjust this setting by going to **Settings** > **Mixed reality** > **Headset display** on your PC.</span></span>

<span data-ttu-id="8fac3-156">헤드셋 IPD 사용자 지정을 지원 하지 않는 경우이 설정은 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8fac3-156">If your headset does not support IPD customization, this setting will be disabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="8fac3-157">참조</span><span class="sxs-lookup"><span data-stu-id="8fac3-157">See also</span></span>
* [<span data-ttu-id="8fac3-158">HoloLens의 환경 고려 사항</span><span class="sxs-lookup"><span data-stu-id="8fac3-158">Environment considerations for HoloLens</span></span>](environment-considerations-for-hololens.md)
