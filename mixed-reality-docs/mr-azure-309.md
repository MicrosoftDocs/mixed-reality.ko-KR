---
title: MR 및 Azure 309-Application insights
description: Azure 애플리케이션 Insights 서비스를 사용 하 여 혼합 현실 응용 프로그램 내에서 사용자 동작에 대 한 분석을 수집 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, application insights, hololens, 몰입 형, vr
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694566"
---
>[!NOTE]
><span data-ttu-id="dd20f-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="dd20f-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="dd20f-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="dd20f-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="dd20f-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="dd20f-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="dd20f-110">MR 및 Azure 309: Application insights</span><span class="sxs-lookup"><span data-stu-id="dd20f-110">MR and Azure 309: Application insights</span></span>

![최종 제품-시작](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="dd20f-112">이 과정에서는 Azure 애플리케이션 Insights API를 사용 하 여 혼합 현실 응용 프로그램에 Application Insights 기능을 추가 하 여 사용자 동작에 대 한 분석을 수집 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="dd20f-113">Application Insights는 개발자가 응용 프로그램에서 분석을 수집 하 고 사용 하기 쉬운 포털에서 관리할 수 있도록 해 주는 Microsoft 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="dd20f-114">분석은 수집 하려는 사용자 지정 정보에 대 한 성능에 이르기까지 모든 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="dd20f-115">자세한 내용은 [Application Insights 페이지](https://azure.microsoft.com/services/application-insights/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dd20f-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="dd20f-116">이 과정을 완료 하면 다음과 같은 작업을 수행할 수 있는 혼합 현실 모던 헤드셋 응용 프로그램이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="dd20f-117">사용자가 장면을 응시 하 고 장면을 탐색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="dd20f-118">응시를 사용 하 고 장면 내 개체에 근접을 사용 하 여 *Application Insights 서비스*에 대 한 분석 보내기를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="dd20f-119">또한 앱은 서비스에 대해를 호출 하 여 최근 24 시간 이내에 사용자가 가장 많이 접근 한 개체에 대 한 정보를 인출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="dd20f-120">해당 개체의 색을 녹색으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-120">That object will change its color to green.</span></span>

<span data-ttu-id="dd20f-121">이 과정을 통해 Application Insights 서비스에서 Unity 기반 샘플 응용 프로그램으로 결과를 가져오는 방법을 배울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="dd20f-122">빌드할 수 있는 사용자 지정 응용 프로그램에 이러한 개념을 적용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="dd20f-123">장치 지원</span><span class="sxs-lookup"><span data-stu-id="dd20f-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="dd20f-124">과정</span><span class="sxs-lookup"><span data-stu-id="dd20f-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="dd20f-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="dd20f-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="dd20f-126"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="dd20f-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="dd20f-127">MR 및 Azure 309: Application insights</span><span class="sxs-lookup"><span data-stu-id="dd20f-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="dd20f-128">✔️</span><span class="sxs-lookup"><span data-stu-id="dd20f-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="dd20f-129">✔️</span><span class="sxs-lookup"><span data-stu-id="dd20f-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="dd20f-130">이 과정에서 주로 Windows Mixed Reality (VR) 헤드셋에 초점을 맞춘 반면,이 과정에서 학습 하는 내용을 Microsoft HoloLens에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="dd20f-131">과정을 진행할 때 HoloLens를 지원 하기 위해 사용 해야 하는 모든 변경 내용에 대 한 메모를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="dd20f-132">HoloLens를 사용 하는 경우 음성 캡처 중에 몇 가지 echo를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dd20f-133">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="dd20f-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="dd20f-134">이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="dd20f-135">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (7 월 2018)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="dd20f-136">[도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="dd20f-137">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="dd20f-138">모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC</span><span class="sxs-lookup"><span data-stu-id="dd20f-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="dd20f-139">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="dd20f-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="dd20f-140">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="dd20f-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="dd20f-141">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="dd20f-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="dd20f-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="dd20f-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="dd20f-143">개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="dd20f-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="dd20f-144">기본 제공 마이크가 있는 헤드폰 집합 (헤드셋에 기본 제공 mic 및 스피커가 없는 경우)</span><span class="sxs-lookup"><span data-stu-id="dd20f-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="dd20f-145">Azure 설정 및 Application Insights 데이터 검색을 위한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="dd20f-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="dd20f-146">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="dd20f-146">Before you start</span></span>

<span data-ttu-id="dd20f-147">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="dd20f-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="dd20f-148">*Application Insights* 로 이동 하는 데이터에는 시간이 걸리므로 잠시 기다려 주십시오.</span><span class="sxs-lookup"><span data-stu-id="dd20f-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="dd20f-149">서비스에서 데이터를 받았는지 확인 하려면 포털을 탐색 하는 방법을 보여 주는 [14 장](#chapter-14---the-application-insights-service-portal)을 확인 하세요.</span><span class="sxs-lookup"><span data-stu-id="dd20f-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="dd20f-150">1 장-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="dd20f-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="dd20f-151">*Application Insights*를 사용 하려면 Azure Portal에서 *Application Insights 서비스* 를 만들고 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="dd20f-152">[Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="dd20f-153">아직 Azure 계정이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="dd20f-154">교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="dd20f-155">로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 *Application Insights*를 검색 한 다음 **Enter 키**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="dd20f-156">새 단어는 **새** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Azure 포털](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="dd20f-158">오른쪽의 새 페이지는 *Azure 애플리케이션 Insights* 서비스에 대 한 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="dd20f-159">이 페이지의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure 포털](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="dd20f-161">**만들기**를 클릭 하면 다음을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="dd20f-162">이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="dd20f-163">**응용 프로그램 유형**으로 **일반**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="dd20f-164">적절 한 **구독**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="dd20f-165">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="dd20f-166">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="dd20f-167">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="dd20f-168">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.</span><span class="sxs-lookup"><span data-stu-id="dd20f-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="dd20f-169">**위치**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="dd20f-170">또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="dd20f-171">**만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-171">Select **Create**.</span></span>

        ![Azure 포털](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="dd20f-173">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="dd20f-174">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure 포털](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="dd20f-176">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Azure 포털](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="dd20f-178">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="dd20f-179">새 *Application Insights 서비스* 인스턴스로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Azure 포털](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="dd20f-181">이 웹 페이지를 열어 쉽게 액세스할 수 있게 되 면 수집 된 데이터를 확인 하기 위해 여기로 다시 돌아옵니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="dd20f-182">Application Insights를 구현 하려면 세 가지 특정 값 (3)을 사용 해야 합니다. **계측 키**, **응용 프로그램 ID**및 **API 키**를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="dd20f-183">아래에는 서비스에서 이러한 값을 검색 하는 방법이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="dd20f-184">이 값은 코드에서 곧 사용 되므로 빈 *메모장* 페이지에서이 값을 기록해 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="dd20f-185">**계측 키**를 찾으려면 서비스 함수 목록을 아래로 스크롤하고 **속성**을 클릭 해야 합니다. 그러면 표시 되는 탭에 **서비스 키**가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Azure 포털](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="dd20f-187">약간의 **속성**을 사용 하 여 **API 액세스**를 찾을 수 있습니다 .이를 클릭 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="dd20f-188">오른쪽 패널에는 앱의 **응용 프로그램 ID** 가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Azure 포털](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="dd20f-190">**응용 프로그램 ID** 패널이 열려 있는 상태에서 **api 키 만들기**를 클릭 하면 *api 키 만들기* 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Azure 포털](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="dd20f-192">이제 open *API Key 만들기* 패널에서 설명을 입력 하 고 **세 상자에 틱**을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="dd20f-193">**키 생성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-193">Click **Generate Key**.</span></span> <span data-ttu-id="dd20f-194">**API 키** 가 생성 되 고 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-194">Your **API Key** will be created and displayed.</span></span> 

    ![Azure 포털](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="dd20f-196">**서비스 키** 가 표시 되는 유일한 시간 이므로 지금 복사본을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="dd20f-197">2 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="dd20f-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="dd20f-198">다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="dd20f-199">*Unity* 를 열고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-199">Open *Unity* and click **New**.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="dd20f-201">이제 Unity 프로젝트 이름을 제공 하 고 **MR\_Azure\_application\_Insights**를 삽입 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="dd20f-202">*템플릿이* **3d**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="dd20f-203">위치를 적절 한 *위치* 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="dd20f-204">그런 다음 **프로젝트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-204">Then, click **Create project**.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="dd20f-206">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="dd20f-207">**기본 설정 편집 \>**  으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="dd20f-208">**외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="dd20f-209">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-209">Close the **Preferences** window.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="dd20f-211">그런 다음 **파일 \> 빌드 설정** 으로 이동 하 고 플랫폼 **전환** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼**로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="dd20f-213">**파일\> 빌드 설정** 으로 이동 하 여 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="dd20f-214">**대상 장치가** **모든 장치로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="dd20f-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="dd20f-215">Microsoft HoloLens의 경우 **대상 장치** 를 *HoloLens*로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="dd20f-216">**빌드 형식이** **D3D** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="dd20f-217">**SDK** 가 **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="dd20f-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="dd20f-218">**빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="dd20f-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="dd20f-219">장면을 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="dd20f-220">이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="dd20f-221">저장 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-221">A save window will appear.</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="dd20f-223">이에 대 한 새 폴더 및 향후 장면을 만든 다음 **새** 폴더 단추를 클릭 하 여 새 폴더를 만들고 이름을 **장면의**로 지정한 다음</span><span class="sxs-lookup"><span data-stu-id="dd20f-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="dd20f-225">새로 만든 **장면** 폴더를 연 다음 *파일 이름:* 텍스트 필드에 **ApplicationInsightsScene**를 입력 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="dd20f-227">**빌드 설정**의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="dd20f-228">**빌드 설정** 창에서 **플레이어 설정** 단추를 클릭 하면 **검사기** 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="dd20f-230">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="dd20f-231">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="dd20f-232">**스크립팅** **런타임 버전** 은 **실험적 (.Net 4.6와 동일)** 이어야 하며,이 경우 편집기를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="dd20f-233">**Scripting 백엔드** 는 **.net** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="dd20f-234">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="dd20f-236">**게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="dd20f-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="dd20f-237">**InternetClient**</span></span>     

            ![Unity 프로젝트 설정](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="dd20f-239">패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="dd20f-241">**빌드 설정**으로 돌아가서 **Unity C# 프로젝트가** 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="dd20f-242">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="dd20f-243">장면 및 프로젝트를 저장 합니다 (**파일** > **저장 장면/파일** > **저장 프로젝트**).</span><span class="sxs-lookup"><span data-stu-id="dd20f-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="dd20f-244">3 장-Unity 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="dd20f-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dd20f-245">이 과정의 *Unity* 구성 요소를 건너뛰고 바로 코드를 계속 진행 하려는 경우이 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)를 무료로 다운로드 하 여 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="dd20f-246">여기에는 다음 챕터의 Dll도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="dd20f-247">가져온 후 [**6 장**](#chapter-6---create-the-applicationinsightstracker-class)에서 계속 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dd20f-248">Unity 내에서 Application Insights를 사용 하려면 Newtonsoft.json DLL과 함께 해당 DLL을 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="dd20f-249">현재 Unity에는 가져온 후 플러그 인을 다시 구성 해야 하는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="dd20f-250">이러한 단계 (이 섹션에서는 4-7)는 버그가 해결 된 후 더 이상 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="dd20f-251">사용자 고유의 프로젝트로 Application Insights를 가져오려면 플러그 인을 포함 하는 ['. unitypackage '를 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="dd20f-252">그런 후에 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-252">Then, do the following:</span></span>

1.  <span data-ttu-id="dd20f-253">**자산 가져오기\> 패키지\> 사용자 지정 패키지** 메뉴 옵션을 사용 하 여 unitypackage을 Unity에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="dd20f-254">표시 되는 **Unity 패키지 가져오기** 상자에서 **플러그 인** 을 포함 하 여 모든 항목을 선택 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="dd20f-256">**가져오기** 단추를 클릭 하 여 프로젝트에 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="dd20f-257">프로젝트 뷰에서 **플러그 인** 아래의 **Insights** 폴더로 이동 하 고 다음 플러그 인 *만*선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="dd20f-258">Microsoft ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="dd20f-258">Microsoft.ApplicationInsights</span></span>

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="dd20f-260">이 *플러그 인* 을 선택한 상태에서 **모든 플랫폼이** 선택 **취소**되어 있는지 확인 한 **다음 WSAPlayer** 도 **선택 취소**되어 있는지 확인 하 고 **적용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="dd20f-261">이 작업을 수행 하는 것은 파일이 올바르게 구성 되어 있는지 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="dd20f-263">이와 같이 플러그 인을 표시 하면 Unity 편집기 에서만 사용 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="dd20f-264">WSA 폴더에는 프로젝트를 Unity에서 내보낸 후에 사용 되는 다른 Dll 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="dd20f-265">다음으로, **Insights** 폴더 내에서 **WSA** 폴더를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="dd20f-266">방금 구성한 파일의 복사본이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="dd20f-267">이 파일을 선택 하 고 검사기에서 **모든 플랫폼이** 선택 **취소**되어 있는지 확인 한 다음 **WSAPlayer** **만** **선택**되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="dd20f-268">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-268">Click **Apply**.</span></span>

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="dd20f-270">이제 *newtonsoft.json* 플러그 인에 대 한 **4-6 단계**를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="dd20f-271">결과는 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="dd20f-273">4 장-카메라 및 사용자 정의 컨트롤 설정</span><span class="sxs-lookup"><span data-stu-id="dd20f-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="dd20f-274">이 장에서는 카메라와 컨트롤을 설정 하 여 사용자가 장면을 보고 이동할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="dd20f-275">계층 패널에서 빈 영역을 마우스 오른쪽 단추로 클릭 한 다음**빈**영역 **만들기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="dd20f-277">새 빈 GameObject을 **카메라 부모로**바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="dd20f-279">계층 패널에서 빈 영역을 마우스 오른쪽 단추로 클릭 한 다음 **3D 개체**에서 **구**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="dd20f-280">구의 이름을 **오른쪽**으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="dd20f-281">오른쪽의 **변환 소수 자릿수** 를 **0.1, 0.1, 0.1** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="dd20f-283">*구 collider* 구성 요소에서 **기어** 를 클릭 하 고 **구성 요소 제거**를 클릭 하 여 오른쪽에서 **구 collider** 구성 요소를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="dd20f-285">계층 패널에서 **기본 카메라** 와 **오른쪽** 개체를 **카메라 부모** 개체로 끌어 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="dd20f-287">**주 카메라** 와 **오른쪽** 개체의 **변환 위치** 를 모두 **0, 0, 0**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-31.png)

    ![카메라 및 사용자 컨트롤 설정](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="dd20f-290">5 장-Unity 장면에서 개체 설정</span><span class="sxs-lookup"><span data-stu-id="dd20f-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="dd20f-291">이제 사용자가 상호 작용할 수 있는 장면에 몇 가지 기본 셰이프를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="dd20f-292">*계층 패널*에서 빈 영역을 마우스 오른쪽 단추로 클릭 한 다음 **3D 개체**에서 **평면**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="dd20f-293">평면 **변환 위치** 를 **0,-1, 0**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="dd20f-294">평면 **변환 눈금** 을 **5, 1, 5**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="dd20f-296">다른 셰이프를 더 쉽게 볼 수 있도록 **평면** 개체에 사용할 기본 자료를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="dd20f-297">*프로젝트 패널로*이동 하 고,를 마우스 오른쪽 단추로 클릭 한 다음 **만들기**를클릭 하 여 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="dd20f-298">이름을 **재질**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-298">Name it **Materials**.</span></span>

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-34.png) ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="dd20f-301">**재질** 폴더를 연 다음 마우스 오른쪽 단추를 클릭 하 고 **만들기**를 클릭 한 다음 **재질**을 클릭 하 여 새 자료를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="dd20f-302">이름을 **Blue**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-302">Name it **Blue**.</span></span>

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-36.png) ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="dd20f-305">새 **파랑** 자료를 선택한 상태에서 *검사기*를 확인 하 고 **albedo**와 함께 사각형 창을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="dd20f-306">파란색을 선택 합니다 (아래 **그림은 16 진수 색: \#3592FFFF**).</span><span class="sxs-lookup"><span data-stu-id="dd20f-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="dd20f-307">선택한 후 닫기 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-307">Click the close button once you have chosen.</span></span>

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="dd20f-309">새 자료를 **재질** 폴더에서 새로 만든 **평면**으로 장면 내에 끌어 놓거나 *계층*내의 **평면** 개체에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="dd20f-311">*계층 패널*에서 빈 영역을 마우스 오른쪽 단추로 클릭 한 다음 **3D 개체, 캡슐을**차례로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="dd20f-312">**캡슐** 을 선택 하 고 **변환** *위치* 를 **-10, 1, 0**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="dd20f-313">*계층 패널*에서 빈 영역을 마우스 오른쪽 단추로 클릭 한 다음 **3D 개체, 큐브**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="dd20f-314">**큐브** 를 선택한 상태에서 해당 **변환** *위치* 를 다음과 같이 변경 합니다. **0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="dd20f-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="dd20f-315">*계층 패널*에서 빈 영역을 마우스 오른쪽 단추로 클릭 한 다음 **3D 개체, 구를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="dd20f-316">**구가** 선택 된 상태에서 해당 **변환** *위치* 를 다음과 같이 변경 합니다. **10, 0, 0**입니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="dd20f-318">이러한 *위치* 값은 *제안*입니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="dd20f-319">개체의 위치를 원하는 대로 설정할 수 있지만, 개체 거리가 카메라에서 멀리 떨어져 있지 않으면 응용 프로그램 사용자가 더 쉽게 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="dd20f-320">응용 프로그램을 실행 하는 경우 장면 내에서 개체를 식별할 수 있어야 합니다 .이를 위해서는 태그를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="dd20f-321">개체 중 하나를 선택 하 고 *검사기* 패널에서 **태그 추가**...를 클릭 합니다. 그러면 *검사기* 가 **& 레이어** 패널의 태그로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="dd20f-322">![Unity 장면](images/AzureLabs-Lab309-41.png) 에서 개체 설정![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="dd20f-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="dd20f-323">**+ (더하기)** 기호를 클릭 한 다음 태그 이름을 **objectinscene**으로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Unity 장면에서 개체 설정](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="dd20f-325">태그에 다른 이름을 사용 하는 경우에는 나중에이 변경 내용이 *DataFromAnalytics*, *Objecttrigger*및 *응시*로 설정 되었는지 확인 하 여 장면 내에서 개체가 검색 되 고 검색 되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="dd20f-326">태그를 만든 후에는 세 개체 모두에 적용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="dd20f-327">*계층*에서 **shift** 키를 누른 상태에서 **캡슐**, **큐브**및 **구**개체를 클릭 한 다음 *검사기*에서 **태그**옆에 있는 드롭다운 메뉴를 클릭 하 고 *objectinscene* 클릭 합니다. 만든 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="dd20f-328">![Unity 장면](images/AzureLabs-Lab309-44.png) 에서 개체 설정![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="dd20f-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="dd20f-329">6 장-ApplicationInsightsTracker 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="dd20f-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="dd20f-330">만들어야 하는 첫 번째 스크립트는 다음을 담당 하는 **ApplicationInsightsTracker**입니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="dd20f-331">Azure 애플리케이션 Insights에 제출할 사용자 상호 작용을 기반으로 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="dd20f-332">사용자 상호 작용에 따라 적절 한 이벤트 이름을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="dd20f-333">Application Insights 서비스 인스턴스에 이벤트를 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="dd20f-334">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="dd20f-334">To create this class:</span></span>

1.  <span data-ttu-id="dd20f-335">*프로젝트 패널*을 마우스 오른쪽 단추로 클릭 한 다음**폴더** **만들기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="dd20f-336">폴더 이름을 **스크립트**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-336">Name the folder **Scripts**.</span></span>

    ![ApplicationInsightsTracker 클래스 만들기](images/AzureLabs-Lab309-46.png)  ![ApplicationInsightsTracker 클래스 만들기](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="dd20f-339">**Scripts** 폴더를 만든 다음 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="dd20f-340">그런 다음 해당 폴더 내에서 **C# 스크립트** **만들기**  >  를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="dd20f-341">스크립트 이름을 **ApplicationInsightsTracker**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="dd20f-342">새 **ApplicationInsightsTracker** 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="dd20f-343">아래와 같이 스크립트의 맨 위에서 네임 스페이스를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="dd20f-344">클래스 내에서 다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-344">Inside the class insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > <span data-ttu-id="dd20f-345">[1 장](#chapter-1---the-azure-portal), 9 단계부터 설명 된 대로 Azure Portal의 *서비스 키* 를 사용 하 여 **instrumentationKey, applicationId 및 API_Key** 값을 적절 하 게 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="dd20f-346">그런 다음 클래스를 초기화할 때 호출 되는 **Start ()** 및 **활성 ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  <span data-ttu-id="dd20f-347">응용 프로그램에서 등록 한 이벤트 및 메트릭을 전송 하는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  <span data-ttu-id="dd20f-348">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="dd20f-349">7 장-응시 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="dd20f-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="dd20f-350">만들 다음 스크립트는 **응시** 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="dd20f-351">이 스크립트는 사용자가 보고 있는 개체를 검색 하기 위해 *기본 카메라*에서 앞으로 프로젝션 될 *raycast* 를 만드는 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="dd20f-352">이 경우 *Raycast* 는 사용자가 **objectinscene** 태그를 사용 하 여 개체를 확인 한 다음 사용자가 해당 개체에서 *gazes* 하는 기간을 계산 해야 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="dd20f-353">**Scripts** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="dd20f-354">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="dd20f-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="dd20f-355">스크립트 이름을 **응시**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="dd20f-356">스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="dd20f-357">기존 코드를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-357">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  <span data-ttu-id="dd20f-358">이제 해제 **()** 및 **Start ()** 메서드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  <span data-ttu-id="dd20f-359">**응시** 클래스 내에서 **Update ()** 메서드에 다음 코드를 추가 하 여 *raycast* 를 프로젝션 하 고 대상 적중을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  <span data-ttu-id="dd20f-360">**ResetFocusedObject ()** 메서드를 추가 하 여 사용자가 개체를 보았을 때 **Application Insights** 에 데이터를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  <span data-ttu-id="dd20f-361">이제 **응시** 스크립트가 완료 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="dd20f-362">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="dd20f-363">8 장-ObjectTrigger 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="dd20f-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="dd20f-364">만들어야 하는 다음 스크립트는 다음을 담당 하는 **Objecttrigger**입니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="dd20f-365">주 카메라와의 충돌에 필요한 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="dd20f-366">카메라가 **Objectinscene**태그가 지정 된 개체 근처에 있는지 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="dd20f-367">스크립트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-367">To create the script:</span></span>

1.  <span data-ttu-id="dd20f-368">**Scripts** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="dd20f-369">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="dd20f-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="dd20f-370">스크립트 **Objecttrigger**의 이름을로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="dd20f-371">스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="dd20f-372">기존 코드를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-372">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  <span data-ttu-id="dd20f-373">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="dd20f-374">9 장-DataFromAnalytics 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="dd20f-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="dd20f-375">이제 다음 작업을 담당 하는 **DataFromAnalytics** 스크립트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="dd20f-376">가장 많은 카메라에 도달 하는 개체에 대 한 분석 데이터를 인출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="dd20f-377">Azure 애플리케이션 Insights 서비스 인스턴스와 통신할 수 있도록 하는 *서비스 키*사용</span><span class="sxs-lookup"><span data-stu-id="dd20f-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="dd20f-378">가장 높은 이벤트 수가 있는 장면에서 개체 정렬</span><span class="sxs-lookup"><span data-stu-id="dd20f-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="dd20f-379">가장 많이 접근 하는 개체의 재질 색을 *녹색*으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="dd20f-380">스크립트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-380">To create the script:</span></span>

1.  <span data-ttu-id="dd20f-381">**Scripts** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="dd20f-382">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="dd20f-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="dd20f-383">스크립트 이름을 **DataFromAnalytics**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="dd20f-384">스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="dd20f-385">다음 네임 스페이스를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="dd20f-386">스크립트 내에서 다음을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-386">Inside the script, insert the following:</span></span>

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  <span data-ttu-id="dd20f-387">**DataFromAnalytics** 클래스 내에서 **Start ()** 메서드 바로 다음에 **fetchanalytics ()** 라는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="dd20f-388">이 메서드는 *GameObject* 및 자리 표시자 이벤트 수 번호를 사용 하 여 키 값 쌍의 목록을 채우는 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="dd20f-389">그런 다음 **Getwebrequest ()** 코 루틴를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="dd20f-390">*Application Insights* 에 대 한 호출의 쿼리 구조는이 메서드 내에서 *쿼리 URL* 끝점으로도 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  <span data-ttu-id="dd20f-391">**Fetchanalytics (** ) 메서드 바로 아래에 *IEnumerator*를 반환 하는 **getwebrequest ()** 라는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="dd20f-392">이 메서드는 *Application Insights*내에서 특정 *GameObject*에 해당 하는 이벤트가 호출 된 횟수를 요청 하는 일을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="dd20f-393">전송 된 모든 쿼리가 반환 되 면 **DetermineWinner ()** 메서드가 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="dd20f-394">다음 메서드는 가장 높은 이벤트 개수에 따라 *GameObject* 및 *Int* 쌍 목록을 정렬 하는 **DetermineWinner ()** 입니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="dd20f-395">그런 다음 해당 *GameObject* 의 재질 색을 *녹색* 으로 변경 합니다 (가장 높은 수가 있는 피드백으로).</span><span class="sxs-lookup"><span data-stu-id="dd20f-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="dd20f-396">그러면 분석 결과가 포함 된 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-396">This displays a message with the analytics results.</span></span>

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  <span data-ttu-id="dd20f-397">*Application Insights*에서 받은 JSON 개체를 deserialize 하는 데 사용 되는 클래스 구조를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="dd20f-398">클래스 정의 **외부** 에서 **DataFromAnalytics** 클래스 파일의 맨 아래에 이러한 클래스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. <span data-ttu-id="dd20f-399">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="dd20f-400">10 장-이동 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="dd20f-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="dd20f-401">**이동** 스크립트는 생성 해야 하는 다음 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="dd20f-402">이 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-402">It is responsible for:</span></span>

- <span data-ttu-id="dd20f-403">카메라가 보이는 방향에 따라 기본 카메라를 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="dd20f-404">장면 개체에 다른 모든 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="dd20f-405">스크립트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-405">To create the script:</span></span>

1.  <span data-ttu-id="dd20f-406">**Scripts** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="dd20f-407">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="dd20f-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="dd20f-408">스크립트 **이동**의 이름을로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="dd20f-409">스크립트를 두 번 클릭 하 여 *Visual Studio*에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="dd20f-410">기존 코드를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-410">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  <span data-ttu-id="dd20f-411">Move 클래스 **의** empty **Update ()** 메서드 *아래* 에서 사용자가 손 컨트롤러를 사용 하 여 가상 공간을 이동할 수 있도록 하는 다음 메서드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  <span data-ttu-id="dd20f-412">마지막으로 **Update ()** 메서드 내에 메서드 호출을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="dd20f-413">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="dd20f-414">11 장-스크립트 참조 설정</span><span class="sxs-lookup"><span data-stu-id="dd20f-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="dd20f-415">이 장에서는 **이동** 스크립트를 **카메라 부모** 에 추가 하 고 해당 참조 대상을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="dd20f-416">그런 다음이 스크립트는 필요한 위치에 다른 스크립트를 배치 하는 것을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="dd20f-417">*프로젝트 패널*의 **Scripts** 폴더에서 **이동** 스크립트를 *계층 패널*에 있는 **카메라 부모** 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Unity 장면에서 스크립트 참조 설정](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="dd20f-419">**카메라 부모**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="dd20f-420">*계층 패널*의 **오른쪽** 개체를 *계층 패널* 에서 *검사기 패널*의 참조 대상 **컨트롤러**로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="dd20f-421">아래 이미지에 표시 된 것 처럼 **사용자 속도** 를 **5**로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Unity 장면에서 스크립트 참조 설정](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="dd20f-423">12 장-Unity 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="dd20f-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="dd20f-424">이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었으므로 Unity에서 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="dd20f-425">**빌드 설정**으로 이동 합니다 (**파일** > **빌드 설정**).</span><span class="sxs-lookup"><span data-stu-id="dd20f-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="dd20f-426">**빌드 설정** 창에서 **빌드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-426">From the **Build Settings** window, click **Build**.</span></span>

    ![UWP 솔루션에 Unity 프로젝트 빌드](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="dd20f-428">빌드 위치를 묻는 메시지를 표시 하는 **파일 탐색기** 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="dd20f-429">왼쪽 위 모서리에서 **새 폴더** 를 클릭 하 여 새 폴더를 만들고 이름을 **작성**합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![UWP 솔루션에 Unity 프로젝트 빌드](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="dd20f-431">새 **빌드** 폴더를 열고 **새 폴더** 를 한 번 더 사용 하 여 다른 폴더를 만든 다음 **MR\_Azure\_application\_Insights**로 이름을로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![UWP 솔루션에 Unity 프로젝트 빌드](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="dd20f-433">**MR\_Azure\_applicationInsights\_** 폴더를 선택 하 고 **폴더 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="dd20f-434">프로젝트를 빌드하는 데 1 분 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="dd20f-435">*빌드*다음에는 새 프로젝트의 위치를 보여 주는 **파일 탐색기** 가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a><span data-ttu-id="dd20f-436">13 장-컴퓨터에 MR_Azure_Application_Insights 앱 배포</span><span class="sxs-lookup"><span data-stu-id="dd20f-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="dd20f-437">로컬 컴퓨터에 **MR\_Azure\_application\_Insights** 앱을 배포 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="dd20f-438">**Visual Studio**에서 **MR\_\_Azure application\_Insights** 앱의 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="dd20f-439">**솔루션 플랫폼**에서 **X86, 로컬 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="dd20f-440">**솔루션 구성** 에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![UWP 솔루션에 Unity 프로젝트 빌드](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="dd20f-442">**빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 컴퓨터에 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="dd20f-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="dd20f-443">이제 앱이 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="dd20f-444">Mixed reality 응용 프로그램을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="dd20f-445">*Azure 정보 서비스* 에서 충분 한 이벤트 데이터를 수집 했을 때 장면에서 이동 하 여 개체에 대 한 정보를 파악 하 고이를 확인 하는 것은 가장 적합 한 개체를 녹색으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="dd20f-446">서비스에서 수집 되는 *이벤트 및 메트릭의* 평균 대기 시간은 약 15 분을 차지 하지만, 경우에 따라 최대 1 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="dd20f-447">14 장-Application Insights 서비스 포털</span><span class="sxs-lookup"><span data-stu-id="dd20f-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="dd20f-448">장면 주위에 로밍 하 고 여러 개체에서 gazed *Application Insights 서비스* 포털에서 수집 된 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="dd20f-449">Application Insights 서비스 포털로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="dd20f-450">*메트릭 탐색기*를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-450">Click on *Metrics Explorer*.</span></span>

    ![수집 된 데이터 보기](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="dd20f-452">응용 프로그램과 관련 된 *이벤트 및 메트릭을* 나타내는 그래프가 포함 된 탭에서 열립니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="dd20f-453">위에서 설명한 것 처럼 그래프에 데이터를 표시 하는 데 약간의 시간이 걸릴 수 있습니다 (최대 1 시간).</span><span class="sxs-lookup"><span data-stu-id="dd20f-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![수집 된 데이터 보기](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="dd20f-455">응용 프로그램 버전별 *총 이벤트* 수에서 *이벤트 막대* 를 클릭 하 여 해당 이름의 이벤트에 대 한 자세한 분석을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![수집 된 데이터 보기](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="dd20f-457">Application Insights 서비스 응용 프로그램을 완료 했습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="dd20f-458">축 하 합니다. Application Insights 서비스를 활용 하 여 앱 내에서 사용자의 활동을 모니터링 하는 혼합 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![과정 결과](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="dd20f-460">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="dd20f-460">Bonus Exercises</span></span>

<span data-ttu-id="dd20f-461">**연습 1**</span><span class="sxs-lookup"><span data-stu-id="dd20f-461">**Exercise 1**</span></span>

<span data-ttu-id="dd20f-462">수동으로 생성 하는 대신 ObjectInScene 개체를 생성 하 고 스크립트 내에서 평면에 해당 좌표를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="dd20f-463">이러한 방식으로 Azure에서 가장 인기 있는 개체 (즉, 응시 또는 근접 결과)를 확인 하 고 이러한 개체 *중 하나를* 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="dd20f-464">**연습 2**</span><span class="sxs-lookup"><span data-stu-id="dd20f-464">**Exercise 2**</span></span>

<span data-ttu-id="dd20f-465">Application Insights 결과를 시간별로 정렬 하 여 가장 관련성이 높은 데이터를 가져오고 응용 프로그램에서 해당 시간이 중요 한 데이터를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="dd20f-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

