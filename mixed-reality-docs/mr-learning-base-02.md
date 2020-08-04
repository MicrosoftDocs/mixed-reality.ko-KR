---
title: 시작 자습서 - 2. 프로젝트 초기화 및 첫 번째 애플리케이션 배포
description: 이 과정에서는 MRTK(Mixed Reality Toolkit)를 사용하여 혼합 현실 애플리케이션을 만드는 방법을 보여줍니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 5cac7d6f776619cbc2a0e0891b7915b656708726
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376655"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="4a2c5-105">2. 프로젝트 초기화 및 첫 번째 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="4a2c5-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="4a2c5-106">개요</span><span class="sxs-lookup"><span data-stu-id="4a2c5-106">Overview</span></span>

<span data-ttu-id="4a2c5-107">이 자습서에서는 새 Unity 프로젝트를 만들어서 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK(Mixed Reality Toolkit)</a> 개발에 맞게 구성하고, MRTK를 가져오는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="4a2c5-108">Visual Studio에서 HoloLens 2 또는 에뮬레이터로 기본 Unity 샘플 장면을 구성, 빌드 및 배포하는 과정도 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-108">You'll also walk through configuring, building, and deploying the basic Unity sample scene from Visual Studio to your HoloLens 2 or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="4a2c5-109">목표</span><span class="sxs-lookup"><span data-stu-id="4a2c5-109">Objectives</span></span>

* <span data-ttu-id="4a2c5-110">HoloLens 개발을 위해 Unity를 구성하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="4a2c5-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="4a2c5-111">HoloLens에 앱을 빌드하고 배포하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="4a2c5-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="4a2c5-112">공간 매핑 메시, 손 메시 및 프레임 속도 카운터 경험하기</span><span class="sxs-lookup"><span data-stu-id="4a2c5-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="4a2c5-113">Unity 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="4a2c5-113">Creating the Unity project</span></span>

<span data-ttu-id="4a2c5-114">**Unity Hub**를 시작하고, **Projects(프로젝트)** 탭을 선택한 다음, **New(새로 만들기)** 단추 옆의 **아래쪽 화살표**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="4a2c5-116">드롭다운에서 [필수 구성 요소](mr-learning-base-01.md#prerequisites)에 지정된 Unity **버전**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="4a2c5-118">Unity 허브에서 특정 Unity 버전을 사용할 수 없으면 Unity의 <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>(아카이브 다운로드)에서 설치를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="4a2c5-119">Create a new project(새 프로젝트 만들기) 창에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-119">In the Create a new project window:</span></span>

* <span data-ttu-id="4a2c5-120">**Templates(템플릿)** 가 **3D**로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="4a2c5-121">적합한 **Project Name(프로젝트 이름)** 을 입력합니다(예: _MRTK 자습서_).</span><span class="sxs-lookup"><span data-stu-id="4a2c5-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="4a2c5-122">프로젝트를 저장할 적합한 **Location(위치)** 을 선택합니다(예: _D:\MixedRealityLearning_).</span><span class="sxs-lookup"><span data-stu-id="4a2c5-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="4a2c5-123">**Create(만들기)** 단추를 클릭하여 새 Unity 프로젝트를 만들고 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-123">Click the **Create** button to create and launch your new Unity project</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="4a2c5-125">Windows에서 작업하는 경우 MAX_PATH 제한은 255자입니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="4a2c5-126">따라서 Unity 프로젝트를 드라이브의 루트에 가깝게 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="4a2c5-127">Unity에서 프로젝트가 만들어질 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-127">Wait for Unity to create the project:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="4a2c5-129">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="4a2c5-129">Switching the build platform</span></span>

<span data-ttu-id="4a2c5-130">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="4a2c5-132">Build Settings 창에서 **Universal Windows Platform(유니버설 Windows 플랫폼)** 을 선택하고, **Switch Platform(플랫폼 전환)** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="4a2c5-134">Unity에서 플랫폼 전환이 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-134">Wait for Unity to finish switching the platform:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="4a2c5-136">Unity에서 플랫폼 전환이 완료되면 빨간색 **x** 아이콘을 클릭하여 Build Settings 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="4a2c5-138">TextMeshPro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="4a2c5-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="4a2c5-139">Unity 메뉴에서 **Window**(창) > **TextMeshPro** > **Import TMP Essential Resources**(TMP 필수 리소스 가져오기)를 선택하여 Import Unity Package(Unity 패키지 가져오기) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="4a2c5-141">Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="4a2c5-143">TextMeshPro 필수 리소스는 MRTK의 UI 요소에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="4a2c5-144">프로젝트에서 MRTK의 UI 요소를 사용할 계획이 없으면 이 단계를 건너뛰어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="4a2c5-145">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="4a2c5-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="4a2c5-146">다음 Unity 사용자 지정 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-146">Download the Unity custom package:</span></span>

* [<span data-ttu-id="4a2c5-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="4a2c5-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

<span data-ttu-id="4a2c5-148">Unity 메뉴에서 **Assets(자산)**  > **Import Package(패키지 가져오기)**  > **Custom Package(사용자 지정 패키지)...** 를 차례로 선택하여 Import package(패키지 가져오기)... 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-148">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="4a2c5-150">패키지 가져오기... 창에서 다운로드한 **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage**를 선택하고 **열기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-150">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="4a2c5-152">Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="4a2c5-154">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="4a2c5-154">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="4a2c5-155">1. MRTK Project Configurator 설정 적용</span><span class="sxs-lookup"><span data-stu-id="4a2c5-155">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="4a2c5-156">Unity가 이전 섹션에서 패키지 가져오기를 완료하면 MRTK Project Configurator 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-156">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="4a2c5-157">그렇지 않으면 Unity 메뉴로 이동하고 **Mixed Reality Toolkit** > **유틸리티** > **Unity 프로젝트 구성**을 선택하여 Configurator 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-157">If it doesn't, open the Configurator window by going to the Unity menu and selecting **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="4a2c5-159">MRTK Project Configurator 창에서 **Modify Configurations**(구성 수정) 섹션을 펼치고, 모든 옵션이 선택되어 있는지 확인한 후 **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-159">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="4a2c5-161">2. 추가 프로젝트 설정 구성</span><span class="sxs-lookup"><span data-stu-id="4a2c5-161">2. Configure additional project settings</span></span>

<span data-ttu-id="4a2c5-162">Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-162">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="4a2c5-164">프로젝트 설정 창에서 **플레이어** > **XR 설정**을 선택하고 **+** 아이콘을 클릭한 후 Windows Mixed Reality를 선택하여 Windows Mixed Reality SDK를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-164">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="4a2c5-166">Unity가 Windows Mixed Reality SDK 가져오기를 마치면 MRTK Project Configurator 창이 다시 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-166">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="4a2c5-167">그렇지 않으면 Unity 메뉴를 사용하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-167">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="4a2c5-168">MRTK Project Configurator 창에서 **Audio spatializer** 드롭다운을 사용하여 **MS HRTF Spatializer**를 선택한 다음, **적용** 단추를 클릭하여 설정을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-168">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="4a2c5-170">프로젝트 설정 창에서 **플레이어** > **XR 설정**을 선택한 다음, **Depth Format**(수준 형식) 드롭다운을 사용하여 **16비트 수준**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-170">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="4a2c5-172">프로젝트 설정 창에서 **플레이어** > **게시 설정**을 선택한 다음, **패키지 이름** 필드에 적절한 이름(예: _MRTKTutorials-GettingStarted_)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-172">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> <span data-ttu-id="4a2c5-174">'패키지 이름'은 앱의 고유 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-174">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="4a2c5-175">이전에 설치된 앱을 덮어쓰지 않도록 앱을 배포하기 전에 이 식별자를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-175">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="4a2c5-176">'제품 이름'은 HoloLens 시작 메뉴에 표시되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-176">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="4a2c5-177">개발 중에 앱을 쉽게 찾을 수 있도록 이름 앞에 밑줄을 추가하면 맨 위에 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-177">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="4a2c5-178">장면 만들기 및 구성</span><span class="sxs-lookup"><span data-stu-id="4a2c5-178">Creating and configuring the scene</span></span>

<span data-ttu-id="4a2c5-179">Unity 메뉴에서 **파일** > **New Scene**(새 장면)을 선택하여 새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-179">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="4a2c5-181">Unity 메뉴에서 **Mixed Reality Toolkit** > **Add to Scene and Configure...** (장면에 추가 및 구성)를 차례로 선택하여 MRTK를 현재 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-181">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="4a2c5-183">계층 구조 창에 **MixedRealityToolkit** 개체가 아직 선택된 상태로 검사기 창에서 **MixedRealityToolkit** 구성 프로필이 **DefaultMixedRealityToolkitConfigurationProfile**로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-183">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="4a2c5-185">일반적으로는 HoloLens용으로 개발할 때 DefaultHoloLens2ConfigurationProfile을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-185">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="4a2c5-186">하지만 이 자습서에서는 DefaultMixedRealityToolkitConfigurationProfile을 사용한 후, 다음 자습서인 [MRTK 프로필 구성](mr-learning-base-03.md)에서 DefaultHoloLens2ConfigurationProfile로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-186">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="4a2c5-187">Unity 메뉴에서 **File(파일)**  > **Save As(다른 이름으로 저장)...** 를 차례로 선택하여 Save Scene(장면 저장) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-187">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="4a2c5-189">Save Scene 창에서 프로젝트의 **Scenes(장면)** 폴더로 이동하여 장면에 적합한 이름(예: _시작_)을 지정하고, **Save(저장)** 단추를 클릭하여 장면을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-189">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="4a2c5-191">HoloLens 2에 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="4a2c5-191">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="4a2c5-192">1. Unity 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="4a2c5-192">1. Build the Unity project</span></span>

<span data-ttu-id="4a2c5-193">Unity 메뉴에서 **File(파일)**  > **Build Settings(빌드 설정)...** 를 차례로 선택하여 Build Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-193">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="4a2c5-194">Build Settings 창에서 **Add Open Scenes(열려 있는 장면 추가)** 단추를 클릭하여 현재 장면을 **Scenes In Build(빌드 중인 장면)** 목록에 추가한 다음, **Build(빌드)** 단추를 클릭하여 Build Universal Windows Platform(유니버설 Windows 플랫폼 빌드) 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-194">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="4a2c5-196">Build Universal Windows Platform 창에서 빌드를 저장할 적합한 위치(예: _D:\MixedRealityLearning\Builds_)를 선택하고, 새 폴더를 만들어 적합한 이름(예: _GettingStarted_)을 지정한 다음, **Select Folder(폴더 선택)** 단추를 클릭하여 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-196">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="4a2c5-198">Unity에서 빌드 프로세스가 완료될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-198">Wait for Unity to finish the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="4a2c5-200">2. 애플리케이션 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="4a2c5-200">2. Build and deploy the application</span></span>

<span data-ttu-id="4a2c5-201">빌드 프로세스가 완료되면 Unity는 빌드를 저장한 위치를 열라는 메시지를 Windows 파일 탐색기에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-201">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="4a2c5-202">폴더 내부를 탐색하고 솔루션 파일을 두 번 클릭하여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-202">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="4a2c5-204">Visual Studio에서 새 구성 요소를 설치하라는 메시지가 표시되면 잠시 시간을 내어 **[도구 설치](install-the-tools.md)** 설명서의 필수 구성 요소가 모두 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-204">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="4a2c5-205">**마스터** 또는 **릴리스** 구성, **ARM64** 아키텍처 및 **디바이스**를 대상으로 선택하여 HoloLens용 Visual Studio를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-205">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="4a2c5-207">HoloLens(1세대)에 배포하는 경우 **x86** 아키텍처를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-207">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="4a2c5-208">HoloLens의 경우 일반적으로 ARM 아키텍처용으로 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-208">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="4a2c5-209">하지만 Unity 2019.3에는 Visual Studio에서 ARM을 빌드 아키텍처로 선택할 때 오류가 발생하는 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>알려진 문제</strong></a>가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-209">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="4a2c5-210">권장 해결 방법은 ARM64용으로 빌드하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-210">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="4a2c5-211">그렇게 할 수 없으면 **편집 > 프로젝트 설정 > 플레이어 > 기타 설정**으로 이동하여 **Graphics Jobs**(그래픽 작업)을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-211">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="4a2c5-212">디바이스가 대상 옵션으로 보이지 않으면, Visual Studio 솔루션의 시작 프로젝트를 IL2CPP 프로젝트에서 UWP 프로젝트로 변경해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-212">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="4a2c5-213">이렇게 하려면 솔루션 탐색기에서 YourProjectName(유니버설 Windows)을 마우스 오른쪽 단추로 클릭하고 **시작 프로젝트로 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-213">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="4a2c5-214">HoloLens를 컴퓨터에 연결한 다음, **디버그** > **디버그하지 않고 시작**을 선택하여 빌드하고 디바이스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-214">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="4a2c5-216">디바이스에 빌드하기 전에 디바이스가 [개발자 모드]에 있고 개발 머신과 페어링되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-216">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="4a2c5-217">이 두 단계는 모두 [이러한 지침](using-visual-studio.md)에 따라 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-217">Both of these steps can be completed by following [these instructions](using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="4a2c5-218">[HoloLens 에뮬레이터](using-the-hololens-emulator.md)에 배포하거나 테스트용 로드 [앱 패키지](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-218">You can also deploy to the [HoloLens Emulator](using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="4a2c5-219">디버그하지 않고 시작을 사용하면 Visual Studio 디버거를 연결하지 않고 디바이스에서 앱이 자동으로 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-219">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="4a2c5-220">**빌드 > 솔루션 배포**를 선택하여 앱을 자동으로 시작하지 않고 디바이스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-220">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="4a2c5-221">앱에 Diagnostics 프로파일러가 보일 수 있으며, 음성 명령 **Toggle Diagnostics**를 사용하여 표시 유형을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-221">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="4a2c5-222">앱을 변경할 때 성능에 영향을 줄 수 있는 시점을 파악하려면 개발하는 동안 프로파일러가 대부분 표시되도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-222">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="4a2c5-223">예를 들어 HoloLens 앱은 [60FPS에서 지속적으로 실행](understanding-performance-for-mixed-reality.md)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-223">For example, HoloLens apps should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="4a2c5-224">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-224">Congratulations</span></span>

<span data-ttu-id="4a2c5-225">이제 첫 번째 HoloLens 앱을 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-225">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="4a2c5-226">연습을 진행하는 동안 HoloLens가 인식한 표면을 덮는 공간 매핑 메시가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-226">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="4a2c5-227">또한 손 추적을 위해 손 및 손가락에 표시기가 나타나며, 앱 성능을 계속 확인하기 위한 프레임 속도 카운터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-227">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="4a2c5-228">이러한 기능은 MRTK에 포함된 몇 가지 기본적인 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-228">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="4a2c5-229">다음 자습서에서는 장면에 콘텐츠를 추가하여 HoloLens와 MRTK의 기능을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="4a2c5-229">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

[<span data-ttu-id="4a2c5-230">다음 자습서: 3. MRTK 프로필 구성</span><span class="sxs-lookup"><span data-stu-id="4a2c5-230">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
