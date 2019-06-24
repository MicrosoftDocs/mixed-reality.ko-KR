---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: f2e8cef618ea2fbee398ce19f1ba60b712b5fe3e
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67327473"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="94e80-104">**여러 사용자를 연결합니다.**</span><span class="sxs-lookup"><span data-stu-id="94e80-104">**Connecting Multiple Users**</span></span> 

<span data-ttu-id="94e80-105">이 단원에서는 라이브 공유 환경의 일부분으로 여러 사용자를 연결 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-105">In this lesson, we will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="94e80-106">이 단원을 마치면 수를 여러 장치에서 응용 프로그램을 열고 "아바타" 표현 (아바타 구로 표시 합니다.)를 조인 하는 각 사용자의를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="94e80-106">By the end of this lesson, you will be able to open the application on multiple devices, and see "avatar" representations of each person that joins (avatars represented by a sphere.)</span></span> 

<span data-ttu-id="94e80-107">목표:</span><span class="sxs-lookup"><span data-stu-id="94e80-107">Objectives:</span></span>

- <span data-ttu-id="94e80-108">예제 응용 프로그램 내에서 구성</span><span class="sxs-lookup"><span data-stu-id="94e80-108">Configure PUN within your application</span></span>
- <span data-ttu-id="94e80-109">플레이어를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-109">Configure players</span></span>
- <span data-ttu-id="94e80-110">공유 환경에서 여러 사용자를 연결 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="94e80-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="94e80-111">지침</span><span class="sxs-lookup"><span data-stu-id="94e80-111">Instructions</span></span>

1. <span data-ttu-id="94e80-112">자산에서 > 리소스 > Prefabs 폴더의 프로젝트 패널, 끌어서 놓기는 "NetworkLobby" 계층에 prefab에서 아래 이미지에 표시 된 대로 합니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-112">In the Assets>Resources>Prefabs folder of the project panel, drag and drop the "NetworkLobby" prefab in to the hierarchy, as shown in the image below.</span></span>


![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="94e80-114">"NetworkRoom." 라는 자식 개체를 prefab "NetworkLobby"를 확장 하면 표시</span><span class="sxs-lookup"><span data-stu-id="94e80-114">When you expand the prefab "NetworkLobby," you should see a child object called "NetworkRoom."</span></span> <span data-ttu-id="94e80-115">검사기 패널로 이동 하 고 "구성 요소를 추가 합니다."를 클릭 후 선택</span><span class="sxs-lookup"><span data-stu-id="94e80-115">With it selected, go into the inspector panel and click "Add Component."</span></span> <span data-ttu-id="94e80-116">"PhotonView"를 검색 하 고 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-116">Search for "PhotonView" and add the component.</span></span>

![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="94e80-118">계층 구조에서 새 빈 게임 개체를 만듭니다 (계층 구조에서 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 "비어 있음"을 선택).</span><span class="sxs-lookup"><span data-stu-id="94e80-118">Create a new empty game object in the hierarchy (right click in the hierarchy and select "Empty" from the context menu).</span></span> <span data-ttu-id="94e80-119">위치를 x로 설정 해야 = 0, y = 0, z = 0 및 "PhotonUser." 개체 이름</span><span class="sxs-lookup"><span data-stu-id="94e80-119">Ensure the positioning is set to x =0, y=0, z=0 and name the object, "PhotonUser."</span></span>

![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="94e80-121">그런 다음 공유 경험을 조인 하는 각 사용자를 나타내는 구 만들기 하고자 합니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-121">Next, we want to create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="94e80-122">방금 만든 "PhotonUser" 개체를 마우스 오른쪽 단추로 클릭, 이동 "3D 개체" 및 "타원 무늬."를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-122">Right click the "PhotonUser" object you just created, go down to "3D Object" and click "Sphere."</span></span> <span data-ttu-id="94e80-123">이렇게 하면 구체 게임 개체를 PhotonUser 개체의 자식으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-123">This will create a sphere game object as a child of the PhotonUser object.</span></span>

![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

5. <span data-ttu-id="94e80-125">X 아래로 구체 확장 0.06, = y 0.06, ad z = 0.06 =.</span><span class="sxs-lookup"><span data-stu-id="94e80-125">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

![Module3hapter3step5im](images/module3chapter3step5im.PNG)

6. <span data-ttu-id="94e80-127">프로젝트 패널에서 "prefabs" 폴더로 "PhotonUser" 게임 개체를 끕니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-127">Drag the "PhotonUser" game object into the "prefabs" folder in the project panel.</span></span> <span data-ttu-id="94e80-128">그런 다음 장면에서 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-128">Then, delete it from the scene.</span></span> <span data-ttu-id="94e80-129">생성 또는 공유 환경에서 새 플레이어를 인스턴스화할 때 사용할 prefab 이제 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-129">We have now created a prefab that will be used when spawning or instantiating new players in a shared experience.</span></span>

![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="94e80-131">참고: 계층 구조에서 삭제 되기 전까지 게임 개체에 "prefabs" 폴더에 성공적으로 복사 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-131">Note: ensure that the game object has successfully copied into the "prefabs" folder before deleting it from your hierarchy.</span></span>

7. <span data-ttu-id="94e80-132">(3 단계는 유사한 지침 사용), 계층 구조에 새 개체를 만들고 이름을 "SharedPlayground."</span><span class="sxs-lookup"><span data-stu-id="94e80-132">Create a new object in the hierarchy (using similar instructions to that of Step 3), and name it "SharedPlayground."</span></span> <span data-ttu-id="94e80-133">그런 다음 "구성 요소 추가" 및 "일반 네트워크 관리자"에 대 한 검색을 클릭 하 고 클릭 하 여 일반 네트워크 관리자 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-133">Then, click "Add Component" and search for "generic network manager" and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="94e80-134">위치를 변경 합니다 개체의 x = 0, y = 0 및 z = 0.</span><span class="sxs-lookup"><span data-stu-id="94e80-134">Change the position of the object to x=0, y=0, and z =0.</span></span>

![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="94e80-136">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-136">Congratulations</span></span>

<span data-ttu-id="94e80-137">위의 모든 단계를 완료 하 고 재생 단추를 누르고 HoloLens 2에 연결 하는 경우 빌드 프로세스는 완료 머리를 이동 하면 이동 구가 표시 됩니다!</span><span class="sxs-lookup"><span data-stu-id="94e80-137">Once all the steps above are complete, and the build process is complete, when you press the play button and connect your HoloLens 2, you should see a sphere moving around as you move your head!</span></span> <span data-ttu-id="94e80-138">Unity 프로젝트를 조인 하는 모든 사용자에 대 한 내용이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="94e80-138">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="94e80-139">[다음 단원: Sharing(Photon) 단원 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="94e80-139">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

