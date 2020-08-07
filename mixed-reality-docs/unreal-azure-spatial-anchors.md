---
title: Unreal의 Azure Spatial Anchors
description: Unreal 엔진에서 Azure Spatial Anchors 만들기에 대한 개요입니다.
author: hferrone
services: azure-spatial-anchors
ms.author: v-haferr
ms.date: 07/01/2020
ms.topic: tutorial
ms.service: azure-spatial-anchors
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, azure 개발, spatial anchors, 혼합 현실, 개발, 기능, 새 프로젝트, 에뮬레이터, 설명서, 가이드, 홀로그램, 게임 개발
ms.openlocfilehash: c7189407bea4b38e7305f0dda7637b82d3325704
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87377348"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="291f4-104">Unreal의 Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="291f4-104">Azure Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="291f4-105">개요</span><span class="sxs-lookup"><span data-stu-id="291f4-105">Overview</span></span>

<span data-ttu-id="291f4-106">Azure Spatial Anchors는 Microsoft Mixed Reality 서비스이며, 증강 현실 디바이스를 사용하여 실제 세계에서 앵커 위치를 검색, 공유 및 유지하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-106">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="291f4-107">아래 설명서는 Azure Spatial Anchors 서비스를 Unreal 프로젝트에 통합하는 지침을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-107">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="291f4-108">자세한 내용은 [Azure Spatial Anchors 서비스](https://azure.microsoft.com/services/spatial-anchors/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="291f4-108">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="291f4-109">로컬 앵커는 디바이스에 저장되는 반면, Azure Spatial Anchors는 클라우드에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="291f4-110">앵커를 로컬로 디바이스에 저장하려는 경우, 해당 프로세스를 안내하는 [로컬 Spatial Anchors](unreal-spatial-anchors.md) 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="291f4-110">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="291f4-111">로컬 및 Azure 앵커는 동일한 프로젝트에서 충돌 없이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="291f4-112">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="291f4-112">Prerequisites</span></span>

<span data-ttu-id="291f4-113">이 가이드를 완료하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-113">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="291f4-114">[Unreal 버전 4.25](https://www.unrealengine.com/get-now) 이상 설치</span><span class="sxs-lookup"><span data-stu-id="291f4-114">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="291f4-115">Unreal에 [HoloLens 2 프로젝트](unreal-uxt-ch1.md) 설정</span><span class="sxs-lookup"><span data-stu-id="291f4-115">A [HoloLens 2 project](unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="291f4-116">[Azure Spatial Anchors 개요](https://docs.microsoft.com/azure/spatial-anchors/overview) 꼼꼼히 읽기</span><span class="sxs-lookup"><span data-stu-id="291f4-116">Read through the [Azure Spatial Anchors overview](https://docs.microsoft.com/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="291f4-117">C++ 및 Unreal에 대한 기본 지식</span><span class="sxs-lookup"><span data-stu-id="291f4-117">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="291f4-118">Azure Spatial Anchors 계정 정보 얻기</span><span class="sxs-lookup"><span data-stu-id="291f4-118">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="291f4-119">프로젝트에서 Azure Spatial Anchors를 사용하기 전에 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-119">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="291f4-120">[공간 앵커 리소스를 만들고](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) 아래 나열된 계정 필드를 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-120">[Create a spatial anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="291f4-121">다음 값은 애플리케이션의 계정으로 사용자를 인증하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-121">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="291f4-122">**계정 ID**</span><span class="sxs-lookup"><span data-stu-id="291f4-122">**Account ID**</span></span>
    * <span data-ttu-id="291f4-123">**계정 키**</span><span class="sxs-lookup"><span data-stu-id="291f4-123">**Account Key**</span></span>

<span data-ttu-id="291f4-124">자세한 내용은 [Azure Spatial Anchors 인증](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) 문서를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="291f4-124">Check out the [Azure Spatial Anchors authentication](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="291f4-125">Unreal 4.25의 Azure Spatial Anchors는 Azure AD 인증 토큰을 지원하지 않지만 이후 릴리스에서는 이 기능에 대한 지원이 제공될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-125">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="291f4-126">Azure Spatial Anchors 플러그 인 추가</span><span class="sxs-lookup"><span data-stu-id="291f4-126">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="291f4-127">다음을 수행하여 Unreal 에디터에서 Azure Spatial Anchors 플러그 인을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-127">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="291f4-128">**편집 > 플러그 인**을 클릭하고 **AzureSpatialAnchors** 및 **AzureSpatialAnchorsForWMR**을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-128">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR**.</span></span>
2. <span data-ttu-id="291f4-129">두 플러그 인의 **사용** 확인란을 선택하여 애플리케이션에서 Azure Spatial Anchors 청사진 라이브러리에 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-129">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="291f4-131">완료되면 Unreal 편집기를 다시 시작하여 플러그 인 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-131">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="291f4-132">이제 프로젝트에서 Azure Spatial Anchors를 사용할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-132">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="291f4-133">Spatial Anchors 세션 시작</span><span class="sxs-lookup"><span data-stu-id="291f4-133">Starting a Spatial Anchors session</span></span>
<span data-ttu-id="291f4-134">Azure Spatial Anchors 세션을 사용하면 클라이언트 애플리케이션에서 Azure Spatial Anchors 서비스와 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-134">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="291f4-135">Azure Spatial Anchors를 만들고 유지하고 공유하려면 Azure Spatial Anchors 세션을 만들고 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-135">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="291f4-136">애플리케이션에서 사용 중인 Pawn에 대한 청사진을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-136">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="291f4-137">**계정 ID**와 **계정 키**에 대한 두 문자열 변수를 추가한 다음, Azure Spatial Anchors 계정에서 해당 값을 할당하여 세션을 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-137">Add two string variables for the **Account ID** and **Account Key**, then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="291f4-139">다음을 수행하여 Azure Spatial Anchors 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-139">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="291f4-140">HoloLens 애플리케이션에서 **AR 세션**을 실행 중인지 확인합니다. AR 세션이 실행될 때까지 Azure Spatial Anchors 세션을 시작할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-140">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="291f4-141">설정되어 있지 않으면 [AR 세션 자산을 만듭니다](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="291f4-141">If you don't have one setup, [create an AR Session asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="291f4-142">**Azure Spatial Anchors 세션 시작** 사용자 지정 이벤트를 추가하고 아래 스크린샷에 표시된 대로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-142">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="291f4-143">세션을 만들면 기본적으로 세션이 시작되지 않습니다. 따라서 개발자가 Azure Spatial Anchors 서비스를 통해 인증할 세션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-143">Creating a session doesn't start the session by default, which allows the developer to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="291f4-145">**계정 ID** 및 **계정 키**를 제공하도록 Azure Spatial Anchors 세션을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-145">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key**.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="291f4-147">애플리케이션이 Azure Spatial Anchors를 만들고 찾을 수 있도록 Azure Spatial Anchors 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-147">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="291f4-149">서비스를 더 이상 사용하지 않는 경우 이벤트 그래프 청사진에서 Azure Spatial Anchors 리소스를 정리하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-149">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="291f4-150">Azure Spatial Anchors 세션을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-150">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="291f4-151">세션은 더 이상 실행되지 않지만 연결된 리소스가 Azure Spatial Anchors 플러그 인에 여전히 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-151">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="291f4-153">Azure Spatial Anchors 세션을 제거하여 Azure Spatial Anchors 플러그 인에 여전히 알려져 있는 Azure Spatial Anchors 세션 리소스를 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-153">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="291f4-155">이벤트 그래프 청사진은 아래 스크린샷과 같은 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-155">Your Event Graph blueprint should look like the screenshot below:</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-08.png)


## <a name="creating-an-anchor"></a><span data-ttu-id="291f4-157">앵커 만들기</span><span class="sxs-lookup"><span data-stu-id="291f4-157">Creating an anchor</span></span>
<span data-ttu-id="291f4-158">Azure Spatial Anchor는 증강 현실 애플리케이션 공간에서 실제 세계 포즈를 나타내며, 증강 현실 콘텐츠를 실제 세계의 위치에 고정합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-158">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to locations in the physical world.</span></span> <span data-ttu-id="291f4-159">Azure Spatial Anchors는 여러 사용자가 서로 공유할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-159">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="291f4-160">이러한 공유를 통해 다른 디바이스에서 그려진 증강 현실 콘텐츠를 실제 세계에서 동일한 위치에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-160">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="291f4-161">새 Azure Spatial Anchor를 만들려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-161">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="291f4-162">Azure Spatial Anchors 세션이 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-162">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="291f4-163">Azure Spatial Anchors 세션이 실행되고 있지 않으면 애플리케이션에서 Azure Spatial Anchor를 만들거나 유지할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-163">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="291f4-165">위치를 유지해야 하는 Unreal **[장면 구성 요소](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** 를 만들거나 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-165">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="291f4-166">아래 이미지에서는 **앵커가 필요한 장면 구성 요소**라는 구성 요소가 변수로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-166">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="291f4-167">Unreal 장면 구성 요소는 [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) 및 Azure Spatial Anchor에 대해 애플리케이션 월드 변환을 설정하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-167">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="291f4-169">Unreal 장면 구성 요소에 대한 Azure Spatial Anchor를 생성하고 저장하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-169">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="291f4-170">Unreal 장면 구성 요소에 대한 [Pin 구성 요소](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html)를 호출하고 장면 구성 요소의 **월드 변환**을 AR Pin에 사용되는 월드 변환으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-170">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="291f4-171">Unreal은 Azure Spatial Anchor를 만드는 데 사용되는 AR Pin을 사용하여 애플리케이션 공간에서 AR 포인트를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-171">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="291f4-172">Unreal에서 AR Pin은 HoloLens의 SpatialAnchor와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-172">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="291f4-174">새로 만든 AR Pin을 사용하여 **Create Cloud Anchor**(클라우드 앵커 만들기)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-174">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="291f4-175">Create Cloud Anchor(클라우드 앵커 만들기)는 Azure Spatial Anchor 서비스가 아닌 로컬에 Azure Spatial Anchor를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-175">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="291f4-176">Azure Spatial Anchor의 매개 변수(예: 만료 날짜)는 서비스를 사용하여 Azure Spatial Anchor를 만들기 전에 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-176">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="291f4-178">Azure Spatial Anchor 만료를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-178">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="291f4-179">이 함수의 Lifetime 매개 변수를 사용하면 개발자가 서비스에서 앵커를 유지해야 하는 시간을 초 단위로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-179">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="291f4-180">예를 들어, 일주일의 만료 시간 값은 60초 x 60분 x 24시간 x 7일 = 604,800초입니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-180">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="291f4-182">앵커 매개 변수를 설정한 후에 저장할 준비가 된 것으로 앵커를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-182">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="291f4-183">아래 예제에서는 새로 만든 Azure Spatial Anchor가 저장이 필요한 Azure Spatial Anchors 세트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-183">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="291f4-184">이 세트는 Pawn 청사진에 대한 변수로 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-184">This set is declared as a variable for the Pawn blueprint.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="291f4-186">앵커 저장</span><span class="sxs-lookup"><span data-stu-id="291f4-186">Saving an Anchor</span></span>

<span data-ttu-id="291f4-187">매개 변수를 사용하여 Azure Spatial Anchor를 구성한 후 **Save Cloud Anchor**(클라우드 앵커 저장)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-187">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor**.</span></span> <span data-ttu-id="291f4-188">Save Cloud Anchor(클라우드 앵커 저장)는 Azure Spatial Anchors 서비스에 대한 앵커를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-188">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="291f4-189">Save Cloud Anchor(클라우드 앵커 저장) 호출이 성공하면 Azure Spatial Anchor 서비스의 다른 사용자가 Azure Spatial Anchor를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-189">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="291f4-191">Save Cloud Anchor(클라우드 앵커 저장)는 비동기 함수이며 게임 스레드 이벤트(예: **EventTick**)에서만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-191">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick**.</span></span> <span data-ttu-id="291f4-192">Save Cloud Anchor(클라우드 앵커 저장)는 사용자 지정 청사진 함수에 사용 가능한 청사진 함수로 나타나지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-192">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="291f4-193">하지만 Pawn 이벤트 그래프 청사진 편집기에서는 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-193">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="291f4-194">아래 예에서 Azure Spatial Anchor는 입력 이벤트 콜백 중에 세트에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-194">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="291f4-195">그런 다음, EventTick에 앵커가 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-195">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="291f4-196">Azure Spatial Anchor를 저장하려면 Azure Spatial Anchors 세션에서 생성한 공간 데이터의 양에 따라 여러 번 시도가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-196">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="291f4-197">그래서 Save 호출이 성공했는지 여부를 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-197">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="291f4-198">앵커가 저장되지 않은 경우 아직 저장이 필요한 앵커 세트에 다시 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-198">If the anchor doesn't save, re-add it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="291f4-199">향후 EventTicks는 Azure Spatial Anchor 서비스에 앵커가 성공적으로 저장될 때까지 저장을 시도할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-199">Future EventTicks will try to save the anchor until it's successfully stored in the Azure Spatial Anchor service.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="291f4-201">앵커가 저장되면 애플리케이션에 콘텐츠를 배치하기 위해 AR Pin의 변환을 참조 변환으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-201">Once the anchor saves, you can use the AR Pins' transform as a reference transform for placing content in the application.</span></span> <span data-ttu-id="291f4-202">다른 사용자가 이 앵커를 감지하고 AR 콘텐츠를 실제 세계의 여러 디바이스에 맞출 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-202">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="291f4-203">앵커 삭제</span><span class="sxs-lookup"><span data-stu-id="291f4-203">Deleting an Anchor</span></span>

<span data-ttu-id="291f4-204">**Delete Cloud Anchor**(클라우드 앵커 삭제)를 호출하여 Azure Spatial Anchor 서비스에서 앵커를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-204">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor**.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="291f4-206">Delete Cloud Anchor(클라우드 앵커 삭제)는 잠재 함수이며 게임 스레드 이벤트(예: EventTick)에서만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-206">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="291f4-207">Delete Cloud Anchor(클라우드 앵커 삭제)는 사용자 지정 청사진 함수에는 사용 가능한 청사진 함수로 나타나지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-207">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="291f4-208">하지만 Pawn 이벤트 그래프 청사진 편집기에서는 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-208">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="291f4-209">아래 예제에서는 사용자 지정 입력 이벤트에서 앵커에 삭제 플래그가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-209">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="291f4-210">그런 다음 EventTick에서 삭제를 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-210">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="291f4-211">앵커 삭제가 실패하면 삭제 플래그가 지정된 앵커 세트에 Azure Spatial Anchor를 추가하고 나중에 EventTicks에서 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-211">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="291f4-212">이제 이벤트 그래프 청사진은 아래 스크린샷과 같은 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-212">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="291f4-214">기존 앵커 찾기</span><span class="sxs-lookup"><span data-stu-id="291f4-214">Locating pre-existing anchors</span></span>

<span data-ttu-id="291f4-215">Azure Spatial Anchors를 만드는 것 외에도 Azure Spatial Anchors 서비스를 사용하여 피어에서 만든 앵커를 감지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-215">In addition to creating Azure Spatial Anchors, you can detect anchors created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="291f4-216">감지할 앵커에 대한 Azure Spatial Anchor 식별자를 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-216">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="291f4-217">앵커 식별자는 이전 Azure Spatial Anchors 세션에서 동일한 디바이스로 만든 앵커에 대해 확보할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-217">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="291f4-218">Azure Spatial Anchors 서비스와 상호 작용하는 피어 디바이스에서 만들고 공유할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-218">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="291f4-220">**AzureSpatialAnchorsEvent** 구성 요소를 Pawn 청사진에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-220">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="291f4-221">이 구성 요소를 사용하면 다양한 Azure Spatial Anchors 이벤트(예: Azure Spatial Anchors가 있을 때 호출되는 이벤트)를 구독할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-221">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="291f4-223">**AzureSpatialAnchorsEvent** 구성 요소에 대한 **ASAAnchor Located 대리자**를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-223">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="291f4-224">대리자는 Azure Spatial Anchors 계정과 연결된 새 앵커가 배치되는 경우 해당 애플리케이션에 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-224">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="291f4-225">이벤트 콜백을 사용하면 Azure Spatial Anchors 세션을 사용하여 피어가 만든 Azure Spatial Anchors에는 기본적으로 AR Pin이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-225">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="291f4-226">감지된 Azure Spatial Anchor에 대한 AR Pin을 만들려면 개발자가 **Create ARPin Around Azure Cloud Spatial Anchor**(Azure Cloud Spatial Anchor에 대한 ARPin 만들기)를 호출하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-226">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor**.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="291f4-228">Azure Spatial Anchor 서비스를 사용하여 피어에서 만든 Azure Spatial Anchors를 찾기 위해 애플리케이션은 **Azure Spatial Anchors Watcher**를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-228">In order to locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher**:</span></span>
1. <span data-ttu-id="291f4-229">Azure Spatial Anchors 세션이 실행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-229">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="291f4-230">**AzureSpatialAnchorsLocateCriteria**를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-230">Create an **AzureSpatialAnchorsLocateCriteria**.</span></span>
    * <span data-ttu-id="291f4-231">다양한 위치 매개 변수(예: 사용자와의 거리 또는 다른 앵커와의 거리)를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-231">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="291f4-232">**AzureSpatialAnchorsLocateCritieria**에서 원하는 Azure Spatial Anchor 식별자를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-232">Declare your desired Azure Spatial Anchor identifier in the **AzureSpatialAnchorsLocateCritieria**.</span></span>
4. <span data-ttu-id="291f4-233">**Create Watcher**(감시자 만들기)를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-233">Call **Create Watcher**.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="291f4-235">이제 애플리케이션이 Azure Spatial Anchors 서비스에 알려진 Azure Spatial Anchors를 찾기 시작합니다. 따라서, 피어에서 만든 Azure Spatial Anchors를 사용자가 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-235">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="291f4-236">Azure Spatial Anchor를 찾은 후 **Stop Watcher**(감시자 중지)를 호출하여 Azure Spatial Anchors Watcher를 중지하고 감시자 리소스를 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-236">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="291f4-238">마지막 이벤트 그래프 청사진은 아래 스크린샷과 같은 모양입니다.</span><span class="sxs-lookup"><span data-stu-id="291f4-238">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![Spatial Anchors 플러그 인](images/asa-unreal/unreal-spatial-anchors-img-23.png)


## <a name="next-steps"></a><span data-ttu-id="291f4-240">다음 단계</span><span class="sxs-lookup"><span data-stu-id="291f4-240">Next steps</span></span>
* [<span data-ttu-id="291f4-241">로컬 Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="291f4-241">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="291f4-242">Spatial Anchors 설명서</span><span class="sxs-lookup"><span data-stu-id="291f4-242">Spatial Anchors documentation</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)
* [<span data-ttu-id="291f4-243">Spatial Anchor 기능</span><span class="sxs-lookup"><span data-stu-id="291f4-243">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="291f4-244">효과적인 앵커 환경 지침</span><span class="sxs-lookup"><span data-stu-id="291f4-244">Effective anchor experience guidelines</span></span>](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)