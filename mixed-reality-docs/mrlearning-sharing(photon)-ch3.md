---
title: 다중 사용자 기능 자습서-3. 여러 사용자 연결
description: 이 과정을 완료 하 여 HoloLens 2 응용 프로그램 내에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보세요.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, Hololens
ms.openlocfilehash: a6d1a269f45b4aaf7cbd8fea948ddcbdf0bf18e2
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437738"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="d235b-105">3. 여러 사용자 연결</span><span class="sxs-lookup"><span data-stu-id="d235b-105">3. Connecting multiple users</span></span>

<span data-ttu-id="d235b-106">이 단원에서는 라이브 공유 환경의 일부로 여러 사용자를 연결 하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-106">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="d235b-107">이 단원을 마치면 여러 장치에서 응용 프로그램을 열고, 참가 하는 각 사용자에 대 한 구로 표시 된 아바타를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-107">By the end of this lesson, you'll be able to open the application on multiple devices and see the avatar, represented by a sphere for each person that joins.</span></span> 

<span data-ttu-id="d235b-108">목표로</span><span class="sxs-lookup"><span data-stu-id="d235b-108">Objectives:</span></span>

- <span data-ttu-id="d235b-109">응용 프로그램 내에서 THIS 구성</span><span class="sxs-lookup"><span data-stu-id="d235b-109">Configure PUN within your application</span></span>
- <span data-ttu-id="d235b-110">플레이어 구성</span><span class="sxs-lookup"><span data-stu-id="d235b-110">Configure players</span></span>
- <span data-ttu-id="d235b-111">공유 환경에서 여러 사용자를 연결 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="d235b-111">Learn how to connect multiple users in a shared experience</span></span>

## <a name="instructions"></a><span data-ttu-id="d235b-112">지침</span><span class="sxs-lookup"><span data-stu-id="d235b-112">Instructions</span></span>

1. <span data-ttu-id="d235b-113">프로젝트 패널의 자산-> 리소스-> Prefabs 폴더에서 아래 이미지와 같이 NetworkLobby prefab를 계층 구조로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-113">In the Assets->Resources->Prefabs folder of the Project panel, drag and drop the NetworkLobby prefab into the hierarchy as shown in the image below.</span></span>

![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="d235b-115">NetworkLobby를 확장 하면 Networklobby 이라는 자식 개체가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-115">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="d235b-116">NetworkRoom을 선택 하 고 검사기 패널로 이동 하 여 구성 요소 추가를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-116">With NetworkRoom selected, go into the Inspector panel and click Add Component.</span></span> <span data-ttu-id="d235b-117">PhotonView를 검색 하 고 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-117">Search for PhotonView and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="d235b-119">계층에 빈 게임 개체를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-119">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="d235b-120">계층 구조를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 비어 있음을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-120">Right-click in the hierarchy and select Empty from the Context menu.</span></span> <span data-ttu-id="d235b-121">위치 지정이 x = 0, y = 0, z = 0으로 설정 되어 있는지 확인 하 고 개체 이름을 PhotonUser로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-121">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="d235b-123">구성 요소 추가를 클릭 하 고 일반 네트워크 동기화를 입력 합니다. 일반 Net Sync 클래스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-123">Click Add Component and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="d235b-124">클래스가 표시 되 면 사용자 확인란을 클릭 하 여 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-124">When the class appears, click the User check box to turn it on.</span></span> 

![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="d235b-126">구성 요소 추가를 다시 클릭 하 고 Photon View를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-126">Click Add Component again, and type Photon View.</span></span> <span data-ttu-id="d235b-127">드롭다운 목록에 표시 되는 Photon View 클래스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-127">Select the Photon View class that appears in the drop-down list.</span></span>

![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="d235b-129">일반 네트워크 동기화 클래스에 대 한 파일 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-129">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="d235b-130">Photon 뷰의 관찰 된 구성 요소 필드에 끌어서 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-130">Drag and drop it in the Photon View's Observed Components field.</span></span> 

![module3chapter3updateStep6im](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="d235b-132">다음으로 공유 환경에 가입 하는 각 사람을 나타내는 구를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-132">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="d235b-133">방금 만든 PhotonUser 개체를 마우스 오른쪽 단추로 클릭 하 고 "3D 개체"로 스크롤한 다음 구를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-133">Right-click the PhotonUser object you just created, scroll-down to "3D Object and click Sphere.</span></span> <span data-ttu-id="d235b-134">그러면 구 게임 개체가 PhotonUser 개체의 자식으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-134">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="d235b-136">X = 0.06, y = 0.06, ad z = 0.06로 구를 축소 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-136">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="d235b-138">PhotonUser game 개체를 프로젝트 패널의 Prefabs 폴더로 끌어 장면에서 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-138">Drag the PhotonUser game object into the Prefabs folder in the Project panel and then delete it from the scene.</span></span> <span data-ttu-id="d235b-139">이제 공유 환경에서 새 플레이어를 생성 하거나 인스턴스화할 때 사용할 수 있는 prefab를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-139">You have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="d235b-141">참고: 게임 개체가 계층 구조에서 삭제 되기 전에 Prefabs 폴더에 성공적으로 복사 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-141">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="d235b-142">3 단계에서 설명 하는 지침에 따라 계층 구조에 새 개체를 만들고 이름을 SharedPlayground로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-142">Create a new object in the hierarchy by following the instructions in Step 3 and name it SharedPlayground.</span></span> <span data-ttu-id="d235b-143">그런 다음 구성 요소 추가를 클릭 하 고 일반 네트워크 관리자를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-143">Then, click Add Component and search for generic network manager.</span></span>  <span data-ttu-id="d235b-144">다시 클릭 하 여 일반 네트워크 관리자 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-144">Click it again to add the Generic Network Manager component.</span></span> <span data-ttu-id="d235b-145">개체의 위치를 x = 0, y = 0 및 z = 0으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-145">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="d235b-147">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-147">Congratulations</span></span>

<span data-ttu-id="d235b-148">위의 모든 단계를 완료 하 고 빌드 프로세스도 완료 되 면 재생 단추를 누르고 HoloLens 2를 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-148">Once all the steps above are complete and the build process is also complete, press the Play button and connect your HoloLens 2.</span></span> <span data-ttu-id="d235b-149">헤드를 이동 하면 구가 이동 하는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-149">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="d235b-150">Unity 프로젝트를 조인 하는 모든 사용자에 대해 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d235b-150">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="d235b-151">[다음 단원: 4. 여러 사용자와 개체 이동 공유](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="d235b-151">[Next Lesson: 4. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch4.md)</span></span>

