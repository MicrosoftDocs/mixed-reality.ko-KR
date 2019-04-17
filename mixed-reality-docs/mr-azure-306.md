---
title: MR 및 Azure 306-스트리밍 비디오
description: 혼합된 현실 응용 프로그램에서 Azure Media Services를 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, media services에서 스트리밍 비디오를 360, 몰입 형, vr
ms.openlocfilehash: f6974ab6a72828a557649d5dc65b4e505a7484ff
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599485"
---
>[!NOTE]
><span data-ttu-id="bb27c-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="bb27c-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="bb27c-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="bb27c-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="bb27c-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="bb27c-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="bb27c-110">MR 및 Azure 306: 스트리밍 비디오</span><span class="sxs-lookup"><span data-stu-id="bb27c-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="bb27c-111">![최종 제품-시작](images/AzureLabs-Lab6-00.png)
![최종 제품-시작](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="bb27c-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="bb27c-112">이 과정에서는 알아봅니다 어떻게 Azure Media Services 스트리밍 몰입 형 헤드셋에서 360도 비디오 재생을 허용 하도록 Windows Mixed Reality VR 환경에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="bb27c-113">**Azure Media Services** 은 오늘날 가장 인기 있는 모바일 장치에서 더 많은 대상과 연결에 브로드캐스트 품질 비디오 스트리밍 서비스를 제공 하는 서비스의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="bb27c-114">자세한 내용은 참조는 [Azure Media Services 페이지](https://azure.microsoft.com/services/media-services)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="bb27c-115">이 과정을 완료 해야 혼합된 현실 몰입 형 헤드셋 응용 프로그램을 다음을 수행할 수 있음:</span><span class="sxs-lookup"><span data-stu-id="bb27c-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="bb27c-116">360도 비디오에서 검색을 **Azure Storage**을 통해 합니다 **Azure 미디어 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="bb27c-117">Unity 장면 내 검색된의 360도 비디오를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="bb27c-118">두 개의 다른 비디오를 사용 하 여 두 장면 사이의 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="bb27c-119">응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="bb27c-120">이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="bb27c-121">혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="bb27c-122">장치 지원</span><span class="sxs-lookup"><span data-stu-id="bb27c-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="bb27c-123">과정</span><span class="sxs-lookup"><span data-stu-id="bb27c-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="bb27c-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="bb27c-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="bb27c-125"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="bb27c-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="bb27c-126">MR 및 Azure 306: 스트리밍 비디오</span><span class="sxs-lookup"><span data-stu-id="bb27c-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="bb27c-127">✔️</span><span class="sxs-lookup"><span data-stu-id="bb27c-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="bb27c-128">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="bb27c-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="bb27c-129">이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="bb27c-130">또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 5 월) 작성 시점에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="bb27c-131">내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구 문서 설치](install-the-tools.md)되지만 하지 가정이 과정에서 정보를 아래에 나열 된 보다 최신 소프트웨어에서 찾을 수 있는 항목을 일치 완벽 하 게 합니다 .</span><span class="sxs-lookup"><span data-stu-id="bb27c-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="bb27c-132">다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="bb27c-133">개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용</span><span class="sxs-lookup"><span data-stu-id="bb27c-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="bb27c-134">Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="bb27c-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="bb27c-135">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="bb27c-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="bb27c-136">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="bb27c-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="bb27c-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="bb27c-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="bb27c-138">[Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="bb27c-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="bb27c-139">Azure 설정 및 데이터 검색에 대 한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="bb27c-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="bb27c-140">Mp4 형식으로 두 360도 비디오 (무료 비디오를 찾을 수 있습니다 [이 다운로드 페이지에서](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span><span class="sxs-lookup"><span data-stu-id="bb27c-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="bb27c-141">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="bb27c-141">Before you start</span></span>

1.  <span data-ttu-id="bb27c-142">이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).</span><span class="sxs-lookup"><span data-stu-id="bb27c-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="bb27c-143">설정 하 고 혼합 현실 몰입 형 헤드셋을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bb27c-144">해야 **되지** 이 과정에 대 한 동작 컨트롤러 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="bb27c-145">몰입 형 헤드셋 설정만 지원에 필요한 경우 클릭 하십시오 [Windows Mixed Reality를 설정 하는 방법에 대 한 링크](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="bb27c-146">장 1-Azure Portal: Azure Storage 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="bb27c-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="bb27c-147">사용 하는 **Azure Storage 서비스**를 만들고 구성 해야 합니다는 **저장소 계정** Azure portal에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="bb27c-148">에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="bb27c-149">Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="bb27c-150">클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="bb27c-151">일단 로그인 하면 클릭할 **저장소 계정** 왼쪽된 메뉴에서.</span><span class="sxs-lookup"><span data-stu-id="bb27c-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Azure Storage 계정 설정](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="bb27c-153">에 **Storage 계정** 탭을 클릭 **추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure Storage 계정 설정](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="bb27c-155">에 **저장소 계정 만들기** 탭:</span><span class="sxs-lookup"><span data-stu-id="bb27c-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="bb27c-156">삽입을 **이름을** 계정의 주의 숫자 및 소문자만이 필드를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="bb27c-157">에 대 한 **배포 모델** 선택 **Resource manager**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="bb27c-158">에 대 한 **계정 종류**를 선택 **저장소 (범용 v1)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="bb27c-159">에 대 한 **성능**, 선택 **Standard \* 합니다.**</span><span class="sxs-lookup"><span data-stu-id="bb27c-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="bb27c-160">에 대 한 **복제** 선택 **로컬 중복 저장소 (LRS)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="bb27c-161">둡니다 **보안 전송 필요** 으로 **비활성**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="bb27c-162">선택 된 **구독**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="bb27c-163">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="bb27c-164">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="bb27c-165">확인 합니다 **위치** (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="bb27c-166">위치는 응용 프로그램은 실행할 지역의 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="bb27c-167">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="bb27c-168">이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure Storage 계정 설정](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="bb27c-170">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="bb27c-171">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Storage 계정 설정](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="bb27c-173">이 시점에서 리소스에 따라, 다음 장으로 이동 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="bb27c-174">Azure Portal-2 장: 미디어 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="bb27c-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="bb27c-175">Azure 미디어 서비스를 사용 하려면 (여기서는 계정 보유자는 활성화 해야 관리자) 응용 프로그램에 사용할 수 있도록 서비스의 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="bb27c-176">Azure 포털에서 클릭 **리소스 만들기** 왼쪽 위에서 모서리 및 검색 **미디어 서비스** 키를 눌러 **Enter**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="bb27c-177">현재 원하는 리소스 아이콘이 분홍색 새 페이지를 표시 하려면이 옵션을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="bb27c-179">새 페이지에 대 한 설명을 제공 합니다는 **미디어 서비스**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="bb27c-180">이 프롬프트의 왼쪽 아래에 있는 클릭 합니다 **만들기** 이 서비스를 사용 하 여 연결을 만들려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="bb27c-182">클릭 한 후 **만들기** 새 미디어 서비스에 대 한 일부 세부 정보를 제공 해야 하는 패널이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="bb27c-183">원하는 삽입 **계정 이름** 이 서비스 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="bb27c-184">선택 된 **구독**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="bb27c-185">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="bb27c-186">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="bb27c-187">것이 좋습니다 (예: 이러한 labs)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).</span><span class="sxs-lookup"><span data-stu-id="bb27c-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="bb27c-188">자세한 하려는 경우 Azure 리소스 그룹에 대 한 따르세요 이렇게 [Azure 리소스 그룹을 관리 하는 방법에 대 한 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="bb27c-189">확인 합니다 **위치** (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="bb27c-190">위치는 응용 프로그램은 실행할 지역의 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="bb27c-191">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="bb27c-192">에 대 한 합니다 **저장소 계정** 섹션을 클릭 합니다 **선택 하세요...**  섹션을 클릭 합니다 **저장소 계정** 마지막 챕터에서 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="bb27c-193">이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="bb27c-194">**만들기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-194">Click **Create**.</span></span>

        ![Azure Portal](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="bb27c-196">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="bb27c-197">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="bb27c-199">새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-199">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="bb27c-201">클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="bb27c-202">왼쪽 패널 내에서 새 미디어 서비스 페이지에서 클릭 합니다 **자산** 링크 아래쪽 중간에 대 한입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="bb27c-203">페이지의 왼쪽 위 모서리에 있는 다음 페이지에서 클릭 **업로드**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="bb27c-205">클릭 합니다 **폴더** 아이콘 파일을 찾아 먼저 360 비디오를 스트리밍 하려는 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="bb27c-206">이 수행할 수 있습니다 [샘플 비디오를 다운로드 하려면 링크](https://vimeo.com/214401712)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="bb27c-208">긴 파일 이름 인코더를 사용 하 여 문제를 발생할 수 있습니다: 따라서 비디오에 문제가 없는 되도록 비디오 파일 이름의 길이 줄이는 고려 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="bb27c-209">진행률 표시줄 비디오 업로드가 완료 되 면 녹색으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="bb27c-211">위의 텍스트를 클릭 (**yourservicename-자산**)를 반환 하는 **자산** 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="bb27c-212">비디오 성공적으로 업로드 되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="bb27c-213">클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-213">Click on it.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="bb27c-215">리디렉션됩니다 페이지는 비디오에 대 한 자세한 정보 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="bb27c-216">클릭 하 여 인코딩해야 비디오를 사용 하는 일을 할 수는 **인코딩** 페이지의 왼쪽 위에 있는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="bb27c-218">새 패널이 있는 인코딩 파일에 대 한 옵션을 설정할 수는 오른쪽에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="bb27c-219">(일부는 이미 설정 기본적으로) 다음 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="bb27c-220">**미디어 인코더 이름 *Media Encoder Standard***</span><span class="sxs-lookup"><span data-stu-id="bb27c-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="bb27c-221">**인코딩 사전 설정을 *콘텐츠 적응 다중 비트 전송률 MP4***</span><span class="sxs-lookup"><span data-stu-id="bb27c-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="bb27c-222">**작업 이름 *설정은 Video1.mp4의 Media Encoder Standard 처리***</span><span class="sxs-lookup"><span data-stu-id="bb27c-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="bb27c-223">**출력 미디어 자산 이름 *설정은 Video1.mp4-Media Encoder Standard 인코딩***</span><span class="sxs-lookup"><span data-stu-id="bb27c-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Azure Portal](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="bb27c-225">**만들기** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="bb27c-226">막대를 사용 하 여 확인할 수 있습니다 **추가 하는 인코딩 작업**창을 클릭 하 고 패널 표시 된 Encoding 진행으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-17.png)

    ![Azure Portal](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="bb27c-229">작업이 완료 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="bb27c-230">완료 되 면 자유롭게 'X' 오른쪽 맨 위에 있는 해당 패널을 사용 하 여 패널을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-19.png)

    ![Azure Portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="bb27c-233">이 데 걸리는 시간은 비디오의 파일 크기에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="bb27c-234">이 프로세스에 다소 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="bb27c-235">비디오의 인코딩된 버전을 만든 했으므로 액세스할 수 있도록 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="bb27c-236">이렇게 하려면 파란색 링크를 클릭 **자산** 자산 페이지로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="bb27c-238">다른와 함께 동영상을 보면 \* \* 자산 형식 \* 다중 비트 전송률 MP4 \* 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-238">You will see your video along with another, which is of \*\*Asset Type \*Multi-Bitrate MP4\*\*\*.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="bb27c-240">초기 비디오를 함께 새 자산 임을 알 수 있습니다 *알 수 없는*, 있고 '0' 바이트로 것에 대 한 **크기**, 방금 업데이트에 대 한 창을 새로 고칩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="bb27c-241">이 새 자산을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-241">Click this new asset.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="bb27c-243">이전에이 다른 자산을 사용 하는 유사한 패널을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="bb27c-244">클릭 합니다 **게시** 페이지의 위쪽 가운데에 있는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="bb27c-246">설정 하 라는 메시지가 표시 됩니다는 **로케이터**, 파일/자산에서 s에 대 한 진입점을를 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="bb27c-247">시나리오에 대 한 다음 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="bb27c-248">**Locator 유형을** > **점진적**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="bb27c-249">합니다 **날짜** 하 고 **시간** 에 설정할을 현재 날짜 로부터 이후의 시간 (이 경우 1 백 년).</span><span class="sxs-lookup"><span data-stu-id="bb27c-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="bb27c-250">에 맞게 변경 하거나 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bb27c-251">Locator 및 선택할 수 있습니다 하는 방법에 대 한 자세한 내용은 참조는 [Azure Media Services 설명서](https://docs.microsoft.com/azure/media-services/media-services-concepts)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="bb27c-252">해당 패널의 맨 아래에서 클릭 합니다 **추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="bb27c-254">비디오 게시 이제 되 고 해당 끝점을 사용 하 여 스트리밍할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="bb27c-255">페이지 아래쪽에 추가 된 **파일** 섹션.</span><span class="sxs-lookup"><span data-stu-id="bb27c-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="bb27c-256">비디오의 다양 한 인코딩된 버전 될 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="bb27c-257">하나 가능한 가장 높은 해상도 선택 (아래 이미지에서는 1920 x 960 파일), 후 오른쪽에 패널이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="bb27c-258">여기서 찾을 수 있습니다는 **다운로드 URL**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="bb27c-259">복사해 **끝점** 나중에 코드에서에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-26.png)    

    ![Azure Portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="bb27c-262">누를 수도 있습니다는 **재생** 단추를 비디오를 재생 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="bb27c-263">이제이 실험에서 사용할 두 번째 비디오를 업로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="bb27c-264">두 번째 비디오에 대 한 동일한 프로세스를 반복 합니다. 위의 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="bb27c-265">두 번째를 복사 **끝점** 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="bb27c-266">다음 사용 하 여 [두 번째 비디오를 다운로드 하려면 링크](https://vimeo.com/214402865)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="bb27c-267">두 비디오를 게시 한 후 다음 장에서 이동할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="bb27c-268">3 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="bb27c-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="bb27c-269">다음은 일반적인 등록 혼합 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="bb27c-270">오픈 **Unity** 누릅니다 **새로 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-270">Open **Unity** and click **New**.</span></span> 

    ![Azure Portal](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="bb27c-272">Unity 프로젝트 이름을 제공 해야 이제 삽입 **MR\_360VideoStreaming.** 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="bb27c-273">프로젝트 형식 설정 되어 있는지 확인 **3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="bb27c-274">위치를 적절 한 위치를 설정 합니다 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다).</span><span class="sxs-lookup"><span data-stu-id="bb27c-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="bb27c-275">그런 다음 클릭 **프로젝트 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-275">Then, click **Create project**.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="bb27c-277">Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio입니다.**</span><span class="sxs-lookup"><span data-stu-id="bb27c-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="bb27c-278">로 이동 ***편집할* *기본 설정*** 로 이동한 다음 새 창에서 **외부 도구**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="bb27c-279">변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="bb27c-280">닫기 합니다 **기본 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-280">Close the **Preferences** window.</span></span>

    ![Azure Portal](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="bb27c-282">이동한 다음 ***파일* *빌드 설정*** 전환 하는 플랫폼이 **유니버설 Windows 플랫폼**, 합니다 클릭하여**플랫폼 전환** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="bb27c-283">또한 다음 사항을 확인 합니다</span><span class="sxs-lookup"><span data-stu-id="bb27c-283">Also make sure that:</span></span>

    1. <span data-ttu-id="bb27c-284">**장치를 대상** 로 설정 된 **모든 장치입니다.**</span><span class="sxs-lookup"><span data-stu-id="bb27c-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="bb27c-285">**빌드 형식** 로 설정 된 **D3D 합니다.**</span><span class="sxs-lookup"><span data-stu-id="bb27c-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="bb27c-286">**SDK** 로 설정 된 **최신 설치 합니다.**</span><span class="sxs-lookup"><span data-stu-id="bb27c-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="bb27c-287">**Visual Studio 버전** 로 설정 된 **최신 설치 합니다.**</span><span class="sxs-lookup"><span data-stu-id="bb27c-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="bb27c-288">**빌드 및 실행** 로 설정 된 **로컬 컴퓨터입니다.**</span><span class="sxs-lookup"><span data-stu-id="bb27c-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="bb27c-289">설정에 대 한 걱정 하지 마십시오 **장면** 지금은 설정할 때 이러한 나중입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="bb27c-290">이제 나머지 설정은 기본값으로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-290">The remaining settings should be left as default for now.</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="bb27c-292">에 **빌드 설정** 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 **검사기** 위치한.</span><span class="sxs-lookup"><span data-stu-id="bb27c-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="bb27c-293">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="bb27c-294">에 **기타 설정** 탭:</span><span class="sxs-lookup"><span data-stu-id="bb27c-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="bb27c-295">**스크립팅** **런타임 버전이** 있어야 **안정적인** (.NET 3.5와 같음).</span><span class="sxs-lookup"><span data-stu-id="bb27c-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="bb27c-296">**백 엔드를 스크립팅** 있어야 **.NET.**</span><span class="sxs-lookup"><span data-stu-id="bb27c-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="bb27c-297">**API 호환성 수준** 있어야 **.NET 4.6입니다.**</span><span class="sxs-lookup"><span data-stu-id="bb27c-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="bb27c-299">패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="bb27c-301">내 합니다 **게시 설정** 탭의 **기능**, 확인:</span><span class="sxs-lookup"><span data-stu-id="bb27c-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="bb27c-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="bb27c-302">**InternetClient**</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="bb27c-304">이러한 변경 했다면 닫습니다 합니다 **빌드 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="bb27c-305">프로젝트를 저장 합니다 \**파일* \* 프로젝트 \* \* 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="bb27c-306">4 장-InsideOutSphere Unity 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="bb27c-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bb27c-307">건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드로 바로 계속, 다운로드 자유롭게 [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage),으로 프로젝트로 가져올를 [ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)를 선택한 다음에서 계속 **5 장**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="bb27c-308">Unity 프로젝트 만들기를 계속 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="bb27c-309">Unity 자산 패키지를 다운로드 해야 합니다.이 코스 이라는 [ **InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="bb27c-310">방법 도움말 가져오기 합니다 **unitypackage**:</span><span class="sxs-lookup"><span data-stu-id="bb27c-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="bb27c-311">사용자 앞에 Unity 대시보드를 클릭 **자산** 화면의 맨 위에 있는 메뉴에서 클릭 **가져오기 패키지 > 사용자 지정 패키지**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="bb27c-313">파일 선택기를 사용 하 여 선택 합니다 **InsideOutSphere.unitypackage** 패키징하고 클릭 **오픈**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="bb27c-314">이 자산에 대 한 구성 요소 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="bb27c-315">가져오기를 클릭 하 여 확인 **가져올**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-315">Confirm the import by clicking **Import**.</span></span>

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="bb27c-317">가져오기 완료 되 고, 세 개의 새 폴더를 확인할 수 있습니다 **자료**, **모델**, 및 **Prefabs**, 추가한 사용자 **자산**폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="bb27c-318">이 종류의 폴더 구조는 Unity 프로젝트에 대 한 일반적인입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="bb27c-320">엽니다는 **모델** 폴더를 확인할 수는 **InsideOutSphere** 모델을 가져온 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="bb27c-321">내에서 **자료** 폴더를 찾을 수 있습니다 합니다 **InsideOutSpheres** 자료 *lambert1*를 호출 하는 자료와 함께 *ButtonMaterial*, 곧 표시 되는 GazeButton에서 사용 되는 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="bb27c-322">**Prefabs** 폴더에는 **InsideOutSphere** prefab 둘 다 포함 하는 합니다 **InsideOutSphere** *모델* 및 합니다  *GazeButton*합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="bb27c-323">**포함 된 코드가 없습니다**,이 과정을 수행 하 여 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="bb27c-324">내에서 **계층**를 선택 합니다 **주 카메라** 개체 및 다음 구성 요소 업데이트:</span><span class="sxs-lookup"><span data-stu-id="bb27c-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="bb27c-325">**Transform**</span><span class="sxs-lookup"><span data-stu-id="bb27c-325">**Transform**</span></span>

        1.  <span data-ttu-id="bb27c-326">위치 = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="bb27c-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="bb27c-327">회전 = **X**: 0, **Y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="bb27c-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="bb27c-328">크기 조정 **X**: 1, **Y**: 1, **Z**: 1.</span><span class="sxs-lookup"><span data-stu-id="bb27c-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="bb27c-329">**카메라**</span><span class="sxs-lookup"><span data-stu-id="bb27c-329">**Camera**</span></span>

        1. <span data-ttu-id="bb27c-330">**플래그 지우기**: 단색입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="bb27c-331">**평면 클리핑**: 거의: 0.1, 지금까지: 6.</span><span class="sxs-lookup"><span data-stu-id="bb27c-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="bb27c-333">로 이동 합니다 **Prefab** 폴더를 연 다음 마우스를 끌어를 **InsideOutSphere** 으로 prefab를 **계층** 패널.</span><span class="sxs-lookup"><span data-stu-id="bb27c-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="bb27c-335">확장 된 **InsideOutSphere** 내에서 개체를 **계층** 옆에 있는 작은 화살표를 클릭 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="bb27c-336">표시 됩니다는 **자식** 호출 아래에 있는 개체 **GazeButton**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="bb27c-337">이 장면 및 비디오를 변경 하려면 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-337">This will be used to change scenes and thus videos.</span></span>

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="bb27c-339">검사기 창에서 클릭 합니다 **InsideOutSphere**의 변환 하는 구성 요소는 다음과 같은 속성이 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="bb27c-340">변환-위치</span><span class="sxs-lookup"><span data-stu-id="bb27c-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="bb27c-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-341">**X** 0</span></span>  |          <span data-ttu-id="bb27c-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-342">**Y** 0</span></span>          |  <span data-ttu-id="bb27c-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="bb27c-344">변환-회전</span><span class="sxs-lookup"><span data-stu-id="bb27c-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="bb27c-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-345">**X** 0</span></span>  |          <span data-ttu-id="bb27c-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="bb27c-346">**Y** -50</span></span>        |  <span data-ttu-id="bb27c-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="bb27c-348">변환-확장</span><span class="sxs-lookup"><span data-stu-id="bb27c-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="bb27c-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="bb27c-349">**X** 1</span></span>   |          <span data-ttu-id="bb27c-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="bb27c-350">**Y** 1</span></span>          |  <span data-ttu-id="bb27c-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="bb27c-351">**Z** 1</span></span>  |

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="bb27c-353">클릭 합니다 **GazeButton** 자식 개체를 설정 하 고 해당 **변환** 다음과 같습니다:</span><span class="sxs-lookup"><span data-stu-id="bb27c-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="bb27c-354">변환-위치</span><span class="sxs-lookup"><span data-stu-id="bb27c-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="bb27c-355">**X** 3.6</span><span class="sxs-lookup"><span data-stu-id="bb27c-355">**X** 3.6</span></span>|          <span data-ttu-id="bb27c-356">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="bb27c-356">**Y** 1.3</span></span>        |  <span data-ttu-id="bb27c-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="bb27c-358">변환-회전</span><span class="sxs-lookup"><span data-stu-id="bb27c-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="bb27c-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-359">**X** 0</span></span>  |          <span data-ttu-id="bb27c-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-360">**Y** 0</span></span>          |  <span data-ttu-id="bb27c-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="bb27c-362">변환-확장</span><span class="sxs-lookup"><span data-stu-id="bb27c-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="bb27c-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="bb27c-363">**X** 1</span></span>   |          <span data-ttu-id="bb27c-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="bb27c-364">**Y** 1</span></span>          |  <span data-ttu-id="bb27c-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="bb27c-365">**Z** 1</span></span>  |

    ![InsideOutSphere Unity 패키지 가져오기](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="bb27c-367">-5 장 VideoController 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="bb27c-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="bb27c-368">합니다 **VideoController** 클래스 Azure 미디어 서비스에서 콘텐츠를 스트림 하는 데 사용할 수 있는 두 비디오 끝점을 호스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="bb27c-369">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="bb27c-369">To create this class:</span></span>

1.  <span data-ttu-id="bb27c-370">마우스 오른쪽 단추로 클릭 합니다 **자산 폴더**에 있는 **프로젝트** 패널과 클릭 **만들기 > 폴더**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="bb27c-371">폴더의 이름을 **스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-371">Name the folder **Scripts**.</span></span>

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-43.png)

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="bb27c-374">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="bb27c-375">폴더를 마우스 오른쪽 단추로 클릭 **만들기 > C\# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="bb27c-376">스크립트 이름을 **VideoController**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-376">Name the script **VideoController**.</span></span>

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="bb27c-378">두 번 클릭 하 여 새 **VideoController** 스크립트를 사용 하 여 열고 **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="bb27c-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="bb27c-380">코드 파일의 맨 위에 있는 네임 스페이스는 다음과 같이 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="bb27c-381">다음 변수를 입력 합니다 **VideoController** 클래스와 함께 합니다 **Awake()** 메서드:</span><span class="sxs-lookup"><span data-stu-id="bb27c-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

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

7.  <span data-ttu-id="bb27c-382">이제 다음과 같습니다. Azure 미디어 서비스 비디오에서 끝점을 입력 하는 시간</span><span class="sxs-lookup"><span data-stu-id="bb27c-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="bb27c-383">첫 번째에는 *video1endpoint* 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="bb27c-384">에 두 번째는 *video2endpoint* 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="bb27c-385">사용 하 여 알려진 문제가 *https* 2017.4.1f1 버전을 사용 하 여 Unity 내에서.</span><span class="sxs-lookup"><span data-stu-id="bb27c-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="bb27c-386">오류가 play에서 제공 하는 비디오를 'http'를 대신 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="bb27c-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="bb27c-387">다음으로 **start ()** 메서드를 편집 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="bb27c-388">이 메서드는 사용자 Gaze 단추를 확인 하 여 (결과적으로 전환 되는 비디오) 장면 전환 될 때마다 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="bb27c-389">다음은 **start ()** 메서드를 삽입 합니다 **PlayVideo()** *IEnumerator* 원활 하 게 (따라서 없습니다 끊김 표시 됩니다) 비디오를 시작 하는 데 사용할 메서드를 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

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

10. <span data-ttu-id="bb27c-390">이 클래스에 대해 필요한 마지막 메서드는 **ChangeScene()** 장면 사이 교환에 사용 되는 메서드.</span><span class="sxs-lookup"><span data-stu-id="bb27c-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="bb27c-391">**ChangeScene()** 방법은 유용한 C\# 라는 기능을 *조건부 연산자*합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="bb27c-392">다음 값에 따라 반환 된 단일 문에서 모든 검사의 결과 및이 조건을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="bb27c-393">이 따라 [조건부 연산자에 자세히 알아보려면 링크](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator)합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="bb27c-394">Visual Studio에서 Unity를 반환 하기 전에 변경 내용을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="bb27c-395">다시 Unity 편집기에서 클릭 하 고 끌어서 합니다 **VideoController** 클래스 [] {.underline}는 **스크립트** 폴더를 **주 카메라** 개체를  **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="bb27c-396">클릭 합니다 **주 카메라** 확인 합니다 **검사기 패널**.</span><span class="sxs-lookup"><span data-stu-id="bb27c-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="bb27c-397">새로 추가 된 스크립트 구성 요소에는 빈 값을 사용 하 여 필드를 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="bb27c-398">이것이 코드 내에서 공용 변수를 대상으로 하는 참조 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="bb27c-399">끌어서를 **InsideOutSphere** 에서 개체를 **계층 패널** 에 **구체** 슬롯을 아래 그림과에서 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="bb27c-400">![VideoController 클래스를 만듭니다](images/AzureLabs-Lab6-47.png)
    ![VideoController 클래스 만들기](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="bb27c-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="bb27c-401">-6 장 게이즈 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="bb27c-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="bb27c-402">이 클래스는 생성을 담당를 **Raycast** 는 beprojected 전달할에서 합니다 **주 카메라**, 사용자를 보고 하는 개체를 검색 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-402">This class is responsible for creating a **Raycast** that will beprojected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="bb27c-403">이 경우에 **Raycast** 사용자를 보고 하는 경우를 식별 해야 합니다는 **GazeButton** 장면에 개체 및 동작을 트리거할 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="bb27c-404">이 클래스 만들려면:</span><span class="sxs-lookup"><span data-stu-id="bb27c-404">To create this Class:</span></span>

1.  <span data-ttu-id="bb27c-405">로 이동 합니다 **스크립트** 이전에 만든 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="bb27c-406">마우스 오른쪽 단추로 클릭 합니다 **프로젝트** 패널 \**만듭니다* \* C\# 스크립트 \* \* 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="bb27c-407">스크립트 이름을 **Gaze**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="bb27c-408">두 번 클릭 하 여 새 ***Gaze*** 스크립트를 사용 하 여 열고 **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="bb27c-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="bb27c-409">스크립트의 맨 위에 다음 네임 스페이스를 확인 하 고 다른를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="bb27c-410">그런 다음 내에서 다음 변수를 추가 합니다 **Gaze** 클래스:</span><span class="sxs-lookup"><span data-stu-id="bb27c-410">Then add the following variables inside the **Gaze** class:</span></span>

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

6.  <span data-ttu-id="bb27c-411">에 대 한 코드를 **Awake()** 하 고 **start ()** 메서드는 이제 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="bb27c-412">다음 코드를 추가 합니다 **update ()** 를 Raycast 프로젝트 대상 적중 횟수를 검색 하는 메서드:</span><span class="sxs-lookup"><span data-stu-id="bb27c-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

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

8.  <span data-ttu-id="bb27c-413">Visual Studio에서 Unity를 반환 하기 전에 변경 내용을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="bb27c-414">클릭 하 고 끌어서 합니다 **Gaze** Scripts 폴더에서 클래스를 주 카메라 개체에는 **계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="bb27c-415">7 장-설치 두 Unity 장면</span><span class="sxs-lookup"><span data-stu-id="bb27c-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="bb27c-416">이 챕터의 목적은 각 호스팅 비디오 스트림에 두 작업을 설정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="bb27c-417">새 장면 편집 하는 경우 다시 설정할 필요가 없습니다 있도록 이미 만든 장면 복제 되도록 합니다 *GazeButton* 개체는 다른 위치에 있고 다른 모양을 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="bb27c-418">이 장면 사이 변경 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="bb27c-419">으로 이동 하 여이 작업을 수행할 **파일 >으로 장면 저장...** . 창 저장 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="bb27c-420">클릭 합니다 **새 폴더** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-420">Click the **New folder** button.</span></span>

    ![7 장-설치 두 Unity 장면](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="bb27c-422">폴더의 이름을 **장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="bb27c-423">합니다 **장면 저장** 창 열기 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="bb27c-424">새로 만든 엽니다 **장면** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="bb27c-425">에 **파일 이름:** 텍스트 필드에 입력 **VideoScene1**를 누릅니다 **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="bb27c-426">Unity에서 다시 열에 **장면** 폴더를 마우스 왼쪽 클릭에 **VideoScene1** 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="bb27c-427">키보드를 사용 하 여 키를 누릅니다 **Ctrl + D** 해당 장면 복제</span><span class="sxs-lookup"><span data-stu-id="bb27c-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="bb27c-428">합니다 **중복** 명령으로 이동 하 여 수행할 수 있습니다 **편집 > 중복**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="bb27c-429">자동으로 unity 장면 이름을 번호를 하나씩 늘립니다 않지만 어쨌든 이전에 삽입 된 코드와 일치 하는지 확인 하려면 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="bb27c-430">있어야 **VideoScene1** 하 고 **VideoScene2**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="bb27c-431">에 두 장면 이동 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="bb27c-432">사용 하 여는 **빌드 설정** 창이 열려 드래그 하 여 장면 합니다 **빌드 장면** 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="bb27c-434">모두에 백그라운드에서 선택할 수 있습니다 하 **장면** 보유를 통해 폴더를 **Ctrl** 단추를 한 다음 각 장면은 마우스 왼쪽 단추로 끌어서 마지막에서 두 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="bb27c-435">닫기 합니다 **빌드 설정** 창에서 마우스 두 번 클릭 **VideoScene2**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="bb27c-436">두 번째 장면을 열기를 클릭 합니다 **GazeButton** 의 자식 개체를 **InsideOutSphere**, 변환을 다음과 같이 설정:</span><span class="sxs-lookup"><span data-stu-id="bb27c-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="bb27c-437">변환-위치</span><span class="sxs-lookup"><span data-stu-id="bb27c-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="bb27c-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-438">**X** 0</span></span>  |         <span data-ttu-id="bb27c-439">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="bb27c-439">**Y** 1.3</span></span>         | <span data-ttu-id="bb27c-440">**Z** 3.6</span><span class="sxs-lookup"><span data-stu-id="bb27c-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="bb27c-441">변환-회전</span><span class="sxs-lookup"><span data-stu-id="bb27c-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="bb27c-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-442">**X** 0</span></span>  |          <span data-ttu-id="bb27c-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-443">**Y** 0</span></span>          |  <span data-ttu-id="bb27c-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="bb27c-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="bb27c-445">변환-확장</span><span class="sxs-lookup"><span data-stu-id="bb27c-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="bb27c-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="bb27c-446">**X** 1</span></span>   |          <span data-ttu-id="bb27c-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="bb27c-447">**Y** 1</span></span>          |  <span data-ttu-id="bb27c-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="bb27c-448">**Z** 1</span></span>  |

10. <span data-ttu-id="bb27c-449">사용 하 여는 **GazeButton** 를 선택한 상태로 조회에서 자식 합니다 **검사기** 및를 **메시 필터**.</span><span class="sxs-lookup"><span data-stu-id="bb27c-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="bb27c-450">옆에 작은 대상을 클릭 합니다 **메시** 참조 필드:</span><span class="sxs-lookup"><span data-stu-id="bb27c-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="bb27c-452">A **메시 선택** 팝업 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="bb27c-453">두 번 클릭 합니다 **큐브** 목록에서 메시 **자산**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="bb27c-455">합니다 **메시 필터** 업데이트 되며 이제는 **큐브**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="bb27c-456">이제 클릭 합니다 **기어** 옆에 아이콘 **구체 Collider** 클릭 **구성 요소 제거**,이 개체에서 collider를 삭제 하 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="bb27c-458">사용 하 여는 **GazeButton** 계속 선택한 상태에서 합니다 **구성 요소 추가** 아래쪽의 단추를 **검사기**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="bb27c-459">검색 필드에 입력 **상자**, 및 **상자 Collider** 옵션-추가 하려면 클릭 합니다를 **상자 Collider** 하 여 **GazeButton** 개체 .</span><span class="sxs-lookup"><span data-stu-id="bb27c-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="bb27c-461">그러나 합니다 **GazeButton** 는 부분적으로 업데이트 하는 이제 다른 모양으로 지금 만들려는 새 **자료**완전히 다른 찾아서 쉽게 보다 다른 개체로 인식할 수 있도록 합니다 첫 번째 장면 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="bb27c-462">로 이동 하 **자료** 폴더 내에서 **프로젝트 패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="bb27c-463">복제는 **ButtonMaterial** 자료 (키를 누릅니다 **Ctrl** + **D** 키보드 또는 마우스 왼쪽 단추로 클릭 합니다 **자료**, 다음 **편집** 메뉴 옵션을 선택 파일 **중복**).</span><span class="sxs-lookup"><span data-stu-id="bb27c-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="bb27c-464">![7 장-설정 두 Unity 장면](images/AzureLabs-Lab6-55.png)
    ![7 장 두 Unity 장면 설정](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="bb27c-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="bb27c-465">새 **ButtonMaterial** 자료 (여기 라는 **ButtonMaterial 1**), 및 내는 **검사기**를 클릭 합니다 **Albedo** 색 창입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="bb27c-466">다른 색을 선택할 수 있는 팝업 표시 됩니다 (원하는 중 선택), 한 다음 팝업을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="bb27c-467">자료에는 자체 인스턴스를 됩니다 원래 다른 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-467">The Material will be its own instance, and different to the original.</span></span>

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="bb27c-469">새 끌어 **자료** 에 **GazeButton** 첫 번째 장면 단추에서 쉽게 구분할 수 있도록 이제 해당 확인을 완전히 업데이트 하려면 자식입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="bb27c-471">이 시점에서 UWP 프로젝트를 빌드하기 전에 편집기에서 프로젝트를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="bb27c-472">키를 눌러 합니다 **재생** 단추를 **편집기** 헤드셋 wear 및 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![7 장-두 Unity 장면 설정](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="bb27c-474">두 살펴봅니다 **GazeButton** 첫 번째와 두 번째 비디오를 전환 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="bb27c-475">8 장-UWP 솔루션 빌드</span><span class="sxs-lookup"><span data-stu-id="bb27c-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="bb27c-476">편집기에 오류가 없는지 확인 한 후 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="bb27c-477">빌드:</span><span class="sxs-lookup"><span data-stu-id="bb27c-477">To Build:</span></span>

1.  <span data-ttu-id="bb27c-478">클릭 하 여 현재 장면 저장 **파일 > 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="bb27c-479">호출 확인란 **Unity C\# 프로젝트** (이 중요 한 빌드가 완료 된 후 클래스를 편집할 수)입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="bb27c-480">로 이동 **파일 > 빌드 설정**, 클릭 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="bb27c-481">Buildthe 솔루션을 저장할 폴더를 선택 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-481">You will be prompted to select the folder where you want to buildthe Solution.</span></span>

5.  <span data-ttu-id="bb27c-482">만들기는 **빌드** 폴더 및 해당 폴더 내에서 원하는 적절 한 이름을 다른 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="bb27c-483">새 폴더를 클릭 한 다음 클릭 **폴더 선택**하므로, 해당 위치에서 빌드를 시작 하려면 해당 폴더를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="bb27c-484">![8 장-UWP 솔루션을 빌드합니다](images/AzureLabs-Lab6-60.png)
    ![8 장 UWP 솔루션 빌드](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="bb27c-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="bb27c-485">한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치는 창입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="bb27c-486">로컬 컴퓨터에서 장 9-배포</span><span class="sxs-lookup"><span data-stu-id="bb27c-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="bb27c-487">빌드가 완료 되 면을 **파일 탐색기** 빌드 위치에서 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="bb27c-488">에 빌드된 라는 폴더를 열고 Visual Studio 2017을 사용 하 여 솔루션을 열려면 해당 폴더 내의 솔루션 (.sln) 파일을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="bb27c-489">일만 남게 작업을 수행 하는 컴퓨터에 앱 배포 (또는 *로컬 컴퓨터*).</span><span class="sxs-lookup"><span data-stu-id="bb27c-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="bb27c-490">로컬 컴퓨터에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="bb27c-491">**Visual Studio 2017**, 방금 만든 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="bb27c-492">에 **솔루션 플랫폼**를 선택 **x86, 로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="bb27c-493">에 **솔루션 구성** 선택 **디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![9 장-로컬 컴퓨터에 배포](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="bb27c-495">이제 솔루션 패키지를 복원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="bb27c-496">마우스 오른쪽 단추로 클릭 하 **솔루션**를 클릭 하 고 **솔루션용 NuGet 패키지 복원 하는 중...**</span><span class="sxs-lookup"><span data-stu-id="bb27c-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="bb27c-497">Unity 기본 제공 된 패키지 수를 대상으로 하 여 로컬 컴퓨터 참조를 사용 하 여 작동 해야 하기 때문에 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="bb27c-498">로 이동 **빌드 메뉴** 을 클릭할 **솔루션 배포** 을 컴퓨터에 응용 프로그램을 사이드 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="bb27c-499">Visual Studio 먼저 작성 되며 그런 다음 응용 프로그램을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="bb27c-500">이제 앱 시작할 준비가 되었습니다. 설치 된 앱 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![9 장-로컬 컴퓨터에 배포](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="bb27c-502">혼합 현실 응용 프로그램을 실행 하는 경우 내 야 합니다 **InsideOutSphere** 앱 내에서 사용 하는 모델입니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="bb27c-503">이 구 비디오를 스트리밍할 수를 (큐브 뷰의 이러한 촬영 된)는 들어오는 비디오의 360도 뷰를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="bb27c-504">하지 마세요 앱이 사용할 수 있는 인터넷 속도 따라 몇 로드 시간 (초)을 사용 하는 비디오 경우 놀랄 비디오 요구 사항에 맞춰 페치 및 다운로드에 있으므로 앱으로 스트림 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="bb27c-505">준비 되 면 장면을 변경 하 고 gazing 빨간색 구체에 의해 두 번째 비디오를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="bb27c-506">그런 다음 자유롭게 돌아가 파란색 큐브를 사용 하 여 두 번째 장면에서!</span><span class="sxs-lookup"><span data-stu-id="bb27c-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="bb27c-507">완성 된 Azure 미디어 서비스 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="bb27c-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="bb27c-508">축 하 360 비디오를 스트리밍하려면 Azure 미디어 서비스를 활용 하는 혼합된 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![랩 결과](images/AzureLabs-Lab6-00.png)

![랩 결과](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="bb27c-511">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="bb27c-511">Bonus Exercises</span></span>

<span data-ttu-id="bb27c-512">**연습 1**</span><span class="sxs-lookup"><span data-stu-id="bb27c-512">**Exercise 1**</span></span>

<span data-ttu-id="bb27c-513">것만 단일 장면을 사용 하 여이 자습서에서 비디오를 변경 하는 것이 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="bb27c-514">응용 프로그램을 사용 하 여 실험 하 고 단일 장면으로!</span><span class="sxs-lookup"><span data-stu-id="bb27c-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="bb27c-515">아마도 다른 비디오 목록에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="bb27c-516">**연습 2**</span><span class="sxs-lookup"><span data-stu-id="bb27c-516">**Exercise 2**</span></span>

<span data-ttu-id="bb27c-517">Azure 및 Unity를 사용 하 여 실험 하 고 앱이 인터넷에 연결의 강도 따라 다른 파일 크기를 사용 하 여 비디오를 자동으로 선택 하는 데는 기능을 구현 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb27c-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


