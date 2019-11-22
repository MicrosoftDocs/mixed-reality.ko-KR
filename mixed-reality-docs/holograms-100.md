---
title: MR 기본 사항 100-Unity 시작
description: 첫 번째 기본 혼합 현실 "hello 세계" 응용 프로그램을 만드는 방법에 대해 알아봅니다.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: 혼합 현실, Windows Mixed Reality, HoloLens, 몰입 형, vr, mr, 시작, 홀로그램, 아카데미, 자습서
ms.openlocfilehash: 0600383b3cca3f580f014597217afc6ae78836dd
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926636"
---
>[!NOTE]
><span data-ttu-id="04978-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="04978-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="04978-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="04978-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04978-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="04978-108">HoloLens 2에 대 한 [새로운 일련의 자습서](mrlearning-base.md) 가 게시 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-108">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="04978-109">MR 기본 사항 100: Unity 시작</span><span class="sxs-lookup"><span data-stu-id="04978-109">MR Basics 100: Getting started with Unity</span></span>

<span data-ttu-id="04978-110">이 자습서에서는 Unity로 빌드된 기본 혼합 현실 앱을 만드는 과정을 안내 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="04978-111">장치 지원</span><span class="sxs-lookup"><span data-stu-id="04978-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="04978-112">과정</span><span class="sxs-lookup"><span data-stu-id="04978-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="04978-113"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="04978-113"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="04978-114"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="04978-114"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="04978-115">MR 기본 사항 100: Unity 시작</span><span class="sxs-lookup"><span data-stu-id="04978-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="04978-116">✔️</span><span class="sxs-lookup"><span data-stu-id="04978-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="04978-117">✔️</span><span class="sxs-lookup"><span data-stu-id="04978-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="04978-118">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="04978-118">Prerequisites</span></span>

* <span data-ttu-id="04978-119">올바른 [도구로](install-the-tools.md)구성 된 WINDOWS 10 PC입니다.</span><span class="sxs-lookup"><span data-stu-id="04978-119">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="04978-120">1 장-새 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="04978-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="04978-121">Unity를 사용 하 여 앱을 빌드하려면 먼저 프로젝트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="04978-122">이 프로젝트는 몇 개의 폴더로 구성 되며 가장 중요 한 것은 자산 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="04978-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="04978-123">이 폴더는 Maya, Max 시네마, Photoshop 등의 디지털 콘텐츠 생성 도구에서 가져온 모든 자산, Visual Studio 또는 즐겨 찾는 코드 편집기를 사용 하 여 만든 모든 코드, 그리고 장면을 작성할 때 Unity가 만드는 모든 콘텐츠 파일을 포함 하는 폴더입니다. 편집기의, 애니메이션 및 기타 Unity 자산 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="04978-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="04978-124">UWP 앱을 빌드 및 배포 하기 위해 Unity는 필요한 모든 자산과 코드 파일을 포함 하는 Visual Studio 솔루션으로 프로젝트를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="04978-125">Unity 시작</span><span class="sxs-lookup"><span data-stu-id="04978-125">Start Unity</span></span>
2. <span data-ttu-id="04978-126">**새로 만들기** 선택</span><span class="sxs-lookup"><span data-stu-id="04978-126">Select **New**</span></span>
3. <span data-ttu-id="04978-127">프로젝트 이름 (예: "MixedRealityIntroduction")을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="04978-128">프로젝트를 저장할 위치를 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="04978-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="04978-129">**3d** 토글이 선택 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="04978-130">**프로젝트 만들기** 선택</span><span class="sxs-lookup"><span data-stu-id="04978-130">Select **Create project**</span></span>

<span data-ttu-id="04978-131">이제 혼합 현실 사용자 지정을 시작 하기 위한 모든 설정이 축 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="04978-132">2 장-카메라 설정</span><span class="sxs-lookup"><span data-stu-id="04978-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="04978-133">Unity 기본 카메라는 헤드 추적 및 stereoscopic 렌더링을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="04978-134">혼합 현실에서 사용할 수 있도록 기본 카메라에 몇 가지 변경 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="04978-135">파일 > 새 장면 선택</span><span class="sxs-lookup"><span data-stu-id="04978-135">Select File > New Scene</span></span>

<span data-ttu-id="04978-136">첫째, 사용자의 시작 위치 (**X**: 0, **Y**: 0, **Z**: 0)를 생각해 보면 앱을 레이아웃 하는 것이 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-136">First, it will be easier to lay out your app if you imagine the starting position of the user as (**X**: 0, **Y**: 0, **Z**: 0).</span></span> <span data-ttu-id="04978-137">주 카메라가 사용자 헤드의 이동을 추적 하므로 기본 카메라의 시작 위치를 설정 하 여 사용자의 시작 위치를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="04978-138">**계층** 패널에서 **주 카메라** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="04978-139">**검사기** 패널에서 **변형** 구성 요소를 찾아 **위치** 를 (**x**: 0, **y**: 1, **z**:-10)에서 (**x**: 0, **y**: 0, **z**: 0)로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from (**X**: 0, **Y**: 1, **Z**: -10) to (**X**: 0, **Y**: 0, **Z**: 0)</span></span>

<span data-ttu-id="04978-140">둘째, 기본 카메라 배경을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="04978-141">**HoloLens 응용 프로그램의**경우 실제 세계는 Skybox 질감이 아닌 카메라에서 렌더링 하는 모든 항목 뒤에 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-141">**For HoloLens applications**, the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="04978-142">**계층** 패널 **에서 주 카메라** 를 선택 하 고, **검사기** 패널에서 **카메라** 구성 요소를 찾고, **Clear Flags** 드롭다운에서 **Skybox** 에서 **Solid 색**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color**.</span></span>
2. <span data-ttu-id="04978-143">**배경색** 선택을 선택 하 고 **RGBA** 값을 (0, 0, 0, 0)으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="04978-144">**모던 헤드셋을 대상으로 하는 혼합 현실 응용 프로그램의**경우 Unity에서 제공 하는 기본 Skybox 텍스처를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-144">**For mixed reality applications targeted to immersive headsets**, we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="04978-145">**계층** 패널 **에서 주 카메라** 를 선택 하 고, **검사기** 패널에서 **카메라** 구성 요소를 찾고, **Clear Flags** 드롭다운을 **Skybox**으로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox**.</span></span>

<span data-ttu-id="04978-146">셋째, Unity에서 가까운 클립 평면을 고려 하 고 사용자가 개체 또는 개체에 접근 하기 때문에 개체가 사용자 눈에 너무 가깝게 렌더링 되지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="04978-147">**Hololens 응용 프로그램의**경우 가까운 클립 평면을 [hololens 권장](camera-in-unity.md#clip-planes) 0.85 미터로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-147">**For HoloLens applications**, the near clip plane can be set to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="04978-148">**계층** 패널 **에서 주 카메라** 를 선택 하 고, **검사기** 패널에서 **카메라** 구성 요소를 찾아 **가까운 클립 평면** 필드를 기본 **0.3** 에서 HoloLens 권장 **0.85**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85**.</span></span>

<span data-ttu-id="04978-149">**모던 헤드셋을 대상으로 하는 혼합 현실 응용 프로그램의**경우 Unity에서 제공 하는 기본 설정을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-149">**For mixed reality applications targeted to immersive headsets**, we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="04978-150">**계층** 패널에서 **주 카메라** 를 선택 하 고, **검사기** 패널에서 **카메라** 구성 요소를 찾아 **가까운 클립 평면** 필드를 기본 **0.3**으로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3**.</span></span>

<span data-ttu-id="04978-151">마지막으로 지금까지 진행 상황을 저장 해 주세요.</span><span class="sxs-lookup"><span data-stu-id="04978-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="04978-152">장면 변경 내용을 저장 하려면 > 파일을 선택 하 고 **다른 이름으로 장면 저장**을 **선택한 다음**, **저장**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-152">To save the scene changes, select **File > Save Scene As**, name the scene **Main**, and select **Save**.</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="04978-153">3 장-프로젝트 설정 설치</span><span class="sxs-lookup"><span data-stu-id="04978-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="04978-154">이 장에서는 개발을 위해 Windows Holographic SDK를 대상으로 하는 데 도움이 되는 몇 가지 Unity 프로젝트 설정을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="04978-155">응용 프로그램에 대 한 몇 가지 품질 설정도 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04978-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="04978-156">마지막으로 빌드 대상이 Windows Store로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-156">Finally, we will ensure our build targets are set to Windows Store.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="04978-157">Unity 성능 및 품질 설정</span><span class="sxs-lookup"><span data-stu-id="04978-157">Unity performance and quality settings</span></span>

<span data-ttu-id="04978-158">**HoloLens 용 Unity 품질 설정**</span><span class="sxs-lookup"><span data-stu-id="04978-158">**Unity quality settings for HoloLens**</span></span>

![HoloLens 용 Unity 품질 설정](images/qualitysettings.png)

<span data-ttu-id="04978-160">HoloLens에서 높은 프레임 속도를 유지 하는 것이 매우 중요 하기 때문에 최상의 성능을 위해 품질 설정을 조정 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="04978-161">자세한 성능 정보는 [Unity에 대 한 성능 권장 사항](performance-recommendations-for-unity.md)을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-161">For more detailed performance information, [Performance recommendations for Unity](performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="04978-162">**편집 > 프로젝트 설정 > 품질** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="04978-163">**Windows 스토어** 로고 아래의 **드롭다운** 을 선택 하 고 **매우 낮음**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-163">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="04978-164">Windows 스토어 열의 상자와 **매우 낮은** 행이 녹색 인 경우 설정이 올바르게 적용 됨을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-164">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="04978-165">**폐색를 대상으로 하는 혼합 현실 응용 프로그램의 경우**품질 설정을 기본값으로 그대로 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-165">**For mixed reality applications targeted to occluded displays**, you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="04978-166">Windows 10 SDK를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="04978-167">**Windows Holographic SDK 대상**</span><span class="sxs-lookup"><span data-stu-id="04978-167">**Target Windows Holographic SDK**</span></span>

![Windows Holographic SDK 대상](images/xrsettings.png)

<span data-ttu-id="04978-169">내보내려는 앱이 2D 보기 대신 [몰입 형 보기](app-views.md) 를 만들어야 한다고 Unity에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-169">We need to let Unity know that the app we are trying to export should create an [immersive view](app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="04978-170">Windows 10 SDK를 대상으로 하는 Unity에서 가상 현실 지원을 사용 하도록 설정 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="04978-171">**편집 > 프로젝트 설정 > 플레이어**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-171">Go to **Edit > Project Settings > Player**.</span></span>
2. <span data-ttu-id="04978-172">플레이어 설정에 대 한 **검사기 패널** 에서 **Windows 스토어** 아이콘을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-172">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="04978-173">**XR 설정** 그룹을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="04978-174">**렌더링** 섹션에서 **가상 현실 지원 됨** 확인란을 선택 하 여 새 **가상 현실 sdk** 목록을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="04978-175">**Windows Mixed Reality** 가 목록에 나타나는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="04978-176">그렇지 않은 경우 목록 맨 아래에 있는 **+** 단추를 선택 하 고 **Windows Mixed Reality**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality**.</span></span>

>[!NOTE]
><span data-ttu-id="04978-177">**Windows 스토어** 아이콘이 표시 되지 않는 경우 설치 하기 전에 windows 스토어 .Net 스크립팅 백 엔드를 선택 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-177">If you do not see the **Windows Store** icon, double check to make sure you selected the Windows Store .NET Scripting Backend prior to installation.</span></span> <span data-ttu-id="04978-178">그렇지 않은 경우 올바른 Windows 설치를 사용 하 여 Unity를 다시 설치 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="04978-179">**.NET 구성 확인**</span><span class="sxs-lookup"><span data-stu-id="04978-179">**Verify .NET Configuration**</span></span>

![.NET 구성 확인](images/configoptions-375px.png)

1. <span data-ttu-id="04978-181">**편집 > 프로젝트 설정 > 플레이어** 로 이동 합니다 (이전 단계에서이 작업을 계속 진행할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="04978-181">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="04978-182">플레이어 설정에 대 한 **검사기 패널** 에서 **Windows 스토어** 아이콘을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-182">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="04978-183">**기타 설정** 구성 섹션에서 **Scripting 백 엔드가** **.net** 으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-183">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="04978-184">모든 프로젝트 설정을 적용 하기 위한 놀라운 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="04978-184">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="04978-185">다음으로, 홀로그램을 추가 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-185">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="04978-186">4 장-큐브 만들기</span><span class="sxs-lookup"><span data-stu-id="04978-186">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="04978-187">Unity 프로젝트에서 큐브를 만드는 것은 Unity에서 다른 개체를 만드는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-187">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="04978-188">Unity의 좌표계가 실제 세계에 매핑되므로 unity의 좌표계가 실제 환경에서 약 1 미터의 약 1 미터에 매핑되므로 사용자 앞에 큐브를 배치 하는 것이 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-188">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="04978-189">**계층** 패널의 왼쪽 위 모서리에서 **만들기** 드롭다운을 선택 하 고 **3d 개체 > 큐브**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-189">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube**.</span></span>
2. <span data-ttu-id="04978-190">**계층** 패널에서 새로 만든 **큐브** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-190">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="04978-191">**검사기** 에서 **변형** 구성 요소를 찾고 **위치** 를 (**X**: 0, **Y**: 0, **Z**: 2)로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-191">In the **Inspector** find the **Transform** component and change **Position** to (**X**: 0, **Y**: 0, **Z**: 2).</span></span> <span data-ttu-id="04978-192">*이는 큐브 2 미터를 사용자의 시작 위치 앞에 배치 합니다.*</span><span class="sxs-lookup"><span data-stu-id="04978-192">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="04978-193">**변환** 구성 요소에서 **회전** 을 (**x**: 45, **y**: 45, **z**: 45)로 변경 하 고 **Scale** 을 (**x**: 0.25, **Y**: 0.25, **z**: 0.25)로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-193">In the **Transform** component, change **Rotation** to (**X**: 45, **Y**: 45, **Z**: 45) and change **Scale** to (**X**: 0.25, **Y**: 0.25, **Z**: 0.25).</span></span> <span data-ttu-id="04978-194">*그러면 큐브의 크기가 0.25 미터가 됩니다.*</span><span class="sxs-lookup"><span data-stu-id="04978-194">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="04978-195">장면 변경 내용을 저장 하려면 **파일 > 장면 저장**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-195">To save the scene changes, select **File > Save Scene**.</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="04978-196">5 장-Unity 편집기에서 장치 확인</span><span class="sxs-lookup"><span data-stu-id="04978-196">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="04978-197">이제 큐브를 만들었으므로 장치를 빠르게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-197">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="04978-198">Unity 편집기 내에서이 작업을 직접 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-198">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="04978-199">초기 설정</span><span class="sxs-lookup"><span data-stu-id="04978-199">Initial setup</span></span>

1. <span data-ttu-id="04978-200">개발 PC의 Unity에서 **파일 > 빌드 설정** 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04978-200">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="04978-201">**플랫폼** 을 **유니버설 Windows 플랫폼** 로 변경 하 고 **플랫폼 전환** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-201">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="04978-202">HoloLens의 경우 Unity 원격 기능 사용</span><span class="sxs-lookup"><span data-stu-id="04978-202">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="04978-203">HoloLens에서 Windows 스토어에서 사용할 수 있는 [Holographic Remoting 플레이어](holographic-remoting-player.md)를 설치 하 고 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-203">On your HoloLens, install and run the [Holographic Remoting Player](holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="04978-204">장치에서 응용 프로그램을 시작 하면 대기 중 상태로 전환 되 고 장치의 IP 주소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04978-204">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="04978-205">IP를 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="04978-205">Note down the IP.</span></span>
2. <span data-ttu-id="04978-206">**창 > XR > Holographic 에뮬레이션**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04978-206">Open **Window > XR > Holographic Emulation**.</span></span>
3. <span data-ttu-id="04978-207">**에뮬레이션 모드** 를 **없음** 에서 **원격에서 장치로**변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-207">Change **Emulation Mode** from **None** to **Remote to Device**.</span></span>
4. <span data-ttu-id="04978-208">**원격 컴퓨터**에 앞에서 적어둔 HOLOLENS의 IP 주소를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-208">In **Remote Machine**, enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="04978-209">**연결**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-209">Click **Connect**.</span></span>
6. <span data-ttu-id="04978-210">**연결 상태가** **녹색으로**변경 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-210">Ensure the **Connection Status** changes to green **Connected**.</span></span>
7. <span data-ttu-id="04978-211">이제 Unity 편집기에서 **Play** 를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-211">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="04978-212">이제 장치 및 편집기에서 큐브를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-212">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="04978-213">편집기에서 응용 프로그램을 실행 하는 것 처럼 편집기에서 응용 프로그램을 실행 하는 것 처럼 응용 프로그램을 일시 중지 하 고 검사 하 고 디버그할 수 있습니다. 단, 비디오, 오디오 및 장치 입력은 네트워크를 통해 호스트 컴퓨터와 장치 간에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04978-213">You can pause, inspect objects, and debug just like you are running an app in the editor, because that’s essentially what’s happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="04978-214">다른 혼합 현실 지원 헤드셋의 경우</span><span class="sxs-lookup"><span data-stu-id="04978-214">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="04978-215">USB 케이블과 HDMI 또는 디스플레이 포트 케이블을 사용 하 여 개발 PC에 헤드셋을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-215">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="04978-216">**혼합 현실 포털** 을 시작 하 고 첫 실행 환경을 완료 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-216">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="04978-217">이제 Unity에서 재생 단추를 누를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-217">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="04978-218">이제 혼합 현실 헤드셋 및 편집기에서 큐브 렌더링을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-218">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="04978-219">6 장-Visual Studio에서 장치 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="04978-219">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="04978-220">이제 프로젝트를 Visual Studio로 컴파일하고 대상 장치에 배포할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-220">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="04978-221">Visual Studio 솔루션으로 내보내기</span><span class="sxs-lookup"><span data-stu-id="04978-221">Export to the Visual Studio solution</span></span>

1.  <span data-ttu-id="04978-222">**파일 > 빌드 설정** 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04978-222">Open **File > Build Settings** window.</span></span>
2.  <span data-ttu-id="04978-223">열려 있는 장면 **추가** 를 클릭 하 여 장면을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-223">Click **Add Open Scenes** to add the scene.</span></span>
3.  <span data-ttu-id="04978-224">**플랫폼** 을 **유니버설 Windows 플랫폼** 로 변경 하 고 **플랫폼 전환**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-224">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**.</span></span>
4.  <span data-ttu-id="04978-225">**Windows 스토어** 설정에서 **SDK** 가 **유니버설 10**인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-225">In **Windows Store** settings ensure, **SDK** is **Universal 10**.</span></span>
5.  <span data-ttu-id="04978-226">대상 장치에 대해 폐색를 표시 하거나 **HoloLens**로 전환 하는 **모든 장치** 를 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="04978-226">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens**.</span></span>
6.  <span data-ttu-id="04978-227">**UWP 빌드 형식은** **D3D**이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-227">**UWP Build Type** should be **D3D**.</span></span>
7.  <span data-ttu-id="04978-228">**UWP SDK** 는 **설치 된 최신 버전**으로 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04978-228">**UWP SDK** could be left at **Latest installed**.</span></span>
8.  <span data-ttu-id="04978-229">디버깅 **중인 C# Unity 프로젝트** 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-229">Check **Unity C# Projects** under Debugging.</span></span>
9.  <span data-ttu-id="04978-230">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-230">Click **Build**.</span></span>
10. <span data-ttu-id="04978-231">파일 탐색기에서 **새 폴더** 를 클릭 하 고 폴더 이름을 **"App"** 으로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-231">In the file explorer, click **New Folder** and name the folder **"App"**.</span></span>
11. <span data-ttu-id="04978-232">**앱** 폴더가 선택 된 상태에서 **폴더 선택** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-232">With the **App** folder selected, click the **Select Folder** button.</span></span>
12. <span data-ttu-id="04978-233">Unity가 빌드를 완료 하면 Windows 파일 탐색기 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04978-233">When Unity is done building, a Windows File Explorer window will appear.</span></span>
13. <span data-ttu-id="04978-234">파일 탐색기에서 **앱** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04978-234">Open the **App** folder in file explorer.</span></span>
14. <span data-ttu-id="04978-235">생성 된 Visual Studio 솔루션 (이 예제에서는 MixedRealityIntroduction)을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04978-235">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="04978-236">Visual Studio 솔루션 컴파일</span><span class="sxs-lookup"><span data-stu-id="04978-236">Compile the Visual Studio solution</span></span>

<span data-ttu-id="04978-237">마지막으로, 내보낸 Visual Studio 솔루션을 컴파일하여 배포 하 고 장치에서 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="04978-237">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="04978-238">Visual Studio의 맨 위 도구 모음을 사용 하 여 대상을 **디버그** 에서 **릴리스** 로, **ARM** 에서 **x 86**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-238">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86**.</span></span>

<span data-ttu-id="04978-239">지침은 장치 및 에뮬레이터에 배포 하는 경우와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="04978-239">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="04978-240">설치와 일치 하는 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="04978-240">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="04978-241">Wi-fi를 통해 혼합 현실 장치에 배포</span><span class="sxs-lookup"><span data-stu-id="04978-241">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="04978-242">**로컬 컴퓨터** 단추 옆의 화살표를 클릭 하 고 배포 대상을 **원격 컴퓨터로**변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-242">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine**.</span></span>
2. <span data-ttu-id="04978-243">혼합 현실 장치의 IP 주소를 입력 하 고 다른 장치의 HoloLens 및 **Windows** 에 대 한 **인증 모드** 를 유니버설 (암호화 되지 않은 프로토콜)으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-243">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="04978-244">**디버그 > 디버깅 하지 않고 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-244">Click **Debug > Start without debugging**.</span></span>

<span data-ttu-id="04978-245">**HoloLens의**경우 장치에 처음 배포 하는 경우 [Visual Studio를 사용 하 여](using-visual-studio.md)페어링 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-245">**For HoloLens**, If this is the first time deploying to your device, you will need to pair [using Visual Studio](using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="04978-246">USB를 통해 혼합 현실 장치에 배포</span><span class="sxs-lookup"><span data-stu-id="04978-246">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="04978-247">USB 케이블을 통해 장치가 연결 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-247">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="04978-248">**HoloLens의**경우 **로컬 컴퓨터** 단추 옆에 있는 화살표를 클릭 하 고 배포 대상을 **장치**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-248">**For HoloLens**, click on the arrow next to the **Local Machine** button, and change the deployment target to **Device**.</span></span>
2. <span data-ttu-id="04978-249">**PC에 연결 된 폐색 장치를 대상으로 지정**하려면 설정을 로컬 컴퓨터에 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-249">**For targeting occluded devices attached to your PC**, keep the setting to Local Machine.</span></span> <span data-ttu-id="04978-250">**혼합 현실 포털이** 실행 중인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-250">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="04978-251">**디버그 > 디버깅 하지 않고 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-251">Click **Debug > Start without debugging**.</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="04978-252">에뮬레이터에 배포</span><span class="sxs-lookup"><span data-stu-id="04978-252">Deploy to Emulator</span></span>

1. <span data-ttu-id="04978-253">**장치** 단추 옆의 화살표를 클릭 하 고 드롭다운에서 **HoloLens 에뮬레이터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-253">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator**.</span></span>
2. <span data-ttu-id="04978-254">**디버그 > 디버깅 하지 않고 시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04978-254">Click **Debug > Start without debugging**.</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="04978-255">앱 사용해 보기</span><span class="sxs-lookup"><span data-stu-id="04978-255">Try out your app</span></span>

<span data-ttu-id="04978-256">이제 앱이 배포 되었으므로 큐브를 모두 이동 하 여 전 세계에 유지 되는지 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="04978-256">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="04978-257">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04978-257">See also</span></span>

* [<span data-ttu-id="04978-258">Unity 개발 개요</span><span class="sxs-lookup"><span data-stu-id="04978-258">Unity development overview</span></span>](unity-development-overview.md)
* [<span data-ttu-id="04978-259">Unity 및 Visual Studio 사용 모범 사례</span><span class="sxs-lookup"><span data-stu-id="04978-259">Best practices for working with Unity and Visual Studio</span></span>](best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="04978-260">MR 기본 사항 101</span><span class="sxs-lookup"><span data-stu-id="04978-260">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="04978-261">MR 기본 사항 101E</span><span class="sxs-lookup"><span data-stu-id="04978-261">MR Basics 101E</span></span>](holograms-101e.md)
