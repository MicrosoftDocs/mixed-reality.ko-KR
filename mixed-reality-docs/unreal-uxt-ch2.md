---
title: 2. 프로젝트 및 첫 번째 애플리케이션 초기화
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그 인을 사용하여 간단한 체스 앱을 만드는 자습서 시리즈 2/6부
author: hferrone
ms.author: v-haferr
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: 1fce9c34b1d31c56eb628979089399926f3cbf51
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376512"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="a86d5-104">2. 프로젝트 및 첫 번째 애플리케이션 초기화</span><span class="sxs-lookup"><span data-stu-id="a86d5-104">2. Initializing your project and first application</span></span>

## <a name="overview"></a><span data-ttu-id="a86d5-105">개요</span><span class="sxs-lookup"><span data-stu-id="a86d5-105">Overview</span></span>

<span data-ttu-id="a86d5-106">이 첫 번째 자습서에서는 HoloLens 2용 새 Unreal 애플리케이션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-106">In this first tutorial, you'll get started with a new Unreal application for HoloLens 2.</span></span> <span data-ttu-id="a86d5-107">여기에는 HoloLens 플러그 인 추가, 수준 만들기 및 조명, 게임 게시판과 체스 말로 채우기가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-107">This is going to include adding the HoloLens plugin, creating and lighting a level, and populating it with a game board and chess piece.</span></span> <span data-ttu-id="a86d5-108">3D 체스 말과 개체 재질용으로 미리 만들어진 자산을 사용하므로 처음부터 모든 것을 새롭게 모델링하는 것이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-108">You'll be using pre-made assets for the 3D chess piece and object materials, so don't worry about modeling anything from scratch.</span></span> <span data-ttu-id="a86d5-109">이 자습서의 끝 부분에서는 혼합 현실에 사용할 수 있는 빈 캔버스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-109">By the end of this tutorial you'll have a blank canvas that's ready for mixed reality.</span></span>

<span data-ttu-id="a86d5-110">계속하기 전에 [시작](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1) 페이지에서 모든 필수 구성 요소를 갖추었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-110">Before continuing, make sure you have all the prerequisites from the [Getting Started](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="a86d5-111">목표</span><span class="sxs-lookup"><span data-stu-id="a86d5-111">Objectives</span></span>
* <span data-ttu-id="a86d5-112">HoloLens 개발을 위한 Unreal 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="a86d5-112">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="a86d5-113">자산 가져오기 및 장면 설정</span><span class="sxs-lookup"><span data-stu-id="a86d5-113">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="a86d5-114">청사진을 사용하여 행위자 및 스크립트 수준 이벤트 만들기</span><span class="sxs-lookup"><span data-stu-id="a86d5-114">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="a86d5-115">새 Unreal 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="a86d5-115">Creating a new Unreal project</span></span>
<span data-ttu-id="a86d5-116">가장 먼저 필요한 것은 작업할 프로젝트입니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="a86d5-117">HoloLens용 Unreal 앱을 처음으로 만드는 경우 Epic Launcher에서 [지원 파일을 다운로드](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-117">If this is your first time creating an Unreal app for HoloLens, you'll need to [download supporting files](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch6#packaging-and-deploying-the-app) from the Epic Launcher.</span></span>

1. <span data-ttu-id="a86d5-118">Unreal Engine 실행</span><span class="sxs-lookup"><span data-stu-id="a86d5-118">Launch Unreal Engine</span></span>

2. <span data-ttu-id="a86d5-119">**새 프로젝트 범주**에서 **게임**을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-119">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![게임 프로젝트 템플릿 선택](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="a86d5-121">**빈** 템플릿을 선택하고 **다음**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-121">Select the **Blank** Template and click **Next**.</span></span> 

![빈 템플릿 선택](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="a86d5-123">**C++** , **확장 가능한 3D 또는 2D, 모바일/태블릿**을 선택하고 **프로젝트 설정**으로 **시작 콘텐츠 없음**을 선택한 다음, 저장 위치를 선택하고 **프로젝트 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-123">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**, then choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="a86d5-124">나중에 섹션 4에서 설정할 UX Tools 플러그 인을 빌드하려면 Blueprint 프로젝트 대신 C++ 프로젝트를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-124">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![초기 프로젝트 설정](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="a86d5-126">Unreal 편집기에서 프로젝트가 자동으로 열리므로, 다음 섹션에 대한 준비가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-126">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="a86d5-127">필수 플러그 인 사용</span><span class="sxs-lookup"><span data-stu-id="a86d5-127">Enabling required plugins</span></span>
<span data-ttu-id="a86d5-128">장면에 개체를 추가하려면 먼저 두 플러그 인을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-128">Before you start adding objects to the scene you'll need to enable two plugins.</span></span>

1. <span data-ttu-id="a86d5-129">**편집 > 플러그 인**을 열고 기본 제공 옵션 목록에서 **증강 현실**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-129">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="a86d5-130">**HoloLens**까지 아래로 스크롤하고 **사용**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-130">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![HoloLens 플러그 인 사용](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="a86d5-132">기본 제공 옵션 목록에서 **가상 현실**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-132">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="a86d5-133">**Microsoft Windows Mixed Reality**까지 아래로 스크롤하고, **사용**을 선택한 다음, 편집기를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-133">Scroll down to **Microsoft Windows Mixed Reality**, check **Enabled**, and restart your editor.</span></span> 

![Windows Mixed Reality 플러그 인 사용](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="a86d5-135">두 플러그 인은 HoloLens 2 개발에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-135">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="a86d5-136">작업이 완료되면 회사에 대한 빈 수준이 준비됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-136">With that done your empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="a86d5-137">수준 만들기</span><span class="sxs-lookup"><span data-stu-id="a86d5-137">Creating a level</span></span>
<span data-ttu-id="a86d5-138">다음 작업은 참조 및 규모에 대한 시작 지점과 큐브를 사용하여 간단한 플레이어 설정을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-138">Your next task is to create a simple player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="a86d5-139">**파일 > 새 수준**을 선택하고 **빈 수준**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-139">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="a86d5-140">이제 뷰포트의 기본 장면이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-140">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="a86d5-141">**모드** 탭에서 **기본**를 선택하고 장면으로 **PlayerStart**를 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-141">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="a86d5-142">**세부 정보** 탭에서 **위치**를 **X = 0**, **Y = 0** 및 **Z = 0**으로 설정합니다. 그러면 앱이 시작될 때 장면의 가운데에 사용자가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-142">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab. This sets the user at the center of the scene when the app starts up.</span></span>

![PlayerStart를 사용하는 뷰포트](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="a86d5-144">**기본** 탭에서 **큐브**를 장면으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-144">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="a86d5-145">**위치**를 **X = 50**, **Y = 0**, **Z = 0**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-145">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="a86d5-146">그러면 시작 시점에 큐브가 플레이어와 50cm 떨어져 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-146">This positions the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="a86d5-147">**배율**을 **X = 0.2**, **Y = 0.2**, **Z = 0.2**로 변경하여 큐브를 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-147">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="a86d5-148">장면을 테스트하기 전에 마지막으로 장면에 조명을 추가하지 않으면 큐브를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-148">You won’t be able to see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="a86d5-149">**모드** 패널에서 **조명** 탭으로 전환하고 **방향성 광원**을 장면으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-149">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="a86d5-150">**PlayerStart** 위에 조명을 배치하면 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-150">Position the light above **PlayerStart** so you can see it.</span></span>

![조명이 추가된 뷰포트](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="a86d5-152">**파일 > 현재 저장**으로 이동하고, 수준 이름을 **Main**으로 지정한 후 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-152">Go to **File > Save Current**, name your level **Main**, and click **Save**.</span></span> 

<span data-ttu-id="a86d5-153">장면 집합에서 도구 모음의 **재생**을 눌러 큐브의 작동을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-153">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="a86d5-154">작업을 감상한 후 **Esc**를 눌러 애플리케이션을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-154">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![뷰포트의 큐브](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="a86d5-156">이제 장면을 설정했으므로 체스 보드와 말에서 추가를 시작하여 애플리케이션 환경을 다듬어갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-156">Now that the scene is setup, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="a86d5-157">자산 가져오기</span><span class="sxs-lookup"><span data-stu-id="a86d5-157">Importing assets</span></span>
<span data-ttu-id="a86d5-158">이 때는 장면이 비어 있지만 미리 준비된 자산을 프로젝트로 가져오면 이 상황을 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-158">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="a86d5-159">[GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 자산 폴더를 다운로드하고 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-159">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder.</span></span>

2. <span data-ttu-id="a86d5-160">**콘텐츠 브라우저**에서 **새로 추가 > 새 폴더**를 클릭하고 이름을 **ChessAssets**로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-160">Click **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="a86d5-161">새 폴더를 두 번 클릭합니다. 여기가 3D 자산을 가져올 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-161">Double-click the new folder - this is where you'll import the 3D assets.</span></span>

![소스 패널 표시 또는 숨기기](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="a86d5-163">**콘텐츠 브라우저**에서 **가져오기**를 클릭하고 압축을 푼 자산 폴더의 모든 항목을 선택한 다음, **열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-163">Click **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="a86d5-164">이 폴더에는 FBX 형식의 체스 보드 및 말용 3D 개체 메시와, 재질에 사용할 TGA 형식의 질감 맵이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-164">This folder contains the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="a86d5-165">FBX 가져오기 옵션 창이 표시되면 **재질** 섹션을 확장하고 **재질 가져오기 메서드**를 **재질 생성 안 함**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-165">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="a86d5-166">**모두 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-166">Click **Import All**.</span></span>

![FBX 옵션 가져오기](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="a86d5-168">이제 자산 작업은 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-168">That's all you need to do for the assets.</span></span> <span data-ttu-id="a86d5-169">다음 작업 집합은 청사진을 사용하여 애플리케이션의 구성 요소를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-169">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="a86d5-170">청사진 추가</span><span class="sxs-lookup"><span data-stu-id="a86d5-170">Adding blueprints</span></span>

1. <span data-ttu-id="a86d5-171">**콘텐츠 브라우저**에서 **새로 추가 > 새 폴더**를 클릭하고 이름을 **Content Browser**로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-171">Click **Add New > New Folder** in the **Content Browser** and name it **Content Browser**.</span></span> 

> [!NOTE]
> <span data-ttu-id="a86d5-172">[청사진](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html)은 새로운 유형의 행위자 및 스크립트 수준 이벤트를 만들기 위한 노드 기반 인터페이스를 제공하는 특수 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-172">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="a86d5-173">**Blueprints** 폴더를 두 번 클릭한 다음, 마우스 오른쪽 단추를 클릭하여 **청사진 클래스**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-173">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="a86d5-174">**행위자**를 클릭하고 청사진의 이름을 **Board**로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-174">Select **Actor** and name the blueprint **Board**.</span></span> 

![청사진의 부모 클래스를 선택합니다.](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="a86d5-176">이제 새 **보드** 청사진이 다음 스크린샷에서처럼 **Blueprints** 폴더에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-176">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![새 보드 청사진](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="a86d5-178">만든 개체에 재질을 추가할 준비가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-178">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="a86d5-179">재질 작업</span><span class="sxs-lookup"><span data-stu-id="a86d5-179">Working with materials</span></span>
<span data-ttu-id="a86d5-180">사용자가 만든 개체는 기본적으로 회색으로 밋밋하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-180">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="a86d5-181">개체에 재질과 메시를 추가하는 작업이 이 자습서의 마지막 과제 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-181">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="a86d5-182">**보드**를 두 번 클릭하여 청사진 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-182">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="a86d5-183">**구성 요소** 패널에서 **구성 요소 추가 > 장면**을 클릭하고 이름을 **Root**로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-183">Click **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="a86d5-184">아래 스크린샷에는 **Root**가 **DefaultSceneRoot**의 자식으로 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-184">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![루트 바꾸기](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="a86d5-186">**Root**를 클릭하고 끌어서 **DefaultSceneRoot**에 놓아 바꾸고 뷰포트의 구를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-186">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![루트 바꾸기](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="a86d5-188">**구성 요소** 패널에서 **구성 요소 추가 > 정적 메시**를 클릭하고 이름을 **SM_Board**로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-188">Click **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="a86d5-189">**Root**에 자식 개체로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-189">It will appear as a child object under **Root**.</span></span>

![정적 메시 추가](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="a86d5-191">**SM_Board**를 클릭하고 **세부 정보** 패널의 **정적 메시** 섹션까지 아래로 스크롤한 다음, 드롭다운에서 **ChessBoard**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-191">Click **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![뷰포트의 보드 메시](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="a86d5-193">**세부 정보** 패널에서 **재질** 섹션을 확장하고 드롭다운 목록에서 **새 자산 만들기 > 재질**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-193">Still in the **Details** panel, expand the **Materials** section and click **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="a86d5-194">이 재질의 이름을 **M_ChessBoard**로 지정하고 **ChessAssets** 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-194">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![새 장면 만들기](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="a86d5-196">**M_ChessBoard** 재질 이미지를 두 번 클릭하여 재질 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-196">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![재질 편집기 열기](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="a86d5-198">재질 편집기를 마우스 오른쪽 단추로 클릭하고 **질감 샘플**을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-198">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="a86d5-199">**세부 정보** 패널의 **재질 식 질감 기본** 섹션에서 **질감**을 **ChessBoard_Albedo**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-199">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="a86d5-200">**RGB** 출력 핀을 **M_ChessBoard**의 기본 색 핀으로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-200">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![기본 색 설정](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="a86d5-202">다음 설정을 통해 이전 단계를 4번 더 반복하여 4개의 **질감 샘플** 노드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-202">Repeat the previous step four more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="a86d5-203">**질감**을 **ChessBoard_AO**로 설정하고 **RGB**를 **앰비언트 어클루전** 핀에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-203">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="a86d5-204">**질감**을 **ChessBoard_Metal**로 설정하고 **RGB**를 **메탈릭** 핀에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-204">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="a86d5-205">**질감**을 **ChessBoard_Normal**로 설정하고 **RGB**를 **기본** 핀에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-205">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="a86d5-206">**질감**을 **ChessBoard_Rough**로 설정하고 **RGB**를 **조도** 핀에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-206">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="a86d5-207">**Save**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-207">Click **Save**.</span></span> 

![나머지 텍스처 연결](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="a86d5-209">계속하기 전에 재질 설정이 위 스크린샷처럼 표시되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-209">Make sure the your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="a86d5-210">장면 채우기</span><span class="sxs-lookup"><span data-stu-id="a86d5-210">Populating the scene</span></span>
<span data-ttu-id="a86d5-211">**Board** 청사진으로 돌아가면 방금 만든 재질이 적용된 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-211">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="a86d5-212">이제 장면을 설정하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-212">All that's left is setting up the scene!</span></span> <span data-ttu-id="a86d5-213">먼저 다음과 같은 속성을 변경하여 보드가 장면에 배치될 때 올바른 크기와 정확한 각도가 되게 합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-213">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="a86d5-214">**배율**을 **(0.05, 0.05, 0.05)** , **Z 회전**을 **90**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-214">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="a86d5-215">상단 도구 모음에서 **컴파일**을 클릭한 다음, **저장**하고 주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-215">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![재질이 적용된 체스 보드](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="a86d5-217">**큐브 > 편집 > 삭제**를 마우스 오른쪽 단추로 클릭하고 **콘텐츠 브라우저**에서 **Board**를 뷰포트로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-217">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="a86d5-218">**위치**를 **X = 80**, **Y = 0**, **Z = -20**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-218">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="a86d5-219">**재생** 단추를 클릭하여 새 보드를 레벨에서 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-219">Click the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="a86d5-220">**Esc** 키를 눌러 편집기로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-220">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="a86d5-221">이제 보드에서 했던 것과 같은 단계를 따라 체스 말을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-221">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="a86d5-222">**Blueprints** 폴더로 이동하고 마우스 오른쪽 단추를 클릭하여 **청사진 클래스**와 **행위자**를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-222">Go to the **Blueprints** folder, right-click and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="a86d5-223">행위자의 이름을 **WhiteKing**으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-223">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="a86d5-224">**WhiteKing**을 두 번 클릭하여 청사진 편집기에서 열고 **구성 요소 추가 > 장면**을 클릭한 다음, 이름을 **Root**로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-224">Double click **WhiteKing** to open it in the Blueprint Editor, click **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="a86d5-225">**Root**를 끌어서 **DefaultSceneRoot**에 놓아 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-225">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="a86d5-226">**구성 요소 추가 > 정적 메시**를 클릭하고 이름을 **SM_King**으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-226">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="a86d5-227">세부 정보 창에서 **정적 메시**를 **Chess_King**으로, **재질**을 새 재질인 **M_ChessWhite**로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-227">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="a86d5-228">재질 편집기에서 **M_ChessWhite**을 열고 다음 **질감 샘플** 노드를 다음에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-228">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
    * <span data-ttu-id="a86d5-229">**질감**을 **ChessWhite_AO**로 설정하고 **RGB**를 **앰비언트 어클루전** 핀에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-229">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="a86d5-230">**질감**을 **ChessWhite_Metal**로 설정하고 **RGB**를 **메탈릭** 핀에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-230">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="a86d5-231">**질감**을 **ChessWhite_Normal**로 설정하고 **RGB**를 **기본** 핀에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-231">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="a86d5-232">**질감**을 **ChessWhite_Rough**로 설정하고 **RGB**를 **조도** 핀에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-232">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="a86d5-233">**Save**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-233">Click **Save**.</span></span> 

<span data-ttu-id="a86d5-234">계속하기 전에 **M_ChessKing** 재질이 다음 이미지와 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-234">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![체스 킹 재질 만들기](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="a86d5-236">거의 완료되었습니다. 새 체스 말을 장면에 추가하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-236">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="a86d5-237">**WhiteKing** 청사진으로 돌아가서 **배율**을 **(0.05, 0.05, 0.05)** , **Z 회전**을 **90**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-237">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="a86d5-238">청사진을 컴파일하고 저장한 다음, 주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-238">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="a86d5-239">**WhiteKing**을 뷰포트에 끌어오고 **World Outliner** 패널로 전환한 다음, **WhiteKing**을 **Board**로 끌어가 자식 개체로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-239">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![월드 아웃라이너](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="a86d5-241">**세부 정보** 패널의 **변환**에서 **WhiteKing**의 **위치**를 **X = -26**, **Y = 4**, **Z = 0**으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-241">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="a86d5-242">이제 마쳤습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-242">That's a wrap!</span></span> <span data-ttu-id="a86d5-243">**재생**를 클릭하여 입력된 수준의 작동을 확인하고 마무리되면 **Esc**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-243">Click **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="a86d5-244">이 자습서에서 다룬 내용은 간단한 프로젝트의 여러 기본적인 사항이지만 이제 프로젝트로 이 시리즈의 다음 부분인 혼합 현실 설정을 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a86d5-244">This tutorial covered a lot of ground creating a simple project, but your project is ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="a86d5-245">다음 섹션: 3. 혼합 현실용 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="a86d5-245">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)
