---
title: Azure 클라우드 자습서 - 4. Integrating Azure Spatial 통합
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 Azure Spatial Anchors를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: 혼합 현실, unity, 자습서, hololens, hololens 2, Azure spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: 4eac2b96519abeebc277a53ad83d1b6dec8d61fd
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305955"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="54976-105">4. Integrating Azure Spatial 통합</span><span class="sxs-lookup"><span data-stu-id="54976-105">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="54976-106">이 자습서에서는 **Azure Spatial Anchors**를 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-106">In this tutorial, you will learn how to use **Azure Spatial Anchors**.</span></span> <span data-ttu-id="54976-107">**추적된 개체**의 위치를 Azure Spatial Anchors로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-107">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="54976-108">그런 다음, 사용자에게 위치를 가리키는 안내 화살표가 있는 사용자를 쿼리하고 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-108">Then you will query and present the user with a guiding arrow pointing to the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="54976-109">목표</span><span class="sxs-lookup"><span data-stu-id="54976-109">Objectives</span></span>

* <span data-ttu-id="54976-110">Azure Spatial Anchors의 기본 사항에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="54976-110">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="54976-111">이 프로젝트에서 Azure Spatial Anchors를 사용하도록 장면을 설정하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="54976-111">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="54976-112">위치 저장 및 쿼리를 통합하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="54976-112">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="54976-113">Azure Spatial Anchors 이해</span><span class="sxs-lookup"><span data-stu-id="54976-113">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="54976-114">**Azure Spatial Anchors**는 Azure Cloud Services 제품군의 일부이며 앵커 위치를 저장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="54976-114">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="54976-115">저장된 앵커 위치는 클라우드의 *앵커 ID* 기반으로 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54976-115">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="54976-116">이 앵커 위치는 HoloLens, iOS 및 Android 디바이스와 같은 다중 플랫폼 디바이스에서 공유하고 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54976-116">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="54976-117">[Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="54976-117">Learn more about [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="54976-118">Azure Spatial Anchors 준비</span><span class="sxs-lookup"><span data-stu-id="54976-118">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="54976-119">시작하기 전에 Azure Portal에서 공간 앵커 리소스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-119">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="54976-120">[공간 앵커 리소스](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)를 만드는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="54976-120">Learn how to make a [spatial anchor resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="54976-121">장면 준비</span><span class="sxs-lookup"><span data-stu-id="54976-121">Preparing the scene</span></span>

<span data-ttu-id="54976-122">이 섹션에서는 장면을 구성하고 필요한 변경을 수행하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="54976-122">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="54976-123">Project 창에서 **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-123">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step1-1.png)

<span data-ttu-id="54976-125">**Manager** 폴더에서 프리팹 **Anchor Manager**를 장면 Hierarchy에 끌어다 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="54976-125">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="54976-126">Hierarchy에서 **Anchor Manager** GameObject를 선택하고 Inspector 섹션에서 **Spatial Anchor Manager**(스크립트)를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="54976-126">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="54976-127">계정 ID 및 키 필드를 찾아 이전 단계의 필수 구성 요소에서 만든 자격 증명을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-127">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="54976-129">이제 장면 Hierarchy에서 **Scene Controller** 개체를 찾아 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-129">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="54976-130">**Scene Controller** Inspector가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54976-130">You will see the **Scene Controller** Inspector.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="54976-132">**Scene Controller** 구성 요소의 **Anchor Manager** 필드가 비어 있음을 확인하고, 장면의 Hierarchy에서 **Anchor Manager**를 해당 필드로 끌어서 놓고 장면을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-132">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="54976-133">HoloLens 2에 앱 빌드 및 배포</span><span class="sxs-lookup"><span data-stu-id="54976-133">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="54976-134">Azure Spatial Anchors는 Unity에서 실행할 수 없으므로 Azure Spatial Anchors 기능을 테스트하려면 프로젝트를 디바이스에 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-134">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="54976-135">Unity 프로젝트를 빌드하고 HoloLens 2에 배포하는 방법을 미리 알아보려면 [디바이스에 애플리케이션 빌드](mr-learning-base-ch1.md#build-your-application-to-your-device) 지침을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54976-135">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mr-learning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="54976-136">HoloLens 2에서 앱 실행 및 앱 내 지침 수행</span><span class="sxs-lookup"><span data-stu-id="54976-136">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="54976-137">위치를 저장할 앵커 만들기</span><span class="sxs-lookup"><span data-stu-id="54976-137">Create an anchor to store a location</span></span>

<span data-ttu-id="54976-138">이 섹션에서는 개체 위치를 저장하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="54976-138">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="54976-139">애플리케이션을 실행하고 환경의 주 메뉴에서 **개체 설정**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-139">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="54976-140">저장하려는 개체의 **이름**을 지정하고 **개체 설정**을 클릭하여 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-140">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="54976-141">개체에 대한 추가 정보를 추가하려면 **이미지**를 선택하고 개체에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-141">To add more information about the object, select the **image**, and describe the object.</span></span>

<span data-ttu-id="54976-142">위치를 저장하려면 **위치 저장**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-142">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="54976-143">저장하려는 위치에 이동하여 놓을 수 있는 **앵커 포인터**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54976-143">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="54976-144">그런 다음, 확인 팝업을 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54976-144">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="54976-145">위치를 확인하고 저장하려면 **예**를 클릭합니다. 그렇지 않으면 **아니오**를 클릭하고 위치를 다시 선택하여 위치를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54976-145">If you want to confirm and save the location, click on **Yes**; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="54976-146">**예**를 클릭하여 위치를 확인하면 위치 및 앵커 ID가 Azure 클라우드 스토리지에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="54976-146">Once you confirm the location by clicking on **Yes**, the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="54976-147">저장되면 개체의 이름과 함께 앵커에 **개체 태그**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54976-147">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="54976-148">이제 개체 위치가 성공적으로 저장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="54976-148">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="54976-149">앵커 위치를 찾기 위한 쿼리</span><span class="sxs-lookup"><span data-stu-id="54976-149">Query for finding an anchor location</span></span>

<span data-ttu-id="54976-150">앵커 위치를 성공적으로 저장한 후에는 주 메뉴에서 **개체 검색**을 선택하여 앵커 위치를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54976-150">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="54976-151">**개체 검색**을 클릭하면 검색할 개체의 이름을 지정해야 하는 새 창이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="54976-151">After clicking on **Search Object**, a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="54976-152">개체의 이름을 입력하고 **개체 검색**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-152">Enter the name of the object and click on **Search Object**.</span></span> <span data-ttu-id="54976-153">개체가 이전에 저장되고 데이터베이스에 있는 경우 이전에 저장한 개체의 모든 세부 정보를 포함하는 개체 카드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54976-153">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="54976-154">이제 **위치 표시**를 클릭하여 개체를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54976-154">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="54976-155">**위치 표시**를 클릭하면 시스템이 클라우드 스토리지에서 개체 주소를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-155">Once you click on **Show Location**, the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="54976-156">위치를 성공적으로 검색한 후 **화살표**를 통해 개체의 위치로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-156">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="54976-157">개체의 위치를 찾을 때까지 화살표 표시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="54976-157">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="54976-158">개체를 찾으면 개체 이름이 맨 위에 표시되고, 화살표 표시가 사라지고, 이제 **개체 태그**를 클릭하여 개체의 세부 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54976-158">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="54976-159">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="54976-159">Congratulations</span></span>

<span data-ttu-id="54976-160">이 자습서에서는 Azure Spatial Anchors가 Hololense 2에서 개체 위치를 저장하고 검색하는 방법을 배웠습니다.</span><span class="sxs-lookup"><span data-stu-id="54976-160">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="54976-161">최종 자습서에서는 **Azure Bot Service**를 사용하여 자연어를 애플리케이션에 대한 새로운 상호 작용 방법으로 추가하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="54976-161">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

[<span data-ttu-id="54976-162">다음 자습서: 5. LUIS와 Azure Bot Service 통합</span><span class="sxs-lookup"><span data-stu-id="54976-162">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)
