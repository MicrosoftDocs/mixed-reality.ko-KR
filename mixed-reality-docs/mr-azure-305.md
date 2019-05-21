---
title: MR 및 Azure 305-함수 및 저장소
description: 혼합된 현실 응용 프로그램에서 Azure Storage 및 함수를 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, 함수, 저장소, hololens, vr, 몰입 형
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598300"
---
>[!NOTE]
><span data-ttu-id="f7ba8-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f7ba8-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f7ba8-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f7ba8-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f7ba8-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f7ba8-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="f7ba8-110">MR 및 Azure 305: 함수 및 저장소</span><span class="sxs-lookup"><span data-stu-id="f7ba8-110">MR and Azure 305: Functions and storage</span></span>

![최종 제품-시작](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="f7ba8-112">이 과정에서는 Azure Functions를 사용 하 여 만들고, 혼합된 현실 응용 프로그램에서 Azure Storage 리소스를 사용 하 여 데이터를 저장 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="f7ba8-113">*Azure Functions* 작은 코드를 실행 하기 위해 개발자를 허용 하는 Microsoft 서비스에 '', Azure에서 functions 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="f7ba8-114">다양 한 이점을 가질 수 있는 로컬 응용 프로그램 보다는 클라우드의 작업을 위임 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="f7ba8-115">*Azure Functions* C를 비롯 한 여러 개발 언어를 지 원하는\#, F\#, Node.js, Java 및 PHP 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="f7ba8-116">자세한 내용은 참조는 [문서에서는 Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="f7ba8-117">*Azure Storage* 는 개발자가 항상 사용 가능한, 보안, 지속형, 확장성 및 중복 되어 있으므로 보험을 사용 하 여 데이터를 저장 하는 Microsoft 클라우드 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="f7ba8-118">즉, Microsoft를 모든 유지 관리 및 중요 한 문제를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="f7ba8-119">자세한 내용은 참조는 [Azure Storage 문서](https://docs.microsoft.com/azure/storage/common/storage-introduction)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="f7ba8-120">이 과정을 마치면 다음을 수행 하는 일을 할 수 있는 혼합된 현실 몰입 형 헤드셋 응용 프로그램을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="f7ba8-121">장면 주위 gaze 사용자를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="f7ba8-122">사용자 '단추' 3D에서 gazes 때 개체의 생성을 트리거하십시오.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="f7ba8-123">생성 된 개체는 Azure 함수에 의해 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="f7ba8-124">각 개체는 생성 된 대로 응용 프로그램의 개체 형식을 저장 한 *Azure File*에 있는 *Azure Storage*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="f7ba8-125">두 번째로 로드 시 합니다 *Azure 파일* 데이터를 검색 및 재생 응용 프로그램의 이전 인스턴스에서 작업을 생성 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="f7ba8-126">응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="f7ba8-127">이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="f7ba8-128">혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="f7ba8-129">장치 지원</span><span class="sxs-lookup"><span data-stu-id="f7ba8-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f7ba8-130">과정</span><span class="sxs-lookup"><span data-stu-id="f7ba8-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f7ba8-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f7ba8-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f7ba8-132"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="f7ba8-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="f7ba8-133">MR 및 Azure 305: 함수 및 저장소</span><span class="sxs-lookup"><span data-stu-id="f7ba8-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="f7ba8-134">✔️</span><span class="sxs-lookup"><span data-stu-id="f7ba8-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f7ba8-135">✔️</span><span class="sxs-lookup"><span data-stu-id="f7ba8-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="f7ba8-136">이 코스는 주로 Windows Mixed Reality 몰입 형 (VR) 헤드셋 주력, Microsoft HoloLens이 과정에서 배운 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="f7ba8-137">과정을 따라가려면 정보 HoloLens를 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7ba8-138">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="f7ba8-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="f7ba8-139">이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="f7ba8-140">또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 5 월) 작성 시점에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="f7ba8-141">내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 아래에 나열 된 보다 최신 소프트웨어에서 찾을 수 있는 항목을 일치 완벽 하 게 됩니다 있지만 문서 .</span><span class="sxs-lookup"><span data-stu-id="f7ba8-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="f7ba8-142">다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="f7ba8-143">개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용</span><span class="sxs-lookup"><span data-stu-id="f7ba8-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="f7ba8-144">Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="f7ba8-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f7ba8-145">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="f7ba8-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f7ba8-146">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="f7ba8-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f7ba8-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f7ba8-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="f7ba8-148">A [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md) 하거나 [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여</span><span class="sxs-lookup"><span data-stu-id="f7ba8-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="f7ba8-149">Azure 리소스 만들기에 대 한 Azure 계정에 대 한 구독</span><span class="sxs-lookup"><span data-stu-id="f7ba8-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="f7ba8-150">Azure 설정 및 데이터 검색에 대 한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="f7ba8-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="f7ba8-151">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="f7ba8-151">Before you start</span></span>

<span data-ttu-id="f7ba8-152">이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).</span><span class="sxs-lookup"><span data-stu-id="f7ba8-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="f7ba8-153">1 장-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="f7ba8-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="f7ba8-154">사용 하는 **Azure Storage 서비스**를 만들고 구성 해야 합니다는 **저장소 계정** Azure portal에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="f7ba8-155">에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="f7ba8-156">Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="f7ba8-157">클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="f7ba8-158">일단 로그인 하면 클릭할 **새로 만들기** 왼쪽 위에서 모서리 및 검색 *저장소 계정*를 클릭 하 고 **Enter**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![azure storage 검색](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="f7ba8-160">단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="f7ba8-161">새 페이지에 대 한 설명을 제공 합니다는 *Azure Storage 계정* 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="f7ba8-162">선택이 프롬프트의 왼쪽 아래에 있는 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![서비스 만들기](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="f7ba8-164">클릭 한 후 **만들기**:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="f7ba8-165">삽입을 *이름을* 계정의 주의 숫자 및 소문자만이 필드를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="f7ba8-166">에 대 한 *배포 모델*를 선택 **Resource manager**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="f7ba8-167">에 대 한 *계정 종류*를 선택 **저장소 (범용 v1)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="f7ba8-168">확인 합니다 *위치* (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="f7ba8-169">위치는 응용 프로그램은 실행할 지역의 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="f7ba8-170">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="f7ba8-171">에 대 한 *복제* 선택 **읽기-액세스-지역 중복 저장소 (RA-GRS)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="f7ba8-172">에 대 한 *성능*를 선택 **표준**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="f7ba8-173">둡니다 *보안 전송 필요* 으로 **비활성**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="f7ba8-174">선택 된 *구독*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="f7ba8-175">선택 된 *리소스 그룹* 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="f7ba8-176">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f7ba8-177">것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).</span><span class="sxs-lookup"><span data-stu-id="f7ba8-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="f7ba8-178">추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="f7ba8-179">이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="f7ba8-180">**만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-180">Select **Create**.</span></span>

        ![입력된 서비스 정보](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="f7ba8-182">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="f7ba8-183">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![azure portal에서 새 알림](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="f7ba8-185">새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-185">Click on the notifications to explore your new Service instance.</span></span>

    ![리소스로 이동](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="f7ba8-187">클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="f7ba8-188">이동에서 새 *저장소 계정* 서비스 인스턴스.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![액세스 키](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="f7ba8-190">클릭 *선택키가*,이 클라우드 서비스에 대 한 끝점을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="f7ba8-191">사용 하 여 *메모장* 또는 유사한 나중에 사용할 키 중 하나를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="f7ba8-192">또한 합니다 *연결 문자열* 값을에서 사용 됩니다 합니다 *Azureservice* 나중에 만들 클래스.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![연결 문자열 복사](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="f7ba8-194">2 장-Azure 함수 설정</span><span class="sxs-lookup"><span data-stu-id="f7ba8-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="f7ba8-195">이제 작성을 **Azure** **함수** Azure 서비스에서.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="f7ba8-196">사용할 수 있는 **Azure Function** 수행 하는 클래식 함수를 사용 하 여 차이 코드에서이 함수는 Azure 계정에 액세스 하려면 자격 증명이 있는 모든 응용 프로그램에서 액세스할 수 있습니다는 거의 모든 작업을 수행 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="f7ba8-197">Azure Function을 만들려면:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="f7ba8-198">사용자 *Azure Portal*, 클릭 **새로 만들기** 왼쪽 위에서 모서리 및 검색할 *함수 앱*, 클릭 **Enter**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![함수 앱 만들기](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="f7ba8-200">단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="f7ba8-201">새 페이지에 대 한 설명을 제공 합니다는 *Azure 함수 앱* 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="f7ba8-202">선택이 프롬프트의 왼쪽 아래에 있는 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![함수 앱 정보](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="f7ba8-204">클릭 한 후 **만들기**:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="f7ba8-205">제공 된 *앱 이름*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-205">Provide an *App name*.</span></span> <span data-ttu-id="f7ba8-206">문자 및 숫자만 사용할 수 여기 (위쪽 또는 아래쪽 사례 허용 됨).</span><span class="sxs-lookup"><span data-stu-id="f7ba8-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="f7ba8-207">선호 하 *구독*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="f7ba8-208">선택 된 *리소스 그룹* 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="f7ba8-209">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f7ba8-210">것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).</span><span class="sxs-lookup"><span data-stu-id="f7ba8-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="f7ba8-211">추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="f7ba8-212">이 연습에서는 선택 *Windows* 으로 선택한 **OS**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="f7ba8-213">선택 *소비 계획* 에 대 한 합니다 **호스팅 계획**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="f7ba8-214">확인 합니다 *위치* (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="f7ba8-215">위치는 응용 프로그램은 실행할 지역의 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="f7ba8-216">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="f7ba8-217">최적의 성능을 위해 저장소 계정과 동일한 영역을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="f7ba8-218">에 대 한 *저장소*를 선택 **사용 하 여 기존**를 찾아 다음 드롭다운 메뉴를 사용 하 여 이전에 만든된 저장소입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="f7ba8-219">둡니다 *Application Insights* 이 연습에 대 한 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-219">Leave *Application Insights* off for this exercise.</span></span>

        ![입력된 함수 앱 세부 정보](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="f7ba8-221">**만들기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="f7ba8-222">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="f7ba8-223">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![새 azure portal 알림](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="f7ba8-225">새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![리소스 함수 앱으로 이동](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="f7ba8-227">클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="f7ba8-228">이동에서 새 *함수 앱* 서비스 인스턴스.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="f7ba8-229">에 *함수 앱* 대시보드를 위로 마우스를 가져가서 *함수*를 왼쪽에서 패널 내에서 발견 하 고 클릭 합니다 **+ (더하기)** 기호.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![새 함수 만들기](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="f7ba8-231">다음 페이지에서 확인 **Webhook + API** 을 선택 하면 한 *언어를 선택* 선택 **CSharp**처럼이 자습서에 사용 된 언어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="f7ba8-232">마지막으로,를 클릭 합니다 **이 함수 만들기** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-232">Lastly, click the **Create this function** button.</span></span>

    ![웹 후크 csharp 선택](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="f7ba8-234">코드 이동 되어야 합니다 (run.csx) 페이지 그렇지 않은 경우 왼쪽 패널에 있는 함수 목록에서 새로 만든된 함수를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![새 함수 열기](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="f7ba8-236">함수에 다음 코드를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-236">Copy the following code into your function.</span></span> <span data-ttu-id="f7ba8-237">이 함수는 0과 호출 될 때 2 사이의 임의의 정수를 반환 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="f7ba8-238">맨 위에 붙여넣을 자유롭게, 기존 코드에 대 한 걱정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

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

13. <span data-ttu-id="f7ba8-239">**저장**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-239">Select **Save**.</span></span>

14. <span data-ttu-id="f7ba8-240">결과 아래 이미지와 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="f7ba8-241">클릭할 **함수 URL 가져오기** 숙지 합니다 *끝점* 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="f7ba8-242">에 삽입 해야 합니다 *Azureservice* 이 과정의 뒷부분에서 만들 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![함수 끝점 가져오기](images/AzureLabs-Lab5-16.png)

    ![함수 끝점 가져오기](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="f7ba8-245">3 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="f7ba8-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="f7ba8-246">다음은 일반적인 등록 혼합 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="f7ba8-247">설정 하 고 혼합된 현실 몰입 형 헤드셋을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ba8-248">해야 **되지** 이 과정에 대 한 동작 컨트롤러 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="f7ba8-249">몰입 형 헤드셋 설정만 지원에 필요한 경우 하세요 [문서를 설정 하는 혼합된 현실 방문](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="f7ba8-250">Unity를 열고 클릭 **새로 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-250">Open Unity and click **New**.</span></span>

    ![새 unity 프로젝트 만들기](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="f7ba8-252">이제 Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="f7ba8-253">삽입 **MR_Azure_Functions**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="f7ba8-254">프로젝트 형식 설정 되어 있는지 확인 **3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="f7ba8-255">설정 된 *위치* 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다).</span><span class="sxs-lookup"><span data-stu-id="f7ba8-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="f7ba8-256">그런 다음 클릭 **프로젝트 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-256">Then, click **Create project**.</span></span>

    ![새 unity 프로젝트에 이름을 부여합니다](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="f7ba8-258">Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="f7ba8-259">로 이동 **편집할* > *기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-259">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="f7ba8-260">변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="f7ba8-261">닫기 합니다 **기본 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-261">Close the **Preferences** window.</span></span>

    ![스크립트 편집기로 visual studio 설정](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="f7ba8-263">이동한 다음 **파일 > 빌드 설정** 플랫폼 전환 **유니버설 Windows 플랫폼**를 클릭 하 여는 **플랫폼 전환** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-263">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![uwp 플랫폼 전환](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="f7ba8-265">로 이동 **파일 > 빌드 설정** 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-265">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="f7ba8-266">**장치를 대상** 로 설정 된 **모든 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="f7ba8-267">Microsoft HoloLens 설정 **대상 장치** 하 *HoloLens*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="f7ba8-268">**빌드 형식** 로 설정 된 **D3D**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="f7ba8-269">**SDK** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="f7ba8-270">**Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="f7ba8-271">**빌드 및 실행** 로 설정 된 **로컬 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="f7ba8-272">장면 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="f7ba8-273">선택 하 여이 작업을 수행할 **열고 장면 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="f7ba8-274">창 저장 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-274">A save window will appear.</span></span>

            ![열기 장면 추가](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="f7ba8-276">새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![백그라운드에서 폴더 만들기](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="f7ba8-278">새로 만든 열 **장면** 폴더를 선택한 다음는 **파일 이름:** 텍스트 필드에 입력 **FunctionsScene**, 키를 누릅니다 **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![함수 장면 저장](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="f7ba8-280">설정에 남아 **빌드 설정**, 지금은 기본값으로 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![함수 장면 저장](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="f7ba8-282">에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![플레이어 설정 관리자에서](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="f7ba8-284">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="f7ba8-285">에 **기타 설정** 탭:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="f7ba8-286">**스크립팅 런타임 버전** 있어야 **실험적** (.NET 4.6 동등), 편집기를 다시 시작 해야를 트리거하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="f7ba8-287">**백 엔드를 스크립팅** 있어야 **.NET**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="f7ba8-288">**API 호환성 수준** 있어야 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="f7ba8-289">내 합니다 **게시 설정** 탭의 **기능**, 확인:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="f7ba8-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-290">**InternetClient**</span></span>

            ![집합 기능](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="f7ba8-292">패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK** 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![xr 하이 설정](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="f7ba8-294">년대 *빌드 설정* *Unity C# 프로젝트* 가 더 이상 회색;이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![눈금 c# 프로젝트](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="f7ba8-296">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="f7ba8-297">장면 및 프로젝트 저장 (**파일 > 저장 장면 파일 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="f7ba8-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="f7ba8-298">4 장-주 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="f7ba8-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f7ba8-299">건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드에 바로 계속, 자유롭게 [이.unitypackage 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage),으로 프로젝트로 가져오는 것을 [사용자 지정 패키지](https://docs.unity3d.com/Manual/AssetPackages.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="f7ba8-300">다음 장에서에서 Dll도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="f7ba8-301">가져온 후 계속 진행 [7 장](#chapter-7---create-the-azureservices-class)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="f7ba8-302">에 *계층 패널*, 라는 개체를 보면 **주 카메라**, "내부" 응용 프로그램 되 면이 개체에 "head" 관점을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="f7ba8-303">사용자 앞에 Unity 대시보드를 선택 합니다 **주 카메라 GameObject**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="f7ba8-304">합니다 *검사기 패널* (일반적으로 대시보드 내에서 오른쪽에 있음)의 다양 한 구성 요소에 표시 됩니다 *GameObject*를 사용 하 여 *변환* 맨 뒤에 *카메라*, 및 기타 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="f7ba8-305">위치가 올바르게 하므로 주 카메라의 변환을 다시 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="f7ba8-306">이렇게 하려면 선택 합니다 **기어** 카메라의 옆에 있는 아이콘 *변환* 구성 요소를 선택한 **재설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![변환 다시 설정](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="f7ba8-308">그런 다음 업데이트를 **변환** 모양 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="f7ba8-309">변환-위치</span><span class="sxs-lookup"><span data-stu-id="f7ba8-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="f7ba8-310">**X**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-310">**X**</span></span>   | <span data-ttu-id="f7ba8-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-311">**Y**</span></span>                     | <span data-ttu-id="f7ba8-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-312">**Z**</span></span> |
    | <span data-ttu-id="f7ba8-313">0</span><span class="sxs-lookup"><span data-stu-id="f7ba8-313">0</span></span>       | <span data-ttu-id="f7ba8-314">1</span><span class="sxs-lookup"><span data-stu-id="f7ba8-314">1</span></span>                         | <span data-ttu-id="f7ba8-315">0</span><span class="sxs-lookup"><span data-stu-id="f7ba8-315">0</span></span>     |    

    |       | <span data-ttu-id="f7ba8-316">변환-회전</span><span class="sxs-lookup"><span data-stu-id="f7ba8-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="f7ba8-317">**X**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-317">**X**</span></span> | <span data-ttu-id="f7ba8-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-318">**Y**</span></span>                | <span data-ttu-id="f7ba8-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-319">**Z**</span></span> |
    | <span data-ttu-id="f7ba8-320">0</span><span class="sxs-lookup"><span data-stu-id="f7ba8-320">0</span></span>     | <span data-ttu-id="f7ba8-321">0</span><span class="sxs-lookup"><span data-stu-id="f7ba8-321">0</span></span>                    | <span data-ttu-id="f7ba8-322">0</span><span class="sxs-lookup"><span data-stu-id="f7ba8-322">0</span></span>     |

    |       | <span data-ttu-id="f7ba8-323">변환-확장</span><span class="sxs-lookup"><span data-stu-id="f7ba8-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="f7ba8-324">**X**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-324">**X**</span></span> | <span data-ttu-id="f7ba8-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-325">**Y**</span></span>             | <span data-ttu-id="f7ba8-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-326">**Z**</span></span> |
    | <span data-ttu-id="f7ba8-327">1</span><span class="sxs-lookup"><span data-stu-id="f7ba8-327">1</span></span>     | <span data-ttu-id="f7ba8-328">1</span><span class="sxs-lookup"><span data-stu-id="f7ba8-328">1</span></span>                 | <span data-ttu-id="f7ba8-329">1</span><span class="sxs-lookup"><span data-stu-id="f7ba8-329">1</span></span>     |

    ![카메라 변환 집합](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="f7ba8-331">5 장-Unity 장면 설정</span><span class="sxs-lookup"><span data-stu-id="f7ba8-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="f7ba8-332">빈 영역을 마우스 오른쪽 단추로 클릭 합니다 *계층 패널*아래에 있는 **3D 개체**, 추가 **평면**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![새 평면 만들기](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="f7ba8-334">사용 하 여 합니다 **평면** 선택한 개체에서 다음 매개 변수를 변경 합니다 *검사기 패널*:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="f7ba8-335">변환-위치</span><span class="sxs-lookup"><span data-stu-id="f7ba8-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="f7ba8-336">**X**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-336">**X**</span></span> | <span data-ttu-id="f7ba8-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-337">**Y**</span></span>                | <span data-ttu-id="f7ba8-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-338">**Z**</span></span> |
    | <span data-ttu-id="f7ba8-339">0</span><span class="sxs-lookup"><span data-stu-id="f7ba8-339">0</span></span>     | <span data-ttu-id="f7ba8-340">0</span><span class="sxs-lookup"><span data-stu-id="f7ba8-340">0</span></span>                    | <span data-ttu-id="f7ba8-341">4</span><span class="sxs-lookup"><span data-stu-id="f7ba8-341">4</span></span>     |

    |       | <span data-ttu-id="f7ba8-342">변환-확장</span><span class="sxs-lookup"><span data-stu-id="f7ba8-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="f7ba8-343">**X**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-343">**X**</span></span> | <span data-ttu-id="f7ba8-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-344">**Y**</span></span>             | <span data-ttu-id="f7ba8-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-345">**Z**</span></span> |
    | <span data-ttu-id="f7ba8-346">10</span><span class="sxs-lookup"><span data-stu-id="f7ba8-346">10</span></span>    | <span data-ttu-id="f7ba8-347">1</span><span class="sxs-lookup"><span data-stu-id="f7ba8-347">1</span></span>                 | <span data-ttu-id="f7ba8-348">10</span><span class="sxs-lookup"><span data-stu-id="f7ba8-348">10</span></span>    |

    ![집합 평면 위치 및 크기 조정](images/AzureLabs-Lab5-32.png)

    ![면과 카메라 장면 보기로](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="f7ba8-351">빈 영역을 마우스 오른쪽 단추로 클릭 합니다 *계층 패널*아래에 있는 **3D 개체**, 추가 **큐브**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="f7ba8-352">큐브 이름 바꾸기 **GazeButton** (선택한 큐브를 사용 하 여 F2 키를 누릅니다 '').</span><span class="sxs-lookup"><span data-stu-id="f7ba8-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="f7ba8-353">다음 매개 변수를 변경 합니다 *검사기 패널*:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="f7ba8-354">변환-위치</span><span class="sxs-lookup"><span data-stu-id="f7ba8-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="f7ba8-355">**X**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-355">**X**</span></span> | <span data-ttu-id="f7ba8-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-356">**Y**</span></span>                | <span data-ttu-id="f7ba8-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-357">**Z**</span></span> |
        | <span data-ttu-id="f7ba8-358">0</span><span class="sxs-lookup"><span data-stu-id="f7ba8-358">0</span></span>     | <span data-ttu-id="f7ba8-359">3</span><span class="sxs-lookup"><span data-stu-id="f7ba8-359">3</span></span>                    | <span data-ttu-id="f7ba8-360">5</span><span class="sxs-lookup"><span data-stu-id="f7ba8-360">5</span></span>     |


        ![집합 게이즈 단추 변환](images/AzureLabs-Lab5-34.png)

        ![장면 보기로 단추가 gaze](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="f7ba8-363">클릭 합니다 **태그** 드롭다운 단추를 클릭 **태그 추가** 열려는 합니다 *태그 및 계층 창*.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![새 태그 추가](images/AzureLabs-Lab5-36.png)

        ![더하기 선택](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="f7ba8-366">선택 합니다 **+ (더하기)** 단추를 및 합니다 *새 태그 이름* 필드를 입력 합니다 **GazeButton**, 키를 누릅니다 **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![새 태그 이름](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="f7ba8-368">클릭 합니다 **GazeButton** 개체를 *계층 패널*, 및를 *검사기 패널*, 새로 만든 할당 **GazeButton** 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![응시 단추 새 태그 할당](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="f7ba8-370">마우스 오른쪽 단추로 클릭 합니다 **GazeButton** 개체에서 *계층 패널*, 추가 **빈 GameObject** (으로 추가 됩니다.는 *자식* 개체)입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="f7ba8-371">새 개체를 선택 하 고 이름을 **ShapeSpawnPoint**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="f7ba8-372">다음 매개 변수를 변경 합니다 *검사기 패널*:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="f7ba8-373">변환-위치</span><span class="sxs-lookup"><span data-stu-id="f7ba8-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="f7ba8-374">**X**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-374">**X**</span></span> |<span data-ttu-id="f7ba8-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-375">**Y**</span></span>                 | <span data-ttu-id="f7ba8-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-376">**Z**</span></span> |
        | <span data-ttu-id="f7ba8-377">0</span><span class="sxs-lookup"><span data-stu-id="f7ba8-377">0</span></span>     | <span data-ttu-id="f7ba8-378">-1</span><span class="sxs-lookup"><span data-stu-id="f7ba8-378">-1</span></span>                   | <span data-ttu-id="f7ba8-379">0</span><span class="sxs-lookup"><span data-stu-id="f7ba8-379">0</span></span>     |

        ![생성 포인트 변환 셰이프를 업데이트 합니다.](images/AzureLabs-Lab5-40.png)

        ![셰이프 생성 장면 관점](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="f7ba8-382">다음을 만듭니다는 **3D 텍스트** Azure 서비스의 상태에 피드백을 제공 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="f7ba8-383">마우스 오른쪽 단추로 클릭 합니다 **GazeButton** 계층 구조에서 패널 다시 추가한를 **3D 개체 > 3D 텍스트** 개체를 *자식*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object > 3D Text** object as a *child*.</span></span>

    ![새 3D 텍스트 개체 만들기](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="f7ba8-385">이름 바꾸기는 **3D 텍스트** 개체를 **AzureStatusText**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="f7ba8-386">변경 된 **AzureStatusText** 다음과 같이 변환 개체:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="f7ba8-387">변환-위치</span><span class="sxs-lookup"><span data-stu-id="f7ba8-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="f7ba8-388">**X**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-388">**X**</span></span> | <span data-ttu-id="f7ba8-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-389">**Y**</span></span>                | <span data-ttu-id="f7ba8-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-390">**Z**</span></span> |
    | <span data-ttu-id="f7ba8-391">0</span><span class="sxs-lookup"><span data-stu-id="f7ba8-391">0</span></span>     | <span data-ttu-id="f7ba8-392">0</span><span class="sxs-lookup"><span data-stu-id="f7ba8-392">0</span></span>                    | <span data-ttu-id="f7ba8-393">-0.6</span><span class="sxs-lookup"><span data-stu-id="f7ba8-393">-0.6</span></span>  |

    |       | <span data-ttu-id="f7ba8-394">변환-확장</span><span class="sxs-lookup"><span data-stu-id="f7ba8-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="f7ba8-395">**X**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-395">**X**</span></span> | <span data-ttu-id="f7ba8-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-396">**Y**</span></span>             | <span data-ttu-id="f7ba8-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="f7ba8-397">**Z**</span></span> |
    | <span data-ttu-id="f7ba8-398">0.1</span><span class="sxs-lookup"><span data-stu-id="f7ba8-398">0.1</span></span>   | <span data-ttu-id="f7ba8-399">0.1</span><span class="sxs-lookup"><span data-stu-id="f7ba8-399">0.1</span></span>               | <span data-ttu-id="f7ba8-400">0.1</span><span class="sxs-lookup"><span data-stu-id="f7ba8-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="f7ba8-401">이 수정 될 때 처럼 centre 해제 되도록 표시 되는 경우 걱정 하지 마십시오는 텍스트 메시 아래 구성 요소를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="f7ba8-402">변경 된 **텍스트 메시** 에 맞게 구성 요소는 아래:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-402">Change the **Text Mesh** component to match the below:</span></span>

    ![집합 텍스트 메시 구성 요소](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="f7ba8-404">여기서 선택한 색은 16 진수 색: **000000FF**하지만 자유롭게 선택할 사용자 고유의만 읽을 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="f7ba8-405">이제 계층 패널 구조에 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![장면 뷰에서 텍스트 메시](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="f7ba8-407">이제 장면 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-407">Your scene should now look like this:</span></span>

    ![장면 뷰에서 텍스트 메시](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="f7ba8-409">6 장-Unity에 대 한 Azure 저장소 가져오기</span><span class="sxs-lookup"><span data-stu-id="f7ba8-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="f7ba8-410">Azure Storage for Unity 사용 (자체는.Net 용 Azure SDK를 활용 함).</span><span class="sxs-lookup"><span data-stu-id="f7ba8-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="f7ba8-411">알아볼 수 있습니다이에 대 한 합니다 [Unity 문서에 대 한 Azure Storage](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="f7ba8-412">플러그 인 가져오기 후 다시 구성 해야 하는 Unity의 알려진된 문제는 현재 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="f7ba8-413">이러한 단계 (4-7이 단원의) 버그가 해결 된 후 필요한 더 이상.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="f7ba8-414">사용자 고유의 프로젝트에 SDK를 가져오려면 최신 다운로드 했는지 확인 [GitHub에서 '.unitypackage'](https://aka.ms/azstorage-unitysdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="f7ba8-415">그런 다음 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-415">Then, do the following:</span></span>

1.  <span data-ttu-id="f7ba8-416">추가 된 **.unitypackage** Unity 사용 하 여 파일을 **자산 > 패키지 가져오기 > 사용자 지정 패키지** 메뉴 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-416">Add the **.unitypackage** file to Unity by using the **Assets > Import Package > Custom Package** menu option.</span></span>

2.  <span data-ttu-id="f7ba8-417">에 **Unity 패키지 가져오기** 팝업에서 선택할 수 있는 아래에 있는 모든 상자 \**플러그 인* > \*저장소\*\*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-417">In the **Import Unity Package** box that pops up, you can select everything under \**Plugin* > \*Storage\*\*.</span></span> <span data-ttu-id="f7ba8-418">이 과정에 대 한 필요 하지 않을 때 나머지 작업은 모두 선택 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![패키지 가져오기](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="f7ba8-420">클릭 합니다 **가져오기** 프로젝트에 항목을 추가 하려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="f7ba8-421">로 이동 합니다 *저장소* 아래에 폴더 *플러그 인*프로젝트 보기 및 다음 플러그 인 선택 *만*:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="f7ba8-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="f7ba8-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="f7ba8-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="f7ba8-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="f7ba8-424">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="f7ba8-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="f7ba8-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="f7ba8-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="f7ba8-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="f7ba8-426">System.Spatial</span></span>

        ![모든 플랫폼을 선택 취소](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="f7ba8-428">사용 하 여 *이러한 특정 플러그 인* 선택 하면 **의 선택을 취소** *Any 플랫폼* 고 **의 선택을 취소** *WSAPlayer* 누른 **적용**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![플랫폼 dll를 적용 합니다.](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="f7ba8-430">이러한 특정 플러그 인 Unity 편집기에서 사용할 수만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="f7ba8-431">Unity에서 프로젝트를 내보낸 후 사용할 WSA 폴더에 같은 플러그 인의 다양 한 버전 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="f7ba8-432">에 *저장소* 플러그 인 폴더에만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="f7ba8-433">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="f7ba8-433">Microsoft.Data.Services.Client</span></span>

        ![집합에 dll에 대 한 처리](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="f7ba8-435">확인 합니다 **없는 프로세스** 상자에 *플랫폼 설정* 클릭 **적용**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![없는 처리 적용](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="f7ba8-437">표시 됩니다이 플러그 인 "처리 하지 않음" Unity 어셈블리 패 처가이 플러그 인을 처리 하는 데 문제가 있어.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="f7ba8-438">플러그 인 처리 되지 않았습니다. 경우에 계속 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="f7ba8-439">7-장 Azureservice 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="f7ba8-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="f7ba8-440">첫 번째 클래스를 만드는 것은 *Azureservice* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="f7ba8-441">합니다 *Azureservice* 클래스에 대 한 지불 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="f7ba8-442">Azure 계정 자격 증명을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="f7ba8-443">Azure 앱 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="f7ba8-444">업로드 및 Azure 클라우드 저장소에서 데이터 파일의 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="f7ba8-445">이 클래스 만들려면:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-445">To create this Class:</span></span>

1.  <span data-ttu-id="f7ba8-446">마우스 오른쪽 단추로 클릭 합니다 *Asset* [프로젝트] 패널에 있는 **만들기 > 폴더**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create > Folder**.</span></span> <span data-ttu-id="f7ba8-447">폴더의 이름을 **스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-447">Name the folder **Scripts**.</span></span>

    ![새 폴더 만들기](images/AzureLabs-Lab5-50.png)

    ![스크립트 폴더를 호출 합니다.](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="f7ba8-450">열려는 방금 만든 폴더를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="f7ba8-451">폴더를 마우스 오른쪽 단추로 클릭 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-451">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="f7ba8-452">스크립트를 호출할 *Azureservice*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="f7ba8-453">두 번 클릭 하 여 새 *Azureservice* 클래스를 사용 하 여 *Visual Studio*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="f7ba8-454">맨 위에 다음 네임 스페이스를 추가 합니다 *Azureservice*:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="f7ba8-455">내부의 다음 검사기 필드를 추가 합니다 *Azureservice* 클래스:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

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

7.  <span data-ttu-id="f7ba8-456">그런 다음 내에서 다음 멤버 변수를 추가 합니다 *Azureservice* 클래스:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-456">Then add the following member variables inside the *AzureServices* class:</span></span>

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
    > <span data-ttu-id="f7ba8-457">바꿔야 합니다 *끝점* 하 고 *연결 문자열* 값과 값에 Azure storage에서 Azure Portal에서 찾을 수</span><span class="sxs-lookup"><span data-stu-id="f7ba8-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="f7ba8-458">에 대 한 코드 *Awake()* 하 고 *start ()* 메서드는 이제 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="f7ba8-459">이러한 메서드는 클래스를 초기화할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-459">These methods will be called when the class initializes:</span></span>

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
    > <span data-ttu-id="f7ba8-460">에 대 한 코드를 입력 했습니다 *CallAzureFunctionForNextShape()* 에 [향후 장](#chapter-10---completing-the-AzureServices-class)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-AzureServices-class).</span></span>

9.  <span data-ttu-id="f7ba8-461">삭제 합니다 *update ()* 메서드가이 클래스는 사용 하지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="f7ba8-462">Visual Studio에서 변경 내용을 저장 하 고 Unity로 돌아와서 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="f7ba8-463">클릭 하 고 끌어서 합니다 *Azureservice* Scripts 폴더에서 클래스를 주 카메라 개체에는 *계층 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="f7ba8-464">주 카메라를 선택 하 고 가져오는 합니다 **AzureStatusText** 아래에서 자식 개체를 **GazeButton** 개체를 내에 배치 합니다 **AzureStatusText** 참조 대상 필드를 *검사기*에 대 한 참조를 제공 하는 *Azureservice* 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![azure 상태 텍스트 참조 대상 할당](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="f7ba8-466">8-장 ShapeFactory 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="f7ba8-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="f7ba8-467">를 만들려면 다음 스크립트를 *ShapeFactory* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="f7ba8-468">이 클래스의 역할은 요청을 만들면 새 셰이프를에서 만든 모양의 기록을 유지 하는 *모양 기록 목록*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="f7ba8-469">셰이프를 만들 때마다를 *셰이프 기록 목록* 에서 업데이트 되는 *AzureService* 클래스를 저장 한 다음에 *Azure Storage*.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="f7ba8-470">응용 프로그램이 시작 되 면 저장 된 파일에서 발견 되 면 프로그램 *Azure Storage*의 *셰이프 기록 목록* 를 검색 하 고 재생을 사용 하 여는 **3D 텍스트** 개체를 제공 하 생성 된 모양 인지 여부 또는 새 저장소에서입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="f7ba8-471">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-471">To create this class:</span></span>

1.  <span data-ttu-id="f7ba8-472">로 이동 합니다 **스크립트** 이전에 만든 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="f7ba8-473">폴더를 마우스 오른쪽 단추로 클릭 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-473">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="f7ba8-474">스크립트를 호출할 *ShapeFactory*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="f7ba8-475">두 번 클릭 하 여 새 *ShapeFactory* 스크립트를 사용 하 여 열고 *Visual Studio*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="f7ba8-476">확인 합니다 *ShapeFactory* 클래스는 다음 네임 스페이스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="f7ba8-477">아래에 표시 된 변수를 추가 합니다 *ShapeFactory* 바꾸고 클래스는 *start ()* 및 *Awake()* 아래와 함수:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

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

6.  <span data-ttu-id="f7ba8-478">합니다 *CreateShape()* 메서드를 기반으로 제공 된 기본 도형 생성 *정수* 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="f7ba8-479">부울 매개 변수 저장소에서 현재 생성된 모양 인지 여부를 지정 하는 데 사용 되었거나 새.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="f7ba8-480">다음 코드를 배치 하 *ShapeFactory* 이전 메서드 아래 클래스:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

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

7.  <span data-ttu-id="f7ba8-481">Unity를 반환 하기 전에 Visual Studio에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="f7ba8-482">다시 Unity 편집기에서 클릭 하 고 끌어서 합니다 *ShapeFactory* 에서 클래스를 **스크립트** 폴더를 **주 카메라** 개체를 *계층 패널*.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="f7ba8-483">선택한 주 카메라를 사용 하 여 확인할 수 있습니다 합니다 *ShapeFactory* 스크립트 구성 요소가 누락 되었습니다 합니다 *Spawn 지점* 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="f7ba8-484">이 문제를 해결 하려면 끌어서를 **ShapeSpawnPoint** 에서 개체를 *계층 패널* 에 **Spawn 지점** 참조 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![집합 셰이프 팩터리 참조 대상](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="f7ba8-486">9-장 게이즈 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="f7ba8-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="f7ba8-487">만들어야 하는 마지막 스크립트를 *Gaze* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="f7ba8-488">이 클래스는 생성을 담당를 **Raycast** 는 프로젝션 앞으로 사용자를 보고 하는 개체를 검색 하는 주 카메라에서.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="f7ba8-489">사용자를 보고 하는 경우를 식별 하는 Raycast 해야이 경우는 **GazeButton** 장면에 개체 및 동작을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="f7ba8-490">이 클래스 만들려면:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-490">To create this Class:</span></span>

1.  <span data-ttu-id="f7ba8-491">로 이동 합니다 **스크립트** 이전에 만든 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="f7ba8-492">프로젝트 패널을 마우스 오른쪽 단추로 클릭 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-492">Right-click in the Project Panel, **Create > C# Script**.</span></span> <span data-ttu-id="f7ba8-493">스크립트를 호출할 *Gaze*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="f7ba8-494">두 번 클릭 하 여 새 *Gaze* 스크립트를 사용 하 여 열고 *Visual Studio입니다.*</span><span class="sxs-lookup"><span data-stu-id="f7ba8-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="f7ba8-495">다음 네임 스페이스 스크립트의 맨 위에 있는 포함 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="f7ba8-496">그런 다음 내에서 다음 변수를 추가 합니다 *Gaze* 클래스:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-496">Then add the following variables inside the *Gaze* class:</span></span>

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
> <span data-ttu-id="f7ba8-497">편집할 수 있으려면 이러한 변수 중 일부는 *편집기*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="f7ba8-498">에 대 한 코드를 *Awake()* 하 고 *start ()* 메서드는 이제 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="f7ba8-499">와 함께 시작, 커서 개체를 만드는 다음 코드를 추가 합니다 *update ()* 이 GazeEnabled 부울 설정/해제 되 고 함께 Raycast 메서드를 실행 하는 메서드:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

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

8. <span data-ttu-id="f7ba8-500">다음 추가 합니다 *UpdateRaycast()* 메서드는 Raycast 프로젝트는 적중 횟수 대상을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

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

9. <span data-ttu-id="f7ba8-501">마지막으로 추가 합니다 *ResetFocusedObject()* 메서드 GazeButton 개체에 현재 색을 나타내는 여부 새 셰이프를 만들기가 있는지 여부를 설정/해제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

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

10.  <span data-ttu-id="f7ba8-502">Visual Studio에서 Unity를 반환 하기 전에 변경 내용을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="f7ba8-503">클릭 하 고 끌어서 합니다 *Gaze* Scripts 폴더에서 클래스를 **주 카메라** 개체를 *계층 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="f7ba8-504">10 장-Azureservice 클래스를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="f7ba8-505">현재 위치에서 다른 스크립트를 사용 하 여 이제 수 있기 *완전* 는 *Azureservice* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="f7ba8-506">이 통해 수행할 수 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="f7ba8-507">라는 새 메서드 추가 *CreateCloudIdentityAsync()*, Azure와의 통신에 필요한 인증 변수를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="f7ba8-508">이 메서드는 또한 셰이프 목록을 포함 하는 이전에 저장 된 파일의 존재 여부 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="f7ba8-509">**파일이 있으면**, 사용자 사용 하지 않도록 설정 됩니다 *Gaze*에 저장 된 모양의 패턴에 따라 셰이프 작성, 트리거 및 합니다 **Azure Storage 파일**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="f7ba8-510">사용자와이 볼 수는 **텍스트 메시** 표시 하면 'Storage' 또는 'New' 셰이프 원점에 따라 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="f7ba8-511">**파일이 없는 경우**를 활성화 합니다 *Gaze*를 보면 모양을 만들 수 있도록를 **GazeButton** 장면에서 개체.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

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

2.  <span data-ttu-id="f7ba8-512">내에서 다음 코드 조각은는 *start ()* 에 전화를 걸 여기서; 메서드는 *CreateCloudIdentityAsync()* 메서드.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="f7ba8-513">현재 복사 자유롭게 *start ()* 메서드를 사용 하 여는 아래:</span><span class="sxs-lookup"><span data-stu-id="f7ba8-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

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

3.  <span data-ttu-id="f7ba8-514">메서드에 대 한 코드를 입력 *CallAzureFunctionForNextShape()* 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="f7ba8-515">이전에 만든 사용할지 *Azure 함수 앱* shape 인덱스를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="f7ba8-516">새 셰이프 수신 되 면이 메서드는 셰이프를 보냅니다는 *ShapeFactory* 장면에 새 셰이프를 만드는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="f7ba8-517">아래 코드의 본문을 완료 하는 데 *CallAzureFunctionForNextShape()* 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

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

4.  <span data-ttu-id="f7ba8-518">에 저장 셰이프 기록 목록에 저장 된 정수를 연결 하 여 문자열을 만드는 메서드를 추가 하면 *Azure Storage 파일*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

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

5.  <span data-ttu-id="f7ba8-519">에 있는 파일에 저장 된 텍스트를 검색 하는 메서드를 추가 하 *Azure Storage File* 및 *deserialize* 목록에 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="f7ba8-520">이 프로세스가 완료 되 면 메서드 다시 사용 하도록 설정 합니다 게이즈 장면에 사용자 추가 셰이프를 추가할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

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

7.  <span data-ttu-id="f7ba8-521">Visual Studio에서 Unity를 반환 하기 전에 변경 내용을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="f7ba8-522">11 장-UWP 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="f7ba8-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="f7ba8-523">빌드 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="f7ba8-524">로 이동 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-524">Go to **File > Build Settings**.</span></span>

    ![앱 빌드](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="f7ba8-526">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-526">Click **Build**.</span></span> <span data-ttu-id="f7ba8-527">Unity가 시작 됩니다는 *파일 탐색기* 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="f7ba8-528">해당 폴더를 이제 만들고 이름을 *앱*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="f7ba8-529">사용 하 여 다음 합니다 *앱* 폴더 선택 키를 눌러 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="f7ba8-530">Unity 프로젝트를 빌드할 예정 된 *앱* 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="f7ba8-531">한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 *파일 탐색기* 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="f7ba8-532">12 장-응용 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="f7ba8-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="f7ba8-533">응용 프로그램을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-533">To deploy your application:</span></span>

1.  <span data-ttu-id="f7ba8-534">로 이동 합니다 *앱* 에서 만든 폴더를 [장의 마지막](#chapter-11---build-the-uwp-solution)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="f7ba8-535">파일을 두 번 클릭 해야 하는 '.sln' 확장을 사용 하 여 앱 이름으로 표시 됩니다 하므로, 내에서 엽니다 *Visual Studio*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="f7ba8-536">에 **솔루션 플랫폼**를 선택 **x86, 로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="f7ba8-537">에 **솔루션 구성** 선택 **디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="f7ba8-538">Microsoft HoloLens 알 수 있습니다 것이 더 쉽게 *원격 컴퓨터*컴퓨터로 테더 링 없습니다 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="f7ba8-539">그러나 또한 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="f7ba8-540">알고는 **IP 주소** 내에서 찾을 수 있는 여 HoloLens의는 *설정 > 네트워크 및 인터넷 > Wi-fi > 고급 옵션*; IPv4는 주소를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-540">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="f7ba8-541">확인 **개발자 모드** 됩니다 **에**에; *설정 > 업데이트 및 보안 > 개발자를 위한*합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-541">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![솔루션 배포](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="f7ba8-543">로 이동 합니다 **빌드** 메뉴를 클릭 **솔루션 배포** 컴퓨터에 응용 프로그램을 테스트용으로 로드 하려면.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="f7ba8-544">앱 시작 하 고 테스트 준비가 설치 된 앱 목록에 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="f7ba8-545">Azure Functions 및 저장소 응용 프로그램 완료</span><span class="sxs-lookup"><span data-stu-id="f7ba8-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="f7ba8-546">축, Azure Functions와 Azure Storage 서비스를 활용 하는 혼합된 현실 앱을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="f7ba8-547">앱 저장 된 데이터 및 해당 데이터를 기반으로 하는 작업을 제공 하는 일을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![최종 제품-종료](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="f7ba8-549">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="f7ba8-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="f7ba8-550">연습 1</span><span class="sxs-lookup"><span data-stu-id="f7ba8-550">Exercise 1</span></span>

<span data-ttu-id="f7ba8-551">지점 및 지점에서 생성 된 개체를 생성 하는 레코드를 두 번째 생성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="f7ba8-552">데이터 파일을 로드 하는 경우 원래 만들어진 위치에서 생성 되는 셰이프를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="f7ba8-553">연습 2</span><span class="sxs-lookup"><span data-stu-id="f7ba8-553">Exercise 2</span></span>

<span data-ttu-id="f7ba8-554">다시 열 때마다 필요 하지 않고 앱을 다시 시작 하는 방법을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="f7ba8-555">**백그라운드에서 로드** 좋은 장소에 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="f7ba8-556">그 후에 저장 된 목록을 지울 것인지 방법을 만들어야 *Azure Storage*앱에서 쉽게 다시 설정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7ba8-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
