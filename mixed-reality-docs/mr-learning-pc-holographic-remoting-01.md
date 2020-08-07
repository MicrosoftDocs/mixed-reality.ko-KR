---
title: PC 홀로그램 원격 자습서 - 1. PC 홀로그램 원격 시작
description: 이 과정을 완료하여 혼합 현실 환경을 PC에서 HoloLens 2로 원격으로 사용하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/29/2020
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 4929634d70a082e835eb7bd6b5680719338a5e92
ms.sourcegitcommit: ef0bf03833eda826ed0b884859b4573775112aba
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87476975"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a><span data-ttu-id="aeddf-105">1. PC 홀로그램 원격 시작</span><span class="sxs-lookup"><span data-stu-id="aeddf-105">1. Getting started with PC Holographic Remoting</span></span>

## <a name="overview"></a><span data-ttu-id="aeddf-106">개요</span><span class="sxs-lookup"><span data-stu-id="aeddf-106">Overview</span></span>

  <span data-ttu-id="aeddf-107">HoloLens 2 자습서를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-107">Welcome to the HoloLens 2 tutorials.</span></span> <span data-ttu-id="aeddf-108">2부로 구성된 이 자습서 시리즈에서는 혼합 현실 환경 데모를 만드는 방법 및 홀로그램 원격 접속을 위한 PC 앱을 만드는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-108">In this two-part tutorial series, you will learn how to create a mixed reality experience demonstration and how to create a PC app for Holographic Remoting.</span></span>

   <span data-ttu-id="aeddf-109">[혼합 현실 환경 만들기](mr-learning-pc-holographic-remoting-01.md) 자습서에서는 혼합 현실 환경을 만드는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-109">In this tutorial, [Create mixed reality experience](mr-learning-pc-holographic-remoting-01.md), you will learn how to create a mixed reality experience.</span></span> <span data-ttu-id="aeddf-110">여기서는 UI 요소, 3D 모델 조작, 모델 클리핑 및 시선 추적 기능을 시연합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-110">It will demonstrate UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span>

  <span data-ttu-id="aeddf-111">두 번째 [홀로그램 원격 애플리케이션 만들기](mr-learning-pc-holographic-remoting-02.md) 자습서에서는 홀로그램 원격 접속을 위한 PC 앱을 만드는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-111">In the second tutorial, [Create a Holographic Remoting application](mr-learning-pc-holographic-remoting-02.md), you will learn how to create a PC app for Holographic Remoting.</span></span> <span data-ttu-id="aeddf-112">그리고 언제든지 HoloLens 2에 연결하여 혼합 현실에서 3D 콘텐츠를 시각화할 수 있는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-112">And connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="aeddf-113">목표</span><span class="sxs-lookup"><span data-stu-id="aeddf-113">Objectives</span></span>

* <span data-ttu-id="aeddf-114">자산 가져오기 및 장면 설정</span><span class="sxs-lookup"><span data-stu-id="aeddf-114">Import assets and set up the scene</span></span>
* <span data-ttu-id="aeddf-115">UI 요소 및 단추를 사용하여 홀로그램과 상호 작용</span><span class="sxs-lookup"><span data-stu-id="aeddf-115">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="aeddf-116">클리핑 기능에 대한 3D 개체 구성</span><span class="sxs-lookup"><span data-stu-id="aeddf-116">Configure 3D objects for the clipping feature</span></span>
* <span data-ttu-id="aeddf-117">시선 추적을 사용하여 도구 설명을 활성화하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="aeddf-117">Learn about activating tooltips with eye-tracking</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aeddf-118">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="aeddf-118">Prerequisites</span></span>

* <span data-ttu-id="aeddf-119">올바른 [도구가 설치](install-the-tools.md)된 상태로 구성된 Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="aeddf-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="aeddf-120">기본적인 C# 프로그래밍 지식</span><span class="sxs-lookup"><span data-stu-id="aeddf-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="aeddf-121">[개발용으로 구성](using-visual-studio.md#enabling-developer-mode)된 HoloLens 2 디바이스</span><span class="sxs-lookup"><span data-stu-id="aeddf-121">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="aeddf-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>(Unity 2019.3.X가 탑재되고 유니버설 Windows 플랫폼 빌드 지원 모듈이 추가됨)</span><span class="sxs-lookup"><span data-stu-id="aeddf-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.X mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="aeddf-123">계속하기 전에 [시작](mr-learning-base-01.md) 자습서 시리즈 또는 Unity 및 MRTK에 대한 기본적인 사전 경험을 완료할 것을 **강력히 권장**합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="aeddf-124">이 자습서 시리즈에 추천되는 Unity 버전은 Unity 2019.3.X입니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-124">The recommended Unity version for this tutorial series is Unity 2019.3.X.</span></span> <span data-ttu-id="aeddf-125">이는 위에서 연결된 필수 구성 요소에서 설명하는 모든 Unity 버전 요구 사항 또는 추천 사항을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>
> * <span data-ttu-id="aeddf-126">MRTK 프로젝트를 사용한 홀로그램 원격 접속은 레거시 XR에서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-126">Holographic Remoting with MRTK projects will only work with legacy XR.</span></span> <span data-ttu-id="aeddf-127">지금은 XR SDK가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-127">XR SDK is not supported at this time.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="aeddf-128">Unity 프로젝트 만들기 및 준비</span><span class="sxs-lookup"><span data-stu-id="aeddf-128">Creating and preparing the Unity project</span></span>

<span data-ttu-id="aeddf-129">이 섹션에서는 새 Unity 프로젝트를 만들고 MRTK 개발을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-129">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="aeddf-130">이를 위해 먼저 [프로젝트 및 첫 번째 애플리케이션 초기화](mr-learning-base-02.md)를 수행합니다. 단, [디바이스에 애플리케이션 빌드](mr-learning-base-02.md#building-your-application-to-your-hololens-2) 지침은 제외합니다. 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-130">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="aeddf-131">[새 Unity 프로젝트 만들기](mr-learning-base-02.md#creating-the-unity-project) 및 적절한 이름 지정(예: *MRTK Tutorials*)</span><span class="sxs-lookup"><span data-stu-id="aeddf-131">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="aeddf-132">빌드 플랫폼 전환</span><span class="sxs-lookup"><span data-stu-id="aeddf-132">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="aeddf-133">TextMeshPro 필수 리소스 가져오기</span><span class="sxs-lookup"><span data-stu-id="aeddf-133">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="aeddf-134">Mixed Reality Toolkit 가져오기</span><span class="sxs-lookup"><span data-stu-id="aeddf-134">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="aeddf-135">Unity 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="aeddf-135">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="aeddf-136">[장면 만들기 및 설정](mr-learning-base-02.md#creating-and-configuring-the-scene) 및 장면에 적절한 이름 지정(예: **PC Holographic Remoting**)</span><span class="sxs-lookup"><span data-stu-id="aeddf-136">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, **PC Holographic Remoting**</span></span>

<span data-ttu-id="aeddf-137">그런 다음, [공간 인식 표시 옵션 변경](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) 지침에 따라 장면의 MRTK 구성 프로필을 **DefaultHoloLens2ConfigurationProfile**로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-137">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile**.</span></span> <span data-ttu-id="aeddf-138">공간 인식 메시의 표시 옵션을 **폐색**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-138">Change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="aeddf-139">자습서 자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="aeddf-139">Importing the tutorial assets</span></span>

<span data-ttu-id="aeddf-140">[MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage)를 다운로드하고 **가져옵니다**.</span><span class="sxs-lookup"><span data-stu-id="aeddf-140">Download and **import** the [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/onginnovations/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).</span></span>

>[!TIP]
> <span data-ttu-id="aeddf-141">Unity 사용자 지정 패키지를 가져오는 방법을 미리 알아보려면 [Mixed Reality Toolkit 가져오기](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-141">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="aeddf-142">자습서 자산을 가져오면 [프로젝트] 창이 다음과 비슷하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-142">After importing the tutorial assets, your Project window should look similar to this:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a><span data-ttu-id="aeddf-144">장면 구성 및 준비</span><span class="sxs-lookup"><span data-stu-id="aeddf-144">Configuring and preparing the scene</span></span>

<span data-ttu-id="aeddf-145">이 섹션에서는 자습서 프리팹 중 일부를 추가하여 장면을 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-145">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="aeddf-146">[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** 폴더로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-146">In the Project window, navigate to **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder.</span></span> <span data-ttu-id="aeddf-147">Ctrl 단추를 누른 채 아래 6개의 프리팹을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-147">While holding down the CTRL button, click on the below six prefabs.</span></span>

* <span data-ttu-id="aeddf-148">ButtonParent</span><span class="sxs-lookup"><span data-stu-id="aeddf-148">ButtonParent</span></span>
* <span data-ttu-id="aeddf-149">ClippingObjects</span><span class="sxs-lookup"><span data-stu-id="aeddf-149">ClippingObjects</span></span>
* <span data-ttu-id="aeddf-150">HandSpatialMapButton</span><span class="sxs-lookup"><span data-stu-id="aeddf-150">HandSpatialMapButton</span></span>
* <span data-ttu-id="aeddf-151">지침</span><span class="sxs-lookup"><span data-stu-id="aeddf-151">Instructions</span></span>
* <span data-ttu-id="aeddf-152">ModelParent</span><span class="sxs-lookup"><span data-stu-id="aeddf-152">ModelParent</span></span>
* <span data-ttu-id="aeddf-153">플랫폼</span><span class="sxs-lookup"><span data-stu-id="aeddf-153">Platform</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

<span data-ttu-id="aeddf-155">이러한 모델을 prefabs 폴더에서 **계층 구조 창**으로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-155">Drag-and-drop these models from the prefabs folder into the **Hierarchy window**.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

<span data-ttu-id="aeddf-157">장면의 개체에 초점을 맞추기 위해 **ModelParent** 개체를 두 번 클릭한 다음, 약간씩 다시 확대할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-157">To focus in on the objects in the scene, you can double-click on the **ModelParent** object, and then zoom slightly in again:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> <span data-ttu-id="aeddf-159">장면에서 큰 아이콘(예: 틀이 있는 매력적인 큰 'T' 아이콘)이 표시되는 경우 <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">Gizmo를 끄기 위치로 전환</a>하여 이러한 아이콘을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-159">If you find the large icons in your scene, such as, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="aeddf-160">장면을 작동하도록 단추 구성</span><span class="sxs-lookup"><span data-stu-id="aeddf-160">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="aeddf-161">이 섹션에서는 스크립트를 장면에 추가하여 모델 전환 및 클리핑 기능의 기본 사항을 시연하는 단추 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-161">In this section, you will add scripts into the scene to create button events demonstrating the fundamentals of model switching and clipping functionality.</span></span>

### <a name="1-configuring-the-interactable-script-component"></a><span data-ttu-id="aeddf-162">1. Interactable(스크립트) 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="aeddf-162">1. Configuring the Interactable (Script) component</span></span>

<span data-ttu-id="aeddf-163">[계층 구조] 창에서 **ButtonParent** 개체를 펼치고 **NextButton**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-163">In the Hierarchy window, expand the **ButtonParent** object and select the **NextButton**.</span></span> <span data-ttu-id="aeddf-164">[검사기] 창에서 **Interactable(스크립트)** 구성 요소를 찾고, **OnClick ()** 이벤트 아래에서 **+** 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-164">In the Inspector window, locate the **Interactable (Script)** component and click on **+** icon under **OnClick ()** event.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

<span data-ttu-id="aeddf-166">[계층 구조] 창에서 **NextButton** 개체를 선택한 상태에서 [계층 구조] 창의 **ButtonParent** 개체를 클릭하여 방금 추가한 이벤트의 비어 있는 **없음(개체)** 필드로 끌어서 ButtonParent 개체에서 이 단추의 단추 클릭 이벤트를 수신 대기하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-166">With the **NextButton** object still selected in the Hierarchy window, click-and-drag the **ButtonParent** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

<span data-ttu-id="aeddf-168">동일한 이벤트의 **함수 없음** 드롭다운을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-168">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="aeddf-169">그런 다음, **ViewButtonControl** > **NextModel ()** 을 차례로 선택하여 **NextModel ()** 함수를 이 단추의 단추 누름 이벤트가 발생할 때 트리거되는 작업으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-169">Then select **ViewButtonControl** > **NextModel ()** to set the **NextModel ()** function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a><span data-ttu-id="aeddf-171">2. 나머지 단추 구성</span><span class="sxs-lookup"><span data-stu-id="aeddf-171">2. Configuring the remaining buttons</span></span>

<span data-ttu-id="aeddf-172">나머지 각 단추에 대해 위에서 설명하는 프로세스를 완료하여 함수를 **OnClick ()** 이벤트에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-172">For each of the remaining buttons, complete the process outlined above to assign functions to the **OnClick ()** events:</span></span>

* <span data-ttu-id="aeddf-173">PreviousButton 개체에 대해 **ViewButtonControl** > **PreviousModel ()** 함수를 차례로 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-173">For PreviousButton object, assign the **ViewButtonContro**l > **PreviousModel ()** function.</span></span>

* <span data-ttu-id="aeddf-174">ClippingButton에 대해 **ToggleButton** > **ToggleClipping ()** 함수를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-174">For ClippingButton select **ToggleButton** > **ToggleClipping ()** function.</span></span>

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a><span data-ttu-id="aeddf-175">3. 보기 단추 컨트롤(스크립트) 및 토글 단추(스크립트) 구성 요소 구성</span><span class="sxs-lookup"><span data-stu-id="aeddf-175">3. Configuring the View Button Control (Script)  and Toggle Button (Script) components</span></span>

<span data-ttu-id="aeddf-176">이제 단추는 모델 전환 및 클리핑 기능을 시연하도록 구성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-176">Now your buttons are configured to demonstrate the model switching and clipping functionality.</span></span> <span data-ttu-id="aeddf-177">이번에는 3D 모델 및 클리핑 개체를 스크립트에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-177">It is time to add 3D models and the clipping objects to the script.</span></span>

<span data-ttu-id="aeddf-178">시연을 위해 6가지 3D 모델이 제공되었습니다. ***ModelParentobject***를 펼쳐서 이러한 3D 모델을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-178">We have provided six different 3D models for demonstration, expand the ***ModelParentobject*** to expose these 3D models.</span></span>

<span data-ttu-id="aeddf-179">[계층 구조] 창에서 ButtonParent 개체를 여전히 선택한 상태에서 [검사기] 창에서 **보기 단추 컨트롤(스크립트)** 구성 요소를 찾아서 **모델** 변수를 펼칩니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-179">With the ButtonParent object still selected in the Hierarchy window, in the Inspector window, locate the **View Button Control (Script)** component and expand the **Models** variable.</span></span>

<span data-ttu-id="aeddf-180">**크기** 필드에서 장면에 포함하려는 3D 모델의 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-180">In the **Size** field, enter the number of 3D models you would like to have in your scene.</span></span> <span data-ttu-id="aeddf-181">여기서는 6입니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-181">In this case, it would be six.</span></span> <span data-ttu-id="aeddf-182">새 3D 모델을 추가하기 위한 필드가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-182">It will create fields for adding new 3D models.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

<span data-ttu-id="aeddf-184">ModelParent 개체의 각 자식 개체를 이러한 필드로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-184">Drag and drop each child object of ModelParent Object into these fields.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

<span data-ttu-id="aeddf-186">**ClippingObjects** 개체를 [계층 구조] 창에서 **토글 단추(스크립트)** 구성 요소의 **클리핑 개체** 필드로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-186">Drag and drop the  **ClippingObjects** object from the Hierarchy window to the  **Toggle Button (Script)** component **Clipping Object** field.</span></span>
>[!NOTE]
><span data-ttu-id="aeddf-187">단추 부모 개체에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-187">Stay in button parent object only.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

<span data-ttu-id="aeddf-189">[계층 구조] 창에서 **ClippingObjects** 프리팹을 선택하고, [검사기] 창에서 이를 사용하도록 설정하여 클리핑 개체를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-189">In the Hierarchy window, select the **ClippingObjects** prefab and enable it in the Inspector window to turn on the Clipping objects.</span></span>

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a><span data-ttu-id="aeddf-190">클리핑 기능을 사용하도록 클리핑 개체 구성</span><span class="sxs-lookup"><span data-stu-id="aeddf-190">Configuring the clipping objects to enable clipping feature</span></span>

<span data-ttu-id="aeddf-191">이 섹션에서는 MarsCuriosityRover 개체의 자식 개체 렌더러를 개별 클리핑 개체에 추가하여 MarsCuriosityRover 모델의 클리핑을 시연합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-191">In this section, you will add MarsCuriosityRover object's child objects renderer into an individual clipping object to demonstrate the clipping of the MarsCuriosityRover model.</span></span>

<span data-ttu-id="aeddf-192">[계층 구조] 창에서 **ClippingObjects** 개체를 펼쳐서 이 프로젝트에서 사용할 서로 다른 세 가지 클리핑 개체를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-192">In the Hierarchy window, expand the **ClippingObjects** object to expose the three different clipping objects that you will be using in this project.</span></span>

<span data-ttu-id="aeddf-193">**ClippingSphere** 개체를 구성하려면 해당 개체를 클릭하고, [검사기] 창에서 **클리핑 구(스크립트)** 구성 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-193">To configure the **ClippingSphere** object, click on it, and in the Inspector window, locate the **Clipping Sphere (Script)** component.</span></span> <span data-ttu-id="aeddf-194">크기 필드에서 3D 모델에 추가해야 하는 렌더러의 수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-194">Enter the number of renderers in the size field that you need to add for your 3D model.</span></span> <span data-ttu-id="aeddf-195">여기서는 MarsCuriosityRover 자식 개체에 대해 10을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-195">In this case, add 10 for MarsCuriosityRover child objects.</span></span> <span data-ttu-id="aeddf-196">렌더러를 추가하기 위한 필드를 만들고, MarsCuriosityRover 개체의 자식 모델 개체를 이러한 필드로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-196">It will create fields for adding renderers, drag and drop MarsCuriosityRover Object's child model objects into these fields.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

<span data-ttu-id="aeddf-198">동일한 프로세스를 수행하고, MarsCuriosityRover의 자식 개체 렌더러를 **ClippingBox** 및 **ClippingPlane** 개체에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-198">Follow the same process and add MarsCuriosityRover's child objects renderers to the **ClippingBox** and **ClippingPlane** objects.</span></span>

<span data-ttu-id="aeddf-199">이 자습서에서는 클리핑 기능을 시연하는 데 MarsCuriosityRover 모델만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-199">In this tutorial, only the MarsCuriosityRover model will be used for demonstrating the clipping feature.</span></span> <span data-ttu-id="aeddf-200">클리핑 기능을 더 많은 모델에 추가하고, 렌더러의 크기를 늘리며, 개별 메시 렌더러를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-200">They were adding clipping features to more models, increasing the size of the renderer, and adding their individual mesh renderers.</span></span>

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a><span data-ttu-id="aeddf-201">도구 설명을 강조 표시하도록 시선 추적 구성</span><span class="sxs-lookup"><span data-stu-id="aeddf-201">Configuring eye-tracking to highlight tooltips</span></span>

<span data-ttu-id="aeddf-202">이 섹션에서는 프로젝트에서 시선 추적을 사용하도록 설정하는 방법을 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-202">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="aeddf-203">예를 들어 MarsCuriosityRover 부품에 연결된 도구 설명을 강조 표시하는 기능을 구현하면서 이를 살펴보고, 해당 부품에서 시선을 거둘 때 이를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-203">For example, you will implement the functionality to highlight tooltips attached to MarsCuriosityRover's parts while looking at them and hiding them, while you are looking away from them.</span></span>

### <a name="1-identify-target-objects-and-associated-tooltips"></a><span data-ttu-id="aeddf-204">1. 대상 개체 및 연결된 도구 설명 식별</span><span class="sxs-lookup"><span data-stu-id="aeddf-204">1. Identify target objects and associated tooltips</span></span>

<span data-ttu-id="aeddf-205">[계층 구조] 창에서 ModelParent 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-205">In the Hierarchy window, select the ModelParent object.</span></span> <span data-ttu-id="aeddf-206">***MarsCuriosity -> Rover***를 차례로 펼쳐서 MarsCuriosityRover의 5개 주요 부품 (**POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**)을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-206">Expand the ***MarsCuriosity -> Rover*** to find five main parts of the MarsCuriosityRover: **POI-Camera**, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span></span>

* <span data-ttu-id="aeddf-207">[계층 구조] 창에서 MarsCuriosityRover 부품과 연결된 5개의 해당 도구 설명 개체를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-207">Observe five corresponding tooltip objects associated with MarsCuriosityRover parts in the Hierarchy window.</span></span>
* <span data-ttu-id="aeddf-208">MarsCuriosityRover 부품을 살펴볼 때 환경을 강조 표시하도록 이러한 개체를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-208">You will be configuring these objects to highlight the experience when you look at the MarsCuriosityRover parts.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a><span data-ttu-id="aeddf-210">2. While Looking At Target () 및 On Look Away () 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="aeddf-210">2. Implement While Looking At Target ()  &  On Look Away () events</span></span>

<span data-ttu-id="aeddf-211">[계층 구조] 창에서 ***POI-Camera*** 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-211">In the Hierarchy window, select the ***POI-Camera*** object.</span></span> <span data-ttu-id="aeddf-212">[검사기] 창에서 **시선 추적 대상(스크립트)** 구성 요소를 찾고 **While Looking At Target ()**  & **On Look Away ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-212">In the Inspector window, locate the **Eye Tracking Target (Script)** component and configure the **While Looking At Target ()** & **On Look Away ()** events as follows:</span></span>

* <span data-ttu-id="aeddf-213">**POI-Camera 도구 설명** 개체를 **없음(개체)** 필드에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-213">To **None (Object)** field, assign the **POI-Camera ToolTip** object</span></span>
* <span data-ttu-id="aeddf-214">**While Looking At Target ()** 이벤트의 **함수 없음** 드롭다운에서 **GameObject** > **SetActive(부울)** 를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-214">From **No Function** dropdown of **While Looking At Target ()** event, select **GameObject** > **SetActive (bool).**</span></span> <span data-ttu-id="aeddf-215">대상 개체를 볼 때 트리거되는 작업으로 도구 설명을 강조 표시하려면 아래쪽에 있는 **확인란**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-215">Select the **Checkbox** under it to highlight the tooltip as the action that is triggered when you look at the target object.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* <span data-ttu-id="aeddf-217">동일한 프로세스를 수행하고, **On Look Away ()** 이벤트 수신기의 **함수 없음** 드롭다운을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-217">Follow the same process and click on the **No Function** dropdown of the **On Look Away ()** event listener.</span></span> <span data-ttu-id="aeddf-218">그런 다음, **GameObject** > **SetActive(부울)** 를 차례로 선택하고, 대상 개체에서 시선을 거둘 때 트리거되는 작업으로 도구 설명을 숨기려면 **확인란**을 비워 둡니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-218">Then select **GameObject** > **SetActive (bool**) and leave the **Checkbox** empty to hide the tooltip as the action that is triggered when you look away from the target object.</span></span>

![mrlearning-pc-holographic-remoting](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

<span data-ttu-id="aeddf-220">동일한 프로세스를 수행하고, 각 도구 설명 개체를 동일한 **MarsCuriosityRover** 부품의 **While Looking At Target ()**  & **On Look Away ()** 이벤트에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-220">Follow the same process and assign respective tooltip objects to their same **MarsCuriosityRover** parts **While Looking At Target ()** & **On Look Away ()** events.</span></span>

<span data-ttu-id="aeddf-221">시선 추적을 사용하도록 설정하려면 이러한 [지침](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations)을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="aeddf-221">To enable eye tracking, please follow these [guidelines](https://docs.microsoft.com/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span></span>

## <a name="congratulations"></a><span data-ttu-id="aeddf-222">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-222">Congratulations</span></span>

<span data-ttu-id="aeddf-223">이 자습서에서는 UI 요소, 3D 모델 조작, 모델 클리핑 및 시선 추적 기능을 시연하는 혼합 현실 환경을 빌드하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-223">In this tutorial, you learned to build a mixed reality experience demonstrating UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span> <span data-ttu-id="aeddf-224">이 자습서에서는 3D 모델 뷰어 환경을 검색할 수 있도록 하는 NextButton 및 PreviousButton을 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-224">The tutorial provided you with NextButton and PreviousButton that let you explore the 3D model viewer experience.</span></span> <span data-ttu-id="aeddf-225">ClippingObjectButton을 사용하여 클리핑 개체를 설정하고 클리핑 기능을 경험해 보았습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-225">The ClippingObjectButton made you turn on clipping objects and experience clipping feature.</span></span> <span data-ttu-id="aeddf-226">또한 이 자습서에서는 환경에서 도구 설명을 강조 표시하도록 설정하는 시선 추적 요소를 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-226">The tutorial also provided you with an eye-tracking element to enable highlighting the tooltips in the experience.</span></span>

<span data-ttu-id="aeddf-227">다음 단원에서는 언제든지 PC에서 HoloLens 2를 연결할 수 있는 홀로그램 원격 애플리케이션을 만들고 혼합 현실에서 3D 콘텐츠를 시각화하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="aeddf-227">In the next lesson, you will learn how to create a Holographic Remoting application for PC to connect HoloLens 2 at any point, providing a way to Visualize 3D content in mixed reality.</span></span>

[<span data-ttu-id="aeddf-228">다음 단원: 2. 홀로그램 원격 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="aeddf-228">Next Lesson: 2. Create Holographic Remoting application</span></span>](mr-learning-pc-holographic-remoting-02.md)
