---
title: Azure 공간 앵커 자습서-1. Azure 공간 앵커 시작
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 0163b61bfbf8bd583532092581d94f63e1c2a624
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77554682"
---
# <a name="1-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="dc54c-105">1. Azure 공간 앵커 시작</span><span class="sxs-lookup"><span data-stu-id="dc54c-105">1. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="dc54c-106">개요</span><span class="sxs-lookup"><span data-stu-id="dc54c-106">Overview</span></span>

<span data-ttu-id="dc54c-107">HoloLens 2 자습서의 두 번째 시리즈를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-107">Welcome to the second series of the HoloLens 2 tutorials.</span></span> <span data-ttu-id="dc54c-108">이 세 부분으로 구성 된 자습서 시리즈에서는 Azure 공간 앵커의 기본 사항을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-108">In this three-part tutorial series, you will learn the fundamentals of Azure Spatial Anchors.</span></span>

<span data-ttu-id="dc54c-109">이 첫 번째 자습서에서는 azure [공간 앵커](mrlearning-asa-ch1.md)를 시작 하 고, azure 세션을 시작 및 중지 하 고, 단일 장치에서 azure 앵커를 만들고, 업로드 하 고, 다운로드 하는 데 필요한 여러 단계를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-109">In this first tutorial, [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md), you will explore the various steps required to start and stop an Azure session and create, upload, and download Azure anchors on a single device.</span></span>

<span data-ttu-id="dc54c-110">두 번째 자습서 인 [Azure 공간 앵커 저장, 검색 및 공유](mrlearning-asa-ch2.md)에서 앵커 정보를 HoloLens 2의 저장소에 저장 하 고 다중 장치 앵커 맞춤을 위해이 앵커 정보를 다른 장치에 공유 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-110">In the second tutorial, [Saving, retrieving, and sharing Azure Spatial Anchors](mrlearning-asa-ch2.md), you will learn how to save Azure Spatial Anchors across multiple app sessions by saving anchor information to the HoloLens 2's storage and how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

<span data-ttu-id="dc54c-111">세 번째 자습서에서는 [Azure 공간 고정 피드백을 표시](mrlearning-asa-ch3.md)하는 방법에 대해 사용자에 게 Azure 공간 앵커를 사용할 때 앵커 이벤트 및 상태에 대 한 피드백을 제공 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-111">In the third tutorial, [Displaying Azure Spatial Anchor feedback](mrlearning-asa-ch3.md), you will learn how to provide users with feedback about anchor events and statuses when using Azure Spatial Anchors.</span></span>

## <a name="objectives"></a><span data-ttu-id="dc54c-112">목표</span><span class="sxs-lookup"><span data-stu-id="dc54c-112">Objectives</span></span>

* <span data-ttu-id="dc54c-113">HoloLens 2 용 Azure 공간 앵커를 사용 하 여 개발 하는 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="dc54c-113">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="dc54c-114">공간 앵커 만들기, 업로드 및 다운로드</span><span class="sxs-lookup"><span data-stu-id="dc54c-114">Create, upload, and download spatial anchors</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc54c-115">필수 조건</span><span class="sxs-lookup"><span data-stu-id="dc54c-115">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="dc54c-116">초보자를 위한 [자습서](mrlearning-base.md) 시리즈를 아직 완료 하지 않은 경우 해당 자습서를 먼저 완료 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-116">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="dc54c-117">올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="dc54c-117">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="dc54c-118">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="dc54c-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="dc54c-119">몇 가지 기본 C# 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="dc54c-119">Some basic C# programming ability</span></span>
* <span data-ttu-id="dc54c-120">[개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="dc54c-120">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="dc54c-121">Unity 2019.2.X가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="dc54c-121"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="dc54c-122">[빠른 시작: Azure 공간 앵커를 사용 하는 Unity HoloLens 앱 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) 자습서의 [공간 앵커 리소스 만들기](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) 섹션을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-122">Complete the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc54c-123">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-123">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="dc54c-124">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-124">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="dc54c-125">Unity 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="dc54c-125">Creating the Unity project</span></span>
<!-- TODO: Consider renaming to 'Creating and preparing the Unity scene and project'-->

<span data-ttu-id="dc54c-126">이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 위한 준비를 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-126">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="dc54c-127">이를 위해 먼저 다음 단계를 포함 하 여 [장치에 응용 프로그램 빌드](mrlearning-base-ch1.md#build-your-application-to-your-device) 지침을 제외 하 [고 프로젝트 및 첫 번째 응용 프로그램 초기화](mrlearning-base-ch1.md)를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-127">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="dc54c-128">[새 Unity 프로젝트를 만들고](mrlearning-base-ch1.md#create-new-unity-project) 적절 한 이름 (예: *Mrtk 자습서*)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-128">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*.</span></span>

2. [<span data-ttu-id="dc54c-129">Windows Mixed Reality의 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="dc54c-129">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="dc54c-130">가져오기 TextMesh Pro 필수 리소스</span><span class="sxs-lookup"><span data-stu-id="dc54c-130">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="dc54c-131">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="dc54c-131">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="dc54c-132">Mixed Reality Toolkit에 대 한 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="dc54c-132">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="dc54c-133">[혼합 현실 도구 키트를 Unity 장면에 추가](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) 하 고 *AzureSpatialAnchors* 와 같은 적절 한 이름을 장면에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-133">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="dc54c-134">그런 다음 [혼합 현실 도구 키트 프로필을 구성 하는 방법 (공간 인식 표시 옵션 변경)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필을 **DefaultHoloLens2ConfigurationProfile** 변경 하 고 공간 인식 메시의 표시 옵션을 **폐색**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-134">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="dc54c-135">위에서 설명한 [Mixed Reality 도구 키트에 대 한 unity 프로젝트 구성 도구](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) 설명에 설명 된 것 처럼 unity에 대해 MSBuild를 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-135">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="dc54c-136">기본 제공 Unity 패키지 추가</span><span class="sxs-lookup"><span data-stu-id="dc54c-136">Adding inbuilt Unity packages</span></span>
<!-- TODO: Consider renaming to 'Installing AR Foundation' -->

<span data-ttu-id="dc54c-137">이 섹션에서는 다음 섹션에서 가져올 Azure 공간 앵커 SDK에 필요 하므로 Unity의 기본 제공 AR 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-137">In this section, you will install Unity's inbuilt AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

<span data-ttu-id="dc54c-138">Unity 메뉴에서 **창** > **패키지 관리자**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-138">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="dc54c-140">AR 패키지를 목록에 표시 하기 전에 몇 초 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-140">It might take a few seconds before the AR Foundation package appears in the list.</span></span>

<span data-ttu-id="dc54c-141">패키지 관리자 창에서 **AR Foundation** 을 선택 하 고 **설치** 단추를 클릭 하 여 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-141">In the Package Manager window, select **AR Foundation** and install the package by clicking the **Install** button:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section2-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="dc54c-143">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="dc54c-143">Importing the tutorial assets</span></span>

<span data-ttu-id="dc54c-144">다음 Unity 사용자 지정 패키지를 다운로드 하 여 **나열 된 순서**대로 **가져옵니다** .</span><span class="sxs-lookup"><span data-stu-id="dc54c-144">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="dc54c-145">[AzureSpatialAnchors. unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (버전 2.1.1)</span><span class="sxs-lookup"><span data-stu-id="dc54c-145">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.1.1/AzureSpatialAnchors.unitypackage) (version 2.1.1)</span></span>
* [<span data-ttu-id="dc54c-146">MRTK. HoloLens2.2.3.0.2. unitypackage를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-146">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)
* [<span data-ttu-id="dc54c-147">MRTK. HoloLens2 AzureSpatialAnchors. 2.3.0.0. unitypackage</span><span class="sxs-lookup"><span data-stu-id="dc54c-147">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="dc54c-148">Unity 사용자 지정 패키지를 가져오는 방법에 대 한 미리 알림은 [혼합 현실 도구 키트 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 명령을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dc54c-148">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="dc54c-149">자습서 자산을 가져온 후 프로젝트 창이 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-149">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section3-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="dc54c-151">장면 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="dc54c-151">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="dc54c-152">이 섹션에서는 자습서 prefabs 중 일부를 추가 하 여 장면을 준비 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-152">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="dc54c-153">프로젝트 창에서 **자산** > **mrtk로 이동 합니다. AzureSpatialAnchors** > **Prefabs** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-153">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="dc54c-154">CTRL 단추를 누른 상태에서 **Buttonparent**, **debugwindow**, **명령**및 **parentanchor** 를 클릭 하 여 4 개의 prefabs 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-154">While holding down the CTRL button, click on **ButtonParent**, **DebugWindow**, **Instructions**, and **ParentAnchor** to select the four prefabs:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section4-step1-1.png)

<span data-ttu-id="dc54c-156">4 개의 prefabs가 선택 된 상태에서 계층 창으로 끌어 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-156">With the four prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section4-step1-2.png)

<span data-ttu-id="dc54c-158">장면의 개체에 초점을 맞추기 위해 ParentAnchor 개체를 두 번 클릭 한 다음 다시 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-158">To focus in on the objects in the scene, you can double-click on the ParentAnchor object, and then zoom slightly out again:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section4-step1-3.png)

> [!TIP]
> <span data-ttu-id="dc54c-160">장면에서 많은 아이콘이 표시 되는 경우, 예를 들어, 크게 프레임을 벗어난 아이콘이 표시 되는 경우 Gizmo 그리려면을 off 위치로 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">전환</a> 하 여 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-160">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="dc54c-161">장면을 작동 하도록 단추 구성</span><span class="sxs-lookup"><span data-stu-id="dc54c-161">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="dc54c-162">이 섹션에서는 스크립트를 장면에 추가 하 여 응용 프로그램에서 로컬 앵커와 Azure 공간 앵커가 동작 하는 방법의 기본 사항을 보여 주는 일련의 단추 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-162">In this section, you will add scripts into the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an application.</span></span>

### <a name="1-configure-the-pressable-button-holo-lens-2-script-component"></a><span data-ttu-id="dc54c-163">1. Pressable Button Holo Lens 2 (스크립트) 구성 요소를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-163">1. Configure the Pressable Button Holo Lens 2 (Script) component</span></span>

<span data-ttu-id="dc54c-164">계층 창에서 **Buttonparent** 개체를 확장 하 고 **StartAzureSession**라는 첫 번째 자식 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-164">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section5-step1-1.png)

<span data-ttu-id="dc54c-166">검사기 창에서 **Pressable Button Holo Lens 2 (스크립트)** 구성 요소를 찾고 **+** 아이콘을 클릭 하 여 **단추 누름 ()** 이벤트에 새 이벤트 수신기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-166">In the Inspector window, locate the **Pressable Button Holo Lens 2 (Script)** component and add a new event listener to the **Button Pressed ()** event by clicking the **+** icon:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section5-step1-2.png)

<span data-ttu-id="dc54c-168">계층 구조 창에서 StartAzureSession 개체를 선택한 상태에서 계층 창의 **Parentanchor** 개체를 클릭 하 고이 단추를 클릭 하 여 parentanchor 개체가 단추 누름 이벤트를 수신 대기 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-168">With the StartAzureSession object still selected in the Hierarchy window, click-and-drag the **ParentAnchor** object from the Hierarchy window into the empty **None (Object)** field of the event listener you just added to make the ParentAnchor object listen for button pressed events from this button:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section5-step1-3.png)

<span data-ttu-id="dc54c-170">동일한 이벤트 수신기의 **함수 없음** 드롭다운을 클릭 한 다음 **AnchorModuleScript** > **StartAzureSession ()** 를 선택 하 여이 단추에서 단추 누름 이벤트가 발생 했을 때 트리거되는 작업으로 StartAzureSession () 함수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-170">Click the **No Function** dropdown of the same event listener, then select **AnchorModuleScript** > **StartAzureSession ()** to set the StartAzureSession () function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section5-step1-4.png)

### <a name="2-configure-the-interactable-script-component"></a><span data-ttu-id="dc54c-172">2. Interactable (스크립트) 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="dc54c-172">2. Configure the Interactable (Script) component</span></span>

<span data-ttu-id="dc54c-173">StartAzureSession 개체가 계층 구조 창에서 선택 된 상태에서 검사기 창에서 **Interactable (스크립트)** 구성 요소를 찾아 **OnClick ()** 이벤트에 대해 위의 1 단계와 동일한 프로세스를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-173">With the StartAzureSession object still selected in the Hierarchy window, in the Inspector window, locate the **Interactable (Script)** component and repeat the same process as in step 1 above for the **OnClick ()** event:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section5-step2-1.png)

### <a name="3-configure-the-remaining-buttons"></a><span data-ttu-id="dc54c-175">3. 나머지 단추를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-175">3. Configure the remaining buttons</span></span>

<span data-ttu-id="dc54c-176">나머지 각 단추에 대해 위의 1 단계와 2 단계에 설명 된 프로세스를 완료 하 여 **단추 누름 ()** 및 **OnClick ()** 이벤트에 함수를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-176">For each of the remaining buttons, complete the process outlined in step 1 and 2 above to assign functions to both the **Button Pressed ()** and **OnClick ()** events:</span></span>

* <span data-ttu-id="dc54c-177">**Stopazuresession** 개체의 경우 AnchorModuleScript > **stopazuresession ()** 함수를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-177">For the **StopAzureSession** object, assign the AnchorModuleScript > **StopAzureSession ()** function.</span></span>
* <span data-ttu-id="dc54c-178">**Createazureanchor** 개체의 경우 AnchorModuleScript > **createazureanchor ()** 함수를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-178">For the **CreateAzureAnchor** object, assign the AnchorModuleScript > **CreateAzureAnchor ()** function,</span></span>
  * <span data-ttu-id="dc54c-179">그런 다음 **Parentanchor** 를 빈 **없음 (게임 개체)** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-179">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="dc54c-180">**Removelocalanchor** 개체의 경우 AnchorModuleScript > **removelocalanchor ()** 함수를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-180">For the **RemoveLocalAnchor** object, assign the AnchorModuleScript > **RemoveLocalAnchor ()** function,</span></span>
  * <span data-ttu-id="dc54c-181">그런 다음 **Parentanchor** 를 빈 **없음 (게임 개체)** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-181">then drag the **ParentAnchor** again into the empty **None (Game Object)** field.</span></span>
* <span data-ttu-id="dc54c-182">**FindAzureAnchor** 개체의 경우 AnchorModuleScript > **FindAzureAnchor ()** 함수를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-182">For the **FindAzureAnchor** object, assign the AnchorModuleScript > **FindAzureAnchor ()** function.</span></span>
* <span data-ttu-id="dc54c-183">**Deleteazureanchor** 개체의 경우 AnchorModuleScript > **deleteazureanchor ()** 함수를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-183">For the **DeleteAzureAnchor** object, assign the AnchorModuleScript > **DeleteAzureAnchor ()** function.</span></span>

### <a name="4-connect-the-scene-to-the-azure-resource"></a><span data-ttu-id="dc54c-184">4. 장면을 Azure 리소스에 연결</span><span class="sxs-lookup"><span data-stu-id="dc54c-184">4. Connect the scene to the Azure resource</span></span>

<span data-ttu-id="dc54c-185">계층 창에서 **Parentanchor** 개체를 선택 하 고 검사기 창에서 **공간 앵커 관리자 (스크립트)** 구성 요소로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-185">In the Hierarchy window, select the **ParentAnchor** object and in the Inspector window, scroll down to the **Spatial Anchor Manager (Script)** component.</span></span>

<span data-ttu-id="dc54c-186">그런 다음 **자격 증명** 섹션에서이 자습서의 [필수 구성](mrlearning-asa-ch1.md#prerequisites)요소로 만든 공간 앵커 계정 id 및 키를 해당 **공간 앵커 계정 Id** 및 **공간 앵커 계정 키** 필드에 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-186">Then, in the **Credentials** section, paste your Spatial Anchors Account ID and Key, which you created as part of this tutorial's [Prerequisites](mrlearning-asa-ch1.md#prerequisites), into the corresponding **Spatial Anchors Account Id** and **Spatial Anchors Account Key** fields:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section5-step4-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="dc54c-188">Azure 공간 앵커의 기본 동작 시도</span><span class="sxs-lookup"><span data-stu-id="dc54c-188">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="dc54c-189">이제 Azure 공간 앵커의 기본 사항을 보여 주기 위해 장면을 구성 했으므로 Azure 공간 앵커 어떠한 체험을 경험할 수 있도록 앱을 배포할 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-189">Now that your scene is configured to demonstrate the basics of Azure Spatial Anchors, it is time to deploy the app so you can experience Azure Spatial Anchors firsthand.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="dc54c-190">1. 필요한 추가 기능을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-190">1. Add additional required capabilities</span></span>

<span data-ttu-id="dc54c-191">Unity 메뉴에서 **편집** > **프로젝트 설정 ...** 을 선택 하 여 플레이어 설정 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-191">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section6-step1-1.png)

<span data-ttu-id="dc54c-193">플레이어 설정 창에서 **플레이어** , **게시 설정**을 차례로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-193">In the Player Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section6-step1-2.png)

<span data-ttu-id="dc54c-195">**게시 설정**에서 **기능** 섹션까지 아래로 스크롤하고 자습서의 시작 부분에서 프로젝트를 만들 때 사용 하도록 설정한 **Internetclient**, **마이크**및 **SpatialPerception** 기능이 사용 되도록 설정 되어 있는지 다시 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-195">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="dc54c-196">그런 다음 **Internetclientserver**, **PrivateNetworkClientServer**, **removablestorage**및 **웹캠** 기능을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-196">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, **RemovableStorage**, and **Webcam** capabilities:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section6-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="dc54c-198">2. HoloLens 2에 앱 배포</span><span class="sxs-lookup"><span data-stu-id="dc54c-198">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="dc54c-199">Azure 공간 앵커는 Unity에서 실행할 수 없으므로 Azure 공간 앵커 기능을 테스트 하려면 장치에 프로젝트를 배포 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-199">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="dc54c-200">Unity 프로젝트를 빌드하고 HoloLens 2에 배포 하는 방법에 대 한 미리 알림은 [장치에 응용 프로그램 빌드](mrlearning-base-ch1.md#build-your-application-to-your-device) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-200">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="dc54c-201">3. HoloLens 2에서 앱을 실행 하 고 앱 내 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-201">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="dc54c-202">Azure 공간 앵커는 인터넷을 사용 하 여 고정 데이터를 저장 하 고 로드 하므로 장치가 인터넷에 연결 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-202">Azure Spatial Anchors uses the internet to save and load the anchor data so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="dc54c-203">응용 프로그램이 장치에서 실행 되는 경우 Azure 공간 고정 자습서 명령 패널에 표시 된 화면에 표시 되는 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-203">When the application is running on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section6-step3-1.png)

## <a name="anchoring-an-experience"></a><span data-ttu-id="dc54c-205">환경 고정</span><span class="sxs-lookup"><span data-stu-id="dc54c-205">Anchoring an experience</span></span>

<span data-ttu-id="dc54c-206">이전 섹션에서는 Azure 공간 앵커의 기본 사항을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-206">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="dc54c-207">큐브를 사용 하 여 연결 된 앵커를 사용 하 여 부모 게임 개체를 나타내고 시각화 했습니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-207">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="dc54c-208">이 섹션에서는 ParentAnchor 개체의 자식으로 배치 하 여 전체 환경을 고정 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-208">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

### <a name="1-add-the-rocket-launcher-experience"></a><span data-ttu-id="dc54c-209">1. 로켓 시작 관리자 환경을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-209">1. Add the Rocket Launcher experience</span></span>

<span data-ttu-id="dc54c-210">프로젝트 창에서 **자산** > **mrtk로 이동 합니다. 자습서. GetPrefabs** 가 시작 > **RocketLauncher** 폴더 > 하 고 **RocketLauncher_Complete** prefab를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-210">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** folder and select the **RocketLauncher_Complete** prefab:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section7-step1-1.png)

<span data-ttu-id="dc54c-212">RocketLauncher_Complete prefab가 선택 된 상태에서 계층 창의 **Parentanchor** 개체 위쪽으로 끌어 parentanchor 개체의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-212">With the RocketLauncher_Complete prefab still selected, drag it on top of the **ParentAnchor** object in the Hierarchy window to make it a child of the ParentAnchor object:</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section7-step1-2.png)

### <a name="2-reposition-the-rocket-launcher-experience"></a><span data-ttu-id="dc54c-214">2. 로켓 시작 관리자 환경의 위치를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-214">2. Reposition the Rocket Launcher experience</span></span>

<span data-ttu-id="dc54c-215">다음과 같이 **Parentanchor** 개체가 계속 노출 되도록 하는 동시에 **RocketLauncher_Complete** 개체를 적절 한 배율 및 방향으로 배치 하 고 회전 하 고 크기를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-215">Position, rotate, and scale the **RocketLauncher_Complete** object to a suitable scale and orientation, while also ensuring the **ParentAnchor** object is still exposed, for example:</span></span>

* <span data-ttu-id="dc54c-216">변환 **위치** X = 0, Y = 0, Z = 3.75</span><span class="sxs-lookup"><span data-stu-id="dc54c-216">Transform **Position** X = 0, Y = 0, Z = 3.75</span></span>
* <span data-ttu-id="dc54c-217">변환 **회전** X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="dc54c-217">Transform **Rotation** X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="dc54c-218">변환 **배율** X = 10, Y = 10, Z = 10</span><span class="sxs-lookup"><span data-stu-id="dc54c-218">Transform **Scale** X = 10, Y = 10, Z = 10</span></span>

![mrlearning](images/mrlearning-asa/tutorial1-section7-step2-1.png)

<span data-ttu-id="dc54c-220">응용 프로그램에서 사용자는 이제 큐브를 이동 하 여 전체 로켓 시작 관리자 환경을 재배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-220">In the application, users may now reposition the entire Rocket Launcher experience by moving the cube.</span></span>

> [!TIP]
> <span data-ttu-id="dc54c-221">위치 조정 개체 (예:이 자습서에서 사용 되는 큐브) 사용, 환경 주위에 있는 경계 상자를 전환 하는 단추 사용, 위치 및 회전 사용 등의 다양 한 사용자 환경 흐름이 있습니다. gizmo 그리려면.</span><span class="sxs-lookup"><span data-stu-id="dc54c-221">There are a variety of user experience flows for repositioning experiences including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="dc54c-222">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-222">Congratulations</span></span>

<span data-ttu-id="dc54c-223">이 자습서에서는 Azure 공간 앵커의 기본 사항을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-223">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="dc54c-224">이 자습서에서는 Azure 공간 앵커 세션을 시작 및 중지 하 고 단일 장치에서 Azure 공간 앵커를 만들고, 업로드 하 고, 다운로드 하는 데 필요한 여러 단계를 살펴볼 수 있는 몇 가지 단추를 제공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-224">The tutorial provided you with several buttons that let you explore the various steps required to start and stop an Azure Spatial Anchors session and create, upload and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="dc54c-225">다음 단원에서는 응용 프로그램을 다시 시작한 후에도 검색을 위해 HoloLens 2에 Azure 앵커 Id를 저장 하는 방법과 여러 장치 간에 앵커 Id를 전송 하 여 공간 맞춤을 구현 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="dc54c-225">In the next lesson, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the application is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="dc54c-226">다음 단원: 2. Azure 공간 앵커 저장, 검색 및 공유</span><span class="sxs-lookup"><span data-stu-id="dc54c-226">Next Lesson: 2. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mrlearning-asa-ch2.md)
