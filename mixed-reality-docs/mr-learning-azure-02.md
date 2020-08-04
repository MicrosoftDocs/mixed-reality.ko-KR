---
title: Azure 클라우드 자습서 - 2. Azure Storage 통합
description: 이 과정을 완료하여 HoloLens 2 애플리케이션 내에서 Azure Table Storage 및 Azure Blob Storage를 구현하는 방법을 알아봅니다.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, 자습서, HoloLens, HoloLens 2, Azure Storage
ms.localizationpriority: high
ms.openlocfilehash: a8d91bc55b3ce73d6e1fb46e5d696d853adcf871
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376475"
---
# <a name="2-integrating-azure-storage"></a><span data-ttu-id="ce4b4-105">2. Azure Storage 통합</span><span class="sxs-lookup"><span data-stu-id="ce4b4-105">2. Integrating Azure storage</span></span>

<span data-ttu-id="ce4b4-106">이 자습서에서는 엔터티 데이터를 Azure Table 스토리지에 저장하고 썸네일 이미지를 Azure Blob 스토리지에 저장하는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-106">In this tutorial, you will learn how to save entity data to Azure Table storage and thumbnail images to Azure Blob storage.</span></span> <span data-ttu-id="ce4b4-107">이 기능을 사용하면 세션과 디바이스에서 ID, 이름, 썸네일 이미지 등과 같은 데이터를 사용하여 *추적된 개체*를 클라우드에 저장하고 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-107">This feature will allow us to store and retrieve *Tracked Objects* with data like ID, Name, Thumbnail Image, etc. across sessions and devices to the cloud.</span></span>

## <a name="objectives"></a><span data-ttu-id="ce4b4-108">목표</span><span class="sxs-lookup"><span data-stu-id="ce4b4-108">Objectives</span></span>

* <span data-ttu-id="ce4b4-109">Azure 스토리지에 대한 기본 사항 알아보기</span><span class="sxs-lookup"><span data-stu-id="ce4b4-109">Learn the basics about Azure storage</span></span>
* <span data-ttu-id="ce4b4-110">Table 스토리지에서 데이터를 저장, 수정 및 검색하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="ce4b4-110">Learn how to store, modify and retrieve data from Table storage</span></span>
* <span data-ttu-id="ce4b4-111">Blob 스토리지에서 이미지를 저장 및 삭제하는 방법 알아보기</span><span class="sxs-lookup"><span data-stu-id="ce4b4-111">Learn how to store and delete images from Blob storage</span></span>

## <a name="understanding-azure-storage"></a><span data-ttu-id="ce4b4-112">Azure 스토리지 이해</span><span class="sxs-lookup"><span data-stu-id="ce4b4-112">Understanding Azure storage</span></span>

<span data-ttu-id="ce4b4-113">**Azure 스토리지**는 클라우드에서 다양한 시나리오와 요구 사항을 처리할 수 있는 Microsoft 스토리지 솔루션입니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-113">**Azure storage** is a Microsoft storage solution on the cloud that can cover many scenarios and requirements.</span></span> <span data-ttu-id="ce4b4-114">이는 크기를 대규모로 조정할 수 있고 개발자가 쉽게 접근할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-114">It can scale massively and is easily approachable by developers.</span></span> <span data-ttu-id="ce4b4-115">모든 서비스는 **Azure 스토리지 계정**의 지원을 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-115">All services can be consumed under the umbrella of an **Azure storage Account**.</span></span> <span data-ttu-id="ce4b4-116">사용 사례에서는 *Table 스토리지* 및 *Blob 스토리지*를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-116">For our use case we will use *Table storage* and *Blob storage*.</span></span>

<span data-ttu-id="ce4b4-117">[Azure 스토리지 서비스](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-117">Learn more about [Azure storage services](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview).</span></span>

### <a name="azure-table-storage"></a><span data-ttu-id="ce4b4-118">Azure Table 스토리지</span><span class="sxs-lookup"><span data-stu-id="ce4b4-118">Azure Table storage</span></span>

<span data-ttu-id="ce4b4-119">이 서비스를 사용하면 데이터를 NoSQL 방식으로 저장할 수 있습니다. 이 프로젝트에서는 이름, 설명, 공간 앵커 ID 등과 같은 *추적된 개체*에 대한 정보를 저장하기 위해 이 스토리지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-119">This services allows us to store data in a NoSQL fashion, in this project we will use it to store information about the *Tracked Object* such as: name, description, spatial anchor id, and more.</span></span>

<span data-ttu-id="ce4b4-120">데모 애플리케이션의 경우 두 개의 테이블이 필요합니다. 하나는 자습서([Azure Custom Vision 통합](mr-learning-azure-03.md))에서 학습된 모델의 상태에 대한 정보와 함께 프로젝트 관련 정보를 더 많이 저장하려는 테이블이고, 다른 하나는 *추적된 개체*에 대한 정보를 저장하는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-120">In context of the demo application, you need two Tables, one to store information about the project with information about the state of trained models more about that in the ([Integrating Azure Custom Vision](mr-learning-azure-03.md)) tutorial and a second table to store information about *Tracked Objects*.</span></span>

<span data-ttu-id="ce4b4-121">[Azure Table 스토리지](https://docs.microsoft.com/azure/storage/tables/table-storage-overview)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-121">Learn more about [Azure Table storage](https://docs.microsoft.com/azure/storage/tables/table-storage-overview).</span></span>

### <a name="azure-blob-storage"></a><span data-ttu-id="ce4b4-122">Azure Blob 스토리지</span><span class="sxs-lookup"><span data-stu-id="ce4b4-122">Azure Blob storage</span></span>

<span data-ttu-id="ce4b4-123">이 서비스를 사용하면 큰 이진 파일을 저장할 수 있습니다. 이 서비스는 *추적된 개체*에 대해 찍은 사진을 썸네일 이미지로 저장하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-123">This service allows to store large binary files, you will use this to store photos taken for *Tracked Objects* as thumbnail.</span></span>
<span data-ttu-id="ce4b4-124">데모 애플리케이션의 경우 이미지를 저장할 하나의 Blob 컨테이너가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-124">For of the demo application you need one Blob Container to store the images.</span></span>

<span data-ttu-id="ce4b4-125">[Azure Blob 스토리지](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-125">Learn more about [Azure Blob storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction).</span></span>

## <a name="preparing-azure-storage"></a><span data-ttu-id="ce4b4-126">Azure Storage 준비</span><span class="sxs-lookup"><span data-stu-id="ce4b4-126">Preparing Azure Storage</span></span>

<span data-ttu-id="ce4b4-127">Azure 스토리지 서비스를 사용하려면 Azure 스토리지 계정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-127">To consume the Azure storage services you will need an Azure storage account.</span></span> <span data-ttu-id="ce4b4-128">스토리지 계정을 만들려면 [스토리지 계정 만들기](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-128">To create a storage account, see [Create a storage account](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal).</span></span> <span data-ttu-id="ce4b4-129">스토리지 계정에 대한 자세한 내용은 [Azure 스토리지 계정 개요](https://docs.microsoft.com/azure/storage/common/storage-account-overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-129">To learn more about storage accounts, see [Azure storage account overview](https://docs.microsoft.com/azure/storage/common/storage-account-overview).</span></span>

<span data-ttu-id="ce4b4-130">스토리지 계정이 있으면 **Azure Portal**에서 이 단원의 다음 섹션에 필요한 연결 문자열을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-130">Once you have a storage account, you can retrieve the connection string from the **Azure Portal** which will be needed in the next section of this lesson.</span></span>

### <a name="optional-azure-storage-explorer"></a><span data-ttu-id="ce4b4-131">선택적 Azure Storage Explorer</span><span class="sxs-lookup"><span data-stu-id="ce4b4-131">Optional Azure Storage Explorer</span></span>

<span data-ttu-id="ce4b4-132">애플리케이션 내의 UI에서 모든 데이터 변경 내용을 확인할 수 있지만 [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/)를 설치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-132">While you can see and verify all data changes from the UI inside the application, we recommend to install [Azure storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="ce4b4-133">이 도구를 사용하면 Azure 스토리지의 데이터를 시각적으로 볼 수 있으며 디버그하고 학습할 때 큰 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-133">This tool allows you to visually see the data in the Azure storage and is of great help when debugging and learning.</span></span>

> [!TIP]
> <span data-ttu-id="ce4b4-134">Unity 편집기 내에서 테스트하는 경우 로컬 에뮬레이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-134">For testing from inside the Unity editor you can use a local emulator:</span></span>

> * <span data-ttu-id="ce4b4-135">Windows 10에서는 [Azure 스토리지 에뮬레이터](https://docs.microsoft.com/azure/storage/common/storage-use-emulator)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-135">on Windows 10 you can use [Azure storage Emulator](https://docs.microsoft.com/azure/storage/common/storage-use-emulator)</span></span>
> * <span data-ttu-id="ce4b4-136">MacOS/Linux에서는 Docker용 [Azurite Docker Image](https://hub.docker.com/_/microsoft-azure-storage-azurite)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-136">on MacOS/Linux you can use [Azurite Docker Image](https://hub.docker.com/_/microsoft-azure-storage-azurite) for Docker</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="ce4b4-137">장면 준비</span><span class="sxs-lookup"><span data-stu-id="ce4b4-137">Preparing the scene</span></span>

<span data-ttu-id="ce4b4-138">[계층 구조] 창에서 **DataManager** 개체를 찾아서 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-138">In the Hierarchy window, locate the **DataManager** object and select it.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial2-section4-step1-1.png)

<span data-ttu-id="ce4b4-140">[검사기] 창에서 **DataManager(스크립트)** 구성 요소가 모든 **Azure 스토리지** 관련 설정을 유지하는 위치임을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-140">From the Inspector window you will see that the **DataManager (script)** component is where all **Azure storage** related settings are kept.</span></span> <span data-ttu-id="ce4b4-141">모든 관련 설정이 이미 설정되어 있으므로 *연결 문자열* 필드를 Azure Portal에서 검색할 수 있는 필드로 바꾸기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-141">All relevant settings are already set, you just need to replace the *Connection String* field with the one you can retrieve from the Azure Portal.</span></span> <span data-ttu-id="ce4b4-142">로컬 Azure 스토리지 에뮬레이터 솔루션을 사용하는 경우 이미 제공된 *연결 문자열*을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-142">If you are using a local Azure storage emulator solution, then you can keep the already provided *Connection String*.</span></span>

<span data-ttu-id="ce4b4-143">**DataManager(스크립트)** 는 UI 구성 요소의 다른 컨트롤러 스크립트에서 사용하는 **Table 스토리지** 및 **Blob 스토리지**와 통신해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-143">The **DataManager (script)** is responsible for talking to the **Table storage** and **Blob storage** which is consumed by other controller scripts on the UI components.</span></span>

## <a name="writing-and-reading-data-from-azure-table-storage"></a><span data-ttu-id="ce4b4-144">Azure Table 스토리지에서 데이터 쓰기 및 읽기</span><span class="sxs-lookup"><span data-stu-id="ce4b4-144">Writing and reading data from Azure Table storage</span></span>

<span data-ttu-id="ce4b4-145">모든 준비가 완료되면 이제 *추적된 개체*를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-145">With everything prepared it's time to create a *Tracked Object*.</span></span>

<span data-ttu-id="ce4b4-146">HoloLens에서 애플리케이션을 열고 **개체 설정**을 클릭합니다. 그러면 *EnterObjectName* 개체가 계층 구조에서 활성화되는 방법이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-146">Open the application on your HoloLens, click on the **Set Object** and you will see how the *EnterObjectName* object will become active in the hierarchy.</span></span> <span data-ttu-id="ce4b4-147">이 메뉴에서 *검색 창*을 클릭하고, *추적된 개체*에 지정하려는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-147">In this menu click on the *search bar* and type in the name you want to give the *Tracked Object*.</span></span> <span data-ttu-id="ce4b4-148">이름이 제공되면 **개체 설정** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-148">After providing a name click on the **Set object** button.</span></span> <span data-ttu-id="ce4b4-149">그러면 *추적된 개체*가 Azure Table 스토리지에 만들어지고, 이제 **개체 카드**가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-149">This will create the *Tracked Object* on the Azure Table storage and you will see now the **Object Card**.</span></span>

<span data-ttu-id="ce4b4-150">이 **개체 카드**는 *추적된 개체*에 대한 UI 표현이며, 이 자습서 시리즈에서 중요한 역할을 여러 번 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-150">This **Object Card** is a UI representation of the *Tracked Object* and will have an important role several times in this tutorial series.</span></span>

<span data-ttu-id="ce4b4-151">이제 설명 *텍스트 상자*를 클릭하고, "Car"를 입력한 다음, **저장** 단추를 클릭하여 변경 내용을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-151">Now click on the description *text box* and type in "Car", after that click on the **Save** button to save the changes.</span></span> <span data-ttu-id="ce4b4-152">애플리케이션을 중지하고 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-152">Stop the application and rerun it.</span></span>

<span data-ttu-id="ce4b4-153">이제 **개체 검색**을 클릭하고, *검색 창*에서 이전에 *추적된 개체*를 만들 때 사용한 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-153">Now this time click on **Search Object** and type in the *search bar* the name you have used before when creating the *Tracked Object*.</span></span> <span data-ttu-id="ce4b4-154">**Azure Table 스토리지**에서 모든 데이터가 포함된 **개체 카드**가 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-154">You will see that the **Object Card** with all the data is retrieved from the **Azure Table storage**.</span></span>

<span data-ttu-id="ce4b4-155">자유롭게 **개체 카드**를 닫고, 새 *추적된 개체*를 만들고, 해당 데이터를 편집해 보세요.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-155">Feel free to close the **Object Card** and create new *Tracked Objects* and edit their data.</span></span>

> [!TIP]
> <span data-ttu-id="ce4b4-156">[Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/)를 설치한 경우 *objects* 테이블을 살펴보면 만들어진 *추적된 개체*가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-156">If you have installed the [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) then look into the *objects* table and you will see there the created *Tracked Object*.</span></span>

## <a name="uploading-and-download-image-from-azure-blob-storage"></a><span data-ttu-id="ce4b4-157">Azure Blob 스토리지에서 이미지 업로드 및 다운로드</span><span class="sxs-lookup"><span data-stu-id="ce4b4-157">Uploading and Download image from Azure Blob storage</span></span>

<span data-ttu-id="ce4b4-158">이 섹션에서는 Azure Blob 스토리지를 사용하여 *추적된 개체*에 대한 썸네일로 사용될 이미지를 업로드 및 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-158">In this section you will use the Azure Blob storage to upload and download images that will be used as thumbnails for *Tracked Objects*.</span></span>

> [!NOTE]
> <span data-ttu-id="ce4b4-159">이 자습서에서는 애플리케이션에서 사진을 찍어 이미지를 Blob 스토리지에 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-159">In this tutorial the application will take photos to upload images to the Blob storage.</span></span> <span data-ttu-id="ce4b4-160">Unity 편집기에서 이 작업을 로컬로 실행하는 경우 웹캠이 컴퓨터에 연결되어 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-160">If you are running this locally from the Unity editor, then make sure that you have a webcam connected to your computer.</span></span>

<span data-ttu-id="ce4b4-161">HoloLens에서 애플리케이션을 열고, **개체 설정**을 클릭하고, *검색 창*에서 "Car"라는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-161">Open the application on your HoloLens, click on **Set Object** and type in the *search bar* the name "Car".</span></span> <span data-ttu-id="ce4b4-162">이제 **개체 카드**가 표시됩니다. **카메라** 단추를 클릭하면 AirTap을 수행하여 사진을 찍도록 지시하는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-162">Now you should see the **Object Card**, click on the **Camera** button and you will be instructed to do an AirTap to take a photo.</span></span> <span data-ttu-id="ce4b4-163">사진을 찍으면 활성 업로드를 알려주는 메시지가 표시되고, 잠시 후 이전에 자리 표시자가 있던 위치에 이미지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-163">After taking a photo you will see a message that informs you about the active upload and after a while the image should appear where the placeholder was before.</span></span>

<span data-ttu-id="ce4b4-164">이제 애플리케이션을 다시 실행하고 *추적된 개체*를 검색합니다. 그러면 이전에 업로드한 이미지가 썸네일로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-164">Now rerun the application and search for the *Tracked Object* and the previously uploaded image should appear as thumbnail.</span></span>

## <a name="deleting-image-from-azure-blob-storage"></a><span data-ttu-id="ce4b4-165">Azure Blob 스토리지에서 이미지 삭제</span><span class="sxs-lookup"><span data-stu-id="ce4b4-165">Deleting image from Azure Blob storage</span></span>

<span data-ttu-id="ce4b4-166">이전 섹션에서 새 이미지를 Azure Blob 스토리지에 업로드했습니다. 이 섹션에서는 *추적된 개체*에 대한 썸네일 이미지를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-166">In the previous section you uploaded new images to Azure Blob storage, in this section you will delete an image thumbnail for *Tracked Objects*.</span></span>

<span data-ttu-id="ce4b4-167">HoloLens에서 애플리케이션을 열고, **개체 설정**을 클릭하고, *검색 창*에서 "Car"라는 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-167">Open the application on your HoloLens, click on **Set Object** and type in the *search bar* the name "Car".</span></span> <span data-ttu-id="ce4b4-168">이제 썸네일 이미지가 있는 **개체 카드**가 표시됩니다. 그러면 **삭제** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-168">Now you should see the **Object Card** with the thumbnail image, click on the **Delete** button.</span></span> <span data-ttu-id="ce4b4-169">썸네일 이미지가 자리 표시자 이미지로 바뀌었습니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-169">You will notice that the thumbnail image is replaced by the placeholder image.</span></span>

<span data-ttu-id="ce4b4-170">이제 애플리케이션을 다시 실행하고, 이전에 삭제한 썸네일 이미지에 대한 *추적된 개체*를 검색합니다. 그러면 자리 표시자 이미지만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-170">Now rerun the application and search for the *Tracked Object* of the previously deleted thumbnail, you should only see the placeholder image.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ce4b4-171">축하합니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-171">Congratulations</span></span>

<span data-ttu-id="ce4b4-172">이 자습서에서는 **추적된 개체**의 경우 및 **HoloLens 2** 데모 애플리케이션에 대한 썸네일 이미지 형식의 이진 파일과 같이 Azure 스토리지 서비스를 사용하여 클라우드에서 비정형 데이터를 유지하는 방법을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-172">In this tutorial you learned how Azure storage services can be used to persist unstructured data, like in our case **Tracked Objects** and binaries in form of thumbnail images for the **HoloLens 2** demo application on the cloud.</span></span>

<span data-ttu-id="ce4b4-173">다음 자습서에서는 Azure Custom Vision을 사용하여 *추적된 개체*와 연결된 이미지를 감지하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="ce4b4-173">In the next tutorial you will learn how to use Azure Custom Vision to detect images associated with a *Tracked Object*.</span></span>

[<span data-ttu-id="ce4b4-174">다음 자습서: 3. Azure Custom Vision 통합</span><span class="sxs-lookup"><span data-stu-id="ce4b4-174">Next tutorial: 3. Integrating Azure Custom Vision</span></span>](mr-learning-azure-03.md)
