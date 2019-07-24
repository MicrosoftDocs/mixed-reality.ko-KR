---
title: MR 및 Azure 305-함수 및 저장소
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Storage 및 함수를 구현 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 함수, 저장소, hololens, 몰입 형, vr
ms.openlocfilehash: 5f3d0c6990249bc32e4c0f55c72dd884c4c2214e
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694554"
---
>[!NOTE]
><span data-ttu-id="b4dc8-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b4dc8-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b4dc8-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b4dc8-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b4dc8-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b4dc8-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="b4dc8-110">MR 및 Azure 305: 함수 및 저장소</span><span class="sxs-lookup"><span data-stu-id="b4dc8-110">MR and Azure 305: Functions and storage</span></span>

![최종 제품-시작](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="b4dc8-112">이 과정에서는 혼합 현실 응용 프로그램 내에서 Azure Storage 리소스를 사용 하 여 Azure Functions를 만들고 사용 하 고 데이터를 저장 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="b4dc8-113">*Azure Functions* 는 개발자가 Azure에서 작은 코드, ' 함수 '를 실행할 수 있도록 해 주는 Microsoft 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="b4dc8-114">이렇게 하면 다양 한 이점을 얻을 수 있는 로컬 응용 프로그램이 아닌 클라우드로 작업을 위임할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="b4dc8-115">*Azure Functions* 는 C\#, F\#, node.js, Java 및 PHP를 비롯 한 몇 가지 개발 언어를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="b4dc8-116">자세한 내용은 [Azure Functions 문서](https://docs.microsoft.com/azure/azure-functions/functions-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="b4dc8-117">*Azure Storage* 는 개발자가 데이터를 저장 하 고, 항상 사용 가능 하 고, 안전 하 고, 내구성이 있으며, 확장 가능 하 고, 중복 될 수 있는 보험 데이터를 저장할 수 있는 Microsoft 클라우드 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="b4dc8-118">즉, Microsoft는 모든 유지 관리 및 중요 한 문제를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="b4dc8-119">자세한 내용은 [Azure Storage 문서](https://docs.microsoft.com/azure/storage/common/storage-introduction)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="b4dc8-120">이 과정을 완료 하면 다음과 같은 작업을 수행할 수 있는 혼합 현실 모던 헤드셋 응용 프로그램이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="b4dc8-121">사용자가 장면을 응시 하도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="b4dc8-122">사용자가 3D ' 단추 '에서 gazes 때 개체 생성을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="b4dc8-123">생성 된 개체는 Azure Function에 의해 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="b4dc8-124">각 개체가 생성 될 때 응용 프로그램은 *Azure Storage*에 있는 *Azure 파일*에 개체 형식을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="b4dc8-125">두 번째로 로드 되 면 *Azure 파일* 데이터가 검색 되 고 응용 프로그램의 이전 인스턴스에서 생성 작업을 재생 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="b4dc8-126">응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="b4dc8-127">이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="b4dc8-128">이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="b4dc8-129">장치 지원</span><span class="sxs-lookup"><span data-stu-id="b4dc8-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b4dc8-130">과정</span><span class="sxs-lookup"><span data-stu-id="b4dc8-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b4dc8-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b4dc8-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b4dc8-132"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="b4dc8-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="b4dc8-133">MR 및 Azure 305: 함수 및 저장소</span><span class="sxs-lookup"><span data-stu-id="b4dc8-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="b4dc8-134">✔️</span><span class="sxs-lookup"><span data-stu-id="b4dc8-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b4dc8-135">✔️</span><span class="sxs-lookup"><span data-stu-id="b4dc8-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="b4dc8-136">이 과정에서 주로 Windows Mixed Reality (VR) 헤드셋에 초점을 맞춘 반면,이 과정에서 학습 하는 내용을 Microsoft HoloLens에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="b4dc8-137">과정을 진행할 때 HoloLens를 지원 하기 위해 사용 해야 하는 모든 변경 내용에 대 한 메모를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b4dc8-138">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b4dc8-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b4dc8-139">이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b4dc8-140">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="b4dc8-141">[도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="b4dc8-142">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b4dc8-143">모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC</span><span class="sxs-lookup"><span data-stu-id="b4dc8-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="b4dc8-144">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="b4dc8-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b4dc8-145">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="b4dc8-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b4dc8-146">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="b4dc8-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b4dc8-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b4dc8-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="b4dc8-148">개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="b4dc8-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="b4dc8-149">Azure 리소스를 만들기 위한 Azure 계정에 대 한 구독</span><span class="sxs-lookup"><span data-stu-id="b4dc8-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="b4dc8-150">Azure 설정 및 데이터 검색을 위한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="b4dc8-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="b4dc8-151">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="b4dc8-151">Before you start</span></span>

<span data-ttu-id="b4dc8-152">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="b4dc8-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="b4dc8-153">1 장-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="b4dc8-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="b4dc8-154">**Azure Storage 서비스**를 사용 하려면 Azure Portal에서 **저장소 계정을** 만들고 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="b4dc8-155">[Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b4dc8-156">아직 Azure 계정이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="b4dc8-157">교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="b4dc8-158">로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 *저장소 계정*을 검색 한 다음 **Enter 키**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![azure 저장소 검색](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="b4dc8-160">새 단어는 **새** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="b4dc8-161">새 페이지에 *Azure Storage 계정* 서비스에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="b4dc8-162">이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![서비스 만들기](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="b4dc8-164">**만들기**를 클릭 하면 다음을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="b4dc8-165">계정에 대 한 *이름을* 삽입 합니다 .이 필드에는 숫자 및 소문자만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="b4dc8-166">*배포 모델*에서 **Resource manager**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="b4dc8-167">*계정 종류*에 대해 **저장소 (범용 v1)** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="b4dc8-168">새 리소스 그룹을 만드는 경우 리소스 그룹의 *위치* 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="b4dc8-169">위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="b4dc8-170">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="b4dc8-171">*복제* 의 경우 **읽기 액세스-지역 중복 저장소 (RA-GRS)** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="b4dc8-172">*성능*으로 **표준**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="b4dc8-173">*보안 전송을* **사용 하지 않도록 설정**해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="b4dc8-174">*구독*을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="b4dc8-175">리소스 그룹을 선택 하거나 새 *리소스 그룹* 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="b4dc8-176">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b4dc8-177">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="b4dc8-178">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="b4dc8-179">또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="b4dc8-180">**만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-180">Select **Create**.</span></span>

        ![입력 서비스 정보](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="b4dc8-182">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="b4dc8-183">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![azure portal의 새 알림](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="b4dc8-185">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-185">Click on the notifications to explore your new Service instance.</span></span>

    ![리소스로 이동](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="b4dc8-187">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="b4dc8-188">새 *저장소 계정* 서비스 인스턴스로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![액세스 키](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="b4dc8-190">*액세스 키*를 클릭 하 여이 클라우드 서비스에 대 한 끝점을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="b4dc8-191">*메모장* 이나 유사한를 사용 하 여 나중에 사용 하기 위해 키 중 하나를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="b4dc8-192">또한 나중에 만들 *Azureservices* 클래스에서 사용 되는 *연결 문자열* 값을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![연결 문자열 복사](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="b4dc8-194">2 장-Azure Function 설정</span><span class="sxs-lookup"><span data-stu-id="b4dc8-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="b4dc8-195">이제 azure 서비스에서 **azure** **Function** 을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="b4dc8-196">**Azure 함수** 를 사용 하 여 코드에서 클래식 함수를 사용 하 여 수행 하는 거의 모든 작업을 수행할 수 있습니다. azure 계정에 액세스 하기 위한 자격 증명이 있는 응용 프로그램에서이 함수에 액세스할 수 있다는 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="b4dc8-197">Azure 함수를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="b4dc8-198">*Azure Portal*의 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 *함수 앱*를 검색 한 다음 **Enter 키**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![함수 앱 만들기](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="b4dc8-200">새 단어는 **새** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="b4dc8-201">새 페이지에는 *Azure 함수 앱* 서비스에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="b4dc8-202">이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![함수 앱 정보](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="b4dc8-204">**만들기**를 클릭 하면 다음을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="b4dc8-205">*앱 이름을*제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-205">Provide an *App name*.</span></span> <span data-ttu-id="b4dc8-206">여기에는 문자와 숫자만 사용할 수 있습니다 (대문자나 소문자가 허용 됨).</span><span class="sxs-lookup"><span data-stu-id="b4dc8-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="b4dc8-207">선호 하는 *구독*을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="b4dc8-208">리소스 그룹을 선택 하거나 새 *리소스 그룹* 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="b4dc8-209">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b4dc8-210">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="b4dc8-211">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="b4dc8-212">이 연습에서는 선택 된 **OS**로 *Windows* 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="b4dc8-213">**호스팅 계획**에 대 한 *소비 계획* 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="b4dc8-214">새 리소스 그룹을 만드는 경우 리소스 그룹의 *위치* 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="b4dc8-215">위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="b4dc8-216">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="b4dc8-217">성능을 최적화 하려면 저장소 계정과 동일한 지역을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="b4dc8-218">*저장소*의 경우 **기존 사용**을 선택 하 고 드롭다운 메뉴를 사용 하 여 이전에 만든 저장소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="b4dc8-219">이 연습에서는 *Application Insights* off로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-219">Leave *Application Insights* off for this exercise.</span></span>

        ![입력 함수 앱 세부 정보](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="b4dc8-221">**만들기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="b4dc8-222">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="b4dc8-223">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![새 azure portal 알림](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="b4dc8-225">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![리소스 함수 앱으로 이동](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="b4dc8-227">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="b4dc8-228">새 *함수 앱* 서비스 인스턴스로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="b4dc8-229">*함수 앱* 대시보드에서 왼쪽의 패널 내에서 *함수*위로 마우스를 가져간 다음 **+ (더하기)** 기호를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![새 함수 만들기](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="b4dc8-231">다음 페이지에서 **Webhook + API** 가 선택 되어 있는지 확인 하 고 *언어 선택에서* **CSharp**를 선택 합니다 .이는이 자습서에 사용 되는 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="b4dc8-232">마지막으로 **이 함수 만들기** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-232">Lastly, click the **Create this function** button.</span></span>

    ![웹 후크 csharp 선택](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="b4dc8-234">그러나 코드 페이지 (csx)로 이동 해야 합니다. 그렇지 않으면 왼쪽 패널의 함수 목록에서 새로 만든 함수를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![새 함수 열기](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="b4dc8-236">함수에 다음 코드를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-236">Copy the following code into your function.</span></span> <span data-ttu-id="b4dc8-237">이 함수는 호출 될 때 0과 2 사이의 임의의 정수를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="b4dc8-238">기존 코드에 대해 걱정 하지 마세요. 맨 위에 자유롭게 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. <span data-ttu-id="b4dc8-239">**저장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-239">Select **Save**.</span></span>

14. <span data-ttu-id="b4dc8-240">결과는 아래 이미지와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="b4dc8-241">**함수 URL 가져오기** 를 클릭 하 고 표시 된 *끝점* 을 기록해 둡니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="b4dc8-242">이 과정의 뒷부분에서 만들 *Azureservices* 클래스에 삽입 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![함수 끝점 가져오기](images/AzureLabs-Lab5-16.png)

    ![함수 끝점 가져오기](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="b4dc8-245">3 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="b4dc8-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="b4dc8-246">다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="b4dc8-247">혼합 현실 모던 헤드셋을 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="b4dc8-248">이 과정에서는 동작 컨트롤러가 필요 **하지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="b4dc8-249">몰입 형 헤드셋을 설정 하는 데 지원이 필요한 경우 [혼합 현실 설정 문서를 참조](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)하세요.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="b4dc8-250">Unity를 열고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-250">Open Unity and click **New**.</span></span>

    ![새 unity 프로젝트 만들기](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="b4dc8-252">이제 Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="b4dc8-253">**MR_Azure_Functions**을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="b4dc8-254">프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="b4dc8-255">위치를 적절 한 *위치* 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b4dc8-256">그런 다음 **프로젝트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-256">Then, click **Create project**.</span></span>

    ![새 unity 프로젝트에 이름을 지정 합니다.](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="b4dc8-258">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b4dc8-259">**기본 설정** **편집** > 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-259">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b4dc8-260">**외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="b4dc8-261">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-261">Close the **Preferences** window.</span></span>

    ![visual studio를 스크립트 편집기로 설정](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="b4dc8-263">그런 다음 **파일** > **빌드 설정** 으로 이동 하 고 플랫폼 **전환** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼**로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-263">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![플랫폼을 uwp로 전환](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="b4dc8-265">**파일** > **빌드 설정** 으로 이동 하 여 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-265">Go to **File** > **Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="b4dc8-266">**대상 장치** 는 **임의의 장치로**설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="b4dc8-267">Microsoft HoloLens의 경우 **대상 장치** 를 *HoloLens*로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="b4dc8-268">**빌드 형식이** **D3D** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="b4dc8-269">**SDK** 가 **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="b4dc8-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="b4dc8-270">**Visual Studio 버전이** **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="b4dc8-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="b4dc8-271">**빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="b4dc8-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="b4dc8-272">장면을 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="b4dc8-273">이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="b4dc8-274">저장 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-274">A save window will appear.</span></span>

            ![열려 있는 장면 추가](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="b4dc8-276">이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을**로 지정한 다음</span><span class="sxs-lookup"><span data-stu-id="b4dc8-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![배경 폴더 만들기](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="b4dc8-278">새로 만든 **장면** 폴더를 연 다음 **파일 이름:** 텍스트 필드에 **FunctionsScene**를 입력 하 고 **저장**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![함수 장면 저장](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="b4dc8-280">**빌드 설정**의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![함수 장면 저장](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="b4dc8-282">*빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![검사기의 플레이어 설정](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="b4dc8-284">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="b4dc8-285">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="b4dc8-286">**Scripting Runtime 버전** 은 **실험적** (.net 4.6 이와 동일) 이어야 하며,이 경우 편집기를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="b4dc8-287">**Scripting 백엔드** 는 **.net** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="b4dc8-288">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="b4dc8-289">**게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="b4dc8-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-290">**InternetClient**</span></span>

            ![기능 설정](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="b4dc8-292">패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![XR 설정 설정](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="b4dc8-294">*빌드 설정* 으로 돌아가서 *Unity C# 프로젝트가* 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![tick c # 프로젝트](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="b4dc8-296">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="b4dc8-297">장면 및 프로젝트를 저장 합니다 (**파일** > **저장 장면/파일** > **저장 프로젝트**).</span><span class="sxs-lookup"><span data-stu-id="b4dc8-297">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="b4dc8-298">4 장-기본 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="b4dc8-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4dc8-299">이 과정의 *Unity 설정* 구성 요소를 건너뛰고 바로 코드를 계속 진행 하려는 경우 [unitypackage를 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)하 여 [사용자 지정 패키지로](https://docs.unity3d.com/Manual/AssetPackages.html)프로젝트에 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="b4dc8-300">여기에는 다음 챕터의 Dll도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="b4dc8-301">가져온 후 [7 장](#chapter-7---create-the-azureservices-class)에서 계속 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="b4dc8-302">*계층 패널*에서 **주 카메라**라는 개체를 찾을 수 있습니다 .이 개체는 응용 프로그램 "내부"에 있는 경우의 "헤드" 관점을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="b4dc8-303">앞의 Unity 대시보드를 사용 하 여 **기본 카메라 GameObject**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="b4dc8-304">*검사기 패널* (일반적으로 대시보드 내에서 오른쪽에 있음)에는 해당 *GameObject*의 다양 한 구성 요소, 위쪽의 *변환* , *카메라*및 기타 구성 요소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="b4dc8-305">기본 카메라의 변환을 다시 설정 해야 올바른 위치에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="b4dc8-306">이렇게 하려면 카메라의 *변형* 구성 요소 옆에 있는 **기어** 아이콘을 선택 하 고 **다시 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![변환 다시 설정](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="b4dc8-308">그런 다음 **변형** 구성 요소를 다음과 같이 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="b4dc8-309">변환 위치</span><span class="sxs-lookup"><span data-stu-id="b4dc8-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="b4dc8-310">**X**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-310">**X**</span></span>   | <span data-ttu-id="b4dc8-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-311">**Y**</span></span>                     | <span data-ttu-id="b4dc8-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-312">**Z**</span></span> |
    | <span data-ttu-id="b4dc8-313">0</span><span class="sxs-lookup"><span data-stu-id="b4dc8-313">0</span></span>       | <span data-ttu-id="b4dc8-314">1</span><span class="sxs-lookup"><span data-stu-id="b4dc8-314">1</span></span>                         | <span data-ttu-id="b4dc8-315">0</span><span class="sxs-lookup"><span data-stu-id="b4dc8-315">0</span></span>     |    

    |       | <span data-ttu-id="b4dc8-316">변환-회전</span><span class="sxs-lookup"><span data-stu-id="b4dc8-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="b4dc8-317">**X**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-317">**X**</span></span> | <span data-ttu-id="b4dc8-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-318">**Y**</span></span>                | <span data-ttu-id="b4dc8-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-319">**Z**</span></span> |
    | <span data-ttu-id="b4dc8-320">0</span><span class="sxs-lookup"><span data-stu-id="b4dc8-320">0</span></span>     | <span data-ttu-id="b4dc8-321">0</span><span class="sxs-lookup"><span data-stu-id="b4dc8-321">0</span></span>                    | <span data-ttu-id="b4dc8-322">0</span><span class="sxs-lookup"><span data-stu-id="b4dc8-322">0</span></span>     |

    |       | <span data-ttu-id="b4dc8-323">변환-배율</span><span class="sxs-lookup"><span data-stu-id="b4dc8-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="b4dc8-324">**X**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-324">**X**</span></span> | <span data-ttu-id="b4dc8-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-325">**Y**</span></span>             | <span data-ttu-id="b4dc8-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-326">**Z**</span></span> |
    | <span data-ttu-id="b4dc8-327">1</span><span class="sxs-lookup"><span data-stu-id="b4dc8-327">1</span></span>     | <span data-ttu-id="b4dc8-328">1</span><span class="sxs-lookup"><span data-stu-id="b4dc8-328">1</span></span>                 | <span data-ttu-id="b4dc8-329">1</span><span class="sxs-lookup"><span data-stu-id="b4dc8-329">1</span></span>     |

    ![카메라 변환 설정](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="b4dc8-331">5 장-Unity 장면 설정</span><span class="sxs-lookup"><span data-stu-id="b4dc8-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="b4dc8-332">*계층 패널*의 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 **3d 개체**아래에서 **평면**을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![새 평면 만들기](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="b4dc8-334">**평면** 개체가 선택 된 상태에서 *Inspector 패널*의 다음 매개 변수를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="b4dc8-335">변환 위치</span><span class="sxs-lookup"><span data-stu-id="b4dc8-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="b4dc8-336">**X**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-336">**X**</span></span> | <span data-ttu-id="b4dc8-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-337">**Y**</span></span>                | <span data-ttu-id="b4dc8-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-338">**Z**</span></span> |
    | <span data-ttu-id="b4dc8-339">0</span><span class="sxs-lookup"><span data-stu-id="b4dc8-339">0</span></span>     | <span data-ttu-id="b4dc8-340">0</span><span class="sxs-lookup"><span data-stu-id="b4dc8-340">0</span></span>                    | <span data-ttu-id="b4dc8-341">4</span><span class="sxs-lookup"><span data-stu-id="b4dc8-341">4</span></span>     |

    |       | <span data-ttu-id="b4dc8-342">변환-배율</span><span class="sxs-lookup"><span data-stu-id="b4dc8-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="b4dc8-343">**X**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-343">**X**</span></span> | <span data-ttu-id="b4dc8-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-344">**Y**</span></span>             | <span data-ttu-id="b4dc8-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-345">**Z**</span></span> |
    | <span data-ttu-id="b4dc8-346">10</span><span class="sxs-lookup"><span data-stu-id="b4dc8-346">10</span></span>    | <span data-ttu-id="b4dc8-347">1</span><span class="sxs-lookup"><span data-stu-id="b4dc8-347">1</span></span>                 | <span data-ttu-id="b4dc8-348">10</span><span class="sxs-lookup"><span data-stu-id="b4dc8-348">10</span></span>    |

    ![평면 위치 및 배율 설정](images/AzureLabs-Lab5-32.png)

    ![평면의 장면 보기](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="b4dc8-351">*계층 패널*의 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 **3d 개체**아래에서 **큐브**를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="b4dc8-352">큐브 이름을 **GazeButton** 로 바꿉니다 (큐브를 선택 하 고 ' F2 '를 누릅니다).</span><span class="sxs-lookup"><span data-stu-id="b4dc8-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="b4dc8-353">*검사기 패널*에서 다음 매개 변수를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="b4dc8-354">변환 위치</span><span class="sxs-lookup"><span data-stu-id="b4dc8-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="b4dc8-355">**X**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-355">**X**</span></span> | <span data-ttu-id="b4dc8-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-356">**Y**</span></span>                | <span data-ttu-id="b4dc8-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-357">**Z**</span></span> |
        | <span data-ttu-id="b4dc8-358">0</span><span class="sxs-lookup"><span data-stu-id="b4dc8-358">0</span></span>     | <span data-ttu-id="b4dc8-359">3</span><span class="sxs-lookup"><span data-stu-id="b4dc8-359">3</span></span>                    | <span data-ttu-id="b4dc8-360">5</span><span class="sxs-lookup"><span data-stu-id="b4dc8-360">5</span></span>     |


        ![응시 단추 변환 설정](images/AzureLabs-Lab5-34.png)

        ![응시 단추 장면 보기](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="b4dc8-363">태그 **드롭다운 단추** 를 클릭 하 고 **태그 추가** 를 클릭 하 여 *& 레이어 창 태그*를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![새 태그 추가](images/AzureLabs-Lab5-36.png)

        ![더하기 더하기](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="b4dc8-366">**+ (더하기)** 단추를 선택 하 고 *새 태그 이름* 필드에 **GazeButton**를 입력 하 고 **저장**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![새 태그 이름](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="b4dc8-368">*계층 패널*에서 **GazeButton** 개체를 클릭 하 고 *검사기 패널*에서 새로 만든 **GazeButton** 태그를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![새 태그에 응시 단추 할당](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="b4dc8-370">*계층 패널*에서 **GazeButton** 개체를 마우스 오른쪽 단추로 클릭 하 고 **빈 GameObject** ( *자식* 개체로 추가 됨)를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="b4dc8-371">새 개체를 선택 하 고 이름을 지정 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="b4dc8-372">*검사기 패널*에서 다음 매개 변수를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="b4dc8-373">변환 위치</span><span class="sxs-lookup"><span data-stu-id="b4dc8-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="b4dc8-374">**X**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-374">**X**</span></span> |<span data-ttu-id="b4dc8-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-375">**Y**</span></span>                 | <span data-ttu-id="b4dc8-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-376">**Z**</span></span> |
        | <span data-ttu-id="b4dc8-377">0</span><span class="sxs-lookup"><span data-stu-id="b4dc8-377">0</span></span>     | <span data-ttu-id="b4dc8-378">-1</span><span class="sxs-lookup"><span data-stu-id="b4dc8-378">-1</span></span>                   | <span data-ttu-id="b4dc8-379">0</span><span class="sxs-lookup"><span data-stu-id="b4dc8-379">0</span></span>     |

        ![셰이프 생성 지점 변환 업데이트](images/AzureLabs-Lab5-40.png)

        ![셰이프 생성 지점 장면 보기](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="b4dc8-382">다음으로, Azure 서비스의 상태에 대 한 피드백을 제공 하는 **3D 텍스트** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="b4dc8-383">계층 패널에서 **GazeButton** 를 마우스 오른쪽 단추로 다시 클릭 하 고 **3d 개체** > **3d 텍스트** 개체를 *자식*으로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object** > **3D Text** object as a *child*.</span></span>

    ![새 3D 텍스트 개체 만들기](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="b4dc8-385">**3D 텍스트** 개체의 이름을 **AzureStatusText**로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="b4dc8-386">**AzureStatusText** 개체 변환을 다음과 같이 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="b4dc8-387">변환 위치</span><span class="sxs-lookup"><span data-stu-id="b4dc8-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="b4dc8-388">**X**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-388">**X**</span></span> | <span data-ttu-id="b4dc8-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-389">**Y**</span></span>                | <span data-ttu-id="b4dc8-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-390">**Z**</span></span> |
    | <span data-ttu-id="b4dc8-391">0</span><span class="sxs-lookup"><span data-stu-id="b4dc8-391">0</span></span>     | <span data-ttu-id="b4dc8-392">0</span><span class="sxs-lookup"><span data-stu-id="b4dc8-392">0</span></span>                    | <span data-ttu-id="b4dc8-393">-0.6</span><span class="sxs-lookup"><span data-stu-id="b4dc8-393">-0.6</span></span>  |

    |       | <span data-ttu-id="b4dc8-394">변환-배율</span><span class="sxs-lookup"><span data-stu-id="b4dc8-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="b4dc8-395">**X**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-395">**X**</span></span> | <span data-ttu-id="b4dc8-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-396">**Y**</span></span>             | <span data-ttu-id="b4dc8-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="b4dc8-397">**Z**</span></span> |
    | <span data-ttu-id="b4dc8-398">0.1</span><span class="sxs-lookup"><span data-stu-id="b4dc8-398">0.1</span></span>   | <span data-ttu-id="b4dc8-399">0.1</span><span class="sxs-lookup"><span data-stu-id="b4dc8-399">0.1</span></span>               | <span data-ttu-id="b4dc8-400">0.1</span><span class="sxs-lookup"><span data-stu-id="b4dc8-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="b4dc8-401">외부에 있는 것 처럼 표시 되는 경우 걱정 하지 마세요 .이는 아래 텍스트 메시 구성 요소가 업데이트 될 때 수정 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="b4dc8-402">아래와 일치 하도록 **텍스트 메시** 구성 요소를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-402">Change the **Text Mesh** component to match the below:</span></span>

    ![텍스트 메시 구성 요소 설정](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="b4dc8-404">선택한 색은 16 진수 색입니다. **000000Ff**는 자유롭게 선택할 수 있지만 읽을 수 있는지 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="b4dc8-405">이제 계층 구조 패널 구조가 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![장면 뷰의 텍스트 메시](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="b4dc8-407">이제 장면이 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-407">Your scene should now look like this:</span></span>

    ![장면 뷰의 텍스트 메시](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="b4dc8-409">6 장-Unity Azure Storage 가져오기</span><span class="sxs-lookup"><span data-stu-id="b4dc8-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="b4dc8-410">Unity에 Azure Storage를 사용 하 게 됩니다 (자체는 Azure 용 .Net SDK를 활용).</span><span class="sxs-lookup"><span data-stu-id="b4dc8-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="b4dc8-411">이에 대 한 자세한 내용은 [Unity의 Azure Storage 문서](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="b4dc8-412">현재 Unity에는 가져온 후 플러그 인을 다시 구성 해야 하는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="b4dc8-413">이러한 단계 (이 섹션에서는 4-7)는 버그가 해결 된 후 더 이상 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="b4dc8-414">SDK를 고유한 프로젝트로 가져오려면 [GitHub에서 최신 '. unitypackage '](https://aka.ms/azstorage-unitysdk)를 다운로드 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="b4dc8-415">그런 후에 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-415">Then, do the following:</span></span>

1.  <span data-ttu-id="b4dc8-416">**자산** **가져오기 패키지 사용자 지정** **패키지** 메뉴 옵션을 사용 하 여 unitypackage 파일을 Unity에 추가 합니다.   >  > </span><span class="sxs-lookup"><span data-stu-id="b4dc8-416">Add the **.unitypackage** file to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="b4dc8-417">표시 되는 **Unity 패키지 가져오기** 상자에서 **플러그 인** > **저장소**아래의 모든 항목을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-417">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span> <span data-ttu-id="b4dc8-418">이 과정에서 필요 하지 않으므로 다른 모든 항목을 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![패키지로 가져오기](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="b4dc8-420">**가져오기** 단추를 클릭 하 여 프로젝트에 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="b4dc8-421">프로젝트 뷰에서 *플러그 인*의 *저장소* 폴더로 이동 하 고 다음 플러그 인 *만*선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="b4dc8-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="b4dc8-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="b4dc8-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="b4dc8-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="b4dc8-424">Windowsazure.servicebus</span><span class="sxs-lookup"><span data-stu-id="b4dc8-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="b4dc8-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="b4dc8-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="b4dc8-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="b4dc8-426">System.Spatial</span></span>

        ![모든 플랫폼 선택 취소](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="b4dc8-428">*이러한 특정 플러그* 인을 선택 하 고 *플랫폼* 을 선택 **취소** 하 고 *WSAPlayer* **선택을 취소** 한 후 **적용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![플랫폼 dll 적용](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="b4dc8-430">이러한 특정 플러그인을 Unity 편집기 에서만 사용 하도록 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="b4dc8-431">이는 프로젝트를 Unity에서 내보낸 후에 사용 되는 WSA 폴더에 동일한 플러그 인의 버전이 서로 다르기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="b4dc8-432">*저장소* 플러그 인 폴더에서 다음만을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="b4dc8-433">Microsoft. Data. Service. 클라이언트</span><span class="sxs-lookup"><span data-stu-id="b4dc8-433">Microsoft.Data.Services.Client</span></span>

        ![dll에 대해 처리 안 함 설정](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="b4dc8-435">*플랫폼 설정* 에서 **처리 안 함** 상자를 선택 하 고 **적용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![처리 안 함 적용](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="b4dc8-437">Unity 어셈블리 patcher이 플러그 인을 처리 하는 데 어려움을 겪고 있으므로이 플러그 인을 "처리 안 함"으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="b4dc8-438">플러그 인은 처리 되지 않은 경우에도 계속 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="b4dc8-439">7 장-AzureServices 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b4dc8-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="b4dc8-440">만들려는 첫 번째 클래스는 *Azureservices* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="b4dc8-441">*Azureservices* 클래스는 다음과 같은 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="b4dc8-442">Azure 계정 자격 증명을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="b4dc8-443">Azure 앱 함수를 호출 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="b4dc8-444">Azure 클라우드 저장소에 데이터 파일을 업로드 하 고 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="b4dc8-445">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b4dc8-445">To create this Class:</span></span>

1.  <span data-ttu-id="b4dc8-446">프로젝트 패널에 있는 *자산* 폴더를 마우스 오른쪽 단추로 클릭 하 고**폴더** **만들기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="b4dc8-447">폴더 이름을 **스크립트**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-447">Name the folder **Scripts**.</span></span>

    ![새 폴더 만들기](images/AzureLabs-Lab5-50.png)

    ![호출 폴더-스크립트](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="b4dc8-450">위에서 만든 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="b4dc8-451">폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **C# 스크립트**를 **만듭니다**  >  .</span><span class="sxs-lookup"><span data-stu-id="b4dc8-451">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="b4dc8-452">*Azureservices*스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="b4dc8-453">새 *Azureservices* 클래스를 두 번 클릭 하 여 *Visual Studio*에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="b4dc8-454">*Azureservices*의 맨 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="b4dc8-455">*Azureservices* 클래스 내부에 다음 Inspector 필드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  <span data-ttu-id="b4dc8-456">그런 다음 *Azureservices* 클래스 내에 다음 멤버 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-456">Then add the following member variables inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="b4dc8-457">*끝점* 및 *연결 문자열* 값을 Azure Portal에 있는 azure storage의 값으로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="b4dc8-458">이제 *활성 ()* 및 *Start ()* 메서드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="b4dc8-459">이러한 메서드는 클래스가 초기화 될 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-459">These methods will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="b4dc8-460">[이후 장에서](#chapter-10---completing-the-azureservices-class) *CallAzureFunctionForNextShape ()* 에 대 한 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-azureservices-class).</span></span>

9.  <span data-ttu-id="b4dc8-461">이 클래스는 사용 하지 않으므로 *Update ()* 메서드를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="b4dc8-462">Visual Studio에서 변경 내용을 저장 한 다음 Unity로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="b4dc8-463">Scripts 폴더에서 *Azureservices* 클래스를 클릭 하 고 *계층 패널*의 기본 카메라 개체로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="b4dc8-464">기본 카메라를 선택 하 고 **GazeButton** 개체 아래에서 **AzureStatusText** 자식 개체를 선택한 다음, *검사기*에서 **AzureStatusText** 참조 대상 필드 내에 추가 하 여 다음에 *대 한 참조를 제공 합니다. AzureServices* 스크립트.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![azure 상태 텍스트 참조 대상 할당](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="b4dc8-466">8 장-ShapeFactory 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b4dc8-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="b4dc8-467">만들 다음 스크립트는 *ShapeFactory* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="b4dc8-468">이 클래스의 역할은 요청 시 새 셰이프를 만들고 *셰이프 기록 목록*에서 만든 셰이프의 기록을 유지 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="b4dc8-469">셰이프를 만들 때마다 *Azureservice* 클래스에서 *셰이프 기록 목록이* 업데이트 된 다음 *Azure Storage*에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="b4dc8-470">응용 프로그램이 시작 되 면 저장 된 파일이 *Azure Storage*에 있는 경우 *셰이프 기록 목록이* 검색 되어 재생 되 고, 생성 된 셰이프가 저장소에서 온 것인지, 아니면 새 인지를 제공 하는 **3d 텍스트** 개체가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="b4dc8-471">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b4dc8-471">To create this class:</span></span>

1.  <span data-ttu-id="b4dc8-472">이전에 만든 **스크립트** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="b4dc8-473">폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **C# 스크립트**를 **만듭니다**  >  .</span><span class="sxs-lookup"><span data-stu-id="b4dc8-473">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="b4dc8-474">*ShapeFactory*스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="b4dc8-475">새 *ShapeFactory* 스크립트를 두 번 클릭 하 여 *Visual Studio*에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="b4dc8-476">*ShapeFactory* 클래스에 다음 네임 스페이스가 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="b4dc8-477">아래에 표시 된 변수를 *ShapeFactory* 클래스에 추가 하 고 *Start ()* 및 *활성 ()* 함수를 아래와 같이 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  <span data-ttu-id="b4dc8-478">*CreateShape ()* 메서드는 제공 된 *정수* 매개 변수를 기반으로 기본 도형을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="b4dc8-479">부울 매개 변수를 사용 하 여 현재 생성 된 셰이프가 저장소에서 생성 되었는지 아니면 새 셰이프 인지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="b4dc8-480">이전 메서드 아래에 *ShapeFactory* 클래스에 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  <span data-ttu-id="b4dc8-481">Unity로 반환 하기 전에 Visual Studio에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="b4dc8-482">Unity 편집기로 돌아가서 **Scripts** 폴더의 *ShapeFactory* 클래스를 클릭 하 여 *계층 패널*의 **기본 카메라** 개체로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="b4dc8-483">기본 카메라를 선택 하면 *ShapeFactory* script 구성 요소에 *생성 지점* 참조가 없다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="b4dc8-484">이 문제를 해결 하려면 *계층 패널* 에서 **생성 지점** 참조 대상으로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![셰이프 팩터리 참조 대상 설정](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="b4dc8-486">9 장-응시 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b4dc8-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="b4dc8-487">생성 해야 하는 마지막 스크립트는 *응시* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="b4dc8-488">이 클래스는 사용자가 보고 있는 개체를 검색 하기 위해 기본 카메라에서 앞으로 프로젝션 될 **Raycast** 를 만드는 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="b4dc8-489">이 경우에는 사용자가 장면의 **GazeButton** 개체를 보고 동작을 트리거할 수 있는지 여부를 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="b4dc8-490">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b4dc8-490">To create this Class:</span></span>

1.  <span data-ttu-id="b4dc8-491">이전에 만든 **스크립트** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="b4dc8-492">프로젝트 패널을 마우스 오른쪽 단추로 클릭 하 고 **C# 스크립트**를 **만듭니다**  >  .</span><span class="sxs-lookup"><span data-stu-id="b4dc8-492">Right-click in the Project Panel, **Create** > **C# Script**.</span></span> <span data-ttu-id="b4dc8-493">스크립트 *응시*를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="b4dc8-494">새 *응시* 스크립트를 두 번 클릭 하 여 *Visual Studio* 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="b4dc8-495">스크립트의 맨 위에 다음 네임 스페이스가 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="b4dc8-496">그런 다음, 다음 변수를 *응시* 클래스 내에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-496">Then add the following variables inside the *Gaze* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> <span data-ttu-id="b4dc8-497">이러한 변수 중 일부는 *편집기*에서 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="b4dc8-498">이제 해제 *()* 및 *Start ()* 메서드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="b4dc8-499">다음 코드를 추가 합니다 .이 메서드는 GazeEnabled 부울이 전환 되는 위치와 함께 Raycast 메서드를 실행 하는 *Update ()* 메서드와 함께 시작 시 커서 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. <span data-ttu-id="b4dc8-500">그런 다음 *UpdateRaycast ()* 메서드를 추가 합니다 .이 메서드는 Raycast를 프로젝션 하 고 적중 대상을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. <span data-ttu-id="b4dc8-501">마지막으로 *ResetFocusedObject ()* 메서드를 추가 합니다 .이 메서드는 GazeButton 개체의 현재 색을 설정 하 여 새 셰이프를 만들지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  <span data-ttu-id="b4dc8-502">Unity로 반환 하기 전에 Visual Studio에서 변경 내용을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="b4dc8-503">Scripts 폴더의 Scripts *클래스를* 클릭 하 고 *계층 패널*의 **기본 카메라** 개체로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="b4dc8-504">10 장-AzureServices 클래스 완료</span><span class="sxs-lookup"><span data-stu-id="b4dc8-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="b4dc8-505">다른 스크립트를 사용 하 여 이제 *Azureservices* 클래스를 *완료할* 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="b4dc8-506">다음을 통해이를 달성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="b4dc8-507">*CreateCloudIdentityAsync ()* 라는 새 메서드를 추가 하 여 Azure와의 통신에 필요한 인증 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="b4dc8-508">이 메서드는 또한 셰이프 목록이 포함 된 이전에 저장 된 파일의 존재 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="b4dc8-509">**파일이 검색 되 면** *사용자가*이를 사용 하지 않도록 설정 하 고, **Azure Storage 파일**에 저장 된 모양의 패턴에 따라 셰이프 생성을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="b4dc8-510">**텍스트 메쉬가** 셰이프 원점에 따라 ' Storage ' 또는 ' New ' 표시를 제공 하므로 사용자는이를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="b4dc8-511">**파일이 없는 경우**에는 사용자가 장면의 **GazeButton** 개체를 볼 때 셰이프를 만들 수 있도록 *응시*를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  <span data-ttu-id="b4dc8-512">다음 코드 조각은 *Start ()* 메서드 내에 있습니다. *CreateCloudIdentityAsync ()* 메서드에 대 한 호출을 수행 하는 것을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="b4dc8-513">다음과 같이 현재 *Start ()* 메서드를 사용 하 여 자유롭게 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  <span data-ttu-id="b4dc8-514">*CallAzureFunctionForNextShape ()* 메서드에 대 한 코드를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="b4dc8-515">이전에 만든 *Azure 함수 앱* 를 사용 하 여 셰이프 인덱스를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="b4dc8-516">새 셰이프를 받은 후이 메서드는 *ShapeFactory* 클래스에 셰이프를 보내 장면에 새 셰이프를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="b4dc8-517">아래 코드를 사용 하 여 *CallAzureFunctionForNextShape ()* 의 본문을 완성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  <span data-ttu-id="b4dc8-518">셰이프 기록 목록에 저장 된 정수를 연결 하 고 *Azure Storage 파일*에 저장 하 여 문자열을 만드는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  <span data-ttu-id="b4dc8-519">*Azure Storage 파일* 에 있는 파일에 저장 된 텍스트를 검색 하 고 목록으로 *deserialize* 하는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="b4dc8-520">이 프로세스가 완료 되 면 메서드는 사용자가 장면에 셰이프를 더 추가할 수 있도록 응시를 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  <span data-ttu-id="b4dc8-521">Unity로 반환 하기 전에 Visual Studio에서 변경 내용을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="b4dc8-522">11 장-UWP 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="b4dc8-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="b4dc8-523">빌드 프로세스를 시작 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="b4dc8-524">**파일** > **빌드 설정**으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-524">Go to **File** > **Build Settings**.</span></span>

    ![앱 빌드](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="b4dc8-526">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-526">Click **Build**.</span></span> <span data-ttu-id="b4dc8-527">Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 *파일 탐색기* 창을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="b4dc8-528">이제 해당 폴더를 만들고 이름을 *App*으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="b4dc8-529">그런 다음 *앱* 폴더를 선택 하 고 **폴더 선택**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="b4dc8-530">Unity는 *응용* 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="b4dc8-531">Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 *파일 탐색기* 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)</span><span class="sxs-lookup"><span data-stu-id="b4dc8-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="b4dc8-532">12 장-응용 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="b4dc8-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="b4dc8-533">응용 프로그램을 배포 하려면:</span><span class="sxs-lookup"><span data-stu-id="b4dc8-533">To deploy your application:</span></span>

1.  <span data-ttu-id="b4dc8-534">[마지막 챕터](#chapter-11---build-the-uwp-solution)에서 만든 *앱* 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="b4dc8-535">*Visual Studio*내에서 열려면 두 번 클릭 해야 하는 ' .sln ' 확장명을 사용 하 여 앱 이름을 가진 파일이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="b4dc8-536">**솔루션 플랫폼**에서 **X86, 로컬 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="b4dc8-537">**솔루션 구성** 에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="b4dc8-538">Microsoft HoloLens의 경우 컴퓨터에 테더 링 된 하지 않도록 *원격 컴퓨터*를 설정 하는 것이 더 쉬울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="b4dc8-539">그러나 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="b4dc8-540">**설정** **네트워크 & Internet**  wi-fi > **고급 옵션**에서 찾을 수 있는 HoloLens의 IP 주소를 알고 있어야 합니다. IPv4는 사용 해야 하는 주소입니다. >  > </span><span class="sxs-lookup"><span data-stu-id="b4dc8-540">Know the **IP Address** of your HoloLens, which can be found within the **Settings** > **Network & Internet** > **Wi-Fi** > **Advanced Options**; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="b4dc8-541">**개발자 모드가** **설정**되어 있는지 확인 합니다. **개발자를 위한** **설정** > **업데이트 & 보안** > 에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-541">Ensure **Developer Mode** is **On**; found in **Settings** > **Update & Security** > **For developers**.</span></span>

    ![솔루션 배포](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="b4dc8-543">**빌드** 메뉴로 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 컴퓨터에 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="b4dc8-544">이제 앱이 설치 된 앱 목록에 표시 되 고, 시작 하 고 테스트할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="b4dc8-545">완성 된 Azure Functions 및 저장소 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="b4dc8-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="b4dc8-546">축 하 합니다. Azure Functions 및 Azure Storage 서비스를 모두 활용 하는 혼합 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="b4dc8-547">앱은 저장 된 데이터에 대 한 그리기를 수행 하 고 해당 데이터를 기반으로 작업을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![최종 제품 종료](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b4dc8-549">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="b4dc8-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="b4dc8-550">연습 1</span><span class="sxs-lookup"><span data-stu-id="b4dc8-550">Exercise 1</span></span>

<span data-ttu-id="b4dc8-551">개체를 만든 위치를 생성 하는 두 번째 생성 지점과 레코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="b4dc8-552">데이터 파일을 로드할 때 원래 생성 된 위치에서 생성 되는 셰이프를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="b4dc8-553">연습 2</span><span class="sxs-lookup"><span data-stu-id="b4dc8-553">Exercise 2</span></span>

<span data-ttu-id="b4dc8-554">매번 다시 열지 않고 앱을 다시 시작 하는 방법을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="b4dc8-555">**장면을 로드** 하는 것이 좋은 시작 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="b4dc8-556">이 작업을 수행한 후에는 앱에서 쉽게 다시 설정할 수 있도록 *Azure Storage*저장 된 목록을 지우는 방법을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4dc8-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
