---
title: MR Learning ASA 모듈 HoloLens 2 Azure 공간 앵커
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.openlocfilehash: 4dc36aec4d885fa75ea490446c2d682264049725
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326802"
---
# <a name="persistence-and-sharing-of-azure-spatial-anchors"></a><span data-ttu-id="1f5d0-104">지 속성 및 Azure 공간 앵커 공유</span><span class="sxs-lookup"><span data-stu-id="1f5d0-104">Persistence and Sharing of Azure Spatial Anchors</span></span>

<span data-ttu-id="1f5d0-105">이 단원에서는 HoloLens 2의 디스크에 우리의 앵커 정보를 저장 하 여 여러 앱 세션에서이 Azure 공간 앵커를 유지 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-105">In this lesson, we will learn how to persist our Azure Spatial Anchors across multiple app sessions by saving our anchor information to the HoloLens 2's disk.</span></span> <span data-ttu-id="1f5d0-106">또한 다중 장치 앵커 맞춤에 대 한 다른 장치에이 앵커 정보를 공유 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-106">We will also learn how to share this anchor information to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="1f5d0-107">목표</span><span class="sxs-lookup"><span data-stu-id="1f5d0-107">Objectives</span></span>

* <span data-ttu-id="1f5d0-108">저장 하 고 응용 프로그램 세션 간에 유지에 HoloLens 2 로컬 디스크에서 Azure 공간 앵커 정보를 검색 하는 방법을 알아봅니다</span><span class="sxs-lookup"><span data-stu-id="1f5d0-108">Learn how to save and retrieve Azure Spatial Anchor information from the HoloLens 2 local disk, for persistence between app sessions</span></span>

* <span data-ttu-id="1f5d0-109">다중 장치 시나리오에서 사용자 간에 Azure 공간 앵커 정보를 공유 하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="1f5d0-109">Learn how to share Azure Spatial Anchor information between users in a multi-device scenario</span></span>

  

## <a name="instructions"></a><span data-ttu-id="1f5d0-110">지침</span><span class="sxs-lookup"><span data-stu-id="1f5d0-110">Instructions</span></span>

### <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="1f5d0-111">디스크에 앵커 ID 저장-응용 프로그램 세션 간에 Azure 앵커를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-111">Persist Azure Anchors Between App Sessions - Save Anchor ID to Disk</span></span>

1. <span data-ttu-id="1f5d0-112">검색 하 고 "SaveAnchorToDisk" prefab 장면에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-112">Search for and add the "SaveAnchorToDisk" prefab to your scene.</span></span> <span data-ttu-id="1f5d0-113">여기에 두 개의 단추, HoloLens 2 디스크 및 디스크에서 모든 Id를 검색 하는 것에 대 한 다른 모든 사용 가능한 Azure 앵커 Id를 저장 하기 위한 단추가 하나 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-113">These include two buttons, one button for saving any available Azure Anchor IDs to the HoloLens 2 disk, and another for retrieving any IDs from the disk.</span></span>

   ![module2chapter2step1im](images/module2chapter2step1im.PNG)

2. <span data-ttu-id="1f5d0-115">아래 지침에 따라 각 단추 구성</span><span class="sxs-lookup"><span data-stu-id="1f5d0-115">Configure Each button according to the instructions below</span></span>
   - <span data-ttu-id="1f5d0-116">"SaveToDisk" 라는 단추의 "클릭" 이벤트 트리거 뿐만 아니라 "단추가 눌림" 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-116">For the Button named "SaveToDisk", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="1f5d0-117">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 SaveAzureAnchorIDToDisk() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-117">Drag the ParentAnchor object into the empty field, and assign the SaveAzureAnchorIDToDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>
   
     > <span data-ttu-id="1f5d0-118">참고: 다른 단추는 장면에서 겹치는 일부 단추가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-118">Note: some of the buttons may appear overlapping the other buttons in the scene.</span></span> <span data-ttu-id="1f5d0-119">자유롭게 단추의 위치를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-119">Feel free to adjust the button's positioning.</span></span>
   

  ![module2chapter2step2aim](images/module2chapter2step2aim.PNG)

![module2chapter2step2aim](images/module2chapter2step2bim.PNG)

![module2chapter2step2aim](images/module2chapter2step2cim.PNG)

   - <span data-ttu-id="1f5d0-123">"GetFromDisk" 라는 단추의 "클릭" 이벤트 트리거 뿐만 아니라 "단추가 눌림" 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-123">For the Button named "GetFromDisk", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="1f5d0-124">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 LoadAzureAnchorIDsFromDisk() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-124">Drag the ParentAnchor object into the empty field, and assign the LoadAzureAnchorIDsFromDisk() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="1f5d0-125">장치에 업데이트 된 응용 프로그램을 빌드하려면 1 단원에서에서 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-125">Follow the instructions from Lesson 1 to build the updated application to your device.</span></span> <span data-ttu-id="1f5d0-126">"Azure 앵커 만들기" 단추를 누르면 이전 단원에서와 같이 지금 저장 수 Azure 앵커 ID를 디스크에 저장 디스크 단추를 눌러 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-126">After pressing the "Create Azure Anchor" button, as you did in the previous lesson, you may now save the Azure Anchor ID to disk by pressing the save to disk button.</span></span>

4. <span data-ttu-id="1f5d0-127">응용 프로그램을 다시 시작, Azure 세션을 시작, "앵커 ID 로드" 단추 및 디스크에 저장 하는 ID와 연결 된 앵커를 찾으려고 "Azure 앵커 찾을" 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-127">Restart the application, start the Azure Session, Press the "Load Anchor ID" button, and then press the "Locate Azure Anchor" button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="1f5d0-128">장면 전체 이제 맞추려면 위치를 위치에 저장 앵커 이전!</span><span class="sxs-lookup"><span data-stu-id="1f5d0-128">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

### <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="1f5d0-129">여러 장치 간에 Azure 앵커를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-129">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="1f5d0-130">이 섹션에서는 여러 장치 간에 Azure 앵커 ID를 공유 하는 방법을 알아보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-130">In this section, we'll learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="1f5d0-131">이렇게 하면 Azure는 동일한 앵커 ID를 쿼리 하는 여러 장치는 고정된 홀로그램 및 백그라운드에서 부분적으로 정렬 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-131">This will allow multiple devices to query Azure for the same anchor ID, allowing our anchored holograms and scenes to be spatially aligned.</span></span> <span data-ttu-id="1f5d0-132">(여러 장치 간에 같은 물리적 위치에 동일한 홀로그램 표시) 하는 공간 맞춤은 HoloLens 2에서 공유 키를 로컬 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-132">Spatial alignment (seeing the same holograms in the same physical location between multiple devices) is key to local shared experiences in the HoloLens 2.</span></span> <span data-ttu-id="1f5d0-133">자습서는 Azure 공간 앵커 공유 환경에 설명 된 메서드를 포함 하 여 장치 간의 azure Id에 관한 정보를 전송 하는 방법은 여러 가지 (할 일: 링크를 추가 합니다.) 이 예제에서는 업로드 및 장치 간에 앵커 Id를 다운로드 하는 간단한 웹 서비스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-133">There are many ways to transfer information regarding azure IDs between devices, including methods outlined in the Azure Spatial Anchors shared experiences tutorials (TODO: add link.) This example uses a simple web service to upload and download Anchor IDs between devices.</span></span>

1. <span data-ttu-id="1f5d0-134">계층에 "ShareAnchor" prefab을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-134">Add the "ShareAnchor" prefab into your hierarchy.</span></span> <span data-ttu-id="1f5d0-135">이 prefab 장면;에 두 개의 새 단추를 추가합니다. 앵커 ID 정보 및 다운로드에 대 한 다른 업로드에 대 한 ID 정보를 고정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-135">This prefab adds two new buttons to your scene; one for uploading anchor ID information and another for downloading anchor ID information.</span></span> 

   ![module2chapter2step5im](images/module2chapter2step5im.PNG)

2. <span data-ttu-id="1f5d0-137">아래 지침에 따라 각 단추 구성</span><span class="sxs-lookup"><span data-stu-id="1f5d0-137">Configure Each button according to the instructions below</span></span>

   - <span data-ttu-id="1f5d0-138">"SendSharedAnchor" 라는 단추의 "클릭" 이벤트 트리거 뿐만 아니라 "단추가 눌림" 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-138">For the Button named "SendSharedAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="1f5d0-139">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 ShareAnchor() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-139">Drag the ParentAnchor object into the empty field, and assign the ShareAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

     ![module2chapter2step6aim](images/module2chapter2step6aim.PNG)

     ![module2chapter2step6bim](images/module2chapter2step6bim.PNG)

     

   - <span data-ttu-id="1f5d0-142">"GetSharedAnchor" 라는 단추의 "클릭" 이벤트 트리거 뿐만 아니라 "단추가 눌림" 이벤트 트리거 아래에서 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-142">For the Button named "GetSharedAnchor", create a new event under the "Button Pressed" event trigger as well as the "On Click" event trigger.</span></span> <span data-ttu-id="1f5d0-143">빈 필드를 끌어다 놓습니다 ParentAnchor 개체 하 고 ParentAnchor 개체의 ASAmoduleScript 구성 요소에서 GetSharedAzureAnchor() 메서드를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-143">Drag the ParentAnchor object into the empty field, and assign the GetSharedAzureAnchor() method from the ParentAnchor Object's ASAmoduleScript component.</span></span>

3. <span data-ttu-id="1f5d0-144">지침을 따릅니다 [1과](mrlearning-base-ch1.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-144">Follow the instructions from [Lesson 1](mrlearning-base-ch1.md).</span></span> <span data-ttu-id="1f5d0-145">장치에 업데이트 된 응용 프로그램을 빌드하려면.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-145">to build the updated application to your device.</span></span> <span data-ttu-id="1f5d0-146">"Azure 앵커 만들기" 단추를 누르면 이전 단원에서와 같이 공유할 수 있습니다 이제 다른 장치에 Azure 앵커 ID는 다른 장치에 공유 단추를 눌러.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-146">After pressing the "Create Azure Anchor" button, as you did in the previous lesson, you may now share the Azure Anchor ID to other devices by pressing the Share To Other Device button.</span></span>

   > <span data-ttu-id="1f5d0-147">참고: 선택 하 고 부모 앵커 부모 앵커 스크립트까지 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-147">Note: Select the parent anchor and scroll down to the parent anchor script.</span></span> <span data-ttu-id="1f5d0-148">공유 하는 본인을 공유 하면 알 수 있도록 "공용 공유 pin" 고유 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-148">Ensure that your "public sharing pin" is unique, so that when you share it, you know it is yours that you are sharing.</span></span> <span data-ttu-id="1f5d0-149">이렇게 하면 올바른 Azure 앵커를 공유 하는 확인 되므로 해당 Azure 앵커를 공유 하는 사용자 수천 개가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-149">There could be thousands of users sharing their Azure Anchors, so doing this will allow you to ensure you are sharing the correct Azure Anchors.</span></span>

4. <span data-ttu-id="1f5d0-150">다른 HoloLens 2 장치에 있는 경우 응용 프로그램을 시작 하 고 Azure 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-150">If you have another HoloLens 2 device, start the application and then start the Azure Session.</span></span> <span data-ttu-id="1f5d0-151">"공유 앵커 ID 가져오기" 단추를 누르고 디스크에 저장 하는 ID와 연결 된 앵커를 찾으려고 "Azure 앵커 찾을" 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-151">Press the "Get Shared Anchor ID" button, and then press the "Locate Azure Anchor" button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="1f5d0-152">장면 전체 위치에 이제 맞추려면 where에서 다른 HoloLens 2 장치에 배치 된 경우.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-152">The entire scene should now snap into position, at the where it was placed on the other HoloLens 2 device!</span></span> <span data-ttu-id="1f5d0-153">하나의 HoloLens 2에만 있는 경우 있습니다 아직 기능 테스트 응용 프로그램을 다시 시작 하 여 Azure 세션을 시작 및 "공유 앵커 ID 가져오기" 단추를 누릅니다. 하 연관 앵커를 찾으려고 "Azure 앵커 찾을" 단추를 누릅니다. 디스크에 저장 하는 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-153">If you only have one HoloLens 2, you may still test functionality by restarting the application, starting the Azure Session, and then Press the "Get Shared Anchor ID" button button, and then press the "Locate Azure Anchor" button to locate the anchor associated with the ID we saved to the disk.</span></span> <span data-ttu-id="1f5d0-154">장면 전체 이제 맞추려면 위치를 위치에 저장 앵커 이전!</span><span class="sxs-lookup"><span data-stu-id="1f5d0-154">The entire scene should now snap into position, at the location you saved the anchor previously!</span></span>

## <a name="congratulations"></a><span data-ttu-id="1f5d0-155">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-155">Congratulations</span></span>
<span data-ttu-id="1f5d0-156">이 단원의 HoloLens 2의 로컬 디스크에 Azure 공간 앵커 ID를 저장 하 여 앱 세션 및 앱 다시 시작 간의 Azure 공간 앵커를 유지 하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-156">In this Lesson you learned how to persist Azure Spatial Anchors between app sessions and app restarts by saving the Azure Spatial Anchor ID to the local disk of the HoloLens 2.</span></span> <span data-ttu-id="1f5d0-157">Azure 공간 앵커를 공유 하는 기본 다중 사용자, 정적 홀로그램 환경에 대 한 여러 장치 간에 공유 하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-157">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience!</span></span>

<span data-ttu-id="1f5d0-158">공유 모듈의 마지막 단원 중 완전 한 대화형 로컬 공유 환경의 일부분으로 Azure 공간 앵커를 구현 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-158">We will learn how to implement Azure Spatial Anchors as part of a fully interactive local shared experience during the final lesson of the Sharing Module.</span></span> <span data-ttu-id="1f5d0-159">로컬 공유 경험을 각 사용자에 대해 동기화 된 3D 개체 위치, 회전 및 비율, 식별자와 같은 기능이 포함 될 수 있습니다 및 응용 프로그램 상태를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-159">A local sharing experience may include functionality such as synchronized 3D object position, rotation, and scale, identifiers for each user, and shared application states.</span></span> <span data-ttu-id="1f5d0-160">각 참가자는 모든 사용자가 동일한 실제 위치에 있는 가상 개체를 일반적인 앵커를 제공 하 여 이러한 공유 시나리오를 개선 하는 azure 공간 앵커 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-160">Azure Spatial Anchors enhances these shared scenarios by providing each participant with a common anchor which allows all users to see virtual objects in the same physical location.</span></span> <span data-ttu-id="1f5d0-161">다양 한 장치 플랫폼, HoloLens, Android 및 iOS 장치를 비롯 한 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-161">This is true across a range of device platforms, including HoloLens, Android, and iOS devices.</span></span> <span data-ttu-id="1f5d0-162">공유 경험을 개발 하는 방법에 알아보려면 공유 모듈의 모든 단원을 완료 하세요.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-162">To learn how to develop a shared experience, please complete all lessons in the Sharing module.</span></span>

<span data-ttu-id="1f5d0-163">다음 단원에서는 실시간 피드백을 사용 하 여 사용자에 게 제공 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-163">In the next Lesson, we will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="1f5d0-164">이 피드백에는 앵커 생성, 환경 이해도 품질 및 Azure 세션 상태에 대 한 정보가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-164">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="1f5d0-165">피드백을 하지 않고 사용자가 모를 수 있습니다 앵커를 Azure에 업로드 했습니다. 되었는지 앵커 생성 또는 현재 상태에 대 한 충분 한 환경의 품질 인지.</span><span class="sxs-lookup"><span data-stu-id="1f5d0-165">Without feedback, users may not know whether an anchor has successfully been upload to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="1f5d0-166">다음 단원: ASA 단원 3</span><span class="sxs-lookup"><span data-stu-id="1f5d0-166">Next Lesson: ASA Lesson 3</span></span>](mrlearning-asa-ch3.md)

