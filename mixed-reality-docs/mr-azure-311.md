---
title: MR 및 Azure 311-Microsoft Graph
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Microsoft Graph 활용 하 고 생산성을 높이는 데이터에 연결 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, microsoft graph, hololens, 몰입 형, vr
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694522"
---
>[!NOTE]
><span data-ttu-id="7dfe1-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7dfe1-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7dfe1-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7dfe1-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7dfe1-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7dfe1-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="7dfe1-110">MR 및 Azure 311-Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="7dfe1-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="7dfe1-111">이 과정에서는 혼합 현실 응용 프로그램 내에서 보안 인증을 사용 하 여 Microsoft 계정에 로그인 하는 데 *Microsoft Graph* 를 사용 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="7dfe1-112">그런 다음 응용 프로그램 인터페이스에서 예약 된 모임을 검색 하 고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="7dfe1-113">*Microsoft Graph* 은 다양 한 Microsoft 서비스에 액세스할 수 있도록 설계 된 api 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="7dfe1-114">Microsoft는 관계를 통해 연결 되는 리소스의 행렬로 Microsoft Graph에 대해 설명 합니다. 즉, 응용 프로그램에서 모든 종류의 연결 된 사용자 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="7dfe1-115">자세한 내용은 [Microsoft Graph 페이지](https://developer.microsoft.com/graph)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="7dfe1-116">개발에는 사용자에 게 암호를 입력 하 라는 메시지가 표시 된 후 구를 탭 하 여 사용자에 게 안전 하 게 Microsoft 계정에 로그인 하 라는 메시지가 표시 되는 앱을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="7dfe1-117">자신의 계정에 로그인 한 후에는 사용자가 하루에 예약 된 모임 목록을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="7dfe1-118">이 과정을 완료 하면 다음과 같은 작업을 수행할 수 있는 혼합 현실 HoloLens 응용 프로그램이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="7dfe1-119">탭 제스처를 사용 하 여 개체를 탭 합니다. 그러면 사용자에 게 Microsoft 계정에 로그인 하 라는 메시지가 표시 됩니다 .이를 통해 로그인 하 고 다시 앱으로 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="7dfe1-120">하루에 예약 된 모임 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="7dfe1-121">응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="7dfe1-122">이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="7dfe1-123">이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="7dfe1-124">장치 지원</span><span class="sxs-lookup"><span data-stu-id="7dfe1-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7dfe1-125">과정</span><span class="sxs-lookup"><span data-stu-id="7dfe1-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7dfe1-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7dfe1-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7dfe1-127"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="7dfe1-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="7dfe1-128">MR 및 Azure 311: Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="7dfe1-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="7dfe1-129">✔️</span><span class="sxs-lookup"><span data-stu-id="7dfe1-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="7dfe1-130">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="7dfe1-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="7dfe1-131">이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="7dfe1-132">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (7 월 2018)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="7dfe1-133">[도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="7dfe1-134">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="7dfe1-135">개발 PC</span><span class="sxs-lookup"><span data-stu-id="7dfe1-135">A development PC</span></span>
- [<span data-ttu-id="7dfe1-136">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="7dfe1-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="7dfe1-137">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="7dfe1-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="7dfe1-138">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="7dfe1-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="7dfe1-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7dfe1-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="7dfe1-140">개발자 모드를 사용 하는 [Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="7dfe1-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="7dfe1-141">Azure 설정 및 Microsoft Graph 데이터 검색을 위한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="7dfe1-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="7dfe1-142">유효한 **Microsoft 계정** (개인 또는 회사/학교)</span><span class="sxs-lookup"><span data-stu-id="7dfe1-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="7dfe1-143">동일한 Microsoft 계정을 사용 하 여 현재 날짜에 대해 예약 된 몇 개의 모임</span><span class="sxs-lookup"><span data-stu-id="7dfe1-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="7dfe1-144">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="7dfe1-144">Before you start</span></span>

1.  <span data-ttu-id="7dfe1-145">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="7dfe1-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="7dfe1-146">HoloLens를 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="7dfe1-147">HoloLens를 설정 하는 데 지원이 필요한 경우 [hololens 설정 문서를 방문](https://docs.microsoft.com/hololens/hololens-setup)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="7dfe1-148">새 HoloLens 앱 개발을 시작할 때 보정 및 센서 조정을 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음).</span><span class="sxs-lookup"><span data-stu-id="7dfe1-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="7dfe1-149">보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에](calibration.md#hololens)대 한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="7dfe1-150">센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](sensor-tuning.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="7dfe1-151">1 장-응용 프로그램 등록 포털에서 앱 만들기</span><span class="sxs-lookup"><span data-stu-id="7dfe1-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="7dfe1-152">먼저 응용 프로그램 **등록 포털**에서 응용 프로그램을 만들고 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="7dfe1-153">이 장에서는 계정 콘텐츠에 액세스 하기 위해 *Microsoft Graph* 에 대 한 호출을 수행할 수 있도록 하는 서비스 키를 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="7dfe1-154">[Microsoft 응용 프로그램 등록 포털](https://apps.dev.microsoft.com) 로 이동 하 여 microsoft 계정으로 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="7dfe1-155">로그인 하면 **응용 프로그램 등록 포털로**리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="7dfe1-156">**내 응용 프로그램** 섹션에서 **앱 추가**단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="7dfe1-157">**응용 프로그램 등록 포털** 은 이전에 *Microsoft Graph*작업을 수행 했는지 여부에 따라 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="7dfe1-158">아래 스크린샷에서는 이러한 다양 한 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="7dfe1-159">응용 프로그램의 이름을 추가 하 고 **만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="7dfe1-160">응용 프로그램을 만든 후에는 응용 프로그램 기본 페이지로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="7dfe1-161">**응용 프로그램 Id** 를 복사 하 고 안전한 위치에이 값을 기록해 두어야 합니다. 코드에서 바로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="7dfe1-162">**플랫폼** 섹션에서 **네이티브 응용 프로그램이** 표시 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="7dfe1-163">**플랫폼 추가** *를 클릭 하* 고 **네이티브 응용 프로그램**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="7dfe1-164">동일한 페이지에서 아래로 스크롤하고 **Microsoft Graph 권한** 섹션에서 응용 프로그램에 대 한 추가 권한을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="7dfe1-165">**위임 된 권한**옆의 **추가** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="7dfe1-166">응용 프로그램에서 사용자의 일정에 액세스 하도록 하려면 일정 확인란을 선택 하 고 **확인**을 클릭 합니다 **.**</span><span class="sxs-lookup"><span data-stu-id="7dfe1-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="7dfe1-167">아래쪽으로 스크롤하고 **저장** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="7dfe1-168">저장이 확인 되 고 **응용 프로그램 등록 포털**에서 로그 아웃할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="7dfe1-169">2 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="7dfe1-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="7dfe1-170">다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="7dfe1-171">*Unity* 를 열고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="7dfe1-172">Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="7dfe1-173">**Msgraphmr**을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="7dfe1-174">프로젝트 템플릿이 **3d**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="7dfe1-175">위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="7dfe1-176">그런 다음 **프로젝트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="7dfe1-177">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="7dfe1-178">**기본 설정** **편집** > 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-178">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="7dfe1-179">**외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="7dfe1-180">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="7dfe1-181">**파일**    빌드 설정으로 이동 하 고 유니버설 Windows 플랫폼를 선택한 후 플랫폼 전환 단추를 클릭 하 여 선택 항목을 적용 합니다. > </span><span class="sxs-lookup"><span data-stu-id="7dfe1-181">Go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="7dfe1-182">**파일** > **빌드 설정**에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-182">While still in **File** > **Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="7dfe1-183">**대상 장치가** **HoloLens** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="7dfe1-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="7dfe1-184">**빌드 형식이** **D3D** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="7dfe1-185">**SDK** 가 **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="7dfe1-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="7dfe1-186">**Visual Studio 버전이** **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="7dfe1-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="7dfe1-187">**빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="7dfe1-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="7dfe1-188">장면을 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="7dfe1-189">이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="7dfe1-190">저장 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="7dfe1-191">이에 대 한 새 폴더 및 향후 장면을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="7dfe1-192">새 **폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면**으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="7dfe1-193">새로 만든 **장면** 폴더를 연 다음 *파일 이름*: 텍스트 필드에 **MR_ComputerVisionScene**를 입력 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="7dfe1-194">Unity 프로젝트와 연결 되어 있어야 하므로 *자산* 폴더 내에 unity 장면을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="7dfe1-195">배경 폴더 (및 기타 유사한 폴더)를 만드는 것은 Unity 프로젝트를 구조화 하는 일반적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="7dfe1-196">*빌드 설정*의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="7dfe1-197">*빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="7dfe1-198">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="7dfe1-199">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="7dfe1-200">**스크립팅** **런타임 버전** 은 **실험적** (.net 4.6와 동일) 이어야 하며,이 경우 편집기를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="7dfe1-201">**Scripting 백엔드** 는 **.net** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="7dfe1-202">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="7dfe1-203">**게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="7dfe1-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="7dfe1-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="7dfe1-205">패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음)에서 **가상 현실 지원**을 확인 하 고 **Windows Mixed Reality SDK** 가 추가 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="7dfe1-206">*빌드 설정*으로 돌아가서 *Unity C# 프로젝트가* 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="7dfe1-207">*빌드 설정* 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="7dfe1-208">장면 및 프로젝트를 저장 합니다 (**파일** > **저장 장면/파일** > **저장 프로젝트**).</span><span class="sxs-lookup"><span data-stu-id="7dfe1-208">Save your scene and project (**FILE** > **SAVE SCENES / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="7dfe1-209">3 장-Unity에서 라이브러리 가져오기</span><span class="sxs-lookup"><span data-stu-id="7dfe1-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7dfe1-210">이 과정의 *Unity 설정* 구성 요소를 건너뛰고 계속 해 서 코드를 계속 사용 하려면이 [311. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)를 다운로드 하 여 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 [5 장에서 계속 진행 합니다. ](#chapter-5---create-meetingsui-class).</span><span class="sxs-lookup"><span data-stu-id="7dfe1-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="7dfe1-211">Unity 내에서 *Microsoft Graph* 를 사용 하려면 **Microsoft. Identity. Client** DLL을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="7dfe1-212">그러나 Microsoft Graph SDK를 사용할 수 있지만 Unity 프로젝트를 빌드한 후에 NuGet 패키지를 추가 해야 합니다 (프로젝트 빌드 후 편집).</span><span class="sxs-lookup"><span data-stu-id="7dfe1-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="7dfe1-213">필요한 Dll을 Unity로 직접 가져오는 것이 더 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="7dfe1-214">현재 Unity에는 가져온 후 플러그 인을 다시 구성 해야 하는 알려진 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="7dfe1-215">이러한 단계 (이 섹션에서는 4-7)는 버그가 해결 된 후 더 이상 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="7dfe1-216">사용자 고유의 프로젝트로 *Microsoft Graph* 를 가져오려면 [MSGraph_LabPlugins 파일을 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="7dfe1-217">이 패키지는 테스트 된 라이브러리 버전을 사용 하 여 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="7dfe1-218">Unity 프로젝트에 사용자 지정 Dll을 추가 하는 방법에 대 한 자세한 내용을 보려면 [이 링크를 따르세요](https://docs.unity3d.com/Manual/UsingDLL.html).</span><span class="sxs-lookup"><span data-stu-id="7dfe1-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="7dfe1-219">패키지를 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="7dfe1-219">To import the package:</span></span>

1.  <span data-ttu-id="7dfe1-220">**자산** > **가져오기**패키지사용자 > **지정 패키지** 메뉴 옵션을 사용 하 여 unity 패키지를 unity에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-220">Add the Unity Package to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span> <span data-ttu-id="7dfe1-221">방금 다운로드 한 패키지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="7dfe1-222">표시 되는 **Unity 패키지 가져오기** 상자에서 **플러그 인** 을 포함 하 여 모든 항목을 선택 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="7dfe1-223">**가져오기** 단추를 클릭 하 여 프로젝트에 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="7dfe1-224">*프로젝트 패널* 에서 **플러그** 인의 **Msgraph** 폴더로 이동 하 고 **Microsoft. Identity. Client**라는 플러그 인을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="7dfe1-225">*플러그 인* 을 선택 하 고 **모든 플랫폼이** 선택 취소 되어 있는지 확인 한 다음 **WSAPlayer** 도 선택 취소 되어 있는지 확인 하 고 **적용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="7dfe1-226">이는 파일이 올바르게 구성 되었는지 확인 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="7dfe1-227">이러한 플러그 인을 표시 하면 Unity 편집기 에서만 사용 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="7dfe1-228">WSA 폴더에는 프로젝트를 Unity에서 유니버설 Windows 응용 프로그램으로 내보낸 후에 사용 되는 다른 Dll 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="7dfe1-229">다음으로, **Msgraph** 폴더 내에서 **WSA** 폴더를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="7dfe1-230">방금 구성한 파일의 복사본이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="7dfe1-231">파일을 선택한 다음 검사기에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="7dfe1-232">**모든 플랫폼이** **선택 취소**되어 있고 **WSAPlayer** **만** **선택**되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="7dfe1-233">**SDK** 가 **UWP**로 설정 되어 있고 **Scripting 백 엔드가** **Dot** 로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="7dfe1-234">**처리 안 함** 이 **선택**되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="7dfe1-235">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="7dfe1-236">4 장-카메라 설정</span><span class="sxs-lookup"><span data-stu-id="7dfe1-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="7dfe1-237">이 챕터에서는 장면의 기본 카메라를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="7dfe1-238">*계층 패널*에서 **기본 카메라**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="7dfe1-239">선택한 후에는 *검사기* 패널에서 **주 카메라** 의 모든 구성 요소를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="7dfe1-240">**카메라 개체** 의 이름을 **주 카메라로** 지정 해야 합니다 (철자 확인).</span><span class="sxs-lookup"><span data-stu-id="7dfe1-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="7dfe1-241">기본 카메라 **태그** 는 **maincamera** 로 설정 되어야 합니다 (철자 확인).</span><span class="sxs-lookup"><span data-stu-id="7dfe1-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="7dfe1-242">**변환 위치가** **0, 0, 0** 으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="7dfe1-243">**Clear 플래그** 를 **Solid 색** 으로 설정</span><span class="sxs-lookup"><span data-stu-id="7dfe1-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="7dfe1-244">카메라 구성 요소의 **배경색** 을 **검은색, 알파 0** **(16 진수 코드: #00000000)** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="7dfe1-245">*계층 패널* 의 최종 개체 구조는 아래 이미지에 표시 된 것과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="7dfe1-246">5 장-MeetingsUI 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="7dfe1-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="7dfe1-247">만들어야 하는 첫 번째 스크립트는 **MeetingsUI**입니다 .이 스크립트는 응용 프로그램의 UI (환영 메시지, 지침 및 모임 세부 정보)를 호스트 하 고 채우는 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="7dfe1-248">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="7dfe1-248">To create this class:</span></span>

1.  <span data-ttu-id="7dfe1-249">*프로젝트 패널*에서 **자산** 폴더를 마우스 오른쪽 단추로 클릭 한 다음**폴더** **만들기** > 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-249">Right-click on the **Assets** folder in the *Project Panel*, then select **Create** > **Folder**.</span></span> <span data-ttu-id="7dfe1-250">폴더 이름을 **스크립트**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="7dfe1-251">**스크립트** 폴더를 열고 해당 폴더 내에서 **C# 스크립트** **만들기**  >  를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-251">Open the **Scripts** folder then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="7dfe1-252">스크립트 이름을 **MeetingsUI로 합니다.**</span><span class="sxs-lookup"><span data-stu-id="7dfe1-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="7dfe1-253">새 **MeetingsUI** 스크립트를 두 번 클릭 하 여 *Visual Studio*에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="7dfe1-254">다음 네임 스페이스를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="7dfe1-255">클래스 내에서 다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-255">Inside the class insert the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  <span data-ttu-id="7dfe1-256">그런 다음 **Start ()** 메서드를 바꾸고 해제 **()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="7dfe1-257">이러한 작업은 클래스가 초기화 될 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-257">These will be called when the class initializes:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  <span data-ttu-id="7dfe1-258">*모임 UI* 만들기를 담당 하는 메서드를 추가 하 고 요청 시 현재 모임으로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. <span data-ttu-id="7dfe1-259">**Update ()** 메서드를 **삭제** 하 고 Unity로 반환 하기 전에 Visual Studio에서 **변경 내용을 저장** 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="7dfe1-260">6 장-그래프 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="7dfe1-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="7dfe1-261">만들 다음 스크립트는 **그래프** 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="7dfe1-262">이 스크립트는를 호출 하 여 사용자를 인증 하 고 사용자의 일정에서 현재 날짜에 대 한 예약 된 모임을 검색 하는 작업을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="7dfe1-263">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="7dfe1-263">To create this class:</span></span>

1.  <span data-ttu-id="7dfe1-264">**Scripts** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="7dfe1-265">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="7dfe1-266">스크립트 **그래프**의 이름을로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="7dfe1-267">스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="7dfe1-268">다음 네임 스페이스를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-268">Insert the following namespaces:</span></span>

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="7dfe1-269">이 스크립트에 포함 된 코드의 일부는 [미리 컴파일 지시문](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)을 기반으로 하기 때문에 Visual Studio 솔루션을 빌드할 때 라이브러리 문제를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="7dfe1-270">**Start ()** 및 **Update ()** 메서드를 사용 하지 않으므로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="7dfe1-271">**Graph** 클래스 외부에서 매일 예약 된 모임을 나타내는 JSON 개체를 deserialize 하는 데 필요한 다음 개체를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  <span data-ttu-id="7dfe1-272">**Graph** 클래스 내에서 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-272">Inside the **Graph** class, add the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > <span data-ttu-id="7dfe1-273">**AppId** 값을  **[1 장](#chapter-1---create-your-app-in-the-application-registration-portal), 4 단계**에서 적어둔 **앱 Id** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="7dfe1-274">이 값은 응용 프로그램 등록 페이지의 **응용 프로그램 등록 포털** 에 표시 되는 값과 동일 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="7dfe1-275">**Graph** 클래스 내에서 **SignInAsync ()** 및 **AquireTokenAsync ()** 메서드를 추가 하 여 사용자에 게 로그인 자격 증명을 삽입 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  <span data-ttu-id="7dfe1-276">다음 두 가지 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="7dfe1-277">**BuildTodayCalendarEndpoint ()** -예약 된 모임이 검색 되는 날짜 및 시간 범위를 지정 하는 URI를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="7dfe1-278">**ListMeetingsAsync ()** - *Microsoft Graph*에서 예약 된 모임을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. <span data-ttu-id="7dfe1-279">이제 **Graph** 스크립트를 완료 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="7dfe1-280">Unity로 반환 하기 전에 Visual Studio에서 **변경 내용을 저장** 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="7dfe1-281">7 장-GazeInput 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="7dfe1-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="7dfe1-282">이제 **GazeInput**을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="7dfe1-283">이 클래스는 **기본 카메라**에서 들어오는 **raycast** 를 사용 하 여 앞으로 프로젝션 하는 사용자의 응시를 처리 하 고 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="7dfe1-284">스크립트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-284">To create the script:</span></span>

1.  <span data-ttu-id="7dfe1-285">**Scripts** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="7dfe1-286">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="7dfe1-287">스크립트 이름을 **GazeInput**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="7dfe1-288">스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="7dfe1-289">Serialize 할 수 있도록 **GazeInput** 클래스 **\[위에\]' system.string**' 태그를 추가 하는 것과 함께 아래와 일치 하도록 네임 스페이스 코드를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="7dfe1-290">**GazeInput** 클래스 내에서 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-290">Inside the **GazeInput** class, add the following variables:</span></span>

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="7dfe1-291">**CreateCursor ()** 메서드를 추가 하 여 장면에 HoloLens 커서를 만들고 **Start ()** 메서드에서 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  <span data-ttu-id="7dfe1-292">다음 메서드는 응시 Raycast를 사용 하도록 설정 하 고 포커스가 있는 개체를 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="7dfe1-293">Unity로 반환 하기 전에 Visual Studio에서 **변경 내용을 저장** 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="7dfe1-294">8 장-상호 작용 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="7dfe1-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="7dfe1-295">이제 다음을 담당 하는 **상호 작용** 스크립트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="7dfe1-296">사용자가 장면에서 "button"의 로그인과 상호 작용할 수 있도록 하는 **탭** 상호 작용 및 **카메라 응시**를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="7dfe1-297">사용자가 상호 작용할 수 있도록 장면에 "button" 개체의 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="7dfe1-298">스크립트를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-298">To create the script:</span></span>

1.  <span data-ttu-id="7dfe1-299">**Scripts** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="7dfe1-300">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="7dfe1-301">스크립트 **상호 작용**의 이름을로 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="7dfe1-302">스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="7dfe1-303">다음 네임 스페이스를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="7dfe1-304">**상호 작용** 클래스의 상속을 *MonoBehaviour* 에서 **GazeInput**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="7dfe1-305">~~공용 클래스 상호 작용: MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="7dfe1-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="7dfe1-306">**상호 작용** 클래스 내에서 다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="7dfe1-307">**Start** 메서드를 대체 합니다. ' base ' 응시 클래스 메서드를 호출 하는 재정의 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="7dfe1-308">**Start ()** 는 클래스가 초기화 되 고, 입력 인식을 등록 하 고, 장면에 로그인 *단추* 를 만들 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  <span data-ttu-id="7dfe1-309">**CreateSignInButton ()** 메서드를 추가 합니다 .이 메서드는 장면의 로그인 *단추* 를 인스턴스화하고 해당 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  <span data-ttu-id="7dfe1-310">*탭핑* 사용자 이벤트에 대해 응답 하는 **GestureRecognizer_Tapped ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. <span data-ttu-id="7dfe1-311">**Update ()** 메서드를 **삭제** 한 다음 Unity로 반환 하기 전에 Visual Studio에서 **변경 내용을 저장** 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="7dfe1-312">9 장-스크립트 참조 설정</span><span class="sxs-lookup"><span data-stu-id="7dfe1-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="7dfe1-313">이 장에서는 **기본 카메라**에 **상호 작용** 스크립트를 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="7dfe1-314">그런 다음이 스크립트는 필요한 위치에 다른 스크립트를 배치 하는 것을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="7dfe1-315">아래 그림과 같이 *프로젝트 패널*의 **Scripts** 폴더에서 스크립트 **상호 작용** 을 **주 카메라** 개체로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="7dfe1-316">10 장-태그 설정</span><span class="sxs-lookup"><span data-stu-id="7dfe1-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="7dfe1-317">응시를 처리 하는 코드는 **SignInButton** 태그를 사용 하 여 사용자가 *Microsoft Graph*에 로그인 하기 위해 상호 작용 하는 개체를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="7dfe1-318">태그를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-318">To create the Tag:</span></span>

1.  <span data-ttu-id="7dfe1-319">Unity 편집기의 *계층 패널*에서 **주 카메라** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="7dfe1-320">*Inspector 패널* 에서 **maincamera** *태그* 를 클릭 하 여 드롭다운 목록을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="7dfe1-321">**태그 추가** ...를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="7dfe1-322">**+** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="7dfe1-323">태그 이름을 **SignInButton** 로 작성 하 고 저장을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="7dfe1-324">11 장-UWP에 Unity 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="7dfe1-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="7dfe1-325">이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었으므로 Unity에서 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="7dfe1-326">이동할 *빌드 설정* (**파일*>*설정** 빌드).</span><span class="sxs-lookup"><span data-stu-id="7dfe1-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="7dfe1-327">아직 없는 경우 tick **\# Unity C 프로젝트**입니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="7dfe1-328">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-328">Click **Build**.</span></span> <span data-ttu-id="7dfe1-329">Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 **파일 탐색기** 창을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="7dfe1-330">이제 해당 폴더를 만들고 이름을 **App**으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="7dfe1-331">그런 다음 **앱** 폴더를 선택 하 고 **폴더 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="7dfe1-332">Unity는 **응용** 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="7dfe1-333">Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)</span><span class="sxs-lookup"><span data-stu-id="7dfe1-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="7dfe1-334">12 장-HoloLens에 배포</span><span class="sxs-lookup"><span data-stu-id="7dfe1-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="7dfe1-335">HoloLens에 배포 하려면:</span><span class="sxs-lookup"><span data-stu-id="7dfe1-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="7dfe1-336">HoloLens의 IP 주소 (원격 배포의 경우)가 필요 하 고 HoloLens가 **개발자 모드** 에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="7dfe1-337">가상 하드 디스크 파일에 대한 중요 정보를 제공하려면</span><span class="sxs-lookup"><span data-stu-id="7dfe1-337">To do this:</span></span>

    1.  <span data-ttu-id="7dfe1-338">HoloLens를 입고 하는 동안 **설정을**엽니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="7dfe1-339">**네트워크 & 인터넷** > **wi-fi** > **고급 옵션** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="7dfe1-340">**IPv4** 주소를 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="7dfe1-341">그런 다음 **설정**으로 다시 이동한 다음**개발자** 를 위한 **& 보안** > 을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="7dfe1-342">**에서 개발자 모드를**설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="7dfe1-343">새 Unity 빌드 ( **앱** 폴더)로 이동 하 여 **Visual Studio**에서 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="7dfe1-344">**솔루션 구성** 에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="7dfe1-345">**솔루션 플랫폼**에서 **X86, 원격 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="7dfe1-346">원격 장치의 **IP 주소** (이 경우에는 HoloLens)를 삽입 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="7dfe1-347">**빌드** 메뉴로 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 HoloLens로 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="7dfe1-348">이제 앱이 HoloLens에 설치 된 앱 목록에 표시 되어 시작할 준비가 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="7dfe1-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="7dfe1-349">Microsoft Graph HoloLens 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="7dfe1-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="7dfe1-350">축 하 합니다. Microsoft Graph를 활용 하 여 사용자 달력 데이터를 읽고 표시 하는 혼합 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="7dfe1-351">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="7dfe1-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="7dfe1-352">연습 1</span><span class="sxs-lookup"><span data-stu-id="7dfe1-352">Exercise 1</span></span>

<span data-ttu-id="7dfe1-353">Microsoft Graph를 사용 하 여 사용자에 대 한 기타 정보 표시</span><span class="sxs-lookup"><span data-stu-id="7dfe1-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="7dfe1-354">사용자 전자 메일/전화 번호/프로필 사진</span><span class="sxs-lookup"><span data-stu-id="7dfe1-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="7dfe1-355">연습 1</span><span class="sxs-lookup"><span data-stu-id="7dfe1-355">Exercise 1</span></span>

<span data-ttu-id="7dfe1-356">음성 컨트롤을 구현 하 여 Microsoft Graph UI를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7dfe1-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
