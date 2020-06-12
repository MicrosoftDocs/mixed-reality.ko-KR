---
title: Azure Spatial Anchors 자습서 - 4. Android 및 iOS용 Azure Spatial Anchors
description: 이 자습서를 완료하여 혼합 현실 애플리케이션 내에서 Azure Spatial Anchors를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: 혼합 현실, unity, 자습서, 과정, hololens, azure, spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: 78fa6a2cdd29bd424ec3016a5467760063b87a14
ms.sourcegitcommit: 7011ac6fde80e5c45f04192fa1db6e1eb559e3b0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84327944"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="8cd8e-105">4. Android 및 iOS용 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="8cd8e-105">4. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="8cd8e-106">이 자습서에서는 AR Foundation, ARCore XR 플러그 인 및 ARKit XR 플러그 인을 사용하여 Android 및 iOS 디바이스에 프로젝트를 빌드하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="8cd8e-107">목표</span><span class="sxs-lookup"><span data-stu-id="8cd8e-107">Objectives</span></span>

* <span data-ttu-id="8cd8e-108">Unity AR Foundation 및 ARCore XR 플러그 인을 사용하여 Android 디바이스에 프로젝트를 빌드하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-108">Learn how to build your project to Android device using Unity AR Foundation and ARCore XR Plugin.</span></span>
* <span data-ttu-id="8cd8e-109">Unity AR Foundation 및 ARKit XR 플러그 인을 사용하여 iOS 디바이스에 프로젝트를 빌드하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-109">Learn how to build your project to an iOS device using Unity AR Foundation and ARKit XR Plugin.</span></span>

> [!NOTE]
> <span data-ttu-id="8cd8e-110">이 자습서를 완료하려면 Azure Spatial Anchors 자습서 -> [Azure Spatial Anchors 시작](mrlearning-asa-ch1.md)을 완료했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-110">To complete this tutorial, make sure you have completed Azure Spatial Anchors Tutorials -> [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md).</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="8cd8e-111">기본 제공 Unity 패키지 추가</span><span class="sxs-lookup"><span data-stu-id="8cd8e-111">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="8cd8e-112">이 섹션에서는 Android 및 iOS 디바이스를 지원하는 데 필요한 Unity의 기본 제공 AR Foundation, ARCore XR 플러그 인 및 ARKit XR 플러그 인 패키지를 설치하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-112">In this section, you will install Unity inbuilt AR Foundation, ARCore XR Plugin, and ARKit XR Plugin packages required to support Android and iOS devices.</span></span>

<span data-ttu-id="8cd8e-113">아래 나열된 올바른 버전의 Unity 패키지를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-113">Make sure you install the correct version of these Unity packages as listed below:</span></span>

* <span data-ttu-id="8cd8e-114">**AR Foundation 2.1.4**</span><span class="sxs-lookup"><span data-stu-id="8cd8e-114">**AR Foundation 2.1.4**</span></span>
* <span data-ttu-id="8cd8e-115">**ARCore XR 플러그 인 2.2.0 preview 2**</span><span class="sxs-lookup"><span data-stu-id="8cd8e-115">**ARCore XR plugin 2.2.0 preview 2**</span></span>
* <span data-ttu-id="8cd8e-116">**ARKit XR 플러그 인 2.1.1**</span><span class="sxs-lookup"><span data-stu-id="8cd8e-116">**ARKit XR plugin 2.1.1**</span></span>

> [!NOTE]
> <span data-ttu-id="8cd8e-117">Android용으로 이 프로젝트를 개발하는 경우 ARKit XR 플러그 인 패키지를 설치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-117">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="8cd8e-118">마찬가지로 iOS용으로 이 프로젝트를 개발하는 경우 ARCore XR 플러그 인을 설치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-118">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

<span data-ttu-id="8cd8e-119">Unity 메뉴에서 **Window** > **패키지 관리자**를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-119">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

<span data-ttu-id="8cd8e-121">모든 패키지가 목록에 표시되는 데 몇 초 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-121">It might take a few seconds before all packages appear in the list.</span></span> <span data-ttu-id="8cd8e-122">고급 옵션을 클릭하고 **미리 보기 패키지 표시**를 선택하여 미리 보기 패키지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-122">Display preview packages by clicking on Advanced option and select **Show preview packages.**</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

<span data-ttu-id="8cd8e-124">패키지 관리자 창에서 **AR Foundation**을 선택합니다. 여기에서 여러 버전을 확인하고 **버전 2.1.4**를 선택하고 **2.1.4로 업데이트** 단추를 클릭하여 패키지를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-124">In the Package Manager window, select **AR Foundation**, here you see many version and need to select **version 2.1.4** and update the package by clicking the **Update to 2.1.4** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

<span data-ttu-id="8cd8e-126">Android 디바이스를 지원하려면 동일한 프로세스에 따라 **ARCore XR 플러그 인 2.2.0 미리 보기 2**를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-126">To support Android devices, follow the same process to import **ARCore XR Plugin 2.2.0 preview 2**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

<span data-ttu-id="8cd8e-128">iOS 디바이스를 지원하려면 패키지 관리자로부터 **ARKit XR 플러그 인 2.1.1** Unity 패키지를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-128">To support iOS devices, you should import the **ARKit XR plugin 2.1.1** Unity package from the Package Manager.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a><span data-ttu-id="8cd8e-130">AR Foundation 카메라를 지원하도록 MRTK 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="8cd8e-130">Customize MRTK to support AR Foundation camera</span></span>

<span data-ttu-id="8cd8e-131">계층 창에서 MixedRealityToolKit를 선택하여 AR Foundation을 지원하도록 MRTK 설정을 사용자 지정하고 검사기 창의 Mixed Reality ToolKit에서 **복제** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-131">Customize MRTK settings to support AR Foundation by selecting MixedRealityToolKit in the Hierarchy window and click the **Clone** button in Mixed Reality ToolKit in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

<span data-ttu-id="8cd8e-133">**복제** 단추를 클릭하면 새 복제 프로필 창이 표시되고 **복제** 단추를 다시 클릭하여 **DefaultMixedRealityToolkitProfile**을 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-133">When you click the **Clone** button, a new clone Profile window will appear, click on the **Clone** button again to clone the **DefaultMixedRealityToolkitProfile**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

<span data-ttu-id="8cd8e-135">마찬가지로 검사기 창에 **카메라 프로필**을 복제합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-135">Similarly, clone the **Camera Profile** in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

<span data-ttu-id="8cd8e-137">검사기 창에서 MixedReality를 찾아 **카메라** 탭을 선택합니다. 검사기 창에서 카메라 설정 공급자를 확장하고, **+ 카메라 설정 공급자 추가**를 클릭하고, **새 데이터 공급자 1**을 확장한 다음, **없음** 유형을 선택하고 **Microsoft.MixedReality.Toolkit.Experimental.UnityAR**, **UnityARCameraSettings**를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-137">In the Inspector window, locate the MixedReality, select the **Camera** tab. Expand the camera setting providers in the inspector window and click on **+ Add Camera Setting Provider** > expand **New data provider 1** > select type **None** > select **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > select **UnityARCameraSettings**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

<span data-ttu-id="8cd8e-139">계층 구조 창에서 선택한 MixedRealityToolKit 개체를 사용하여 검사기 창에서 **구성 요소 추가** 단추를 클릭하여 지원 스크립트를 첨부하고 AR 참조 지점 관리자에서 입력한 후 스크립트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-139">With the MixedRealityToolKit object selected in the Hierarchy window, In the Inspector window, attach supporting scripts by clicking on the **Add component** button and type in AR reference Point manager and select the script.</span></span>

<span data-ttu-id="8cd8e-140">**AR 참조 지점 관리자** 스크립트를 추가하면 검사기 창에 **AR 세션 원본**이 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-140">Adding the  **AR Reference Point Manager** script will automatically add **AR session origin** to the Inspector window.</span></span> <span data-ttu-id="8cd8e-141">지원 스크립트를 추가하면 검사기 창은 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-141">After adding the supporting scripts, the Inspector window should look like this.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-5.png)

## <a name="build-an-application-to-an-android-device"></a><span data-ttu-id="8cd8e-143">Android 디바이스에 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="8cd8e-143">Build an application to an Android device</span></span>

<span data-ttu-id="8cd8e-144">Android 디바이스에 이 애플리케이션을 빌드하려면 창 맨 위에 있는 **파일**을 클릭하고 **빌드 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-144">To build this application to your Android device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="8cd8e-145">화면에 새 창이 표시되면 **Android**를 선택하고 **플랫폼 전환**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-145">A new window will appear on the screen, select **Android**, and click on the **Switch Platform**.</span></span> <span data-ttu-id="8cd8e-146">플랫폼을 전환하는 데 몇 분 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-146">It will take a few minutes to switch platform.</span></span> <span data-ttu-id="8cd8e-147">Android 플랫폼으로 전환한 후 **장면 열기 추가**를 클릭하고 현재 장면이 **빌드의 장면** 목록에서 선택된 장면인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-147">After switching to the Android platform, click on **Add Open Scenes** and make sure your current scene is the only selected scene in the **Scenes In Build** list.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

<span data-ttu-id="8cd8e-149">**빌드 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-149">Close the **Build Settings** window.</span></span> <span data-ttu-id="8cd8e-150">Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > Unity 프로젝트 구성을 선택하고 **적용**을 클릭하여 Android 플랫폼용 Unity 프로젝트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-150">In the Unity menu, select Mixed Reality Toolkit > Utilities > Configure Unity Project and click on **Apply** to configure the Unity project for the Android platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

<span data-ttu-id="8cd8e-152">Unity 메뉴에서 **편집** > **프로젝트 설정...** 을 차례로 선택하여 프로젝트 설정 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-152">In the Unity menu, select **Edit** > **Project Settings** to open the Project Settings window.</span></span> <span data-ttu-id="8cd8e-153">프로젝트 설정에서 창이 **플레이어** 탭을 선택하면, **기타 설정** 섹션을 확장한 다음, **Vulkan**을 선택하고 " **-** " 기호를 클릭하여 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-153">In the Project Settings, window selects the **Player** tab, expand the **Other Settings** section, select **Vulkan**, and remove it by clicking the "**-**" symbol.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

<span data-ttu-id="8cd8e-155">**플레이어 설정** 창을 닫고 **빌드** 설정 창을 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-155">Close the **Player Settings** window and open the **Build Settings** window again.</span></span> <span data-ttu-id="8cd8e-156">그런 다음, USB 케이블을 사용하여 Android 디바이스를 컴퓨터에 연결하고, 드롭다운의 **빌드 및 실행**에서 디바이스를 선택한 후, **빌드 및 실행**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-156">Then, using a USB cable, connect your Android device to your computer and select your device in the **Build and Run** on the dropdown, then click **Build And Run**.</span></span> <span data-ttu-id="8cd8e-157">이름을 선택할 수 있는 .apk 파일을 저장하라는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-157">You will be asked to save a .apk file, which you can pick any name.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> <span data-ttu-id="8cd8e-159">Android SDK, NDK 및 JDK 모듈과 관련된 Unity 콘솔 창에 오류가 발생하면 Unity Hub를 열고 Android 빌드 지원 모듈과 관련된 SDK, NDK 및 JDK 모듈을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-159">If you get any error in the Unity Console window related to Android SDK, NDK, and or JDK modules, you need to open Unity Hub and install the associated SDK, NDK, and JDK modules for the Android Build Support module.</span></span>

<span data-ttu-id="8cd8e-160">빌드 프로세스가 완료되면 애플리케이션이 Android 디바이스에 자동으로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-160">When the build process is complete, your applications should automatically load on your Android device.</span></span>

## <a name="build-an-application-to-ios-device"></a><span data-ttu-id="8cd8e-161">iOS 디바이스에 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="8cd8e-161">Build an application to iOS Device</span></span>

<span data-ttu-id="8cd8e-162">iOS 디바이스에 이 애플리케이션을 빌드하려면 창 맨 위에 있는 **파일**을 클릭하고 **빌드 설정**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-162">To build this application to your iOS device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="8cd8e-163">화면에 새 창이 표시되면 **iOS**를 선택하고 **플랫폼 전환**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-163">A new window will appear on the screen, then select **iOS** and click on the **Switch Platform**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

<span data-ttu-id="8cd8e-165">**빌드 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-165">Close the **Build Settings** window.</span></span> <span data-ttu-id="8cd8e-166">Unity 메뉴에서 Mixed Reality Toolkit > 유틸리티 > Unity 프로젝트 구성을 선택하고 **적용**을 클릭하여 iOS 플랫폼용 Unity 프로젝트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-166">In the Unity menu, select Mixed Reality Toolkit > Utilities > Configure Unity Project, and click on **Apply** to configure the Unity project for the iOS platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

<span data-ttu-id="8cd8e-168">iOS XCode 프로젝트를 빌드하려면 빌드 설정으로 이동하여 **빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-168">To build the iOS XCode project, go to Build Settings, and click on **Build**.</span></span>

<span data-ttu-id="8cd8e-169">이 프로젝트를 iOS 디바이스에 배포하는 방법을 알아보려면 [이 가이드](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project)를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-169">Follow [this guide](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) to learn how to deploy this project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="8cd8e-170">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-170">Congratulations</span></span>

<span data-ttu-id="8cd8e-171">이 자습서에서는 Android 및 iOS 디바이스용 프로젝트를 빌드하는 방법에 대해 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-171">In this tutorial, you learned how to build your project for Android and iOS devices.</span></span> <span data-ttu-id="8cd8e-172">또한 AR Foundation, ARCore XR 플러그 인 및 ARKit XR 플러그 인을 사용하여 Android 및 iOS 디바이스에서 프로젝트를 작동하도록 하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="8cd8e-172">You also learned how to use AR Foundation, ARCore XR Plugin, and ARKit XR Plugin to make your project work for Android and iOS devices.</span></span>
