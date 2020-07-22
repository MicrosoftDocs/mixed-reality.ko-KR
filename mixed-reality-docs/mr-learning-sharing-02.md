---
title: 다중 사용자 기능 자습서 - 2. Photon Unity 네트워킹 설정
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: e5817338dbed944232664a86f8b0625bc9d3e1e7
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306641"
---
# <a name="2-setting-up-photon-unity-networking"></a><span data-ttu-id="855f1-105">2. Photon Unity 네트워킹 설정</span><span class="sxs-lookup"><span data-stu-id="855f1-105">2. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="855f1-106">개요</span><span class="sxs-lookup"><span data-stu-id="855f1-106">Overview</span></span>

<span data-ttu-id="855f1-107">이 자습서에서는 PUN(Photon Unity Networking)을 사용하여 공유 환경을 만들기 위해 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-107">In this tutorial, you will prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="855f1-108">PUN 앱을 만들고 PUN 자산을 Unity 프로젝트로 가져오고 Unity 프로젝트를 PUN 앱에 연결하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-108">You will learn how to create a PUN app, import PUN assets into your Unity project, and connect your Unity project to the PUN app.</span></span>

## <a name="objectives"></a><span data-ttu-id="855f1-109">목표</span><span class="sxs-lookup"><span data-stu-id="855f1-109">Objectives</span></span>

* <span data-ttu-id="855f1-110">PUN 앱을 만드는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="855f1-110">Learn how to create a PUN app</span></span>
* <span data-ttu-id="855f1-111">PUN 자산을 찾아서 가져오는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="855f1-111">Learn how to find and import the PUN assets</span></span>
* <span data-ttu-id="855f1-112">Unity 프로젝트를 PUN 앱에 연결하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="855f1-112">Learn how to connect your Unity project to the PUN app</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="855f1-113">Unity 프로젝트 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="855f1-113">Creating and preparing the Unity project</span></span>

<span data-ttu-id="855f1-114">이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-114">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="855f1-115">이를 위해 먼저 [프로젝트 초기화 및 첫 번째 애플리케이션 배포](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-115">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="855f1-116">[Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정</span><span class="sxs-lookup"><span data-stu-id="855f1-116">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="855f1-117">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="855f1-117">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="855f1-118">TextMeshPro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="855f1-118">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="855f1-119">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="855f1-119">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="855f1-120">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="855f1-120">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="855f1-121">[장면 만들기 및 구성](mr-learning-base-02.md#creating-and-configuring-the-scene) 및 장면에 적절한 이름(예: *MultiUserCapabilities*) 지정</span><span class="sxs-lookup"><span data-stu-id="855f1-121">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="855f1-122">그런 다음, [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-122">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="855f1-123">**MRTK 구성 프로필**을 **DefaultHoloLens2ConfigurationProfile**로 변경</span><span class="sxs-lookup"><span data-stu-id="855f1-123">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="855f1-124">**공간 인식 메시 표시 옵션**을 **폐색**으로 변경</span><span class="sxs-lookup"><span data-stu-id="855f1-124">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="enabling-additional-capabilities"></a><span data-ttu-id="855f1-125">추가 기능 사용</span><span class="sxs-lookup"><span data-stu-id="855f1-125">Enabling additional capabilities</span></span>

<span data-ttu-id="855f1-126">Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 [플레이어 설정] 창을 연 다음, **플레이어** >  **게시 설정** 섹션을 차례로 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-126">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

<span data-ttu-id="855f1-128">**게시 설정**에서 **기능** 섹션까지 아래로 스크롤하여 위의 [Unity 프로젝트 구성](mr-learning-base-02.md#configuring-the-unity-project) 단계 중에 사용하도록 설정한 **InternetClient**, **Microphone**, **SpatialPerception** 및 **GazeInput** 기능이 사용하도록 설정되어 있는지 다시 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-128">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, **SpatialPerception**, and **GazeInput** capabilities, which you enabled during the [Configuring the Unity project](mr-learning-base-02.md#configuring-the-unity-project) step above, are enabled.</span></span>

<span data-ttu-id="855f1-129">그런 다음, 다음과 같은 추가 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-129">Then enable the following additional capabilities:</span></span>

* <span data-ttu-id="855f1-130">**InternetClientServer** 기능</span><span class="sxs-lookup"><span data-stu-id="855f1-130">**InternetClientServer** capability</span></span>
* <span data-ttu-id="855f1-131">**PrivateNetworkClientServer** 기능</span><span class="sxs-lookup"><span data-stu-id="855f1-131">**PrivateNetworkClientServer** capability</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="855f1-133">기본 제공 Unity 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="855f1-133">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="855f1-134">Unity 메뉴에서 **창** > **패키지 관리자**를 차례로 선택하여 [패키지 관리자] 창을 연 다음, **AR Foundation**을 선택하고, **설치** 단추를 클릭하여 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-134">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="855f1-136">Azure Spatial Anchors SDK에 필요하므로 AR Foundation 패키지를 설치합니다. 이 패키지는 다음 섹션에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-136">You are installing the AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="855f1-137">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="855f1-137">Importing the tutorial assets</span></span>

<span data-ttu-id="855f1-138">다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.</span><span class="sxs-lookup"><span data-stu-id="855f1-138">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="855f1-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)(버전 2.2.1)</span><span class="sxs-lookup"><span data-stu-id="855f1-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="855f1-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="855f1-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="855f1-141">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="855f1-141">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [<span data-ttu-id="855f1-142">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="855f1-142">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

<span data-ttu-id="855f1-143">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-143">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="855f1-145">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-145">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="855f1-146">MultiUserCapabilities 자습서 자산 패키지를 가져오면 유형 또는 네임스페이스가 누락되었음을 나타내는 [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) 오류가 Console 창에 보입니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-146">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="855f1-147">이것은 예상한 오류이며, 다음 섹션에서 PUN 자산을 가져오면 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-147">This is expected and will be resolved in the next section when you import the PUN assets.</span></span>

## <a name="importing-the-pun-assets"></a><span data-ttu-id="855f1-148">PUN 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="855f1-148">Importing the PUN assets</span></span>

<span data-ttu-id="855f1-149">Unity 메뉴에서 **Window** > **Asset Store**를 선택하여 Asset Store 창을 열고 Exit Games에서 **PUN 2 - FREE**를 검색하여 선택하고, **Download** 단추를 클릭하여 자산 패키지를 Unity 계정에 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-149">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, click the **Download** button to download the asset package to your Unity account.</span></span>

<span data-ttu-id="855f1-150">다운로드가 완료되면 **Import** 단추를 클릭하여 Import Unity Package 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-150">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

<span data-ttu-id="855f1-152">Import Unity Package(Unity 패키지 가져오기) 창에서 **All(모두)** 단추를 클릭하여 모든 자산이 선택되었는지 확인한 다음, **Import(가져오기)** 단추를 클릭하여 자산을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

<span data-ttu-id="855f1-154">Unity에서 Import(가져오기) 프로세스가 완료되면 Pun Wizard 창이 PUN Setup 메뉴가 로드된 상태로 나타납니다. 지금은 이 창을 무시하거나 닫으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-154">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a><span data-ttu-id="855f1-156">PUN 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="855f1-156">Creating the PUN application</span></span>

<span data-ttu-id="855f1-157">이 섹션에서는 Photon 계정이 없으면 만들고 새 PUN 앱을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-157">In this section, you will create a Photon account, if you don't already have one, and create a new PUN app.</span></span>

<span data-ttu-id="855f1-158">Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">대시보드</a>로 이동하여 로그인하고(사용할 계정이 있는 경우) 그렇지 않으면 **Create One** 링크를 클릭하여 지침에 따라 새 계정을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-158">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

<span data-ttu-id="855f1-160">로그인되면 **Create a New App** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-160">Once signed in, click the **Create a New App** button:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

<span data-ttu-id="855f1-162">Create a New Application(새 애플리케이션 만들기) 페이지에서 다음 값을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-162">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="855f1-163">Photon 유형의 경우 PUN을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-163">For Photon Type, select PUN</span></span>
* <span data-ttu-id="855f1-164">이름에는 적절한 이름(예: _MRTK Tutorials_)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-164">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="855f1-165">설명에는 적절한 설명(선택 사항)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-165">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="855f1-166">URL 필드는 비워둡니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-166">For Url, leave the field empty</span></span>

<span data-ttu-id="855f1-167">그런 다음, **만들기** 단추를 클릭하여 새 앱을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-167">Then click the **Create** button to create the new app:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

<span data-ttu-id="855f1-169">Photon에서 만들기 프로세스가 완료되면 새 PUN 앱이 대시보드에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-169">Once Photon has finished the creation process, the new PUN app will appear on your dashboard:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="855f1-171">Unity 프로젝트를 PUN 애플리케이션에 연결</span><span class="sxs-lookup"><span data-stu-id="855f1-171">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="855f1-172">이 섹션에서는 Unity 프로젝트를 이전 섹션에서 만든 PUN 앱에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-172">In this section, you will connect your Unity project to the PUN app you created in the previous section.</span></span>

<span data-ttu-id="855f1-173">Photon 대시보드에서 **App ID** 필드를 클릭하고 앱 ID 필드를 표시하여 클립보드에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-173">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

<span data-ttu-id="855f1-175">Unity 메뉴에서 **Window** > **Photon Unity Networking** > **PUN Wizard**를 선택하여 Pun Wizard 창을 열고 **Setup Project** 창을 클릭하여 PUN Setup 메뉴를 열어서 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-175">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="855f1-176">**AppId or Email** 필드에 이전 단계에서 복사한 PUN App ID를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-176">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="855f1-177">그런 다음, **Setup Project** 단추를 클릭하여 App ID를 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-177">Then click the **Setup Project** button to apply the app ID:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

<span data-ttu-id="855f1-179">Unity에서 PUN 설정 프로세스가 완료되면 PUN Setup 메뉴에 **Done!** 이라는 메시지가 표시되고</span><span class="sxs-lookup"><span data-stu-id="855f1-179">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="855f1-180">Project 창에 **PhotonServerSettings** 자산이 자동으로 선택되고 해당 속성이 Inspector 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-180">and automatically select the **PhotonServerSettings** asset in the Project window, so its properties are displayed in the Inspector window:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="855f1-182">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-182">Congratulations</span></span>

<span data-ttu-id="855f1-183">PUN 앱을 만들어서 Unity 프로젝트에 연결하는 데 성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-183">You have successfully created a PUN app and connected it to your Unity project.</span></span> <span data-ttu-id="855f1-184">다음 단계에서는 여러 사용자가 서로 볼 수 있도록 다른 사용자와 연결을 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="855f1-184">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

[<span data-ttu-id="855f1-185">다음 자습서: 3. 여러 사용자 연결</span><span class="sxs-lookup"><span data-stu-id="855f1-185">Next Tutorial: 3. Connecting multiple users</span></span>](mr-learning-sharing-03.md)
