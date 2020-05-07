---
title: Azure Speech Services 자습서 - 1. 음성 인식 및 전사 통합 및 사용
description: 이 과정을 완료하여 혼합 현실 애플리케이션 내에서 Azure Speech SDK를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 71a6c2124258f05e80e624b940386db72a36070b
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604984"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="25a05-105">1. 음성 인식 및 전사 통합 및 사용</span><span class="sxs-lookup"><span data-stu-id="25a05-105">1. Integrating and using speech recognition and transcription</span></span>

## <a name="overview"></a><span data-ttu-id="25a05-106">개요</span><span class="sxs-lookup"><span data-stu-id="25a05-106">Overview</span></span>


<span data-ttu-id="25a05-107">이 자습서 시리즈에서는 HoloLens 2에서 Azure Speech Services의 사용을 검색하는 Mixed Reality 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-107">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="25a05-108">이 자습서 시리즈를 완료하면 디바이스의 마이크를 사용하여 음성을 텍스트로 실시간으로 전사하고, 음성을 다른 언어로 번역하고, 의도 인식 기능을 활용하여 AI를 통해 음성 명령을 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-108">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="25a05-109">목표</span><span class="sxs-lookup"><span data-stu-id="25a05-109">Objectives</span></span>

* <span data-ttu-id="25a05-110">Azure Speech Services를 HoloLens 2 애플리케이션과 통합하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="25a05-110">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="25a05-111">음성 인식을 사용하여 텍스트를 전사하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="25a05-111">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="25a05-112">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="25a05-112">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="25a05-113">[시작 자습서](mrlearning-base.md) 시리즈를 아직 완료하지 않은 경우 먼저 해당 자습서를 완료하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-113">If you have not completed the [Getting started tutorials](mrlearning-base.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="25a05-114">올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="25a05-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="25a05-115">Windows 10 SDK 10.0.18362.0 이상</span><span class="sxs-lookup"><span data-stu-id="25a05-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="25a05-116">몇 가지 기본 C# 프로그래밍 기능</span><span class="sxs-lookup"><span data-stu-id="25a05-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="25a05-117">[개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="25a05-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="25a05-118">Unity 2019.2.X가 설치되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가된 <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="25a05-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25a05-119">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.2.X입니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="25a05-120">이 버전은 필수 구성 요소에서 설명한 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="25a05-121">Unity 프로젝트 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="25a05-121">Creating and preparing the Unity project</span></span>

<span data-ttu-id="25a05-122">이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-122">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="25a05-123">이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mrlearning-base-ch1.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mrlearning-base-ch1.md#build-your-application-to-your-device) 지침은 제외합니다. 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-123">For this, first follow the [Initializing your project and first application](mrlearning-base-ch1.md), excluding the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="25a05-124">[새 Unity 프로젝트 만들기](mrlearning-base-ch1.md#create-new-unity-project) 및 적절한 이름(예: *MRTK Tutorials*) 지정</span><span class="sxs-lookup"><span data-stu-id="25a05-124">[Create new Unity project](mrlearning-base-ch1.md#create-new-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="25a05-125">Windows Mixed Reality용 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="25a05-125">Configure the Unity project for Windows Mixed Reality</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-windows-mixed-reality)

3. [<span data-ttu-id="25a05-126">TextMesh Pro Essential Resources 가져오기</span><span class="sxs-lookup"><span data-stu-id="25a05-126">Import TextMesh Pro Essential Resources</span></span>](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources)

4. [<span data-ttu-id="25a05-127">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="25a05-127">Import the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit)

5. [<span data-ttu-id="25a05-128">Mixed Reality Toolkit용 Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="25a05-128">Configure the Unity project for the Mixed Reality Toolkit</span></span>](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit)

6. <span data-ttu-id="25a05-129">[Unity 장면에 Mixed Reality Toolkit 추가](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) 및 장면에 적절한 이름(예: *AzureSpeechServices*) 지정</span><span class="sxs-lookup"><span data-stu-id="25a05-129">[Add the Mixed Reality Toolkit to the Unity scene](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="25a05-130">그런 다음, [Mixed Reality Toolkit 프로필을 구성하는 방법(공간 인식 표시 옵션 변경)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필을 **DefaultHoloLens2ConfigurationProfile**로 변경하고, 공간 인식 메시의 표시 옵션을 **폐색**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-130">Then follow the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

> [!CAUTION]
> <span data-ttu-id="25a05-131">위에 연결된 [Mixed Reality Toolkit용 Unity 프로젝트 구성](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) 지침에서 설명한 대로 Unity용 MSBuild를 사용하지 않도록 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-131">As mentioned in the [Configure the Unity project for the Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-unity-project-for-the-mixed-reality-toolkit) instructions linked above, it is strongly recommended to not enable MSBuild for Unity.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="25a05-132">음성 명령 시작 동작 구성</span><span class="sxs-lookup"><span data-stu-id="25a05-132">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="25a05-133">음성 인식 및 전사에 음성 SDK를 사용하므로 음성 SDK 기능을 방해하지 않도록 MRTK 음성 명령을 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-133">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="25a05-134">이를 위해 음성 명령 시작 동작을 [자동 시작]에서 [수동 시작]으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-134">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="25a05-135">[계층 구조] 창에서 **MixedRealityToolkit** 개체를 선택한 채 [검사기] 창에서 **입력** 탭을 선택하고, **DefaultHoloLens2InputSystemProfile** 및 **DefaultMixedRealitySpeechCommandsProfile**을 복제한 다음, 음성 명령 **시작 동작**을 **수동 시작**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-135">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="25a05-137">MRTK 프로필을 복제하고 구성하는 방법을 미리 알아보려면 [Mixed Reality Toolkit 프로필을 구성하는 방법(공간 인식 표시 옵션 변경)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-137">For a reminder on how to clone and configure MRTK profiles, you can refer to the [How to configure the Mixed Reality Toolkit Profiles (Change Spatial Awareness Display Option)](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) instructions.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="25a05-138">기능 구성</span><span class="sxs-lookup"><span data-stu-id="25a05-138">Configuring the capabilities</span></span>

<span data-ttu-id="25a05-139">Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 [플레이어 설정] 창을 연 다음, **플레이어** >  **게시 설정** 섹션을 차례로 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-139">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="25a05-141">**게시 설정**에서 **기능** 섹션까지 아래로 스크롤하여 자습서의 시작 부분에서 프로젝트를 만들 때 사용하도록 설정한 **InternetClient**, **Microphone** 및 **SpatialPerception** 기능이 사용하도록 설정되어 있는지 다시 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-141">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="25a05-142">그런 다음, **InternetClientServer** 및 **PrivateNetworkClientServer** 기능을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-142">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="25a05-144">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="25a05-144">Importing the tutorial assets</span></span>

<span data-ttu-id="25a05-145">다음 Unity 사용자 지정 패키지를 **나열된 순서대로** 다운로드하여 **가져옵니다**.</span><span class="sxs-lookup"><span data-stu-id="25a05-145">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="25a05-146">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage)(최신 버전)</span><span class="sxs-lookup"><span data-stu-id="25a05-146">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="25a05-147">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="25a05-147">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="25a05-148">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="25a05-148">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="25a05-149">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-149">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="25a05-150">자습서 자산을 가져오면 [프로젝트] 창이 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-150">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a><span data-ttu-id="25a05-152">장면 준비</span><span class="sxs-lookup"><span data-stu-id="25a05-152">Preparing the scene</span></span>

<span data-ttu-id="25a05-153">이 섹션에서는 자습서 프리팹을 추가하여 장면을 준비하고, 장면을 제어하는 Lunarcom 컨트롤러(스크립트) 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-153">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="25a05-154">[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** 폴더로 차례로 이동하고, **Lunarcom** 프리팹을 [계층 구조] 창으로 끌어 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-154">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="25a05-156">[계층 구조] 창에서 **Lunarcom** 개체를 선택한 채로 [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 컨트롤러(스크립트)** 구성 요소를 Lunarcom 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-156">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="25a05-158">Lunarcom 컨트롤러(스크립트) 구성 요소는 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-158">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="25a05-159">이 자습서의 자산과 함께 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-159">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="25a05-160">**Lunarcom** 개체를 선택한 상태에서 이 개체를 펼쳐 자식 개체를 표시한 다음, **Terminal** 개체를 Lunarcom 컨트롤러(스크립트) 구성 요소의 **터미널** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-160">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="25a05-162">**Lunarcom** 개체를 선택한 상태에서 Terminal 개체를 펼쳐 자식 개체를 표시한 다음, **ConnectionLight** 개체 및 **OutputText** 개체를 각각 Lunarcom 컨트롤러(스크립트) 구성 요소의 **연결 조명** 필드 및 **출력 텍스트** 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-162">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="25a05-164">**Lunarcom** 개체를 선택한 상태에서 Buttons 개체를 펼쳐 자식 개체를 표시한 다음, [검사기] 창에서 **단추** 목록을 펼치고, **크기**를 3으로 설정하고, **MicButton**, **SatelliteButton** 및 **RocketButton** 필드를 각각 **요소** 0, 1 및 2 필드로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-164">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="25a05-166">Unity 프로젝트를 Azure 리소스에 연결</span><span class="sxs-lookup"><span data-stu-id="25a05-166">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="25a05-167">Azure Speech Services를 사용하려면 Azure 리소스를 만들고, Speech Service에 대한 API 키를 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-167">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="25a05-168">[Speech Service 체험해 보기](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) 지침을 수행하고, 서비스 지역(위치라고도 함) 및 API 키(Key1 또는 Key2라고도 함)를 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-168">Follow the [Try the Speech service for free](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="25a05-169">[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **Lunarcom 컨트롤러(스크립트)** 구성 요소의 **Speech SDK 자격 증명** 섹션을 찾아서 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-169">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="25a05-170">**Speech Service API 키** 필드에서 API 키(Key1 또는 Key2)를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-170">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="25a05-171">**Speech Service 지역** 필드에서 공백 없이 소문자를 사용하여 서비스 지역(위치)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-171">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="25a05-173">음성 인식을 사용하여 음성 전사</span><span class="sxs-lookup"><span data-stu-id="25a05-173">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="25a05-174">[계층 구조] 창에서 **Lunarcom** 개체를 선택한 다음, [검사기] 창에서 **구성 요소 추가** 단추를 사용하여 **Lunarcom 음성 인식기(스크립트)** 구성 요소를 Lunarcom 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-174">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="25a05-176">Lunarcom 음성 인식기(스크립트) 구성 요소는 MRTK의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-176">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="25a05-177">이 자습서의 자산과 함께 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-177">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="25a05-178">이제 게임 모드로 들어가면 먼저 마이크 단추를 눌러 음성 인식을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-178">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="25a05-180">그런 다음, 마이크가 컴퓨터에 있다고 가정하여 사용자가 무언가를 말하면 음성이 터미널 패널에 전사됩니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-180">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> <span data-ttu-id="25a05-182">애플리케이션에서 Azure에 연결해야 하므로 컴퓨터/디바이스가 인터넷에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-182">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="25a05-183">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-183">Congratulations</span></span>

<span data-ttu-id="25a05-184">Azure에서 구동하는 음성 인식을 구현했습니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-184">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="25a05-185">디바이스에서 애플리케이션을 실행하여 기능이 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-185">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="25a05-186">다음 자습서에서는 Azure 음성 인식을 사용하여 명령을 실행하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="25a05-186">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

[<span data-ttu-id="25a05-187">다음 자습서: 2. 음성 인식을 사용하여 명령 실행</span><span class="sxs-lookup"><span data-stu-id="25a05-187">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)
