---
title: Azure Spatial Anchors 자습서 - 2. Azure Spatial Anchors 시작
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure Spatial Anchors를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: a24b6b03ce75a57db49b3d0c875d123ea87c8162
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306128"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="69edd-105">2. Azure Spatial Anchors 시작</span><span class="sxs-lookup"><span data-stu-id="69edd-105">2. Getting started with Azure Spatial Anchors</span></span>

## <a name="overview"></a><span data-ttu-id="69edd-106">개요</span><span class="sxs-lookup"><span data-stu-id="69edd-106">Overview</span></span>

<span data-ttu-id="69edd-107">이 자습서에서는 Azure Spatial Anchors 세션을 시작 및 중지하고 단일 디바이스에서 Azure Spatial Anchors를 생성, 업로드 및 다운로드하는 데 필요한 여러 단계를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-107">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="69edd-108">목표</span><span class="sxs-lookup"><span data-stu-id="69edd-108">Objectives</span></span>

* <span data-ttu-id="69edd-109">HoloLens 2용 Azure Spatial Anchors를 사용하여 개발하는 방법에 대한 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="69edd-109">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="69edd-110">공간 앵커를 만들고 Azure에서 가져오는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="69edd-110">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="69edd-111">Unity 프로젝트 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="69edd-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="69edd-112">이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="69edd-113">이를 위해 먼저 [프로젝트 초기화 및 첫 번째 애플리케이션 배포](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-113">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="69edd-114">[Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정</span><span class="sxs-lookup"><span data-stu-id="69edd-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="69edd-115">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="69edd-115">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="69edd-116">TextMeshPro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="69edd-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="69edd-117">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="69edd-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="69edd-118">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="69edd-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="69edd-119">[장면 만들기 및 구성](mr-learning-base-02.md#creating-and-configuring-the-scene) 및 장면에 적절한 이름(예: *AzureSpatialAnchors*) 지정</span><span class="sxs-lookup"><span data-stu-id="69edd-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="69edd-120">그런 다음, [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="69edd-121">**MRTK 구성 프로필**을 **DefaultHoloLens2ConfigurationProfile**로 변경</span><span class="sxs-lookup"><span data-stu-id="69edd-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="69edd-122">**공간 인식 메시 표시 옵션**을 **폐색**으로 변경</span><span class="sxs-lookup"><span data-stu-id="69edd-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="69edd-123">기본 제공 Unity 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="69edd-123">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="69edd-124">Unity 메뉴에서 **창** > **패키지 관리자**를 차례로 선택하여 패키지 관리자 창을 연 다음, **AR Foundation**을 선택하고, **설치** 단추를 클릭하여 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-124">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="69edd-126">Azure Spatial Anchors SDK에 필요하므로 AR Foundation 패키지를 설치합니다. 이 패키지는 다음 섹션에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-126">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="69edd-127">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="69edd-127">Importing the tutorial assets</span></span>

<span data-ttu-id="69edd-128">다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.</span><span class="sxs-lookup"><span data-stu-id="69edd-128">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="69edd-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)(버전 2.2.1)</span><span class="sxs-lookup"><span data-stu-id="69edd-129">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="69edd-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="69edd-130">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="69edd-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="69edd-131">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

<span data-ttu-id="69edd-132">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-132">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="69edd-134">Unity 사용자 지정 패키지를 가져오는 방법은 [Mixed Reality Toolkit 가져오기](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69edd-134">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="69edd-135">장면 준비</span><span class="sxs-lookup"><span data-stu-id="69edd-135">Preparing the scene</span></span>

<span data-ttu-id="69edd-136">이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-136">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="69edd-137">프로젝트 창에서 **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** 폴더로 이동한 후 다음과 같은 프리팹을 클릭하고 Hierarchy(계층 구조) 창으로 끌어서 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="69edd-138">**ButtonParent** 프리팹</span><span class="sxs-lookup"><span data-stu-id="69edd-138">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="69edd-139">**DebugWindow** 프리팹</span><span class="sxs-lookup"><span data-stu-id="69edd-139">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="69edd-140">**Instructions** 프리팹</span><span class="sxs-lookup"><span data-stu-id="69edd-140">**Instructions** prefabs</span></span>
* <span data-ttu-id="69edd-141">**ParentAnchor** 프리팹</span><span class="sxs-lookup"><span data-stu-id="69edd-141">**ParentAnchor** prefabs</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="69edd-143">장면에 큰 아이콘(예: 방해가 되는 큰 틀의 'T' 아이콘)이 표시되는 경우 위 이미지와 같이 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos를 끄기 위치로 전환</a>하여 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-143">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="69edd-144">장면을 작동하도록 단추 구성</span><span class="sxs-lookup"><span data-stu-id="69edd-144">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="69edd-145">이 섹션에서는 스크립트를 장면에 추가하여 로컬 앵커와 Azure Spatial Anchors가 앱에서 동작하는 방식에 대한 기본 사항을 보여 주는 일련의 단추 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-145">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="69edd-146">Hierarchy(계층 구조) 창에서 **ButtonParent** 개체를 펼쳐서 **StartAzureSession**라는 첫 번째 자식 개체를 선택하고 Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-146">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="69edd-147">**ParentAnchor** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="69edd-147">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="69edd-148">**No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **StartAzureSession ()** 을 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="69edd-148">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="69edd-150">Hierarchy(계층 구조) 창에서 **StopAzureSession**이라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-150">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="69edd-151">**ParentAnchor** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="69edd-151">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="69edd-152">**No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **StopAzureSession ()** 을 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="69edd-152">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="69edd-154">Hierarchy(계층 구조) 창에서 **CreateAzureAnchor**라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-154">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="69edd-155">**ParentAnchor** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="69edd-155">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="69edd-156">**No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **CreateAzureAnchor ()** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="69edd-156">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="69edd-157">**ParentAnchor** 개체를 빈 **None (Game Object)** 필드에 할당하여 CreateAzureAnchor () 함수의 인수로 만들기</span><span class="sxs-lookup"><span data-stu-id="69edd-157">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="69edd-159">Hierarchy(계층 구조) 창에서 **RemoveLocalAnchor**라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-159">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="69edd-160">**ParentAnchor** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="69edd-160">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="69edd-161">**No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **RemoveLocalAnchor ()** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="69edd-161">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="69edd-162">**ParentAnchor** 개체를 빈 **None (Game Object)** 필드에 할당하여 RemoveLocalAnchor () 함수의 인수로 만들기</span><span class="sxs-lookup"><span data-stu-id="69edd-162">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="69edd-164">Hierarchy(계층 구조) 창에서 **FindAzureAnchor**라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-164">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="69edd-165">**ParentAnchor** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="69edd-165">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="69edd-166">**No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **FindAzureAnchor ()** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="69edd-166">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="69edd-168">Hierarchy(계층 구조) 창에서 **DeleteAzureAnchor**라는 다음 단추를 선택한 후, Inspector(인스펙터) 창에서 **Button Config Helper(스크립트)** 구성 요소의 **On Click ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-168">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="69edd-169">**ParentAnchor** 개체를 **None (Object)** 필드에 할당</span><span class="sxs-lookup"><span data-stu-id="69edd-169">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="69edd-170">**No Function**(함수 없음) 드롭다운에서 **AnchorModuleScript** > **DeleteAzureAnchor ()** 를 선택하고 이 함수를 이벤트가 트리거될 때 실행할 동작으로 설정</span><span class="sxs-lookup"><span data-stu-id="69edd-170">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="69edd-172">Azure 리소스에 장면 연결</span><span class="sxs-lookup"><span data-stu-id="69edd-172">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="69edd-173">Hierarchy(계층 구조) 창에서 **ParentAnchor** 개체를 선택하고, Inspector(인스펙터) 창에서 **Spatial Anchor Manager(스크립트)** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-173">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="69edd-174">이 자습서 시리즈에서 [필수 구성 요소](mr-learning-asa-01.md#prerequisites)의 일부로 생성된 Azure Spatial Anchors 계정의 자격 증명을 사용하여 **Credentials** 섹션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-174">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="69edd-175">**Spatial Anchors Account ID** 필드에 Azure Spatial Anchors 계정의 **계정 ID**를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-175">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="69edd-176">**Spatial Anchors Account Key** 필드에 Azure Spatial Anchors 계정의 기본 또는 보조 **액세스 키**를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-176">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="69edd-178">Azure Spatial Anchors의 기본 동작 사용해 보기</span><span class="sxs-lookup"><span data-stu-id="69edd-178">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="69edd-179">Azure Spatial Anchors는 Unity에서 실행할 수 없으므로 Azure Spatial Anchors 기능을 테스트하려면 프로젝트를 빌드하고 디바이스에 앱을 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-179">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="69edd-180">Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법은 [HoloLens 2에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69edd-180">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="69edd-181">앱이 디바이스에서 실행되는 경우 Azure Spatial Anchor 자습서 지침 패널에 표시되는 화면의 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-181">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="69edd-182">큐브를 다른 위치로 이동</span><span class="sxs-lookup"><span data-stu-id="69edd-182">Move the cube to a different location</span></span>
1. <span data-ttu-id="69edd-183">Azure 세션 시작</span><span class="sxs-lookup"><span data-stu-id="69edd-183">Start Azure Session</span></span>
1. <span data-ttu-id="69edd-184">Azure 앵커 만들기(큐브의 위치에 앵커 만들기)</span><span class="sxs-lookup"><span data-stu-id="69edd-184">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="69edd-185">Azure 세션 중지</span><span class="sxs-lookup"><span data-stu-id="69edd-185">Stop Azure Session</span></span>
1. <span data-ttu-id="69edd-186">로컬 앵커 제거(사용자가 큐브를 이동할 수 있도록 허용)</span><span class="sxs-lookup"><span data-stu-id="69edd-186">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="69edd-187">큐브를 다른 곳으로 이동</span><span class="sxs-lookup"><span data-stu-id="69edd-187">Move the cube somewhere else</span></span>
1. <span data-ttu-id="69edd-188">Azure 세션 시작</span><span class="sxs-lookup"><span data-stu-id="69edd-188">Start Azure Session</span></span>
1. <span data-ttu-id="69edd-189">Azure 앵커 찾기(큐브를 3단계의 위치에 배치)</span><span class="sxs-lookup"><span data-stu-id="69edd-189">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="69edd-190">Azure 앵커 삭제</span><span class="sxs-lookup"><span data-stu-id="69edd-190">Delete Azure Anchor</span></span>
1. <span data-ttu-id="69edd-191">Azure 세션 중지</span><span class="sxs-lookup"><span data-stu-id="69edd-191">Stop Azure session</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="69edd-193">Azure Spatial Anchors는 인터넷을 사용하여 앵커 데이터를 저장하고 로드하므로 디바이스가 인터넷에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-193">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="69edd-194">환경 고정</span><span class="sxs-lookup"><span data-stu-id="69edd-194">Anchoring an experience</span></span>

<span data-ttu-id="69edd-195">이전 섹션에서는 Azure Spatial Anchors의 기본 사항을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-195">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="69edd-196">큐브를 사용하여 연결된 앵커가 있는 부모 게임 개체를 표현하고 시각화했습니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-196">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="69edd-197">이 섹션에서는 전체 환경을 ParentAnchor 개체의 자식 항목으로 배치하여 이 환경을 고정시키는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-197">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="69edd-198">Hierarchy(계층 구조) 창에서 **ParentAnchor** 개체를 선택하고, Inspector(인스펙터) 창에서 **Transform** 구성 요소를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-198">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="69edd-199">**X 배율**을 1.1로 변경</span><span class="sxs-lookup"><span data-stu-id="69edd-199">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="69edd-200">**Z 배율**을 1.1로 변경</span><span class="sxs-lookup"><span data-stu-id="69edd-200">Change **Scale Z** to 1.1</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="69edd-202">프로젝트 창에서 **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** 폴더로 이동한 다음, **RoverExplorer_Complete** 프래팹을 클릭하여 Hierarchy(계층 구조) 창으로 끌어서 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-202">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="69edd-204">Hierarchy(계층 구조) 창에 RoverModule_Complete 개체가 아직 선택되어 있으면 **ParentAnchor** 개체로 끌어서 ParentAnchor 개체의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-204">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="69edd-206">이제 프로젝트를 다시 빌드하고 디바이스에 앱을 배포하는 경우, 크기 조정된 큐브를 이동하여 전체 Rover Explorer 환경을 재배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-206">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="69edd-207">위치 변경 개체(예: 이 자습서에 사용된 큐브) 사용, 환경 주위의 경계 상자를 해제/설정하는 단추 사용, 위치 및 회전 gizmos 사용 등을 포함하여 환경 위치 변경을 위한 다양한 사용자 환경 흐름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-207">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounding box that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="69edd-208">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-208">Congratulations</span></span>

<span data-ttu-id="69edd-209">이 자습서에서는 Azure Spatial Anchors의 기본 사항을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-209">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="69edd-210">이 자습서에는 Azure Spatial Anchors 세션을 시작 및 중지하는 데 필요한 다양한 단계를 살펴볼 수 있는 몇 가지 단추를 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-210">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="69edd-211">이를 통해 단일 디바이스에서 Azure Spatial Anchors를 생성, 업로드 및 다운로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-211">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="69edd-212">다음 자습서에서는 앱이 다시 시작된 후에도 검색을 위해 Azure 앵커 ID를 HoloLens 2에 저장하는 방법 및 여러 디바이스 간에 앵커 ID를 전송하여 공간 맞춤을 구현하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="69edd-212">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

[<span data-ttu-id="69edd-213">다음 자습서: 3. Azure Spatial Anchors 저장, 검색 및 공유</span><span class="sxs-lookup"><span data-stu-id="69edd-213">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
