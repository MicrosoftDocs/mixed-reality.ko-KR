---
title: 보정
description: IPD (interpupillary distance)를 보정 하면 시각적 개체의 품질을 향상 시킬 수 있습니다. HoloLens와 Windows Mixed Reality 모던 헤드셋은 IPD를 사용자 지정 하는 방법을 제공 합니다.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: 보정, 편안 함, 시각적 개체, 품질, ipd
ms.openlocfilehash: 354d7eb74666471f24a6b5774e5772260b1e3570
ms.sourcegitcommit: 5d3be2d7569d912011ea114c0a283bc3c635d5df
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69979477"
---
# <a name="improve-visual-quality-and-comfort"></a><span data-ttu-id="83a5f-105">시각적 품질 및 편안 함 개선</span><span class="sxs-lookup"><span data-stu-id="83a5f-105">Improve visual quality and comfort</span></span>
<span data-ttu-id="83a5f-106">HoloLens, HoloLens 2 및 Windows Mixed Reality 몰입 형 헤드셋은 시각적 효과의 품질을 향상 시키는 다양 한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-106">HoloLens, HoloLens 2 and Windows Mixed Reality immersive headsets offer different ways to improve quality of visual experience.</span></span> 

## <a name="hololens-2"></a><span data-ttu-id="83a5f-107">Hololens 2</span><span class="sxs-lookup"><span data-stu-id="83a5f-107">Hololens 2</span></span>

### <a name="calibration"></a><span data-ttu-id="83a5f-108">보정</span><span class="sxs-lookup"><span data-stu-id="83a5f-108">Calibration</span></span>

<span data-ttu-id="83a5f-109">Hololens 2는 최고 품질의 시각적 이미지를 제공 하 고 고객에 게 편안 하 게 사용할 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-109">Hololens 2 is designed to provide the highest quality visual imagery and comfort for our customers.</span></span> <span data-ttu-id="83a5f-110">아이 추적 기술은 가상 환경을 보고 상호 작용 하는 사용자 환경을 개선 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-110">Eye tracking technology is used to improve the user experience of seeing and interacting with the virtual environment.</span></span>  
<span data-ttu-id="83a5f-111">HoloLens 2에서는 장치를 설치 하는 동안 시각적 개체를 보정 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-111">On HoloLens 2, you'll be prompted to calibrate your visuals during device setup.</span></span> <span data-ttu-id="83a5f-112">사용자에 게는 고정 대상 집합을 확인 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-112">Users are asked to look at the set of fixation targets.</span></span> <span data-ttu-id="83a5f-113">이렇게 하면 장치에서 사용자에 대 한 홀로그램 렌더링을 조정 하 여 holograms, 편안한 3D 시청 환경 및 향상 된 디스플레이 품질을 정확 하 게 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-113">This allows the device to adjust hologram rendering for the user to ensure accurately positioned holograms, comfortable 3D viewing experience and improved display quality.</span></span> <span data-ttu-id="83a5f-114">모든 조정은 수동 조정을 수행할 필요 없이 즉시 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-114">All adjustments happen on the fly without a need for manual tuning.</span></span> <span data-ttu-id="83a5f-115">랜드마크로 눈동자를 사용 하 여 모든 사용자에 대 한 장치를 조정 하 고, 헤드셋이 약간의 사용을 통해 약간 이동 됨에 따라 시각적 개체를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-115">By using the eyes as landmarks, the device is adjusted for every user and visuals are tuned as the headset shifts slightly throughout use.</span></span> <span data-ttu-id="83a5f-116">눈 위치 추적은 시스템에서 내부적으로 사용 되며 개발자는이 기능을 활용 하기 위해 아무것도 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-116">Eye position tracking is used internally by the system and developers don’t need to do anything to leverage this capability.</span></span> <span data-ttu-id="83a5f-117">개발자는이 정보를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-117">This information is not available to developers.</span></span> <span data-ttu-id="83a5f-118">Hololens 2에서는 보정을 수행 하는 경우 모든 사용자에 대 한 정확한 눈동자를 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-118">On Hololens 2, performing calibration also ensures accurate eye gaze tracking for every user.</span></span> <span data-ttu-id="83a5f-119">시선 추적을 사용하여 애플리케이션에서는 사용자가 실시간으로 보는 곳을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-119">Eye tracking enables applications to track where the user is looking in real time.</span></span> <span data-ttu-id="83a5f-120">이는 개발자가 Holographic 환경 내에서 새로운 수준의 컨텍스트, 인간 이해 및 상호 작용을 최대한 활용할 수 있도록 하는 기본 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-120">This is the main capability developers can leverage to enable a whole new level of context, human understanding and interactions within the Holographic experience.</span></span>  
<span data-ttu-id="83a5f-121">보정은 장치에 로컬로 저장 되며 어떤 계정 정보에도 연결 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-121">Calibration is stored locally on the device and is not associated with any account information.</span></span> <span data-ttu-id="83a5f-122">보정 없이 장치를 사용한 사용자의 레코드는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-122">There is no record of who has used the device without calibration.</span></span> <span data-ttu-id="83a5f-123">이는 새 사용자가 처음으로 장치를 사용 하는 경우 시각적 개체를 보정 하는 메시지를 표시 하 고 이전에는 보정을 옵트아웃 하거나 보정에 실패 한 경우에는 시각적 개체를 보정 하는 메시지를 받게 됩니다</span><span class="sxs-lookup"><span data-stu-id="83a5f-123">This mean new users will get prompted to calibrate visuals when they use the device for the first time, as well as users who opted out of calibration previously or if calibration was unsuccessful.</span></span> <span data-ttu-id="83a5f-124">보정은 항상 **설정** > **개인 정보 취급 방침** > **추적**장치에서 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-124">Calibration can always be deleted from the device in **Settings** > **Privacy** > **Eye Tracker**.</span></span> 

### <a name="calibration-failures"></a><span data-ttu-id="83a5f-125">보정 오류</span><span class="sxs-lookup"><span data-stu-id="83a5f-125">Calibration failures</span></span>

<span data-ttu-id="83a5f-126">보정은 대부분의 사용자에 대해 작동 해야 하지만 사용자가 성공적으로 보정할 수 없는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-126">Calibration should work for most users, but there are cases in which the user might be unable to calibrate successfully.</span></span>  
<span data-ttu-id="83a5f-127">보정 오류의 몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-127">Some examples of calibration failures are due to:</span></span>
- <span data-ttu-id="83a5f-128">보정 환경에서 보정 대상을 따르지 않고 무시를 가져오는 사용자</span><span class="sxs-lookup"><span data-stu-id="83a5f-128">User getting distracted and not following the calibration targets during calibration experience</span></span>
- <span data-ttu-id="83a5f-129">더티 또는 긁힌 장치 센터 또는 장치 센터의 위치가 올바르게 지정 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-129">Dirty or scratched device visor or device visor not positioned properly</span></span> 
- <span data-ttu-id="83a5f-130">더티 또는 긁힌</span><span class="sxs-lookup"><span data-stu-id="83a5f-130">Dirty or scratched glasses</span></span>
- <span data-ttu-id="83a5f-131">특정 유형의 연락처 lenses 및 고 사양 (컬러 연락처 lenses, 일부 toric 연락처 lenses, IR 차단, 몇 가지 높은 prescription 고, 선글라스 등)</span><span class="sxs-lookup"><span data-stu-id="83a5f-131">Certain types of contact lenses and glasses (colored contact lenses, some toric contact lenses, IR blocking glasses, some high prescription glasses, sunglasses, etc.)</span></span>
- <span data-ttu-id="83a5f-132">구성을, eyelash 확장</span><span class="sxs-lookup"><span data-stu-id="83a5f-132">More-pronounced makeup, some eyelash extensions</span></span>
- <span data-ttu-id="83a5f-133">눈 및/또는 장치 Occlusions (머리카락, 일부 굵은 eyeglass 프레임)</span><span class="sxs-lookup"><span data-stu-id="83a5f-133">Occlusions of eye and/or device visor (hair, some thick eyeglass frames)</span></span>
- <span data-ttu-id="83a5f-134">아이 physiology, 특정 눈동자 조건 및/또는 눈 수술 (좁은 눈, 긴 eyelashes, amblyopia, nystagmus, LASIK 또는 기타 아이 surgeries의 일부 사례 등)</span><span class="sxs-lookup"><span data-stu-id="83a5f-134">Eye physiology, certain eye conditions and/or eye surgery (some narrow eyes, long eyelashes, amblyopia, nystagmus, some cases of LASIK or other eye surgeries, etc.)</span></span>

<span data-ttu-id="83a5f-135">보정에 실패 한 경우 다음 해결 방법 중 하나를 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-135">If calibration is unsuccessful try one of these fixes:</span></span> 
- <span data-ttu-id="83a5f-136">장치 센터 정리</span><span class="sxs-lookup"><span data-stu-id="83a5f-136">Clean your device visor</span></span>
- <span data-ttu-id="83a5f-137">제거</span><span class="sxs-lookup"><span data-stu-id="83a5f-137">Clean your glasses</span></span>
- <span data-ttu-id="83a5f-138">장치 센터를 모든 방식으로 푸시</span><span class="sxs-lookup"><span data-stu-id="83a5f-138">Push your device visor all the way in</span></span>
- <span data-ttu-id="83a5f-139">센서 또는 눈에 방해 하지 않는지 (예: 머리)이 없는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-139">Make sure nothing is obstructing the sensors or your eyes (e.g. hair)</span></span> 
- <span data-ttu-id="83a5f-140">대화방에 충분 한 조명이 있고 직접 햇빛에 있지 않은지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-140">Make sure there is enough light in your room and that you are not under direct sunlight</span></span>
- <span data-ttu-id="83a5f-141">보정 중에 대상을 신중 하 게 따라야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-141">Make sure you are carefully following the targets during calibration</span></span>

<span data-ttu-id="83a5f-142">모든 지침을 따르고 보정을 계속 실패 하는 경우 **설정** > **시스템** > **보정**에서 보정 프롬프트를 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-142">If you followed all guidelines and calibration is still failing, you can disable calibration prompt in **Settings** > **System** > **Calibration**.</span></span> <span data-ttu-id="83a5f-143">' 새로운 사용자가이 Hololens를 사용 하는 경우 자동으로 눈동자 보정 실행을 요청 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-143">‘When a new person uses this Hololens, automatically ask to run eye calibration’ should be tuned off.</span></span> <span data-ttu-id="83a5f-144">이로 인해 홀로그램 렌더링 품질과 discomfort이 악화 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-144">Please understand that this might result in worse hologram rendering quality and discomfort.</span></span>

### <a name="launching-the-calibration-app-from-settings"></a><span data-ttu-id="83a5f-145">설정에서 보정 앱 시작</span><span class="sxs-lookup"><span data-stu-id="83a5f-145">Launching the Calibration app from Settings</span></span>
1. <span data-ttu-id="83a5f-146">시작 제스처를 사용 하 여 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-146">Use Start Gesture to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="83a5f-147">**설정이** 시작에 고정 되지 않은 경우 모든 앱을 보려면 **모든 앱** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-147">Select **All Apps** to view all apps if **Settings** isn't pinned to Start.</span></span>
3. <span data-ttu-id="83a5f-148">시작 **설정**입니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-148">Launch **Settings**.</span></span>
4. <span data-ttu-id="83a5f-149">**시스템** > **보정** 눈 모양 보정으로 이동 하 여 눈동자 보정 실행을 선택 합니다. > </span><span class="sxs-lookup"><span data-stu-id="83a5f-149">Navigate to **System** > **Calibration** > **Eye Calibration** and select **Run Eye Calibration**.</span></span>

### <a name="calibration-when-sharing-a-device--session"></a><span data-ttu-id="83a5f-150">장치/세션을 공유할 때의 보정</span><span class="sxs-lookup"><span data-stu-id="83a5f-150">Calibration when sharing a device / session</span></span>

<span data-ttu-id="83a5f-151">Hololens 2는 각 사용자가 장치 설치를 통과 하지 않아도 사용자 간에 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-151">Hololens 2 can be shared between people, without a need for each person to go through device setup.</span></span> <span data-ttu-id="83a5f-152">사용자가 장치를 처음 사용 하는 경우 Hololens 2는 사용자에 게 장치를 배치할 때 시각적 개체를 보정할 지 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-152">Hololens 2 will prompt the user to calibrate visuals when the device is put on the head if the user is new to the device.</span></span> <span data-ttu-id="83a5f-153">사용자가 이전에 장치에서 시각적 개체를 보정 한 경우 사용자가 헤드에 장치를 배치할 때 품질 및 편안 하 게 볼 수 있도록 디스플레이를 원활 하 게 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-153">If the user has previously calibrated visuals on the device, the display will be seamlessly adjusted for quality and a comfortable viewing experience when the user puts the device on the head.</span></span> 


## <a name="hololens"></a><span data-ttu-id="83a5f-154">Hololens</span><span class="sxs-lookup"><span data-stu-id="83a5f-154">Hololens</span></span>

<span data-ttu-id="83a5f-155">IPD (interpupillary distance)를 보정 하면 시각적 개체의 품질을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-155">Calibrating your IPD (interpupillary distance) can improve the quality of your visuals.</span></span>

### <a name="during-setup"></a><span data-ttu-id="83a5f-156">설치 하는 동안</span><span class="sxs-lookup"><span data-stu-id="83a5f-156">During setup</span></span>

![두 번째 단계의 IPD 손가락 맞춤 화면](images/ipd-finger-alignment-300px.jpg)<br>

<span data-ttu-id="83a5f-158">*두 번째 단계의 IPD 손가락 맞춤 화면*</span><span class="sxs-lookup"><span data-stu-id="83a5f-158">*IPD finger-alignment screen at second step*</span></span>

<span data-ttu-id="83a5f-159">HoloLens에는 설치 중에 시각적 개체를 보정 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-159">On HoloLens, you'll be prompted to calibrate your visuals during setup.</span></span> <span data-ttu-id="83a5f-160">이를 통해 장치는 사용자의 [interpupillary 거리](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD)에 따라 홀로그램 표시를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-160">This allows the device to adjust hologram display according to the user's [interpupillary distance](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD).</span></span> <span data-ttu-id="83a5f-161">잘못 된 IPD를 사용 하는 경우 holograms는 불안정 하거나 잘못 된 거리에 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-161">With an incorrect IPD, holograms may appear unstable or at an incorrect distance.</span></span>

<span data-ttu-id="83a5f-162">Cortana가 자신을 도입 하면 첫 번째 설정 단계는 보정입니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-162">After Cortana introduces herself, the first setup step is calibration.</span></span> <span data-ttu-id="83a5f-163">이 설정 단계에서 보정 단계를 완료 하는 것이 좋지만 Cortana가 "건너뛰기"로 이동 하 라는 메시지가 표시 될 때까지 대기 하 여이 단계를 건너뛸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-163">It's recommended that you complete the calibration step during this setup phase, but it can be skipped by waiting until Cortana prompts you to say "Skip" to move on.</span></span>

<span data-ttu-id="83a5f-164">사용자는 자신의 손가락을 눈에 관계 없이 6 개의 대상과 맞추고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-164">Users are asked to align their finger with a series of six targets per eye.</span></span> <span data-ttu-id="83a5f-165">이 프로세스를 통해 HoloLens는 사용자에 대 한 올바른 IPD를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-165">Through this process, HoloLens sets the correct IPD for the user.</span></span> <span data-ttu-id="83a5f-166">새 사용자에 대해 보정을 업데이트 하거나 조정 해야 하는 경우 보정 앱을 사용 하 여 설치 프로그램 외부에서 해당 보정을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-166">If the calibration needs to be updated or adjusted for a new user, it can be run outside of setup using the Calibration app.</span></span>

### <a name="calibration-app"></a><span data-ttu-id="83a5f-167">보정 앱</span><span class="sxs-lookup"><span data-stu-id="83a5f-167">Calibration app</span></span>

<span data-ttu-id="83a5f-168">보정 앱을 통해 언제 든 지 보정을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-168">Calibration can be performed any time through the Calibration app.</span></span> <span data-ttu-id="83a5f-169">보정 앱은 기본적으로 설치 되며, 시작 메뉴 또는 설정 앱을 통해 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-169">The Calibration app is installed by default and may be accessed from the Start menu, or through the Settings app.</span></span> <span data-ttu-id="83a5f-170">시각적 개체의 품질을 개선 하거나 새 사용자에 대 한 시각적 개체를 보정 하려면 보정을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-170">Calibration is recommended if you'd like to improve the quality of your visuals or calibrate visuals for a new user.</span></span>

<span data-ttu-id="83a5f-171">**시작에서 앱 시작**</span><span class="sxs-lookup"><span data-stu-id="83a5f-171">**Launching the app from Start**</span></span>
1. <span data-ttu-id="83a5f-172">[블 룸](gestures.md#bloom) 를 사용 하 여 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-172">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="83a5f-173">모든 **+** 앱을 보려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-173">Select **+** to view all apps.</span></span>
3. <span data-ttu-id="83a5f-174">**보정**을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-174">Launch **Calibration**.</span></span>

![셸에서 보정 앱에 액세스](images/calibration-shell.png)

![시작 된 후에 라이브 큐브로 표시 되는 보정 앱](images/calibration-livecube-200px.png)

<span data-ttu-id="83a5f-177">**설정에서 앱 시작**</span><span class="sxs-lookup"><span data-stu-id="83a5f-177">**Launching the app from Settings**</span></span>
1. <span data-ttu-id="83a5f-178">[블 룸](gestures.md#bloom) 를 사용 하 여 [시작 메뉴](navigating-the-windows-mixed-reality-home.md#start-menu)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-178">Use [bloom](gestures.md#bloom) to get to [Start Menu](navigating-the-windows-mixed-reality-home.md#start-menu).</span></span>
2. <span data-ttu-id="83a5f-179">설정이 **+** 시작에 고정 되지 않은 경우 모든 앱을 보려면 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-179">Select **+** to view all apps if **Settings** isn't pinned to Start.</span></span>
3. <span data-ttu-id="83a5f-180">시작 **설정**입니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-180">Launch **Settings**.</span></span>
4. <span data-ttu-id="83a5f-181">**시스템** > **유틸리티** 로 이동 하 여 **보정 열기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-181">Navigate to **System** > **Utilities** and select **Open Calibration**.</span></span>

![설정 앱에서 보정 앱 시작](images/calibration-settings-500px.jpg)


## <a name="immersive-headsets"></a><span data-ttu-id="83a5f-183">몰입형 헤드셋</span><span class="sxs-lookup"><span data-stu-id="83a5f-183">Immersive headsets</span></span>

<span data-ttu-id="83a5f-184">헤드셋 내에서 IPD를 변경 하려면 설정 앱을 열고 **Mixed reality** > **헤드셋 표시** 로 이동 하 여 슬라이더 컨트롤을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-184">To change IPD within your headset, open the Settings app and navigate to **Mixed reality** > **Headset display** and move the slider control.</span></span> <span data-ttu-id="83a5f-185">헤드셋에서 실시간으로 변경 내용을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-185">You’ll see the changes in real time in your headset.</span></span> <span data-ttu-id="83a5f-186">IPD을 알고 있는 경우 optometrist에 대 한 방문에서 직접 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-186">If you know your IPD, maybe from a visit to the optometrist, you can enter it directly as well.</span></span>

<span data-ttu-id="83a5f-187">PC에 **설정** > **혼합 현실** > **헤드셋 표시** 로 이동 하 여이 설정을 조정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-187">You can also adjust this setting by going to **Settings** > **Mixed reality** > **Headset display** on your PC.</span></span>

<span data-ttu-id="83a5f-188">헤드셋에서 IPD 사용자 지정을 지원 하지 않는 경우이 설정이 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a5f-188">If your headset does not support IPD customization, this setting will be disabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="83a5f-189">참조</span><span class="sxs-lookup"><span data-stu-id="83a5f-189">See also</span></span>
* [<span data-ttu-id="83a5f-190">HoloLens의 환경 고려 사항</span><span class="sxs-lookup"><span data-stu-id="83a5f-190">Environment considerations for HoloLens</span></span>](environment-considerations-for-hololens.md)
