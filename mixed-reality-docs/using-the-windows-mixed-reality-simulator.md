---
title: Windows Mixed Reality 시뮬레이터를 사용 하 여
description: Windows Mixed Reality 시뮬레이터를 사용 하면 Windows Mixed Reality 몰입 형 헤드셋 없이 PC에서 혼합된 현실 앱을 테스트할 수 있습니다.
author: pbarnettms
ms.author: pbarnett
ms.date: 04/25/2019
ms.topic: article
keywords: Windows는 시뮬레이터를 실제로 테스트 혼합
ms.openlocfilehash: a7cbd5b5ca1c0ed0e4f81715d337d5eec68117f0
ms.sourcegitcommit: f5c1dedb3b9e29f27f627025b9e7613931a7ce18
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64580698"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="18696-104">Windows Mixed Reality 시뮬레이터를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="18696-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="18696-105">Windows Mixed Reality 시뮬레이터를 사용 하면 Windows Mixed Reality 몰입 형 헤드셋 없이 PC에서 혼합된 현실 앱을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18696-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="18696-106">Windows 10 크리에이터 스 업데이트부터 사용할 수는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="18696-106">It is available beginning with the Windows 10 Creators Update.</span></span> <span data-ttu-id="18696-107">시뮬레이터는 비슷합니다는 [HoloLens 에뮬레이터](using-the-hololens-emulator.md)되지만 시뮬레이터 가상 컴퓨터를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="18696-107">The simulator is similar to the [HoloLens Emulator](using-the-hololens-emulator.md), though the simulator does not use a virtual machine.</span></span> <span data-ttu-id="18696-108">시뮬레이터에서 실행 되는 앱을 몰입 형 헤드셋을 사용한 경우와 마찬가지로 Windows 10 데스크톱 사용자 세션에서 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="18696-108">Apps running in the simulator run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="18696-109">일반적으로 몰입 형 헤드셋에 센서에서 읽을 수 있는 사람과 환경 입력 키보드, 마우스, 또는 Xbox 컨트롤러를 사용 하 여 시뮬레이션 대신 됩니다.</span><span class="sxs-lookup"><span data-stu-id="18696-109">The human and environmental input that would usually be read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="18696-110">앱은 시뮬레이터에서 실행을 수정할 필요가 없습니다 및 알지 들는 몰입 형 헤드셋에서 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="18696-110">Apps don't need to be modified to run in the simulator, and don't know that they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="18696-111">Windows Mixed Reality 시뮬레이터를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="18696-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="18696-112">**개발자 모드를 사용 하도록 설정** 설정에서-> 업데이트 및 개발자를 위한 보안-></span><span class="sxs-lookup"><span data-stu-id="18696-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="18696-113">시작 합니다 **혼합 현실 포털** 바탕 화면에서</span><span class="sxs-lookup"><span data-stu-id="18696-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="18696-114">설치 환경을 통해 이동 해야 처음 포털 시작 인 경우</span><span class="sxs-lookup"><span data-stu-id="18696-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="18696-115">클릭 **시작**</span><span class="sxs-lookup"><span data-stu-id="18696-115">Click **Get started**</span></span>
   2. <span data-ttu-id="18696-116">클릭 **동의 함** 계약에 동의</span><span class="sxs-lookup"><span data-stu-id="18696-116">Click **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="18696-117">클릭 **(개발자 용) 시뮬레이션에 대 한 설정** 물리적 장치 없이 설치 프로그램을 통해 계속 하려면</span><span class="sxs-lookup"><span data-stu-id="18696-117">Click **Set up for simulation (for developers)** to proceed through setup without a physical device</span></span>
   4. <span data-ttu-id="18696-118">클릭 **설정** 선택을 확인 하려면</span><span class="sxs-lookup"><span data-stu-id="18696-118">Click **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="18696-119">클릭 합니다 **개발자를 위한** 혼합 현실 포털의 왼쪽에 단추</span><span class="sxs-lookup"><span data-stu-id="18696-119">Click the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="18696-120">시뮬레이션 토글 스위치를 전환 하 고 **에서**</span><span class="sxs-lookup"><span data-stu-id="18696-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="18696-121">설치 하 고 왼쪽된 시뮬레이션된 6-DOF 컨트롤러에서는 기본적으로 시뮬레이션을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="18696-121">Enabling simulation installs and enables the left simulated 6-DOF controller by default.</span></span>  <span data-ttu-id="18696-122">이전 Windows 10 월 2019 업데이트를 시뮬레이션 된 6 DOF 컨트롤러를 설치 관리자 권한이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="18696-122">Prior to the Windows 10 May 2019 update, installing a simulated 6-DOF controller requires administrator permissions.</span></span>  <span data-ttu-id="18696-123">사용자 계정 컨트롤 대화 상자가 나타나면 동의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="18696-123">You must accept the User Account Control dialog if one appears.</span></span>

<span data-ttu-id="18696-124">이제 시뮬레이션을 사용 하 여 실행 해야!</span><span class="sxs-lookup"><span data-stu-id="18696-124">You should now be running with simulation!</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="18696-125">혼합 현실 시뮬레이터에 앱 배포</span><span class="sxs-lookup"><span data-stu-id="18696-125">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="18696-126">시뮬레이터를 가상 컴퓨터 없이 로컬 PC에서 실행 되므로 유니버설 Windows 앱을 간단히 배포할 수 있습니다 합니다 **로컬 컴퓨터** 디버깅 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="18696-126">Since the simulator runs on your local PC without a Virtual Machine, you can simply deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="18696-127">기본 시뮬레이터 입력</span><span class="sxs-lookup"><span data-stu-id="18696-127">Basic simulator input</span></span>

<span data-ttu-id="18696-128">시뮬레이터를 제어 하는 것은 매우 많은 일반적인 3D 비디오 게임 비슷합니다는 [HoloLens 에뮬레이터](using-the-hololens-emulator.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="18696-128">Controlling the simulator is very similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="18696-129">키보드, 마우스 또는 Xbox 컨트롤러를 사용 하 여 사용할 수는 입력된 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18696-129">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="18696-130">착용 하는 몰입 형 헤드셋 시뮬레이션된 된 사용자의 동작을 지시 하 여 시뮬레이터를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="18696-130">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="18696-131">작업은 시뮬레이션 된 사용자를 이동 하 고 응답 하는 몰입 형 헤드셋에서 일관 되 게는 앱과 상호 작용을 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="18696-131">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="18696-132">**앞으로, 다시을 유지 하 고 마우스 오른쪽 단추로** -W, 사용 하 여 키보드 또는 Xbox 컨트롤러에 왼쪽된 메모리에서 A, S, D 키입니다.</span><span class="sxs-lookup"><span data-stu-id="18696-132">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="18696-133">**조회할 아래, 왼쪽 및 오른쪽** -클릭 하 고 마우스를 끌어 키보드 또는 Xbox 컨트롤러에 올바른 메모리에서 화살표 키를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="18696-133">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="18696-134">**컨트롤러에서 작업 단추 누름** -마우스, 키보드에서 Enter 키를 눌러 또는 Xbox 컨트롤러에는 단추를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="18696-134">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="18696-135">**홈 컨트롤러 단추 누름** -키보드에서 Windows 키나 F2 키를 눌러 또는 Xbox 컨트롤러 B 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="18696-135">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="18696-136">**스크롤 하는 것에 대 한 컨트롤러 이동을** -Alt 키를 누른 채로 마우스 오른쪽 단추 및 위쪽 / 아래쪽에 마우스를 끌어 또는 Xbox 컨트롤러를에서 오른쪽 트리거와 단추 누른 오른쪽 스틱을 위아래로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="18696-136">**Controller movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="18696-137">추적된 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="18696-137">Tracked controllers</span></span>

<span data-ttu-id="18696-138">혼합 현실 시뮬레이터는 최대 2 명의 핸드헬드 추적된 동작 컨트롤러를 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18696-138">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="18696-139">혼합 현실 포털의 설정/해제 스위치를 사용 하 여 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="18696-139">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="18696-140">시뮬레이션 된 각 컨트롤러에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18696-140">Each simulated controller has:</span></span>
* <span data-ttu-id="18696-141">위치와 방향을 공간에서</span><span class="sxs-lookup"><span data-stu-id="18696-141">Position and orientation in space</span></span>
* <span data-ttu-id="18696-142">홈 버튼</span><span class="sxs-lookup"><span data-stu-id="18696-142">Home button</span></span>
* <span data-ttu-id="18696-143">메뉴 단추</span><span class="sxs-lookup"><span data-stu-id="18696-143">Menu button</span></span>
* <span data-ttu-id="18696-144">그립 단추</span><span class="sxs-lookup"><span data-stu-id="18696-144">Grip button</span></span>
* <span data-ttu-id="18696-145">터치 패드</span><span class="sxs-lookup"><span data-stu-id="18696-145">Touchpad</span></span>
* <span data-ttu-id="18696-146">엄지 스틱</span><span class="sxs-lookup"><span data-stu-id="18696-146">Thumbstick</span></span>
* <span data-ttu-id="18696-147">배터리 수준</span><span class="sxs-lookup"><span data-stu-id="18696-147">Battery level</span></span>

## <a name="see-also"></a><span data-ttu-id="18696-148">참조</span><span class="sxs-lookup"><span data-stu-id="18696-148">See also</span></span>
* [<span data-ttu-id="18696-149">Using the HoloLens emulator(HoloLens 에뮬레이터 사용)</span><span class="sxs-lookup"><span data-stu-id="18696-149">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="18696-150">혼합된 현실 시뮬레이터 입력 고급</span><span class="sxs-lookup"><span data-stu-id="18696-150">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="18696-151">Unity의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="18696-151">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="18696-152">DirectX의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="18696-152">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
