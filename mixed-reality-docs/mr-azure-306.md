---
title: MR 및 Azure 306-스트리밍 비디오
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Media Services을 구현 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, media services, 스트리밍 비디오, 360, 몰입 형, vr
ms.openlocfilehash: 6585aa731ff7ebb89beae67ab0b61ac5ef026e47
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438569"
---
>[!NOTE]
><span data-ttu-id="1c942-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1c942-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1c942-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1c942-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1c942-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1c942-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="1c942-110">MR 및 Azure 306: 스트리밍 비디오</span><span class="sxs-lookup"><span data-stu-id="1c942-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="1c942-111">최종 제품 시작](images/AzureLabs-Lab6-00.png)
![최종 제품 시작을 ![](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="1c942-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="1c942-112">이 과정에서는 Azure Media Services을 Windows Mixed Reality VR 환경에 연결 하 여 몰입 형 헤드셋에서 스트리밍 360도 비디오 재생을 허용 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="1c942-113">**Azure Media Services** 는 브로드캐스트 품질의 비디오 스트리밍 서비스를 제공 하 여 오늘날 가장 인기 있는 모바일 장치에서 더 많은 사용자에 게 도달 하는 서비스 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="1c942-114">자세한 내용은 [Azure Media Services 페이지](https://azure.microsoft.com/services/media-services)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c942-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="1c942-115">이 과정을 완료 하면 다음과 같은 작업을 수행할 수 있는 혼합 현실 모던 헤드셋 응용 프로그램이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="1c942-116">**Azure 미디어 서비스**를 통해 **Azure Storage**에서 360 학위 비디오를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="1c942-117">Unity 장면 내에서 검색 된 360 정도 비디오를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="1c942-118">두 개의 다른 비디오를 사용 하 여 두 장면을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="1c942-119">응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="1c942-120">이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="1c942-121">이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="1c942-122">장치 지원</span><span class="sxs-lookup"><span data-stu-id="1c942-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1c942-123">과정</span><span class="sxs-lookup"><span data-stu-id="1c942-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1c942-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1c942-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1c942-125"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="1c942-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1c942-126">MR 및 Azure 306: 스트리밍 비디오</span><span class="sxs-lookup"><span data-stu-id="1c942-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="1c942-127">✔️</span><span class="sxs-lookup"><span data-stu-id="1c942-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="1c942-128">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="1c942-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="1c942-129">이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="1c942-130">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="1c942-131">[도구 설치 문서](install-the-tools.md)에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="1c942-132">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="1c942-133">모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC</span><span class="sxs-lookup"><span data-stu-id="1c942-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="1c942-134">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="1c942-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1c942-135">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="1c942-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1c942-136">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="1c942-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1c942-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1c942-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="1c942-138">[Windows Mixed Reality 몰입 (VR) 헤드셋](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="1c942-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="1c942-139">Azure 설정 및 데이터 검색을 위한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="1c942-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="1c942-140">Mp4 형식의 2 360 수준 비디오 ( [이 다운로드 페이지에서](https://www.mettle.com/360vr-master-series-free-360-downloads-page)일부 로열티 없는 비디오를 찾을 수 있음)</span><span class="sxs-lookup"><span data-stu-id="1c942-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1c942-141">시작하기 전 확인 사항</span><span class="sxs-lookup"><span data-stu-id="1c942-141">Before you start</span></span>

1.  <span data-ttu-id="1c942-142">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="1c942-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="1c942-143">혼합 현실 모던 헤드셋을 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1c942-144">이 과정에서는 동작 컨트롤러가 필요 **하지** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="1c942-145">모던 헤드셋을 설정 하는 데 지원이 필요한 경우 [Windows Mixed Reality를 설정 하는 방법에 대 한 링크](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)를 클릭 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c942-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="1c942-146">1 장-Azure Portal: Azure Storage 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="1c942-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="1c942-147">**Azure Storage 서비스**를 사용 하려면 Azure Portal에서 **저장소 계정을** 만들고 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="1c942-148">[Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="1c942-149">아직 Azure 계정이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="1c942-150">교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="1c942-151">로그인 되 면 왼쪽 메뉴에서 **저장소 계정** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![계정 설정 Azure Storage](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="1c942-153">**저장소 계정** 탭에서 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![계정 설정 Azure Storage](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="1c942-155">**저장소 계정 만들기** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="1c942-156">계정에 대 한 **이름을** 삽입 합니다 .이 필드에는 숫자 및 소문자만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="1c942-157">**배포 모델에서** **Resource manager**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="1c942-158">**계정 종류**에 대해 **저장소 (범용 v1)** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="1c942-159">**성능**으로 \**표준 *을 선택 합니다.**</span><span class="sxs-lookup"><span data-stu-id="1c942-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="1c942-160">**복제** 의 경우 **LRS (로컬 중복 저장소)** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="1c942-161">**보안 전송을** **사용 하지 않도록 설정**해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="1c942-162">**구독**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="1c942-163">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="1c942-164">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="1c942-165">새 리소스 그룹을 만드는 경우 리소스 그룹의 **위치** 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="1c942-166">위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="1c942-167">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="1c942-168">이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![계정 설정 Azure Storage](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="1c942-170">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="1c942-171">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![계정 설정 Azure Storage](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="1c942-173">이 시점에서 리소스를 따를 필요는 없으며, 다음 챕터로 이동 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="1c942-174">2 장-Azure Portal: Media Service 만들기</span><span class="sxs-lookup"><span data-stu-id="1c942-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="1c942-175">Azure 미디어 서비스를 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다 (계정 소유자가 관리자 여야 함).</span><span class="sxs-lookup"><span data-stu-id="1c942-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="1c942-176">Azure Portal의 왼쪽 위 모서리에서 **리소스 만들기** 를 클릭 하 고 **미디어 서비스를** 검색 한 후 **enter**키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="1c942-177">현재 원하는 리소스에는 분홍색 아이콘이 있습니다. 새 페이지를 표시 하려면이를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="1c942-179">새 페이지에는 **미디어 서비스**에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="1c942-180">이 프롬프트의 왼쪽 아래에서 **만들기** 단추를 클릭 하 여이 서비스와의 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="1c942-182">[ **만들기** ]를 클릭 하면 새 미디어 서비스에 대 한 세부 정보를 제공 해야 하는 위치에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="1c942-183">이 서비스 인스턴스에 대해 원하는 **계정 이름을** 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="1c942-184">**구독**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="1c942-185">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1c942-186">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1c942-187">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="1c942-188">Azure 리소스 그룹에 대해 자세히 알아보려면 [Azure 리소스 그룹을 관리 하는 방법에 대](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c942-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="1c942-189">새 리소스 그룹을 만드는 경우 리소스 그룹의 **위치** 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="1c942-190">위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="1c942-191">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="1c942-192">**저장소 계정** 섹션에서 **선택 ...** 섹션을 클릭 한 다음, 마지막 챕터에서 만든 **저장소 계정을** 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="1c942-193">또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="1c942-194">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-194">Click **Create**.</span></span>

        ![Azure 포털](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="1c942-196">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="1c942-197">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="1c942-199">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-199">Click on the notification to explore your new Service instance.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="1c942-201">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="1c942-202">새 미디어 서비스 페이지의 왼쪽 패널에서 **자산** 링크를 클릭 합니다 (약 중간).</span><span class="sxs-lookup"><span data-stu-id="1c942-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="1c942-203">페이지의 왼쪽 위 모서리에 있는 다음 페이지에서 **업로드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="1c942-205">**폴더** 아이콘을 클릭 하 여 파일을 검색 하 고 스트리밍할 첫 번째 360 비디오를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="1c942-206">이 [링크를 따라 샘플 비디오를 다운로드할](https://vimeo.com/214401712)수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="1c942-208">긴 파일 이름으로 인해 인코더와 관련 된 문제가 발생할 수 있습니다. 따라서 비디오에 문제가 발생 하지 않도록 비디오 파일 이름의 길이를 줄이는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="1c942-209">비디오 업로드가 완료 되 면 진행률 표시줄이 녹색으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="1c942-211">위의 텍스트를 클릭 하 여 **자산** 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="1c942-212">비디오를 성공적으로 업로드 한 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="1c942-213">클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-213">Click on it.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="1c942-215">리디렉션되는 페이지에 비디오에 대 한 자세한 정보가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="1c942-216">비디오를 사용 하려면 페이지 왼쪽 위에 있는 **인코딩** 단추를 클릭 하 여 해당 비디오를 인코딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="1c942-218">파일에 대 한 인코딩 옵션을 설정할 수 있는 새 패널이 오른쪽에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="1c942-219">다음 속성을 설정 합니다. 일부 속성은 기본적으로 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="1c942-220">**미디어 인코더 이름 *Media Encoder Standard***</span><span class="sxs-lookup"><span data-stu-id="1c942-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="1c942-221">**인코딩 사전 설정 *콘텐츠 적응 다중 비트 전송률 MP4***</span><span class="sxs-lookup"><span data-stu-id="1c942-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="1c942-222">***Video1의 작업 이름 Media Encoder Standard 처리 중입니다. mp4***</span><span class="sxs-lookup"><span data-stu-id="1c942-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="1c942-223">**출력 미디어 자산 이름 *Video1--Media Encoder Standard 인코드* 됨**</span><span class="sxs-lookup"><span data-stu-id="1c942-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Azure 포털](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="1c942-225">**만들기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="1c942-226">**인코딩 작업이 추가**된 표시줄이 표시 되 면 해당 표시줄을 클릭 하면 인코딩 진행률이 표시 된 패널이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-17.png)

    ![Azure 포털](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="1c942-229">작업이 완료 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="1c942-230">완료 되 면 해당 패널의 오른쪽 위에 있는 ' X '를 사용 하 여 패널을 자유롭게 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-19.png)

    ![Azure 포털](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="1c942-233">이 작업을 수행 하는 데 걸리는 시간은 비디오의 파일 크기에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="1c942-234">이 프로세스는 상당한 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="1c942-235">이제 인코딩된 버전의 비디오가 생성 되었으므로이를 게시 하 여 액세스할 수 있도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="1c942-236">이렇게 하려면 파란색 링크 **자산** 을 클릭 하 여 자산 페이지로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="1c942-238">비디오는 **자산 유형 _다중 비트 전송률 MP4_** 인 다른 비디오와 함께 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-238">You will see your video along with another, which is of **Asset Type _Multi-Bitrate MP4_**.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="1c942-240">초기 비디오와 함께 새 자산을 *알*수 없으며, **크기**에 대해 ' 0 ' 바이트를 포함 하는 것을 확인할 수 있습니다 .이는 업데이트를 위해 창을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="1c942-241">새 자산을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-241">Click this new asset.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="1c942-243">이전에 사용 했던 것과 비슷한 패널이 표시 됩니다 .이는 다른 자산입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="1c942-244">페이지의 위쪽 가운데에 있는 **게시** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="1c942-246">항목 지점인 **로케이터**를 자산의 파일/s로 설정 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="1c942-247">시나리오에 대해 다음 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="1c942-248"> > **점진적**으로 **로케이터 유형** 입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="1c942-249">**날짜** 및 **시간은** 현재 날짜부터 미래의 시간 (이 경우 100 년)으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="1c942-250">그대로 두거나에 맞게 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1c942-251">로케이터 및 선택할 수 있는 옵션에 대 한 자세한 내용은 [Azure Media Services 설명서](https://docs.microsoft.com/azure/media-services/media-services-concepts)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1c942-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="1c942-252">해당 패널의 아래쪽에서 **추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="1c942-254">이제 비디오가 게시 되 고 해당 끝점을 사용 하 여 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="1c942-255">페이지 아래쪽에는 **파일** 섹션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="1c942-256">여기에는 다양 한 인코딩된 버전의 비디오가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="1c942-257">가능한 가장 높은 해상도를 선택 하 고 (아래 이미지에서 1920x960 파일) 오른쪽에 패널이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="1c942-258">여기에서 **다운로드 URL**을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="1c942-259">나중에 코드에서 사용할 때이 **끝점** 을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-26.png)    

    ![Azure 포털](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="1c942-262">**재생** 단추를 눌러 비디오를 재생 하 고 테스트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="1c942-263">이제이 랩에서 사용할 두 번째 비디오를 업로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="1c942-264">위의 단계를 수행 하 여 두 번째 비디오에 대해 동일한 프로세스를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="1c942-265">두 번째 **끝점** 도 복사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="1c942-266">다음 링크를 사용 [하 여 두 번째 비디오를 다운로드할 수](https://vimeo.com/214402865)있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="1c942-267">두 비디오를 모두 게시 한 후에는 다음 장으로 이동할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="1c942-268">3 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="1c942-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="1c942-269">다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="1c942-270">**Unity** 를 열고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-270">Open **Unity** and click **New**.</span></span> 

    ![Azure 포털](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="1c942-272">이제 Unity 프로젝트 이름을 제공 하 고 **MR\_360VideoStreaming**을 삽입 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="1c942-273">프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="1c942-274">위치를 적절 한 위치에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1c942-275">그런 다음 **프로젝트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-275">Then, click **Create project**.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="1c942-277">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio** 로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="1c942-278">***기본 설정* 편집** 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1c942-279">**외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="1c942-280">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-280">Close the **Preferences** window.</span></span>

    ![Azure 포털](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="1c942-282">그런 다음 ***파일* *빌드 설정*** 으로 이동 하 고 플랫폼 **전환** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼**로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="1c942-283">또한 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-283">Also make sure that:</span></span>

    1. <span data-ttu-id="1c942-284">**대상 장치** 는 **임의의 장치로** 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="1c942-285">**빌드 형식이** D3D로 설정 됩니다 **.**</span><span class="sxs-lookup"><span data-stu-id="1c942-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="1c942-286">**SDK** 가 최신 설치로 설정 되어 **있습니다.**</span><span class="sxs-lookup"><span data-stu-id="1c942-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="1c942-287">**Visual Studio 버전이** 최신 설치로 설정 되어 **있습니다.**</span><span class="sxs-lookup"><span data-stu-id="1c942-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="1c942-288">**빌드 및 실행** 이 **로컬 컴퓨터** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="1c942-289">나중에 설정 하므로 지금 바로 **장면을** 설정 하는 것에 대해 걱정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="1c942-290">지금은 나머지 설정이 기본값으로 유지 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-290">The remaining settings should be left as default for now.</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="1c942-292">**빌드 설정** 창에서 **플레이어 설정** 단추를 클릭 하면 **검사기** 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="1c942-293">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="1c942-294">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="1c942-295">**Scripting** **Runtime 버전** 은 **안정적** 이어야 합니다 (.net 3.5 해당).</span><span class="sxs-lookup"><span data-stu-id="1c942-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="1c942-296">**Scripting 백엔드** 는 .net 이어야 합니다 **.**</span><span class="sxs-lookup"><span data-stu-id="1c942-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="1c942-297">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="1c942-299">패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="1c942-301">**게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="1c942-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="1c942-302">**InternetClient**</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="1c942-304">이러한 변경을 수행한 후에는 **빌드 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="1c942-305">프로젝트를 저장 합니다. \**파일* \* 프로젝트 저장 \* \*.</span><span class="sxs-lookup"><span data-stu-id="1c942-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="1c942-306">4 장-Into Out구에 Unity 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="1c942-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c942-307">이 과정의 *Unity 설정* 구성 요소를 건너뛰고 계속 해 서 코드를 계속 사용 하려면 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)를 다운로드 하 여 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 **5 장**에서 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="1c942-308">Unity 프로젝트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="1c942-309">이 과정에서는 [**unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)이라는 Unity 자산 패키지를 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="1c942-310">방법: **unitypackage**를 가져오는 방법:</span><span class="sxs-lookup"><span data-stu-id="1c942-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="1c942-311">앞의 Unity 대시보드를 사용 하 여 화면 위쪽의 메뉴에서 **자산** 을 클릭 하 고 **패키지 가져오기 > 사용자 지정 패키지**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="1c942-313">파일 선택기를 사용 하 여 **unitypackage** 패키지를 선택 하 고 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="1c942-314">이 자산의 구성 요소 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="1c942-315">**가져오기를 클릭 하**여 가져오기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-315">Confirm the import by clicking **Import**.</span></span>

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="1c942-317">가져오기가 완료 되 면 세 개의 새 폴더 ( **재질**, **모델**및 **Prefabs**)가 **자산** 폴더에 추가 된 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="1c942-318">이러한 종류의 폴더 구조는 Unity 프로젝트에 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="1c942-320">**모델** 폴더를 열면 **Into out구에** 모델을 가져왔는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="1c942-321">**재질** 폴더 내에서 GazeButton에서 사용 되는 *buttonmaterial*이라는 재질과 함께 **inlambert1 out구** 자료를 찾을 수 있습니다 .이는 곧 표시 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="1c942-322">**Prefabs** 폴더에는 **insideoutsphere** *모델* 및 *GazeButton*를 모두 포함 하는 **inprefab out구가** 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="1c942-323">**코드는 포함 되지 않으며**,이 과정을 수행 하 여 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="1c942-324">**계층**내에서 **주 카메라** 개체를 선택 하 고 다음 구성 요소를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="1c942-325">**변환**</span><span class="sxs-lookup"><span data-stu-id="1c942-325">**Transform**</span></span>

        1.  <span data-ttu-id="1c942-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="1c942-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="1c942-327">회전 = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="1c942-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="1c942-328">크기 조정 **X**: 1, **Y**: 1, **Z**: 1.</span><span class="sxs-lookup"><span data-stu-id="1c942-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="1c942-329">**카메라**</span><span class="sxs-lookup"><span data-stu-id="1c942-329">**Camera**</span></span>

        1. <span data-ttu-id="1c942-330">**플래그 지우기**: 단색입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="1c942-331">**클리핑 평면**: 근거리: 0.1, 먼: 6.</span><span class="sxs-lookup"><span data-stu-id="1c942-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="1c942-333">**Prefab** 폴더로 이동한 다음 **Insideoutsphere** Prefab을 **계층** 패널로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="1c942-335">옆의 작은 화살표를 클릭 하 여 **계층** 내에서 **Insideoutsphere** 개체를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="1c942-336">**GazeButton**라는 자식 개체 아래에 **자식** 개체가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="1c942-337">이는 장면을 변경 하는 데 사용 되며 비디오를 변경 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-337">This will be used to change scenes and thus videos.</span></span>

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="1c942-339">검사기 창에서 **Insideoutsphere**변형 구성 요소를 클릭 하 고 다음 속성을 설정 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="1c942-340">변환 위치</span><span class="sxs-lookup"><span data-stu-id="1c942-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="1c942-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-341">**X** 0</span></span>  |          <span data-ttu-id="1c942-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-342">**Y** 0</span></span>          |  <span data-ttu-id="1c942-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="1c942-344">변환-회전</span><span class="sxs-lookup"><span data-stu-id="1c942-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="1c942-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-345">**X** 0</span></span>  |          <span data-ttu-id="1c942-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="1c942-346">**Y** -50</span></span>        |  <span data-ttu-id="1c942-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="1c942-348">변환-배율</span><span class="sxs-lookup"><span data-stu-id="1c942-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="1c942-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="1c942-349">**X** 1</span></span>   |          <span data-ttu-id="1c942-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="1c942-350">**Y** 1</span></span>          |  <span data-ttu-id="1c942-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="1c942-351">**Z** 1</span></span>  |

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="1c942-353">**GazeButton** 자식 개체를 클릭 하 고 다음과 같이 **변환을** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="1c942-354">변환 위치</span><span class="sxs-lookup"><span data-stu-id="1c942-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="1c942-355">**X** 3.6</span><span class="sxs-lookup"><span data-stu-id="1c942-355">**X** 3.6</span></span>|          <span data-ttu-id="1c942-356">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="1c942-356">**Y** 1.3</span></span>        |  <span data-ttu-id="1c942-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="1c942-358">변환-회전</span><span class="sxs-lookup"><span data-stu-id="1c942-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="1c942-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-359">**X** 0</span></span>  |          <span data-ttu-id="1c942-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-360">**Y** 0</span></span>          |  <span data-ttu-id="1c942-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="1c942-362">변환-배율</span><span class="sxs-lookup"><span data-stu-id="1c942-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="1c942-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="1c942-363">**X** 1</span></span>   |          <span data-ttu-id="1c942-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="1c942-364">**Y** 1</span></span>          |  <span data-ttu-id="1c942-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="1c942-365">**Z** 1</span></span>  |

    ![Into Out구에 Unity 패키지 가져오기](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="1c942-367">5 장-VideoController 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="1c942-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="1c942-368">**Videocontroller** 클래스는 Azure 미디어 서비스에서 콘텐츠를 스트리밍하는 데 사용 되는 두 개의 비디오 끝점을 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="1c942-369">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="1c942-369">To create this class:</span></span>

1.  <span data-ttu-id="1c942-370">**프로젝트** 패널에 있는 **자산 폴더**를 마우스 오른쪽 단추로 클릭 하 고 **> 폴더 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="1c942-371">폴더 이름을 **스크립트**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-371">Name the folder **Scripts**.</span></span>

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-43.png)

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="1c942-374">**스크립트** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="1c942-375">폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **> C\# 스크립트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="1c942-376">스크립트의 이름을 **Videocontroller**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-376">Name the script **VideoController**.</span></span>

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="1c942-378">새 **Videocontroller** 스크립트를 두 번 클릭 하 여 **Visual Studio 2017** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="1c942-380">다음과 같이 코드 파일의 맨 위에 있는 네임 스페이스를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="1c942-381">**Videocontroller** 클래스에서 다음 변수를 해제 **()** 메서드와 함께 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  <span data-ttu-id="1c942-382">이제 Azure 미디어 서비스 비디오에서 끝점을 입력 하는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="1c942-383">*Video1endpoint* 변수에 대 한 첫 번째입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="1c942-384">*Video2endpoint* 변수에 대 한 두 번째입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="1c942-385">Unity에서 *https* 를 사용 하는 경우 버전 2017.4.1 f1를 사용 하는 것과 관련 된 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="1c942-386">비디오를 재생 하는 동안 오류가 발생 하는 경우 ' http '를 대신 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="1c942-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="1c942-387">다음으로 **Start ()** 메서드를 편집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="1c942-388">이 메서드는 사용자가 장면을 전환할 때마다 (따라서 비디오를 전환) 응시 단추를 살펴보면 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="1c942-389">**Start ()** 메서드를 따라 비디오를 원활 하 게 시작 하는 데 사용 되는 **playvideo ()** *IEnumerator* 메서드를 삽입 합니다 (끊길 표시 되지 않음).</span><span class="sxs-lookup"><span data-stu-id="1c942-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. <span data-ttu-id="1c942-390">이 클래스에 필요한 마지막 메서드는 **ChangeScene ()** 메서드로, 장면을 전환 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="1c942-391">**ChangeScene ()** 메서드는 *조건 연산자*라고 하는 유용한 C\# 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="1c942-392">이렇게 하면 조건을 확인 한 다음 검사 결과에 따라 반환 되는 값을 모두 단일 문 내에서 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="1c942-393">[조건 연산자에 대 한 자세한 내용을 보려면이 링크를](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)따르세요.</span><span class="sxs-lookup"><span data-stu-id="1c942-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="1c942-394">Unity로 반환 하기 전에 Visual Studio에서 변경 내용을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="1c942-395">Unity 편집기로 돌아가서, **Videocontroller** 클래스 [from] {. 밑줄} **스크립트** 폴더를 **계층** 패널의 **기본 카메라** 개체로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="1c942-396">**주 카메라** 를 클릭 하 고 **검사기 패널**을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="1c942-397">새로 추가한 스크립트 구성 요소에 빈 값이 있는 필드가 있음을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="1c942-398">코드 내에서 공용 변수를 대상으로 하는 참조 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="1c942-399">아래 이미지에 표시 된 것 처럼 **계층 패널** 에서 **구** 슬롯으로 **in의 out구** 개체를 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="1c942-400">videocontroller 클래스](images/AzureLabs-Lab6-47.png)
    만드는 ![![비디오 컨트롤러 클래스를 만듭니다](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="1c942-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="1c942-401">6 장-응시 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="1c942-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="1c942-402">이 클래스는 사용자가 보고 있는 개체를 검색 하기 위해 **기본 카메라**에서 전달 되는 **raycast** 를 만드는 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-402">This class is responsible for creating a **Raycast** that will beprojected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="1c942-403">이 경우에는 사용자가 장면의 **GazeButton** 개체를 보고 동작을 트리거할 수 있는지 여부를 확인 **해야 합니다.**</span><span class="sxs-lookup"><span data-stu-id="1c942-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="1c942-404">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="1c942-404">To create this Class:</span></span>

1.  <span data-ttu-id="1c942-405">이전에 만든 **스크립트** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="1c942-406">**프로젝트** 패널을 마우스 오른쪽 단추로 클릭 하 고 \**만들기* \* C\# 스크립트 \* \*를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="1c942-407">스크립트 이름을 **응시**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="1c942-408">새 ***응시*** 스크립트를 두 번 클릭 하 여 **Visual Studio 2017** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="1c942-409">다음 네임 스페이스가 스크립트의 맨 위에 있는지 확인 하 고 다른 네임 스페이스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="1c942-410">그런 다음, 다음 변수를 **응시** 클래스 내에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-410">Then add the following variables inside the **Gaze** class:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  <span data-ttu-id="1c942-411">이제 해제 **()** 및 **Start ()** 메서드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  <span data-ttu-id="1c942-412">**Update ()** 메서드에 다음 코드를 추가 하 여 Raycast를 프로젝션 하 고 대상 적중을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  <span data-ttu-id="1c942-413">Unity로 반환 하기 전에 Visual Studio에서 변경 내용을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="1c942-414">Scripts 폴더의 Scripts **클래스를** 클릭 하 고 **계층** 패널의 기본 카메라 개체로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="1c942-415">7 장-두 Unity 장면 설정</span><span class="sxs-lookup"><span data-stu-id="1c942-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="1c942-416">이 챕터의 목적은 각각 비디오를 스트리밍하는 두 개의 장면을 설정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="1c942-417">이미 만든 장면을 복제 하므로 다시 설정할 필요가 없습니다. 그러나 *GazeButton* 개체가 다른 위치에 있고 다른 모양을 갖도록 하기 위해 새 장면을 편집 하는 경우에는 새 장면을 편집 해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="1c942-418">이는 장면을 변경 하는 방법을 보여 주기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="1c942-419">파일로 이동 하 여이 작업을 수행 하려면 **다른 이름으로 장면 저장**...을 > 합니다. 저장 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="1c942-420">**새 폴더** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-420">Click the **New folder** button.</span></span>

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="1c942-422">폴더 이름을 **장면**으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="1c942-423">**장면 저장** 창이 계속 열려 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="1c942-424">새로 만든 **장면** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="1c942-425">**파일 이름:** 텍스트 필드에 **VideoScene1**를 입력 하 고 **저장**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="1c942-426">Unity로 돌아가서, **장면** 폴더를 열고 **VideoScene1** 파일을 마우스 왼쪽 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="1c942-427">키보드를 사용 하 고 **ctrl + D** 를 누르면 해당 장면이 복제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="1c942-428">**편집 > 복제**로 이동 하 여 **중복** 명령을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="1c942-429">Unity는 장면 이름 번호를 자동으로 증가 하지만이를 확인 하 여 이전에 삽입 된 코드와 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="1c942-430">**VideoScene1** 및 **VideoScene2**가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="1c942-431">두 개의 장면을 사용 하 여 **파일 > 빌드 설정**으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="1c942-432">**빌드 설정** 창을 열고, **빌드 섹션에서** 장면을 장면을 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="1c942-434">**Ctrl** 단추를 누른 채 각 장면을 마우스 왼쪽 단추로 클릭 하 고 마지막으로 둘 다로 끌어 **장면** 폴더에서 두 장면을 모두 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="1c942-435">**빌드 설정** 창을 닫고 **VideoScene2**을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="1c942-436">두 번째 장면을 연 상태에서 **InGazeButton** 자식 개체를 클릭 하 고다음과 같이 변환을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="1c942-437">변환 위치</span><span class="sxs-lookup"><span data-stu-id="1c942-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="1c942-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-438">**X** 0</span></span>  |         <span data-ttu-id="1c942-439">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="1c942-439">**Y** 1.3</span></span>         | <span data-ttu-id="1c942-440">**Z** 3.6</span><span class="sxs-lookup"><span data-stu-id="1c942-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="1c942-441">변환-회전</span><span class="sxs-lookup"><span data-stu-id="1c942-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="1c942-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-442">**X** 0</span></span>  |          <span data-ttu-id="1c942-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-443">**Y** 0</span></span>          |  <span data-ttu-id="1c942-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="1c942-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="1c942-445">변환-배율</span><span class="sxs-lookup"><span data-stu-id="1c942-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="1c942-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="1c942-446">**X** 1</span></span>   |          <span data-ttu-id="1c942-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="1c942-447">**Y** 1</span></span>          |  <span data-ttu-id="1c942-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="1c942-448">**Z** 1</span></span>  |

10. <span data-ttu-id="1c942-449">**GazeButton** child가 선택 된 상태에서 **검사기** 와 **메시 필터**를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="1c942-450">**메시** 참조 필드 옆에 있는 대상을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="1c942-452">**메시 선택** 팝업 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="1c942-453">**자산**목록에서 **큐브** 메시를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="1c942-455">**메시 필터** 는 업데이트 되 고 이제 **큐브**를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="1c942-456">이제 **구 collider** 옆의 **기어** 아이콘을 클릭 하 고 **구성 요소 제거**를 클릭 하 여이 개체에서 Collider를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="1c942-458">**GazeButton** 가 선택 된 상태에서 **검사기**아래쪽의 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="1c942-459">검색 필드에 **box**를 입력 하 고 **상자 collider** 가 옵션으로 선택 되어 **GazeButton** 개체에 **상자 collider** 를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="1c942-461">이제 **GazeButton** 가 부분적으로 업데이트 되 고, 다른 것 처럼 보이지만, 이제는 새 **자료**를 만들어이를 완전히 다르게 표시 하 고 첫 번째 장면의 개체와 다른 개체로 인식 하기가 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="1c942-462">**프로젝트 패널**내에서 **재질** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="1c942-463">**Buttonmaterial** 재질을 복제 합니다. 키보드에서 **Ctrl** + **D** 를 누르거나 **재질**을 마우스 왼쪽 단추로 클릭 한 다음 파일 **편집** 메뉴 옵션에서 **중복**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="1c942-464">7 장 ![--두 Unity 장면을 설정](images/AzureLabs-Lab6-55.png)
    ![7 장--두 Unity 장면을 설정](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="1c942-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="1c942-465">새 **buttonmaterial** 재질 (여기서는 **buttonmaterial 1**이라고 함)을 선택 하 고 **검사기**내에서 **albedo** 색 창을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="1c942-466">다른 색을 선택할 수 있는 팝업이 표시 됩니다. 여기서 원하는 것을 선택 하 고 팝업을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="1c942-467">자료는 자체 인스턴스가 되며 원본과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-467">The Material will be its own instance, and different to the original.</span></span>

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="1c942-469">새 **자료** 를 **GazeButton** 자식으로 끌어 옵니다. 그러면 첫 번째 장면 단추와 쉽게 구분할 수 있도록 모양이 완전히 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="1c942-471">이 시점에서 UWP 프로젝트를 빌드하기 전에 편집기에서 프로젝트를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="1c942-472">**편집기** 에서 **재생** 단추를 누르고 헤드셋을 착용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![7 장--두 Unity 장면 설정](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="1c942-474">두 개의 **GazeButton** 개체를 확인 하 여 첫 번째와 두 번째 비디오 간을 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="1c942-475">8 장-UWP 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="1c942-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="1c942-476">편집기에 오류가 없으면 빌드할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="1c942-477">빌드:</span><span class="sxs-lookup"><span data-stu-id="1c942-477">To Build:</span></span>

1.  <span data-ttu-id="1c942-478">**파일 > 저장**을 클릭 하 여 현재 장면을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="1c942-479">**Unity C\# 프로젝트** 라는 상자를 선택 합니다 .이는 빌드를 완료 한 후 클래스를 편집할 수 있도록 하기 때문에 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="1c942-480">**파일 > 빌드 설정**으로 이동 하 고 **빌드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="1c942-481">솔루션을 buildthe 폴더를 선택 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-481">You will be prompted to select the folder where you want to buildthe Solution.</span></span>

5.  <span data-ttu-id="1c942-482">**빌드** 폴더를 만들고 해당 폴더 내에서 원하는 적절 한 이름을 사용 하 여 다른 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="1c942-483">새 폴더를 클릭 한 다음 **폴더 선택**을 클릭 하 여 해당 폴더를 선택 하 고 해당 위치에서 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="1c942-484">![장 8 장--![챕터를](images/AzureLabs-Lab6-60.png)
    UWP 솔루션 빌드](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="1c942-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="1c942-485">Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="1c942-486">9 장-로컬 컴퓨터에 배포</span><span class="sxs-lookup"><span data-stu-id="1c942-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="1c942-487">빌드가 완료 되 면 빌드 위치에 **파일 탐색기** 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="1c942-488">이름을 지정 하 고 빌드한 폴더를 연 다음 해당 폴더 내에서 솔루션 (.sln) 파일을 두 번 클릭 하 여 Visual Studio 2017에서 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="1c942-489">남은 작업은 사용자의 컴퓨터 (또는 *로컬 컴퓨터*)에 앱을 배포 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="1c942-490">로컬 컴퓨터에 배포 하려면:</span><span class="sxs-lookup"><span data-stu-id="1c942-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="1c942-491">**Visual Studio 2017**에서 방금 만든 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="1c942-492">**솔루션 플랫폼**에서 **X86, 로컬 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="1c942-493">**솔루션 구성** 에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![9 장--로컬 컴퓨터에 배포](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="1c942-495">이제 솔루션에 대 한 패키지를 복원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="1c942-496">**솔루션**을 마우스 오른쪽 단추로 클릭 하 고 **솔루션에 대 한 NuGet 패키지 복원** ...을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="1c942-497">이 작업은 Unity가 빌드된 패키지가 로컬 컴퓨터 참조를 대상으로 해야 하기 때문에 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="1c942-498">**빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 컴퓨터에 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="1c942-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="1c942-499">Visual Studio는 먼저 응용 프로그램을 빌드한 다음 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="1c942-500">이제 앱이 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![9 장--로컬 컴퓨터에 배포](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="1c942-502">Mixed Reality 응용 프로그램을 실행 하는 경우 앱 내에서 사용한 **Into Out구에** 모델 내에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="1c942-503">이 구는 이러한 종류의 관점에서 filmed 된 들어오는 비디오 (360)를 제공 하 여 비디오가 스트리밍되는 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="1c942-504">비디오를 로드 하는 데 몇 초 정도 걸릴 수 있으며, 비디오를 가져와 다운로드 한 다음 앱으로 스트리밍하려면 앱에 사용 가능한 인터넷 속도가 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="1c942-505">준비가 되 면 장면을 변경 하 고 red 구를 gazing 하 여 두 번째 비디오를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="1c942-506">그런 다음 두 번째 장면에서 파란색 큐브를 사용 하 여 뒤로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="1c942-507">완성 된 Azure Media Service 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="1c942-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="1c942-508">축 하 합니다. Azure 미디어 서비스를 활용 하 여 360 비디오를 스트리밍하는 혼합 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![랩 결과](images/AzureLabs-Lab6-00.png)

![랩 결과](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="1c942-511">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="1c942-511">Bonus Exercises</span></span>

<span data-ttu-id="1c942-512">**연습 1**</span><span class="sxs-lookup"><span data-stu-id="1c942-512">**Exercise 1**</span></span>

<span data-ttu-id="1c942-513">이 자습서 내에서 단일 장면을 사용 하 여 비디오를 변경 하는 것만 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="1c942-514">응용 프로그램을 실험 하 고 단일 장면으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="1c942-515">혼합에 다른 비디오를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c942-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="1c942-516">**연습 2**</span><span class="sxs-lookup"><span data-stu-id="1c942-516">**Exercise 2**</span></span>

<span data-ttu-id="1c942-517">Azure 및 Unity를 실험 하 고 인터넷 연결의 강도에 따라 앱에서 다른 파일 크기의 비디오를 자동으로 선택 하는 기능을 구현 해 보세요.</span><span class="sxs-lookup"><span data-stu-id="1c942-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


