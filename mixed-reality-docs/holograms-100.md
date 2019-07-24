---
title: MR 기본 사항 100-Unity 시작
description: 첫 번째 기본 혼합 현실 "hello 세계" 응용 프로그램을 만드는 방법에 대해 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: 혼합 현실, Windows Mixed Reality, HoloLens, 몰입 형, vr, mr, 시작, 홀로그램, 아카데미, 자습서
ms.openlocfilehash: fd3bed955e80ec18b7be500adbdb0fcb7062d129
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993616"
---
>[!NOTE]
><span data-ttu-id="fa7e5-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="fa7e5-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="fa7e5-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="fa7e5-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="fa7e5-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="fa7e5-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="fa7e5-110">MR 기본 사항 100: Unity 시작</span><span class="sxs-lookup"><span data-stu-id="fa7e5-110">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="fa7e5-111">이 자습서에서는 Unity로 빌드된 기본 혼합 현실 앱을 만드는 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-111">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="fa7e5-112">장치 지원</span><span class="sxs-lookup"><span data-stu-id="fa7e5-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="fa7e5-113">과정</span><span class="sxs-lookup"><span data-stu-id="fa7e5-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="fa7e5-114"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="fa7e5-114"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="fa7e5-115"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="fa7e5-115"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="fa7e5-116">MR 기본 사항 100: Unity 시작</span><span class="sxs-lookup"><span data-stu-id="fa7e5-116">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="fa7e5-117">✔️</span><span class="sxs-lookup"><span data-stu-id="fa7e5-117">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="fa7e5-118">✔️</span><span class="sxs-lookup"><span data-stu-id="fa7e5-118">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="fa7e5-119">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="fa7e5-119">Prerequisites</span></span>

* <span data-ttu-id="fa7e5-120">올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-120">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="fa7e5-121">1 장-새 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="fa7e5-121">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="fa7e5-122">Unity를 사용 하 여 앱을 빌드하려면 먼저 프로젝트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-122">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="fa7e5-123">이 프로젝트는 몇 개의 폴더로 구성 되며 가장 중요 한 것은 자산 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-123">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="fa7e5-124">이 폴더는 Maya, Max 시네마, Photoshop 등의 디지털 콘텐츠 생성 도구에서 가져온 모든 자산, Visual Studio 또는 즐겨 찾는 코드 편집기를 사용 하 여 만든 모든 코드, 그리고 장면을 작성할 때 Unity가 만드는 모든 콘텐츠 파일을 포함 하는 폴더입니다. 편집기의, 애니메이션 및 기타 Unity 자산 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-124">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="fa7e5-125">UWP 앱을 빌드 및 배포 하기 위해 Unity는 필요한 모든 자산과 코드 파일을 포함 하는 Visual Studio 솔루션으로 프로젝트를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-125">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="fa7e5-126">Unity 시작</span><span class="sxs-lookup"><span data-stu-id="fa7e5-126">Start Unity</span></span>
2. <span data-ttu-id="fa7e5-127">**새로 만들기** 선택</span><span class="sxs-lookup"><span data-stu-id="fa7e5-127">Select **New**</span></span>
3. <span data-ttu-id="fa7e5-128">프로젝트 이름(예: "MixedRealityIntroduction")</span><span class="sxs-lookup"><span data-stu-id="fa7e5-128">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="fa7e5-129">프로젝트를 저장할 위치를 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-129">Enter a location to save your project</span></span>
5. <span data-ttu-id="fa7e5-130">**3d** 토글이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-130">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="fa7e5-131">**프로젝트 만들기** 선택</span><span class="sxs-lookup"><span data-stu-id="fa7e5-131">Select **Create project**</span></span>

<span data-ttu-id="fa7e5-132">이제 혼합 현실 사용자 지정을 시작 하기 위한 모든 설정이 축 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-132">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="fa7e5-133">2 장-카메라 설정</span><span class="sxs-lookup"><span data-stu-id="fa7e5-133">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="fa7e5-134">Unity 기본 카메라는 헤드 추적 및 stereoscopic 렌더링을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-134">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="fa7e5-135">혼합 현실에서 사용할 수 있도록 기본 카메라에 몇 가지 변경 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-135">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>
1. <span data-ttu-id="fa7e5-136">파일 > 새 장면 선택</span><span class="sxs-lookup"><span data-stu-id="fa7e5-136">Select File > New Scene</span></span>

<span data-ttu-id="fa7e5-137">첫째, 사용자의 시작 위치 (**X**:)를 사용 하는 경우 앱을 레이아웃 하는 것이 더 쉽습니다. 0, **Y**: 0, **Z**: 0).</span><span class="sxs-lookup"><span data-stu-id="fa7e5-137">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="fa7e5-138">주 카메라가 사용자 헤드의 이동을 추적 하므로 기본 카메라의 시작 위치를 설정 하 여 사용자의 시작 위치를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-138">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>
1. <span data-ttu-id="fa7e5-139">**계층** 패널에서 **주 카메라** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-139">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="fa7e5-140">**검사기** 패널에서 **변형** 구성 요소를 찾아 **위치** (**X**:)를 변경 합니다. 0, **Y**: 1, **Z**:-10) ~ (**X**: 0, **Y**: 0, **Z**: 0</span><span class="sxs-lookup"><span data-stu-id="fa7e5-140">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="fa7e5-141">둘째, 기본 카메라 배경을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-141">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="fa7e5-142">**HoloLens 응용 프로그램의**경우 실제 세계는 Skybox 질감이 아닌 카메라에서 렌더링 하는 모든 항목 뒤에 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-142">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>
1. <span data-ttu-id="fa7e5-143">**계층** 패널 **에서 주 카메라** 를 선택 하 고, **검사기** 패널에서 **카메라** 구성 요소를 찾고, **Clear Flags** 드롭다운에서 **Skybox** 에서 **Solid 색**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-143">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="fa7e5-144">**배경색** 선택을 선택 하 고 **RGBA** 값을 (0, 0, 0, 0)으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-144">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="fa7e5-145">**모던 헤드셋을 대상으로 하는 혼합 현실 응용 프로그램의**경우 Unity에서 제공 하는 기본 Skybox 텍스처를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-145">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>
1. <span data-ttu-id="fa7e5-146">**계층** 패널 **에서 주 카메라** 를 선택 하 고, **검사기** 패널에서 **카메라** 구성 요소를 찾고, **Clear Flags** 드롭다운을 **Skybox**으로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-146">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="fa7e5-147">셋째, Unity에서 가까운 클립 평면을 고려 하 고 사용자가 개체 또는 개체에 접근 하기 때문에 개체가 사용자 눈에 너무 가깝게 렌더링 되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-147">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="fa7e5-148">**Hololens 응용 프로그램의**경우 가까운 클립 평면을 [hololens 권장](camera-in-unity.md#clip-planes) 0.85 미터로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-148">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>
1. <span data-ttu-id="fa7e5-149">**계층** 패널 **에서 주 카메라** 를 선택 하 고, **검사기** 패널에서 **카메라** 구성 요소를 찾아 **가까운 클립 평면** 필드를 기본값 **0.3** 에서 HoloLens 권장 0.85으로 변경 합니다. .</span><span class="sxs-lookup"><span data-stu-id="fa7e5-149">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="fa7e5-150">**모던 헤드셋을 대상으로 하는 혼합 현실 응용 프로그램의**경우 Unity에서 제공 하는 기본 설정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-150">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>
1. <span data-ttu-id="fa7e5-151">**계층** 패널에서 **주 카메라** 를 선택 하 고, **검사기** 패널에서 **카메라** 구성 요소를 찾아 **가까운 클립 평면** 필드를 기본 **0.3**으로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-151">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="fa7e5-152">마지막으로 지금까지 진행 상황을 저장 해 주세요.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-152">Finally, let us save our progress so far.</span></span> <span data-ttu-id="fa7e5-153">장면 변경 내용을 저장 하려면 > 파일을 선택 하 고 **다른 이름으로 장면 저장**을 선택한 다음, **저장**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-153">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="fa7e5-154">3 장-프로젝트 설정 설치</span><span class="sxs-lookup"><span data-stu-id="fa7e5-154">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="fa7e5-155">이 장에서는 개발을 위해 Windows Holographic SDK를 대상으로 하는 데 도움이 되는 몇 가지 Unity 프로젝트 설정을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-155">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="fa7e5-156">응용 프로그램에 대 한 몇 가지 품질 설정도 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-156">We will also set some quality settings for our application.</span></span> <span data-ttu-id="fa7e5-157">마지막으로 빌드 대상이 Windows Store로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-157">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="fa7e5-158">Unity 성능 및 품질 설정</span><span class="sxs-lookup"><span data-stu-id="fa7e5-158">Unity performance and quality settings</span></span>

<span data-ttu-id="fa7e5-159">**HoloLens 용 Unity 품질 설정**</span><span class="sxs-lookup"><span data-stu-id="fa7e5-159">**Unity quality settings for HoloLens**</span></span>

![HoloLens 용 Unity 품질 설정](images/qualitysettings.png) 

<span data-ttu-id="fa7e5-161">HoloLens에서 높은 프레임 속도를 유지 하는 것이 매우 중요 하기 때문에 최상의 성능을 위해 품질 설정을 조정 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-161">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="fa7e5-162">자세한 성능 정보는 [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-162">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>
1. <span data-ttu-id="fa7e5-163">**편집 > 프로젝트 설정 > 품질** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-163">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="fa7e5-164">**Windows 스토어** 로고 아래의 **드롭다운** 을 선택 하 고 **매우 낮음**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-164">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="fa7e5-165">Windows 스토어 열의 상자와 **매우 낮은** 행이 녹색 인 경우 설정이 올바르게 적용 됨을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-165">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="fa7e5-166">**폐색를 대상으로 하는 혼합 현실 응용 프로그램의 경우**품질 설정을 기본값으로 그대로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-166">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="fa7e5-167">Windows 10 SDK를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-167">Target Windows 10 SDK</span></span>

<span data-ttu-id="fa7e5-168">**Windows Holographic SDK 대상**</span><span class="sxs-lookup"><span data-stu-id="fa7e5-168">**Target Windows Holographic SDK**</span></span>

![Windows Holographic SDK 대상](images/xrsettings.png) 

<span data-ttu-id="fa7e5-170">내보내려는 앱이 2D 보기 대신 [몰입 형 보기](app-views.md) 를 만들어야 한다고 Unity에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-170">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="fa7e5-171">Windows 10 SDK를 대상으로 하는 Unity에서 가상 현실 지원을 사용 하도록 설정 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-171">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>
1. <span data-ttu-id="fa7e5-172">**편집 > 프로젝트 설정 > 플레이어**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-172">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="fa7e5-173">플레이어 설정에 대 한 **검사기 패널** 에서 **Windows 스토어** 아이콘을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-173">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="fa7e5-174">**XR 설정** 그룹을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-174">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="fa7e5-175">**렌더링** 섹션에서 **가상 현실 지원 됨** 확인란을 선택 하 여 새 **가상 현실 sdk** 목록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-175">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="fa7e5-176">**Windows Mixed Reality** 가 목록에 나타나는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-176">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="fa7e5-177">그렇지 않은 경우 목록 아래쪽 **+** 의 단추를 선택 하 고 **Windows Mixed Reality**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-177">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="fa7e5-178">**Windows 스토어** 아이콘이 표시 되지 않는 경우 설치 하기 전에 windows 스토어 .Net 스크립팅 백 엔드를 선택 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-178">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="fa7e5-179">그렇지 않은 경우 올바른 Windows 설치를 사용 하 여 Unity를 다시 설치 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-179">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="fa7e5-180">**.NET 구성 확인**</span><span class="sxs-lookup"><span data-stu-id="fa7e5-180">**Verify .NET Configuration**</span></span>

![.NET 구성 확인](images/configoptions-375px.png)

1. <span data-ttu-id="fa7e5-182">**편집 > 프로젝트 설정 > 플레이어** 로 이동 합니다 (이전 단계에서이 작업을 계속 진행할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="fa7e5-182">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="fa7e5-183">플레이어 설정에 대 한 **검사기 패널** 에서 **Windows 스토어** 아이콘을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-183">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="fa7e5-184">**기타 설정** 구성 섹션에서 **Scripting 백 엔드가** **.net** 으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-184">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="fa7e5-185">모든 프로젝트 설정을 적용 하기 위한 놀라운 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-185">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="fa7e5-186">다음으로, 홀로그램을 추가 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-186">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="fa7e5-187">4 장-큐브 만들기</span><span class="sxs-lookup"><span data-stu-id="fa7e5-187">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="fa7e5-188">Unity 프로젝트에서 큐브를 만드는 것은 Unity에서 다른 개체를 만드는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-188">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="fa7e5-189">Unity의 좌표계가 실제 세계에 매핑되므로 unity의 좌표계가 실제 환경에서 약 1 미터의 약 1 미터에 매핑되므로 사용자 앞에 큐브를 배치 하는 것이 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-189">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>
1. <span data-ttu-id="fa7e5-190">**계층** 패널의 왼쪽 위 모서리에서 **만들기** 드롭다운을 선택 하 고 **3d 개체 > 큐브**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-190">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="fa7e5-191">**계층** 패널에서 새로 만든 **큐브** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-191">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="fa7e5-192">**검사기** 에서 **변형** 구성 요소를 찾고 **위치** 를 (**X**:)로 변경 합니다. 0, **Y**: 0, **Z**: 2).</span><span class="sxs-lookup"><span data-stu-id="fa7e5-192">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="fa7e5-193">*이는 큐브 2 미터를 사용자의 시작 위치 앞에 배치 합니다.*</span><span class="sxs-lookup"><span data-stu-id="fa7e5-193">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="fa7e5-194">**변환** 구성 요소에서 **회전** 을 (**X**: 45, **Y**: 45, **Z**: 45) 및 **배율** 변경 (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span><span class="sxs-lookup"><span data-stu-id="fa7e5-194">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="fa7e5-195">*그러면 큐브의 크기가 0.25 미터가 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="fa7e5-195">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="fa7e5-196">장면 변경 내용을 저장 하려면 **파일 > 장면 저장**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-196">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="fa7e5-197">5 장-Unity 편집기에서 장치 확인</span><span class="sxs-lookup"><span data-stu-id="fa7e5-197">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="fa7e5-198">이제 큐브를 만들었으므로 장치를 빠르게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-198">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="fa7e5-199">Unity 편집기 내에서이 작업을 직접 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-199">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="fa7e5-200">초기 설정</span><span class="sxs-lookup"><span data-stu-id="fa7e5-200">Initial setup</span></span>
1. <span data-ttu-id="fa7e5-201">개발 PC의 Unity에서 **파일 > 빌드 설정** 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-201">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="fa7e5-202">**플랫폼** 을 **유니버설 Windows 플랫폼** 로 변경 하 고 **platfrom.details.heap.alignedallocate 전환** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-202">Change **Platform** to **Universal Windows Platform** and click **Switch Platfrom**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="fa7e5-203">HoloLens의 경우 Unity 원격 기능 사용</span><span class="sxs-lookup"><span data-stu-id="fa7e5-203">For HoloLens use Unity Remoting</span></span>
1. <span data-ttu-id="fa7e5-204">HoloLens에서 Windows 스토어에서 사용할 수 있는 [Holographic Remoting 플레이어](holographic-remoting-player.md)를 설치 하 고 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-204">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="fa7e5-205">장치에서 응용 프로그램을 시작 하면 대기 중 상태로 전환 되 고 장치의 IP 주소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-205">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="fa7e5-206">IP를 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-206">Note down the IP.</span></span>
2. <span data-ttu-id="fa7e5-207">**창 > XR > Holographic 에뮬레이션**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-207">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="fa7e5-208">**에뮬레이션 모드** 를 **없음** 에서 **원격에서 장치로**변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-208">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="fa7e5-209">**원격 컴퓨터**에 앞에서 적어둔 HOLOLENS의 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-209">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="fa7e5-210">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-210">Click **Connect**.</span></span>
6. <span data-ttu-id="fa7e5-211">**연결 상태가** **녹색으로**변경 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-211">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="fa7e5-212">이제 Unity 편집기에서 **Play** 를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-212">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="fa7e5-213">이제 장치 및 편집기에서 큐브를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-213">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="fa7e5-214">편집기에서 응용 프로그램을 실행 하는 것 처럼 편집기에서 응용 프로그램을 실행 하는 것 처럼 응용 프로그램을 일시 중지 하 고 검사 하 고 디버그할 수 있습니다. 단, 비디오, 오디오 및 장치 입력은 네트워크를 통해 호스트 컴퓨터와 장치 간에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-214">You can pause, inspect objects, and debug just like you are running an app in the editor, because that’s essentially what’s happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="fa7e5-215">다른 혼합 현실 지원 헤드셋의 경우</span><span class="sxs-lookup"><span data-stu-id="fa7e5-215">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="fa7e5-216">USB 케이블과 HDMI 또는 디스플레이 포트 케이블을 사용 하 여 개발 PC에 헤드셋을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-216">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="fa7e5-217">**혼합 현실 포털** 을 시작 하 고 첫 실행 환경을 완료 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-217">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="fa7e5-218">이제 Unity에서 재생 단추를 누를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-218">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="fa7e5-219">이제 혼합 현실 헤드셋 및 편집기에서 큐브 렌더링을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-219">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="fa7e5-220">6 장-Visual Studio에서 장치 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="fa7e5-220">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="fa7e5-221">이제 프로젝트를 Visual Studio로 컴파일하고 대상 장치에 배포할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-221">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="fa7e5-222">Visual Studio 솔루션으로 내보내기</span><span class="sxs-lookup"><span data-stu-id="fa7e5-222">Export to the Visual Studio solution</span></span>
1.  <span data-ttu-id="fa7e5-223">**파일 > 빌드 설정** 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-223">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="fa7e5-224">열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-224">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="fa7e5-225">**플랫폼** 을 **유니버설 Windows 플랫폼** 로 변경 하 고 **플랫폼 전환**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-225">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="fa7e5-226">**Windows 스토어** 설정에서 **SDK** 가 **유니버설 10**인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-226">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="fa7e5-227">대상 장치에 대해 폐색를 표시 하거나 **HoloLens**로 전환 하는 **모든 장치** 를 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-227">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="fa7e5-228">**UWP 빌드 형식은** **D3D**이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-228">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="fa7e5-229">**UWP SDK** 는 **설치 된 최신 버전**으로 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-229">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="fa7e5-230">디버깅 **중인 C# Unity 프로젝트** 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-230">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="fa7e5-231">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-231">Click **Build**.</span></span>
10. <span data-ttu-id="fa7e5-232">파일 탐색기에서 **새 폴더** 를 클릭 하 고 폴더 이름을 **"App"** 으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-232">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="fa7e5-233">**앱** 폴더가 선택 된 상태에서 **폴더 선택** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-233">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="fa7e5-234">Unity가 빌드를 완료 하면 Windows 파일 탐색기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-234">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="fa7e5-235">파일 탐색기에서 **앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-235">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="fa7e5-236">생성 된 Visual Studio 솔루션 (이 예제에서는 MixedRealityIntroduction)을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-236">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="fa7e5-237">Visual Studio 솔루션 컴파일</span><span class="sxs-lookup"><span data-stu-id="fa7e5-237">Compile the Visual Studio solution</span></span>

<span data-ttu-id="fa7e5-238">마지막으로, 내보낸 Visual Studio 솔루션을 컴파일하여 배포 하 고 장치에서 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-238">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>
1. <span data-ttu-id="fa7e5-239">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 **디버그** 에서 **릴리스** 로, **ARM** 에서 **x 86**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-239">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="fa7e5-240">지침은 장치 및 에뮬레이터에 배포 하는 경우와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-240">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="fa7e5-241">설치와 일치 하는 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-241">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="fa7e5-242">Wi-fi를 통해 혼합 현실 장치에 배포</span><span class="sxs-lookup"><span data-stu-id="fa7e5-242">Deploy to mixed reality device over Wi-Fi</span></span>
1. <span data-ttu-id="fa7e5-243">**로컬 컴퓨터** 단추 옆의 화살표를 클릭 하 고 배포 대상을 **원격 컴퓨터로**변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-243">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="fa7e5-244">혼합 현실 장치의 IP 주소를 입력 하 고 다른 장치의 HoloLens 및 **Windows** 에 대 한 **인증 모드** 를 유니버설 (암호화 되지 않은 프로토콜)으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-244">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="fa7e5-245">**디버그 > 디버깅 하지 않고 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-245">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="fa7e5-246">**HoloLens의**경우 장치에 처음 배포 하는 경우 [Visual Studio를 사용 하 여](using-visual-studio.md)페어링 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-246">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="fa7e5-247">USB를 통해 혼합 현실 장치에 배포</span><span class="sxs-lookup"><span data-stu-id="fa7e5-247">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="fa7e5-248">USB 케이블을 통해 장치가 연결 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-248">Ensure you device is plugged in via the USB cable.</span></span>
1. <span data-ttu-id="fa7e5-249">**HoloLens의**경우 **로컬 컴퓨터** 단추 옆에 있는 화살표를 클릭 하 고 배포 대상을 **장치**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-249">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="fa7e5-250">**PC에 연결 된 폐색 장치를 대상으로 지정**하려면 설정을 로컬 컴퓨터에 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-250">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="fa7e5-251">**혼합 현실 포털이** 실행 중인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-251">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="fa7e5-252">**디버그 > 디버깅 하지 않고 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-252">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="fa7e5-253">에뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="fa7e5-253">Deploy to Emulator</span></span>
1. <span data-ttu-id="fa7e5-254">**장치** 단추 옆의 화살표를 클릭 하 고 드롭다운에서 **HoloLens 에뮬레이터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-254">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="fa7e5-255">**디버그 > 디버깅 하지 않고 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-255">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="fa7e5-256">앱 사용해 보기</span><span class="sxs-lookup"><span data-stu-id="fa7e5-256">Try out your app</span></span>

<span data-ttu-id="fa7e5-257">이제 앱이 배포 되었으므로 큐브를 모두 이동 하 여 전 세계에 유지 되는지 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa7e5-257">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa7e5-258">참조</span><span class="sxs-lookup"><span data-stu-id="fa7e5-258">See also</span></span>
* [<span data-ttu-id="fa7e5-259">Unity 개발 개요</span><span class="sxs-lookup"><span data-stu-id="fa7e5-259">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="fa7e5-260">Unity 및 Visual Studio 사용 모범 사례</span><span class="sxs-lookup"><span data-stu-id="fa7e5-260">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="fa7e5-261">MR 기본 사항 101</span><span class="sxs-lookup"><span data-stu-id="fa7e5-261">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="fa7e5-262">MR 기본 사항 101E</span><span class="sxs-lookup"><span data-stu-id="fa7e5-262">MR Basics 101E</span></span>](holograms-101e.md)
