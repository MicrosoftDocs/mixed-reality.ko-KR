---
title: Windows Mixed Reality 시뮬레이터를 사용 하 여
description: Windows Mixed Reality 시뮬레이터를 사용 하면 Windows Mixed Reality 몰입 형 헤드셋 없이 PC에서 혼합된 현실 앱을 테스트할 수 있습니다.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Windows는 시뮬레이터를 실제로 테스트 혼합
ms.openlocfilehash: 782cab85f163edd2afc4251210b7596c73dcc8b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603638"
---
# <a name="using-the-windows-mixed-reality-simulator"></a><span data-ttu-id="034b5-104">Windows Mixed Reality 시뮬레이터를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="034b5-104">Using the Windows Mixed Reality simulator</span></span>

<span data-ttu-id="034b5-105">Windows Mixed Reality 시뮬레이터를 사용 하면 Windows Mixed Reality 몰입 형 헤드셋 없이 PC에서 혼합된 현실 앱을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-105">The Windows Mixed Reality simulator allows you to test mixed reality apps on your PC without a Windows Mixed Reality immersive headset.</span></span> <span data-ttu-id="034b5-106">Windows 10 크리에이터 스 업데이트부터 사용할 수는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-106">It is available beginning with the Windows 10 Creators Update.</span></span> <span data-ttu-id="034b5-107">시뮬레이터는 비슷합니다는 [HoloLens 에뮬레이터](using-the-hololens-emulator.md)되지만 시뮬레이터 가상 컴퓨터를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-107">The simulator is similar to the [HoloLens emulator](using-the-hololens-emulator.md), though the simulator does not use a virtual machine.</span></span> <span data-ttu-id="034b5-108">시뮬레이터에서 실행 되는 앱을 몰입 형 헤드셋을 사용한 경우와 마찬가지로 Windows 10 데스크톱 사용자 세션에서 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-108">Apps running in the simulator run in your Windows 10 desktop user session, just like they would if you were using an immersive headset.</span></span> <span data-ttu-id="034b5-109">일반적으로 몰입 형 헤드셋에 센서에서 읽을 수 있는 사람과 환경 입력 키보드, 마우스, 또는 Xbox 컨트롤러를 사용 하 여 시뮬레이션 대신 됩니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-109">The human and environmental input that would usually be read by the sensors on an immersive headset are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="034b5-110">앱은 시뮬레이터에서 실행을 수정할 필요가 없습니다 및 알지 들는 몰입 형 헤드셋에서 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-110">Apps don't need to be modified to run in the simulator, and don't know that they aren't running on an immersive headset.</span></span>

## <a name="enabling-the-windows-mixed-reality-simulator"></a><span data-ttu-id="034b5-111">Windows Mixed Reality 시뮬레이터를 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="034b5-111">Enabling the Windows Mixed Reality simulator</span></span>

1. <span data-ttu-id="034b5-112">**개발자 모드를 사용 하도록 설정** 설정에서-> 업데이트 및 개발자를 위한 보안-></span><span class="sxs-lookup"><span data-stu-id="034b5-112">**Enable Developer mode** from Settings -> Update and Security -> For developers</span></span>
2. <span data-ttu-id="034b5-113">시작 합니다 **혼합 현실 포털** 바탕 화면에서</span><span class="sxs-lookup"><span data-stu-id="034b5-113">Launch the **Mixed Reality Portal** from the desktop</span></span>
3. <span data-ttu-id="034b5-114">설치 환경을 통해 이동 해야 처음 포털 시작 인 경우</span><span class="sxs-lookup"><span data-stu-id="034b5-114">If this is your first time launching the portal, you'll need to go through the setup experience</span></span>
   1. <span data-ttu-id="034b5-115">클릭 **시작**</span><span class="sxs-lookup"><span data-stu-id="034b5-115">Click **Get started**</span></span>
   2. <span data-ttu-id="034b5-116">클릭 **동의 함** 계약에 동의</span><span class="sxs-lookup"><span data-stu-id="034b5-116">Click **I agree** to accept the agreement</span></span>
   3. <span data-ttu-id="034b5-117">클릭 **(개발자 용) 시뮬레이션에 대 한 설정** 물리적 장치 없이 설치 프로그램을 통해 계속 하려면</span><span class="sxs-lookup"><span data-stu-id="034b5-117">Click **Set up for simulation (for developers)** to proceed through setup without a physical device</span></span>
   4. <span data-ttu-id="034b5-118">클릭 **설정** 선택을 확인 하려면</span><span class="sxs-lookup"><span data-stu-id="034b5-118">Click **Set up** to confirm your choice</span></span>
4. <span data-ttu-id="034b5-119">클릭 합니다 **개발자를 위한** 혼합 현실 포털의 왼쪽에 단추</span><span class="sxs-lookup"><span data-stu-id="034b5-119">Click the **For developers** button on the left side of the Mixed Reality Portal</span></span>
5. <span data-ttu-id="034b5-120">시뮬레이션 토글 스위치를 전환 하 고 **에서**</span><span class="sxs-lookup"><span data-stu-id="034b5-120">Turn the Simulation toggle switch to **On**</span></span>
   * <span data-ttu-id="034b5-121">이렇게 하려면 관리자 권한 및 사용자 계정 컨트롤 대화 상자가 나타나면 받아들여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-121">This requires admin permissions and you must accept the User Account Control dialog that appears</span></span>

<span data-ttu-id="034b5-122">이제 시뮬레이션을 사용 하 여 실행 해야!</span><span class="sxs-lookup"><span data-stu-id="034b5-122">You should now be running with simulation!</span></span>

## <a name="deploying-apps-to-the-mixed-reality-simulator"></a><span data-ttu-id="034b5-123">혼합 현실 시뮬레이터에 앱 배포</span><span class="sxs-lookup"><span data-stu-id="034b5-123">Deploying apps to the Mixed Reality simulator</span></span>

<span data-ttu-id="034b5-124">시뮬레이터를 가상 컴퓨터 없이 로컬 PC에서 실행 되므로 유니버설 Windows 앱을 간단히 배포할 수 있습니다 합니다 **로컬 컴퓨터** 디버깅 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="034b5-124">Since the simulator runs on your local PC without a Virtual Machine, you can simply deploy your Universal Windows apps to the **Local Machine** when debugging.</span></span>

## <a name="basic-simulator-input"></a><span data-ttu-id="034b5-125">기본 시뮬레이터 입력</span><span class="sxs-lookup"><span data-stu-id="034b5-125">Basic simulator input</span></span>

<span data-ttu-id="034b5-126">시뮬레이터를 제어 하는 것은 매우 많은 일반적인 3D 비디오 게임 비슷합니다는 [HoloLens 에뮬레이터](using-the-hololens-emulator.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-126">Controlling the simulator is very similar to many common 3D video games and the [HoloLens emulator](using-the-hololens-emulator.md).</span></span> <span data-ttu-id="034b5-127">키보드, 마우스 또는 Xbox 컨트롤러를 사용 하 여 사용할 수는 입력된 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-127">There are input options available using the keyboard, mouse, or Xbox controller.</span></span>

<span data-ttu-id="034b5-128">착용 하는 몰입 형 헤드셋 시뮬레이션된 된 사용자의 동작을 지시 하 여 시뮬레이터를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-128">You control the simulator by directing the actions of a simulated user wearing an immersive headset.</span></span> <span data-ttu-id="034b5-129">작업은 시뮬레이션 된 사용자를 이동 하 고 응답 하는 몰입 형 헤드셋에서 일관 되 게는 앱과 상호 작용을 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-129">Your actions move the simulated user and cause interactions with apps that respond as they would on an immersive headset.</span></span>
* <span data-ttu-id="034b5-130">**앞으로, 다시을 유지 하 고 마우스 오른쪽 단추로** -W, 사용 하 여 키보드 또는 Xbox 컨트롤러에 왼쪽된 메모리에서 A, S, D 키입니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-130">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="034b5-131">**조회할 아래, 왼쪽 및 오른쪽** -클릭 하 고 마우스를 끌어 키보드 또는 Xbox 컨트롤러에 올바른 메모리에서 화살표 키를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-131">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="034b5-132">**컨트롤러에서 작업 단추 누름** -마우스, 키보드에서 Enter 키를 눌러 또는 Xbox 컨트롤러에는 단추를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-132">**Action button press on controller** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="034b5-133">**홈 컨트롤러 단추 누름** -키보드에서 Windows 키나 F2 키를 눌러 또는 Xbox 컨트롤러 B 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-133">**Home button press on controller** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="034b5-134">**스크롤 하는 것에 대 한 컨트롤러 이동을** -Alt 키를 누른 채로 마우스 오른쪽 단추 및 위쪽 / 아래쪽에 마우스를 끌어 또는 Xbox 컨트롤러를에서 오른쪽 트리거와 단추 누른 오른쪽 스틱을 위아래로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-134">**Controller movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="tracked-controllers"></a><span data-ttu-id="034b5-135">추적된 컨트롤러</span><span class="sxs-lookup"><span data-stu-id="034b5-135">Tracked controllers</span></span>

<span data-ttu-id="034b5-136">혼합 현실 시뮬레이터는 최대 2 명의 핸드헬드 추적된 동작 컨트롤러를 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-136">The Mixed Reality simulator can simulate up to two hand-held tracked motion controllers.</span></span> <span data-ttu-id="034b5-137">혼합 현실 포털의 설정/해제 스위치를 사용 하 여 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-137">Enable them using the toggle switches in the Mixed Reality Portal.</span></span> <span data-ttu-id="034b5-138">시뮬레이션 된 각 컨트롤러에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="034b5-138">Each simulated controller has:</span></span>
* <span data-ttu-id="034b5-139">공간 내의 위치</span><span class="sxs-lookup"><span data-stu-id="034b5-139">Position in space</span></span>
* <span data-ttu-id="034b5-140">홈 버튼</span><span class="sxs-lookup"><span data-stu-id="034b5-140">Home button</span></span>
* <span data-ttu-id="034b5-141">메뉴 버튼</span><span class="sxs-lookup"><span data-stu-id="034b5-141">Menu button</span></span>
* <span data-ttu-id="034b5-142">그립 단추</span><span class="sxs-lookup"><span data-stu-id="034b5-142">Grip button</span></span>
* <span data-ttu-id="034b5-143">터치 패드</span><span class="sxs-lookup"><span data-stu-id="034b5-143">Touchpad</span></span>

## <a name="see-also"></a><span data-ttu-id="034b5-144">참조</span><span class="sxs-lookup"><span data-stu-id="034b5-144">See also</span></span>
* [<span data-ttu-id="034b5-145">Using the HoloLens emulator(HoloLens 에뮬레이터 사용)</span><span class="sxs-lookup"><span data-stu-id="034b5-145">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="034b5-146">혼합된 현실 시뮬레이터 입력 고급</span><span class="sxs-lookup"><span data-stu-id="034b5-146">Advanced Mixed Reality Simulator Input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="034b5-147">Unity에서 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="034b5-147">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="034b5-148">DirectX의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="034b5-148">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
