---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: d5bed61f5ffc1d3b4efed96f47c3568fbf3a2948
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67416014"
---
# <a name="synchronizing-the-movements-of-shared-objects"></a><span data-ttu-id="3e273-104">공유 개체의 움직임을 동기화</span><span class="sxs-lookup"><span data-stu-id="3e273-104">Synchronizing the Movements of Shared Objects</span></span>

<span data-ttu-id="3e273-105">이 단원에서는 공유 세션의 모든 참가자가 공동 작업 하 고 다른 사용자 상호 작용을 볼 수 있도록 개체의 움직임을 공유 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-105">In this lesson, we will learn how to share the movements of objects so that all participants of a shared session can collaborate together and view each others' interactions.</span></span> <span data-ttu-id="3e273-106">단원은의 일부로 만든 음력 시작 관리자에이 [자료 모듈 자습서](mrlearning-base.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-106">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

<span data-ttu-id="3e273-107">목표:</span><span class="sxs-lookup"><span data-stu-id="3e273-107">Objectives:</span></span>

- <span data-ttu-id="3e273-108">상태로 음력 시작 관리자에서 3D 모델을 공유할 수</span><span class="sxs-lookup"><span data-stu-id="3e273-108">Bring in the Lunar Launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="3e273-109">3D 모델의 움직임을 공유 하기 위해 프로젝트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-109">Configure your project to share the movements of the 3D model.</span></span>
- <span data-ttu-id="3e273-110">기본적인 다중 사용자 공동 작업 응용 프로그램을 빌드하는 방법을 알아봅니다</span><span class="sxs-lookup"><span data-stu-id="3e273-110">Learn how to build a basic multi-user collaborative application</span></span>

### <a name="instructions"></a><span data-ttu-id="3e273-111">지침</span><span class="sxs-lookup"><span data-stu-id="3e273-111">Instructions</span></span>

1. <span data-ttu-id="3e273-112">이전 단원 (control + S)에서 장면을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-112">Save the scene from the previous lesson (control+S).</span></span> <span data-ttu-id="3e273-113">쉽게 다시 필요할 때 찾을 수 있도록 "HLSharedProjectMainPart4.unity" 이름을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-113">You may name it "HLSharedProjectMainPart4.unity" so that it's easier to find when you need it again.</span></span>

2. <span data-ttu-id="3e273-114">자산에서 프로젝트 창에서 > Scripts 폴더에서 Visual Studio 또는 이전 코드에 사용 하는 편집기에서 엽니다 GenericNetSync 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-114">In the Project window, in the Assets > Scripts folder, double click on GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  ![](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="3e273-115">34 및 38 줄을 제거는 "/ /"이이 단원에서 사용 하는 테이블에 대 한 코드를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-115">On lines 34 and 38, remove the "//" to activate the code for the Table that we will use in this lesson.</span></span>  <span data-ttu-id="3e273-116">다음 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-116">Then Save the file.</span></span> ![](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="3e273-117">자산에서 PhotonRoom.cs 파일 프로젝트 창에서 두 번 클릭 > Scripts 폴더 다시 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-117">In the project window, double click on the PhotonRoom.cs file in the Assets > Scripts folder to again open it in Visual Studio.</span></span> ![](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="3e273-118">마찬가지로 3 단계에서 제거 해야 합니다 "/ /" 26, 25, 106 줄에서 코드를 활성화 합니다.![](images/module3chapter4updatestep5a.png)</span><span class="sxs-lookup"><span data-stu-id="3e273-118">Just like in step 3 we need to remove the "//" to activate the code at lines 25, 26, and 106.![](images/module3chapter4updatestep5a.png)</span></span> ![](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="3e273-119">계층 뷰에서 NetworkRoom 개체를 선택 합니다.![](images/module3chapter4updatestep6.png)</span><span class="sxs-lookup"><span data-stu-id="3e273-119">In the Hierarchy view, select the NetworkRoom object.![](images/module3chapter4updatestep6.png)</span></span>

7. <span data-ttu-id="3e273-120">프로젝트 보기에서 자산으로 이동 > 리소스 > Prefabs 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-120">In the project view, navigate to Assets > Resources > Prefabs.</span></span> <span data-ttu-id="3e273-121">먼저 끌어서 테이블 prefab PhotonRoom 클래스에서 "Tableprefab" 슬롯에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-121">First, drag and drop the Table prefab to the "Tableprefab" slot on the PhotonRoom class.</span></span> <span data-ttu-id="3e273-122">그런 다음 끌어서 놓기 LunarModule prefab PhotonRoom 클래스에서 "모듈 Prefab" 슬롯에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-122">Next drag and drop the LunarModule prefab to the "Module Prefab" slot on the PhotonRoom class.</span></span> ![](images/module3chapter4updatestep7.png)

   <span data-ttu-id="3e273-123">참고: Prefab 개체 및 릴리스 중 하나를 클릭 하면 검사기는 해당 개체에 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-123">Note: If you click on one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="3e273-124">클릭, 끌어서 놓거나 적절 한 해당 슬롯에 있는 각 개체를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-124">Click, drag, drop and release each object to its appropriate slot.</span></span>



8. <span data-ttu-id="3e273-125">이제 "MixedRealityPlayspace"의 왼쪽에 있는 화살표를 클릭 하 고 "SharedPlayground" prefab으로 자식 게임 개체를 "MainCamera" 아래로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-125">Now, click the arrow to the left of "MixedRealityPlayspace" and move the child game object, "MainCamera" down into the "SharedPlayground" prefab.</span></span> <span data-ttu-id="3e273-126">그런 다음 (삭제, 선택 하 여 prefab 키보드의 "삭제"를 탭) prefab "MixedRealityPlayspace"를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-126">Then, delete the prefab "MixedRealityPlayspace" (to delete, select the prefab and tap "delete" on your keyboard).</span></span>

![Module3hapter4step5im](images/module3chapter4step5im.PNG)

<span data-ttu-id="3e273-128">참고:  주 카메라와 SharedPlayground 위치 0,0,0에 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-128">note:  Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="3e273-129">자식 개체를 "SharedPlayground" 부모 개체 (새 개체를 만들고 부모 개체를 마우스 오른쪽 단추로 클릭 한 다음 "빈 항목 만들기"를 선택)로 새 게임 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-129">Create a new game object set as a child object to the "SharedPlayground" parent object (to create a new object, right click on the parent object, and select "create  empty").</span></span> 

10. <span data-ttu-id="3e273-130">계층에서 선택한 새 개체를 사용 하 여 "TableAnchor" 개체의 이름을 [관리자] 패널에서 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-130">With the new object selected in your hierarchy, change the name of the object to "TableAnchor" in the inspector panel.</span></span> <span data-ttu-id="3e273-131">또한 "구성 요소를 추가"를 클릭 하 고 "TableAnchor" 구성 요소에 대 한 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-131">Also, click "add component" and search for the "TableAnchor" component.</span></span> <span data-ttu-id="3e273-132">선택한 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-132">Select it and add it to the object.</span></span> 

![Module3Chapter4step6im](images/module3chapter4step7im.PNG)

> <span data-ttu-id="3e273-134">참고: x 위치 설정 = 1, y = 0.55 및 z = 2입니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-134">note: set the positioning to x=1, y=-0.55, and z=2.</span></span> <span data-ttu-id="3e273-135">또한 회전 y로 = 90입니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-135">Also, set the rotation to y=90.</span></span> 
>
> ![Module3Chapter4step6im](images/module3chapter4noteim.PNG)

11. <span data-ttu-id="3e273-137">이제 프로젝트 패널에서 "prefabs" 폴더에 끌어다 놓습니다 "table" prefab "TableAnchor" 자식 개체를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-137">Now in the project panel, in the "prefabs" folder, drag the "table" prefab into the "TableAnchor" child object you just created.</span></span>

![Module3Chapter4step8im](images/module3chapter4step8im.PNG)



12. <span data-ttu-id="3e273-139">마지막으로 "DebugWindow" 개체의 너비를 80 및 높이를 10으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-139">Finally, in the "DebugWindow" object, change the width to 80 and the height to 10.</span></span>

![Module3Chapter4step9im](images/module3chapter4step11im.PNG)




## <a name="congratulations"></a><span data-ttu-id="3e273-141">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-141">Congratulations</span></span>

<span data-ttu-id="3e273-142">완료 되 면 Unity 프로젝트를 조인 하는 모든 사용자 음력 시작 관리자를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-142">Once this is complete, all users that join your Unity project can move the Lunar Launcher around.</span></span> <span data-ttu-id="3e273-143">각 사용자는 다른 사용자 상호 작용을 볼 수 있도록 모든 움직임 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-143">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="3e273-144">이러한 개념 갖춘 공유 공동 작업 환경 위한 기본적인 빌딩 블록으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-144">These concepts serve as the foundational building blocks for full-featured shared collaboration experiences.</span></span> 

<span data-ttu-id="3e273-145">응용 프로그램은 정확 하 게 볼 수 있도록 로컬 서로 및 실제 내에서 같은 위치에 개체 아바타 및 개체를 정렬 하는 데 수 공유 환경의 일부분으로 연결 된 모든 사용자에 개체의 상대적인 움직임을 볼 수 있지만 전 세계입니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-145">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="3e273-146">로컬 공유 경험을 고정 하려면 모든 장치에 물리적 환경에 대 한 일반적인 이해에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-146">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="3e273-147">이 모듈에서는 이렇게 사용 하 여 [Azure 공간 앵커](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA)는 다음 단원에서 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-147">In this module, we will achieve this using [Azure Spatial Anchors](<https://azure.microsoft.com/en-us/services/spatial-anchors/>) (ASA), which will be implemented in the next lesson.</span></span>

<span data-ttu-id="3e273-148">다음 단원에 하기 전에 알아야 할 ASA에 필요한 Azure 계정 및 리소스 생성 및 다른 기본 빌딩 블록이 공유 경험에 통합 수 전에 ASA 학습 모듈을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e273-148">Before proceeding to the next lesson, we will need to complete the ASA Learning Module, which will cover ASA basics, Azure account and resource creation, and other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="3e273-149">[다음 단원: Sharing(Photon) 단원 5](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="3e273-149">[Next Lesson: Sharing(Photon) Lesson 5](mrlearning-sharing(photon)-ch5.md)</span></span>

