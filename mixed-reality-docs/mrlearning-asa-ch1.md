---
title: Azure 공간 앵커 자습서-1. Azure 공간 앵커 시작
description: 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 알아보려면 이 과정을 완료합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 861c42f9449fcb3cf038258af91088fc927941e5
ms.sourcegitcommit: f4812e1312c4751a22a2de56771c475b22a4ba24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2019
ms.locfileid: "74940981"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="625ae-105">1. Azure 공간 앵커 시작</span><span class="sxs-lookup"><span data-stu-id="625ae-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="625ae-106">개요</span><span class="sxs-lookup"><span data-stu-id="625ae-106">Overview</span></span>

<span data-ttu-id="625ae-107">HoloLens 2 자습서의 두 번째 시리즈를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="625ae-108">이 세 부분으로 구성 된 자습서 시리즈에서는 Azure 공간 앵커의 기본 사항을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="625ae-109">이 첫 번째 자습서에서는 azure [공간 앵커](mrlearning-asa-ch1.md)를 시작 하 고, azure 세션을 시작 및 중지 하 고, 단일 장치에서 azure 앵커를 만들고, 업로드 하 고, 다운로드 하는 데 필요한 여러 단계를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="625ae-110">두 번째 자습서 인 [Azure 공간 앵커 저장, 검색 및 공유](mrlearning-asa-ch2.md)에서 앵커 정보를 HoloLens 2의 저장소에 저장 하 고 다중 장치 앵커 맞춤을 위해이 앵커 정보를 다른 장치에 공유 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="625ae-111">세 번째 자습서에서는 [Azure 공간 고정 피드백을 표시](mrlearning-asa-ch3.md)하는 방법에 대해 사용자에 게 Azure 공간 앵커를 사용할 때 앵커 이벤트 및 상태에 대 한 피드백을 제공 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="625ae-112">목표</span><span class="sxs-lookup"><span data-stu-id="625ae-112">Objectives</span></span>

* <span data-ttu-id="625ae-113">HoloLens 2 용 Azure 공간 앵커를 사용 하 여 개발 하는 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="625ae-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="625ae-114">공간 앵커 만들기, 업로드 및 다운로드</span><span class="sxs-lookup"><span data-stu-id="625ae-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="625ae-115">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="625ae-115">Prerequisites</span></span>

* <span data-ttu-id="625ae-116">[빠른 시작: Azure 공간 앵커를 사용 하는 Unity HoloLens 앱 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서의 [전제 조건](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) 섹션에 나열 된 요구 사항을 충족 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-116">Meet the requirements listed in the [Prerequisites](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#prerequisites) section of the  [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="625ae-117">[빠른 시작: Azure 공간 앵커를 사용 하는 Unity HoloLens 앱 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서의 [공간 앵커 리소스 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) 섹션을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-117">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>
* <span data-ttu-id="625ae-118">초보자를 위한 [자습서](mrlearning-base.md) 시리즈를 아직 완료 하지 않은 경우 해당 자습서를 먼저 완료 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-118">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="625ae-119">Unity 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="625ae-119">Creating the Unity project</span></span>

<span data-ttu-id="625ae-120">이 섹션에서는 새 Unity 프로젝트를 만들고 Windows Mixed Reality에 대해 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-120">In this section, you will create a new Unity project and configure it for Windows Mixed Reality.</span></span>

1. <span data-ttu-id="625ae-121">Unity 프로젝트를 만들고 적절 한 이름 (예: _Azure 공간 앵커 자습서_)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-121">Create a Unity project and give it a suitable name, for example, _Azure Spatial Anchors tutorial_.</span></span>

2. <span data-ttu-id="625ae-122">Windows Mixed Reality의 Unity 프로젝트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-122">Configure the Unity project for Windows Mixed Reality.</span></span>

    >[!TIP]
    ><span data-ttu-id="625ae-123">Unity 프로젝트를 만들고 Windows Mixed Reality에 맞게 구성 하는 방법에 대 한 미리 알림은 [시작 자습서](mrlearning-base.md) 시리즈의 일부인 [프로젝트 및 첫 번째 응용 프로그램 초기화](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) 자습서의 [새 Unity 프로젝트 만들기](mrlearning-base-ch1.md#create-new-unity-project) 및 [windows mixed reality 용 Unity 프로젝트 구성](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) 섹션을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-123">For a reminder on how to create a Unity project and configure it for Windows Mixed Reality, you can refer to the [Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and the [Configure the Unity project for Windows Mixed Reality](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="625ae-124">기본 제공 Unity 패키지 추가</span><span class="sxs-lookup"><span data-stu-id="625ae-124">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="625ae-125">이 섹션에서는 프로젝트에서 사용 하는 도구 키트와 Sdk에 필요한 기본 제공 Unity 자산 및 패키지를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-125">In this section, you will add inbuilt Unity assets and packages required by the toolkits and SDKs you will be using in the project.</span></span>

1. <span data-ttu-id="625ae-126">TMP 필수 리소스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-126">Import TMP Essential Resources.</span></span>

    >[!NOTE]
    ><span data-ttu-id="625ae-127">혼합 현실 도구 키트에 필요한이 패키지를 추가 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-127">We are adding this package because it is required by the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="625ae-128">Unity 메뉴에서 **Window** > **TEXTMESHPRO** > **Import TMP 필수 리소스**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-128">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-2-1.1.png)

    <span data-ttu-id="625ae-130">Unity 패키지 가져오기 팝업 창에서 먼저 **모두** 단추를 클릭 하 여 모든 자산을 선택 했는지 확인 한 다음 **가져오기** 단추를 클릭 하 여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-130">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-2-1.2.png)

2. <span data-ttu-id="625ae-132">AR를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-132">Install AR Foundation.</span></span>

    >[!NOTE]
    ><span data-ttu-id="625ae-133">Azure 공간 앵커 SDK에 필요한이 패키지를 추가 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-133">We are adding this package because it is required by the Azure Spatial Anchors SDK.</span></span>

    <span data-ttu-id="625ae-134">Unity 메뉴에서 **창** > **패키지 관리자**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-134">In the Unity menu, select **Window** > **Package Manager**.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-2-2.1.png)

    <span data-ttu-id="625ae-136">패키지 관리자 창에서 **AR Foundation** 을 선택 하 고 **설치** 단추를 클릭 하 여 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-136">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button.</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="625ae-137">AR 패키지를 목록에 표시 하기 전에 몇 초 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-137">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-2-2.2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="625ae-139">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="625ae-139">Importing the tutorial assets</span></span>

<span data-ttu-id="625ae-140">이 섹션에서는 모든 자습서 자산을 다운로드 하 고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-140">In this section, you will download and import all the tutorial assets.</span></span>

1. <span data-ttu-id="625ae-141">자산을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-141">Download the assets.</span></span>

    * <span data-ttu-id="625ae-142">[AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (버전 2.0.0)</span><span class="sxs-lookup"><span data-stu-id="625ae-142">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.0.0/AzureSpatialAnchors.unitypackage) (version 2.0.0)</span></span>
    * [<span data-ttu-id="625ae-143">MixedReality. 2.1.0. unitypackage.</span><span class="sxs-lookup"><span data-stu-id="625ae-143">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage)
    * [<span data-ttu-id="625ae-144">MRTK. HoloLens2.2.1.0.1. unitypackage를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.1.0.1.unitypackage)
    * [<span data-ttu-id="625ae-145">MRTK. HoloLens2 AzureSpatialAnchors. 2.1.0.1. unitypackage</span><span class="sxs-lookup"><span data-stu-id="625ae-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.1.0.1/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.1.0.1.unitypackage)

2. <span data-ttu-id="625ae-146">자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-146">Import the assets.</span></span>

    <span data-ttu-id="625ae-147">Unity 메뉴에서 **자산** > **가져오기 패키지** > **사용자 지정 패키지**...를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-147">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...**.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-3-2.1.png)

    <span data-ttu-id="625ae-149">패키지 가져오기 ... 팝업 창에서 **AzureSpatialAnchors** 를 선택 하 고 **열기** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-149">In the Import package... pop-up window, select the **AzureSpatialAnchors.unitypackage** and click the **Open** button.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-3-2.2.png)

    <span data-ttu-id="625ae-151">Unity 패키지 가져오기 팝업 창에서 먼저 **모두** 단추를 클릭 하 여 모든 자산을 선택 했는지 확인 한 다음 **가져오기** 단추를 클릭 하 여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-151">In the Import Unity Package pop-up window, first make sure all the assets are selected by clicking the **All** button, then import the assets by clicking the **Import** button.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-3-2.3.png)

    <span data-ttu-id="625ae-153">이러한 단계를 반복 하 여 나머지 자산 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-153">Repeat these steps to import the remaining asset packages.</span></span> <span data-ttu-id="625ae-154">완료 되 면 Unity 프로젝트의 **자산** 폴더에 이러한 하위 폴더가 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-154">Once complete, your Unity project's **Assets** folder should contain these sub-folders.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-3-2.4.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="625ae-156">장면 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="625ae-156">Creating and preparing the scene</span></span>

<span data-ttu-id="625ae-157">이 섹션에서는 혼합 현실 도구 키트와 일부 자습서 prefabs를 추가 하 여 장면을 만들고 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-157">In this section, you will create and prepare the scene by adding the Mixed Reality Toolkit and some of the tutorial prefabs.</span></span>

1. <span data-ttu-id="625ae-158">새 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-158">Create a new scene.</span></span>

    <span data-ttu-id="625ae-159">Unity 메뉴에서 **파일** > **새 장면**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-159">In the Unity menu, select **File** > **New Scene**.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-4-1.1.png)

    <span data-ttu-id="625ae-161">Unity 메뉴에서 **파일** > 다른 **이름으로 저장**...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-161">In the Unity menu, select **File** > **Save As...**.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-4-1.2.png)

    <span data-ttu-id="625ae-163">장면 저장 팝업 창에서 프로젝트의 **배경** 폴더로 이동 하 고, 장면에 적절 한 이름 (예: _ASATutorialScene_)을 지정 하 고, **저장** 단추를 클릭 하 여 장면을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-163">In the Save Scene pop-up window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _ASATutorialScene_, and save the scene by clicking the **Save** button.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-4-1.3.png)

    >[!TIP]
    ><span data-ttu-id="625ae-165">프로젝트의 자산 폴더 내에 있는 한 언제 든 지 장면을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-165">You can save the scene anywhere you like as long as it is inside the project's Assets folder.</span></span> <span data-ttu-id="625ae-166">그러나 프로젝트를 계속 구성 하려면 일반적으로 프로젝트의 배경 폴더에 저장 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-166">However, to keep your project organized, it's generally recommended to save it in the project's Scenes folder.</span></span>

2. <span data-ttu-id="625ae-167">Mixed Reality Toolkit을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-167">Add the Mixed Reality Toolkit.</span></span>

    <span data-ttu-id="625ae-168">Unity 메뉴에서 **Mixed Reality Toolkit** > **장면에 추가 및 구성**...을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-168">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-4-2.1.png)

    <span data-ttu-id="625ae-170">MixedRealityToolkitConfigurationProfile 선택 팝업 창에서 **DefaultHoloLens2ConfigurationProfile** 를 클릭 하 여 장면의 MRTK 구성 프로필로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-170">In the Select MixedRealityToolkitConfigurationProfile pop-up window, click the **DefaultHoloLens2ConfigurationProfile** to set it as the scene's MRTK configuration profile.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-4-2.2.png)

    <span data-ttu-id="625ae-172">Unity 메뉴에서 **파일** > **저장** 을 선택 하 여 장면을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-172">In the Unity menu, select **File** > **Save** to save the scene.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-4-2.3.png)

    >[!TIP]
    ><span data-ttu-id="625ae-174">바로 가기 키 CTRL + S (macOS에서 command + S)를 사용 하 여이 자습서를 진행 하면서 장면을 빠르게 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-174">You can use the keyboard shortcut CTRL+S (command + S on macOS) to quickly save your scene as you are working through this tutorial.</span></span>

3. <span data-ttu-id="625ae-175">자습서 prefabs를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-175">Add the tutorial prefabs.</span></span>

    <span data-ttu-id="625ae-176">프로젝트 패널에서 **자산** > **mrtk로 이동 합니다. AzureSpatialAnchors** > **Prefabs** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-176">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="625ae-177">CTRL 단추 (macOS에서 명령)를 누른 상태에서 **Buttonparent**, **Debugwindow**및 **parentanchor** 를 클릭 하 여 세 개의 prefabs를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-177">While holding down the CTRL button (command on macOS), click on **ButtonParent**, **DebugWindow**, and **ParentAnchor** to select the three prefabs.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-4-3.1.png)

    <span data-ttu-id="625ae-179">세 개의 prefabs를 선택한 상태에서 계층 패널로 끌어 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-179">With the three prefabs still selected, drag them into the Hierarchy panel to add them to the scene.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-4-3.2.png)

    <span data-ttu-id="625ae-181">장면의 개체에 초점을 맞추기 위해 ParentAnchor 개체를 두 번 클릭 한 다음 약간 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-181">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-4-3.3.png)

    >[!TIP]
    ><span data-ttu-id="625ae-183">장면에서 많은 아이콘이 표시 되는 경우, 예를 들어, 크게 프레임을 벗어난 아이콘이 표시 되는 경우 Gizmo 그리려면을 off 위치로 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">전환</a> 하 여 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-183">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="625ae-184">장면을 작동 하도록 단추 구성</span><span class="sxs-lookup"><span data-stu-id="625ae-184">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="625ae-185">이 섹션에서는 prefabs 및 스크립트를 장면에 추가 하 여 로컬 앵커와 Azure 공간 앵커가 응용 프로그램에서 작동 하는 방식에 대 한 기본 사항을 보여 주는 일련의 단추를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-185">In this section, you will add prefabs and scripts into the scene to create a series of buttons that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

1. <span data-ttu-id="625ae-186">Pressable Button Holo Lens 2 (스크립트) 구성 요소를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-186">Configure the Pressable Button Holo Lens 2 (script) component.</span></span>

    <span data-ttu-id="625ae-187">계층 패널에서 **Buttonparent** 개체를 확장 하 고 **StartAzureSession**라는 첫 번째 자식 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-187">In the Hierarchy panel, expand the **ButtonParent** object and select the first child object named **StartAzureSession**.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-5-1.1.png)

    <span data-ttu-id="625ae-189">검사기 패널에서 **Pressable Button Holo Lens 2 (스크립트)** 구성 요소로 스크롤하고 **+** 아이콘을 클릭 하 여 **단추 누름 ()** 이벤트에 새 이벤트 수신기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-189">In the Inspector panel, scroll down to the **Pressable Button Holo Lens 2 (script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-5-1.2.png)

    <span data-ttu-id="625ae-191">계층 패널에서 StartAzureSession 개체를 선택한 상태에서 계층 패널의 **Parentanchor** 개체를 클릭 하 고이 단추를 클릭 하 여 parentanchor 개체가 단추 누름 이벤트를 수신 하도록 합니다 .이 필드를 방금 추가한 이벤트 수신기의 빈 **없음 (개체)** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-191">With the StartAzureSession object still selected in the Hierarchy panel, click-and-drag the **ParentAnchor** object from the Hierarchy panel into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-5-1.3.png)

    <span data-ttu-id="625ae-193">동일한 이벤트 수신기의 **함수 없음** 드롭다운을 클릭 한 다음 **AnchorModuleScript** > **StartAzureSession ()** 를 선택 하 여이 단추에서 단추 누름 이벤트가 발생 했을 때 트리거되는 작업으로 StartAzureSession () 함수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-193">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-5-1.4.png)

2. <span data-ttu-id="625ae-195">Interactable (스크립트) 구성 요소를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-195">Configure the Interactable (script) component.</span></span>

    <span data-ttu-id="625ae-196">계층 패널에서 StartAzureSession 개체를 선택 하 고, 검사기 패널에서 **Interactable (스크립트)** 구성 요소로 스크롤하고, **OnClick ()** 이벤트에 대해 위의 1 단계와 동일한 프로세스를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-196">With the StartAzureSession object still selected in the Hierarchy panel, in the Inspector panel, scroll down to the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-5-2.1.png)

3. <span data-ttu-id="625ae-198">나머지 단추 구성</span><span class="sxs-lookup"><span data-stu-id="625ae-198">Configure the remaining buttons</span></span>

    <span data-ttu-id="625ae-199">나머지 각 단추에 대해 위의 1 단계와 2 단계에 설명 된 프로세스를 완료 하 여 다음과 같은 단추 누름 () 및 OnClick () 이벤트에 함수를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-199">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the Button Pressed () and OnClick () events following:</span></span>

    * <span data-ttu-id="625ae-200">**Stopazuresession** 개체에 대해 **stopazuresession ()** 함수를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-200">For the **StopAzureSession** object, assign the **StopAzureSession()** function.</span></span>
    * <span data-ttu-id="625ae-201">**Createanchor** 개체의 경우 **createazureanchor ()** 함수를 할당 하 고 **Parentanchor** 를 빈 **None (Game object)** 필드로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-201">For the **CreateAnchor** object, assign the **CreateAzureAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
    * <span data-ttu-id="625ae-202">Anchor 개체를 **검색** 하려면 **FindAzureAnchor ()** 함수를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-202">For the **Start Looking for Anchor** object, assign the **FindAzureAnchor()** function.</span></span>
    * <span data-ttu-id="625ae-203">**Delete Azure anchor** 개체의 경우 **deleteazureanchor ()** 함수를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-203">For the **Delete Azure Anchor** object, assign the **DeleteAzureAnchor()** function.</span></span>
    * <span data-ttu-id="625ae-204">**Delete Local anchor** 개체의 경우 **removelocalanchor ()** 함수를 할당 하 고 **parentanchor** 를 빈 **없음 (게임 개체)** 필드로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-204">For the **Delete Local Anchor** object, assign the **RemoveLocalAnchor()** function, then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>

4. <span data-ttu-id="625ae-205">Azure 리소스에 장면 연결</span><span class="sxs-lookup"><span data-stu-id="625ae-205">Connect the scene to the Azure resource</span></span>

    <span data-ttu-id="625ae-206">계층 패널에서 **Parentanchor** 개체를 선택 하 고 검사기 패널에서 **공간 앵커 관리자 (스크립트)** 구성 요소로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-206">In the Hierarchy panel, select the **ParentAnchor** object and in the Inspector panel, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

    <span data-ttu-id="625ae-207">그런 다음 **자격 증명** 섹션에서 공간 앵커 계정 Id 및 키를 해당 **공간** 앵커 계정 Id 및 **공간 앵커 계정 키** 필드에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-207">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields.</span></span>

    >[!NOTE]
    ><span data-ttu-id="625ae-208">이 자습서의 [필수 구성 요소](mrlearning-asa-ch1.md#prerequisites)에 따라 공간 앵커 계정 Id 및 키를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-208">You created your Spatial Anchors Account Id and Key as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites).</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-5-4.1.png)

    >[!CAUTION]
    ><span data-ttu-id="625ae-210">장면을 저장 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-210">Make sure you save your scene.</span></span>

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="625ae-211">Azure 공간 앵커의 기본 동작 시도</span><span class="sxs-lookup"><span data-stu-id="625ae-211">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="625ae-212">이제 Azure 공간 앵커의 기본 사항을 보여 주기 위해 장면을 구성 했으므로 Azure 공간 앵커 어떠한 체험을 경험할 수 있도록 앱을 배포할 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-212">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

1. <span data-ttu-id="625ae-213">필요한 추가 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-213">Add additional required capabilities.</span></span>

    <span data-ttu-id="625ae-214">Unity 메뉴에서 **편집** > **프로젝트 설정 ...** 을 선택 하 여 플레이어 설정 패널을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-214">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings panel.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-6-1.1.png)

    <span data-ttu-id="625ae-216">플레이어 설정 패널에서 **플레이어** , **게시 설정**을 차례로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-216">In the Player Settings panel, select **Player** and then **Publishing Settings**.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-6-1.2.png)

    <span data-ttu-id="625ae-218">**게시 설정**에서 **기능** 섹션까지 아래로 스크롤하고 자습서의 시작 부분에서 프로젝트를 만들 때 사용 하도록 설정 된 **SpatialPerception**이 사용 하도록 설정 되어 있는지 두 번 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-218">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that **SpatialPerception**, which you enabled when you created the project at the beginning of the tutorial, is enabled.</span></span> <span data-ttu-id="625ae-219">그런 다음 **Internetclient**, **internetclientserver**, **PrivateNetworkClientServer**, **removablestorage**, **웹캠**및 **마이크** 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-219">Then, enabled the **InternetClient**, **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, **Webcam**, and **Microphone** capabilities.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-6-1.3.png)

2. <span data-ttu-id="625ae-221">HoloLens 2에 앱을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-221">Deploy the app to your HoloLens 2.</span></span>

    >[!TIP]
    ><span data-ttu-id="625ae-222">Unity 프로젝트를 빌드하고 HoloLens 2에 배포 하는 방법에 대 한 미리 알림은 [시작 자습서](mrlearning-base.md) 시리즈의 일부인 [프로젝트 및 첫 번째 응용 프로그램 초기화](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) 자습서의 [장치에 응용 프로그램 빌드](mrlearning-base-ch1.md#build-your-application-to-your-device) 섹션을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-222">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) sections of the [Initializing your project and first application](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch1) tutorial which is part of the the [Getting started tutorials](mrlearning-base.md) series.</span></span>

3. <span data-ttu-id="625ae-223">앱을 실행 하 고 앱의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-223">Run the app and follow the in-app instructions.</span></span>

    >[!CAUTION]
    ><span data-ttu-id="625ae-224">Azure 공간 앵커는 인터넷을 사용 하 여 고정 데이터를 저장 하 고 로드 하므로 장치가 인터넷에 연결 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-224">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

    <span data-ttu-id="625ae-225">응용 프로그램이 장치에서 실행 되는 경우 **Azure 공간 고정 모듈 명령** 패널에 표시 된 화면의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-225">When the application is running on your device, follow the on-screen instructions displayed on the **Azure Spatial Anchor Module Instructions** panel.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-6-3.1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="625ae-227">환경 고정</span><span class="sxs-lookup"><span data-stu-id="625ae-227">Anchoring an experience</span></span>

<span data-ttu-id="625ae-228">이전 섹션에서는 Azure 공간 앵커의 기본 사항을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-228">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="625ae-229">큐브를 사용 하 여 연결 된 앵커를 사용 하 여 부모 게임 개체를 나타내고 시각화 했습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-229">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="625ae-230">이 섹션에서는 ParentAnchor 개체의 자식으로 배치 하 여 전체 환경을 고정 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-230">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

1. <span data-ttu-id="625ae-231">로켓 시작 관리자 환경을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-231">Add the Rocket Launcher experience.</span></span>

    <span data-ttu-id="625ae-232">프로젝트 패널에서 **자산** > **mrtk로 이동 합니다. 자습서. GetPrefabs** 가 시작 > 폴더를 선택 하 고 **로켓 Launcher_Complete** prefab를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-232">In the Project panel, navigate to **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder and select the **Rocket Launcher_Complete** prefab.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-7-1.1.png)

    <span data-ttu-id="625ae-234">로켓 Launcher_Complete prefab를 선택한 상태에서 계층 패널의 **parentanchor** 개체 위쪽으로 끌어 parentanchor 개체의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-234">With the Rocket Launcher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy panel to make it a child of the ParentAnchor object.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-7-1.2.png)

2. <span data-ttu-id="625ae-236">로켓 시작 관리자 환경의 위치를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-236">Reposition the Rocket Launcher experience.</span></span>

    <span data-ttu-id="625ae-237">**Parentanchor** (cube)가 계속 노출 되도록 모듈 **로켓 Launcher_Complete** 개체를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-237">Move module **Rocket Launcher_Complete** object so that the **ParentAnchor** (the cube) is still exposed.</span></span>

    ![mrlearning](images/mrlearning-asa-ch1-7-2.1.png)

    <span data-ttu-id="625ae-239">응용 프로그램에서 사용자는 이제 큐브를 이동 하 여 전체 로켓 시작 관리자 환경을 재배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-239">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

    >[!TIP]
    ><span data-ttu-id="625ae-240">위치 조정 개체 (예:이 자습서에서 사용 되는 큐브) 사용, 환경 주위에 있는 경계 상자를 전환 하는 단추 사용, 위치 및 회전 사용 등의 다양 한 사용자 환경 흐름이 있습니다. gizmo 그리려면.</span><span class="sxs-lookup"><span data-stu-id="625ae-240">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="625ae-241">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-241">Congratulations</span></span>

<span data-ttu-id="625ae-242">이 자습서에서는 Azure 공간 앵커의 기본 사항을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-242">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="625ae-243">이 단원에서는 Azure 세션을 시작 및 중지 하 고 단일 장치에서 azure 앵커를 만들고 업로드 하 고 다운로드 하는 데 필요한 여러 단계를 살펴볼 수 있는 몇 가지 단추를 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-243">This Lesson provided you with several buttons that let you  explore the various steps required to start and stop an Azure session and create, upload and download azure anchors on a single device.</span></span>

<span data-ttu-id="625ae-244">다음 단원에서는 응용 프로그램을 다시 시작한 후에도 검색을 위해 HoloLens 2에 Azure 앵커 Id를 저장 하는 방법과 여러 장치 간에 앵커 Id를 전송 하 여 공간 맞춤을 구현 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="625ae-244">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="625ae-245">다음 단원: 2. Azure 공간 앵커 저장, 검색 및 공유</span><span class="sxs-lookup"><span data-stu-id="625ae-245">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
