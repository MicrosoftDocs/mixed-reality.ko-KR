---
title: 시작 자습서 - 2. 프로젝트 및 첫 번째 애플리케이션 초기화
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 56adb4bfc66768684c8269c0f0cafd70c486ea8a
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376210"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="65891-105">2. 프로젝트 및 첫 번째 애플리케이션 초기화</span><span class="sxs-lookup"><span data-stu-id="65891-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="65891-106">개요</span><span class="sxs-lookup"><span data-stu-id="65891-106">Overview</span></span>

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
<span data-ttu-id="65891-107">이 첫 번째 자습서에서는 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK(Mixed Reality Toolkit)</a>에서 제공해야 하는 기능 중 일부에 대해 알아보고, HoloLens 2용 첫 번째 애플리케이션을 시작하고 이를 디바이스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-107">In this first tutorial, you will learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="65891-108">목표</span><span class="sxs-lookup"><span data-stu-id="65891-108">Objectives</span></span>

* <span data-ttu-id="65891-109">HoloLens 개발을 위한 Unity 구성</span><span class="sxs-lookup"><span data-stu-id="65891-109">Configure Unity for HoloLens development</span></span>
* <span data-ttu-id="65891-110">자산 가져오기 및 장면 설정</span><span class="sxs-lookup"><span data-stu-id="65891-110">Import assets and set up the scene</span></span>
* <span data-ttu-id="65891-111">공간 매핑 메시, 손 메시 및 프레임 속도 카운터 시각화</span><span class="sxs-lookup"><span data-stu-id="65891-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65891-112">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="65891-112">Prerequisites</span></span>

* <span data-ttu-id="65891-113">올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="65891-113">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="65891-114">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="65891-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="65891-115">몇 가지 기본 C# 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="65891-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="65891-116">[개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="65891-116">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="65891-117">Unity 2019.2.X가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="65891-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65891-118">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다.</span><span class="sxs-lookup"><span data-stu-id="65891-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="65891-119">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="65891-120">새 Unity 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="65891-120">Create new Unity project</span></span>

<span data-ttu-id="65891-121">**Unity Hub**를 시작하고, **Projects(프로젝트)** 탭을 선택한 다음, **New(새로 만들기)** 단추 옆의 **아래쪽 화살표**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

<span data-ttu-id="65891-123">위의 [필수 구성 요소](#prerequisites) 섹션에 지정된 Unity 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-123">Select the Unity version specified in the [Prerequisites](#prerequisites) section above:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

<span data-ttu-id="65891-125">Create a new project(새 프로젝트 만들기) 창에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-125">In the Create a new project window:</span></span>

* <span data-ttu-id="65891-126">**Templates(템플릿)** 가 **3D**로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-126">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="65891-127">적합한 **Project Name(프로젝트 이름)** 을 입력합니다(예: _MRTK 자습서_).</span><span class="sxs-lookup"><span data-stu-id="65891-127">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="65891-128">프로젝트를 저장할 적합한 **Location(위치)** 을 선택합니다(예: _D:\MixedRealityLearning_).</span><span class="sxs-lookup"><span data-stu-id="65891-128">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="65891-129">**Create(만들기)** 단추를 클릭하여 새 Unity 프로젝트를 만들고 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-129">Click the **Create** button to create and launch your new Unity project</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="65891-131">Windows에서 작업하는 경우 MAX_PATH 제한은 255자입니다.</span><span class="sxs-lookup"><span data-stu-id="65891-131">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="65891-132">Unity는 이러한 제한의 영향을 받으며, 파일 경로가 255자를 초과하면 컴파일이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-132">Unity is affected by these limits and may fail to compile if any file path is longer than 255 characters.</span></span> <span data-ttu-id="65891-133">따라서 Unity 프로젝트를 드라이브의 루트에 최대한 가깝게 저장하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-133">Consequently, it is strongly recommended to store your Unity project as close to the root of the drive as possible.</span></span>

<span data-ttu-id="65891-134">Unity에서 프로젝트가 만들어질 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="65891-134">Wait for Unity to create the project:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="65891-136">Windows Mixed Reality를 위한 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="65891-136">Configure the Unity project for Windows Mixed Reality</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="65891-137">이 섹션에서는 빌드 플랫폼을 전환하고, 가상 현실과 공간 인식을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-137">In this section, you will switch build platform, enable virtual reality, and enable spatial perception.</span></span>

### <a name="1-switch-build-platform"></a><span data-ttu-id="65891-138">1. 빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="65891-138">1. Switch build platform</span></span>

<span data-ttu-id="65891-139">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65891-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

<span data-ttu-id="65891-141">Build Settings 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고, **Switch Platform(플랫폼 전환)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-141">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

<span data-ttu-id="65891-143">Unity에서 플랫폼 전환이 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="65891-143">Wait for Unity to finish switching the platform:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

<span data-ttu-id="65891-145">Unity에서 플랫폼 전환이 완료되면 빨간색 **x** 아이콘을 클릭하여 Build Settings 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-145">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a><span data-ttu-id="65891-147">2. 가상 현실 사용</span><span class="sxs-lookup"><span data-stu-id="65891-147">2. Enable virtual reality</span></span>

> [!NOTE]
> <span data-ttu-id="65891-148">양안식 비전, 즉 각 눈에 대해 다른 이미지 렌더링을 사용하도록 설정하므로 가상 현실을 사용하도록 설정하는 것은 혼합 현실 및 확대된 현실 헤드셋에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="65891-148">Enabling virtual reality also applies to mixed reality and augmented reality headsets because it refers to enabling stereoscopic vision, i.e. rendering different images for each eye.</span></span>

<span data-ttu-id="65891-149">Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65891-149">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

<span data-ttu-id="65891-151">Project Settings 창에서 **Player(플레이어)**  > **XR Settings(XR 설정)** 를 차례로 선택하여 XR Settings를 펼칩니다.</span><span class="sxs-lookup"><span data-stu-id="65891-151">In the Project Settings window, select **Player** > **XR Settings** to expand the XR Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

<span data-ttu-id="65891-153">XR Settings에서 **Virtual Reality Supported(가상 현실 지원됨)** 확인란을 선택하여 가상 현실을 사용하도록 설정한 다음, **+** 아이콘을 클릭하고 **Windows Mixed Reality**를 선택하여 Windows Mixed Reality SDK를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-153">In the XR Settings, check the **Virtual Reality Supported** checkbox to enable virtual reality, then click the **+** icon and select **Windows Mixed Reality** to add the Windows Mixed Reality SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

<span data-ttu-id="65891-155">Unity에서 SDK 추가가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="65891-155">Wait for Unity to finish adding the SDK:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

<span data-ttu-id="65891-157">Unity에서 SDK 추가가 완료되면 다음과 같이 XR Settings를 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-157">When Unity has finished adding the SDK, optimize the XR Settings as follows:</span></span>

* <span data-ttu-id="65891-158">Windows Mixed Reality **Depth Format(깊이 형식)** 을 **16-bit depth(16비트 깊이)** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-158">Set Windows Mixed Reality **Depth Format** to **16-bit depth**</span></span>
* <span data-ttu-id="65891-159">Windows Mixed Reality **Enable Depth Sharing(깊이 공유 사용)** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-159">Check the Windows Mixed Reality **Enable Depth Sharing** checkbox</span></span>
* <span data-ttu-id="65891-160">스테레오 **Rendering Mode(렌더링 모드)\*** 를 **Single Pass Instanced**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-160">Set Stereo **Rendering Mode\*** to **Single Pass Instanced**</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> <span data-ttu-id="65891-162">Windows Mixed Reality용 Unity를 최적화하는 방법에 대해 자세히 알아보려면 [Unity 추천 설정](recommended-settings-for-unity.md) 설명서를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-162">To learn more about optimizing Unity for Windows Mixed Reality, you can refer to the [Recommended settings for Unity](recommended-settings-for-unity.md) documentation.</span></span>

### <a name="3-enable-spatial-perception"></a><span data-ttu-id="65891-163">3. 공간 인식 사용</span><span class="sxs-lookup"><span data-stu-id="65891-163">3. Enable spatial perception</span></span>

> [!NOTE]
> <span data-ttu-id="65891-164">공간 인식을 사용하면 Windows Mixed Reality 디바이스에서 공간 매핑 메시를 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-164">Spatial perception allows visualization of the spatial mapping mesh on Windows Mixed Reality devices.</span></span>

<span data-ttu-id="65891-165">Project Settings(프로젝트 설정) 창에서 **Player(플레이어)**  > **Publishing Settings(게시 설정)** 를 차례로 선택하여 Publishing Settings를 펼칩니다.</span><span class="sxs-lookup"><span data-stu-id="65891-165">In the Project Settings window, select **Player** > **Publishing Settings** to expand the Publishing Settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

<span data-ttu-id="65891-167">Publishing Settings에서 **Capabilities(기능)** 섹션까지 아래로 스크롤하고 **SpatialPerception** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-167">In the Publishing Settings, scroll down to the **Capabilities** section and check the **SpatialPerception** checkbox:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

<span data-ttu-id="65891-169">Publishing Settings 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-169">Close the Project Settings window.</span></span>

## <a name="import-textmesh-pro-essential-resources"></a><span data-ttu-id="65891-170">TextMesh Pro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="65891-170">Import TextMesh Pro Essential Resources</span></span>

> [!NOTE]
> <span data-ttu-id="65891-171">Mixed Reality Toolkit의 UI 요소에 필요하므로 이 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="65891-171">We are importing this package because it is required by Mixed Reality Toolkit's UI elements.</span></span>

<span data-ttu-id="65891-172">Unity 메뉴에서 **Window(창)**  > **TextMeshPro** > **Import TMP Essential Resources(TMP 필수 리소스 가져오기)** 를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-172">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

<span data-ttu-id="65891-174">Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="65891-174">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="65891-176">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="65891-176">Import the Mixed Reality Toolkit</span></span>

<span data-ttu-id="65891-177">다음 Unity 사용자 지정 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-177">Download the Unity custom package:</span></span>

* [<span data-ttu-id="65891-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="65891-178">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.3.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage)

<span data-ttu-id="65891-179">Unity 메뉴에서 **Assets(자산)**  > **Import Package(패키지 가져오기)**  > **Custom Package(사용자 지정 패키지)...** 를 차례로 선택하여 Import package(패키지 가져오기)... 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65891-179">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

<span data-ttu-id="65891-181">Import package... 창에서 다운로드한 **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage**를 선택하고 **Open(열기)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-181">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.3.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

<span data-ttu-id="65891-183">Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="65891-183">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a><span data-ttu-id="65891-185">Mixed Reality Toolkit용 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="65891-185">Configure the Unity project for the Mixed Reality Toolkit</span></span>

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

<span data-ttu-id="65891-186">패키지를 가져오면 MRTK Project Configurator(MRTK 프로젝트 구성기) 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65891-186">After the package has been imported, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="65891-187">그렇지 않으면 Unity 메뉴에서 **Mixed Reality Toolkit** > **Utilities(유틸리티)**  > **Configure Unity Project(Unity 프로젝트 구성)** 를 차례로 선택하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65891-187">If it does not, open it by selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** in the Unity menu.</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

<span data-ttu-id="65891-189">MRTK Project Configurator 창에서 **Modify Configurations(구성 수정)** 섹션을 펼치고, **Enable MSBuild for Unity(Unity용 MSBuild 사용)** 확인란을 <u>선택 취소</u>하고, 다른 모든 옵션이 선택되었는지 확인한 다음, **Apply(적용)** 단추를 클릭하여 해당 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-189">In the MRTK Project Configurator window, expand the **Modify Configurations** section, <u>uncheck</u> the **Enable MSBuild for Unity** checkbox, ensure all other options are checked, and click the **Apply** button to apply the settings:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> <span data-ttu-id="65891-191">Unity용 MSBuild는 사용할 SDK 중 일부만 지원할 수 있으며, 사용하도록 설정된 후에 이를 사용하지 않도록 설정하는 것이 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-191">MSBuild for Unity may not support all SDKs you will be using and can be challenging to disable after it has been enabled.</span></span> <span data-ttu-id="65891-192">따라서 Unity용 MSBuild를 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-192">Consequently, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="65891-193">Mixed Reality Toolkit 구성</span><span class="sxs-lookup"><span data-stu-id="65891-193">Configure the Mixed Reality Toolkit</span></span>
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

<span data-ttu-id="65891-194">Unity 메뉴에서 **Mixed Reality Toolkit** > **Add to Scene and Configure(장면에 추가 및 구성)...** 를 차례로 선택하여 Mixed Reality Toolkit를 현재 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-194">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the Mixed Reality Toolkit to your current scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

<span data-ttu-id="65891-196">Hierarchy(계층 구조) 창에서 MixedRealityToolkit 개체를 선택한 상태로 검사기 창에서 Mixed Reality Toolkit 구성 프로필이 **DefaultMixedRealityToolkitConfigurationProfile**로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-196">With the MixedRealityToolkit object selected in the Hierarchy window, in the Inspector window, verify the Mixed Reality Toolkit configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

> [!IMPORTANT]
> <span data-ttu-id="65891-198">일반적으로는 HoloLens 2용으로 개발할 때 DefaultHoloLens2ConfigurationProfile을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-198">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens 2.</span></span> <span data-ttu-id="65891-199">그러나 여기에서는 이 자습서의 목적상 DefaultMixedRealityToolkitConfigurationProfile를 사용하고, 다음 자습서인 [사용자 인터페이스 만들기 및 Mixed Reality Toolkit 구성](mrlearning-base-ch2.md)에서 DefaultHoloLens2ConfigurationProfile을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-199">However, for the purpose of this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Creating user interface and configure Mixed Reality Toolkit](mrlearning-base-ch2.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="65891-200">Unity 메뉴에서 **File(파일)**  > **Save As(다른 이름으로 저장)...** 를 차례로 선택하여 Save Scene(장면 저장) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65891-200">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

<span data-ttu-id="65891-202">Save Scene 창에서 프로젝트의 **Scenes(장면)** 폴더로 이동하여 장면에 적합한 이름(예: _시작_)을 지정하고, **Save(저장)** 단추를 클릭하여 장면을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-202">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="65891-204">디바이스로 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="65891-204">Build your application to your device</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="65891-205">1. Unity 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="65891-205">1. Build the Unity project</span></span>

<span data-ttu-id="65891-206">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65891-206">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="65891-207">Build Settings 창에서 **Add Open Scenes(열려 있는 장면 추가)** 단추를 클릭하여 현재 장면을 **Scenes In Build(빌드 중인 장면)** 목록에 추가한 다음, **Build(빌드)** 단추를 클릭하여 Build Universal Windows Platform(유니버설 Windows 플랫폼 빌드) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65891-207">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

<span data-ttu-id="65891-209">Build Universal Windows Platform 창에서 빌드를 저장할 적합한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택하고, 새 폴더를 만들어 적합한 이름(예: _GettingStarted_)을 지정한 다음, **Select Folder(폴더 선택)** 단추를 클릭하여 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-209">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

<span data-ttu-id="65891-211">Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="65891-211">Wait for Unity to finish the build process:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="65891-213">2. 애플리케이션 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="65891-213">2. Build and deploy the application</span></span>

<span data-ttu-id="65891-214">빌드 프로세스가 완료되면 Unity에서 빌드를 저장한 위치를 열라는 메시지를 Windows 파일 탐색기에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-214">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="65891-215">폴더 내부를 탐색하고 솔루션 파일을 두 번 클릭하여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65891-215">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> <span data-ttu-id="65891-217">Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 [도구 설치](install-the-tools.md) 설명서에서 지정한 대로 모든 필수 구성 요소가 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-217">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the [Install the Tools](install-the-tools.md) documentation.</span></span>

<span data-ttu-id="65891-218">Visual Studio에서 **마스터** 또는 **릴리스** 구성, **ARM** 아키텍처 및 **디바이스**를 대상으로 선택하여 HoloLens 2를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-218">Configure Visual Studio for HoloLens 2 by selecting the **Master** or **Release** configuration, the **ARM** architecture, and **Device** as target:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

> [!NOTE]
> <span data-ttu-id="65891-220">디바이스가 옵션으로 표시되지 않는 경우 기본 시작 프로젝트를 IC2Lpp 프로젝트에서 UWP 프로젝트로 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-220">If you don't see Device as an option you may need to change the default start up project from the IC2Lpp project to your UWP Project.</span></span> <span data-ttu-id="65891-221">**솔루션 탐색기**에서 **yourprojectname(유니버설 Windows)** 을 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-221">In the **Solution Explorer**, right click on **yourprojectname (Universal Windows)** and select **Set as StartUp Project**.</span></span> 

<span data-ttu-id="65891-222">HoloLens 2를 컴퓨터에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-222">Connect your HoloLens 2 to your computer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65891-223">디바이스에 빌드하기 전에 디바이스가 [개발자 모드]에 있고 개발 머신과 페어링되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-223">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="65891-224">이 두 단계는 모두 [이러한 지침](using-visual-studio.md)에 따라 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-224">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

<span data-ttu-id="65891-225">마지막 단계는 **디버그** > **디버깅하지 않고 시작**을 차례로 선택하여 빌드하고 디바이스에 배포하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="65891-225">The final step is to build and deploy to your device by selecting **Debug** > **Start Without Debugging**:</span></span>

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

<span data-ttu-id="65891-227">이러한 지침에서는 HoloLens 2 디바이스에 배포한다고 가정하지만, [HoloLens 2 에뮬레이터](using-the-hololens-emulator.md)에 배포하거나 [사이드로드용 앱 패키지](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-227">While these instructions assume you will be deploying to a HoloLens 2 device, you can also deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).</span></span>

<span data-ttu-id="65891-228">[디버깅하지 않고 시작]을 선택하면 빌드 성공 시 애플리케이션이 디바이스에서 즉시 시작되지만, 디버거가 연결되지 않고 정보가 Visual Studio에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-228">Selecting Start without Debugging causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="65891-229">따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-229">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

<span data-ttu-id="65891-230">애플리케이션을 자동으로 시작하지 않고 디바이스에 배포하려면 빌드 > 솔루션 배포를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-230">To deploy to your device without having the application start automatically, you can select Build > Deploy Solution.</span></span>

## <a name="congratulations"></a><span data-ttu-id="65891-231">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-231">Congratulations</span></span>

<!-- TODO: Consider cleanup and adding in app screenshots -->
<span data-ttu-id="65891-232">이제 첫 번째 HoloLens 2 애플리케이션을 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-232">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="65891-233">연습을 진행하면서 HoloLens 2에서 인식한 모든 표면이 포함된 공간 매핑 메시가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65891-233">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="65891-234">또한 손을 추적하기 위한 손 및 손가락의 표시기와 애플리케이션 성능을 감시하기 위한 프레임 속도 카운터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="65891-234">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="65891-235">이러한 기능은 Mixed Reality Toolkit과 함께 기본적으로 포함되어 있는 기본적인 기능 중 일부에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-235">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="65891-236">다음 자습서에서는 더 많은 콘텐츠와 대화형 작업을 장면에 추가하여 HoloLens 2 및 Mixed Reality Toolkit의 기능을 완벽하게 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-236">In the tutorials to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="65891-237">앱에서 진단 프로파일러를 확인할 수 있습니다. **Toggle Diagnostics** 음성 명령을 사용하여 표시 유형을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65891-237">In the app, you may notice the Diagnostics profiler, you can toggle it's visibility using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="65891-238">그러나 일반적으로 개발 중에 프로파일러를 항상 표시하여 앱의 변경이 성능에 영향을 줄 수 있는 시기를 파악하는 것이 좋습니다. 예를 들어 HoloLens 2 애플리케이션은 [60FPS로 계속 실행](understanding-performance-for-mixed-reality.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65891-238">However, it is generally recommended to keep the profiler visible at all times during development to understand when changes to the app may have impacted performance, for example, HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="65891-239">다음 자습서: 3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 도구 키트 구성</span><span class="sxs-lookup"><span data-stu-id="65891-239">Next Tutorial: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)
