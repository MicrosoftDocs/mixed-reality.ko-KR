---
title: 다중 사용자 기능 자습서-4. 여러 사용자와 개체 이동 공유
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: 56f7c767323285453cbeea9034f97a7c14e92359
ms.sourcegitcommit: d73d9012941fa1b13eb7d2f45ccc481d6365827a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76885629"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="7caa5-105">4. 여러 사용자와 개체 이동 공유</span><span class="sxs-lookup"><span data-stu-id="7caa5-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="7caa5-106">이 자습서에서는 공유 세션의 모든 참가자가 공동 작업을 진행 하 고 서로의 상호 작용을 볼 수 있도록 개체의 움직임을 공유 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-106">In this Tutorial, you'll learn how to share the movements of objects so that all participants of a shared session can collaborate and view each others' interactions.</span></span> <span data-ttu-id="7caa5-107">이 단원에서는 [기본 모듈 자습서](mrlearning-base.md)의 일부로 작성 된 음력 시작 관리자를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-107">This lesson builds upon the Lunar Launcher that was built as part of the [Base Module Tutorials](mrlearning-base.md).</span></span>

## <a name="objectives"></a><span data-ttu-id="7caa5-108">목표</span><span class="sxs-lookup"><span data-stu-id="7caa5-108">Objectives</span></span>

- <span data-ttu-id="7caa5-109">공유할 3D 모델로 음력 시작 관리자 가져오기</span><span class="sxs-lookup"><span data-stu-id="7caa5-109">Bring in the lunar launcher as the 3D model to be shared</span></span>
- <span data-ttu-id="7caa5-110">3D 모델의 움직임을 공유 하도록 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="7caa5-110">Configure your project to share the movements of the 3D model</span></span>
- <span data-ttu-id="7caa5-111">기본 다중 사용자 공동 작업 응용 프로그램을 빌드하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="7caa5-111">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="instructions"></a><span data-ttu-id="7caa5-112">지침</span><span class="sxs-lookup"><span data-stu-id="7caa5-112">Instructions</span></span>

1. <span data-ttu-id="7caa5-113">이전 단원 (컨트롤 + S)의 장면을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-113">Save the scene from the previous lesson (Control+S).</span></span> <span data-ttu-id="7caa5-114">HLSharedProjectMainPart4에 이름을 지정할 수 있으므로 필요할 때 더 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-114">You can name it HLSharedProjectMainPart4.unity so it's easier to find when you need it.</span></span>

2. <span data-ttu-id="7caa5-115">프로젝트 창의 자산-> Scripts 폴더에서 GenericNetSync를 두 번 클릭 하 여 Visual Studio에서 열거나 사용 중인 코드 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-115">From the Project window, in the Assets->Scripts folder, double-click GenericNetSync to open it in Visual Studio or which ever code editor you are using.</span></span>  

    ![module3chapter4updatestep2](images/module3chapter4updatestep2.png)

3. <span data-ttu-id="7caa5-117">34 줄과 38 줄에서 "//"를 제거 하 여이 단원에서 사용할 테이블의 코드를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-117">On Lines 34 and 38, remove "//" to activate the code for the table that you will use in this lesson.</span></span> <span data-ttu-id="7caa5-118">다음으로 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-118">Next, save the file.</span></span>

    ![module3chapter4updatestep3](images/module3chapter4updatestep3.png)

4. <span data-ttu-id="7caa5-120">프로젝트 창의 자산-> Scripts 폴더에서 PhotonRoom.cs 파일을 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-120">In the Project window, double-click the PhotonRoom.cs file in the Assets->Scripts folder to open it in Visual Studio.</span></span>

    ![module3chapter4updatestep4](images/module3chapter4updatestep4.png)

5. <span data-ttu-id="7caa5-122">3 단계와 마찬가지로 25, 26, 106 줄에서 코드를 활성화 하려면 "//"를 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-122">Just like in Step 3, we need to remove "//" to activate the code at Lines 25, 26, and 106.</span></span>

    ![module3chapter4updatestep5a](images/module3chapter4updatestep5a.png)

    ![module3chapter4updatestep5b](images/module3chapter4updatestep5b.png)

6. <span data-ttu-id="7caa5-125">계층 구조 보기에서 NetworkRoom 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-125">In the Hierarchy view, select the NetworkRoom object.</span></span>

    ![module3chapter4updatestep6](images/module3chapter4updatestep6.png)

7. <span data-ttu-id="7caa5-127">프로젝트 뷰에서 자산-> 리소스-> Prefabs로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-127">In the Project view, navigate to Assets->Resources->Prefabs.</span></span> <span data-ttu-id="7caa5-128">먼저 prefab 테이블을 PhotonRoom 클래스의 Tableprefab 슬롯으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-128">First, drag and drop the Table prefab to the Tableprefab slot on the PhotonRoom class.</span></span> <span data-ttu-id="7caa5-129">그런 다음 RocketLauncherCompleteVariantprefab를 PhotonRoom 클래스의 Prefab slot 모듈에 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-129">Next, drag and drop the RocketLauncherCompleteVariantprefab to the Module Prefab slot on the PhotonRoom class.</span></span>

    ![module3chapter4updatestep7](images/module3chapter4updatestep7.png)

    >[!NOTE]
    ><span data-ttu-id="7caa5-131">Prefab 개체와 릴리스 중 하나를 클릭 하면 검사기가 해당 개체로 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-131">If you click one of the prefab objects and release, the inspector will switch to that object.</span></span> <span data-ttu-id="7caa5-132">각 개체를 적절 한 슬롯으로 클릭 하 고 끌어서 놓고 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-132">Click, drag, drop, and release each object to its appropriate slot.</span></span>

8. <span data-ttu-id="7caa5-133">MixedRealityPlayspace 왼쪽의 화살표를 클릭 하 고 자식 게임 개체 MainCamera를 SharedPlayground로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-133">Click the arrow to the left of MixedRealityPlayspace and move the child game object MainCamera down into the SharedPlayground prefab.</span></span> <span data-ttu-id="7caa5-134">그런 다음 prefab를 선택 하 고 키보드에서 "삭제"를 탭 하 여 prefab, MixedRealityPlayspace를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-134">Next, delete the prefab, MixedRealityPlayspace by selecting the prefab and tap "delete" on your keyboard).</span></span>

    ![Module3hapter4step5im](images/module3chapter4step5im.PNG)

    >[!NOTE]
    ><span data-ttu-id="7caa5-136">주 카메라와 SharedPlayground 위치가 모두 0, 0, 0으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-136">Make sure that both the Main Camera and SharedPlayground positions are set to 0,0,0.</span></span>

9. <span data-ttu-id="7caa5-137">"SharedPlayground" 개체를 선택 하 고 마우스 오른쪽 단추를 클릭 하 여 "빈 게임 개체를" SharedPlayground "게임 개체의 자식으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-137">Select "SharedPlayground" object and right click the mouse to choose "create empty" option to create an empty game object as a child of "SharedPlayground" game object.</span></span>

   ![Module3chapter4step6im](images/module3chapter4step6im.PNG)

10. <span data-ttu-id="7caa5-139">계층에서 새 개체를 선택한 상태에서 개체의 이름을 Inspector 패널의 TableAnchor로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-139">With the new object selected in your hierarchy, change the name of the object to TableAnchor in the Inspector panel.</span></span> <span data-ttu-id="7caa5-140">또한 구성 요소 추가를 클릭 하 고 TableAnchor 구성 요소를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-140">Also, click Add Component and search for the TableAnchor component.</span></span> <span data-ttu-id="7caa5-141">이를 선택 하 고 개체에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-141">Select it and add it to the object.</span></span>

    ![Module3Chapter4step7im](images/module3chapter4step7im.PNG)

11. <span data-ttu-id="7caa5-143">Prefabs 폴더의 프로젝트 패널에서 prefab 테이블을 방금 만든 "TableAnchor" 자식 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-143">From the Project panel in the Prefabs folder, drag the Table prefab into the "TableAnchor" child object that you just created.</span></span>

    ![Module3Chapter4step8im](images/module3chapter4step8im.PNG)
   
12. <span data-ttu-id="7caa5-145">자산-> 리소스-> Prefabs에서 "로켓 Launcher_Complete 변형" prefab을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-145">Open the "Rocket Launcher_Complete Variant" prefab from Assets->Resources->Prefabs.</span></span>

13. <span data-ttu-id="7caa5-146">"LunarModule" GameObject를 선택 하 고 다음 두 구성 요소인 "Photon Transform View" 및 "Photon View"를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-146">Select the "LunarModule" GameObject and add the following two components: "Photon Transform View" and "Photon View".</span></span>

14. <span data-ttu-id="7caa5-147">"LunarModule" GameObject를 선택한 상태에서 "Photon Transform View" 구성 요소를 "Photon View" 구성 요소의 "관찰 된 구성 요소" 슬롯으로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-147">With the "LunarModule" GameObject still selected, drag the "Photon Transform View" component into the "Observed Components" slot in the "Photon View" component.</span></span>

## <a name="congratulations"></a><span data-ttu-id="7caa5-148">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-148">Congratulations</span></span>

<span data-ttu-id="7caa5-149">이 작업이 완료 되 면 주위의 방법으로 음력 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-149">Once this is complete, look around to find the lunar module.</span></span> <span data-ttu-id="7caa5-150">그러면 Unity 프로젝트에 참여 하는 모든 사용자가 음력 시작 관리자를 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-150">After this, all users that join your Unity project can move the lunar launcher around.</span></span>  <span data-ttu-id="7caa5-151">각 사용자가 다른 사람의 상호 작용을 볼 수 있도록 모든 이동이 동기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-151">All movements are synchronized so that each user can see each others' interactions.</span></span> <span data-ttu-id="7caa5-152">이러한 개념은 모든 기능을 갖춘 공유 공동 작업 환경을 위한 기본 구성 요소로 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-152">These concepts serve as the fundamental building blocks for full-featured, shared collaboration experiences.</span></span>

<span data-ttu-id="7caa5-153">모든 사용자가 공유 환경의 일부로 연결 되어 있고 개체의 상대 움직임을 볼 수 있지만, 응용 프로그램은 로컬 사용자가 아바타 및 개체를 정확 하 게 맞출 수 없게 됩니다. 실제 세계.</span><span class="sxs-lookup"><span data-stu-id="7caa5-153">Although all users are connected as part of a shared experience and can see the relative movements of objects, the application is still unable to accurately align avatars and objects so that local users were not able see each other and objects in the same place within the physical world.</span></span> <span data-ttu-id="7caa5-154">로컬 공유 환경을 고정 하기 위해 모든 장치에는 물리적 환경을 일반적으로 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-154">In order to anchor a local shared experiences, every device requires a common understanding of the physical environment.</span></span> <span data-ttu-id="7caa5-155">이 모듈에서는 다음 단원에서 구현 될 [Azure 공간 앵커](<https://azure.microsoft.com//services/spatial-anchors/>) (global.asa)를 사용 하 여이를 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-155">In this module, we'll achieve this by using [Azure Spatial Anchors](<https://azure.microsoft.com//services/spatial-anchors/>) (ASA) which will be implemented in the next lesson.</span></span>

<span data-ttu-id="7caa5-156">다음 단원을 진행 하기 전에이를 공유 환경에 통합 하기 전에 필요한 다른 기본 빌딩 블록 뿐만 아니라, Azure 계정 및 리소스 만들기의 기본 사항에 대해 설명 하는 GLOBAL.ASA 학습 모듈을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caa5-156">Before proceeding to the next lesson, we'll need to complete the ASA Learning Module that covers ASA basics, Azure account and resource creation, as well as other fundamental buildings blocks required before we can integrate this into our shared experience.</span></span>

<span data-ttu-id="7caa5-157">[다음 단원: 5. 공유 환경에 Azure 공간 앵커 통합](mrlearning-sharing(photon)-ch5.md)</span><span class="sxs-lookup"><span data-stu-id="7caa5-157">[Next Lesson: 5. Integration Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch5.md)</span></span>
