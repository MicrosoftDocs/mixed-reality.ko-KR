---
title: HoloLens 에뮬레이터를 사용 하 여
description: HoloLens 에뮬레이터를 사용 하면 실제 HoloLens 하지 않고 PC에서 혼합된 현실 앱을 테스트할 수 있습니다.
author: JonMLyons
ms.author: jlyons
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, 에뮬레이터
ms.openlocfilehash: 3551bf48037f0cb7e8d243f2d89d43664e7c3475
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604102"
---
# <a name="using-the-hololens-emulator"></a><span data-ttu-id="8d0b7-104">HoloLens 에뮬레이터를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="8d0b7-104">Using the HoloLens emulator</span></span>

<span data-ttu-id="8d0b7-105">HoloLens 에뮬레이터 실제 HoloLens 하지 않고 PC에서 holographic 앱을 테스트할 수 있습니다 및 HoloLens 개발 도구 집합과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-105">The HoloLens emulator allows you to test holographic apps on your PC without a physical HoloLens and comes with the HoloLens development toolset.</span></span> <span data-ttu-id="8d0b7-106">에뮬레이터는 Hyper-v 가상 컴퓨터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-106">The emulator uses a Hyper-V virtual machine.</span></span> <span data-ttu-id="8d0b7-107">일반적으로 HoloLens에 센서에서 읽을 수 있는 사람과 환경 입력 키보드, 마우스, 또는 Xbox 컨트롤러를 사용 하 여 시뮬레이션 대신 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-107">The human and environmental inputs that would usually be read by the sensors on the HoloLens are instead simulated using your keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="8d0b7-108">에뮬레이터에서 실행을 수정할 필요가 없습니다 프로그램과 알지 들 실제 HoloLens에서 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-108">Apps don't need to be modified to run on the emulator and don't know that they aren't running on a real HoloLens.</span></span>

<span data-ttu-id="8d0b7-109">데스크톱 Pc에 대 한 Windows Mixed Reality 몰입 형 (VR) 헤드셋 앱 또는 게임을 개발 하려는 경우 체크 아웃 합니다 [Windows Mixed Reality 시뮬레이터](using-the-windows-mixed-reality-simulator.md), 대신 데스크톱 헤드셋을 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-109">If you're looking to develop Windows Mixed Reality immersive (VR) headset apps or games for desktop PCs, check out the [Windows Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md), which lets you simulate desktop headsets instead.</span></span>

> [!NOTE]
> <span data-ttu-id="8d0b7-110">HoloLens 2 관련 된 자세한 지침 [예정](index.md#news-and-notes)합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-110">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>

## <a name="installing-the-hololens-emulator"></a><span data-ttu-id="8d0b7-111">HoloLens 에뮬레이터 설치</span><span class="sxs-lookup"><span data-stu-id="8d0b7-111">Installing the HoloLens emulator</span></span>

<span data-ttu-id="8d0b7-112">다운로드 합니다 [HoloLens (첫 번째 gen) holographic 프로젝트 템플릿과 에뮬레이터](https://go.microsoft.com/fwlink/?linkid=2065980)합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-112">Download the [HoloLens (1st gen) emulator and holographic project templates](https://go.microsoft.com/fwlink/?linkid=2065980).</span></span>

<span data-ttu-id="8d0b7-113">HoloLens 에뮬레이터의 이전 빌드를 찾을 수 있습니다 합니다 [HoloLens 에뮬레이터 아카이브](hololens-emulator-archive.md) 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-113">You can find older builds of the HoloLens emulator on the [HoloLens emulator archive](hololens-emulator-archive.md) page.</span></span>

### <a name="hololens-emulator-system-requirements"></a><span data-ttu-id="8d0b7-114">HoloLens 에뮬레이터 시스템 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8d0b7-114">HoloLens emulator system requirements</span></span>

<span data-ttu-id="8d0b7-115">HoloLens 에뮬레이터에서 Hyper-v를 기반으로 하 고 하드웨어 가속된 그래픽에 대 한 RemoteFx를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-115">The HoloLens emulator is based on Hyper-V and uses RemoteFx for hardware accelerated graphics.</span></span> <span data-ttu-id="8d0b7-116">에뮬레이터를 사용 하려면 PC에 이러한 하드웨어 요구 사항을 충족 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-116">To use the emulator, make sure your PC meets these hardware requirements:</span></span>
* <span data-ttu-id="8d0b7-117">64 비트 Windows 10 Pro, Enterprise 또는 교육</span><span class="sxs-lookup"><span data-stu-id="8d0b7-117">64-bit Windows 10 Pro, Enterprise, or Education</span></span> 
    >[!NOTE]
    ><span data-ttu-id="8d0b7-118">Windows 10 Home edition에는 Hyper-v 또는 HoloLens 에뮬레이터를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-118">Windows 10 Home edition does not support Hyper-V or the HoloLens emulator</span></span>
* <span data-ttu-id="8d0b7-119">64비트 CPU</span><span class="sxs-lookup"><span data-stu-id="8d0b7-119">64-bit CPU</span></span>
* <span data-ttu-id="8d0b7-120">CPU 코어 4 개 (또는 총 코어 수 4 개를 사용 하 여 여러 Cpu)</span><span class="sxs-lookup"><span data-stu-id="8d0b7-120">CPU with 4 cores (or multiple CPUs with a total of 4 cores)</span></span>
* <span data-ttu-id="8d0b7-121">8GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="8d0b7-121">8 GB of RAM or more</span></span>
* <span data-ttu-id="8d0b7-122">BIOS에서 다음 기능 이어야 합니다 [지원 하 고 사용 하도록 설정](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):</span><span class="sxs-lookup"><span data-stu-id="8d0b7-122">In the BIOS, the following features must be [supported and enabled](http://blogs.technet.com/b/iftekhar/archive/2010/08/09/enable-hardware-settings-in-bios-to-run-hyper-v.aspx):</span></span>
   * <span data-ttu-id="8d0b7-123">하드웨어 지원 가상화</span><span class="sxs-lookup"><span data-stu-id="8d0b7-123">Hardware-assisted virtualization</span></span>
   * <span data-ttu-id="8d0b7-124">SLAT(Second Level Address Translation)</span><span class="sxs-lookup"><span data-stu-id="8d0b7-124">Second Level Address Translation (SLAT)</span></span>
   * <span data-ttu-id="8d0b7-125">하드웨어 기반 DEP(데이터 실행 방지)</span><span class="sxs-lookup"><span data-stu-id="8d0b7-125">Hardware-based Data Execution Prevention (DEP)</span></span>
* <span data-ttu-id="8d0b7-126">GPU 요구 사항 (에뮬레이터는 지원 되지 않는 GPU에서 작동 하지만 성능이 크게 저하 됩니다.)</span><span class="sxs-lookup"><span data-stu-id="8d0b7-126">GPU requirements (the emulator might work with an unsupported GPU, but will be significantly slower)</span></span>
   * <span data-ttu-id="8d0b7-127">DirectX 11.0 이상</span><span class="sxs-lookup"><span data-stu-id="8d0b7-127">DirectX 11.0 or later</span></span>
   * <span data-ttu-id="8d0b7-128">WDDM 1.2 드라이버 이상</span><span class="sxs-lookup"><span data-stu-id="8d0b7-128">WDDM 1.2 driver or later</span></span>

<span data-ttu-id="8d0b7-129">시스템에는 위의 요구 사항을 충족 하는 경우 **시스템에서 "하이퍼-V" 기능이 설정 되어 있는지를 확인 하세요** 제어판을 통해-> 프로그램-> 프로그램 및 기능에서-> Windows 기능 설정 또는 해제-> 확인 찾기가 성공 하려면 에뮬레이터 설치에 대 한 해당 "하이퍼-V" 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-129">If your system meets the above requirements, **please ensure that the "Hyper-V" feature has been enabled on your system** through Control Panel -> Programs -> Programs and Features -> Turn Windows Features on or off -> ensure that "Hyper-V" is selected for the Emulator installation to be successful.</span></span>

### <a name="installation-troubleshooting"></a><span data-ttu-id="8d0b7-130">설치 문제 해결</span><span class="sxs-lookup"><span data-stu-id="8d0b7-130">Installation troubleshooting</span></span>

<span data-ttu-id="8d0b7-131">해야 하는 에뮬레이터를 설치 하는 동안 오류가 표시 될 수 있습니다 *"Visual Studio 2015 업데이트 1 및 UWP 도구 버전 1.2"* 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-131">You may see an error while installing the emulator that you need *"Visual Studio 2015 Update 1 and UWP tools version 1.2"*.</span></span> <span data-ttu-id="8d0b7-132">이 오류의 원인은 3 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-132">There are three possible causes of this error:</span></span>
* <span data-ttu-id="8d0b7-133">최신 버전의 Visual Studio (Visual Studio 2017 또는 Visual Studio 2015 업데이트 1 이상)는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-133">You do not have a recent enough version of Visual Studio (Visual Studio 2017 or Visual Studio 2015 Update 1 or later).</span></span> <span data-ttu-id="8d0b7-134">이 해결 하려면 Visual Studio의 최신 릴리스를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-134">To correct this, install the latest release of Visual Studio.</span></span>
* <span data-ttu-id="8d0b7-135">Visual Studio의 최신 버전의 유니버설 Windows 플랫폼 (UWP) 도구가 설치 되어 있지 않은 있지만</span><span class="sxs-lookup"><span data-stu-id="8d0b7-135">You have a recent enough version of Visual Studio, but you do not have the Universal Windows Platform (UWP) tools installed.</span></span> <span data-ttu-id="8d0b7-136">이것이 Visual Studio에 대 한 선택적 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-136">This is an optional feature for Visual Studio.</span></span>

<span data-ttu-id="8d0b7-137">에뮬레이터에는 비-PRO/Enterprise/교육 SKU의 Windows를 설치 하는 오류가 나타날 수도 있습니다 또는 Hyper-v 기능이 없는 경우 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-137">You may also see an error installing the emulator on a non-PRO/Enterprise/Education SKU of Windows or if you do not have Hyper-V feature enabled.</span></span>
* <span data-ttu-id="8d0b7-138">읽어보세요 합니다 [시스템 요구 사항](#hololens-emulator-system-requirements) 전체 요구 사항 집합에 대 한 위 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-138">Please read the [system requirements](#hololens-emulator-system-requirements) section above for a complete set of requirements.</span></span>
* <span data-ttu-id="8d0b7-139">하세요 시스템에서 Hyper-v 기능이 설정 되어 있는지 확인도 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-139">Please also ensure that Hyper-V feature has been enabled on your system.</span></span>

## <a name="deploying-apps-to-the-hololens-emulator"></a><span data-ttu-id="8d0b7-140">HoloLens 에뮬레이터에 앱 배포</span><span class="sxs-lookup"><span data-stu-id="8d0b7-140">Deploying apps to the HoloLens emulator</span></span>

1. <span data-ttu-id="8d0b7-141">Visual Studio 2015에서 앱 솔루션을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-141">Load your app solution in Visual Studio 2015.</span></span>
    >[!NOTE]
    ><span data-ttu-id="8d0b7-142">Unity를 사용 하면 Unity에서 프로젝트를 빌드할 한 다음 빌드된 솔루션이 Visual Studio를 정상적으로 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-142">When using Unity, build your project from Unity and then load the built solution into Visual Studio as usual.</span></span>
2. <span data-ttu-id="8d0b7-143">플랫폼으로 설정 되었는지 확인 **x86**합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-143">Ensure the Platform is set to **x86**.</span></span>
3. <span data-ttu-id="8d0b7-144">선택 된 **HoloLens 에뮬레이터** 디버깅에 대 한 대상 장치로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-144">Select the **HoloLens Emulator** as the target device for debugging.</span></span>
4. <span data-ttu-id="8d0b7-145">로 이동 **디버그 > 디버깅 시작** 누르거나 **F5** 에뮬레이터를 시작 하 여 디버깅을 위해 앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-145">Go to **Debug > Start Debugging** or press **F5** to launch the emulator and deploy your app for debugging.</span></span>

<span data-ttu-id="8d0b7-146">에뮬레이터는 1 분 이상 처음 시작할 때 부팅 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-146">The emulator may take a minute or more to boot when you first start it.</span></span> <span data-ttu-id="8d0b7-147">열어 에뮬레이터 디버깅 세션 중 실행 중인 에뮬레이터에 앱을 신속 하 게 배포할 수 있습니다 있도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-147">We recommend that you keep the emulator open during your debugging session so you can quickly deploy apps to the running emulator.</span></span>

## <a name="basic-emulator-input"></a><span data-ttu-id="8d0b7-148">기본 에뮬레이터 입력</span><span class="sxs-lookup"><span data-stu-id="8d0b7-148">Basic emulator input</span></span>

<span data-ttu-id="8d0b7-149">에뮬레이터를 제어 하는 것은 많은 일반적인 3D 비디오 게임 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-149">Controlling the emulator is very similar to many common 3D video games.</span></span> <span data-ttu-id="8d0b7-150">키보드, 마우스 또는 Xbox 컨트롤러를 사용 하 여 사용할 수는 입력된 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-150">There are input options available using the keyboard, mouse, or Xbox controller.</span></span> <span data-ttu-id="8d0b7-151">HoloLens 착용 시뮬레이션된 된 사용자의 동작을 지시 하 여 에뮬레이터를 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-151">You control the emulator by directing the actions of a simulated user wearing a HoloLens.</span></span> <span data-ttu-id="8d0b7-152">작업 관련 시뮬레이션 된 사용자와 에뮬레이터에서 실행 되는 앱이 실제 장치에서 하 듯는 응답을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-152">Your actions move that simulated user around and apps running in the emulator respond like they would on a real device.</span></span>
* <span data-ttu-id="8d0b7-153">**앞으로, 다시을 유지 하 고 마우스 오른쪽 단추로** -W, 사용 하 여 키보드 또는 Xbox 컨트롤러에 왼쪽된 메모리에서 A, S, D 키입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-153">**Walk forward, back, left, and right** - Use the W,A,S, and D keys on your keyboard, or the left stick on an Xbox controller.</span></span>
* <span data-ttu-id="8d0b7-154">**조회할 아래, 왼쪽 및 오른쪽** -클릭 하 고 마우스를 끌어 키보드 또는 Xbox 컨트롤러에 올바른 메모리에서 화살표 키를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-154">**Look up, down, left, and right** - Click and drag the mouse, use the arrow keys on your keyboard, or the right stick on an Xbox controller.</span></span>
* <span data-ttu-id="8d0b7-155">**어 탭 제스처** -마우스, 키보드에서 Enter 키를 눌러 또는 Xbox 컨트롤러에는 단추를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-155">**Air tap gesture** - Right-click the mouse, press the Enter key on your keyboard, or use the A button on an Xbox controller.</span></span>
* <span data-ttu-id="8d0b7-156">**제스처 피우는** -키보드에서 Windows 키나 F2 키를 눌러 또는 Xbox 컨트롤러 B 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-156">**Bloom gesture** - Press the Windows key or F2 key on your keyboard, or press the B button on an Xbox controller.</span></span>
* <span data-ttu-id="8d0b7-157">**스크롤 하는 것에 대 한 이동을 제공할** -Alt 키를 누른 채로 마우스 오른쪽 단추 및 위쪽 / 아래쪽에 마우스를 끌어 또는 Xbox 컨트롤러를에서 오른쪽 트리거와 단추 누른 오른쪽 스틱을 위아래로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-157">**Hand movement for scrolling** - Hold the Alt key, hold the right mouse button, and drag the mouse up / down, or in an Xbox controller hold the right trigger and A button down and move the right stick up and down.</span></span>

## <a name="anatomy-of-the-hololens-emulator"></a><span data-ttu-id="8d0b7-158">HoloLens 에뮬레이터의 분석</span><span class="sxs-lookup"><span data-stu-id="8d0b7-158">Anatomy of the HoloLens emulator</span></span>

### <a name="main-window"></a><span data-ttu-id="8d0b7-159">주 창</span><span class="sxs-lookup"><span data-stu-id="8d0b7-159">Main window</span></span>

<span data-ttu-id="8d0b7-160">에뮬레이터를 시작, HoloLens OS를 표시 하는 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-160">When the emulator launches, you will see a window which displays the HoloLens OS.</span></span>

![HoloLens 에뮬레이터 주 창](images/emulator-890px.png)

### <a name="toolbar"></a><span data-ttu-id="8d0b7-162">도구 모음</span><span class="sxs-lookup"><span data-stu-id="8d0b7-162">Toolbar</span></span>

<span data-ttu-id="8d0b7-163">주 창의 오른쪽에는 에뮬레이터 도구 모음을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-163">To the right of the main window, you will find the emulator toolbar.</span></span> <span data-ttu-id="8d0b7-164">도구 모음에 다음 단추가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-164">The toolbar contains the following buttons:</span></span>
* <span data-ttu-id="8d0b7-165">![닫기 아이콘](images/emulator-close.png) **닫기**: 에뮬레이터를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-165">![Close icon](images/emulator-close.png) **Close**: Closes the emulator.</span></span>
* <span data-ttu-id="8d0b7-166">![최소화 아이콘](images/emulator-minimize.png) **최소화**: 에뮬레이터 창을 최소화합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-166">![Minimize icon](images/emulator-minimize.png) **Minimize**: Minimizes the emulator window.</span></span>
* <span data-ttu-id="8d0b7-167">![사용자 입력된 아이콘](images/emulator-control.png) **휴먼 입력**: 마우스 및 키보드 사용을 시뮬레이션할 휴먼 [에뮬레이터에 대 한 입력](#basic-emulator-input)합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-167">![Human input icon](images/emulator-control.png) **Human Input**: Mouse and Keyboard are used to simulate human [input to the emulator](#basic-emulator-input).</span></span>
* <span data-ttu-id="8d0b7-168">![키보드 및 마우스 입력된 아이콘](images/emulator-input.png) **키보드 및 마우스 입력**: 키보드 및 마우스 입력에 직접 전달 되는 HoloLens OS 키보드 및 마우스 이벤트로 Bluetooth 키보드와 마우스를 연결 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-168">![Keyboard and mouse input icon](images/emulator-input.png) **Keyboard and Mouse Input**: Keyboard and mouse input are passed directly to the HoloLens OS as keyboard and mouse events as if you connected a Bluetooth keyboard and mouse.</span></span>
* <span data-ttu-id="8d0b7-169">![화면에 맞춤 아이콘](images/emulator-fit.png) **화면에 맞추기**: 에뮬레이터를 화면에 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-169">![Fit to screen icon](images/emulator-fit.png) **Fit to Screen**: Fits the emulator to screen.</span></span>
* <span data-ttu-id="8d0b7-170">![확대/축소 아이콘](images/emulator-zoom.png) **확대/축소**: 크고 작은 에뮬레이터를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-170">![Zoom icon](images/emulator-zoom.png) **Zoom**: Make the emulator larger and smaller.</span></span>
* <span data-ttu-id="8d0b7-171">![도움말 아이콘](images/emulator-help.png) **도움말**: 에뮬레이터 도움말을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-171">![Help icon](images/emulator-help.png) **Help**: Open emulator help.</span></span>
* <span data-ttu-id="8d0b7-172">![열린 장치 포털 아이콘](images/emulator-deviceportal.png) **장치 포털 열기**: 에뮬레이터에서 HoloLens OS에 대 한 Windows Device Portal 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-172">![Open device portal icon](images/emulator-deviceportal.png) **Open Device Portal**: Open the Windows Device Portal for the HoloLens OS in the emulator.</span></span>
* <span data-ttu-id="8d0b7-173">![도구 아이콘](images/emulator-tools.png) **도구**: 엽니다는 **추가 도구** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-173">![Tools icon](images/emulator-tools.png) **Tools**: Open the **Additional Tools** pane.</span></span>

### <a name="simulation-tab"></a><span data-ttu-id="8d0b7-174">시뮬레이션 탭</span><span class="sxs-lookup"><span data-stu-id="8d0b7-174">Simulation tab</span></span>

<span data-ttu-id="8d0b7-175">내에서 기본 탭의 **추가 도구** 창은 합니다 **시뮬레이션** 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-175">The default tab within the **Additional Tools** pane is the **Simulation** tab.</span></span>

![HoloLens 에뮬레이터 ' 추가 ' 도구 창](images/emulator-simulation-500px.png)

<span data-ttu-id="8d0b7-177">시뮬레이션 탭 에뮬레이터 내에서 HoloLens OS 드라이브를 사용 하 고 시뮬레이트된 센서의 현재 상태를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-177">The Simulation tab shows the current state of the simulated sensors used to drive the HoloLens OS within the emulator.</span></span> <span data-ttu-id="8d0b7-178">시뮬레이션 탭에 있는 값을 마우스로 가리키면 해당 값을 제어 하는 방법을 설명 하는 도구 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-178">Hovering over any value in the Simulation tab will provide a tooltip describing how to control that value.</span></span>

### <a name="room-tab"></a><span data-ttu-id="8d0b7-179">공간 탭</span><span class="sxs-lookup"><span data-stu-id="8d0b7-179">Room tab</span></span>

<span data-ttu-id="8d0b7-180">에뮬레이터에서 시뮬레이트된 "방" 공간 매핑 메시의 형태로 world 입력을 시뮬레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-180">The emulator simulates world input in the form of the spatial mapping mesh from simulated "rooms".</span></span> <span data-ttu-id="8d0b7-181">이 탭에는 기본 단체 실 대신 로드 하는 대화방을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-181">This tab lets you pick which room to load instead of the default room.</span></span>

![HoloLens 에뮬레이터 '방' 탭](images/emulator-room-500px.png)

<span data-ttu-id="8d0b7-183">시뮬레이션 된 대화방 앱 테스트를 위해 여러 환경에서 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-183">Simulated rooms are useful for testing your app in multiple environments.</span></span> <span data-ttu-id="8d0b7-184">여러 방 에뮬레이터와 함께 제공 됩니다 하 고 찾을 수 %Programfiles(x86)% %\Program 파일 (x86) \Microsoft XDE\10.0.11082.0\Plugins\Rooms 에뮬레이션을 설치한 경우.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-184">Several rooms are shipped with the emulator and once you install the emulation, you will find them in %ProgramFiles(x86)%\Program Files (x86)\Microsoft XDE\10.0.11082.0\Plugins\Rooms.</span></span> <span data-ttu-id="8d0b7-185">HoloLens를 사용 하 여 실제 환경에서 이러한 대화방의 모든 캡처된:</span><span class="sxs-lookup"><span data-stu-id="8d0b7-185">All of these rooms were captured in real environments using a HoloLens:</span></span>
* <span data-ttu-id="8d0b7-186">**DefaultRoom.xef** -TV, 커피 테이블과 두 sofas를 사용 하 여 작은 거실 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-186">**DefaultRoom.xef** - A small living room with a TV, coffee table, and two sofas.</span></span> <span data-ttu-id="8d0b7-187">에뮬레이터를 시작할 때 기본적으로 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-187">Loaded by default when you start the emulator.</span></span>
* <span data-ttu-id="8d0b7-188">**Bedroom1.xef** -책상을 사용 하 여 작은 침실 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-188">**Bedroom1.xef** - A small bedroom with a desk.</span></span>
* <span data-ttu-id="8d0b7-189">**Bedroom2.xef** -퀸 크기 평판, 장, nightstands, 및 walk-in 벽장 침실 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-189">**Bedroom2.xef** - A bedroom with a queen size bed, dresser, nightstands, and walk-in closet.</span></span>
* <span data-ttu-id="8d0b7-190">**GreatRoom.xef** -거실, 식탁, 및 주방을 사용 하 여 열려 있는 대규모 공간 훌륭한 객실을 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-190">**GreatRoom.xef** - A large open space great room with living room, dining table, and kitchen.</span></span>
* <span data-ttu-id="8d0b7-191">**LivingRoom.xef** 를 벽난로, 소파, armchairs, 거실 및 coffee 테이블과 꽃병-합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-191">**LivingRoom.xef** - A living room with a fireplace, sofa, armchairs, and a coffee table with a vase.</span></span>

<span data-ttu-id="8d0b7-192">고유한 공간과의 시뮬레이션 페이지를 사용 하 여 에뮬레이터에서 사용 하 여 기록할 수도 있습니다는 [Windows Device Portal](using-the-windows-device-portal.md) 에 HoloLens에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-192">You can also record your own rooms to use in the emulator using the Simulation page of the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens.</span></span>

<span data-ttu-id="8d0b7-193">에뮬레이터에만 표시 됩니다 홀로그램 렌더링 하 여 홀로그램 뒤 시뮬레이션 된 대화방 표시 되지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-193">On the emulator, you will only see holograms that you render and you will not see the simulated room behind the holograms.</span></span> <span data-ttu-id="8d0b7-194">이 둘 다 표시 되는 실제 HoloLens 달리 혼합 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-194">This is in contrast to the real HoloLens where you see both blended together.</span></span> <span data-ttu-id="8d0b7-195">HoloLens 에뮬레이터에서 시뮬레이트된 대화방 표시 하려는 경우에 장면에서 공간 매핑 메시 렌더링 하도록 앱을 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-195">If you want to see the simulated room in the HoloLens emulator, you will need to update your app to render the spatial mapping mesh in the scene.</span></span>

### <a name="account-tab"></a><span data-ttu-id="8d0b7-196">계정 탭</span><span class="sxs-lookup"><span data-stu-id="8d0b7-196">Account Tab</span></span>

<span data-ttu-id="8d0b7-197">계정 탭을 사용 하면 Microsoft 계정으로 로그인 하도록 에뮬레이터를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-197">The Account tab allows you to configure the emulator to sign-in with a Microsoft Account.</span></span> <span data-ttu-id="8d0b7-198">API의 사용자 계정으로 로그인 해야 하는 테스트에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-198">This is useful for testing API's that require the user to be signed-in with an account.</span></span> <span data-ttu-id="8d0b7-199">이 페이지에서 확인란을 선택 후 에뮬레이터의 후속 실행에서 로그인을 묻는는 HoloLens 시작 되는 사용자가 처음 처럼 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d0b7-199">After checking the box on this page, subsequent launches of the emulator will ask you to sign-in, just like a user would the first time the HoloLens is started.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d0b7-200">참조</span><span class="sxs-lookup"><span data-stu-id="8d0b7-200">See also</span></span>
* [<span data-ttu-id="8d0b7-201">고급 HoloLens 에뮬레이터 및 혼합 현실 시뮬레이터 입력</span><span class="sxs-lookup"><span data-stu-id="8d0b7-201">Advanced HoloLens Emulator and Mixed Reality Simulator input</span></span>](advanced-hololens-emulator-and-mixed-reality-simulator-input.md)
* [<span data-ttu-id="8d0b7-202">HoloLens 에뮬레이터 소프트웨어 기록</span><span class="sxs-lookup"><span data-stu-id="8d0b7-202">HoloLens emulator software history</span></span>](hololens-emulator-archive.md)
* [<span data-ttu-id="8d0b7-203">Unity에서 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="8d0b7-203">Spatial mapping in Unity</span></span>](spatial-mapping-in-unity.md)
* [<span data-ttu-id="8d0b7-204">DirectX의 공간 매핑</span><span class="sxs-lookup"><span data-stu-id="8d0b7-204">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
