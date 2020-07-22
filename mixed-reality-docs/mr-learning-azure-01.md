---
title: Azure 클라우드 자습서 - 1. HoloLens 2용 Azure Cloud Services
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다양한 Azure 서비스를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Azure, Mixed Reality, Unity, 자습서, HoloLens, HoloLens 2, Azure Blob Storage, Azure Table Storage, Azure Spatial Anchors, Azure Bot Framework
ms.localizationpriority: high
ms.openlocfilehash: 649046f9416c880d6e69b544866fba60d3e43f4c
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306003"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a><span data-ttu-id="39cff-105">1. HoloLens 2용 Azure Cloud Services</span><span class="sxs-lookup"><span data-stu-id="39cff-105">1. Azure Cloud Services for HoloLens 2</span></span>

## <a name="overview"></a><span data-ttu-id="39cff-106">개요</span><span class="sxs-lookup"><span data-stu-id="39cff-106">Overview</span></span>

<span data-ttu-id="39cff-107">**Azure 클라우드** 서비스를 **HoloLens 2** 애플리케이션에 가져오는 데 초점을 맞춘 이 자습서 시리즈를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-107">Welcome to this series of tutorials focused on bringing **Azure Cloud** services into a **HoloLens 2** application.</span></span> <span data-ttu-id="39cff-108">5부로 구성된 이 자습서 시리즈에서는 여러 **Azure 클라우드** 서비스를 **HoloLens 2**용 **Unity** 프로젝트에 통합하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-108">In this five-part tutorial series, you will learn how to integrate several **Azure Cloud** services into a **Unity** project for **HoloLens 2**.</span></span> <span data-ttu-id="39cff-109">연속된 각 챕터에서 새로운 **Azure 클라우드** 서비스를 추가하여 애플리케이션 기능 및 사용자 환경을 확장하는 한편, 각 **Azure 클라우드** 서비스의 기본 사항을 학습합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-109">With each consecutive chapter, you will add new **Azure Cloud** services to expand the application features and user experience, while teaching you the fundamentals of each **Azure Cloud** service.</span></span>

> [!NOTE]
> <span data-ttu-id="39cff-110">이 자습서 시리즈는 **HoloLens 2**에 집중하지만 Unity의 플랫폼 간 특성으로 인해 대부분의 학습 내용이 데스크톱 및 스마트폰 애플리케이션에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-110">This tutorial series will focus on the **HoloLens 2** but due the cross-platform nature of Unity, most of your learnings will also apply for Desktop and Smartphone applications.</span></span>

<span data-ttu-id="39cff-111">첫 번째 [HoloLens 2용 Azure Cloud Services 소개](mr-learning-azure-01.md) 자습서에서는 먼저 애플리케이션의 목표를 설명하고, 각 Azure 클라우드 서비스를 간략하게 소개한 다음, Unity 프로젝트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-111">In this first tutorial, [Introducing Azure Cloud Services for HoloLens 2](mr-learning-azure-01.md), you begin by explaining the goals of the application, briefly introduce you to each Azure Cloud service and set up the unity project.</span></span>

<span data-ttu-id="39cff-112">두 번째 [Azure Storage 통합](mr-learning-azure-02.md) 자습서에서는 Azure Storage를 데모 애플리케이션의 지속성 솔루션으로 통합하고, Blob Storage와 Table Storage 간의 차이점을 알아보고, 필요한 프로젝트 리소스를 준비하며, 장면을 설정하고, 데이터 읽기, 업데이트 및 삭제 작업을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-112">In the second tutorial, [Integrating Azure Storage](mr-learning-azure-02.md), you start off by integrating Azure Storage as the persistence solution for the demo application, learn the differences between Blob Storage and Table Storage, prepare the needed project resources, setup the scene and verify the read, update and delete data operations.</span></span>

<span data-ttu-id="39cff-113">세 번째 [Azure Custom Vision 통합](mr-learning-azure-03.md) 자습서를 계속 진행하면 Azure Custom Vision을 사용하여 HoloLens 2 애플리케이션에서 이미지를 학습하고 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-113">Continuing with the third tutorial, [Integrating Azure Custom Vision](mr-learning-azure-03.md), you will use Azure Custom Vision to train and detect images in the HoloLens 2 application.</span></span> <span data-ttu-id="39cff-114">이 챕터는 사용자 고유의 Azure Custom Vision 리소스를 설정하고 장면 구성 요소를 준비하며, 애플리케이션 내에서 사용자 고유의 이미지를 학습하고 검색하는 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-114">The chapter starts off with setting up your own Azure Custom Vision resource, preparing the scene components and getting into action by training and detecting your own images from inside the application.</span></span>

<span data-ttu-id="39cff-115">다음으로, 네 번째 [Azure Spatial Anchors 통합](mr-learning-azure-04.md) 자습서에서 Azure Spatial Anchors 서비스를 검색하여 위치를 저장하여 찾고, 핵심 개념을 학습하며, 필요한 리소스를 준비하고, 애플리케이션의 새 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-115">Next you advance in the fourth tutorial, [Integrating Azure Spatial Anchors](mr-learning-azure-04.md), with exploring Azure Spatial Anchors service to save and find locations, learn the core concepts, prepare necessary resources, setup the scene and start using the new feature in the application.</span></span>

<span data-ttu-id="39cff-116">다섯 번째 [LUIS와 Azure Bot Service 통합](mr-learning-azure-05.md) 자습서를 통해 새로운 사용자 상호 작용 방법인 자연어를 애플리케이션에 제공하여 마무리합니다!</span><span class="sxs-lookup"><span data-stu-id="39cff-116">With the fifth tutorial, [Integrating Azure Bot Service with LUIS](mr-learning-azure-05.md), you finalize by giving the application a new method of user interaction: natural language!</span></span> <span data-ttu-id="39cff-117">이 기능은 LUIS(Language Understanding)에서 Azure Bot Framework를 사용하여 실현됩니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-117">This feature will be realized by using the Azure Bot Framework together with Language Understanding (LUIS).</span></span> <span data-ttu-id="39cff-118">이 마지막 챕터에서는 Azure Bot Service의 기본 사항을 설명하고, 프로세스의 속도를 향상시키기 위해 Bot Framework 작성기를 제로 코드 솔루션으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-118">This final chapter teaches you the basics of Azure Bot Service and to speed up the process you will be using the Bot Framework Composer as a zero code solution.</span></span> <span data-ttu-id="39cff-119">봇이 만들어지면 이를 장면에 통합하고 HoloLens 2 애플리케이션의 마지막 단계에서 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-119">Once the bot is created, you will integrate it into the scene and give it a run with the final stage of the HoloLens 2 application.</span></span>

## <a name="application-goals"></a><span data-ttu-id="39cff-120">애플리케이션 목표</span><span class="sxs-lookup"><span data-stu-id="39cff-120">Application goals</span></span>

<span data-ttu-id="39cff-121">이 자습서 시리즈에서는 이미지에서 개체를 감지하고 해당 공간 위치를 찾을 수 있는 **HoloLens 2** 애플리케이션을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-121">In this tutorial series, you will build a **HoloLens 2** application that can detect objects from images and find its spatial location.</span></span> <span data-ttu-id="39cff-122">도메인 언어를 설정하려면 이제 **추적된 개체**에서 이러한 엔터티를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-122">To set a domain language, you call such entities from now **Tracked Object**.</span></span>
<span data-ttu-id="39cff-123">사용자는 컴퓨터 비전 및/또는 공간 위치를 통해 이미지 세트를 연결하거나 둘 모두를 연결하는 **추적된 개체**를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-123">The user can create a **Tracked Object** to either or both associate a set of images via computer vision and/or a spatial location.</span></span> <span data-ttu-id="39cff-124">모든 데이터가 클라우드에 유지되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-124">All data must be persisted into the cloud.</span></span> <span data-ttu-id="39cff-125">또한 애플리케이션의 일부 측면은 필요에 따라 봇을 통해 지원되는 자연어로 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-125">Furthermore some aspects of the application will be optionally controlled by natural language assisted through a bot.</span></span>

### <a name="features"></a><span data-ttu-id="39cff-126">기능</span><span class="sxs-lookup"><span data-stu-id="39cff-126">Features</span></span>

* <span data-ttu-id="39cff-127">데이터 및 이미지에 대한 기본 관리</span><span class="sxs-lookup"><span data-stu-id="39cff-127">Basic managing of data and images</span></span>
* <span data-ttu-id="39cff-128">이미지 학습 및 검색</span><span class="sxs-lookup"><span data-stu-id="39cff-128">Image training and detection</span></span>
* <span data-ttu-id="39cff-129">공간 위치 및 지침 저장</span><span class="sxs-lookup"><span data-stu-id="39cff-129">Storing a spatial location and guidance to it</span></span>
* <span data-ttu-id="39cff-130">자연어를 통해 일부 기능을 사용하는 봇 도우미</span><span class="sxs-lookup"><span data-stu-id="39cff-130">Bot assistant to use some features via natural language</span></span>

## <a name="azure-cloud-services"></a><span data-ttu-id="39cff-131">Azure 클라우드 서비스</span><span class="sxs-lookup"><span data-stu-id="39cff-131">Azure Cloud services</span></span>

<span data-ttu-id="39cff-132">애플리케이션에 필요한 기능을 해결하려면 다음과 같은 **Azure 클라우드** 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-132">To solve the required features for the application, you will use these **Azure Cloud** services:</span></span>

### <a name="azure-storage"></a><span data-ttu-id="39cff-133">Azure Storage</span><span class="sxs-lookup"><span data-stu-id="39cff-133">Azure Storage</span></span>

<span data-ttu-id="39cff-134">[Azure Storage](https://azure.microsoft.com/services/storage/)는 지속성 솔루션에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-134">You will use [Azure Storage](https://azure.microsoft.com/services/storage/) for the persistence solution.</span></span> <span data-ttu-id="39cff-135">이를 통해 데이터를 테이블에 저장하고 이미지와 같은 큰 이진 파일을 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-135">It allows you to store data on a table and upload large binaries like images.</span></span>

### <a name="azure-custom-vision"></a><span data-ttu-id="39cff-136">Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="39cff-136">Azure Custom Vision</span></span>

<span data-ttu-id="39cff-137">[Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)([Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)의 일부)을 사용하면 이미지 세트인 *추적된 개체*에 연결하고, 이 세트에서 기계 학습 모델을 학습시키고, *추적된 개체*를 감지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-137">With [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (part of the [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) you can associate to *Tracked Objects* a set of images, train a machine learning model on the set and detect the *Tracked Object*.</span></span>

### <a name="azure-spatial-anchors"></a><span data-ttu-id="39cff-138">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="39cff-138">Azure Spatial Anchors</span></span>

<span data-ttu-id="39cff-139">*추적된 개체* 위치를 저장하고 이를 찾기 위한 단계별 지침을 제공하려면 [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-139">To store a *Tracked Object* location and give a guided directions to find it, you use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

### <a name="azure-bot-service"></a><span data-ttu-id="39cff-140">Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="39cff-140">Azure Bot Service</span></span>

<span data-ttu-id="39cff-141">이 애플리케이션은 주로 기존 UI를 기반으로 하므로 [Azure Bot Service](https://azure.microsoft.com/services/bot-service/)를 사용하여 일부 프로필을 추가하고 새로운 상호 작용 방법으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-141">The application is mainly driven by traditional UI, so you use the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) to add some personality and act as a new interaction method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="39cff-142">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="39cff-142">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="39cff-143">[시작 자습서](mr-learning-base-01.md) 시리즈를 아직 완료하지 않은 경우 먼저 해당 자습서를 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-143">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="39cff-144">올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="39cff-144">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="39cff-145">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="39cff-145">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="39cff-146">몇 가지 기본 C# 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="39cff-146">Some basic C# programming ability</span></span>
* <span data-ttu-id="39cff-147">[개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="39cff-147">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="39cff-148">연결된 웹캠(Unity 편집기에서 테스트하려는 경우)</span><span class="sxs-lookup"><span data-stu-id="39cff-148">A connected webcam if you like to test from Unity editor</span></span>
* <span data-ttu-id="39cff-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>(Unity 2019.3.X가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가됨)</span><span class="sxs-lookup"><span data-stu-id="39cff-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="39cff-150">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.3.X입니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-150">The recommended Unity version for this tutorial series is Unity 2019.3.X.</span></span> <span data-ttu-id="39cff-151">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-151">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="39cff-152">Unity 프로젝트 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="39cff-152">Creating and preparing the Unity project</span></span>

<span data-ttu-id="39cff-153">이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-153">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="39cff-154">이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-154">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="39cff-155">[Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름 지정(예: *Azure Cloud Tutorials*)</span><span class="sxs-lookup"><span data-stu-id="39cff-155">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *Azure Cloud Tutorials*</span></span>
2. [<span data-ttu-id="39cff-156">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="39cff-156">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="39cff-157">TextMeshPro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="39cff-157">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="39cff-158">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="39cff-158">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="39cff-159">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="39cff-159">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="39cff-160">[장면 만들기 및 구성](mr-learning-base-02.md#creating-and-configuring-the-scene) 및 적절한 장면 이름 지정(예: *AzureCloudServices*)</span><span class="sxs-lookup"><span data-stu-id="39cff-160">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureCloudServices*</span></span>

<span data-ttu-id="39cff-161">그런 다음, [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필을 **DefaultHoloLens2ConfigurationProfile**로 변경하고, 공간 인식 메시의 표시 옵션을 **폐색**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-161">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="39cff-162">기본 제공 Unity 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="39cff-162">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="39cff-163">Unity 메뉴에서 **창** > **패키지 관리자**를 차례로 선택하여 [패키지 관리자] 창을 연 다음, **AR Foundation**을 선택하고, **설치** 단추를 클릭하여 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-163">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-azure](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="39cff-165">Azure Spatial Anchors SDK에 필요하므로 AR Foundation 패키지를 설치합니다. 이 패키지는 다음 섹션에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-165">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="39cff-166">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="39cff-166">Importing the tutorial assets</span></span>

<span data-ttu-id="39cff-167">다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.</span><span class="sxs-lookup"><span data-stu-id="39cff-167">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="39cff-168">Unity용 Azure 스토리지</span><span class="sxs-lookup"><span data-stu-id="39cff-168">Azure storage for Unity</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="39cff-169">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="39cff-169">Azure Spatial Anchors</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [<span data-ttu-id="39cff-170">MRTK.Tutorials.AzureCloudServices</span><span class="sxs-lookup"><span data-stu-id="39cff-170">MRTK.Tutorials.AzureCloudServices</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/a-tag/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> <span data-ttu-id="39cff-171">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-171">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="39cff-172">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-172">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section4-step1-1.png)

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="39cff-174">장면 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="39cff-174">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="39cff-175">이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-175">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="39cff-176">[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** 폴더로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-176">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span> <span data-ttu-id="39cff-177">Ctrl 단추를 누른 채 **SceneController**, **RootMenu** 및 **DataManager**를 클릭하여 세 개의 프리팹을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-177">While holding down the CTRL button, click on **SceneController**, **RootMenu** and **DataManager** to select the three prefabs:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-1.png)

<span data-ttu-id="39cff-179">**SceneController(프리팹)** 에는 **SceneController(스크립트)** 및 **UnityDispatcher(스크립트)** 라는 두 개의 스크립트가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-179">The **SceneController (prefab)** contains two scripts, **SceneController (script)** and **UnityDispatcher (script)**.</span></span> <span data-ttu-id="39cff-180">**SceneController** 스크립트 구성 요소는 여러 UX 함수를 포함하고 있고 사진 캡처 기능을 용이하게 하며, **UnityDispatcher**는 Unity 주 스레드에서 작업을 실행할 수 있는 도우미 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-180">The **SceneController** script component contains several UX functions and facilitates the photo capture functionality while **UnityDispatcher** is a helper class to allow execute actions on the Unity main thread.</span></span>

<span data-ttu-id="39cff-181">**RootMenu(프리팹)** 는 다양한 작은 스크립트 구성 요소를 통해 서로 연결되는 모든 UI 창을 보유하고 애플리케이션의 일반 UX 흐름을 제어하는 기본 UI 프리팹입니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-181">The **RootMenu (prefab)** is the primary UI prefab that holds all UI windows that are connected to each other through various small script components and control the general UX flow of the application.</span></span>

<span data-ttu-id="39cff-182">**DataManager(프리팹)** 는 Azure 스토리지와의 통신을 담당하며 다음 자습서에서 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-182">The **DataManager (prefab)** is responsible for talking to Azure storage and will be explained further in the next tutorial.</span></span>

<span data-ttu-id="39cff-183">이제 세 개의 프리팹을 선택한 채 [계층 구조] 창으로 끌어 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-183">Now with the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-2.png)

<span data-ttu-id="39cff-185">장면의 개체에 초점을 맞추기 위해 **RootMenu** 개체를 두 번 클릭한 다음, 약간씩 다시 축소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-185">To focus in on the objects in the scene, you can double-click on the **RootMenu** object, and then zoom slightly out again:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> <span data-ttu-id="39cff-187">장면에서 큰 아이콘(예: 틀이 있는 매력적인 큰 'T' 아이콘)이 표시되는 경우 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmos를 끄기 위치로 전환</a>하여 이러한 아이콘을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-187">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-scene"></a><span data-ttu-id="39cff-188">장면 구성</span><span class="sxs-lookup"><span data-stu-id="39cff-188">Configuring the scene</span></span>

<span data-ttu-id="39cff-189">이 섹션에서는 *SceneManager*, *DataManager* 및 *RootMenu*를 모두 연결하여 다음 [Azure Storage 통합](mr-learning-azure-01.md) 자습서에서 사용할 수 있도록 작업 장면을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-189">In this section, you will connect *SceneManager*, *DataManager* and *RootMenu* together to have a working scene to be ready for the following [Integrating Azure storage](mr-learning-azure-01.md) tutorial.</span></span>

### <a name="connect-the-objects"></a><span data-ttu-id="39cff-190">개체 연결</span><span class="sxs-lookup"><span data-stu-id="39cff-190">Connect the objects</span></span>

<span data-ttu-id="39cff-191">[계층 구조] 창에서 **DataManager** 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-191">In the Hierarchy window, select the **DataManager** object:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-1.png)

<span data-ttu-id="39cff-193">[검사기] 창에서 **DataManager(스크립트)** 구성 요소를 찾습니다. 그러면 **On Data Manager Ready ()** 이벤트에 빈 슬롯이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-193">In the Inspector window, locate the **DataManager (Script)** component and you will see an empty slot on the **On Data Manager Ready ()** event.</span></span> <span data-ttu-id="39cff-194">이제 [계층 구조] 창에서 **SceneController** 개체를 **On Data Manager Ready ()** 이벤트로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-194">Now from the Hierarchy window drag the **SceneController** object into the **On Data Manager Ready ()** event.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-2.png)

<span data-ttu-id="39cff-196">이벤트의 드롭다운 메뉴가 활성화되었음을 알 수 있습니다. 드롭다운 메뉴를 클릭하고, **SceneController**로 이동하고, 하위 메뉴에서 **Init ()** 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-196">You will notice that the dropdown menu of the event became active, click on the dropdown menu and navigate to **SceneController** and in the sub menu select the **Init ()** option:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-3.png)

<span data-ttu-id="39cff-198">[계층 구조] 창에서 **SceneController** 개체를 선택합니다. 그러면 [검사기]에서 **SceneController**(스크립트) 구성 요소를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-198">From the Hierarchy window, select the **SceneController** object, there in the Inspector you will find the **SceneController** (script) component.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-4.png)

<span data-ttu-id="39cff-200">채워지지 않은 몇 가지 필드가 있습니다. 이를 변경해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-200">You will see that there are several unpopulated fields, let's change that.</span></span> <span data-ttu-id="39cff-201">**DataManager** 개체를 [계층 구조]에서 *데이터 관리자* 필드로 이동하고, **RootMenu** GameObject를 [계층 구조]에서 *주 메뉴* 필드로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-201">Move the **DataManager** object from the Hierarchy into the *Data Manager* field and move the **RootMenu** GameObject from the Hierarchy into the *Main Menu* field.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section6-step1-5.png)

<span data-ttu-id="39cff-203">이제 장면이 다음 자습서에서 사용할 수 있도록 준비되었습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-203">Now your scene is ready for the upcoming tutorials.</span></span> <span data-ttu-id="39cff-204">프로젝트에 저장하는 것을 잊지 마세요.</span><span class="sxs-lookup"><span data-stu-id="39cff-204">Don't forget to save it into your project.</span></span>

## <a name="prepare-project-build-pipeline"></a><span data-ttu-id="39cff-205">프로젝트 빌드 파이프라인 준비</span><span class="sxs-lookup"><span data-stu-id="39cff-205">Prepare project build pipeline</span></span>

<span data-ttu-id="39cff-206">프로젝트는 아직 콘텐츠로 채워야 하지만 **HoloLens 2**에 맞게 빌드할 수 있도록 몇 가지 항목을 준비해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-206">While the project yet has to be filled with content, you have to perform some preparations, so the project is ready for building for **HoloLens 2**.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="39cff-207">1. 필요한 추가 기능 추가</span><span class="sxs-lookup"><span data-stu-id="39cff-207">1. Add additional required capabilities</span></span>

<span data-ttu-id="39cff-208">Unity 메뉴에서 **Edit(편집)**  > **Project Settings(프로젝트 설정)...** 를 차례로 선택하여 Project Settings 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-208">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-1.png)

<span data-ttu-id="39cff-210">[프로젝트 설정] 창에서 **플레이어**, **게시 설정**을 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-210">In the Project Settings window, select **Player** and then **Publishing Settings**:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-2.png)

<span data-ttu-id="39cff-212">**게시 설정**에서 **기능** 섹션까지 아래로 스크롤하여 자습서의 시작 부분에서 프로젝트를 만들 때 사용하도록 설정한 **InternetClient**, **Microphone** 및 **SpatialPerception** 기능이 사용하도록 설정되어 있는지 다시 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-212">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone** and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="39cff-213">그런 다음, **InternetClientServer**, **PrivateNetworkClientServer** 및 **Webcam** 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-213">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **Webcam** capabilities:</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="39cff-215">2. HoloLens 2에 앱 배포</span><span class="sxs-lookup"><span data-stu-id="39cff-215">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="39cff-216">이 자습서 시리즈에서 사용할 일부 기능은 Unity 편집기 내에서 실행할 수 없습니다. 즉, 애플리케이션을 HoloLens 2 디바이스에 배포하는 방법을 잘 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-216">Not all features that you will use in this tutorial series can run inside the Unity editor, this means that you need to be familiar with deploying the application to your HoloLens 2 device.</span></span>

> [!TIP]
> <span data-ttu-id="39cff-217">Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법을 미리 알아보려면 [시작 자습서 - 디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39cff-217">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Getting started tutorials - Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="39cff-218">3. HoloLens 2에서 앱 실행 및 앱 내 지침 수행</span><span class="sxs-lookup"><span data-stu-id="39cff-218">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="39cff-219">모든 Azure 서비스에서 인터넷을 사용하므로 디바이스가 인터넷에 연결되어 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="39cff-219">All Azure Services uses the internet, so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="39cff-220">애플리케이션이 디바이스에서 실행되는 경우 다음과 같은 요청된 기능에 대한 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-220">When the application is running on your device, accept access to the following requested capabilities:</span></span>

* <span data-ttu-id="39cff-221">마이크</span><span class="sxs-lookup"><span data-stu-id="39cff-221">Microphone</span></span>
* <span data-ttu-id="39cff-222">카메라</span><span class="sxs-lookup"><span data-stu-id="39cff-222">Camera</span></span>

<span data-ttu-id="39cff-223">*채팅 봇* 및 *Custom Vision*과 같은 서비스가 제대로 작동하려면 이러한 기능이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-223">These capabilities are required for services like *Chat Bot* and *Custom Vision* to function properly.</span></span>

## <a name="congratulations"></a><span data-ttu-id="39cff-224">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-224">Congratulations</span></span>

<span data-ttu-id="39cff-225">이 자습서에서는 자습서 시리즈를 소개하고, 구현할 기능 및 **Azure 클라우드** 서비스를 연결하여 *HoloLens 2* 애플리케이션을 실행하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-225">In this tutorial, you were introduced to the tutorial series, learned about the features you will implement and how **Azure Cloud** services tie in to making your *HoloLens 2* application happen.</span></span> <span data-ttu-id="39cff-226">필요한 구성 요소를 프로젝트에 추가하고, 이 자습서 시리즈에서 사용할 장면을 준비했습니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-226">You added the required components into the project and prepared the scene for this tutorial series.</span></span>

<span data-ttu-id="39cff-227">다음 단원에서는 데이터와 이미지를 저장하기 위한 클라우드 기반 지속성 솔루션으로 Azure 스토리지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="39cff-227">In the next lesson, you will use Azure storage as a cloud based persistence solution for storing data and images.</span></span>

[<span data-ttu-id="39cff-228">다음 자습서: 2. Azure Storage 통합</span><span class="sxs-lookup"><span data-stu-id="39cff-228">Next tutorial: 2. Integrating Azure storage</span></span>](mr-learning-azure-02.md)
