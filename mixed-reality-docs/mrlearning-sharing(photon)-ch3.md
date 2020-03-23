---
title: 다중 사용자 기능 자습서 - 3. 여러 사용자 연결
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: cbe0d8d2db6c34ba262fe9c946b68366ed3dbb93
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031225"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="6622e-105">3. 여러 사용자 연결</span><span class="sxs-lookup"><span data-stu-id="6622e-105">3. Connecting multiple users</span></span>

<span data-ttu-id="6622e-106">이 단원에서는 라이브 공유 환경의 일부로 여러 사용자를 연결하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="6622e-107">이 단원이 완료되면 여러 디바이스에서 애플리케이션을 열고, 조인하는 각 사람에 대한 구로 표현된 아바타를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span>

## <a name="objectives"></a><span data-ttu-id="6622e-108">목표</span><span class="sxs-lookup"><span data-stu-id="6622e-108">Objectives</span></span>

* <span data-ttu-id="6622e-109">애플리케이션 내에서 PUN 구성</span><span class="sxs-lookup"><span data-stu-id="6622e-109">Configure PUN within your application</span></span>
* <span data-ttu-id="6622e-110">플레이어 구성</span><span class="sxs-lookup"><span data-stu-id="6622e-110">Configure players</span></span>
* <span data-ttu-id="6622e-111">공유 환경에서 여러 사용자를 연결하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="6622e-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="6622e-112">지침</span><span class="sxs-lookup"><span data-stu-id="6622e-112">Instructions</span></span>

1. <span data-ttu-id="6622e-113">[프로젝트] 패널의 Assets->Resources->Prefabs 폴더에서 아래 이미지와 같이 NetworkLobby 프리팹을 계층 구조로 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

    ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="6622e-115">NetworkLobby를 펼치면 NetworkRoom이라는 자식 개체가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="6622e-116">NetworkRoom을 선택한 상태에서 [검사기] 패널로 이동하여 [구성 요소 추가]를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="6622e-117">PhotonView를 검색하고 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-117">Search for PhotonView and add the component.</span></span>

    ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="6622e-119">새 빈 게임 개체를 계층 구조에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="6622e-120">마우스 오른쪽 단추로 계층 구조를 클릭하고, 컨텍스트 메뉴에서 [빈 개체]를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="6622e-121">위치 지정이 x =0, y=0, z=0으로 설정되어 있는지 확인하고 개체 이름을 PhotonUser로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

    ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="6622e-123">[구성 요소 추가]를 클릭하고, [일반 네트워크 동기화]를 입력합니다. [일반 네트워크 동기화] 클래스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="6622e-124">클래스가 표시되면 [사용자] 확인란을 클릭하여 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-124">When the class appears, click the User check box to turn it on.</span></span>

    ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="6622e-126">[구성 요소 추가]를 다시 클릭하고, [Photon 보기]를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="6622e-127">드롭다운 목록에 표시되는 [Photon 보기] 클래스를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-127">Select the Photon View class that appears in the drop-down list.</span></span>

    ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="6622e-129">[일반 네트워크 동기화] 클래스에 대한 [파일] 아이콘을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="6622e-130">[Photon 보기]의 [관찰된 구성 요소] 필드에 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-130">Drag and drop it in the Photon View's Observed Components field.</span></span>

    ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png)

7. <span data-ttu-id="6622e-132">다음으로, 공유 환경에 조인하는 각 사람을 나타내는 구를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="6622e-133">마우스 오른쪽 단추로 방금 만든 PhotonUser 개체를 클릭하고, "3D 개체"까지 아래로 스크롤한 다음, [구]를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="6622e-134">그러면 구 게임 개체가 PhotonUser 개체의 자식 항목으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

    ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="6622e-136">구의 크기를 x=0.06, y=0.06 및 z=0.06으로 축소합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

    ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="6622e-138">PhotonUser 게임 개체를 [프로젝트] 패널의 Prefabs 폴더로 끌어서 놓은 다음, 장면에서 이 개체를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="6622e-139">이제 공유 환경에서 새 플레이어를 생성하거나 인스턴스화할 때 사용할 수 있는 프리팹이 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

    ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

    >[!NOTE]
    ><span data-ttu-id="6622e-141">먼저 게임 개체가 Prefabs 폴더에 성공적으로 복사되었는지 확인한 후에 계층 구조에서 해당 개체를 삭제하세요.</span><span class="sxs-lookup"><span data-stu-id="6622e-141">Ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="6622e-142">3단계의 지침에 따라 계층 구조에서 새 개체를 만들고, SharedPlayground라는 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="6622e-143">그런 다음, [구성 요소 추가]를 클릭하고, 일반 네트워크 관리자를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="6622e-144">이 항목을 다시 클릭하여 [일반 네트워크 관리자] 구성 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="6622e-145">개체의 위치를 x=0, y=0 및 z=0으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)

## <a name="congratulations"></a><span data-ttu-id="6622e-147">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-147">Congratulations</span></span>

<span data-ttu-id="6622e-148">위의 모든 단계와 빌드 프로세스가 완료되면 [재생] 단추를 누르고 HoloLens 2를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="6622e-149">머리를 이동함에 따라 움직이는 구를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6622e-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="6622e-150">이는 Unity 프로젝트에 조인하는 모든 사용자에게 표시됩니다!</span><span class="sxs-lookup"><span data-stu-id="6622e-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="6622e-151">[다음 단원: 4. 여러 사용자와 개체 이동 공유](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="6622e-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>
