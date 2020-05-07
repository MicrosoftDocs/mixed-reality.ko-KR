---
title: 다중 사용자 기능 자습서 - 5. 공유 환경에 Azure Spatial Anchors 통합
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 다중 사용자 공유 환경을 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, Unity, 자습서, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604974"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="be2e6-105">4. 공유 환경에 Azure Spatial Anchors 통합</span><span class="sxs-lookup"><span data-stu-id="be2e6-105">4. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="be2e6-106">이 자습서에서는 ASA(Azure Spatial Anchors)를 공유 환경에 통합하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="be2e6-107">ASA를 사용하면 여러 디바이스에서 실제 세계에 대한 공통 참조가 가능하기 때문에 사용자가 각자 실제 위치에서 서로를 볼 수 있고 동일한 위치에서 공유 환경을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="be2e6-108">목표</span><span class="sxs-lookup"><span data-stu-id="be2e6-108">Objectives</span></span>

* <span data-ttu-id="be2e6-109">다중 디바이스 맞춤을 위해 ASA를 공유 환경에 통합</span><span class="sxs-lookup"><span data-stu-id="be2e6-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="be2e6-110">ASA가 로컬 공유 환경의 컨텍스트에서 작동하는 방식에 대한 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="be2e6-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="be2e6-111">장면 준비</span><span class="sxs-lookup"><span data-stu-id="be2e6-111">Preparing the scene</span></span>

<span data-ttu-id="be2e6-112">Hierarchy 창에서 **SharedPlayground** 개체를 펼친 다음, **TableAnchor** 개체를 펼쳐서 자식 개체를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

<span data-ttu-id="be2e6-114">Project 창에서 **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** 폴더로 이동하여 **Buttons** 프리팹을 Hierarchy 창의 **TableAnchor** 자식 개체 위로 끌어와서 TableAnchor 개체의 자식으로 장면에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab on top of the **TableAnchor** child object in the Hierarchy window to add it to your scene as a child of the TableAnchor object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="be2e6-116">장면을 작동하도록 단추 구성</span><span class="sxs-lookup"><span data-stu-id="be2e6-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="be2e6-117">이 섹션에서는 Azure Spatial Anchors를 사용하여 공유 환경에서 공간 정렬을 구현하는 방법에 대한 기본 사항을 보여주는 일련의 단추 이벤트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-117">In this section, you will configure a series of button events that demonstrate the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="be2e6-118">Hierarchy 창에서 **Button** 개체를 펼치고 첫째 자식 단추 개체인 **StartAzureSession**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

<span data-ttu-id="be2e6-120">Inspector 창에서 **Interactable (Script)** 구성 요소를 찾아서 **OnClick ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="be2e6-121">**None (Object)** 필드에는 **TableAnchor** 개체를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-121">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="be2e6-122">**No Function** 드롭다운에서 **AnchorModuleScript** > **StartAzureSession ()** 함수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-122">From **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

<span data-ttu-id="be2e6-124">Hierarchy 창에서 둘째 자식 단추 개체인 **CreateAzureAnchor**를 선택한 다음, Inspector 창에서 **Interactable (Script)** 구성 요소를 찾아서 **OnClick ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="be2e6-125">**None (Object)** 필드에는 **TableAnchor** 개체를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-125">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="be2e6-126">**No Function** 드롭다운에서 **AnchorModuleScript** > **CreateAzureAnchor ()** 함수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-126">From **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="be2e6-127">새로운 **None (Game Object)** 필드가 나타나면 **TableAnchor** 개체를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

<span data-ttu-id="be2e6-129">Hierarchy 창에서 셋째 자식 단추 개체인 **ShareAzureAnchor**를 선택한 다음, Inspector 창에서 **Interactable (Script)** 구성 요소를 찾아서 **OnClick ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="be2e6-130">**None (Object)** 필드에는 **TableAnchor** 개체를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-130">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="be2e6-131">**No Function** 드롭다운에서 **SharingModuleScript** > **ShareAzureAnchor ()** 함수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-131">From **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

<span data-ttu-id="be2e6-133">Hierarchy 창에서 넷째 자식 단추 개체인 **GetAzureAnchor**를 선택한 다음, Inspector 창에서 **Interactable (Script)** 구성 요소를 찾아서 **OnClick ()** 이벤트를 다음과 같이 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-133">In the Hierarchy window, select the forth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="be2e6-134">**None (Object)** 필드에는 **TableAnchor** 개체를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-134">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="be2e6-135">**No Function** 드롭다운에서 **SharingModuleScript** > **GetAzureAnchor ()** 함수를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-135">From **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="be2e6-137">Azure 리소스에 장면 연결</span><span class="sxs-lookup"><span data-stu-id="be2e6-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="be2e6-138">Hierarchy 창에서 **SharedPlayground** 개체를 펼치고 **TableAnchor** 개체를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span> <span data-ttu-id="be2e6-139">그런 다음, Inspector 창에서 **Spatial Anchor Manager (Script)** 구성 요소를 찾아서, 이 자습서 시리즈에서 [필수 구성 요소](mrlearning-sharing(photon)-ch1.md#prerequisites)의 일부로 생성된 Azure Spatial Anchors 계정의 자격 증명을 사용하여 **Credentials** 섹션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-139">Then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mrlearning-sharing(photon)-ch1.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="be2e6-140">**Spatial Anchors Account ID** 필드에 Azure Spatial Anchors 계정의 **계정 ID**를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="be2e6-141">**Spatial Anchors Account Key** 필드에 Azure Spatial Anchors 계정의 기본 또는 보조 **액세스 키**를 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

<span data-ttu-id="be2e6-143">**TableAnchor** 개체가 선택된 상태로 Inspector 창에서 모든 스크립트 구성 요소가 활성화되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-143">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are enabled:</span></span>

* <span data-ttu-id="be2e6-144">**Spatial Anchor Manager (Script)** 구성 요소 옆에 있는 확인란을 선택하여 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-144">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="be2e6-145">**Anchor Module Script (Script)** 구성 요소 옆에 있는 확인란을 선택하여 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-145">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="be2e6-146">**Sharing Module Script (Script)** 구성 요소 옆에 있는 확인란을 선택하여 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-146">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="be2e6-148">공간 맞춤 환경 체험</span><span class="sxs-lookup"><span data-stu-id="be2e6-148">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="be2e6-149">Azure Spatial Anchors는 Unity에서 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-149">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="be2e6-150">따라서 Azure Spatial Anchors 기능을 테스트하려면 둘 이상의 HoloLens 디바이스에 프로젝트를 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-150">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two HoloLens devices.</span></span>

<span data-ttu-id="be2e6-151">Unity 프로젝트를 빌드하여 두 개의 HoloLens 디바이스에 배포하면 Azure Anchor ID를 공유하여 디바이스 간의 공간 맞춤을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-151">If you now build and deploy the Unity project to two HoloLens devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="be2e6-152">이를 테스트하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-152">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="be2e6-153">HoloLens 디바이스 1: **애플리케이션 시작**(로켓 발사대가 인스턴스화되어 테이블에 배치됩니다.)</span><span class="sxs-lookup"><span data-stu-id="be2e6-153">On HoloLens device 1: **Start the application** (the Rocket Launcher is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="be2e6-154">HoloLens 디바이스 2: **애플리케이션 시작**(두 사용자 모두에게 로켓 발사대가 있는 테이블이 보이지만 테이블이 동일한 위치에 나타나지 않고 사용자가 있는 곳에 사용자 아바타가 나타나지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="be2e6-154">On HoloLens device 2: **Start the application** (both users see the table with the Rocket Launcher, however, the table does not appear in the same place and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="be2e6-155">HoloLens 디바이스 1: **Start Azure Session** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-155">On HoloLens device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="be2e6-156">HoloLens 디바이스 1: **Create Azure Anchor** 단추를 누릅니다. (TableAnchor 개체의 위치에 앵커를 만들고 Azure 리소스에 앵커 정보를 저장합니다.)</span><span class="sxs-lookup"><span data-stu-id="be2e6-156">On HoloLens device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="be2e6-157">HoloLens 디바이스 1: **Share Azure Anchor** 단추를 누릅니다. (앵커 ID를 다른 사용자와 실시간으로 공유합니다.)</span><span class="sxs-lookup"><span data-stu-id="be2e6-157">On HoloLens device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="be2e6-158">HoloLens 디바이스 2: **Start Azure Session** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-158">On HoloLens device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="be2e6-159">HoloLens 디바이스 2: **Get Azure Anchor** 단추를 누릅니다. (Azure 리소스에 연결하여 공유 앵커 ID에 대한 앵커 정보를 검색한 다음, HoloLens 디바이스 1에 앵커가 생성된 위치로 TableAnchor 개체를 이동합니다.)</span><span class="sxs-lookup"><span data-stu-id="be2e6-159">On HoloLens device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the HoloLens device 1)</span></span>

## <a name="congratulations"></a><span data-ttu-id="be2e6-160">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-160">Congratulations</span></span>

<span data-ttu-id="be2e6-161">이 자습서에서는 Azure의 강력한 Spatial Anchors를 통합하여 공유 환경에서 디바이스를 맞추는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-161">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span> <span data-ttu-id="be2e6-162">이것으로 자습서 시리즈를 마치겠습니다. 이 시리즈에서는 Photon 계정과 애플리케이션을 설정하고, Photon과 PUN을 Unity 애플리케이션에 통합하고, 사용자 아바타와 공유 개체를 구성하고, 마지막으로 ASA를 사용하여 여러 참가자를 맞추는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="be2e6-162">This also concludes this tutorial series where you have learned how to set up a Photon account and application, integrate Photon and PUN into a Unity application, configure user avatars and shared objects, and finally align multiple participants using ASA.</span></span>
