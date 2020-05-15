---
title: 2. 프로젝트 및 첫 번째 애플리케이션 초기화
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그인을 사용하여 간단한 체스 앱을 만드는 자습서의 2부
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: fc85f011ff3b186f3b4b5449b4f8ec49f0b6418f
ms.sourcegitcommit: 189a47b8712dd5b620e19815f5cf6d1ac0f29880
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82851577"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="82b42-104">2. 프로젝트 및 첫 번째 애플리케이션 초기화</span><span class="sxs-lookup"><span data-stu-id="82b42-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="82b42-105">이 섹션에서는 HoloLens 2용 Unreal 애플리케이션을 새로 만드는 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-105">This section gets you started with creating a new Unreal application for HoloLens 2.</span></span> 

## <a name="objectives"></a><span data-ttu-id="82b42-106">목표</span><span class="sxs-lookup"><span data-stu-id="82b42-106">Objectives</span></span>

* <span data-ttu-id="82b42-107">HoloLens 개발용으로 Unreal 구성</span><span class="sxs-lookup"><span data-stu-id="82b42-107">Configure Unreal for HoloLens development</span></span>
* <span data-ttu-id="82b42-108">자산 가져오기 및 장면 설정</span><span class="sxs-lookup"><span data-stu-id="82b42-108">Import assets and set up the scene</span></span>

## <a name="create-a-new-unreal-project"></a><span data-ttu-id="82b42-109">새 Unreal 프로젝트 만들기</span><span class="sxs-lookup"><span data-stu-id="82b42-109">Create a new Unreal project</span></span>

1. <span data-ttu-id="82b42-110">Unreal Engine 실행</span><span class="sxs-lookup"><span data-stu-id="82b42-110">Launch Unreal Engine</span></span>

2. <span data-ttu-id="82b42-111">**새 프로젝트 범주**에서 **게임**을 선택하고 [다음]을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-111">Under **New Project Categories**, select **Games** and click Next.</span></span> <span data-ttu-id="82b42-112">**빈** 템플릿을 선택하고 [다음]을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-112">Select a **Blank** Template and click Next.</span></span> 

![빈 템플릿 선택](images/unreal-uxt/2-template.PNG)

3. <span data-ttu-id="82b42-114">[프로젝트 설정]에서 **C++, 확장 가능한 3D 또는 2D, 모바일/태블릿**을 선택하고, **시작 콘텐츠 없음**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-114">In Project Settings, choose **C++, Scalable 3D or 2D, Mobile / Tablet**, and **No Starter Content**.</span></span> <span data-ttu-id="82b42-115">프로젝트를 저장할 위치를 선택하고 **프로젝트 만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-115">Select a location for your project to be saved and click **Create Project**.</span></span> <span data-ttu-id="82b42-116">그러면 Visual Studio 프로젝트 및 Unreal 편집기에서 C++ 파일이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-116">This will open up your C++ files in a Visual Studio project and the Unreal editor.</span></span> 

![초기 프로젝트 설정](images/unreal-uxt/2-project-settings.PNG)

4. <span data-ttu-id="82b42-118">왼쪽 위 모서리에서 **편집 > 플러그 인**으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-118">In the top left-hand corner, go to **Edit > Plugins**.</span></span> <span data-ttu-id="82b42-119">[증강 현실]에서 확인란을 선택하여 **HoloLens** 플러그 인을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-119">Under Augmented Reality, check the box to enable the **HoloLens** plugin.</span></span> <span data-ttu-id="82b42-120">[가상 현실] 섹션까지 아래로 스크롤하고 확인란을 선택하여 **Microsoft Windows Mixed Reality** 플러그 인을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-120">Scroll down to the Virtual Reality section and check the box to enable the **Microsoft Windows Mixed Reality** plugin.</span></span> <span data-ttu-id="82b42-121">두 플러그 인은 HoloLens 2 개발에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-121">Both plugins are required for HoloLens 2 development.</span></span> <span data-ttu-id="82b42-122">편집기를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-122">Restart your editor.</span></span> 

![플러그 인](images/unreal-uxt/2-plugins.PNG)

5. <span data-ttu-id="82b42-124">왼쪽 위 모서리에서 **파일 > 새 레벨**로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-124">In the top left-hand corner, go to **File > New Level**.</span></span> <span data-ttu-id="82b42-125">**빈 레벨**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-125">Select **Empty Level**.</span></span> <span data-ttu-id="82b42-126">이제 뷰포트의 기본 장면이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-126">The default scene in the viewport should now be empty.</span></span>

6. <span data-ttu-id="82b42-127">[기본] 탭의 왼쪽에 있는 [모드] 패널에서 PlayerStart를 끌어다 놓습니다. 앱이 시작될 때 사용자가 원점에서 시작하도록, 오른쪽의 [세부 정보] 패널에서 위치를 X = 0, Y = 0, Z = 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-127">Drag PlayerStart and drop PlayerStart from the Modes panel on the left, located in the Basic tab. In the Details panel on the right, set the location to X = 0, Y = 0, Z = 0 in order to have the user start at the origin when the app stars.</span></span>

![PlayerStart를 사용하는 뷰포트](images/unreal-uxt/2-playerstart.PNG)

7. <span data-ttu-id="82b42-129">[모드] 패널의 [기본] 탭에서 **큐브**를 뷰포트로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-129">Drag a **Cube** from the Basic tab of the Modes panel into the viewport.</span></span> <span data-ttu-id="82b42-130">시작할 때 큐브가 플레이어와 50cm 떨어지도록, [세부 정보] 패널에서 위치를 X = 50, Y = 0, Z = 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-130">In the Details panel, set the location to X = 50, Y = 0, Z = 0 to set the cube to 50 cm away from the player at start time.</span></span> <span data-ttu-id="82b42-131">기본 큐브가 매우 크기 때문에 큐브 배율을 (0.2, 0.2, 0.2)로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-131">Since the default cube is quite large, change the Scale of the cube to (0.2, 0.2, 0.2).</span></span> 

8. <span data-ttu-id="82b42-132">장면에 조명을 추가하기 전에는 큐브를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-132">You won’t be able to see the cube unless you add a light to your scene.</span></span> <span data-ttu-id="82b42-133">[모드] 패널에서 **조명** 탭으로 전환하고, **방향성 광원**을 PlayerStart 위의 장면으로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-133">Switch to the **Lights** tab on the Modes panel and drag a **Directional Light** into the scene, above the PlayerStart.</span></span>

![조명이 추가된 뷰포트](images/unreal-uxt/2-light.PNG)

9.  <span data-ttu-id="82b42-135">도구 모음에서 **재생** 단추를 누르면 뷰포트에 큐브가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-135">Press the **Play** button on the toolbar to see your cube in the viewport!</span></span> <span data-ttu-id="82b42-136">**Esc** 키를 눌러 레벨을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-136">Press **Esc** to stop the level.</span></span> 

![뷰포트의 큐브](images/unreal-uxt/2-cube.PNG)

10. <span data-ttu-id="82b42-138">레벨을 저장하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-138">Let’s save your level.</span></span> <span data-ttu-id="82b42-139">왼쪽 위 모서리에서 **파일 > 현재 레벨 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-139">In the top left corner, click on **File > Save Current**.</span></span> <span data-ttu-id="82b42-140">레벨 이름을 "기본"으로 지정하고 **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-140">Name your level "Main" and click **Save**.</span></span> 

## <a name="set-up-a-chess-scene"></a><span data-ttu-id="82b42-141">체스 장면 설정</span><span class="sxs-lookup"><span data-stu-id="82b42-141">Set up a chess scene</span></span>

1. <span data-ttu-id="82b42-142">콘텐츠 브라우저에서 [새 항목 추가] 아래에 있는 아이콘을 클릭하여 소스 패널을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-142">In your Content Browser, click icon under Add New to show the sources panel.</span></span> <span data-ttu-id="82b42-143">그런 다음, **새 항목 추가 > 새 폴더**를 클릭하고 폴더 이름을 "ChessAssets"로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-143">Then click on **Add New > New Folder** and name the folder “ChessAssets”.</span></span> <span data-ttu-id="82b42-144">이 폴더를 두 번 클릭하여 내부로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-144">Double-click this folder to navigate in.</span></span> <span data-ttu-id="82b42-145">여기서는 체스 세트의 3D 자산을 가져오겠습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-145">This is where we’ll import the 3D assets for our chess set.</span></span>

![소스 패널 표시 또는 숨기기](images/unreal-uxt/2-showhidesources.PNG)

2. <span data-ttu-id="82b42-147">[GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z)에서 자산의 zip 파일을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-147">Download the zip file of assets from [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z).</span></span> <span data-ttu-id="82b42-148">이 파일에는 체스 보드와 체스 세트의 3D 모델이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-148">This file contains the 3D models for a chess board and chess set.</span></span> <span data-ttu-id="82b42-149">이 파일의 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-149">Unzip this file.</span></span>

3. <span data-ttu-id="82b42-150">콘텐츠 브라우저의 맨 위에서 **가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-150">At the top of the Content Browser, click on **Import**.</span></span> <span data-ttu-id="82b42-151">방금 압축을 푼 폴더로 이동하여 폴더 안에 있는 모든 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-151">Navigate to the folder that you just unzipped and select all the items within.</span></span> <span data-ttu-id="82b42-152">이 폴더에는 체스 보드와 체스 말의 3D 개체 메시인 FBX 파일, 그리고 체스 보드와 체스 말의 재질을 만드는 데 사용할 재질 맵인 TGA 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-152">This folder contains FBX files which are the 3D object meshes for our chess board and pieces, as well as TGA files which are the texture maps we’ll use to create materials for our board and pieces.</span></span> <span data-ttu-id="82b42-153">**열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-153">Click **Open**.</span></span> 

4. <span data-ttu-id="82b42-154">FBX 가져오기 옵션 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-154">An FBX Import Options window will pop up.</span></span> <span data-ttu-id="82b42-155">**재질** 섹션에서 **재질 가져오기 방법**을 **재질을 만들지 않음**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-155">In the **Material** section, change the **Material Import Method** to **Do Not Create Material**.</span></span> <span data-ttu-id="82b42-156">그런 다음, **모두 가져오기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-156">Then, click **Import All**.</span></span>

![FBX 옵션 가져오기](images/unreal-uxt/2-nocreatemat.PNG)

5. <span data-ttu-id="82b42-158">콘텐츠 폴더로 돌아가서 **Blueprints**라는 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-158">Back in your Content folder, create a new folder called **Blueprints**.</span></span> <span data-ttu-id="82b42-159">새로운 유형의 행위자 및 스크립트 수준 이벤트를 만들 수 있는 노드 기반 인터페이스를 제공하는 특수 자산인 청사진을 전부 이 폴더에 저장할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-159">This is where we will store all our blueprints, which are special assets that provide a node-based interface to create new types of Actors and script level events.</span></span> 

6. <span data-ttu-id="82b42-160">**Blueprints** 폴더를 두 번 클릭하여 내부로 이동한 다음, 콘텐츠 브라우저를 마우스 오른쪽 단추로 클릭하고, **청사진 클래스**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-160">Double click the **Blueprints** folder to navigate inside, then right click in your Content Browser and select **Blueprint Class**.</span></span> <span data-ttu-id="82b42-161">**행위자**를 클릭하고 새 청사진의 이름을 "Board"로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-161">Click on **Actor** and name the new blueprint “Board”.</span></span> <span data-ttu-id="82b42-162">Board를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-162">Double click Board to open it.</span></span> 

![청사진의 부모 클래스를 선택합니다.](images/unreal-uxt/2-bpparent.PNG)

![새 보드 청사진](images/unreal-uxt/2-bpboard.PNG)

7. <span data-ttu-id="82b42-165">청사진 편집기에서 [구성 요소] 패널로 이동하여 **구성 요소 추가 > 장면**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-165">In the Blueprint editor, navigate to the Components panel and click **Add Component > Scene**.</span></span> <span data-ttu-id="82b42-166">새로 만든 장면의 이름을 "Root"로 지정한 다음, DefaultSceneRoot 위로 Root를 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-166">Name the newly created scene “Root”, and then click and drag Root over the DefaultSceneRoot.</span></span> <span data-ttu-id="82b42-167">그러면 기본 장면 루트가 바뀌고 뷰포트의 구가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-167">This will replace the default scene root and get rid of the sphere in the viewport.</span></span> 

![루트 바꾸기](images/unreal-uxt/2-root.PNG)

8. <span data-ttu-id="82b42-169">**구성 요소 추가**를 다시 클릭하고, 이번에는 **정적 메시**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-169">Click **Add Component** again, and this time choose **Static Mesh**.</span></span> <span data-ttu-id="82b42-170">새 정적 메시의 이름을 "SM_Board"로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-170">Name the new static mesh “SM_Board”.</span></span> 

![정적 메시 추가](images/unreal-uxt/2-sm-board.PNG)

9. <span data-ttu-id="82b42-172">**세부 정보** 패널에서 **정적 메시** 섹션을 찾아 드롭다운을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-172">In the **Details** panel, locate the **Static Mesh** section and click the dropdown.</span></span> <span data-ttu-id="82b42-173">**ChessBoard**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-173">Select **ChessBoard**.</span></span> 

![뷰포트의 보드 메시](images/unreal-uxt/2-sm-board-view.PNG)

10. <span data-ttu-id="82b42-175">계속해서 **세부 정보** 패널에서 **재질** 섹션을 찾아 드롭다운을 클릭합니다,</span><span class="sxs-lookup"><span data-stu-id="82b42-175">Still in the **Details** panel, locate the **Materials** section and click the dropdown.</span></span> <span data-ttu-id="82b42-176">**새 자산 만들기**에서 **재질**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-176">Under **Create New Asset**, select **Material**.</span></span> <span data-ttu-id="82b42-177">이 자산의 이름을 **M_ChessBoard**로 지정하고 **ChessAssets** 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-177">Name this asset **M_ChessBoard** and save it in the **ChessAssets** folder.</span></span> 

![새 장면 만들기](images/unreal-uxt/2-newmat.PNG)

11. <span data-ttu-id="82b42-179">M_ChessBoard 드롭다운의 옆에 있는 사각형을 두 번 클릭하여 새로 만든 M_ChessBoard 재질을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-179">Double click the square next to M_ChessBoard dropdown to open your newly created M_ChessBoard material.</span></span> <span data-ttu-id="82b42-180">재질 편집기를 마우스 오른쪽 단추로 클릭하고 **텍스처 샘플** 노드를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-180">In the Material Editor, right click and search for the **Texture Sample** node.</span></span> <span data-ttu-id="82b42-181">**세부 정보** 패널의 **재질 식 텍스처 기본** 섹션에서 드롭다운을 클릭하고 **ChessBoard_Albedo**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-181">In the **Details** panel under the **Material Expression Texture Base** section, click the dropdown and select **ChessBoard_Albedo**.</span></span> <span data-ttu-id="82b42-182">마지막으로 **RGB** 출력 핀을 **M_ChessBoard**의 기본 색 핀으로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-182">Finally, drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![기본 색 설정](images/unreal-uxt/2-boardalbedomat.PNG)

12. <span data-ttu-id="82b42-184">같은 과정을 네 번 더 반복하여 **ChessBoard_AO** 텍스처 샘플을 **주변 폐색** 핀에 연결하고, **ChessBoard_Metal** 텍스처 샘플을 **금속** 핀에 연결하고, **ChessBoard_Normal** 텍스처 샘플을 **일반** 핀에 연결하고, **ChessBoard_Rough** 텍스처 샘플을 **거칠기** 핀에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-184">Do the same four more times, linking the **ChessBoard_AO** Texture Sample to the **Ambient Occlusion** pin, the **ChessBoard_Metal** Texture Sample to the **Metallic** pin, the **ChessBoard_Normal** Texture Sample to the **Normal** pin, and the **ChessBoard_Rough** Texture Sample to the **Roughness** pin.</span></span> <span data-ttu-id="82b42-185">**Save**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-185">Click **Save**.</span></span> 

![나머지 텍스처 연결](images/unreal-uxt/2-boardmat.PNG)

13. <span data-ttu-id="82b42-187">**Board** 청사진으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-187">Return to your **Board** Blueprint.</span></span> <span data-ttu-id="82b42-188">방금 만든 재질이 청사진에 적용된 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-188">You should see that the material you just created has been applied to your Blueprint.</span></span> <span data-ttu-id="82b42-189">보드를 화면에 배치할 때 보드의 크기와 위치가 적절하도록 보드의 **배율**을 (0.05, 0.05, 0.05)로 변경하고 **회전**을 Z = 90으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-189">To ensure the board is at a reasonable size and position once we place it in our scene, change the **Scale** of the board to (0.05, 0.05, 0.05) and the **Rotation** to Z = 90.</span></span> <span data-ttu-id="82b42-190">위쪽의 도구 모음에서 **컴파일**을 클릭한 다음, **저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-190">In the toolbar at the top, click **Compile**, then **Save**.</span></span> <span data-ttu-id="82b42-191">주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-191">Return to your Main window.</span></span> 

![재질이 적용된 체스 보드](images/unreal-uxt/2-chessboard.PNG)

14. <span data-ttu-id="82b42-193">이제 큐브를 삭제하고 새로 만든 Board 행위자로 바꾸겠습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-193">Let’s now delete the cube and replace it with your newly created Board actor.</span></span> <span data-ttu-id="82b42-194">**월드 아웃라이너**에서 마우스 오른쪽 단추로 **큐브 > 편집 > 삭제**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-194">In the **World Outliner**, right click your **Cube > Edit > Delete**.</span></span> <span data-ttu-id="82b42-195">콘텐츠 브라우저에서 Board를 뷰포트로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-195">Drag Board from your Content Browser into the viewport.</span></span> <span data-ttu-id="82b42-196">보드의 위치를 X = 80, Y = 0, Z =-20으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-196">Set the location of the board to X = 80, Y = 0, Z = -20.</span></span> 

15. <span data-ttu-id="82b42-197">**재생** 단추를 클릭하여 새 보드를 레벨에서 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-197">Click the **Play** button to view your new board in your level.</span></span> <span data-ttu-id="82b42-198">**Esc** 키를 눌러 편집기로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-198">Press **Esc** to return to the editor.</span></span> 

16. <span data-ttu-id="82b42-199">보드와 똑같은 단계를 따라 체스 말을 만들겠습니다. 이번에는 다음과 같이 체스 말의 메시와 재질을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-199">Now we’ll follow the same steps to create a chess piece as we did with the board, this time selecting the mesh and material for the chess piece:</span></span>

    <span data-ttu-id="82b42-200">a) 콘텐츠 브라우저에서 Blueprints 폴더로 이동하여 행위자 형식의 새 청사진 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-200">a) Navigate to the Blueprints folder in the Content Browser and create a new Blueprint class of type Actor.</span></span> <span data-ttu-id="82b42-201">이 행위자의 이름을 "WhiteKing"으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-201">Name this actor “WhiteKing”.</span></span>

    <span data-ttu-id="82b42-202">b) WhiteKing을 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-202">b) Double click WhiteKing to open it.</span></span> <span data-ttu-id="82b42-203">"Root"라는 새 장면 구성 요소를 추가하여 DefaultSceneRoot 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-203">Add a new Scene component named “Root” and use it to replace DefaultSceneRoot.</span></span> 

    <span data-ttu-id="82b42-204">c) "SM_King"이라는 새 정적 메시 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-204">c) Add a new Static Mesh component named “SM_King”.</span></span> <span data-ttu-id="82b42-205">[세부 정보] 패널에서 **정적 메시**를 **Chess_King**으로 설정하고, **재질**을 **M_ChessWhite**라는 새 재질로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-205">In the Details panel, set the **Static Mesh** to **Chess_King** and the **Material** to a new Material called **M_ChessWhite**.</span></span> 

    <span data-ttu-id="82b42-206">d) 새 **M_ChessWhite** 재질을 열고 관련 텍스처를 해당하는 재질 입력에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-206">d) Open the new **M_ChessWhite** Material and hook up the relevant textures to their corresponding material inputs.</span></span> 

    ![체스 킹 재질 만들기](images/unreal-uxt/2-chesskingmat.PNG)

    <span data-ttu-id="82b42-208">e) **WhiteKing** 청사진으로 돌아가서 **배율**을 (0.05, 0.05, 0.05)로 변경하고 **회전**을 Z = 90으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-208">e) Back in your **WhiteKing** Blueprint, change the **Scale** to (0.05, 0.05, 0.05) and **Rotation** to Z = 90.</span></span>

    <span data-ttu-id="82b42-209">f) 청사진을 컴파일하고 저장한 다음, 주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-209">f) Compile and save your blueprint, then navigate back to your main window.</span></span> 

17. <span data-ttu-id="82b42-210">WhiteKing을 뷰포트로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-210">Drag WhiteKing into your viewport.</span></span> <span data-ttu-id="82b42-211">WhiteKing이 Board의 자식이 되도록, **월드 아웃라이너**에서 WhiteKing을 Board로 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-211">In the **World Outliner**, drag WhiteKing onto Board so that WhiteKing is now a child of Board.</span></span> 

![월드 아웃라이너](images/unreal-uxt/2-child.PNG)

18. <span data-ttu-id="82b42-213">**세부 정보** 패널의 **변환**에서 WhiteKing의 **위치**를 X =-26, Y = 4, Z = 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-213">In the **Details** panel under **Transform**, set the **Location** of WhiteKing to X = -26, Y = 4, Z = 0</span></span>

19. <span data-ttu-id="82b42-214">**재생**을 클릭하여 레벨을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-214">Click **Play** to see your level.</span></span> <span data-ttu-id="82b42-215">**Esc** 키를 눌러 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="82b42-215">Press **Esc** to exit.</span></span> 

[<span data-ttu-id="82b42-216">다음 섹션: 3. 혼합 현실용 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="82b42-216">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)