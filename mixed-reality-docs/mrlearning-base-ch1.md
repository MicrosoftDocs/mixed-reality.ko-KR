---
title: 시작 자습서 - 2. 프로젝트 및 첫 번째 애플리케이션 초기화
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: d0c166f760884efab9719ecba1ff83285872e2ef
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334409"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="aaf74-105">2. 프로젝트 및 첫 번째 애플리케이션 초기화</span><span class="sxs-lookup"><span data-stu-id="aaf74-105">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="aaf74-106">개요</span><span class="sxs-lookup"><span data-stu-id="aaf74-106">Overview</span></span>

<span data-ttu-id="aaf74-107">이 첫 번째 단원에서는 <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">MRTK(Mixed Reality Toolkit)</a>에서 제공해야 하는 기능 중 일부에 대해 알아보고, HoloLens 2용 첫 번째 애플리케이션을 시작하고, 이를 디바이스에 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-107">In this first lesson, you'll learn about some of the capabilities the <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> has to offer, start your first application for the HoloLens 2, and deploy it to the device.</span></span>

## <a name="objectives"></a><span data-ttu-id="aaf74-108">목표</span><span class="sxs-lookup"><span data-stu-id="aaf74-108">Objectives</span></span>

* <span data-ttu-id="aaf74-109">HoloLens 개발을 위해 Unity를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-109">Configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="aaf74-110">자산을 가져오고 장면을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-110">Import assets and set up the scene.</span></span>
* <span data-ttu-id="aaf74-111">공간 매핑 메시, 손 메시 및 프레임 속도 카운터를 시각화합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-111">Visualization of the spatial mapping mesh, hand meshes, and the framerate counter.</span></span>

## <a name="create-new-unity-project"></a><span data-ttu-id="aaf74-112">새 Unity 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="aaf74-112">Create new Unity project</span></span>

1. <span data-ttu-id="aaf74-113">Unity를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-113">Start Unity.</span></span>

2. <span data-ttu-id="aaf74-114">**New**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-114">Select **New**.</span></span>

    ![단원 1 섹션 1 단계 2](images/mrlearning-base-ch1-1-step2.JPG)

3. <span data-ttu-id="aaf74-116">프로젝트 이름(예: "MixedRealityBase")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-116">Enter a project name (e.g. "MixedRealityBase").</span></span>

    ![단원 1 섹션 1 단계 3](images/mrlearning-base-ch1-1-step3.JPG)

4. <span data-ttu-id="aaf74-118">프로젝트를 저장할 위치를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-118">Enter a location to save your project.</span></span>

    ![단원 1 섹션 1 단계 4](images/mrlearning-base-ch1-1-step4.JPG)

5. <span data-ttu-id="aaf74-120">프로젝트가 **3D**로 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-120">Make sure the project is set to **3D**.</span></span>

    ![단원 1 섹션 1 단계 5](images/mrlearning-base-ch1-1-step5.JPG)

6. <span data-ttu-id="aaf74-122">**Create Project**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-122">Click **Create Project**.</span></span>

    ![단원 1 섹션 1 단계 6](images/mrlearning-base-ch1-1-step6.JPG)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="aaf74-124">Windows Mixed Reality를 위한 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="aaf74-124">Configure the Unity project for Windows Mixed Reality</span></span>

1. <span data-ttu-id="aaf74-125">**파일** > **빌드 설정**으로 차례로 이동하여 *빌드 설정* 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-125">Open the *Build Settings* window by going to **File** > **Build Settings**.</span></span>

    ![단원 1 섹션 2 단계 1](images/mrlearning-base-ch1-2-step1.JPG)

2. <span data-ttu-id="aaf74-127">*유니버설 Windows 플랫폼*을 선택하고, **플랫폼 전환** 단추를 클릭하여 플랫폼을 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-127">Select the *Universal Windows Platform* and click the **Switch Platform** button to switch platforms.</span></span> <span data-ttu-id="aaf74-128">HoloLens 2에서 실행되는 애플리케이션은 UWP(유니버설 Windows 플랫폼)와 호환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-128">Applications running on HoloLens 2 are required to be Universal Windows Platform (UWP) compatible.</span></span>

    ![단원 1 섹션 2 단계 2](images/mrlearning-base-ch1-2-step2.JPG)

3. <span data-ttu-id="aaf74-130">[빌드] 창에서 **플레이어 설정** 단추를 클릭하여 가상 현실을 사용하도록 설정하고, 아래 이미지와 같이 검사기 패널의 [XR 설정] 아래에서 *가상 현실 지원* 확인란을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-130">Enable virtual reality by clicking the **Player Settings** button in the Build Window, and enable the *Virtual Reality Supported* checkbox under XR Settings from the inspector panel, as shown in the image below.</span></span> <span data-ttu-id="aaf74-131">검사기 패널을 표시하기 위해 *빌드 설정* 창을 다른 위치로 끌어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-131">Note that you might need to drag the *Build Settings* window out of the way in order to see the inspector panel.</span></span> <span data-ttu-id="aaf74-132">또한 *가상 현실 지원* 확인란은 입체 시각(stereoscopic vision, 각 눈에 대해 서로 다른 이미지 렌더링)을 사용하도록 설정한다는 것을 나타내므로 Mixed Reality(혼합 현실) 및 Augmented Reality(확대된 현실) 헤드셋에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-132">The *Virtual Reality Supported* checkbox also applies to Mixed Reality and Augmented Reality headsets because it refers to the enabling of stereoscopic vision (rendering different images for each eye.)</span></span>

    ![단원 1 섹션 2 단계 3](images/mrlearning-base-ch1-2-step3.JPG)

4. <span data-ttu-id="aaf74-134">[XR 설정] 아래에서 *스테레오 렌더링 모드*를 *단일 패스 인스턴스화됨*으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-134">Also under XR Settings, change the *Stereo Rendering Mode* to *Single Pass Instanced*.</span></span> <span data-ttu-id="aaf74-135">이 [렌더링 파이프라인 스타일](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html)은 일반적으로 HoloLens 2에 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-135">This [rendering pipeline style](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) is generally most performant for HoloLens 2.</span></span> <span data-ttu-id="aaf74-136">Unity 환경의 다른 성능 구성에 관심이 있는 경우 [이 지침](recommended-settings-for-unity.md)을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="aaf74-136">If interested in other performant configurations for your Unity environment, follow [these instructions](recommended-settings-for-unity.md).</span></span>

    ![단원 1 섹션 2 단계 4](images/mrlearning-base-ch1-2-step4.jpg)

5. <span data-ttu-id="aaf74-138">동일한 검사기 패널에 있는 *게시 설정* 아래의 [기능] 섹션에서 *Spatial Perception* 확인란을 사용하도록 설정되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-138">From the same inspector panel, ensure that the *Spatial Perception* checkbox in the capabilities section is enabled under *Publishing Settings*.</span></span> <span data-ttu-id="aaf74-139">Spatial Perception(공간 인식)을 사용하면 HoloLens 2와 같은 혼합 현실 디바이스에서 공간 매핑 메시를 시각화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-139">Spatial Perception allows us to visualize the spatial mapping mesh on a mixed reality device, such as HoloLens 2.</span></span> <span data-ttu-id="aaf74-140">[게시 설정]은 검사기 패널에서 [XR 설정] 위와 [기타 설정] 아래에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-140">Publishing Settings are found in the inspector panel, above XR Settings and under Other Settings.</span></span>

    ![단원 1 섹션 2 단계 5](images/mrlearning-base-ch1-2-step5.JPG)

    >[!NOTE]
    ><span data-ttu-id="aaf74-142">이 섹션에서 사용되지는 않지만, 사용하도록 설정할 수 있는 몇 가지 다른 일반적인 기능으로 *Microphone*(음성 명령용) 및 *InternetClient*(네트워크 연결이 필요한 서비스 연결용)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-142">While not used in this section, some other common capabilities you might want to enable include the *Microphone* for voice commands, and *InternetClient* for connecting to services requiring a network connection.</span></span>

## <a name="import-the-mixed-reality-toolkit"></a><span data-ttu-id="aaf74-143">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="aaf74-143">Import the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="aaf74-144">[Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [기초 패키지 버전 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)을 다운로드하여 PC의 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-144">Download the [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) Unity [foundation package version 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) and save it to a folder on your PC.</span></span>

2. <span data-ttu-id="aaf74-145">이전 단계에서 다운로드한 *Mixed Reality Toolkit* 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-145">Import the *Mixed Reality Toolkit* package that you downloaded in the previous step.</span></span> <span data-ttu-id="aaf74-146">먼저 **자산** > **가져오기** > **사용자 지정 패키지**를 클릭하고, *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage*를 선택하고, 이를 열어 가져오기 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-146">Start by clicking on **Assets** > **Import** > **Custom Package**, select *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* and open it to begin the importing process.</span></span> <span data-ttu-id="aaf74-147">가져오기 프로세스가 완료될 때까지 몇 분 정도 기다리세요.</span><span class="sxs-lookup"><span data-stu-id="aaf74-147">Allow a few minutes for the importing process to complete.</span></span>

    ![단원 1 섹션 3 단계 2a](images/mrlearning-base-ch1-3-step2a.JPG)

    ![단원 1 섹션 3 단계 2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. <span data-ttu-id="aaf74-150">다음 팝업 창에서 **가져오기**를 클릭하여 선택한 패키지를 Unity 프로젝트로 가져오기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-150">In the next pop-up window, click **Import** to begin importing the selected package into the Unity project.</span></span> <span data-ttu-id="aaf74-151">이미지와 같이 모든 항목이 선택되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-151">Ensure all items are checked as shown in the image.</span></span>

    ![단원 1 섹션 3 단계 3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > <span data-ttu-id="aaf74-153">Mixed Reality Toolkit 기본 설정을 적용하도록 요청하는 팝업 대화 상자가 표시되면 **적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-153">If you see a pop-up dialog box asking to apply the Mixed Reality Toolkit default settings, click **Apply**.</span></span> <span data-ttu-id="aaf74-154">MRTK는 자동화된 설정을 위해 가져올 때 누락된 추천 설정이 있는지 프로젝트를 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-154">MRTK analyzes your project for any missing recommended settings when imported for automated setup.</span></span> <span data-ttu-id="aaf74-155">설정에 따라 팝업이 아래 이미지와 다르게 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-155">Depending on your settings, the pop-up might look different than the image below.</span></span>

    ![단원 1 섹션 3 단계 4 참고 1](images/mrlearning-base-ch1-3-step4-note1.JPG)

## <a name="configure-the-mixed-reality-toolkit"></a><span data-ttu-id="aaf74-157">Mixed Reality Toolkit 구성</span><span class="sxs-lookup"><span data-stu-id="aaf74-157">Configure the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="aaf74-158">메뉴 모음에서**Mixed Reality Toolkit** > **장면에 추가 및 구성..** 을 차례로 선택하여 *Mixed Reality Toolkit*를</span><span class="sxs-lookup"><span data-stu-id="aaf74-158">Add the *Mixed Reality Toolkit* to your current scene by selecting **Mixed Reality Toolkit** > **Add to Scene and Configure..**</span></span> <span data-ttu-id="aaf74-159">현재 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-159">from the menu bar.</span></span> <span data-ttu-id="aaf74-160">Mixed Reality Toolkit을 가져온 후에 이 메뉴 항목이 보이지 않으면 Unity를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-160">If you don't see this menu item after importing the mixed reality toolkit, restart Unity.</span></span>

    ![단원 1 섹션 4 단계 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > <span data-ttu-id="aaf74-162">[Mixed Reality Toolkit용 프로필](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html)을 선택하기 위한 팝업 대화 상자가 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-162">You may see a pop-up dialog box for selecting a [profile for the Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html).</span></span> <span data-ttu-id="aaf74-163">*DefaultHoloLens2ConfigurationProfile*이라는 프로필을 두 번 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-163">Choose the profile named *DefaultHoloLens2ConfigurationProfile* by double-clicking it.</span></span>

2. <span data-ttu-id="aaf74-164">장면에는 몇 가지 새로운 항목과 수정이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-164">Your scene will have several new items and modifications.</span></span> <span data-ttu-id="aaf74-165">**파일** > **다른 이름으로 저장...** 을 클릭하여 장면을 다른 이름으로 저장하고, 해당 장면에 *BaseScene*과 같은 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-165">Save your scene under a different name by clicking **File** > **Save As...**, and give your scene a name, such as *BaseScene*.</span></span> <span data-ttu-id="aaf74-166">프로젝트의 *Assets* 폴더에 있는 *Scenes* 폴더에 저장하여 장면을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-166">Keep your scene organized by saving it to the *Scenes* folder in your project’s *Assets* folder.</span></span>

    ![단원 1 섹션 4 단계 2a](images/mrlearning-base-ch1-4-step2a.JPG)

    ![단원 1 섹션 4 단계 2b](images/mrlearning-base-ch1-4-step2b.JPG)

## <a name="build-your-application-to-your-device"></a><span data-ttu-id="aaf74-169">디바이스로 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="aaf74-169">Build your application to your device</span></span>

1. <span data-ttu-id="aaf74-170">이전 섹션에서 *빌드 설정* 창을 닫은 경우 **파일** > **빌드 설정**으로 차례로 이동하여 *빌드 설정* 창을 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-170">If you closed the *Build Settings* window from the previous sections, open the *Build Settings* window again by going to **File** > **Build Settings**.</span></span>

    ![단원 1 섹션 5 단계 1](images/mrlearning-base-ch1-5-step1.JPG)

2. <span data-ttu-id="aaf74-172">장면이 Unity에서 열려 있는 상태에서 **열린 장면 추가** 단추를 클릭하여 방금 만든 장면이 *빌드 중 장면* 목록에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-172">Ensure the scene you just created is in the *Scenes in Build* list by clicking on the **Add Open Scenes** button while your scene is open in Unity.</span></span>

3. <span data-ttu-id="aaf74-173">**빌드** 단추를 눌러 빌드 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-173">Press the **Build** button to begin the build process.</span></span>

    ![단원 1 섹션 5 단계 3](images/mrlearning-base-ch1-5-step3.JPG)

4. <span data-ttu-id="aaf74-175">애플리케이션의 새 폴더를 만들고 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-175">Create and name a new folder for your application.</span></span> <span data-ttu-id="aaf74-176">아래 이미지에서는 애플리케이션을 포함할 App이라는 폴더가 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-176">In the image below, a folder with the name App was created to contain the application.</span></span> <span data-ttu-id="aaf74-177">**폴더 선택**을 클릭하여 빌드를 새로 만든 폴더에 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-177">Click **Select Folder** to begin building to the newly created folder.</span></span> <span data-ttu-id="aaf74-178">빌드가 완료되면에 Unity에서 *빌드 설정* 창을 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-178">After the build has completed, you can close the *Build Settings* window in Unity.</span></span>

    ![단원 1 섹션 5 단계 4](images/mrlearning-base-ch1-5-step4.JPG)

    >[!IMPORTANT]
    ><span data-ttu-id="aaf74-180">빌드가 실패하는 경우 다시 빌드하거나 Unity를 다시 시작한 후 다시 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-180">If the build fails, try building again or restarting Unity and building again.</span></span> <span data-ttu-id="aaf74-181">오류: CS0246 = "XX" 유형 또는 네임스페이스 이름을 찾을 수 없습니다. using 지시문 또는 어셈블리 참조가 누락되었습니까?와 같은 오류가 표시되는 경우</span><span class="sxs-lookup"><span data-stu-id="aaf74-181">If you see an error, such as "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?).</span></span> <span data-ttu-id="aaf74-182">[Windows 10 SDK(10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)를 설치해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-182">If so, you might need to install [Windows 10 SDK (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk)</span></span>

5. <span data-ttu-id="aaf74-183">빌드가 완료된 후 새로 빌드한 애플리케이션 파일을 포함하는 새로 만든 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-183">After the build is completed, open the newly created folder containing your newly built application files.</span></span> <span data-ttu-id="aaf74-184">*MixedRealityBase.sln* 솔루션 또는 해당 이름(프로젝트에 대한 대체 이름을 사용한 경우)을 두 번 클릭하여 Visual Studio에서 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-184">Double-click on the *MixedRealityBase.sln* solution, or the corresponding name, if you used an alternative name for your project, to open the solution file in Visual Studio.</span></span>

    >[!NOTE]
    ><span data-ttu-id="aaf74-185">새로 만든 폴더(즉, 이전 단계의 명명 규칙을 따르는 경우 *App* 폴더)를 열어야 합니다. 이 폴더 외부에 비슷한 이름의 .sln 파일이 있으므로 빌드 폴더 내의 .sln 파일과 혼동하지 않도록 주의합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-185">Be sure to open the newly created folder (i.e. the *App* folder, if following the naming conventions from the previous steps), as there will be a similarly named .sln file outside of that folder, that is not to be confused with the .sln file inside the build folder.</span></span> <span data-ttu-id="aaf74-186">폴더 구조는 아래 이미지와 비슷하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-186">The folder structure should look similar to the image below.</span></span>
    >
    ><span data-ttu-id="aaf74-187">Visual Studio에서 새로운 구성 요소를 설치하라는 메시지를 표시하면 ["도구 설치" 페이지](install-the-tools.md)에 지정된 모든 필수 구성 요소가 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-187">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in [the "Install the Tools" page](install-the-tools.md)</span></span>

    ![단원 1 섹션 5 단계 5](images/mrlearning-base-ch1-5-step5.JPG)

6. <span data-ttu-id="aaf74-189">HoloLens 2를 PC에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-189">Connect your HoloLens 2 into your PC.</span></span> <span data-ttu-id="aaf74-190">이러한 지침에서는 HoloLens 2 디바이스에 배포한다고 가정하지만, [HoloLens 2 에뮬레이터](using-the-hololens-emulator.md)에 배포하거나 [테스트용으로 로드할 앱 패키지](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)를 만들도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-190">While these instructions assume you will be deploying to a HoloLens 2 device, you might also choose to deploy to the [HoloLens 2 emulator](using-the-hololens-emulator.md) or choose to create an [app package for sideloading](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>)</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="aaf74-191">디바이스에 빌드하기 전에 디바이스가 *개발자 모드*에 있고 개발 머신과 페어링되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-191">Before building to your device, the device must be in *Developer Mode* and paired with your development machine.</span></span> <span data-ttu-id="aaf74-192">이 두 단계는 모두 [이 지침](using-visual-studio.md)에 따라 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-192">Both of these steps can be completed by following [these instructions](using-visual-studio.md)</span></span>

7. <span data-ttu-id="aaf74-193">*릴리스* 또는 *마스터* 구성, *ARM* 아키텍처 및 대상으로 *디바이스*를 선택하여 HoloLens 2에 빌드하도록 Visual Studio를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-193">Configure Visual Studio for building to your HoloLens 2 by selecting the *Release* or *Master* configuration, the *ARM* architecture, and *Device* as target.</span></span>

    ![단원 1 섹션 5 단계 8](images/mrlearning-base-ch1-5-step7.JPG)

8. <span data-ttu-id="aaf74-195">마지막 단계는 **디버그** > **디버깅하지 않고 시작**을 차례로 선택하여 빌드하고 디바이스에 배포하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-195">The final step is to build and deploy to your device by selecting **Debug** > **Start without debugging**.</span></span> <span data-ttu-id="aaf74-196">*디버깅하지 않고 시작*을 선택하면 빌드 성공 시 애플리케이션이 디바이스에서 즉시 시작되지만, 디버거가 연결되지 않고 정보가 Visual Studio에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-196">Selecting *Start without Debugging* causes the application to immediately start on your device upon a successful build, but without the debugger attached and information appearing in Visual Studio.</span></span> <span data-ttu-id="aaf74-197">따라서 HoloLens 2에서 애플리케이션이 실행되는 동안 USB 케이블 연결을 끊어도 애플리케이션이 중지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-197">This also means that you can disconnect your USB cable while your application is running on your HoloLens 2 without stopping the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="aaf74-198">애플리케이션을 자동으로 시작하지 않고 **빌드** > **솔루션 배포**를 차례로 선택하여 디바이스에 배포할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-198">You might also select **Build** > **Deploy Solution** to deploy to your device without having the application automatically start.</span></span>

    ![단원 1 섹션 5 단계 9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a><span data-ttu-id="aaf74-200">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-200">Congratulations</span></span>

<span data-ttu-id="aaf74-201">이제 첫 번째 HoloLens 2 애플리케이션을 배포했습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-201">You have now deployed your first HoloLens 2 application.</span></span> <span data-ttu-id="aaf74-202">연습을 진행하면서 HoloLens 2에서 인식한 모든 표면이 포함된 공간 매핑 메시가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-202">As you walk around, you should see a spatial mapping mesh covering all the surfaces that have been perceived by the HoloLens 2.</span></span> <span data-ttu-id="aaf74-203">또한 손을 추적하기 위한 손 및 손가락의 표시기와 애플리케이션 성능을 감시하기 위한 프레임 속도 카운터가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-203">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on application performance.</span></span> <span data-ttu-id="aaf74-204">이러한 기능은 Mixed Reality Toolkit과 함께 기본적으로 포함되어 있는 기본적인 기능 중 일부에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-204">These are just a few of the foundational pieces, included out of the box, with the Mixed Reality Toolkit.</span></span> <span data-ttu-id="aaf74-205">다음 단원에서는 더 많은 콘텐츠와 대화형 작업을 장면에 추가하여 HoloLens 2 및 Mixed Reality Toolkit의 기능을 전체적으로 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-205">In the lessons to come, you will start adding more content and interactivity to your scene so that you can fully explore the capabilities of HoloLens 2 and the Mixed Reality Toolkit.</span></span>

> [!NOTE]
> <span data-ttu-id="aaf74-206">앱에서 시각적 프로파일러를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-206">In the app, you may notice the visual profiler.</span></span> <span data-ttu-id="aaf74-207">[5단원](mrlearning-base-ch5.md)의 음성 명령을 사용하여 프레임 속도 카운터를 설정/해제하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-207">You will cover how to toggle the frame rate counter using a voice command in [Lesson 5](mrlearning-base-ch5.md).</span></span> <span data-ttu-id="aaf74-208">일반적으로 코드 변경이 성능에 영향을 줄 수 있는 경우를 이해하기 위해 개발 중에 항상 시각적 프로파일러를 표시하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-208">It is generally recommended to keep the visual profiler visible at all times during development to understand when code changes may have impacted perf.</span></span> <span data-ttu-id="aaf74-209">HoloLens 2 애플리케이션은 [60FPS에서 지속적으로 실행](understanding-performance-for-mixed-reality.md)되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aaf74-209">HoloLens 2 application should [continuously run at 60 FPS](understanding-performance-for-mixed-reality.md).</span></span>

[<span data-ttu-id="aaf74-210">다음 단원: 3. 사용자 인터페이스 만들기 및 Mixed Reality Toolkit 도구 키트 구성</span><span class="sxs-lookup"><span data-stu-id="aaf74-210">Next Lesson: 3. Creating user interface and configure Mixed Reality Toolkit</span></span>](mrlearning-base-ch2.md)
