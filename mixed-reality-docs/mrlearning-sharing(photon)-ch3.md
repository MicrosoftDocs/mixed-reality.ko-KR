---
title: HoloLens 2에 대 한 모듈을 공유 학습 MR
description: HoloLens 2 응용 프로그램에서 다중 사용자 공유 환경을 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 4625acfcb3353e9537961a444012452139705359
ms.sourcegitcommit: 78e21e887bf4357c96c9ab2164559d610e8c041e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67465212"
---
# <a name="connecting-multiple-users"></a><span data-ttu-id="04a00-104">**여러 사용자를 연결합니다.**</span><span class="sxs-lookup"><span data-stu-id="04a00-104">**Connecting multiple users**</span></span> 

<span data-ttu-id="04a00-105">이 단원에서는 라이브를 공유 과정의 일부로 서 여러 사용자를 연결 하는 방법에 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-105">In this lesson, we learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="04a00-106">이 단원에서는 말 구, 조인 하는 각 사람의 표현 나타내는 아바타를 여러 장치에서 응용 프로그램을 열어 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-106">By the end of this lesson, you'll be able to open the application on multiple devices, and see avatar, represented by a sphere, representations of each person that joins.</span></span> 

<span data-ttu-id="04a00-107">목표:</span><span class="sxs-lookup"><span data-stu-id="04a00-107">Objectives:</span></span>

- <span data-ttu-id="04a00-108">예제 응용 프로그램 내에서 구성</span><span class="sxs-lookup"><span data-stu-id="04a00-108">Configure PUN within your application</span></span>
- <span data-ttu-id="04a00-109">플레이어를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-109">Configure players</span></span>
- <span data-ttu-id="04a00-110">공유 환경에서 여러 사용자를 연결 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="04a00-110">Learn how to connect multiple users in a shared experience</span></span>

### <a name="instructions"></a><span data-ttu-id="04a00-111">지침</span><span class="sxs-lookup"><span data-stu-id="04a00-111">Instructions</span></span>

1. <span data-ttu-id="04a00-112">자산-> 리소스-> [프로젝트] 패널에 Prefabs 폴더, 끌어서 놓기 계층 구조에서 NetworkLobby prefab 아래 이미지에 표시 된 대로 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-112">In the Assets->Resources->Prefabs folder in the Project panel, drag and drop the NetworkLobby prefab in to the hierarchy as shown in the image below.</span></span>


   ![Module3Chapter3step1im](images/module3chapter3step1im.PNG)

2. <span data-ttu-id="04a00-114">NetworkLobby를 확장 하면 NetworkRoom 라는 자식 개체를 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-114">When you expand NetworkLobby, you'll see a child object called NetworkRoom.</span></span> <span data-ttu-id="04a00-115">선택한 NetworkRoom를 사용 하 여 검사기 패널로 이동 하 고 구성 요소 추가 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-115">With NetworkRoom selected, go into the Inspector panel, and click Add Component.</span></span> <span data-ttu-id="04a00-116">PhotonView 검색 하 고 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-116">Search for PhotonView and add the component.</span></span>

   ![Module3Chapter3tep2im](images/module3chapter3step2im.PNG)

3. <span data-ttu-id="04a00-118">계층 구조에서 새 빈 게임 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-118">Create a new empty game object in the hierarchy.</span></span> <span data-ttu-id="04a00-119">계층을 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 빈을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-119">Right click in the hierarchy, and select Empty from the Context menu.</span></span> <span data-ttu-id="04a00-120">위치를 x로 설정 해야 = 0, y = 0, z = 0 및 PhotonUser 개체 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-120">Ensure the positioning is set to x =0, y=0, z=0 and name the object, PhotonUser.</span></span>

   ![Module3Chapter3step3im](images/module3chapter3step3im.PNG)

4. <span data-ttu-id="04a00-122">구성 요소 추가 클릭 하 고 제네릭 Net 동기화를 입력 합니다. Net 동기화 제네릭 클래스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-122">Click Add Component, and type Generic Net Sync. Select the Generic Net Sync class.</span></span> <span data-ttu-id="04a00-123">클래스에는 다음이 표시 되 면 설정 하려면 사용자 확인란을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-123">When the class appears, click on the User check box to turn it on.</span></span> 

   ![module3chapter3updateStep4im](images/module3chapter3updateStep4im.png)

5. <span data-ttu-id="04a00-125">추가 구성 요소를 다시 클릭 하 고 Photon 보기를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-125">Click on Add Component again, and type Photon View.</span></span> <span data-ttu-id="04a00-126">드롭다운 목록에 표시 되는 Photon 뷰 클래스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-126">Select the Photon View class that appears in the drop-down list.</span></span>

   ![module3chapter3updateStep5im](images/module3chapter3updateStep5im.png)

6. <span data-ttu-id="04a00-128">Net 동기화 제네릭 클래스에 대 한 파일 아이콘을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-128">Click the File icon for the Generic Net Sync class.</span></span> <span data-ttu-id="04a00-129">끌어서 Photon 보기의 관찰 된 구성 요소 필드에 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-129">Drag and drop it in the Photon View's Observed Components field.</span></span> ![module3chapter3updateStep6im.png](images/module3chapter3updateStep6im.png) 

7. <span data-ttu-id="04a00-131">그런 다음 공유 경험을 조인 하는 각 사용자를 나타내는 구 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-131">Next, we create spheres to represent each person that joins a shared experience.</span></span> <span data-ttu-id="04a00-132">방금 만든 PhotonUser 개체 및 scrolldown를 마우스 오른쪽 단추로 클릭 "하 고 3D 개체 타원 무늬입니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-132">Right click the PhotonUser object you just created, and scrolldown to "3D Object, and click Sphere.</span></span> <span data-ttu-id="04a00-133">이렇게 하면 구체 게임 개체를 PhotonUser 개체의 자식으로 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-133">This will create a sphere game object as a child of the PhotonUser object.</span></span>

   ![Module3Chapter3step4im](images/module3chapter3step4im.PNG)

8. <span data-ttu-id="04a00-135">X 아래로 구체 확장 0.06, = y 0.06, ad z = 0.06 =.</span><span class="sxs-lookup"><span data-stu-id="04a00-135">Scale the sphere down to x=0.06, y=0.06, ad z=0.06.</span></span>

   ![Module3hapter3step5im](images/module3chapter3step5im.PNG)

9. <span data-ttu-id="04a00-137">프로젝트 패널에서 Prefabs 폴더에 PhotonUser 게임 개체를 끌어서 장면에서 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-137">Drag the PhotonUser game object into the Prefabs folder in the Project panel, and then delete it from the scene.</span></span> <span data-ttu-id="04a00-138">생성 또는 공유 환경에서 새 플레이어를 인스턴스화할 때 사용할 수 있는 prefab 이제 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-138">We have now created a prefab that can be used when spawning or instantiating new players in a shared experience.</span></span>

   ![Module3Chapter3step6im](images/module3chapter3step6im.PNG)

> <span data-ttu-id="04a00-140">참고: 계층 구조에서 삭제 되기 전까지 게임 개체 Prefabs 폴더에 복사 성공적으로를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-140">Note: ensure that the game object has successfully copied into the Prefabs folder before deleting it from your hierarchy.</span></span>

10. <span data-ttu-id="04a00-141">3 단계의 지침에 따라 새 개체를 계층 구조에서 만들고 SharedPlayground 라는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-141">Create a new object in the hierarchy by following the instructions in Step 3, and name it SharedPlayground.</span></span> <span data-ttu-id="04a00-142">그런 다음 구성 요소 추가 클릭 일반 네트워크 관리자를 검색 하 고 클릭 하 여 일반 네트워크 관리자 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-142">Then, click Add Component, and search for generic network manager, and click it to add the Generic Network Manager component.</span></span> <span data-ttu-id="04a00-143">위치를 변경 합니다 개체의 x = 0, y = 0 및 z = 0.</span><span class="sxs-lookup"><span data-stu-id="04a00-143">Change the position of the object to x=0, y=0, and z =0.</span></span>

    ![Module3Chapter3step7im](images/module3chapter3step7im.PNG)


## <a name="congratulations"></a><span data-ttu-id="04a00-145">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-145">Congratulations</span></span>

<span data-ttu-id="04a00-146">위의 모든 단계를 완료 하 고 빌드 프로세스를 완료 이기도 play 단추를 누르고 HoloLens 2에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-146">Once all the steps above are complete, and the build process is also complete, press the play button and connect your HoloLens 2.</span></span> <span data-ttu-id="04a00-147">머리를 이동 하면 이동 구가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-147">You should see a sphere moving around as you move your head.</span></span> <span data-ttu-id="04a00-148">Unity 프로젝트를 조인 하는 모든 사용자에 대 한 내용이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04a00-148">This will be shown for any user that joins your Unity project!</span></span>

<span data-ttu-id="04a00-149">[다음 단원: Sharing(Photon) 단원 4](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="04a00-149">[Next Lesson: Sharing(Photon) Lesson 4](mrlearning-sharing(photon)-ch4.md)</span></span>

