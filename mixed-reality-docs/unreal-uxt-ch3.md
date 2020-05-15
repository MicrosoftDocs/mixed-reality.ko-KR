---
title: 3. 혼합 현실용 프로젝트 설정
description: Unreal Engine 4와 Mixed Reality Toolkit UX Tools 플러그인을 사용하여 간단한 체스 앱을 만드는 자습서의 3부
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, 자습서, 시작, mrtk, uxt, UX Tools, 설명서
ms.openlocfilehash: b5b5e2de787279602341e60f2bfa29aa05ea9b31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840622"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="ce26a-104">3. 혼합 현실용 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="ce26a-104">3. Setting up your project for mixed reality</span></span>

<span data-ttu-id="ce26a-105">이 섹션에서는 혼합 현실 개발용으로 앱을 구성하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-105">This section walks you through the process of configuring your app for mixed reality development.</span></span> 

## <a name="objectives"></a><span data-ttu-id="ce26a-106">목표</span><span class="sxs-lookup"><span data-stu-id="ce26a-106">Objectives</span></span>

* <span data-ttu-id="ce26a-107">ARSessionConfig, 폰 및 GameMode를 사용하여 혼합 현실 프로젝트를 설정하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="ce26a-107">Understand how to set up a mixed reality project with ARSessionConfig, Pawn, and GameMode</span></span>

## <a name="configure-the-session"></a><span data-ttu-id="ce26a-108">세션 구성</span><span class="sxs-lookup"><span data-stu-id="ce26a-108">Configure the Session</span></span>

1. <span data-ttu-id="ce26a-109">콘텐츠 브라우저에서 **Content** 폴더로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-109">In the Content Browser, navigate back to the **Content** folder.</span></span> <span data-ttu-id="ce26a-110">**새로 추가 > 기타 > 데이터 자산**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-110">Click **Add New > Miscellaneous > Data Asset**.</span></span> 

2. <span data-ttu-id="ce26a-111">**ARSessionConfig**를 클래스로 선택하고, **선택**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-111">Pick **ARSessionConfig** as the class and click **Select**.</span></span> <span data-ttu-id="ce26a-112">자산 이름을 "ARSessionConfig"로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-112">Name the asset “ARSessionConfig”.</span></span>

![데이터 자산 만들기](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="ce26a-114">ARSessionConfig를 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-114">Double click ARSessionConfig to open it.</span></span> <span data-ttu-id="ce26a-115">ARSessionConfig 데이터 자산에는 공간 매핑과 폐색을 포함하여 여러 가지 유용한 AR 설정이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-115">An ARSessionConfig data asset contains a number of useful AR settings including spatial mapping and occlusion.</span></span> <span data-ttu-id="ce26a-116">ARSessionConfig에 대한 자세한 내용은 [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html)에서 Unreal Engine 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce26a-116">For more details on ARSessionConfig, take a look at Unreal Engine’s documentation on [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span></span> <span data-ttu-id="ce26a-117">우리가 하고 있는 체스 앱은 설정을 수정할 필요가 없으므로 **저장**을 누르고 주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-117">For our chess app, we won’t need to modify any settings, so just hit **Save** and return to the Main window.</span></span> 

![AR 세션 구성](images/unreal-uxt/3-arsessionconfig.PNG)

4. <span data-ttu-id="ce26a-119">뷰포트 위에 있는 도구 모음에서 **청사진 > 레벨 청사진 열기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-119">On the toolbar above the viewport, click **Blueprints > Open Level Blueprint**.</span></span> <span data-ttu-id="ce26a-120">레벨 청사진은 레벨 수준에서 글로벌 이벤트 그래프 역할을 하는 특수한 청사진입니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-120">The Level Blueprint is a special Blueprint that acts as a level-wide global event graph.</span></span> <span data-ttu-id="ce26a-121">레벨의 처음부터 AR 세션 구성이 적용되도록 여기서 AR 세션을 시작하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-121">We’re going to start an AR session here, so that our AR session configuration is applied at the start of the level.</span></span>  

5. <span data-ttu-id="ce26a-122">**Event BeginPlay**에서 실행 노드를 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-122">Drag the execution node off **Event BeginPlay** and release.</span></span> <span data-ttu-id="ce26a-123">**AR 세션 시작** 노드를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-123">Search for the **Start AR Session** node.</span></span> <span data-ttu-id="ce26a-124">**세션 구성**을 클릭하고, 새로 만든 **ARSessionConfig** 자산을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-124">Click on **Session Config** and select your newly created **ARSessionConfig** asset.</span></span> <span data-ttu-id="ce26a-125">**컴파일**을 누른 다음, **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-125">Hit **Compile**, then **Save**.</span></span> <span data-ttu-id="ce26a-126">주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-126">Return to the Main window.</span></span>

![AR 세션 시작](images/unreal-uxt/3-startarsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="ce26a-128">폰 만들기</span><span class="sxs-lookup"><span data-stu-id="ce26a-128">Create a Pawn</span></span>

1.  <span data-ttu-id="ce26a-129">Content 폴더에 **DefaultPawn**에서 상속하는 새 청사진을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-129">In the Content folder, create a new Blueprint that inherits from **DefaultPawn**.</span></span> <span data-ttu-id="ce26a-130">Unreal에서 폰은 게임의 사용자(여기서는 HoloLens 2 환경)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-130">In Unreal, a Pawn represents the user in the game, or in this case, the HoloLens 2 experience.</span></span> <span data-ttu-id="ce26a-131">새 폰의 이름을 "MRPawn"으로 바꾸고 MRPawn을 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-131">Rename your new Pawn “MRPawn” and double click on MRPawn to open it.</span></span> 

![DefaultPawn에서 상속하는 새 폰 만들기](images/unreal-uxt/3-defaultpawn.PNG)

2.  <span data-ttu-id="ce26a-133">대부분의 Unreal 프로젝트에서 사용자가 제어하는 폰은 다른 구성 요소와 충돌하는 솔리드 개체이므로, 기본적으로 폰에는 메시 구성 요소와 충돌 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-133">By default, the Pawn has a mesh component and a collision component, since in most Unreal projects, Pawns controlled by the user are solid objects that collides with other components.</span></span> <span data-ttu-id="ce26a-134">여기서는 사용자가 폰이므로 충돌을 생성하지 않고 홀로그램을 통과할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-134">In this situation, since the user is the Pawn, we want to be able to pass through holograms without generating collisions.</span></span> <span data-ttu-id="ce26a-135">[구성 요소] 패널에서 **CollisionComponent**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-135">In the Components panel, select the **CollisionComponent**.</span></span> <span data-ttu-id="ce26a-136">[세부 정보] 패널에서 [충돌] 섹션까지 아래로 스크롤한 다음, [충돌 사전 설정] 옆에 있는 드롭다운을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-136">In the Details panel, scroll down to the Collision section and click the dropdown next to Collision Presets.</span></span> <span data-ttu-id="ce26a-137">이 설정을 [폰]에서 **NoCollision**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-137">Change this from Pawn to **NoCollision**.</span></span> <span data-ttu-id="ce26a-138">**MeshComponent**도 똑같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-138">Do the same for the **MeshComponent**.</span></span> <span data-ttu-id="ce26a-139">청사진을 **컴파일**한 다음, **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-139">**Compile**, then **Save** the Blueprint.</span></span> <span data-ttu-id="ce26a-140">주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-140">Return to the Main window.</span></span> 

![폰의 충돌 사전 설정 조정](images/unreal-uxt/3-nocollision.PNG)

## <a name="create-a-game-mode"></a><span data-ttu-id="ce26a-142">게임 모드 만들기</span><span class="sxs-lookup"><span data-stu-id="ce26a-142">Create a Game Mode</span></span>

1.  <span data-ttu-id="ce26a-143">콘텐츠 브라우저의 Content 폴더에서 부모가 **게임 모드 기본**인 새 청사진을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-143">In the Content folder in the Content Browser, create a new Blueprint with the parent **Game Mode Base**.</span></span> <span data-ttu-id="ce26a-144">이름을 MRGameMode로 지정하고 두 번 클릭하여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-144">Name it MRGameMode and double click to open.</span></span> <span data-ttu-id="ce26a-145">Unreal에서 게임 모드는 사용할 기본 폰을 포함하여 게임 또는 환경에 대한 여러 설정을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-145">In Unreal, the Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span> 

![콘텐츠 브라우저의 MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="ce26a-147">[세부 정보] 패널에서 [클래스] 섹션을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-147">In the Details panel, locate the Classes section.</span></span> <span data-ttu-id="ce26a-148">[기본 폰 클래스]를 DefaultPawn에서 방금 만든 **MRPawn**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-148">Change the Default Pawn Class from DefaultPawn to the **MRPawn** you just created.</span></span> <span data-ttu-id="ce26a-149">**컴파일**을 누른 다음, **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-149">Hit **Compile**, then **Save**.</span></span> <span data-ttu-id="ce26a-150">주 창으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-150">Return to the Main window.</span></span> 

![기본 폰 클래스 설정](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="ce26a-152">프로젝트 설정의 마지막 단계는 MRGameMode를 기본값으로 사용하라고 Unreal에 알리는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-152">The last step in setting up your project is to tell Unreal to default to MRGameMode.</span></span> <span data-ttu-id="ce26a-153">[프로젝트]에서 **편집 > 프로젝트 설정 > 맵 및 모드** 섹션으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-153">Go to **Edit > Projects Settings > Maps & Modes** (in the Projects) section.</span></span> <span data-ttu-id="ce26a-154">[기본 모드] 섹션에서 드롭다운을 클릭하고 **MRGameMode**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-154">In the Default Modes section, click the dropdown and choose **MRGameMode**.</span></span> <span data-ttu-id="ce26a-155">바로 아래에 있는 [기본 맵] 섹션에서 **EditorStartupMap** 및 **GameDefaultMap**을 **기본**으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-155">In the Default Maps section right below, change both the **EditorStartupMap** and the **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="ce26a-156">이렇게 하면 편집기를 닫았다가 다시 열 때 기본 맵이 기본적으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-156">This way when you close the editor and reopen it, the Main map will be selected by default.</span></span> <span data-ttu-id="ce26a-157">마찬가지로, 게임을 플레이할 때 기본 맵이 시작 레벨입니다.</span><span class="sxs-lookup"><span data-stu-id="ce26a-157">Similarly, when you play the game, the Main map will be the level that is started.</span></span> 

![프로젝트 설정 - 맵 및 모드](images/unreal-uxt/3-mapsandmodes.PNG)

[<span data-ttu-id="ce26a-159">다음 섹션: 4. 대화형 장면 만들기</span><span class="sxs-lookup"><span data-stu-id="ce26a-159">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)