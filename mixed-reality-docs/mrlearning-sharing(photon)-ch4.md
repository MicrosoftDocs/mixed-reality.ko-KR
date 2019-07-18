---
title: HoloLens 용 MR 학습 공유 모듈 2
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 3e4be00ddeab6d91dbbc8226bfa3dc543cded095
ms.sourcegitcommit: 611af6ff7a2412abad80c0c7d4decfc0c3a0e8c8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/17/2019
ms.locfileid: "68293698"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="a4fc9-104">4. 여러 사용자와 개체 이동 공유</span><span class="sxs-lookup"><span data-stu-id="a4fc9-104">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="a4fc9-105">이 자습서에서는 공유 세션의 모든 참가자가 함께 공동 작업 하 고 다른 사람의 상호 작용을 볼 수 있도록 개체의 움직임을 공유 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-105">In this Tutorial, we learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="a4fc9-106">이 단원에서는 [기본 모듈 자습서](mrlearning-base.md)의 일부로 작성 된 음력 시작 관리자를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="a4fc9-107">목표로</span><span class="sxs-lookup"><span data-stu-id="a4fc9-107">Objectives:</span></span>

- <span data-ttu-id="a4fc9-108">공유할 3D 모델로 음력 시작 관리자 가져오기</span><span class="sxs-lookup"><span data-stu-id="a4fc9-108">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="a4fc9-109">3D 모델의 움직임을 공유 하도록 프로젝트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="a4fc9-110">기본 다중 사용자 공동 작업 응용 프로그램을 빌드하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="a4fc9-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="a4fc9-111">지침</span><span class="sxs-lookup"><span data-stu-id="a4fc9-111">Instructions</span></span>


1. <span data-ttu-id="a4fc9-112">이전 단원 (컨트롤 + S)의 장면을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-112">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="a4fc9-113">필요할 때 더 쉽게 찾을 수 있도록 이름을 HLSharedProjectMainPart4으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-113">You can name it, HLSharedProjectMainPart4.unity, so that it's easier to find when you need it.</span></span>

2. <span data-ttu-id="a4fc9-114">프로젝트 창의 자산-> Scripts 폴더에서 GenericNetSync를 두 번 클릭 하 여 Visual Studio에서 열거나 사용 중인 코드 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-114">From the Project window, in the Assets->Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="a4fc9-116">34 줄과 38 줄에서이 단원에서 사용할 테이블의 코드를 활성화 하려면//를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-116">On Lines 34 and 38, remove the // to activate the code for the table that we will use in this lesson.</span></span> <span data-ttu-id="a4fc9-117">다음으로 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-117">next, Save the file.</span></span> 

![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="a4fc9-119">프로젝트 창의 자산-> Scripts 폴더에서 PhotonRoom.cs 파일을 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-119">In the Project window, double click on the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span> 

![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="a4fc9-121">3 단계와 마찬가지로 25, 26, 106 줄에서 코드를 활성화 하려면//를 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-121">Just like in Step 3, we need to remove the // to activate the code at Lines 25, 26, and 106.</span></span>

![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png) 

![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="a4fc9-124">계층 구조 보기에서 NetworkRoom 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-124">In the Hierarchy view, select the NetworkRoom object.</span></span>

![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="a4fc9-126">프로젝트 뷰에서 자산-> 리소스-> Prefabs로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-126">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="a4fc9-127">먼저 prefab 테이블을 PhotonRoom 클래스의 Tableprefab 슬롯으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-127">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="a4fc9-128">그런 다음 LunarModule prefab를 PhotonRoom 클래스의 모듈 Prefab 슬롯에 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-128">Next drag and drop the LunarModule prefab to the Module Prefab slot on the PhotonRoom class.</span></span>

![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

   <span data-ttu-id="a4fc9-130">참고: Prefab 개체와 릴리스 중 하나를 클릭 하면 검사기가 해당 개체로 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-130">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="a4fc9-131">각 개체를 적절 한 슬롯으로 클릭 하 고 끌어서 놓고 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-131">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="a4fc9-132">MixedRealityPlayspace 왼쪽에 있는 화살표를 클릭 하 고 자식 게임 개체인 MainCamera를 SharedPlayground로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-132">Click the arrow to the left of MixedRealityPlayspace, and move the child game object, MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="a4fc9-133">그런 다음 prefab, MixedRealityPlayspace를 삭제 하 고, prefab를 선택 하 고, 키보드에서 "삭제"를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-133">Next, delete the prefab, MixedRealityPlayspace, to delete, select the prefab, and tap "delete" on your keyboard).</span></span>
<span data-ttu-id="a4fc9-134">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span><span class="sxs-lookup"><span data-stu-id="a4fc9-134">![Module3hapter4step5im](images/module3chapter4step5im.PNG)</span></span>

><span data-ttu-id="a4fc9-135">참고:  주 카메라와 SharedPlayground 위치가 모두 0, 0, 0으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-135">Note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>
>

9. <span data-ttu-id="a4fc9-136">새 개체를 만들기 위해 SharedPlayground 부모 개체에 대 한 자식 개체로 설정 된 새 게임 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-136">Create a new game object set as a child object to the SharedPlayground parent object to create a new object.</span></span> <span data-ttu-id="a4fc9-137">부모 개체를 마우스 오른쪽 단추로 클릭 하 고 빈 만들기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-137">Right click on the parent object, and select Create Empty.</span></span> 

10. <span data-ttu-id="a4fc9-138">계층에서 새 개체를 선택한 상태에서 개체의 이름을 Inspector 패널의 TableAnchor로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-138">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="a4fc9-139">또한 구성 요소 추가를 클릭 하 고 TableAnchor 구성 요소를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-139">Also, click Add Component, and search for the TableAnchor component.</span></span> <span data-ttu-id="a4fc9-140">이를 선택 하 고 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-140">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="a4fc9-142">참고: 위치를 x = 1, y =-0.55 및 z = 2로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-142">Note: Set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="a4fc9-143">또한 회전을 y = 90으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-143">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="a4fc9-145">이제 Prefabs 폴더의 프로젝트 패널에서 prefab 테이블을 방금 만든 "TableAnchor" 자식 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-145">Now from the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)

12. <span data-ttu-id="a4fc9-147">마지막으로 DebugWindow 개체에서 너비를 50으로 변경 하 고 높이를 20으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-147">Finally, in the DebugWindow object, change the width to 50 and the height to 20.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)

## <a name="congratulations"></a><span data-ttu-id="a4fc9-149">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-149">Congratulations</span></span>


<span data-ttu-id="a4fc9-150">이 작업이 완료 되 면 Unity 프로젝트에 참여 하는 모든 사용자가 음력 시작 관리자를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-150">Once this is complete, all users that join your Unity project can move the lunar launcher around.</span></span> <span data-ttu-id="a4fc9-151">각 사용자가 다른 사람의 상호 작용을 볼 수 있도록 모든 이동이 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-151">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="a4fc9-152">이러한 개념은 모든 기능을 갖춘 공유 공동 작업 환경을 위한 기본 구성 요소로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-152">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span> 

<span data-ttu-id="a4fc9-153">모든 사용자가 공유 환경의 일부로 연결 되어 있고 개체의 상대 움직임을 볼 수 있지만, 로컬 사용자가 물리적 위치에서 같은 위치에 있는 개체와 개체를 볼 수 있도록 응용 프로그램은 아바타 및 개체를 정확 하 게 맞출 수 없습니다. world.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-153">Although all users are connected as part of a shared experience, and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="a4fc9-154">로컬 공유 환경을 고정 하기 위해 모든 장치에는 물리적 환경을 일반적으로 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-154">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="a4fc9-155">이 모듈에서는 다음 단원에서 구현 될 [Azure 공간 앵커](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (global.asa)를 사용 하 여이를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-155">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA) that will be implemented in the next lesson.</span></span>

<span data-ttu-id="a4fc9-156">다음 단원을 진행 하기 전에이를 공유 환경에 통합 하기 위해 필요한 기본 사항, Azure 계정 및 리소스 생성 및 기타 기본 빌딩 블록을 다루는 GLOBAL.ASA 학습 모듈을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4fc9-156">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="a4fc9-157">[다음 단원: 공유 (Photon) 단원 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="a4fc9-157">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

