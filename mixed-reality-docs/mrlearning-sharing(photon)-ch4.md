---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 2a4ea599fd4887f30589c2d839be305d3dc8d1bd
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523198"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="e6876-104">4. 여러 사용자와 공유 개체 이동</span><span class="sxs-lookup"><span data-stu-id="e6876-104">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="e6876-105">이 자습서에서는 공유 세션의 모든 참가자가 공동 작업 하 고 다른 사용자 상호 작용을 볼 수 있도록 개체의 움직임을 공유 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-105">In this Tutorial, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="e6876-106">단원은의 일부로 만든 음력 시작 관리자에이 [자료 모듈 자습서](mrlearning-base.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="e6876-107">목표:</span><span class="sxs-lookup"><span data-stu-id="e6876-107">Objectives:</span></span>

- <span data-ttu-id="e6876-108">상태로 음력 시작 관리자에서 3D 모델을 공유할 수</span><span class="sxs-lookup"><span data-stu-id="e6876-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="e6876-109">3D 모델의 움직임을 공유 하기 위해 프로젝트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="e6876-110">기본적인 다중 사용자 공동 작업 응용 프로그램을 빌드하는 방법을 알아봅니다</span><span class="sxs-lookup"><span data-stu-id="e6876-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="e6876-111">지침</span><span class="sxs-lookup"><span data-stu-id="e6876-111">Instructions</span></span>


1. <span data-ttu-id="e6876-112">이전 단원 (Control + S)에서 장면을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="e6876-113">이름을 지정할 수 있습니다, HLSharedProjectMainPart4.unity, 쉽게 필요할 때 찾을 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-113">You can name it, HLSharedProjectMainPart4.unity, so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="e6876-114">프로젝트 창에서 자산-> Scripts 폴더에서 Visual Studio 또는 이전 코드에 사용 하는 편집기에서 엽니다 GenericNetSync를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="e6876-115">줄 34 및 38에서 제거는 / /이 단원에서 사용 하는 테이블에 대 한 코드를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-115">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="e6876-116">그런 다음 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-116">next, Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="e6876-117">프로젝트 창에서 자산에서 PhotonRoom.cs 파일을 두 번 클릭-> Visual Studio에서 열려는 스크립트 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-117">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="e6876-118">3 단계에서에서 제거 해야 하는 것 처럼는 / / 26, 25, 106 줄에서 코드를 활성화 합니다.![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="e6876-118">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="e6876-119">계층 뷰에서 NetworkRoom 개체를 선택 합니다.![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="e6876-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="e6876-120">이동할 프로젝트 보기에서 자산에는 리소스-> Prefabs-> 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-120">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="e6876-121">먼저 끌어서 테이블 prefab Tableprefab 슬롯 PhotonRoom 클래스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-121">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="e6876-122">그런 다음 끌어서 놓기 LunarModule prefab 모듈 Prefab 슬롯 PhotonRoom 클래스에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-122">Next drag and drop the LunarModule prefab to the Module Prefab slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="e6876-123">참고: Prefab 개체 및 릴리스 중 하나를 클릭 하면 검사기는 해당 개체에 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="e6876-124">클릭, 끌어서, drop 및 해당 슬롯에 있는 각 개체를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-124">Click, drag, drop, and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="e6876-125">MixedRealityPlayspace, 왼쪽에 있는 화살표를 클릭 하 고 SharedPlayground prefab으로 MainCamera 자식 게임 개체를 아래로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-125">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="e6876-126">삭제를 prefab을 선택 하 고 키보드에서 "삭제"를 탭 MixedRealityPlayspace prefab을 삭제할 어).</span><span class="sxs-lookup"><span data-stu-id="e6876-126">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="e6876-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="e6876-127">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

<span data-ttu-id="e6876-128">참고:  주 카메라와 SharedPlayground 위치 0,0,0에 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-128">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="e6876-129">새 개체를 만들려면 SharedPlayground 부모 개체에 자식 개체로 설정 하는 새 게임 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-129">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="e6876-130">부모 개체를 마우스 오른쪽 단추로 클릭 하 고 빈 항목 만들기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-130">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="e6876-131">계층에서 선택한 새 개체를 사용 하 여 TableAnchor 개체의 이름을 [관리자] 패널에서 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-131">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="e6876-132">또한 구성 요소 추가 클릭 하 고 TableAnchor 구성 요소를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-132">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="e6876-133">선택한 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-133">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="e6876-135">참고: X 위치 설정 = 1, y = 0.55 및 z = 2입니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-135">Note: Set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="e6876-136">또한 회전 y로 = 90입니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-136">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="e6876-138">이제 Prefabs 폴더에 [프로젝트] 패널에서 방금 만든 "TableAnchor" 자식 개체로 테이블 prefab을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-138">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="e6876-140">마지막으로, DebugWindow 개체에서 80 및 높이를 10으로 너비를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-140">Finally, in the DebugWindow object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="e6876-142">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-142">Congratulations</span></span>


<span data-ttu-id="e6876-143">완료 되 면 Unity 프로젝트를 조인 하는 모든 사용자 음력 시작 관리자를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-143">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="e6876-144">각 사용자는 다른 사용자 상호 작용을 볼 수 있도록 모든 움직임 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-144">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="e6876-145">이러한 개념 갖춘 공유 공동 작업 환경 위한 기본적인 빌딩 블록으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-145">These concepts serve as the foundational building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="e6876-146">응용 프로그램은 정확 하 게 아바타 및 개체를 정렬 하 여 실제 내에서 같은 위치에 개체 및 서로 참조 하는 로컬 사용자 수를 공유 과정의 일부로 서 연결 된 모든 사용자에 개체의 상대적인 움직임을 볼 수 있지만 전 세계입니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-146">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="e6876-147">로컬 공유 경험을 고정 하려면 모든 장치에 물리적 환경에 대 한 일반적인 이해에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-147">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="e6876-148">이 모듈에서는에서는에서는 이렇게 사용 하 여 [Azure 공간 앵커](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA)는 다음 단원에서 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-148">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="e6876-149">다음 단원 전에 다루는 ASA 기본 사항, Azure 계정 및 리소스 생성 및 다른 기본 빌딩 블록 필요한이 공유 경험에 통합 수 전에 ASA 학습 모듈을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6876-149">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="e6876-150">[다음 단원: Sharing(Photon) 단원 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="e6876-150">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

