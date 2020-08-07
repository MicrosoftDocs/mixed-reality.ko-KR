# <a name="unity"></a>[<span data-ttu-id="43f8a-101">Unity</span><span class="sxs-lookup"><span data-stu-id="43f8a-101">Unity</span></span>](#tab/unity)

![Unity](../images/unity_logo_banner.png)<br>

### <a name="1-download-the-latest-version"></a><span data-ttu-id="43f8a-103">1. 최신 버전 다운로드</span><span class="sxs-lookup"><span data-stu-id="43f8a-103">1. Download the latest version</span></span>

<span data-ttu-id="43f8a-104">새 프로젝트를 시작할 때 사용하기 가장 좋은 버전은 [Unity LTS(장기 지원)](https://unity3d.com/unity/qa/lts-releases) 스트림이며, 이것을 최신 개정판으로 업데이트하여 안정적인 최신 수정 프로그램을 선택하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-104">We recommend the [Unity LTS (Long Term Support)](https://unity3d.com/unity/qa/lts-releases) stream as the best version to use when starting new projects, updating to its latest revision to pick up the latest stable fixes.</span></span> 
* <span data-ttu-id="43f8a-105">현재 추천 사항은 아래의 MRTK v2에 필요한 LTS 빌드인 **Unity 2019**를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-105">The current recommendation is to use **Unity 2019**, which is the LTS build required for MRTK v2 below.</span></span>
* <span data-ttu-id="43f8a-106">특정 이유로 인해 다른 Unity 버전을 사용해야 하는 경우 Unity는 서로 다른 버전을 함께 설치하도록 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-106">If you need to use a different version of Unity for specific reasons, Unity supports side-by-side installs of different versions.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="43f8a-107">2. MRTK(Mixed Reality Toolkit) 가져오기</span><span class="sxs-lookup"><span data-stu-id="43f8a-107">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../images/UX/MRTK_UX_Hero.png)

<span data-ttu-id="43f8a-109">MRTK([Mixed Reality Toolkit](../mrtk-getting-started.md))는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-109">[Mixed Reality Toolkit](../mrtk-getting-started.md) (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="43f8a-110">MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-110">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="43f8a-111">도구 키트는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-111">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="43f8a-112"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="43f8a-112"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">![Unity](../images/MRTK-Unity-Banner.png)</span></span><br><span data-ttu-id="43f8a-113">**Mixed Reality Toolkit-Unity(GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="43f8a-113">**Mixed Reality Toolkit-Unity (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="43f8a-114">Unity에 MRTK를 사용하지 않으려면 모든 상호 작용과 동작을 직접 스크립팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-114">If you don't want to use MRTK for Unity, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="43f8a-115">기타 도구 [선택 사항]</span><span class="sxs-lookup"><span data-stu-id="43f8a-115">Other tools [optional]</span></span>
* <span data-ttu-id="43f8a-116"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit(GitHub)</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-116"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="43f8a-117"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common(GitHub)</a> - 공유 스크립트 및 구성 요소의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-117"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="43f8a-118">3. Mixed Reality 개발용 PC 설정</span><span class="sxs-lookup"><span data-stu-id="43f8a-118">3. Set up your PC for Mixed Reality development</span></span>

<span data-ttu-id="43f8a-119">Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-119">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="43f8a-120">또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-120">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="43f8a-121">일부 도구는 이전 운영 체제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-121">Note that not all tools are supported on older operating systems.</span></span> 

> [!NOTE]
> <span data-ttu-id="43f8a-122">HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-122">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="43f8a-123">필요에 따라 아래 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-123">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="43f8a-124">HoloLens 개발</span><span class="sxs-lookup"><span data-stu-id="43f8a-124">For HoloLens development</span></span>

<span data-ttu-id="43f8a-125">HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> 및 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a> 둘 다에 대한 시스템 요구 사항을 충족하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-125">When setting up your development PC for HoloLens development, please make sure it meets the system requirements for both <a href="https://unity3d.com/unity/system-requirements" target="_blank">Unity</a> and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="43f8a-126">[HoloLens 에뮬레이터](../using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-126">If you plan on using the [HoloLens emulator](../using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="43f8a-127">HoloLens 에뮬레이터를 시작하려면 [HoloLens 에뮬레이터 사용](../using-the-hololens-emulator.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="43f8a-127">To get started with the HoloLens emulator, see [Using the HoloLens emulator](../using-the-hololens-emulator.md).</span></span>

<span data-ttu-id="43f8a-128">HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="43f8a-128">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="43f8a-129">몰입형 (VR) 헤드셋 요구 사항</span><span class="sxs-lookup"><span data-stu-id="43f8a-129">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="43f8a-130">다음 지침은 몰입형(VR) 헤드셋 *개발 PC*에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-130">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="43f8a-131">이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양*을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="43f8a-131">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="43f8a-132">몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-132">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="43f8a-133">현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-133">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="43f8a-134">최소값</span><span class="sxs-lookup"><span data-stu-id="43f8a-134">Minimum</span></span></th><th> <span data-ttu-id="43f8a-135">권장</span><span class="sxs-lookup"><span data-stu-id="43f8a-135">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="43f8a-136">프로세서</span><span class="sxs-lookup"><span data-stu-id="43f8a-136">Processor</span></span></td><td> <span data-ttu-id="43f8a-137"><b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</span><span class="sxs-lookup"><span data-stu-id="43f8a-137"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="43f8a-138"><b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</span><span class="sxs-lookup"><span data-stu-id="43f8a-138"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-139">GPU</span><span class="sxs-lookup"><span data-stu-id="43f8a-139">GPU</span></span></td><td> <span data-ttu-id="43f8a-140"><b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="43f8a-140"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="43f8a-141"><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="43f8a-141"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-142">GPU 드라이버 WDDM 버전</span><span class="sxs-lookup"><span data-stu-id="43f8a-142">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-143">WDDM 2.2 드라이버</span><span class="sxs-lookup"><span data-stu-id="43f8a-143">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-144">열 디자인 전원</span><span class="sxs-lookup"><span data-stu-id="43f8a-144">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-145">15W 이상</span><span class="sxs-lookup"><span data-stu-id="43f8a-145">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-146">그래픽 디스플레이 포트</span><span class="sxs-lookup"><span data-stu-id="43f8a-146">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-147">헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="43f8a-147">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-148">디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="43f8a-148">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-149">해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</span><span class="sxs-lookup"><span data-stu-id="43f8a-149">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-150">메모리</span><span class="sxs-lookup"><span data-stu-id="43f8a-150">Memory</span></span></td><td> <span data-ttu-id="43f8a-151">8GB&#160;RAM 이상</span><span class="sxs-lookup"><span data-stu-id="43f8a-151">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="43f8a-152">16GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="43f8a-152">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-153">스토리지</span><span class="sxs-lookup"><span data-stu-id="43f8a-153">Storage</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-154">&gt;10GB의 추가 사용 가능 공간</span><span class="sxs-lookup"><span data-stu-id="43f8a-154">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-155">USB 포트</span><span class="sxs-lookup"><span data-stu-id="43f8a-155">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-156">헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></span><span class="sxs-lookup"><span data-stu-id="43f8a-156">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-157">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="43f8a-157">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-158">Bluetooth 4.0(액세서리 연결용)</span><span class="sxs-lookup"><span data-stu-id="43f8a-158">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

### <a name="whats-next"></a><span data-ttu-id="43f8a-159">다음 작업</span><span class="sxs-lookup"><span data-stu-id="43f8a-159">What's next?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="43f8a-160">Unity 경험 시작</span><span class="sxs-lookup"><span data-stu-id="43f8a-160">Start your Unity journey</span></span>](../unity-development-overview.md)

# <a name="unreal"></a>[<span data-ttu-id="43f8a-161">Unreal</span><span class="sxs-lookup"><span data-stu-id="43f8a-161">Unreal</span></span>](#tab/unreal)

![Unreal](../images/unreal_logo_banner.png)

### <a name="1-download-the-latest-version"></a><span data-ttu-id="43f8a-163">1. 최신 버전 다운로드</span><span class="sxs-lookup"><span data-stu-id="43f8a-163">1. Download the latest version</span></span>

<span data-ttu-id="43f8a-164">HoloLens에 기본 제공되는 지원 기능을 최대한 활용하려면 [Unreal Engine 버전 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) 이상을 설치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-164">We recommend installing [Unreal Engine version 4.25](https://docs.unrealengine.com//GettingStarted/Installation/index.html) or later to take full advantage of built-in HoloLens support.</span></span>

### <a name="2-import-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="43f8a-165">2. MRTK(Mixed Reality Toolkit) 가져오기</span><span class="sxs-lookup"><span data-stu-id="43f8a-165">2. Import Mixed Reality Toolkit (MRTK)</span></span>
![MRTK](../images/UX/MRTK_UX_Hero.png)

<span data-ttu-id="43f8a-167">MRTK(Mixed Reality Toolkit)는 혼합 현실 애플리케이션을 위한 오픈 소스 플랫폼 간 개발 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-167">Mixed Reality Toolkit (MRTK) is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="43f8a-168">MRTK는 플랫폼 간 입력 시스템, 기본 구성 요소 및 공간 상호 작용을 위한 공통 빌딩 블록을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-168">MRTK provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="43f8a-169">도구 키트는 Microsoft HoloLens, Windows Mixed Reality 몰입형(VR) 헤드셋 및 OpenVR 플랫폼을 대상으로 하는 애플리케이션 개발을 가속화하기 위해 고안되었습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-169">The toolkit is intended to accelerate the development of applications targeting Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and the OpenVR platform.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="43f8a-170"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)</span><span class="sxs-lookup"><span data-stu-id="43f8a-170"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unreal" target="_blank">![Unity](../images/MRTK-Unreal-Banner.png)</span></span><br><span data-ttu-id="43f8a-171">**Mixed Reality Toolkit-Unreal(GitHub)** </a></span><span class="sxs-lookup"><span data-stu-id="43f8a-171">**Mixed Reality Toolkit-Unreal (GitHub)**</a></span></span><br>
    :::column-end:::
:::row-end:::

> [!NOTE]
> <span data-ttu-id="43f8a-172">Unreal에 MRTK를 사용하지 않으려면 모든 상호 작용과 동작을 직접 스크립팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-172">If you don't want to use MRTK for Unreal, you'll need to script all interactions and behaviors yourself.</span></span>

#### <a name="other-tools-optional"></a><span data-ttu-id="43f8a-173">기타 도구 [선택 사항]</span><span class="sxs-lookup"><span data-stu-id="43f8a-173">Other tools [optional]</span></span>
* <span data-ttu-id="43f8a-174"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit(GitHub)</a> - HoloLens 또는 몰입형(VR) 헤드셋에서 직접 실행하지 못할 수 있으나, 대신 Windows Mixed Reality를 대상으로 하는 환경을 빌드하는 데 사용할 수 있는 코드 비트 및 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-174"><a href="https://github.com/Microsoft/MixedRealityCompanionKit" target="_blank">Mixed Reality Companion Kit (GitHub)</a> - code bits and components that might not run directly on HoloLens or immersive (VR) headsets, but instead pair with them to build experiences targeting Windows Mixed Reality.</span></span>
* <span data-ttu-id="43f8a-175"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Common(GitHub)</a> - 공유 스크립트 및 구성 요소의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-175"><a href="https://github.com/Microsoft/MixedRealityToolkit" target="_blank">Mixed Reality Toolkit - Co mmon (GitHub)</a> - a collection of shared scripts and components.</span></span>

### <a name="3-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="43f8a-176">3. 혼합 현실 개발용 PC 설정</span><span class="sxs-lookup"><span data-stu-id="43f8a-176">3. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="43f8a-177">Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-177">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="43f8a-178">또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-178">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="43f8a-179">일부 도구는 이전 운영 체제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-179">Note that not all tools are supported on older operating systems.</span></span> 

> [!NOTE]
> <span data-ttu-id="43f8a-180">HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-180">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="43f8a-181">필요에 따라 아래 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-181">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="43f8a-182">HoloLens 개발</span><span class="sxs-lookup"><span data-stu-id="43f8a-182">For HoloLens development</span></span>

<span data-ttu-id="43f8a-183">HoloLens 개발을 위해 개발 PC를 설정할 때 [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) 및 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>의 시스템 요구 사항을 충족하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-183">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for [Unreal](https://docs.unrealengine.com/GettingStarted/RecommendedSpecifications/index.html) and and <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="43f8a-184">[HoloLens 에뮬레이터](../using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-184">If you plan on using the [HoloLens emulator](../using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="43f8a-185">HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="43f8a-185">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="43f8a-186">몰입형 (VR) 헤드셋 요구 사항</span><span class="sxs-lookup"><span data-stu-id="43f8a-186">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="43f8a-187">다음 지침은 몰입형(VR) 헤드셋 *개발 PC*에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-187">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="43f8a-188">이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양*을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="43f8a-188">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="43f8a-189">몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-189">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="43f8a-190">현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-190">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="43f8a-191">최소값</span><span class="sxs-lookup"><span data-stu-id="43f8a-191">Minimum</span></span></th><th> <span data-ttu-id="43f8a-192">권장</span><span class="sxs-lookup"><span data-stu-id="43f8a-192">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="43f8a-193">프로세서</span><span class="sxs-lookup"><span data-stu-id="43f8a-193">Processor</span></span></td><td> <span data-ttu-id="43f8a-194"><b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</span><span class="sxs-lookup"><span data-stu-id="43f8a-194"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="43f8a-195"><b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</span><span class="sxs-lookup"><span data-stu-id="43f8a-195"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-196">GPU</span><span class="sxs-lookup"><span data-stu-id="43f8a-196">GPU</span></span></td><td> <span data-ttu-id="43f8a-197"><b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="43f8a-197"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="43f8a-198"><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="43f8a-198"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-199">GPU 드라이버 WDDM 버전</span><span class="sxs-lookup"><span data-stu-id="43f8a-199">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-200">WDDM 2.2 드라이버</span><span class="sxs-lookup"><span data-stu-id="43f8a-200">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-201">열 디자인 전원</span><span class="sxs-lookup"><span data-stu-id="43f8a-201">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-202">15W 이상</span><span class="sxs-lookup"><span data-stu-id="43f8a-202">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-203">그래픽 디스플레이 포트</span><span class="sxs-lookup"><span data-stu-id="43f8a-203">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-204">헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="43f8a-204">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-205">디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="43f8a-205">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-206">해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</span><span class="sxs-lookup"><span data-stu-id="43f8a-206">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-207">메모리</span><span class="sxs-lookup"><span data-stu-id="43f8a-207">Memory</span></span></td><td> <span data-ttu-id="43f8a-208">8GB&#160;RAM 이상</span><span class="sxs-lookup"><span data-stu-id="43f8a-208">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="43f8a-209">16GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="43f8a-209">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-210">스토리지</span><span class="sxs-lookup"><span data-stu-id="43f8a-210">Storage</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-211">&gt;10GB의 추가 사용 가능 공간</span><span class="sxs-lookup"><span data-stu-id="43f8a-211">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-212">USB 포트</span><span class="sxs-lookup"><span data-stu-id="43f8a-212">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-213">헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></span><span class="sxs-lookup"><span data-stu-id="43f8a-213">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-214">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="43f8a-214">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-215">Bluetooth 4.0(액세서리 연결용)</span><span class="sxs-lookup"><span data-stu-id="43f8a-215">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

### <a name="whats-next"></a><span data-ttu-id="43f8a-216">다음 작업</span><span class="sxs-lookup"><span data-stu-id="43f8a-216">What's next?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="43f8a-217">Unreal 경험 시작</span><span class="sxs-lookup"><span data-stu-id="43f8a-217">Start your Unreal journey</span></span>](../unreal-development-overview.md)

# <a name="native-openxr"></a>[<span data-ttu-id="43f8a-218">네이티브(OpenXR)</span><span class="sxs-lookup"><span data-stu-id="43f8a-218">Native (OpenXR)</span></span>](#tab/native)

 ![네이티브 앱 개발](../images/native_logo_banner.png)

<span data-ttu-id="43f8a-220">네이티브 OpenXR 개발의 경우 다운로드할 엔진이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-220">Native OpenXR development doesn't have an engine for you to download.</span></span> <span data-ttu-id="43f8a-221">개발을 시작하는 데 필요한 모든 것은 [OpenXR 시작](../openxr-getting-started.md) 문서에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-221">You can find everything you need to begin development in the [Getting started with OpenXR](../openxr-getting-started.md) document.</span></span>

### <a name="1-set-up-your-pc-for-mixed-reality-development"></a><span data-ttu-id="43f8a-222">1. 혼합 현실 개발용 PC 설정</span><span class="sxs-lookup"><span data-stu-id="43f8a-222">1. Set up your PC for mixed reality development</span></span>

<span data-ttu-id="43f8a-223">Windows 10 SDK는 Windows 10 운영 체제에서 가장 잘 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-223">The Windows 10 SDK works best on the Windows 10 operating system.</span></span> <span data-ttu-id="43f8a-224">또한 이 SDK는 Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-224">This SDK is also supported on Windows 8.1, Windows 8, Windows 7, Windows Server 2012, Windows Server 2008 R2.</span></span> <span data-ttu-id="43f8a-225">일부 도구는 이전 운영 체제에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-225">Note that not all tools are supported on older operating systems.</span></span>

#### <a name="for-hololens-development"></a><span data-ttu-id="43f8a-226">HoloLens 개발</span><span class="sxs-lookup"><span data-stu-id="43f8a-226">For HoloLens development</span></span>

<span data-ttu-id="43f8a-227">HoloLens 개발을 위해 개발 PC를 설정할 때 <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>의 시스템 요구 사항을 충족하는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-227">When setting up your development PC for HoloLens development, please make sure you meet the system requirements for <a href="https://docs.microsoft.com//visualstudio/releases/2019/system-requirements" target="_blank">Visual Studio</a>.</span></span> <span data-ttu-id="43f8a-228">[HoloLens 에뮬레이터](../using-the-hololens-emulator.md)를 사용하려는 경우 PC가 [HoloLens 에뮬레이터 시스템 요구 사항](../using-the-hololens-emulator.md#hololens-emulator-system-requirements)도 충족하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-228">If you plan on using the [HoloLens emulator](../using-the-hololens-emulator.md), you'll want to make sure your PC meets the [HoloLens emulator system requirements](../using-the-hololens-emulator.md#hololens-emulator-system-requirements) as well.</span></span>

<span data-ttu-id="43f8a-229">HoloLens와 Windows Mixed Reality 몰입형(VR) 헤드셋용으로 개발을 수행하려는 경우 아래 섹션에 제공되는 시스템 권장 사항 및 요구 사항을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="43f8a-229">If you plan to develop for both HoloLens and Windows Mixed Reality immersive (VR) headsets, use the system recommendations and requirements in the section below.</span></span>

> [!NOTE]
> <span data-ttu-id="43f8a-230">HoloLens, VR 몰입형 헤드셋 또는 둘 다를 위한 앱을 개발하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-230">You can develop and deploy your apps for HoloLens, VR immersive headsets, or both.</span></span> <span data-ttu-id="43f8a-231">필요에 따라 아래 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-231">Make sure you fulfill the requirements below depending on your needs.</span></span>

#### <a name="immersive-vr-headset-requirements"></a><span data-ttu-id="43f8a-232">몰입형 (VR) 헤드셋 요구 사항</span><span class="sxs-lookup"><span data-stu-id="43f8a-232">Immersive (VR) headset requirements</span></span>

>[!NOTE]
><span data-ttu-id="43f8a-233">다음 지침은 몰입형(VR) 헤드셋 *개발 PC*에 대한 현재 최소 및 권장 사양으로, 정기적으로 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-233">The following guidelines are the current minimum and recommended specs for your immersive (VR) headset *development PC*, and are updated regularly.</span></span>

>[!WARNING]
><span data-ttu-id="43f8a-234">이 지침을 몰입형 (VR) 헤드셋 앱 또는 게임을 대상으로 하는 *소비자 PC 사양*을 나타내는 [최소 PC 하드웨어 호환성 지침](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)과 혼동하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="43f8a-234">Do not confuse this with the [minimum PC hardware compatibility guidelines](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines), which outlines the *consumer PC specs* to which you should target your immersive (VR) headset app or game.</span></span>

<span data-ttu-id="43f8a-235">몰입형 헤드셋 개발 PC에 전체 크기 HDMI 및/또는 USB 3.0 포트가 없는 경우 헤드셋에 연결하기 위한 [어댑터](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-235">If your immersive headset development PC does not have full-sized HDMI and/or USB 3.0 ports, you'll need [adapters](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs) to connect your headset.</span></span>

<span data-ttu-id="43f8a-236">현재, 일부 하드웨어 구성, 특히 하이브리드 그래픽이 있는 노트북에서 [알려진 이슈](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43f8a-236">There are currently [known issues](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality) with some hardware configurations, particularly notebooks that have hybrid graphics.</span></span>

<table>
<tr>
<th></th><th> <span data-ttu-id="43f8a-237">최소값</span><span class="sxs-lookup"><span data-stu-id="43f8a-237">Minimum</span></span></th><th> <span data-ttu-id="43f8a-238">권장</span><span class="sxs-lookup"><span data-stu-id="43f8a-238">Recommended</span></span></th>
</tr><tr>
<td> <span data-ttu-id="43f8a-239">프로세서</span><span class="sxs-lookup"><span data-stu-id="43f8a-239">Processor</span></span></td><td> <span data-ttu-id="43f8a-240"><b>노트북:</b> Intel Mobile Core i5 7세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>데스크톱:</b> Intel Desktop i5 6세대 CPU, 듀얼 코어, 하이퍼 스레딩 <b>또는</b> 동급 사양의 AMD FX4350 4.2Ghz 쿼드 코어</span><span class="sxs-lookup"><span data-stu-id="43f8a-240"><b>Notebook:</b> Intel Mobile Core i5 7th generation CPU, Dual-Core with Hyper Threading <b>Desktop:</b> Intel Desktop i5 6th generation CPU, Dual-Core with Hyper Threading <b>OR</b> AMD FX4350 4.2Ghz Quad-Core equivalent</span></span></td><td> <span data-ttu-id="43f8a-241"><b>데스크톱:</b> Intel Desktop i7 6세대(6 코어) <b>또는</b> AMD Ryzen 5 1600(6코어, 12스레드)</span><span class="sxs-lookup"><span data-stu-id="43f8a-241"><b>Desktop:</b> Intel Desktop i7 6th generation (6 Core) <b>OR</b> AMD Ryzen 5 1600 (6 Core, 12 threads)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-242">GPU</span><span class="sxs-lookup"><span data-stu-id="43f8a-242">GPU</span></span></td><td> <span data-ttu-id="43f8a-243"><b>노트북:</b> NVIDIA GTX 965M, AMD RX 460M(2GB) 동급 또는 그 이상의 DX12 지원 GPU <b>데스크톱:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="43f8a-243"><b>Notebook:</b> NVIDIA GTX 965M, AMD RX 460M (2GB) equivalent or greater DX12 capable GPU <b>Desktop:</b> NVIDIA GTX 960/1050, AMD Radeon RX 460 (2GB) equivalent or greater DX12 capable GPU</span></span></td><td><span data-ttu-id="43f8a-244"><b>데스크톱:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480(2GB) 동급 또는 그 이상의 DX12 지원 GPU</span><span class="sxs-lookup"><span data-stu-id="43f8a-244"><b>Desktop:</b> NVIDIA GTX 980/1060, AMD Radeon RX 480 (2GB) equivalent or greater DX12 capable GPU</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-245">GPU 드라이버 WDDM 버전</span><span class="sxs-lookup"><span data-stu-id="43f8a-245">GPU driver WDDM version</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-246">WDDM 2.2 드라이버</span><span class="sxs-lookup"><span data-stu-id="43f8a-246">WDDM 2.2 driver</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-247">열 디자인 전원</span><span class="sxs-lookup"><span data-stu-id="43f8a-247">Thermal Design Power</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-248">15W 이상</span><span class="sxs-lookup"><span data-stu-id="43f8a-248">15W or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-249">그래픽 디스플레이 포트</span><span class="sxs-lookup"><span data-stu-id="43f8a-249">Graphics display ports</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-250">헤드셋용 가용 그래픽 디스플레이 포트&#160;1개(60Hz 헤드셋용 HDMI 1.4 또는 DisplayPort 1.2, 90Hz 헤드셋용 HDMI 2.0 또는 DisplayPort 1.2)</span><span class="sxs-lookup"><span data-stu-id="43f8a-250">1x available graphics display port for&#160;headset (HDMI 1.4 or DisplayPort 1.2 for 60Hz headsets, HDMI 2.0 or DisplayPort 1.2 for 90Hz headsets)</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-251">디스플레이 해상도</span><span class="sxs-lookup"><span data-stu-id="43f8a-251">Display resolution</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-252">해상도: SVGA(800x600) 이상 비트 수준: 픽셀당 32비트 색상</span><span class="sxs-lookup"><span data-stu-id="43f8a-252">Resolution: SVGA (800x600) or greater Bit depth: 32 bits of color per pixel</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-253">메모리</span><span class="sxs-lookup"><span data-stu-id="43f8a-253">Memory</span></span></td><td> <span data-ttu-id="43f8a-254">8GB&#160;RAM 이상</span><span class="sxs-lookup"><span data-stu-id="43f8a-254">8&#160;GB of RAM or greater</span></span></td><td> <span data-ttu-id="43f8a-255">16GB RAM 이상</span><span class="sxs-lookup"><span data-stu-id="43f8a-255">16 GB of RAM or greater</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-256">스토리지</span><span class="sxs-lookup"><span data-stu-id="43f8a-256">Storage</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-257">&gt;10GB의 추가 사용 가능 공간</span><span class="sxs-lookup"><span data-stu-id="43f8a-257">&gt;10 GB additional free space</span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-258">USB 포트</span><span class="sxs-lookup"><span data-stu-id="43f8a-258">USB Ports</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-259">헤드셋용 가용 USB 포트 1개(USB 3.0 A형) <b>참고: USB은 최소 900mA를 제공해야 합니다.</b></span><span class="sxs-lookup"><span data-stu-id="43f8a-259">1x available USB port for headset (USB 3.0 Type-A) <b>Note: USB must supply a minimum of 900mA</b></span></span></td>
</tr><tr>
<td> <span data-ttu-id="43f8a-260">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="43f8a-260">Bluetooth</span></span></td><td colspan="2"> <span data-ttu-id="43f8a-261">Bluetooth 4.0(액세서리 연결용)</span><span class="sxs-lookup"><span data-stu-id="43f8a-261">Bluetooth 4.0 (for accessory connectivity)</span></span></td>
</tr>
</table>

### <a name="whats-next"></a><span data-ttu-id="43f8a-262">다음 작업</span><span class="sxs-lookup"><span data-stu-id="43f8a-262">What's next?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="43f8a-263">기본 경험 시작</span><span class="sxs-lookup"><span data-stu-id="43f8a-263">Start your Native journey</span></span>](../directx-development-overview.md)


