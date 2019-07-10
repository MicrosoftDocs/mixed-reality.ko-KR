---
title: MR 및 Azure 309-Application insights
description: Azure Application Insights 서비스를 사용 하 여, 혼합된 현실 응용 프로그램 내의 사용자 동작에 대 한 분석을 수집 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, application insights, hololens, 몰입 형, vr
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694566"
---
>[!NOTE]
><span data-ttu-id="e5ca0-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="e5ca0-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="e5ca0-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="e5ca0-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="e5ca0-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="e5ca0-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="e5ca0-110">MR 및 Azure 309: Application insights</span><span class="sxs-lookup"><span data-stu-id="e5ca0-110">MR and Azure 309: Application insights</span></span>

![최종 제품-시작](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="e5ca0-112">이 과정에서는 배웁니다 혼합된 현실 응용 프로그램에 Application Insights 기능을 추가 하는 방법을 사용자 동작에 대 한 분석을 수집 하는 Azure Application Insights API를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="e5ca0-113">Application Insights는 Microsoft 서비스 개발자가 자신의 응용 프로그램에서 분석을 수집 하 고는 사용 하기 쉬운 포털에서 관리할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="e5ca0-114">분석은 사용자 지정 정보를 수집 하려는 성능에 이르기까지 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="e5ca0-115">자세한 내용은 참조는 [Application Insights 페이지](https://azure.microsoft.com/services/application-insights/)합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="e5ca0-116">이 과정을 마치면 다음을 수행 하는 일을 할 수 있는 혼합된 현실 몰입 형 헤드셋 응용 프로그램을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="e5ca0-117">사용자가 gaze 장면 이동를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="e5ca0-118">분석 보내기를 트리거하려면 합니다 *Application Insights 서비스*, 응시 및 근접 장면에 개체를 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="e5ca0-119">앱은 서비스, 사용자가 가장 최근 24 시간 이내에 접근 된 개체에 대 한 정보를 가져오는 중에 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="e5ca0-120">해당 개체에는 녹색으로 색이 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-120">That object will change its color to green.</span></span>

<span data-ttu-id="e5ca0-121">이 코스 샘플 Unity 기반 응용 프로그램에 Application Insights 서비스에서 결과 가져오는 방법을 배우게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="e5ca0-122">사용자 지정 응용 프로그램을 작성 하려는 경우에 이러한 개념을 적용 하는 것이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="e5ca0-123">장치 지원</span><span class="sxs-lookup"><span data-stu-id="e5ca0-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e5ca0-124">과정</span><span class="sxs-lookup"><span data-stu-id="e5ca0-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="e5ca0-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e5ca0-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e5ca0-126"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="e5ca0-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="e5ca0-127">MR 및 Azure 309: Application insights</span><span class="sxs-lookup"><span data-stu-id="e5ca0-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="e5ca0-128">✔️</span><span class="sxs-lookup"><span data-stu-id="e5ca0-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e5ca0-129">✔️</span><span class="sxs-lookup"><span data-stu-id="e5ca0-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="e5ca0-130">이 코스는 주로 Windows Mixed Reality 몰입 형 (VR) 헤드셋 주력, Microsoft HoloLens이 과정에서 배운 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="e5ca0-131">과정을 따라가려면 정보 HoloLens를 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="e5ca0-132">HoloLens를 사용 하는 경우 음성 캡처하는 동안 일부 echo를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e5ca0-133">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e5ca0-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="e5ca0-134">이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="e5ca0-135">또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 7 월) 작성 시점에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="e5ca0-136">내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 나열 된 것 보다 최신 소프트웨어에 맞게 보면 일치 완벽 하 게 됩니다 있지만 문서 아래.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="e5ca0-137">다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="e5ca0-138">개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용</span><span class="sxs-lookup"><span data-stu-id="e5ca0-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="e5ca0-139">Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="e5ca0-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="e5ca0-140">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="e5ca0-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="e5ca0-141">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="e5ca0-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="e5ca0-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="e5ca0-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="e5ca0-143">A [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md) 하거나 [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여</span><span class="sxs-lookup"><span data-stu-id="e5ca0-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="e5ca0-144">(없으면 헤드셋 내장 마이크와 스피커) 내장 마이크를 사용 하 여 헤드폰 집합</span><span class="sxs-lookup"><span data-stu-id="e5ca0-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="e5ca0-145">Azure 설정 및 Application Insights 데이터 검색에 대 한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="e5ca0-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="e5ca0-146">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="e5ca0-146">Before you start</span></span>

<span data-ttu-id="e5ca0-147">이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).</span><span class="sxs-lookup"><span data-stu-id="e5ca0-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="e5ca0-148">데이터 인식 될 *Application Insights* 시간이 많이 걸리며, 따라서 기다려주십시오.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="e5ca0-149">서비스가 데이터를 수신한 경우 확인 하려는 경우 체크 아웃 [14 장](#chapter-14---the-application-insights-service-portal), 포털을 탐색 하는 방법을 보여는입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="e5ca0-150">1 장-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="e5ca0-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="e5ca0-151">사용 하도록 *Application Insights*를 만들고 구성 해야 합니다는 *Application Insights 서비스* Azure portal에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="e5ca0-152">에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="e5ca0-153">Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="e5ca0-154">클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="e5ca0-155">일단 로그인 하면 클릭할 **새로 만들기** 왼쪽 위에서 모서리 및 검색 *Application Insights*를 클릭 하 고 **Enter**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e5ca0-156">단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="e5ca0-158">오른쪽에 새 페이지에 대 한 설명을 제공 합니다는 *Azure Application Insights* 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="e5ca0-159">선택이 페이지의 왼쪽 아래에 있는 합니다 **만들기** 이 연결 서비스를 만들려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="e5ca0-161">클릭 한 후 **만들기**:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="e5ca0-162">원하는 삽입 **이름을** 이 서비스 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="e5ca0-163">로 **응용 프로그램 종류**를 선택 **일반**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="e5ca0-164">적절 한 선택 **구독**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="e5ca0-165">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="e5ca0-166">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="e5ca0-167">좋습니다 일반적인 리소스 그룹에서 (예: 이러한 교육 과정) 예: 단일 프로젝트와 연결 된 Azure 서비스를 모두 유지).</span><span class="sxs-lookup"><span data-stu-id="e5ca0-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="e5ca0-168">추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="e5ca0-169">선택 된 **위치**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="e5ca0-170">이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="e5ca0-171">**만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-171">Select **Create**.</span></span>

        ![Azure Portal](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="e5ca0-173">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="e5ca0-174">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="e5ca0-176">새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="e5ca0-178">클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="e5ca0-179">이동에서 새 *Application Insights 서비스* 인스턴스.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="e5ca0-181">이 웹 페이지를 열어 쉽게 액세스 하 여, 있습니다를 여기로 돌아와 수집 된 데이터를 참조 하는 빈도.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="e5ca0-182">Application Insights를 구현 하려면 세 가지 (3) 특정 값을 사용 해야 합니다. **계측 키**하십시오 **응용 프로그램 ID**, 및 **API 키**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="e5ca0-183">다음 서비스에서 이러한 값을 검색 하는 방법을 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="e5ca0-184">빈 값에서 이러한 값을 기록해 *메모장* 코드에서 곧 사용할 것 이므로 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="e5ca0-185">찾을 수를 **계측 키**, 서비스 함수 목록 아래로 스크롤하여 클릭 해야 합니다 **속성**를 탭이 표시 되어 표시 됩니다는 **서비스 키**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="e5ca0-187">다음 잠시 **속성**를 찾을 수 있습니다 **API 액세스**를 클릭 해야 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="e5ca0-188">오른쪽 패널을 제공 합니다 **응용 프로그램 ID** 앱의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="e5ca0-190">사용 하 여는 **응용 프로그램 ID** 패널 아직 열려 클릭 **API 키 만들기**를 엽니다 합니다 *API 키 만들기* 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="e5ca0-192">이제 오픈 내 *API 키 만들기* 패널에서 설명을 입력 하 고 **3 개의 상자 눈금**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="e5ca0-193">클릭 **키 생성**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-193">Click **Generate Key**.</span></span> <span data-ttu-id="e5ca0-194">프로그램 **API 키** 생성 되어 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-194">Your **API Key** will be created and displayed.</span></span> 

    ![Azure Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="e5ca0-196">이 유일한 경우에 **서비스 키** 있도록 표시 합니다. 이제 복사본을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="e5ca0-197">2 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="e5ca0-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="e5ca0-198">다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="e5ca0-199">오픈 *Unity* 누릅니다 **새로 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-199">Open *Unity* and click **New**.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="e5ca0-201">Unity 프로젝트 이름을 제공 해야 이제 삽입 **MR\_Azure\_응용 프로그램\_Insights**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="e5ca0-202">있는지 확인 합니다 *템플릿을* 로 설정 된 **3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="e5ca0-203">설정 된 *위치* 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다).</span><span class="sxs-lookup"><span data-stu-id="e5ca0-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="e5ca0-204">그런 다음 클릭 **프로젝트 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-204">Then, click **Create project**.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="e5ca0-206">Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="e5ca0-207">로 이동 **편집할 \> 기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="e5ca0-208">변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="e5ca0-209">닫기 합니다 **기본 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-209">Close the **Preferences** window.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="e5ca0-211">이동한 다음 **파일 \> 빌드 설정** 전환 하는 플랫폼 **유니버설 Windows 플랫폼**를 클릭 하 여를 **플랫폼 전환** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="e5ca0-213">로 이동 **파일 \> 빌드 설정** 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="e5ca0-214">**장치를 대상** 로 설정 된 **모든 장치**</span><span class="sxs-lookup"><span data-stu-id="e5ca0-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="e5ca0-215">Microsoft HoloLens 설정 **대상 장치** 하 *HoloLens*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="e5ca0-216">**빌드 형식** 로 설정 된 **D3D**</span><span class="sxs-lookup"><span data-stu-id="e5ca0-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="e5ca0-217">**SDK** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="e5ca0-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="e5ca0-218">**빌드 및 실행** 로 설정 된 **로컬 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="e5ca0-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="e5ca0-219">장면 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="e5ca0-220">선택 하 여이 작업을 수행할 **열고 장면 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="e5ca0-221">창 저장 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-221">A save window will appear.</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="e5ca0-223">및 모든 향후 장면에 대 한 새 폴더를 만들려면 클릭 합니다 **새 폴더** 단추를 새 폴더를 만들고 이름을 **장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="e5ca0-225">새로 만든 열 **장면** 폴더를 선택한 다음는 *파일 이름:* 텍스트 필드에 입력 **ApplicationInsightsScene**, 클릭 **저장**.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="e5ca0-227">설정에 남아 **빌드 설정**, 지금은 기본값으로 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="e5ca0-228">에 **빌드 설정** 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 **검사기** 위치한.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="e5ca0-230">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="e5ca0-231">에 **기타 설정** 탭:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="e5ca0-232">**스크립팅** **런타임 버전** 해야 **실험적 (.NET 4.6 동등)** , 편집기를 다시 시작 해야 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="e5ca0-233">**백 엔드를 스크립팅** 있어야 **.NET**</span><span class="sxs-lookup"><span data-stu-id="e5ca0-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="e5ca0-234">**API 호환성 수준** 있어야 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="e5ca0-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="e5ca0-236">내 합니다 **게시 설정** 탭의 **기능**, 확인:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="e5ca0-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="e5ca0-237">**InternetClient**</span></span>     

            ![Unity 프로젝트 설정](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="e5ca0-239">패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK** 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="e5ca0-241">년대 **빌드 설정**를 **Unity C# 프로젝트** 가 더 이상 회색;이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="e5ca0-242">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="e5ca0-243">장면 및 프로젝트 저장 (**파일** > **장면 저장 파일** > **프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="e5ca0-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="e5ca0-244">3 장-Unity 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="e5ca0-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5ca0-245">건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드로 바로 계속, 다운로드 자유롭게 [309.unitypackage-MR-Azure](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage),으로 프로젝트로 가져올를 [ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="e5ca0-246">다음 장에서에서 Dll도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="e5ca0-247">가져온 후 계속 진행 [ **6 장**](#chapter-6---create-the-applicationinsightstracker-class)합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5ca0-248">Unity 내에서 Application Insights를 사용 하려면 Newtonsoft DLL과 함께,에 대 한 DLL 가져오기 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="e5ca0-249">플러그 인 가져오기 후 다시 구성 해야 하는 Unity의 알려진된 문제는 현재 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="e5ca0-250">이러한 단계 (4-7이 단원의) 버그가 해결 된 후 필요한 더 이상.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="e5ca0-251">사용자 고유의 프로젝트에 Application Insights를 가져오려면 했는지 확인 [는 '.unitypackage', 플러그 인 포함 된 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="e5ca0-252">그런 다음 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-252">Then, do the following:</span></span>

1.  <span data-ttu-id="e5ca0-253">추가 합니다 **.unitypackage** 사용 하 여 Unity에는 **자산 \> 패키지 가져오기 \> 사용자 지정 패키지** 메뉴 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="e5ca0-254">에 **Unity 패키지 가져오기** 표시 되는 상자에서 아래에 있는 포함 하 여 모든 것을 확인 **플러그 인** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="e5ca0-256">클릭 합니다 **가져오기** 프로젝트에 항목을 추가 하려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="e5ca0-257">로 이동 합니다 **Insights** 아래에 폴더 **플러그 인** 프로젝트에서 표시 하 고 다음 플러그 인 선택 *만*:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="e5ca0-258">Microsoft.ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="e5ca0-258">Microsoft.ApplicationInsights</span></span>

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="e5ca0-260">이 사용 하 여 *플러그 인* 되도록 선택 하면 **Any 플랫폼** 는 **unchecked**, 한지 확인 합니다 **WSAPlayer** 이기도  **unchecked**, 클릭 **적용**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="e5ca0-261">이 방법은 파일이 올바르게 구성 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="e5ca0-263">Unity 편집기에서 사용할 수만 구성 같이 플러그 인을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="e5ca0-264">다양 한 Dll 프로젝트 Unity에서 내보낸 후 사용 되는 WSA 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="e5ca0-265">열어야 할 때 다음에 **WSA** 폴더 내에서 합니다 **Insights** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="e5ca0-266">방금 구성한 동일한 파일의 복사본을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="e5ca0-267">이 파일을 선택한 다음 [관리자]에서 있는지를 확인 **Any 플랫폼** 는 **unchecked**, 한지 확인 합니다 **만** **WSAPlayer** 는**체크**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="e5ca0-268">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-268">Click **Apply**.</span></span>

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="e5ca0-270">수행 해야 **4 ~ 6 단계**에 대해서는 *Newtonsoft* 플러그 인 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="e5ca0-271">참조 된 결과 모양을 스크린샷 아래.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Unity 패키지 가져오기](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="e5ca0-273">4 장-카메라 및 설정 사용자 컨트롤</span><span class="sxs-lookup"><span data-stu-id="e5ca0-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="e5ca0-274">이 장에서 설정한 카메라 및 컨트롤을 확인 하는 장면에서 이동 가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="e5ca0-275">마우스 오른쪽 단추로 클릭 계층 창에서 빈 영역에 다음 **Create** > **빈**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![카메라 및 사용자 정의 컨트롤 설정](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="e5ca0-277">에 새 빈 GameObject 이름 바꾸기 **카메라 부모**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![카메라 및 사용자 정의 컨트롤 설정](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="e5ca0-279">마우스 오른쪽 단추로 클릭 계층 창에서 빈 영역에 다음 **3D 개체**, 그런 다음 **구체**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="e5ca0-280">구체 이름 바꾸기 **오른쪽**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="e5ca0-281">설정 된 **배율 변환** 하려면 오른쪽의 **0.1, 0.1, 0.1**</span><span class="sxs-lookup"><span data-stu-id="e5ca0-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![카메라 및 사용자 정의 컨트롤 설정](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="e5ca0-283">제거는 **구체 Collider** 구성 요소를 클릭 하 여 오른쪽에서는 **기어** 에 *구체 Collider* 구성 요소를 차례로 **구성 요소 제거** .</span><span class="sxs-lookup"><span data-stu-id="e5ca0-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![카메라 및 사용자 정의 컨트롤 설정](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="e5ca0-285">계층 패널 끌기에는 **주 카메라** 및 **오른쪽** 끌어온 개체를 **카메라 부모** 개체.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![카메라 및 사용자 정의 컨트롤 설정](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="e5ca0-287">설정 합니다 **변환 위치** 둘 다의 합니다 **주 카메라** 및 **오른쪽** 개체를 **0, 0, 0**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![카메라 및 사용자 정의 컨트롤 설정](images/AzureLabs-Lab309-31.png)

    ![카메라 및 사용자 정의 컨트롤 설정](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="e5ca0-290">5 장-Unity 장면에서 개체를 설정</span><span class="sxs-lookup"><span data-stu-id="e5ca0-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="e5ca0-291">이제 사용자 작용할 수 있는 장면에 대 한 일부 기본 셰이프를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="e5ca0-292">빈 영역을 마우스 오른쪽 단추로 클릭 합니다 *계층 패널*, 그런 다음 **3D 개체**을 선택한 후 **평면**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="e5ca0-293">평면 설정 **위치를 변환** 하 **0,-1, 0**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="e5ca0-294">평면 설정 **배율 변환** 하 **5, 1, 5**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Unity 장면에서 개체를 설정](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="e5ca0-296">사용 하려면 기본 재질을 만드는 사용자 **평면** 개체를 다른 셰이프를 더 쉽게 볼 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="e5ca0-297">로 이동 하 *프로젝트 패널*, 마우스 오른쪽 단추로 클릭 한 다음 **만들기**뒤 **폴더**, 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="e5ca0-298">이름을 **자료**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-298">Name it **Materials**.</span></span>

    ![Unity 장면에서 개체를 설정](images/AzureLabs-Lab309-34.png) ![Unity 장면에서 개체를 설정](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="e5ca0-301">엽니다는 **자료** 폴더를 마우스 오른쪽 단추를 클릭 **만들기**, 다음 **자료**새 자료를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="e5ca0-302">이름을 **파란색**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-302">Name it **Blue**.</span></span>

    ![Unity 장면에서 개체를 설정](images/AzureLabs-Lab309-36.png) ![Unity 장면에서 개체를 설정](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="e5ca0-305">새 **파란색** 자료를 확인에서 선택 합니다 *검사기*를 함께 사각형 창을 클릭 하 고 **Albedo**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="e5ca0-306">파랑 색 선택 (아래 그림은 **16 진수 색: \#3592FFFF**).</span><span class="sxs-lookup"><span data-stu-id="e5ca0-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="e5ca0-307">선택 했으면 닫기 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-307">Click the close button once you have chosen.</span></span>

    ![Unity 장면에서 개체를 설정](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="e5ca0-309">경우 새 자료를 끌어를 **자료** 에 새로 만든 폴더 **평면**, 장면 내 (에서 삭제 또는 **평면** 내에서 개체를  *계층*).</span><span class="sxs-lookup"><span data-stu-id="e5ca0-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Unity 장면에서 개체를 설정](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="e5ca0-311">빈 영역을 마우스 오른쪽 단추로 클릭 합니다 *계층 패널*, 그런 다음 **3D 개체, Capsule**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="e5ca0-312">사용 하 여는 **Capsule** 변경 선택 하면 해당 **변환** *위치* 에: **-10, 1, 0**.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="e5ca0-313">빈 영역을 마우스 오른쪽 단추로 클릭 합니다 *계층 패널*, 그런 다음 **3D 개체를 큐브의**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="e5ca0-314">사용 하 여는 **큐브** 변경 선택 하면 해당 **변환** *위치* 에: **0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="e5ca0-315">빈 영역을 마우스 오른쪽 단추로 클릭 합니다 *계층 패널*, 그런 다음 **3D 개체, 구**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="e5ca0-316">사용 하 여를 **구체** 변경 선택 하면 해당 **변환** *위치* 에: **10, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Unity 장면에서 개체를 설정](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="e5ca0-318">이러한 *위치* 값은 *제안*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="e5ca0-319">자유롭게 개체 거리는 카메라에서 멀리 없으면 응용 프로그램의 사용자가 보다 쉽게 것에 원하는 개체의 위치를 설정 하 여 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="e5ca0-320">응용 프로그램이 실행 되는 경우이 달성 하기 위해 장면 내의 개체를 식별할 수 있어야 할 태그를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="e5ca0-321">개체의 하나를 선택 합니다 *검사기* 패널에서 **태그 추가...** 가 교환 하는 합니다 *검사기* 사용 하 여 합니다 **태그 및 계층** 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="e5ca0-322">![Unity 장면에서 개체를 설정](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="e5ca0-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="e5ca0-323">클릭 합니다 **+ (더하기)** 기호를 다음으로 태그 이름 입력 **ObjectInScene**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Unity 장면에서 개체를 설정](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="e5ca0-325">다른 이름으로 태그를 사용 하는 경우이 변경도 확인 해야 합니다는 *DataFromAnalytics*를 *ObjectTrigger*, 및 *Gaze*, 나중에 스크립트 있도록 프로그램 개체를 찾을 장면 내에서 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="e5ca0-326">이제 생성 된 태그를 사용 하 여 개체의 세 가지 모두에 적용 하도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="e5ca0-327">*계층*, 보유를 **Shift** 키를 클릭 합니다 **Capsule**, **큐브**, 및 **구체**, 개체를 그런 다음는 *검사기*, 함께 드롭다운 메뉴를 클릭 **태그**를 클릭 합니다 *ObjectInScene* 만든 태그.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="e5ca0-328">![Unity 장면에서 개체를 설정](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="e5ca0-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="e5ca0-329">-6 장 ApplicationInsightsTracker 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="e5ca0-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="e5ca0-330">생성 해야 하는 첫 번째 스크립트 **ApplicationInsightsTracker**를 담당 하는:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="e5ca0-331">Azure Application Insights로 전송 하도록 사용자 상호 작용을 기반으로 이벤트를 만드는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="e5ca0-332">사용자 상호 작용에 따라 적절 한 이벤트 이름으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="e5ca0-333">Application Insights 서비스 인스턴스에 이벤트를 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="e5ca0-334">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-334">To create this class:</span></span>

1.  <span data-ttu-id="e5ca0-335">마우스 오른쪽 단추로 클릭 합니다 *프로젝트 패널*, 한 다음 **만들기** > **폴더**.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="e5ca0-336">폴더의 이름을 **스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-336">Name the folder **Scripts**.</span></span>

    ![ApplicationInsightsTracker 클래스 만들기](images/AzureLabs-Lab309-46.png)  ![ApplicationInsightsTracker 클래스 만들기](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="e5ca0-339">사용 하 여는 **스크립트** 가 만든 폴더를 열려면이 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="e5ca0-340">그런 다음, 해당 폴더 내에서 마우스 오른쪽 단추로 클릭 **Create**  >   **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="e5ca0-341">스크립트 이름을 **ApplicationInsightsTracker**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="e5ca0-342">새 두 번 클릭 **ApplicationInsightsTracker** 스크립트를 사용 하 여 열고 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="e5ca0-343">스크립트를 맨 위에 있는 네임 스페이스를 업데이트 합니다. 아래와 같이:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="e5ca0-344">클래스 내에서 다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-344">Inside the class insert the following variables:</span></span>

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
    > <span data-ttu-id="e5ca0-345">설정 합니다 **instrumentationKey applicationId 및 API_Key** 사용 하 여 적절 하 게 값을 *서비스 키* 에서 설명한 것 처럼 Azure Portal에서 [1 장](#chapter-1---the-azure-portal), 9 단계 이상.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="e5ca0-346">다음 추가 합니다 **start ()** 하 고 **Awake()** 클래스를 초기화 하는 경우 호출 될 메서드를:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="e5ca0-347">응용 프로그램에서 등록 하는 메트릭 및 이벤트를 보내는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

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

8.  <span data-ttu-id="e5ca0-348">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="e5ca0-349">7-장 게이즈 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="e5ca0-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="e5ca0-350">만들려면 다음 스크립트를 **Gaze** 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="e5ca0-351">이 스크립트는 생성을 담당를 *Raycast* 는 프로젝션 앞에서 *주 카메라*, 사용자를 보고 하는 개체를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="e5ca0-352">이 경우에 *Raycast* 사용자 개체를 보고 하는 경우를 식별 해야 합니다는 **ObjectInScene** 태그 및 다음 기간 사용자를 계산 *gazes* 해당 개체에서.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="e5ca0-353">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="e5ca0-354">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="e5ca0-355">스크립트 이름을 **Gaze**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="e5ca0-356">스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="e5ca0-357">기존 코드를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-357">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="e5ca0-358">에 대 한 코드를 **Awake()** 하 고 **start ()** 메서드는 이제 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

6.  <span data-ttu-id="e5ca0-359">내부를 **Gaze** 클래스에 다음 코드를 추가 합니다를 **update ()** 프로젝트에 대 한 메서드를 *Raycast* 대상 적중 횟수를 검색 하 고:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

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

7.  <span data-ttu-id="e5ca0-360">추가 합니다 **ResetFocusedObject()** 데이터를 전송 하는 메서드인 **Application Insights** 개체에 사용자가 검토 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

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

8.  <span data-ttu-id="e5ca0-361">이제 완료 합니다 **Gaze** 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="e5ca0-362">변경 내용을 저장 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="e5ca0-363">8-장 ObjectTrigger 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="e5ca0-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="e5ca0-364">생성 해야 하는 다음 스크립트 **ObjectTrigger**를 담당 하는:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="e5ca0-365">주 카메라에 대 한 충돌에 대 한 필요한 구성 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="e5ca0-366">카메라로 태그가 지정 된 개체에 가까운 경우 감지 **ObjectInScene**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="e5ca0-367">스크립트를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-367">To create the script:</span></span>

1.  <span data-ttu-id="e5ca0-368">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="e5ca0-369">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="e5ca0-370">스크립트 이름을 **ObjectTrigger**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="e5ca0-371">스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="e5ca0-372">기존 코드를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-372">Replace the existing code with the following:</span></span>

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

4.  <span data-ttu-id="e5ca0-373">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="e5ca0-374">9-장 DataFromAnalytics 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="e5ca0-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="e5ca0-375">만들려는 해야 합니다 **DataFromAnalytics** 담당 하는 스크립트:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="e5ca0-376">에 대 한 개체 되었습니다 도달 카메라로 가장 하는 분석 데이터를 가져오고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="e5ca0-377">사용 하는 *서비스 키*, Azure Application Insights 서비스 인스턴스와 통신을 허용 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="e5ca0-378">장면에서 개체 정렬 기준인에 가장 높은 이벤트 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="e5ca0-379">에 가장 approached 개체의 재질 색 변경 *녹색*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="e5ca0-380">스크립트를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-380">To create the script:</span></span>

1.  <span data-ttu-id="e5ca0-381">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="e5ca0-382">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="e5ca0-383">스크립트 이름을 **DataFromAnalytics**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="e5ca0-384">스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="e5ca0-385">다음 네임 스페이스를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="e5ca0-386">스크립트 내에서 다음을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-386">Inside the script, insert the following:</span></span>

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

6.  <span data-ttu-id="e5ca0-387">내 합니다 **DataFromAnalytics** 클래스, 후 마우스 오른쪽 단추로 합니다 **start ()** 메서드를 이라는 다음 메서드를 추가 **FetchAnalytics()** 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="e5ca0-388">이 메서드는 사용 하 여 키 값 쌍의 목록 채워야는 *GameObject* 및 자리 표시자 이벤트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="e5ca0-389">초기화 합니다 **GetWebRequest()** 코 루틴입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="e5ca0-390">쿼리 구조에 대 한 호출 *Application Insights* 이 메서드 내에서 찾을 수 있습니다으로 또한 합니다 *쿼리 URL* 끝점입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

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

7.  <span data-ttu-id="e5ca0-391">바로 아래 합니다 **FetchAnalytics()** 메서드를 라는 메서드를 추가 **GetWebRequest()** 를 반환 하는 *IEnumerator*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="e5ca0-392">이 메서드는 이벤트를 특정 해당 횟수를 요청 하는 일을 담당 *GameObject*, 내에서 호출한 *Application Insights*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="e5ca0-393">보낸된 모든 쿼리를 반환한 경우 합니다 **DetermineWinner()** 메서드가 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

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

8.  <span data-ttu-id="e5ca0-394">다음 메서드는 **DetermineWinner()** , 목록을 정렬 하는 *GameObject* 하 고 *Int* 가장 높은 이벤트 수에 따라 쌍입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="e5ca0-395">그런 다음의 재질 색 변경 *GameObject* 하 *녹색* (가장 높은 수 있는 것에 대 한 피드백)으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="e5ca0-396">이 분석 결과 사용 하 여 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-396">This displays a message with the analytics results.</span></span>

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

9.  <span data-ttu-id="e5ca0-397">받은 JSON 개체를 deserialize 하는 데 사용 되는 클래스 구조를 추가 *Application Insights*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="e5ca0-398">이러한 클래스의 맨 아래에 추가 하 **DataFromAnalytics** 클래스 파일인 **외부** 클래스 정의의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

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

10. <span data-ttu-id="e5ca0-399">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="e5ca0-400">10-장 이동 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="e5ca0-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="e5ca0-401">합니다 **이동** 스크립트는 다음 스크립트 만들기 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="e5ca0-402">이 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-402">It is responsible for:</span></span>

- <span data-ttu-id="e5ca0-403">카메라 방향에 따라 주 카메라를 이동은 포함을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="e5ca0-404">장면 개체를 다른 모든 스크립트를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="e5ca0-405">스크립트를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-405">To create the script:</span></span>

1.  <span data-ttu-id="e5ca0-406">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="e5ca0-407">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="e5ca0-408">스크립트 이름을 **이동**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="e5ca0-409">사용 하 여 열고 스크립트를 두 번 클릭 *Visual Studio*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="e5ca0-410">기존 코드를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-410">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="e5ca0-411">내를 **이동** 클래스 *아래* 빈 **update ()** 메서드를 사용자가 직접 컨트롤러를 사용 하 여 가상 공간에 이동 하도록 허용 하는 다음 메서드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

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

6.  <span data-ttu-id="e5ca0-412">마지막으로 내에서 메서드 호출을 추가 합니다 **update ()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="e5ca0-413">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="e5ca0-414">11 장-스크립트 파일에 대 한 참조 설정</span><span class="sxs-lookup"><span data-stu-id="e5ca0-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="e5ca0-415">이 챕터에 배치 해야 합니다 **이동** 에 스크립트를 **카메라 부모** 참조 대상을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="e5ca0-416">해당 스크립트는 필요할 수 있는 다른 스크립트를 배치 하는 것을 처리 한 다음 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="e5ca0-417">**스크립트** 폴더에는 *프로젝트 패널*을 끌어를 **이동** 스크립트를 **카메라 부모** 개체에는  *계층 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Unity 장면에 대 한 스크립트 참조 설정](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="e5ca0-419">클릭 합니다 **카메라 부모**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="e5ca0-420">에 *계층 패널*, 끌어를 **오른쪽** 에서 개체를 *계층 패널* 참조 대상에 **컨트롤러**의 *검사기 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="e5ca0-421">설정 합니다 **사용자 속도** 하 **5**아래 이미지에서 보여준 것 처럼 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Unity 장면에 대 한 스크립트 참조 설정](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="e5ca0-423">12 장-Unity 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="e5ca0-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="e5ca0-424">이 프로젝트의 Unity 섹션에 필요한 모든 항목이 이제 완료 되 면 Unity에서 작성 하는 시간 이므로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="e5ca0-425">이동할 **빌드 설정**, (**파일** > **빌드 설정**).</span><span class="sxs-lookup"><span data-stu-id="e5ca0-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="e5ca0-426">**빌드 설정** 창에서 클릭 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-426">From the **Build Settings** window, click **Build**.</span></span>

    ![Unity 프로젝트를 UWP 솔루션 빌드](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="e5ca0-428">A **파일 탐색기** 창은 팝업에서 빌드에 대 한 위치에 대 한 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="e5ca0-429">새 폴더를 만듭니다 (클릭 하 여 **새 폴더** 왼쪽 위 모서리에), 이름을 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Unity 프로젝트를 UWP 솔루션 빌드](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="e5ca0-431">새로운 **빌드** 폴더를 다른 폴더를 만들고 (사용 하 여 **새 폴더** 번)을 하 고 이름을 **MR\_Azure\_응용 프로그램\_ Insights**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![Unity 프로젝트를 UWP 솔루션 빌드](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="e5ca0-433">사용 하 여 합니다 **MR\_Azure\_응용 프로그램\_Insights** 폴더를 선택, 클릭 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="e5ca0-434">프로젝트 빌드를 1 분 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="e5ca0-435">다음 *빌드*하십시오 **파일 탐색기** 새 프로젝트의 위치를 표시 하는 데 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a><span data-ttu-id="e5ca0-436">13 장-MR_Azure_Application_Insights 앱을 컴퓨터에 배포</span><span class="sxs-lookup"><span data-stu-id="e5ca0-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="e5ca0-437">배포 하는 **MR\_Azure\_응용 프로그램\_Insights** 로컬 컴퓨터에 앱:</span><span class="sxs-lookup"><span data-stu-id="e5ca0-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="e5ca0-438">솔루션 파일을 열고 프로그램 **MR\_Azure\_응용 프로그램\_Insights** 앱 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="e5ca0-439">에 **솔루션 플랫폼**를 선택 **x86, 로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="e5ca0-440">에 **솔루션 구성** 선택 **디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![Unity 프로젝트를 UWP 솔루션 빌드](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="e5ca0-442">로 이동 **빌드 메뉴** 을 클릭할 **솔루션 배포** 을 컴퓨터에 응용 프로그램을 사이드 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="e5ca0-443">이제 앱 시작할 준비가 되었습니다. 설치 된 앱 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="e5ca0-444">혼합된 현실 응용 프로그램을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="e5ca0-445">개체에 근접 하 고, 원하는 장면 이동할 때를 *Azure Insight* 충분 한 이벤트 데이터 수집 녹색으로 가장 도달 하는 개체를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="e5ca0-446">에 대 한 평균 대기 시간 동안 합니다 *이벤트 및 메트릭* 서비스를 통해 수집 되려면 약 15 분을 사용, 일부 경우에서 최대 1 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="e5ca0-447">14 장-Application Insights 서비스 포털</span><span class="sxs-lookup"><span data-stu-id="e5ca0-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="e5ca0-448">장면 주위를 로밍 하 고 몇 가지 개체 gazed에서 수집 된 데이터를 볼 수는 *Application Insights 서비스* 포털입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="e5ca0-449">Application Insights 서비스 포털로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="e5ca0-450">클릭할 *메트릭 탐색기*합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-450">Click on *Metrics Explorer*.</span></span>

    ![수집 된 데이터를 보면](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="e5ca0-452">나타내는 그래프를 포함 하는 탭에서 열립니다는 *이벤트 및 메트릭* 응용 프로그램에 관련 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="e5ca0-453">그래프에 표시할 데이터에 대 한 (최대 1 시간) 약간의 시간이 걸릴 수 있습니다 위에서 설명한 대로</span><span class="sxs-lookup"><span data-stu-id="e5ca0-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![수집 된 데이터를 보면](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="e5ca0-455">클릭 합니다 *이벤트 모음* 에 *이벤트의 총* 이름만 사용 하 여 이벤트의 자세한 분석을 보려면 응용 프로그램 버전에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![수집 된 데이터를 보면](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="e5ca0-457">에 Application Insights 서비스 응용 프로그램을 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="e5ca0-458">축, 앱 내에서 사용자의 작업을 모니터링할 Application Insights 서비스를 활용 하는 혼합된 현실 앱을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![과정 결과](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="e5ca0-460">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="e5ca0-460">Bonus Exercises</span></span>

<span data-ttu-id="e5ca0-461">**연습 1**</span><span class="sxs-lookup"><span data-stu-id="e5ca0-461">**Exercise 1**</span></span>

<span data-ttu-id="e5ca0-462">ObjectInScene 개체를 수동으로 만드는 대신, 생성 하 고 스크립트 내에서 평면에 해당 좌표를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="e5ca0-463">이러한 방식으로 질문할 수 있습니다 Azure는 가장 인기 있는 개체에 따라 다시 (게이즈 또는 근접 결과에서)를 생성 하 고는 *추가* 이러한 개체 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="e5ca0-464">**연습 2**</span><span class="sxs-lookup"><span data-stu-id="e5ca0-464">**Exercise 2**</span></span>

<span data-ttu-id="e5ca0-465">가장 관련성이 높은 데이터를 가져오고 응용 프로그램에서 시간이 중요 한 데이터를 구현할 수 있도록 시점에서는 Application Insights 결과 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5ca0-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

