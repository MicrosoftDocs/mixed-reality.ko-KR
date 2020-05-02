---
title: Azure Spatial Anchors 자습서 - 2. Azure Spatial Anchors 저장, 검색 및 공유
description: 이 과정을 완료하면 혼합 현실 애플리케이션 내에서 Azure 얼굴 인식을 구현하는 방법을 이해할 수 있습니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 36f25229469e848a3f0612a5971cc8e9381262f5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2020
ms.locfileid: "80362012"
---
# <a name="2-saving-retrieving-and-sharing-azure-spatial-anchors"></a><span data-ttu-id="509a7-105">2. Azure Spatial Anchors 저장, 검색 및 공유</span><span class="sxs-lookup"><span data-stu-id="509a7-105">2. Saving, retrieving, and sharing Azure Spatial Anchors</span></span>

<span data-ttu-id="509a7-106">이 자습서에서는 앵커 ID를 HoloLens 2의 스토리지에 저장하여 여러 앱 세션에서 Azure Spatial Anchors를 저장하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-106">In this tutorial, you will learn how to save Azure Spatial Anchors across multiple app sessions by saving the anchor ID to the HoloLens 2's storage.</span></span> <span data-ttu-id="509a7-107">또한 다중 디바이스 앵커 맞춤을 위해 이 앵커 ID를 다른 디바이스와 공유하는 방법에 대해서도 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-107">You will also learn how to share this anchor ID to other devices for a multi-device anchor alignment.</span></span>

## <a name="objectives"></a><span data-ttu-id="509a7-108">목표</span><span class="sxs-lookup"><span data-stu-id="509a7-108">Objectives</span></span>

* <span data-ttu-id="509a7-109">앱 세션 간의 지속성을 위해 HoloLens 2 로컬 디스크에서 Azure Spatial Anchor ID를 저장 및 검색하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="509a7-109">Learn how to save and retrieve Azure Spatial Anchor IDs to and from the HoloLens 2 local disk, for persistence between app sessions</span></span>
* <span data-ttu-id="509a7-110">다중 디바이스 시나리오에서 사용자 간에 Azure Spatial Anchor ID를 공유하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="509a7-110">Learn how to share Azure Spatial Anchor IDs between users in a multi-device scenario</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="509a7-111">장면 준비</span><span class="sxs-lookup"><span data-stu-id="509a7-111">Preparing the scene</span></span>

<span data-ttu-id="509a7-112">[프로젝트] 창에서 **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** 폴더로 차례로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-112">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder.</span></span> <span data-ttu-id="509a7-113">CTRL 단추를 누른 채 **ButtonParent_SaveAnchorId** 및 **ButtonParent_ShareAnchorId**를 클릭하여 두 개의 프리팹을 선택한 다음, [계층 구조] 창으로 끌어 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-113">While holding down the CTRL button, click on **ButtonParent_SaveAnchorId** and **ButtonParent_ShareAnchorId** to select the two prefabs, then drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section1-step1-1.png)

## <a name="persist-azure-anchors-between-app-sessions---save-anchor-id-to-disk"></a><span data-ttu-id="509a7-115">앱 세션 간 Azure 앵커 유지 - 디스크에 앵커 ID 저장</span><span class="sxs-lookup"><span data-stu-id="509a7-115">Persist Azure Anchors between app sessions - Save anchor ID to disk</span></span>
<!-- TODO: Consider renaming to 'Persist Azure Anchors between app sessions' -->

<span data-ttu-id="509a7-116">이 섹션에서는 Azure 앵커 ID를 HoloLens 2 로컬 디스크로 저장하고 가져오는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-116">In this section, you will learn how to save and retrieve the Azure Anchor ID to and from the HoloLens 2 local disk.</span></span> <span data-ttu-id="509a7-117">이렇게 하면 서로 다른 앱 세션 간에 동일한 앵커 ID를 Azure에 쿼리하여 고정된 홀로그램을 이전 앱 세션과 동일한 위치에 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-117">This will allow you to query Azure for the same anchor ID between different app sessions, allowing the anchored holograms to be position at the same location as in the previous app session.</span></span>

<span data-ttu-id="509a7-118">[계층 구조] 창에서 두 개의 단추가 포함된 **ButtonParent_SaveAnchorId** 개체를 펼칩니다. 하나는 Azure 앵커 ID를 HoloLens 2 스토리지에 저장하는 단추이고, 다른 하나는 디스크에서 저장된 ID를 검색하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-118">In the Hierarchy window, expand the **ButtonParent_SaveAnchorId** object which contains two buttons, one button for saving the Azure Anchor ID to the HoloLens 2 storage and another for retrieving the saved ID from the disk:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section2-step1-1.png)

<span data-ttu-id="509a7-120">이전 자습서의 [장면을 작동하도록 단추 구성](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) 지침과 동일한 단계를 수행하여 두 개의 단추 각각에 **누름 가능한 단추 HoloLens 2(스크립트)** 구성 요소 및 **Interactable(스크립트)** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-120">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="509a7-121">**SaveAzureAnchorIdToDisk** 개체에 대해 AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-121">For the **SaveAzureAnchorIdToDisk** object, assign the AnchorModuleScript > **SaveAzureAnchorIdToDisk ()** function.</span></span>
* <span data-ttu-id="509a7-122">**GetAzureAnchorIdFromDisk** 개체에 대해 AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-122">For the **GetAzureAnchorIdFromDisk** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromDisk ()** function.</span></span>

<span data-ttu-id="509a7-123">업데이트된 애플리케이션을 HoloLens에 빌드하는 경우 이제 Azure 앵커 ID를 저장하여 앱 세션 간에 Azure Spatial Anchors를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-123">If you build the updated application to your HoloLens, you can now persist Azure Spatial Anchors between app sessions by saving the Azure Anchor ID.</span></span> <span data-ttu-id="509a7-124">이를 테스트하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-124">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="509a7-125">로켓 발사대 환경을 원하는 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-125">Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="509a7-126">Azure 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-126">Start Azure Session.</span></span>
3. <span data-ttu-id="509a7-127">Azure Anchor를 만듭니다(앵커를 로켓 발사대 환경의 위치에 만듦).</span><span class="sxs-lookup"><span data-stu-id="509a7-127">Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="509a7-128">Azure 앵커 ID를 디스크에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-128">Save Azure Anchor ID to Disk.</span></span>
5. <span data-ttu-id="509a7-129">애플리케이션을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-129">Restart the application.</span></span>
6. <span data-ttu-id="509a7-130">디스크에서 Azure 앵커를 가져옵니다(방금 저장한 앵커 ID를 로드함).</span><span class="sxs-lookup"><span data-stu-id="509a7-130">Get Azure Anchor from Disk (loads the anchor ID you just saved).</span></span>
7. <span data-ttu-id="509a7-131">Azure 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-131">Start Azure Session.</span></span>
8. <span data-ttu-id="509a7-132">Azure 앵커를 찾습니다(로켓 발사대 환경을 3단계의 위치에 배치함).</span><span class="sxs-lookup"><span data-stu-id="509a7-132">Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

> [!NOTE]
> <span data-ttu-id="509a7-133">애플리케이션을 완전히 다시 시작하려면 몰입형 앱 보기를 종료한 후, 혼합 현실 홈의 앱 창을 닫고 [시작] 메뉴에서 애플리케이션을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-133">To fully restart the application, after exiting the immersive app view, the app window in the mixed reality home needs to be closed before relaunching the application from the Start menu.</span></span> <span data-ttu-id="509a7-134">자세한 내용은 [HoloLens에서 앱 사용](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens) 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="509a7-134">For additional details, you can refer to the [Using apps on HoloLens](https://docs.microsoft.com/hololens/holographic-home#using-apps-on-hololens) documentation.</span></span>

## <a name="share-azure-anchors-between-multiple-devices"></a><span data-ttu-id="509a7-135">여러 디바이스 간에 Azure 앵커 공유</span><span class="sxs-lookup"><span data-stu-id="509a7-135">Share Azure Anchors between multiple devices</span></span>

<span data-ttu-id="509a7-136">이 섹션에서는 여러 디바이스 간에 Azure 앵커 ID를 공유하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-136">In this section, you will learn how to share the Azure Anchor ID between multiple devices.</span></span> <span data-ttu-id="509a7-137">이렇게 하면 여러 디바이스에서 동일한 앵커 ID를 Azure에 쿼리하여 고정된 홀로그램을 공간적으로 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-137">This will allow multiple devices to query Azure for the same anchor ID, allowing the anchored holograms to be spatially aligned.</span></span> <span data-ttu-id="509a7-138">공간 맞춤, 즉 여러 디바이스 간에 동일한 실제 위치에서 동일한 홀로그램을 보는 것은 HoloLens 2에서 로컬 공유 환경의 핵심입니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-138">Spatial alignment, i.e. seeing the same holograms in the same physical location between multiple devices, is key to local shared experiences in the HoloLens 2.</span></span>

<span data-ttu-id="509a7-139">[다중 사용자 기능 자습서](mrlearning-sharing(photon)-ch1.md) 시리즈에서 설명하는 방법을 포함하여 디바이스 간에 Azure 앵커 ID를 전송하는 여러 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-139">There are many ways to transfer Azure Anchor IDs between devices, including methods outlined in the the [Multi-user capabilities tutorials](mrlearning-sharing(photon)-ch1.md) series.</span></span> <span data-ttu-id="509a7-140">이 예에서는 간단한 웹 서비스를 사용하여 디바이스 간에 앵커 ID를 업로드하고 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-140">In this example, you will use a simple web service to upload and download anchor IDs between devices.</span></span>

<span data-ttu-id="509a7-141">[계층 구조] 창에서 두 개의 단추가 포함된 **ButtonParent_ShareAnchorId** 개체를 펼칩니다. 하나는 Azure 앵커 ID를 웹 서버에 업로드하는 단추이고, 다른 하나는 웹 서버에서 ID를 다운로드하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-141">In the Hierarchy window, expand the **ButtonParent_ShareAnchorId** object which contains two buttons; one button for uploading the Azure Anchor ID to the web server, and another for downloading the ID from the web server:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial2-section3-step1-1.png)

<span data-ttu-id="509a7-143">이전 자습서의 [장면을 작동하도록 단추 구성](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) 지침과 동일한 단계를 수행하여 두 개의 단추 각각에 **누름 가능한 단추 HoloLens 2(스크립트)** 구성 요소 및 **Interactable(스크립트)** 구성 요소를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-143">Follow the same steps as in the [configuring the buttons to operate the scene](mrlearning-asa-ch1.md#configuring-the-buttons-to-operate-the-scene) instructions from the previous tutorial to configure the **Pressable Button Holo Lens 2 (Script)** component and the **Interactable (Script)** component on each of the two buttons:</span></span>

* <span data-ttu-id="509a7-144">**ShareAzureAnchorIdToNetwork** 개체에 대해 AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-144">For the **ShareAzureAnchorIdToNetwork** object, assign the AnchorModuleScript > **ShareAzureAnchorIdToNetwork ()** function.</span></span>
* <span data-ttu-id="509a7-145">**GetAzureAnchorIdFromNetwork** 개체에 대해 AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** 함수를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-145">For the **GetAzureAnchorIdFromNetwork** object, assign the AnchorModuleScript > **GetAzureAnchorIdFromNetwork ()** function.</span></span>

<span data-ttu-id="509a7-146">업데이트된 애플리케이션을 두 개의 HoloLens 디바이스에 빌드하는 경우 이제 Azure 앵커 ID를 공유하여 두 디바이스 간에 공간을 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-146">If you build the updated application to two HoloLens devices, you can now achieve spatial alignment between them by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="509a7-147">이를 테스트하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-147">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="509a7-148">HoloLens 디바이스 1: 로켓 발사대 환경을 원하는 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-148">On HoloLens device 1: Move the Rocket Launcher experience to desired location.</span></span>
2. <span data-ttu-id="509a7-149">HoloLens 디바이스 1: Azure 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-149">On HoloLens device 1: Start Azure Session.</span></span>
3. <span data-ttu-id="509a7-150">HoloLens 디바이스 1: Azure Anchor를 만듭니다(앵커를 로켓 발사대 환경의 위치에 만듦).</span><span class="sxs-lookup"><span data-stu-id="509a7-150">On HoloLens device 1: Create Azure Anchor (creates anchors at the location of the Rocket Launcher experience).</span></span>
4. <span data-ttu-id="509a7-151">HoloLens 디바이스 1: Azure 앵커 ID를 네트워크에 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-151">On HoloLens device 1: Share Azure Anchor ID to Network.</span></span>
5. <span data-ttu-id="509a7-152">HoloLens 디바이스 2: 애플리케이션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-152">On HoloLens device 2: Start the application.</span></span>
6. <span data-ttu-id="509a7-153">HoloLens 디바이스 2: 네트워크에서 공유 앵커 ID를 가져옵니다(HoloLens 디바이스 1에서 방금 공유한 앵커 ID를 가져옴).</span><span class="sxs-lookup"><span data-stu-id="509a7-153">On HoloLens device 2: Get Shared Anchor ID from Network (fetches the anchor ID just shared from HoloLens device 1).</span></span>
7. <span data-ttu-id="509a7-154">HoloLens 디바이스 2: Azure 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-154">On HoloLens device 2: Start Azure Session.</span></span>
8. <span data-ttu-id="509a7-155">HoloLens 디바이스 2: Azure 앵커를 찾습니다(로켓 발사대 환경을 3단계의 위치에 배치함).</span><span class="sxs-lookup"><span data-stu-id="509a7-155">On HoloLens device 2: Find Azure Anchor (positions the Rocket Launcher experience at the location from step 3).</span></span>

> [!TIP]
> <span data-ttu-id="509a7-156">하나의 HoloLens만 있는 경우에도 두 번째 HoloLens 디바이스를 사용하는 대신 애플리케이션을 다시 시작하여 기능을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-156">If you only have one HoloLens, you can still test the functionality by restarting the application instead of using a second HoloLens device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="509a7-157">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-157">Congratulations</span></span>

<span data-ttu-id="509a7-158">이 자습서에서는 Azure Spatial Anchor ID를 HoloLens의 로컬 디스크에 저장하여 애플리케이션 세션과 애플리케이션 다시 시작 간에 Azure Spatial Anchors를 유지하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-158">In this tutorial you learned how to persist Azure Spatial Anchors between application sessions and application restarts by saving the Azure Spatial Anchor ID to the local disk on HoloLens.</span></span> <span data-ttu-id="509a7-159">또한 기본 다중 사용자, 정적 홀로그램 공유 환경을 위해 여러 디바이스 간에 Azure Spatial Anchors를 공유하는 방법도 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-159">You also learned how to share Azure Spatial Anchors between multiple devices for a basic multi-user, static hologram shared experience.</span></span>

<span data-ttu-id="509a7-160">다음 자습서에서는 사용자에게 실시간 피드백을 제공하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-160">In the next tutorial you will learn how to provide users with real-time feedback.</span></span> <span data-ttu-id="509a7-161">이 피드백에는 앵커 만들기, 환경 이해 품질 및 Azure 세션 상태에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-161">This feedback will include information about Anchor creation, the quality of environment understanding, and the state of the Azure session.</span></span> <span data-ttu-id="509a7-162">피드백을 사용하지 않는 경우 사용자는 앵커가 Azure에 성공적으로 업로드되었는지 여부, 환경의 품질이 앵커를 만드는 데 충분한지 여부 또는 현재 상태를 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="509a7-162">Without feedback, users may not know whether an anchor has successfully been uploaded to Azure, whether the quality of the environment is sufficient for anchor creation, or the current state.</span></span>

[<span data-ttu-id="509a7-163">다음 단원: 3. Azure Spatial Anchor 피드백 표시</span><span class="sxs-lookup"><span data-stu-id="509a7-163">Next Lesson: 3. Displaying Azure Spatial Anchor feedback</span></span>](mrlearning-asa-ch3.md)
