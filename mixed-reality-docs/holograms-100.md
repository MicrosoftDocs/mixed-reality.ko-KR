---
title: MR 기본 사항 100-Unity를 사용 하 여 시작
description: 첫 번째 기본 혼합된 현실 "hello world" 응용 프로그램을 만드는 방법에 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality 실제로 혼합 HoloLens, 몰입 형, vr, mr, 시작, 홀로그램 academy, 자습서
ms.openlocfilehash: fd3bed955e80ec18b7be500adbdb0fcb7062d129
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993616"
---
>[!NOTE]
><span data-ttu-id="236d0-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="236d0-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="236d0-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="236d0-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="236d0-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="236d0-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="236d0-110">MR 100의 기초: Unity를 사용 하 여 시작</span><span class="sxs-lookup"><span data-stu-id="236d0-110">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="236d0-111">이 자습서 Unity를 사용 하 여 빌드한 기본 혼합된 현실 앱을 만드는 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-111">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="236d0-112">장치 지원</span><span class="sxs-lookup"><span data-stu-id="236d0-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="236d0-113">과정</span><span class="sxs-lookup"><span data-stu-id="236d0-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="236d0-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="236d0-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="236d0-115"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="236d0-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="236d0-116">MR 100의 기초: Unity를 사용 하 여 시작</span><span class="sxs-lookup"><span data-stu-id="236d0-116">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="236d0-117">✔️</span><span class="sxs-lookup"><span data-stu-id="236d0-117">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="236d0-118">✔️</span><span class="sxs-lookup"><span data-stu-id="236d0-118">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="236d0-119">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="236d0-119">Prerequisites</span></span>

* <span data-ttu-id="236d0-120">올바른를 사용 하 여 구성 하는 Windows 10 PC [도구가 설치 되어](install-the-tools.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="236d0-121">장 1-새 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="236d0-121">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="236d0-122">Unity 사용 하 여 앱을 빌드하려면 먼저 프로젝트를 만들려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-122">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="236d0-123">이 프로젝트는 가장 중요 한 자산 폴더에는 몇 가지 폴더로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-123">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="236d0-124">Maya, 최대 시네마 4d 또는 Photoshop, Visual Studio 또는 즐겨 찾는 코드 편집기를 사용 하 여 만든 모든 코드와 같은 디지털 콘텐츠 작성 도구에서 가져와야 하는 모든 자산을 보유 하는 폴더 이며 Unity 때 만들어지는 콘텐츠 파일을 개수에 관계 없이 백그라운드에서 작성 애니메이션 및 편집기에서 다른 Unity 자산 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-124">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="236d0-125">Unity를 빌드 및 UWP 앱을 배포 하려면 모든 필요한 자산 및 코드 파일에 포함 될 Visual Studio 솔루션으로 프로젝트를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-125">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="236d0-126">Unity를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-126">Start Unity</span></span>
2. <span data-ttu-id="236d0-127">선택 **새**</span><span class="sxs-lookup"><span data-stu-id="236d0-127">Select **New**</span></span>
3. <span data-ttu-id="236d0-128">프로젝트 이름 (예: 입력 "MixedRealityIntroduction")</span><span class="sxs-lookup"><span data-stu-id="236d0-128">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="236d0-129">프로젝트를 저장할 위치를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-129">Enter a location to save your project</span></span>
5. <span data-ttu-id="236d0-130">확인 합니다 **3D** 토글 선택</span><span class="sxs-lookup"><span data-stu-id="236d0-130">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="236d0-131">선택 **프로젝트 만들기**</span><span class="sxs-lookup"><span data-stu-id="236d0-131">Select **Create project**</span></span>

<span data-ttu-id="236d0-132">축에 이제 혼합된 현실 사용자 지정을 사용 하 여 시작 하려면 모든 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-132">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="236d0-133">2 장-카메라 설정</span><span class="sxs-lookup"><span data-stu-id="236d0-133">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="236d0-134">Unity 주 카메라 헤드 추적 및 stereoscopic 렌더링을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-134">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="236d0-135">혼합된 현실 함께 사용 하 여 주 카메라를 확인 하려면 몇 가지 변경 내용이.입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-135">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>
1. <span data-ttu-id="236d0-136">파일 선택 > 새 장면</span><span class="sxs-lookup"><span data-stu-id="236d0-136">Select File > New Scene</span></span>

<span data-ttu-id="236d0-137">첫째,이 더 쉽게 레이아웃 지정 앱으로 사용자의 시작 위치를 가정해 보겠습니다 (**X**: 0, **Y**: 0, **Z**: 0).</span><span class="sxs-lookup"><span data-stu-id="236d0-137">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="236d0-138">주 카메라 사용자의 헤드의 움직임 추적, 이후 주 카메라의 시작 위치를 설정 하 여 사용자의 시작 위치를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-138">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>
1. <span data-ttu-id="236d0-139">선택 **주 카메라** 에 **계층** 패널</span><span class="sxs-lookup"><span data-stu-id="236d0-139">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="236d0-140">에 **검사기** 패널에서 찾을 합니다 **변환** 구성 요소 및 변경 합니다 **위치** 에서 (**X**: 0, **Y**: 1 **Z**:-10)를 (**X**: 0 **Y**: 0, **Z**: 0)</span><span class="sxs-lookup"><span data-stu-id="236d0-140">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="236d0-141">둘째, 기본 카메라 배경을 약간의 고려를 해야합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-141">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="236d0-142">**HoloLens 응용 프로그램에 대 한**, 카메라 모든 개체의 뒤에 실제 표시 되어야 하지 Skybox 텍스처를 렌더링 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-142">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>
1. <span data-ttu-id="236d0-143">사용 하 여는 **주 카메라** 선택 계속을 **계층** 패널에서 찾을 **카메라** 구성 요소를 **검사기** 패널 및 변경 합니다 **플래그 지우기** 드롭다운 **Skybox** 하 **단색**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-143">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="236d0-144">선택 된 **백그라운드** 색 선택기 및 변경 합니다 **RGBA** 값 (0, 0, 0, 0)을</span><span class="sxs-lookup"><span data-stu-id="236d0-144">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="236d0-145">**몰입 형 헤드셋을 대상으로 하는 혼합된 현실 응용 프로그램에 대 한**, Unity가 제공 하는 기본 Skybox 질감을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-145">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>
1. <span data-ttu-id="236d0-146">사용 하 여는 **주 카메라** 선택 계속 합니다 **계층** 패널에서 찾을 **카메라** 구성 요소를 **검사기** 패널 및 유지를 **플래그 지우기** 드롭다운에서 **Skybox**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-146">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="236d0-147">셋째, 보겠습니다 Unity의 가까운 클립 면과 고려 있으며 못하도록 개체 렌더링 너무 가깝게 사용자에 게 눈 사용자 개체에 도달 하거나 개체를 사용자에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-147">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="236d0-148">**HoloLens 응용 프로그램에 대 한**, 가까운 클립 면과 카메라를 설정할 수 있는 합니다 [권장 HoloLens](camera-in-unity.md#clip-planes) 0.85 미터입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-148">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>
1. <span data-ttu-id="236d0-149">사용 하 여는 **주 카메라** 선택 계속을 **계층** 패널에서 찾을 **카메라** 구성 요소를 **검사기** 패널 및 변경 합니다 **가까운 클립 면과 카메라** 기본값과에서 필드 **0.3** 권장 HoloLens에 **0.85**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-149">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="236d0-150">**몰입 형 헤드셋을 대상으로 하는 혼합된 현실 응용 프로그램에 대 한**, Unity가 제공 하는 기본 설정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-150">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>
1. <span data-ttu-id="236d0-151">사용 하 여는 **주 카메라** 선택 계속 합니다 **계층** 패널에서 찾을 **카메라** 구성 요소를 **검사기** 패널 및 유지를 **가까운 클립 면과 카메라** 기본 필드 **0.3**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-151">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="236d0-152">마지막으로 진행 상황을 지금 저장 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-152">Finally, let us save our progress so far.</span></span> <span data-ttu-id="236d0-153">장면 변경 내용을 저장 하려면 선택 **파일 > 다른 이름으로 장면 저장**, 장면 이름을 **Main**를 선택 하 고 **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-153">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="236d0-154">3 장-설치 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="236d0-154">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="236d0-155">이 챕터에 설정 데 도움이 되는 일부 Unity 프로젝트 설정은 Windows Holographic SDK 개발에 대 한 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-155">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="236d0-156">또한 일부 품질 설정을 응용 프로그램에 대 한 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-156">We will also set some quality settings for our application.</span></span> <span data-ttu-id="236d0-157">마지막으로, Windows 스토어에는 빌드 대상 설정이 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-157">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="236d0-158">Unity 성능 및 품질 설정</span><span class="sxs-lookup"><span data-stu-id="236d0-158">Unity performance and quality settings</span></span>

<span data-ttu-id="236d0-159">**HoloLens에 대 한 unity 품질 설정**</span><span class="sxs-lookup"><span data-stu-id="236d0-159">**Unity quality settings for HoloLens**</span></span>

![HoloLens에 대 한 unity 품질 설정](images/qualitysettings.png) 

<span data-ttu-id="236d0-161">HoloLens에 높은 프레임 속도 유지 관리 하므로 중요 한 이므로 가장 빠른 성능을 위해 조정 품질 설정 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-161">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="236d0-162">성능 정보를 자세한 [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-162">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>
1. <span data-ttu-id="236d0-163">선택 **편집 > 프로젝트 설정 > 품질**</span><span class="sxs-lookup"><span data-stu-id="236d0-163">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="236d0-164">선택 합니다 **드롭다운** 아래를 **Windows 스토어** 로고 및 선택 **매우 낮음**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-164">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="236d0-165">설정을 때 적용 되 올바르게 알 수 있습니다 Windows Store 열에 있는 상자 및 **매우 낮음** 행은 녹색입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-165">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="236d0-166">**폐색 표시를 대상으로 하는 혼합된 현실 응용 프로그램에 대 한**, 품질 설정을 기본값으로 두면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-166">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="236d0-167">대상 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="236d0-167">Target Windows 10 SDK</span></span>

<span data-ttu-id="236d0-168">**대상 Windows Holographic SDK**</span><span class="sxs-lookup"><span data-stu-id="236d0-168">**Target Windows Holographic SDK**</span></span>

![대상 Windows Holographic SDK](images/xrsettings.png) 

<span data-ttu-id="236d0-170">Unity 내보내기 하려는 앱을 만들어야 알 수 있도록 해야는 [몰입 형 뷰](app-views.md) 2D 보기 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-170">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="236d0-171">이 작업을 수행 Unity에서 가상 현실 지원을 사용 하도록 설정 하 여 Windows 10 SDK를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-171">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>
1. <span data-ttu-id="236d0-172">로 이동 **편집 > 프로젝트 설정 > 플레이어**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-172">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="236d0-173">에 **검사기 패널** 플레이어 설정에 대 한 선택 합니다 **Windows 스토어** 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-173">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="236d0-174">확장 된 **xr 하이 설정을** 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-174">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="236d0-175">에 **렌더링** 섹션을 **가상 현실 지원** 새 추가 하려면이 확인란을 **가상 현실 Sdk** 목록.</span><span class="sxs-lookup"><span data-stu-id="236d0-175">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="236d0-176">확인 **Windows Mixed Reality** 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-176">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="236d0-177">그렇지 않은 경우 선택 합니다 **+** 목록의 맨 아래에 있는 단추를 선택 **Windows Mixed Reality**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-177">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="236d0-178">표시 되지 않으면 합니다 **Windows 스토어** 아이콘을 Windows 스토어.NET 스크립팅 백 엔드를 설치 하기 전에 선택한 있는지 다시 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-178">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="236d0-179">그렇지 않은 경우 적절 한 Windows 설치를 사용 하 여 Unity를 다시 설치 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-179">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="236d0-180">**.NET 구성 확인**</span><span class="sxs-lookup"><span data-stu-id="236d0-180">**Verify .NET Configuration**</span></span>

![.NET 구성 확인](images/configoptions-375px.png)

1. <span data-ttu-id="236d0-182">로 이동 **편집 > 프로젝트 설정 > 플레이어** (될 수 있습니다이 이전 단계에서).</span><span class="sxs-lookup"><span data-stu-id="236d0-182">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="236d0-183">에 **검사기 패널** 플레이어 설정에 대 한 선택 합니다 **Windows 스토어** 아이콘입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-183">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="236d0-184">에 **기타 설정** 구성 섹션, 했는지 **스크립팅 백 엔드** 로 설정 된 **.NET**</span><span class="sxs-lookup"><span data-stu-id="236d0-184">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="236d0-185">적용 되는 모든 프로젝트 설정을 가져오는의 멋진 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-185">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="236d0-186">다음으로, 추가 홀로그램 주세요!</span><span class="sxs-lookup"><span data-stu-id="236d0-186">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="236d0-187">4-장을 큐브 만들기</span><span class="sxs-lookup"><span data-stu-id="236d0-187">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="236d0-188">Unity 프로젝트에서 큐브를 만드는 Unity에서 다른 개체를 만들 때 처럼 됩니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-188">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="236d0-189">큐브는 사용자 앞에 배치 하면 Unity의 좌표 시스템을 실제-Unity의 1 미터 인 실제 환경에서 약 1 미터에 매핑되므로 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-189">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>
1. <span data-ttu-id="236d0-190">왼쪽된 위 모퉁이에 **계층** 패널에서 합니다 **만들기** 드롭다운 선택 **3D 개체 > 큐브**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-190">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="236d0-191">새로 만든 선택 **큐브** 에 **계층** 패널</span><span class="sxs-lookup"><span data-stu-id="236d0-191">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="236d0-192">에 **검사기** 찾을 합니다 **변환** 구성 요소 및 변경 **위치** 에 (**X**: 0, **Y**: 0, **Z**: 2).</span><span class="sxs-lookup"><span data-stu-id="236d0-192">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="236d0-193">*이 배치 큐브 2m 사용자의 시작 위치 앞에 합니다.*</span><span class="sxs-lookup"><span data-stu-id="236d0-193">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="236d0-194">에 **변환** 구성 요소 변경 **회전** 에 (**X**: 45, **Y**: 45, **Z**: 45) 및 변경 **크기 조정** 를 (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span><span class="sxs-lookup"><span data-stu-id="236d0-194">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="236d0-195">*0.25 미터제로 바뀌는 큐브 크기를 조정 합니다.*</span><span class="sxs-lookup"><span data-stu-id="236d0-195">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="236d0-196">장면 변경 내용을 저장 하려면 선택 **파일 > 저장 장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-196">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="236d0-197">Unity 편집기에서 장치의-5 장 확인</span><span class="sxs-lookup"><span data-stu-id="236d0-197">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="236d0-198">이제 큐브를 만든 장치에서 빠른 검사를 수행 하는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-198">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="236d0-199">Unity 편집기 내에서 직접이 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-199">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="236d0-200">초기 설치</span><span class="sxs-lookup"><span data-stu-id="236d0-200">Initial setup</span></span>
1. <span data-ttu-id="236d0-201">Unity에서 개발 PC에서 엽니다 **파일 > 빌드 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-201">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="236d0-202">변경 **플랫폼** 하 **유니버설 Windows 플랫폼** 를 클릭 하 고 **스위치 플랫폼**</span><span class="sxs-lookup"><span data-stu-id="236d0-202">Change **Platform** to **Universal Windows Platform** and click **Switch Platfrom**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="236d0-203">HoloLens 원격 Unity를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-203">For HoloLens use Unity Remoting</span></span>
1. <span data-ttu-id="236d0-204">에 HoloLens에서 설치 하 고 실행 합니다 [Holographic 원격 플레이어](holographic-remoting-player.md), Windows 스토어에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-204">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="236d0-205">장치에서 응용 프로그램을 시작 하 고 대기 상태로 전환 하 고 장치의 IP 주소를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-205">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="236d0-206">IP 아래로 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-206">Note down the IP.</span></span>
2. <span data-ttu-id="236d0-207">오픈 **창 > xr 하이 > Holographic 에뮬레이션**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-207">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="236d0-208">변경 **에뮬레이션 모드** 에서 **None** 하 **장치에 원격**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-208">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="236d0-209">**원격 컴퓨터**, 앞서 언급 했 듯이 HoloLens의 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-209">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="236d0-210">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-210">Click **Connect**.</span></span>
6. <span data-ttu-id="236d0-211">확인 합니다 **연결 상태** 녹색으로 바뀝니다 **Connected**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-211">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="236d0-212">이제 클릭할 수 있습니다 **재생** Unity 편집기에서.</span><span class="sxs-lookup"><span data-stu-id="236d0-212">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="236d0-213">이제 장치에서 및 편집기에서 큐브를 볼 수 됩니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-213">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="236d0-214">일시 중지 하 고, 개체를 검사 하 고, 상황을 기본적으로 이기 때문에 편집기에서 앱을 실행 된 것 처럼 하지만 비디오, 오디오 및 호스트 컴퓨터와 장치 간의 네트워크를 통해 앞뒤로 전송 장치 입력을 사용 하 여 디버깅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-214">You can pause, inspect objects, and debug just like you are running an app in the editor, because that’s essentially what’s happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="236d0-215">다른 혼합된 현실 헤드셋을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-215">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="236d0-216">헤드셋을 개발 PC에 USB 케이블 및 HDMI를 사용 하 여 연결 하거나 포트 케이블을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-216">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="236d0-217">시작 합니다 **혼합 현실 포털** 첫 실행된 경험 완료를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-217">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="236d0-218">Unity에서 재생 단추를 눌러 지금 있습니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-218">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="236d0-219">이제 편집기에서 혼합된 현실 헤드셋에 큐브 렌더링을 볼 수 됩니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-219">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="236d0-220">-6 장 빌드하고 Visual Studio에서 장치에 배포</span><span class="sxs-lookup"><span data-stu-id="236d0-220">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="236d0-221">Visual studio 프로젝트를 컴파일 및 대상 장치에 배포할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-221">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="236d0-222">Visual Studio 솔루션을 내보내려면</span><span class="sxs-lookup"><span data-stu-id="236d0-222">Export to the Visual Studio solution</span></span>
1.  <span data-ttu-id="236d0-223">오픈 **파일 > 빌드 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-223">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="236d0-224">클릭 **열기 장면 추가** 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-224">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="236d0-225">변경 **플랫폼** 하 **유니버설 Windows 플랫폼** 누릅니다 **플랫폼 전환**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-225">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="236d0-226">**Windows 스토어** 설정을 위해 **SDK** 됩니다 **유니버설 10**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-226">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="236d0-227">대상 장치를 둡니다 **모든 장치** 폐색 표시 또는 전환에 대 한 **HoloLens**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-227">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="236d0-228">**UWP 빌드 형식** 있어야 **D3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-228">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="236d0-229">**UWP SDK** 으로 유지할 수 없습니다 **가장 최근에 설치 된**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-229">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="236d0-230">확인할 **Unity C# 프로젝트** 디버깅에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-230">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="236d0-231">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-231">Click **Build**.</span></span>
10. <span data-ttu-id="236d0-232">파일 탐색기에서 클릭 **새 폴더** 는 폴더의 이름을 **"App"** 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-232">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="236d0-233">사용 하 여는 **앱** 선택한 폴더를 클릭 합니다 **폴더 선택** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-233">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="236d0-234">Unity 완료 되 면을 빌드하는 Windows 파일 탐색기 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-234">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="236d0-235">엽니다는 **앱** 파일 탐색기에서 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-235">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="236d0-236">생성 된 Visual Studio 솔루션 (이 예제의 MixedRealityIntroduction.sln) 열기</span><span class="sxs-lookup"><span data-stu-id="236d0-236">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="236d0-237">Visual Studio 솔루션</span><span class="sxs-lookup"><span data-stu-id="236d0-237">Compile the Visual Studio solution</span></span>

<span data-ttu-id="236d0-238">마지막으로 내보낸된 Visual Studio 솔루션을 컴파일, 배포 하 고 장치에서이 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="236d0-238">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>
1. <span data-ttu-id="236d0-239">대상을 변경 맨 위의 도구 모음을 사용 하 여 Visual Studio에서 **디버그** 하 **릴리스** 들어오고 **ARM** 에 **X86**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-239">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="236d0-240">에뮬레이터 및 장치에 배포 하기 위한 지침을 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-240">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="236d0-241">설치와 일치 하는 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-241">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="236d0-242">Wi-fi를 통해 혼합된 현실 장치에 배포</span><span class="sxs-lookup"><span data-stu-id="236d0-242">Deploy to mixed reality device over Wi-Fi</span></span>
1. <span data-ttu-id="236d0-243">옆에 화살표를 클릭 합니다 **로컬 컴퓨터** 단추를 선택한 하 고 배포 대상을 변경할 **원격 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-243">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="236d0-244">혼합된 현실 장치의 IP 주소를 입력 하 고 변경할 **인증 모드** HoloLens에 대 한 유니버설 (암호화 되지 않은 프로토콜)를 하 고 **Windows** 다른 장치에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-244">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="236d0-245">클릭 **디버그 > 디버깅 하지 않고 시작**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-245">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="236d0-246">**HoloLens에 대 한**처음으로이 경우 장치에 배포 해야 쌍 [Visual Studio를 사용 하 여](using-visual-studio.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-246">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="236d0-247">혼합된 현실 장치에 USB를 통해 배포</span><span class="sxs-lookup"><span data-stu-id="236d0-247">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="236d0-248">USB 케이블을 통해 장치 연결 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-248">Ensure you device is plugged in via the USB cable.</span></span>
1. <span data-ttu-id="236d0-249">**HoloLens에 대 한**, 옆에 화살표를 클릭 합니다 **로컬 컴퓨터** 단추를 선택한 하 고 배포 대상을 변경할 **장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-249">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="236d0-250">**사용자 PC에 연결 하는 폐색 장치를 대상으로 하는 것에 대 한**, 로컬 컴퓨터 설정을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-250">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="236d0-251">했는지 확인 합니다 **혼합 현실 포털** 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-251">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="236d0-252">클릭 **디버그 > 디버깅 하지 않고 시작**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-252">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="236d0-253">에뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="236d0-253">Deploy to Emulator</span></span>
1. <span data-ttu-id="236d0-254">옆에 화살표를 클릭 합니다 **장치** 단추 및 드롭다운 선택 목록에서 **HoloLens 에뮬레이터**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-254">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="236d0-255">클릭 **디버그 > 디버깅 하지 않고 시작**합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-255">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="236d0-256">앱을 사용해</span><span class="sxs-lookup"><span data-stu-id="236d0-256">Try out your app</span></span>

<span data-ttu-id="236d0-257">에 앱을 배포 했으므로 큐브 주위의 모든 이동 하 고는 사용자 앞에 전 세계에 유지 되는 관찰 합니다.</span><span class="sxs-lookup"><span data-stu-id="236d0-257">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="236d0-258">참조</span><span class="sxs-lookup"><span data-stu-id="236d0-258">See also</span></span>
* [<span data-ttu-id="236d0-259">Unity 개발 개요</span><span class="sxs-lookup"><span data-stu-id="236d0-259">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="236d0-260">Unity 및 Visual Studio 사용 모범 사례</span><span class="sxs-lookup"><span data-stu-id="236d0-260">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="236d0-261">MR Basics 101</span><span class="sxs-lookup"><span data-stu-id="236d0-261">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="236d0-262">MR Basics 101E</span><span class="sxs-lookup"><span data-stu-id="236d0-262">MR Basics 101E</span></span>](holograms-101e.md)
