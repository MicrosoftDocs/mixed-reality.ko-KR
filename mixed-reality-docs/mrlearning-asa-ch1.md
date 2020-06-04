---
title: Azure Spatial Anchors 자습서 - 1. Azure Spatial Anchors 시작
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 2a171d601d094375a56734e8d7890c9d3e17c887
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83866913"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="161e2-105">1. Azure Spatial Anchors 시작</span><span class="sxs-lookup"><span data-stu-id="161e2-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="161e2-106">개요</span><span class="sxs-lookup"><span data-stu-id="161e2-106">Overview</span></span>

<span data-ttu-id="161e2-107">HoloLens 2 자습서의 두 번째 시리즈를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="161e2-108">4부로 구성된 이 자습서 시리즈에서는 Azure Spatial Anchors의 기본 사항에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-108">In this four-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="161e2-109">첫 번째 자습서인 이 [Azure Spatial Anchors 시작](mrlearning-asa-ch1.md)에서는 Azure 세션을 시작 및 중지하고 단일 디바이스에서 Azure 앵커를 생성, 업로드 및 다운로드하는 데 필요한 여러 단계를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="161e2-110">두 번째 자습서인 [Azure Spatial Anchors 저장, 검색 및 공유](mrlearning-asa-ch2.md)에서는 앵커 정보를 HoloLens 2의 스토리지에 저장하여 여러 앱 세션에서 Azure Spatial Anchors를 저장하는 방법 및 이 앵커 정보를 다른 디바이스와 공유하여 다중 디바이스 앵커 맞춤을 수행하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="161e2-111">세 번째 자습서인 [Azure Spatial Anchor 피드백 표시](mrlearning-asa-ch3.md)에서는 Azure Spatial Anchors를 사용할 때 앵커 이벤트 및 상태에 대한 피드백을 사용자에게 제공하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

<span data-ttu-id="161e2-112">네 번째 자습서인 [Android 및 iOS용 Azure Spatial Anchors](mrlearning-asa-ch4.md)에서는 Android 및 iOS 디바이스에 프로젝트를 빌드하고 배포하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-112">In the fourth tutorial, [Azure Spatial Anchors for Android and iOS](mrlearning-asa-ch4.md), you will learn how to build and deploy your project to Android and iOS devices.</span></span>

## <a name="objectives"></a><span data-ttu-id="161e2-113">목표</span><span class="sxs-lookup"><span data-stu-id="161e2-113">Objectives</span></span>

* <span data-ttu-id="161e2-114">HoloLens 2용 Azure Spatial Anchors를 사용하여 개발하는 방법에 대한 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="161e2-114">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="161e2-115">Spatial Anchors 만들기, 업로드 및 다운로드</span><span class="sxs-lookup"><span data-stu-id="161e2-115">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="161e2-116">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="161e2-116">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="161e2-117">[시작 자습서](mrlearning-base.md) 시리즈를 아직 완료하지 않은 경우 먼저 해당 자습서를 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-117">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="161e2-118">올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="161e2-118">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="161e2-119">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="161e2-119">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="161e2-120">몇 가지 기본 C# 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="161e2-120">Some basic C# programming ability</span></span>
* <span data-ttu-id="161e2-121">[개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="161e2-121">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="161e2-122">Unity 2019.2.X가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="161e2-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="161e2-123">다음 자습서의 [Spatial Anchors 리소스 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) 섹션을 완료합니다. [빠른 시작: Azure Spatial Anchors를 사용하는 Unity HoloLens 앱 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서.</span><span class="sxs-lookup"><span data-stu-id="161e2-123">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="161e2-124">Android에 배포하려는 경우</span><span class="sxs-lookup"><span data-stu-id="161e2-124">If you intend to deploy to Android</span></span>
    * <span data-ttu-id="161e2-125">Windows 또는 macOS 컴퓨터에 USB 연결을 사용하는 <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">개발자 사용</a> 및 <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 지원 가능</a> Android 디바이스</span><span class="sxs-lookup"><span data-stu-id="161e2-125">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
    * <span data-ttu-id="161e2-126">Unity 2019.2.X가 설치되고 Android 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="161e2-126"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Android Build Support module added</span></span>
* <span data-ttu-id="161e2-127">iOS에 배포하려는 경우</span><span class="sxs-lookup"><span data-stu-id="161e2-127">If you intend to deploy to iOS</span></span>
    * <span data-ttu-id="161e2-128">최신 버전의 <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> 및 <a href="https://cocoapods.org" target="_blank">CocoaPods</a>가 설치된 macOS 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="161e2-128">A macOS computer with the the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
    * <span data-ttu-id="161e2-129">macOS 컴퓨터에 USB로 연결된 <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 호환</a> iOS 디바이스</span><span class="sxs-lookup"><span data-stu-id="161e2-129">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
    * <span data-ttu-id="161e2-130">Unity 2019.2.X가 설치되고 iOS 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="161e2-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the iOS Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="161e2-131">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-131">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="161e2-132">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-132">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="161e2-133">Unity 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="161e2-133">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity project'-->

<span data-ttu-id="161e2-134">이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-134">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="161e2-135">이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mrlearning-base-ch1.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mrlearning-base-ch1.md#build-your-application-to-your-device) 지침은 제외합니다. 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-135">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="161e2-136">[새 Unity 프로젝트 만들기](mrlearning-base-ch1.md#create-new-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정</span><span class="sxs-lookup"><span data-stu-id="161e2-136">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="161e2-137">Windows Mixed Reality용 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="161e2-137">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="161e2-138">TextMesh Pro Essential Resources 가져오기</span><span class="sxs-lookup"><span data-stu-id="161e2-138">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="161e2-139">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="161e2-139">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="161e2-140">Mixed Reality Toolkit용 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="161e2-140">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="161e2-141">[Unity 장면에 Mixed Reality Toolkit 추가](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) 및 장면에 적절한 이름(예: *AzureSpatialAnchors*) 지정</span><span class="sxs-lookup"><span data-stu-id="161e2-141">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="161e2-142">그런 다음, [Mixed Reality Toolkit 프로필을 구성하는 방법(공간 인식 표시 옵션 변경)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필을 **DefaultHoloLens2ConfigurationProfile**로 변경하고, 공간 인식 메시의 표시 옵션을 **폐색**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-142">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="161e2-143">위에 연결된 [Mixed Reality Toolkit용 Unity 프로젝트 구성](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) 지침에서 설명한 대로 Unity용 MSBuild를 사용하지 않도록 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-143">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="161e2-144">기본 제공 Unity 패키지 추가</span><span class="sxs-lookup"><span data-stu-id="161e2-144">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="161e2-145">이 섹션에서는 다음 섹션에서 가져올 Azure Spatial Anchors SDK에 필요하므로 Unity의 기본 제공 AR Foundation 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-145">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="161e2-146">Unity 메뉴에서 **Window** > **패키지 관리자**를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-146">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="161e2-148">AR Foundation 패키지가 목록에 표시되는 데 몇 초 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-148">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="161e2-149">패키지 관리자 창에서 **AR Foundation**을 선택하고, **설치** 단추를 클릭하여 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-149">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="161e2-151">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="161e2-151">Importing the tutorial assets</span></span>

<span data-ttu-id="161e2-152">다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.</span><span class="sxs-lookup"><span data-stu-id="161e2-152">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="161e2-153">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage)(버전 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="161e2-153">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="161e2-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="161e2-154">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="161e2-155">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="161e2-155">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)

> [!TIP]
> <span data-ttu-id="161e2-156">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-156">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="161e2-157">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-157">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="161e2-159">장면 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="161e2-159">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="161e2-160">이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-160">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="161e2-161">[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** 폴더로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-161">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="161e2-162">CTRL 단추를 누른 상태에서 **ButtonParent**, **DebugWindow**, **Instructions** 및 **ParentAnchor**를 클릭하여 4개의 프리팹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-162">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="161e2-164">4개의 프리팹을 선택한 상태에서 [계층 구조] 창으로 끌어서 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-164">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="161e2-166">장면의 개체에 초점을 맞추기 위해 ParentAnchor 개체를 두 번 클릭한 다음, 약간씩 다시 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-166">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="161e2-168">장면에서 큰 아이콘(예: 틀이 있는 매력적인 큰 'T' 아이콘)이 표시되는 경우 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos를 끄기 위치로 전환</a>하여 이러한 아이콘을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-168">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="161e2-169">장면을 작동하도록 단추 구성</span><span class="sxs-lookup"><span data-stu-id="161e2-169">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="161e2-170">이 섹션에서는 스크립트를 장면에 추가하여 로컬 앵커와 Azure Spatial Anchors가 애플리케이션에서 동작하는 방법에 대한 기본 사항을 보여 주는 일련의 단추 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-170">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="161e2-171">1. 누름 가능한 단추 HoloLens 2(스크립트) 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="161e2-171">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="161e2-172">[계층 구조] 창에서 **ButtonParent** 개체를 펼치고, **StartAzureSession**이라는 첫 번째 자식 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-172">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="161e2-174">[검사기] 창에서 **누름 가능한 단추 HoloLens 2(스크립트)** 구성 요소를 찾고, **+** 아이콘을 클릭하여 새 이벤트 수신기를 **Button Pressed ()** 이벤트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-174">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="161e2-176">[계층 구조] 창에서 StartAzureSession 개체를 선택한 상태에서 [계층 구조] 창의 **ParentAnchor** 개체를 클릭하여 방금 추가한 이벤트 수신기의 빈 **없음(개체)** 필드로 끌어서 ParentAnchor 개체에서 이 단추의 단추 누름 이벤트를 수신 대기하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-176">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="161e2-178">동일한 이벤트 수신기의 **함수 없음** 드롭다운을 클릭한 다음, **AnchorModuleScript** > **StartAzureSession ()** 을 차례로 선택하여 StartAzureSession () 함수를 이 단추의 단추 누름 이벤트가 실행될 때 트리거되는 작업으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-178">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="161e2-180">2. Interactable(스크립트) 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="161e2-180">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="161e2-181">[계층 구조] 창에서 StartAzureSession 개체를 선택한 채로 [검사기] 창에서 **Interactable(스크립트)** 구성 요소를 찾고, **OnClick ()** 이벤트에 대해 위의 1단계와 동일한 프로세스를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-181">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="161e2-183">3. 나머지 단추 구성</span><span class="sxs-lookup"><span data-stu-id="161e2-183">3. Configure the remaining buttons</span></span>

<span data-ttu-id="161e2-184">나머지 각 단추에 대해 위의 1단계 및 2단계에서 설명한 프로세스를 완료하여 함수를 **Button Pressed ()** 및 **OnClick ()** 이벤트 모두에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-184">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="161e2-185">**StopAzureSession** 개체에 대해 AnchorModuleScript > **StopAzureSession ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-185">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="161e2-186">**CreateAzureAnchor** 개체에 대해 AnchorModuleScript > **CreateAzureAnchor ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-186">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="161e2-187">그런 다음, **ParentAnchor**를 빈 **없음(게임 개체)** 필드로 다시 끕니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-187">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="161e2-188">**RemoveLocalAnchor** 개체에 대해 AnchorModuleScript > **RemoveLocalAnchor ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-188">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="161e2-189">그런 다음, **ParentAnchor**를 빈 **없음(게임 개체)** 필드로 다시 끕니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-189">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="161e2-190">**FindAzureAnchor** 개체에 대해 AnchorModuleScript > **FindAzureAnchor ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-190">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="161e2-191">**DeleteAzureAnchor** 개체에 대해 AnchorModuleScript > **DeleteAzureAnchor ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-191">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="161e2-192">4. Azure 리소스에 장면 연결</span><span class="sxs-lookup"><span data-stu-id="161e2-192">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="161e2-193">[계층 구조] 창에서 **ParentAnchor** 개체를 선택하고, [검사기] 창에서 **공간 앵커 관리자(스크립트)** 구성 요소까지 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-193">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="161e2-194">그런 다음, **자격 증명** 섹션에서 이 자습서에 있는 [필수 구성 요소](mrlearning-asa-ch1.md#prerequisites)의 일부로 만든 Spatial Anchors 계정 ID 및 키를 해당 **Spatial Anchors 계정 ID** 및 **Spatial Anchors 계정 키** 필드에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-194">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="161e2-196">Azure Spatial Anchors의 기본 동작 사용해 보기</span><span class="sxs-lookup"><span data-stu-id="161e2-196">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="161e2-197">이제 장면에서 Azure Spatial Anchors의 기본 사항을 보여 주도록 구성되었으므로 Azure Spatial Anchors를 직접 경험할 수 있도록 앱을 배포할 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-197">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="161e2-198">1. 필요한 추가 기능 추가</span><span class="sxs-lookup"><span data-stu-id="161e2-198">1. Add additional required capabilities</span></span>

<span data-ttu-id="161e2-199">Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 [플레이어 설정] 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-199">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="161e2-201">[플레이어 설정] 창에서 **플레이어**, **게시 설정**을 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-201">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="161e2-203">**게시 설정**에서 **기능** 섹션까지 아래로 스크롤하여 자습서의 시작 부분에서 프로젝트를 만들 때 사용하도록 설정한 **InternetClient**, **Microphone** 및 **SpatialPerception** 기능이 사용하도록 설정되어 있는지 다시 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-203">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="161e2-204">그런 다음, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** 및 **Webcam** 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-204">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="161e2-206">2. HoloLens 2에 앱 배포</span><span class="sxs-lookup"><span data-stu-id="161e2-206">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="161e2-207">Azure Spatial Anchors는 Unity에서 실행할 수 없으므로 Azure Spatial Anchors 기능을 테스트하려면 프로젝트를 디바이스에 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-207">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="161e2-208">Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법을 미리 알아보려면 [디바이스에 애플리케이션 빌드](mrlearning-base-ch1.md#build-your-application-to-your-device) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-208">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="161e2-209">3. HoloLens 2에서 앱 실행 및 앱 내 지침 수행</span><span class="sxs-lookup"><span data-stu-id="161e2-209">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="161e2-210">Azure Spatial Anchors는 인터넷을 사용하여 앵커 데이터를 저장하고 로드하므로 디바이스가 인터넷에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-210">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="161e2-211">애플리케이션이 디바이스에서 실행되는 경우 Azure Spatial Anchor 자습서 지침 패널에 표시되는 화면상의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-211">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="161e2-213">환경 고정</span><span class="sxs-lookup"><span data-stu-id="161e2-213">Anchoring an experience</span></span>

<span data-ttu-id="161e2-214">이전 섹션에서는 Azure Spatial Anchors의 기본 사항을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-214">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="161e2-215">큐브를 사용하여 연결된 앵커가 있는 부모 게임 개체를 표현하고 시각화했습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-215">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="161e2-216">이 섹션에서는 전체 환경을 ParentAnchor 개체의 자식 항목으로 배치하여 이 환경을 고정시키는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-216">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="161e2-217">1. 로켓 발사대 환경 추가</span><span class="sxs-lookup"><span data-stu-id="161e2-217">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="161e2-218">[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** 폴더로 차례로 이동하고, **RocketLauncher_Complete** 프리팹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-218">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="161e2-220">RocketLauncher_Complete 프리팹을 선택한 채로 [계층 구조] 창의 **ParentAnchor** 개체 위로 끌어서 ParentAnchor 개체의 자식 항목으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-220">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="161e2-222">2. 로켓 발사대 환경의 위치 변경</span><span class="sxs-lookup"><span data-stu-id="161e2-222">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="161e2-223">**RocketLauncher_Complete** 개체를 적절한 크기 조정 및 방향으로 위치 지정, 회전 및 크기 조정하고, **ParentAnchor** 개체가 계속 공개되도록 합니다. 예를 들어 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-223">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="161e2-224">변환 **위치** X = 0, Y = 0, Z = 3.75</span><span class="sxs-lookup"><span data-stu-id="161e2-224">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="161e2-225">변환 **회전** X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="161e2-225">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="161e2-226">변환 **크기 조정** X = 10, Y = 10, Z = 10</span><span class="sxs-lookup"><span data-stu-id="161e2-226">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="161e2-228">애플리케이션에서 사용자는 큐브를 이동하여 전체 로켓 발사대 환경의 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-228">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="161e2-229">위치 변경 개체 사용, 환경 주위의 경계 상자를 해제/설정하는 단추 사용, 위치 및 회전 gizmos 사용 등을 포함하여 위치 변경 환경에 대한 다양한 사용자 환경 흐름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-229">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="161e2-230">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-230">Congratulations</span></span>

<span data-ttu-id="161e2-231">이 자습서에서는 Azure Spatial Anchors의 기본 사항을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-231">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="161e2-232">여기서는 Azure Spatial Anchors 세션을 시작 및 중지하고 단일 디바이스에서 Azure Spatial Anchors를 생성, 업로드 및 다운로드하는 데 필요한 다양한 단계를 살펴볼 수 있는 몇 가지 단추를 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-232">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="161e2-233">다음 단원에서는 애플리케이션이 다시 시작된 후에도 검색을 위해 Azure 앵커 ID를 HoloLens 2에 저장하는 방법 및 여러 디바이스 간에 앵커 ID를 전송하여 공간 맞춤을 구현하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="161e2-233">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="161e2-234">다음 단원: 2. Azure Spatial Anchors 저장, 검색 및 공유</span><span class="sxs-lookup"><span data-stu-id="161e2-234">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
