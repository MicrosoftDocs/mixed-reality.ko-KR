---
title: 다중 사용자 기능 자습서 - 1. Photon Unity 네트워킹 설정
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 2f5b55fe9c54e9e2c08177266c04a97d2302230e
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610814"
---
# <a name="1-setting-up-photon-unity-networking"></a><span data-ttu-id="a76f6-105">1. Photon Unity 네트워킹 설정</span><span class="sxs-lookup"><span data-stu-id="a76f6-105">1. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="a76f6-106">개요</span><span class="sxs-lookup"><span data-stu-id="a76f6-106">Overview</span></span>

<span data-ttu-id="a76f6-107">이 자습서에서는 PUN(Photon Unity Networking)을 사용하여 공유 환경을 만들기 위해 준비하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-107">In this tutorial, you will learn how to prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="a76f6-108">Photon은 Mixed Reality 개발자가 공유 환경을 만드는 데 사용할 수 있는 몇 가지 네트워킹 옵션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-108">Photon is one of several networking options available to Mixed Reality developers to create shared experiences.</span></span> <span data-ttu-id="a76f6-109">Photon PUN 애플리케이션을 만들고 Photon PUN 자산을 Unity 프로젝트로 가져오고 Unity 프로젝트를 Photon PUN 애플리케이션에 연결하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-109">You will learn how to create a Photon PUN application, import Photon PUN assets into your Unity project, and connect your Unity project to the Photon PUN application.</span></span>

## <a name="objectives"></a><span data-ttu-id="a76f6-110">목표</span><span class="sxs-lookup"><span data-stu-id="a76f6-110">Objectives</span></span>

* <span data-ttu-id="a76f6-111">Photon PUN 애플리케이션을 만드는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="a76f6-111">Learn how to create a Photon PUN application</span></span>
* <span data-ttu-id="a76f6-112">Photon PUN 자산을 찾아서 가져오는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="a76f6-112">Learn how to find and import the Photon PUN assets</span></span>
* <span data-ttu-id="a76f6-113">Unity 프로젝트를 Photon PUN 애플리케이션에 연결하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="a76f6-113">Learn how to connect your Unity project to the Photon PUN application</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a76f6-114">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="a76f6-114">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="a76f6-115">[시작 자습서](mrlearning-base.md) 및 [Azure Spatial Anchors 자습서](mrlearning-asa-ch1.md) 시리즈를 아직 완료하지 않은 경우 먼저 해당 자습서를 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-115">If you have not completed the [Getting started tutorials](mrlearning-base.md) and [Azure Spatial Anchors tutorials](mrlearning-asa-ch1.md) tutorial series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="a76f6-116">올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="a76f6-116">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="a76f6-117">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="a76f6-117">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="a76f6-118">몇 가지 기본 C# 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="a76f6-118">Some basic C# programming ability</span></span>
* <span data-ttu-id="a76f6-119">[개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="a76f6-119">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="a76f6-120">Unity 2019.2.X가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="a76f6-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="a76f6-121">[Spatial Anchors 리소스 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) 섹션([빠른 시작: Azure Spatial Anchors를 사용하는 Unity HoloLens 앱 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서)을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-121">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a76f6-122">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-122">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="a76f6-123">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-123">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="a76f6-124">Unity 프로젝트 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="a76f6-124">Creating and preparing the Unity project</span></span>

<span data-ttu-id="a76f6-125">이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-125">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="a76f6-126">이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mrlearning-base-ch1.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mrlearning-base-ch1.md#build-your-application-to-your-device) 지침은 제외합니다. 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-126">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="a76f6-127">[새 Unity 프로젝트 만들기](mrlearning-base-ch1.md#create-new-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정</span><span class="sxs-lookup"><span data-stu-id="a76f6-127">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="a76f6-128">Windows Mixed Reality용 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="a76f6-128">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="a76f6-129">TextMesh Pro Essential Resources 가져오기</span><span class="sxs-lookup"><span data-stu-id="a76f6-129">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="a76f6-130">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="a76f6-130">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="a76f6-131">Mixed Reality Toolkit용 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="a76f6-131">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="a76f6-132">[Unity 장면에 Mixed Reality Toolkit 추가](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) 및 장면에 적절한 이름(예: *MultiUserCapabilities*) 지정</span><span class="sxs-lookup"><span data-stu-id="a76f6-132">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="a76f6-133">그런 다음, [Mixed Reality Toolkit 프로필을 구성하는 방법(공간 인식 표시 옵션 변경)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필을 **DefaultHoloLens2ConfigurationProfile**로 변경하고, 공간 인식 메시의 표시 옵션을 **폐색**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-133">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="a76f6-134">위에 연결된 [Mixed Reality Toolkit용 Unity 프로젝트 구성](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) 지침에서 설명한 대로 Unity용 MSBuild를 사용하지 않도록 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-134">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="a76f6-135">기능 구성</span><span class="sxs-lookup"><span data-stu-id="a76f6-135">Configuring the capabilities</span></span>

<span data-ttu-id="a76f6-136">Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 [플레이어 설정] 창을 연 다음, **플레이어** >  **게시 설정** 섹션을 차례로 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-1.png)

<span data-ttu-id="a76f6-138">**게시 설정**에서 **기능** 섹션까지 아래로 스크롤하여 자습서의 시작 부분에서 프로젝트를 만들 때 사용하도록 설정한 **InternetClient**, **Microphone** 및 **SpatialPerception** 기능이 사용하도록 설정되어 있는지 다시 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="a76f6-139">그런 다음, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage** 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-139">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **RemovableStorage** capabilities:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section2-step1-2.png)

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="a76f6-141">기본 제공 Unity 패키지 추가</span><span class="sxs-lookup"><span data-stu-id="a76f6-141">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="a76f6-142">이 섹션에서는 다음 섹션에서 가져올 Azure Spatial Anchors SDK에 필요하므로 Unity의 기본 제공 AR Foundation 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-142">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="a76f6-143">Unity 메뉴에서 **Window** > **패키지 관리자**를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-143">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a76f6-145">AR Foundation 패키지가 목록에 표시되는 데 몇 초 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-145">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="a76f6-146">패키지 관리자 창에서 **AR Foundation**을 선택하고, **설치** 단추를 클릭하여 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-146">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="a76f6-148">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="a76f6-148">Importing the tutorial assets</span></span>

<span data-ttu-id="a76f6-149">다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.</span><span class="sxs-lookup"><span data-stu-id="a76f6-149">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="a76f6-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage)(버전 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="a76f6-150">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="a76f6-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a76f6-151">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="a76f6-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a76f6-152">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.1.unitypackage)
* [<span data-ttu-id="a76f6-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a76f6-153">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="a76f6-154">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-154">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="a76f6-155">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-155">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a76f6-157">MultiUserCapabilities 자습서 자산 패키지를 가져오면 유형 또는 네임스페이스가 누락되었음을 나타내는 [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) 오류가 Console 창에 보입니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-157">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="a76f6-158">이것은 예상한 오류이며, 다음 섹션에서 Photon 자산을 가져오면 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-158">This is to be expected and will be resolved in the next section when you import the Photon assets.</span></span>

## <a name="importing-the-photon-assets"></a><span data-ttu-id="a76f6-159">Photon 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="a76f6-159">Importing the Photon assets</span></span>

<span data-ttu-id="a76f6-160">이 섹션에서는 Unity의 Asset Store에서 PUN(Photon Unity Network) 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-160">In this section, you will import the Photon Unity Network (PUN) assets from Unity's Asset Store.</span></span>

<span data-ttu-id="a76f6-161">Unity 메뉴에서 **Window** > **Asset Store**를 선택하여 Asset Store 창을 열고 Exit Games에서 **PUN 2 - FREE**를 검색하여 선택한 다음, **Download** 단추를 클릭하여 자산 패키지를 Unity 계정에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-161">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, and then click the **Download** button to download the asset package to your Unity account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-1.png)

<span data-ttu-id="a76f6-163">다운로드가 완료되면 **Import** 단추를 클릭하여 Import Unity Package 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-163">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-2.png)

<span data-ttu-id="a76f6-165">Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-165">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-3.png)

<span data-ttu-id="a76f6-167">Unity에서 Import(가져오기) 프로세스가 완료되면 Pun Wizard 창이 PUN Setup 메뉴가 로드된 상태로 나타납니다. 지금은 이 창을 무시하거나 닫으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-167">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section5-step1-4.png)

## <a name="setting-up-photon"></a><span data-ttu-id="a76f6-169">Photon 설정</span><span class="sxs-lookup"><span data-stu-id="a76f6-169">Setting up Photon</span></span>

<span data-ttu-id="a76f6-170">이 섹션에서는 Photon 계정이 없으면 만들고 새 PUN 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-170">In this section, you will create a Photon account, if you don't already have one, and create a new PUN application.</span></span>

<span data-ttu-id="a76f6-171">Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">대시보드</a>로 이동하여 로그인하고(사용할 계정이 있는 경우) 그렇지 않으면 **Create One** 링크를 클릭하여 지침에 따라 새 계정을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-171">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-1.png)

<span data-ttu-id="a76f6-173">로그인되면 **Create a New App** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-173">Once signed in, click the **Create a New App** button:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-2.png)

<span data-ttu-id="a76f6-175">Create a New Application(새 애플리케이션 만들기) 페이지에서 다음 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-175">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="a76f6-176">Photon Type에는 Photon PUN을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-176">For Photon Type, select Photon PUN</span></span>
* <span data-ttu-id="a76f6-177">이름에는 적절한 이름(예: _MRTK Tutorials_)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-177">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="a76f6-178">설명에는 적절한 설명(선택 사항)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-178">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="a76f6-179">URL 필드는 비워둡니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-179">For Url, leave the field empty</span></span>

<span data-ttu-id="a76f6-180">**Create** 단추를 클릭하여 새 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-180">Then click the **Create** button to create the new application:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-3.png)

<span data-ttu-id="a76f6-182">Photon에서 만들기 프로세스가 완료되면 새 PUN 애플리케이션이 대시보드에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-182">Once Photon has finished the creation process, the new PUN application will appear on your dashboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="a76f6-184">Unity 프로젝트를 PUN 애플리케이션에 연결</span><span class="sxs-lookup"><span data-stu-id="a76f6-184">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="a76f6-185">이 섹션에서는 Unity 프로젝트를 이전 섹션에서 만든 PUN 애플리케이션에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-185">In this section, you will connect your Unity project to the PUN application you created in the previous section.</span></span>

<span data-ttu-id="a76f6-186">Photon 대시보드에서 **App ID** 필드를 클릭하고 앱 ID 필드를 표시하여 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-186">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-1.png)

<span data-ttu-id="a76f6-188">Unity 메뉴에서 **Window** > **Photon Unity Networking** > **PUN Wizard**를 선택하여 Pun Wizard 창을 열고 **Setup Project** 창을 클릭하여 PUN Setup 메뉴를 열어서 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-188">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="a76f6-189">**AppId or Email** 필드에 이전 단계에서 복사한 PUN App ID를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-189">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="a76f6-190">그런 다음, **Setup Project** 단추를 클릭하여 App ID를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-190">Then click the **Setup Project** button to apply the app ID:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-2.png)

<span data-ttu-id="a76f6-192">Unity에서 PUN 설정 프로세스가 완료되면 PUN Setup 메뉴에 **Done!** 이라는 메시지가 표시되고</span><span class="sxs-lookup"><span data-stu-id="a76f6-192">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="a76f6-193">Project 창에 **PhotonServerSettings** 자산이 자동으로 선택되고 해당 속성이 Inspector 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-193">and automatically select the **PhotonServerSettings** asset in the Project window so its properties are displayed in the Inspector window:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial1-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="a76f6-195">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-195">Congratulations</span></span>

<span data-ttu-id="a76f6-196">Photon PUN 애플리케이션을 만들어서 Unity 프로젝트에 연결하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-196">You have successfully created a Photon PUN application and connected it to your Unity project.</span></span> <span data-ttu-id="a76f6-197">다음 단계에서는 여러 사용자가 서로 볼 수 있도록 다른 사용자와 연결을 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a76f6-197">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

<span data-ttu-id="a76f6-198">[다음 자습서: 2. 여러 사용자 연결](mrlearning-sharing(photon)-ch2.md)</span><span class="sxs-lookup"><span data-stu-id="a76f6-198">[Next tutorial: 2. Connecting multiple users](mrlearning-sharing(photon)-ch2.md)</span></span>
