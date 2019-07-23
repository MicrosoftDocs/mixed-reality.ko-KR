---
title: MR 및 311-Microsoft Graph, Azure
description: Microsoft Graph를 활용 하 고 혼합된 현실 응용 프로그램에서 생산성을 높이 데이터에 연결 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, microsoft graph, hololens, 몰입 형, vr
ms.openlocfilehash: 04c72a7ef7724cfcc27867f7f003c171a6f7851f
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694522"
---
>[!NOTE]
><span data-ttu-id="d7f9f-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="d7f9f-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="d7f9f-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="d7f9f-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="d7f9f-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="d7f9f-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="d7f9f-110">MR 및 311-Microsoft Graph, Azure</span><span class="sxs-lookup"><span data-stu-id="d7f9f-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="d7f9f-111">이 과정에서 사용 하는 방법을 배우게 됩니다 *Microsoft Graph* 혼합된 현실 응용 프로그램에서 보안 인증을 사용 하 여 Microsoft 계정에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="d7f9f-112">그런 다음 검색 하 고 예약 된 회의 응용 프로그램 인터페이스에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="d7f9f-113">*Microsoft Graph* 는 여러 Microsoft 서비스에 액세스할 수 있도록 Api의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="d7f9f-114">Microsoft에 설명 합니다 Microsoft Graph 관계에 의해 연결 된 리소스의 행렬으로 응용 프로그램을 모든 종류의 연결 된 사용자 데이터에 액세스할 수 있도록 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="d7f9f-115">자세한 내용은 참조는 [Microsoft Graph 페이지](https://developer.microsoft.com/graph)합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="d7f9f-116">개발 응시를 안전 하 게 Microsoft 계정에 로그인 하 라는 메시지가 나타납니다 구를 누른 다음에 사용자가 지시 하는 위치는 앱을 만드는 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="d7f9f-117">계정에 로그인 한 사용자를 하루에 예약 된 회의의 목록을 볼 수 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="d7f9f-118">이 과정을 마치면 다음을 수행 하는 일을 할 수는 HoloLens 응용 프로그램을 혼합된 현실이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="d7f9f-119">사용자 (로그인을 다시 앱으로 다시를 앱 외부로 이동) Microsoft 계정에 로그인 하 라는 메시지를 표시할 개체 탭 탭 제스처를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="d7f9f-120">하루에 예약 된 회의의 목록을 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="d7f9f-121">응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="d7f9f-122">이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="d7f9f-123">혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="d7f9f-124">장치 지원</span><span class="sxs-lookup"><span data-stu-id="d7f9f-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="d7f9f-125">과정</span><span class="sxs-lookup"><span data-stu-id="d7f9f-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="d7f9f-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="d7f9f-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="d7f9f-127"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="d7f9f-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="d7f9f-128">MR 및 311 Azure: Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="d7f9f-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="d7f9f-129">✔️</span><span class="sxs-lookup"><span data-stu-id="d7f9f-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="d7f9f-130">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="d7f9f-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="d7f9f-131">이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="d7f9f-132">또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 7 월) 작성 시점에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="d7f9f-133">내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 나열 된 것 보다 최신 소프트웨어에 맞게 보면 일치 완벽 하 게 됩니다 있지만 문서 아래.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="d7f9f-134">다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="d7f9f-135">PC 개발</span><span class="sxs-lookup"><span data-stu-id="d7f9f-135">A development PC</span></span>
- [<span data-ttu-id="d7f9f-136">Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="d7f9f-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d7f9f-137">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="d7f9f-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d7f9f-138">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="d7f9f-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="d7f9f-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d7f9f-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="d7f9f-140">A [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여</span><span class="sxs-lookup"><span data-stu-id="d7f9f-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="d7f9f-141">Azure 설정 및 Microsoft Graph 데이터 검색에 대 한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="d7f9f-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="d7f9f-142">유효한 **Microsoft 계정** (개인 또는 회사/학교)</span><span class="sxs-lookup"><span data-stu-id="d7f9f-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="d7f9f-143">동일한 Microsoft 계정을 사용 하 여 현재 날짜에 대해 예약 된 몇 회의</span><span class="sxs-lookup"><span data-stu-id="d7f9f-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="d7f9f-144">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="d7f9f-144">Before you start</span></span>

1.  <span data-ttu-id="d7f9f-145">이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).</span><span class="sxs-lookup"><span data-stu-id="d7f9f-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="d7f9f-146">설정 하 고 여 HoloLens를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="d7f9f-147">에 HoloLens 등록 설정을 지원 해야 하는 경우 [HoloLens 설치 문서를 참조 하도록](https://docs.microsoft.com/hololens/hololens-setup)합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="d7f9f-148">(때로는 도움이 각 사용자에 대 한 이러한 작업을 수행) 새 HoloLens 앱 개발을 시작할 때 보정 및 센서 튜닝을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="d7f9f-149">보정에 대 한 도움말을 따라이 [HoloLens 보정 문서 링크](calibration.md#hololens)합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="d7f9f-150">센서 조정에 대 한 도움말을 따라이 [HoloLens 센서 튜닝 문서 링크](sensor-tuning.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="d7f9f-151">1-장 응용 프로그램 등록 포털에서 앱 만들기</span><span class="sxs-lookup"><span data-stu-id="d7f9f-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="d7f9f-152">시작 하려면를 만들어 응용 프로그램에 등록 해야 합니다 **응용 프로그램 등록 포털**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="d7f9f-153">이 챕터에 수도 있습니다. 호출을 수행할 수 있도록 서비스 키 *Microsoft Graph* 계정 콘텐츠를 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="d7f9f-154">로 이동 합니다 [Microsoft 응용 프로그램 등록 포털](https://apps.dev.microsoft.com) 및 Microsoft 계정으로 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="d7f9f-155">로그인 하면, 리디렉션됩니다 하는 **응용 프로그램 등록 포털**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="d7f9f-156">에 **내 응용 프로그램** 섹션에서 단추를 클릭 **앱 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="d7f9f-157">합니다 **응용 프로그램 등록 포털** 여부 이전에 작업을 수행한에 따라 다르게 보일 수 있습니다 *Microsoft Graph*합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="d7f9f-158">아래 스크린샷은 이러한 서로 다른 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="d7f9f-159">응용 프로그램 및 클릭에 대 한 이름 추가 **만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="d7f9f-160">응용 프로그램을 만든 후 응용 프로그램 기본 페이지로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="d7f9f-161">복사 합니다 **응용 프로그램 Id** 안전한 곳에이 값을 메모를 코드에서 곧 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="d7f9f-162">에 **플랫폼** 섹션에, 반드시 **네이티브 응용 프로그램** 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="d7f9f-163">하는 경우 *되지* 클릭할 **플랫폼 추가** 선택한 **네이티브 응용 프로그램**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="d7f9f-164">같은 페이지에 이라는 섹션에서 아래로 스크롤하여 **Microsoft Graph 권한** 응용 프로그램에 대 한 사용 권한을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="d7f9f-165">클릭할 **추가** 옆에 **위임 된 권한**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="d7f9f-166">사용자의 일정에 액세스 하도록 응용 프로그램을 원하므로 확인란 호출 **Calendars.Read** 클릭 **확인**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="d7f9f-167">아래로 스크롤하여을 클릭 합니다 **저장** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="d7f9f-168">저장을 확인할 수는 및에서 로그 아웃 수를 **응용 프로그램 등록 포털**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="d7f9f-169">2 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="d7f9f-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="d7f9f-170">다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="d7f9f-171">오픈 *Unity* 누릅니다 **새로 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="d7f9f-172">Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="d7f9f-173">삽입 **MSGraphMR**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="d7f9f-174">프로젝트 템플릿은 설정 되어 있는지 확인 **3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="d7f9f-175">설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다).</span><span class="sxs-lookup"><span data-stu-id="d7f9f-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="d7f9f-176">그런 다음 클릭 **프로젝트 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="d7f9f-177">Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="d7f9f-178">로 이동 **편집할** > **기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-178">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="d7f9f-179">변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="d7f9f-180">닫기 합니다 **기본 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="d7f9f-181">로 이동 **파일** > **빌드 설정** 선택한 **유니버설 Windows 플랫폼**를 클릭 합니다 **플랫폼 전환** 선택 항목을 적용 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-181">Go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="d7f9f-182">있는 동안 **파일** > **빌드 설정**, 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-182">While still in **File** > **Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="d7f9f-183">**장치를 대상** 로 설정 된 **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="d7f9f-184">**빌드 형식** 로 설정 된 **D3D**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="d7f9f-185">**SDK** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="d7f9f-186">**Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="d7f9f-187">**빌드 및 실행** 로 설정 된 **로컬 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="d7f9f-188">장면 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="d7f9f-189">선택 하 여이 작업을 수행할 **열고 장면 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="d7f9f-190">창 저장 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="d7f9f-191">따라서 모든 미래를 장면에 대 한 새 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="d7f9f-192">선택 된 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="d7f9f-193">새로 만든 열 **장면** 폴더를 선택한 다음는 *파일 이름*: 텍스트 필드에 입력 **MR_ComputerVisionScene**, 클릭 **저장** .</span><span class="sxs-lookup"><span data-stu-id="d7f9f-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="d7f9f-194">주의 내에서 Unity 장면에 저장 해야 합니다 *자산* 폴더를 Unity 프로젝트와 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="d7f9f-195">백그라운드에서 폴더 (및 다른 유사한 폴더)를 만들기 Unity 프로젝트를 구성 하는 일반적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="d7f9f-196">설정에 남아 *빌드 설정*, 지금은 기본값으로 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="d7f9f-197">에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="d7f9f-198">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="d7f9f-199">에 **기타 설정** 탭:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="d7f9f-200">**스크립팅** **런타임 버전** 있어야 **실험적** (.NET 4.6 동등), 편집기를 다시 시작 해야를 트리거하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="d7f9f-201">**백 엔드를 스크립팅** 있어야 **.NET**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="d7f9f-202">**API 호환성 수준** 있어야 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="d7f9f-203">내 합니다 **게시 설정** 탭의 **기능**, 확인:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="d7f9f-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="d7f9f-205">패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 확인 **지원 되는 가상 현실**, 있는지 확인 합니다 **Windows Mixed Reality SDK** 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="d7f9f-206">년대 *빌드 설정*를 *Unity C# 프로젝트* 가 더 이상 회색;이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="d7f9f-207">닫기 합니다 *빌드 설정* 창입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="d7f9f-208">장면 및 프로젝트 저장 (**파일** > **장면 저장 파일** > **프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="d7f9f-208">Save your scene and project (**FILE** > **SAVE SCENES / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="d7f9f-209">3 장-Unity에서 가져오기 라이브러리</span><span class="sxs-lookup"><span data-stu-id="d7f9f-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7f9f-210">건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드로 바로 계속, 다운로드 자유롭게 [311.unitypackage-MR-Azure](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage),으로 프로젝트로 가져올를 [ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)를 계속 진행 한 다음 [5 장](#chapter-5---create-meetingsui-class)합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="d7f9f-211">사용 하도록 *Microsoft Graph* 해야 하는 Unity 내에서 사용 합니다 **Microsoft.Identity.Client** DLL입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="d7f9f-212">그러나 Microsoft Graph SDK를 사용 하는 것, 즉 프로젝트 post-build 편집 Unity 프로젝트를 구성한 후에 NuGet 패키지를 추가 해야 합니다 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="d7f9f-213">Unity를 직접 필요한 Dll을 가져오는 간단한 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="d7f9f-214">플러그 인 가져오기 후 다시 구성 해야 하는 Unity의 알려진된 문제는 현재 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="d7f9f-215">이러한 단계 (4-7이 단원의) 버그가 해결 된 후 필요한 더 이상.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="d7f9f-216">가져오려는 *Microsoft Graph* 고유한 프로젝트로 [MSGraph_LabPlugins.zip 파일 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="d7f9f-217">테스트 된 라이브러리의 버전을 사용 하 여이 패키지를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="d7f9f-218">Unity 프로젝트에 사용자 지정 Dll을 추가 하는 방법에 대 한 자세한 내용을 원한다 [이 링크를 따라](https://docs.unity3d.com/Manual/UsingDLL.html)합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="d7f9f-219">패키지를 가져오려면:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-219">To import the package:</span></span>

1.  <span data-ttu-id="d7f9f-220">Unity를 사용 하 여 Unity 패키지를 추가 합니다 **자산** > **패키지 가져오기** > **Custom Package** 메뉴 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-220">Add the Unity Package to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span> <span data-ttu-id="d7f9f-221">방금 다운로드 한 패키지를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="d7f9f-222">에 **Unity 패키지 가져오기** 표시 되는 상자에서 아래에 있는 포함 하 여 모든 것을 확인 **플러그 인** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="d7f9f-223">클릭 합니다 **가져오기** 프로젝트에 항목을 추가 하려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="d7f9f-224">로 이동 합니다 **MSGraph** 아래에 폴더 **플러그 인** 에 *프로젝트 패널* 이라는 플러그 인을 선택 하 고 **Microsoft.Identity.Client**.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="d7f9f-225">사용 하 여는 *플러그 인* 되도록 선택 하면 **Any 플랫폼** 이 선택 취소 한 다음 확인 **WSAPlayer** 이 선택도 취소 클릭 **적용**.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="d7f9f-226">이 파일이 올바르게 구성 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="d7f9f-227">이러한 플러그 인을 표시만 Unity 편집기에서 사용 되도록 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="d7f9f-228">다양 한 Dll 프로젝트가 유니버설 Windows 응용 프로그램으로 Unity에서 내보낸 후 사용 되는 WSA 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="d7f9f-229">열어야 할 때 다음에 **WSA** 폴더 내에서 합니다 **MSGraph** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="d7f9f-230">방금 구성한 동일한 파일의 복사본을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="d7f9f-231">파일을 선택한 다음 검사기:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="d7f9f-232">되도록 **Any 플랫폼** 는 **unchecked**, 하 고 **만** **WSAPlayer** 는 **체크**.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="d7f9f-233">확인 **SDK** 로 설정 된 **UWP**, 및 **백 엔드 스크립팅** 로 설정 된 **.net**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="d7f9f-234">했는지 **처리 하지** 됩니다 **체크**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="d7f9f-235">**적용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="d7f9f-236">4 장-카메라 설정</span><span class="sxs-lookup"><span data-stu-id="d7f9f-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="d7f9f-237">이 장에서 동안 주 카메라 장면의을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="d7f9f-238">에 *계층 패널*를 선택 합니다 **주 카메라**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="d7f9f-239">선택한 후에의 모든 구성 요소를 볼 수는 합니다 **주 카메라** 에 *검사기* 패널입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="d7f9f-240">합니다 **카메라 개체** 이름은 **주 카메라** (맞춤법 참고!)</span><span class="sxs-lookup"><span data-stu-id="d7f9f-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="d7f9f-241">주 카메라 **태그** 으로 설정 되어 있어야 **MainCamera** (맞춤법 참고!)</span><span class="sxs-lookup"><span data-stu-id="d7f9f-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="d7f9f-242">있는지 확인 합니다 **변환 위치** 로 설정 된 **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="d7f9f-243">설정할 **플래그 지우기** 에 **단색**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="d7f9f-244">설정 된 **배경색** 카메라 구성 요소의 **검정, 알파 0** **(코드를 16 진수: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="d7f9f-245">마지막 개체 구조를 *계층 패널* 아래 이미지에 표시 된 것 처럼 보여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="d7f9f-246">5 장-MeetingsUI 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="d7f9f-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="d7f9f-247">생성 해야 하는 첫 번째 스크립트 **MeetingsUI**를 담당 하는 호스팅 및 (환영 메시지, 지침 및 모임 세부 정보) 응용 프로그램의 UI를 채우는 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="d7f9f-248">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-248">To create this class:</span></span>

1.  <span data-ttu-id="d7f9f-249">마우스 오른쪽 단추로 클릭 합니다 **자산** 폴더에는 *프로젝트 패널*을 선택한 후 **만들기** > **폴더**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-249">Right-click on the **Assets** folder in the *Project Panel*, then select **Create** > **Folder**.</span></span> <span data-ttu-id="d7f9f-250">폴더의 이름을 **스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="d7f9f-251">열기는 **스크립트** 폴더 그런 다음 해당 폴더 내에서 마우스 오른쪽 단추로 클릭 합니다 **만들기**  >   **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-251">Open the **Scripts** folder then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="d7f9f-252">스크립트 이름을 **MeetingsUI 합니다.**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="d7f9f-253">새 두 번 클릭 **MeetingsUI** 스크립트를 사용 하 여 열고 *Visual Studio*합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="d7f9f-254">다음 네임 스페이스를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="d7f9f-255">클래스 내에서 다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-255">Inside the class insert the following variables:</span></span>

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

6.  <span data-ttu-id="d7f9f-256">그런 다음 대체는 **start ()** 메서드 추가 **Awake()** 메서드.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="d7f9f-257">이러한 클래스를 초기화할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-257">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="d7f9f-258">생성을 담당 하는 메서드를 추가 합니다 *회의 UI* 현재 모임 요청 하는 경우 입력:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

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

8. <span data-ttu-id="d7f9f-259">**삭제할** 는 **update ()** 메서드 및 **변경 내용을 저장** Unity를 반환 하기 전에 Visual Studio에서.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="d7f9f-260">-6 장 그래프 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="d7f9f-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="d7f9f-261">만들려면 다음 스크립트를 **그래프** 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="d7f9f-262">이 스크립트는 사용자를 인증 하 고 사용자의 일정에서 현재 날짜에 대 한 예약 된 회의 검색에 대 한 호출을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="d7f9f-263">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-263">To create this class:</span></span>

1.  <span data-ttu-id="d7f9f-264">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="d7f9f-265">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="d7f9f-266">스크립트 이름을 **그래프**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="d7f9f-267">스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="d7f9f-268">다음 네임 스페이스를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-268">Insert the following namespaces:</span></span>

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
    > <span data-ttu-id="d7f9f-269">이 스크립트의 코드 부분 래핑하는 것을 알 수 있습니다 [미리 컴파일 지시문](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), Visual Studio 솔루션을 빌드할 때 라이브러리를 사용 하 여 문제를 방지 하기 위해서입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="d7f9f-270">삭제를 **start ()** 하 고 **update ()** 메서드를 사용 되지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="d7f9f-271">외부 합니다 **그래프** 클래스, 매일 예약 된 회의 나타내는 JSON 개체를 deserialize 하는 데 필요한 다음 개체를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

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

7.  <span data-ttu-id="d7f9f-272">내부를 **그래프** 클래스를 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-272">Inside the **Graph** class, add the following variables:</span></span>

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
    > <span data-ttu-id="d7f9f-273">변경 합니다 **appId** 값을 합니다 **앱 Id** 에서 기록한  **[1 장](#chapter-1---create-your-app-in-the-application-registration-portal), 4 단계**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="d7f9f-274">이 값에 표시 된 것과 동일 해야 합니다 **응용 프로그램 등록 포털** 응용 프로그램 등록 페이지에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="d7f9f-275">내 합니다 **그래프** 클래스, 메서드를 추가 합니다 **SignInAsync()** 및 **AquireTokenAsync()** 는 사용자 로그인 자격 증명을 삽입 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

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

9.  <span data-ttu-id="d7f9f-276">다음 두 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="d7f9f-277">**BuildTodayCalendarEndpoint()** , 빌드 및 예약 된 회의 검색 하는 기간을 지정 하는 URI입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="d7f9f-278">**ListMeetingsAsync()** 에 요청에서 예약 된 회의 *Microsoft Graph*합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

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

10. <span data-ttu-id="d7f9f-279">이제 완료 합니다 **그래프** 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="d7f9f-280">**변경 내용을 저장** Unity를 반환 하기 전에 Visual Studio에서.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="d7f9f-281">7-장 GazeInput 스크립트 만들기</span><span class="sxs-lookup"><span data-stu-id="d7f9f-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="d7f9f-282">이제 만들려는 합니다 **GazeInput**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="d7f9f-283">이 클래스는 처리 하 고 사용자의 게이즈를 사용 하는 추적을 **Raycast** 에서 들어오는 합니다 **주 카메라**, 앞으로 프로젝션 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="d7f9f-284">스크립트를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-284">To create the script:</span></span>

1.  <span data-ttu-id="d7f9f-285">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="d7f9f-286">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="d7f9f-287">스크립트 이름을 **GazeInput**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="d7f9f-288">스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="d7f9f-289">추가 함께 아래 것과 일치 하도록 네임 스페이스 코드를 변경는 ' **\[System.Serializable\]** ' 위의 태그에 **GazeInput** 클래스를 serialize 할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="d7f9f-290">내 합니다 **GazeInput** 클래스를 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-290">Inside the **GazeInput** class, add the following variables:</span></span>

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

6.  <span data-ttu-id="d7f9f-291">추가 된 **CreateCursor()** 장면에서 HoloLens 커서를 만들고에서 메서드를 호출 하는 메서드는 **start ()** 메서드:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

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

7.  <span data-ttu-id="d7f9f-292">다음 방법 Raycast 게이즈를 사용 하도록 설정 하 고 추적 합니다 포커스가 있는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

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

8.  <span data-ttu-id="d7f9f-293">**변경 내용을 저장** Unity를 반환 하기 전에 Visual Studio에서.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="d7f9f-294">8-장 상호 작용 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="d7f9f-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="d7f9f-295">만들려는 해야 합니다 **상호 작용** 담당 하는 스크립트:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="d7f9f-296">처리를 **누릅니다** 상호 작용 및 **카메라 Gaze**, "단추" 장면에서 로그를 사용 하 여 상호 작용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="d7f9f-297">사용자와 상호 작용 하는 장면에서 개체 "단추"에서 로그를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="d7f9f-298">스크립트를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-298">To create the script:</span></span>

1.  <span data-ttu-id="d7f9f-299">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="d7f9f-300">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **Create** >  **C# 스크립트**.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="d7f9f-301">스크립트 이름을 **상호 작용**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="d7f9f-302">스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="d7f9f-303">다음 네임 스페이스를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="d7f9f-304">상속을 변경 합니다 **상호 작용** 에서 클래스 *MonoBehaviour* 에 **GazeInput**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="d7f9f-305">~~공용 클래스 상호 작용 합니다. MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="d7f9f-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="d7f9f-306">내부를 **상호 작용** 클래스에 다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="d7f9f-307">대체는 **시작** 메서드를 '기본' 게이즈 클래스 메서드를 호출 하는 재정의 메서드를 사용 하는 것이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="d7f9f-308">**Start ()** 입력된 인식에 대 한 등록 하 고 로그인을 만드는 클래스를 초기화 하는 경우 호출 될 *단추* 장면에서:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

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

8.  <span data-ttu-id="d7f9f-309">추가 된 **CreateSignInButton()** 로그인을 인스턴스화하는 메서드를 *단추* 장면에서 해당 속성을 설정:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

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

9.  <span data-ttu-id="d7f9f-310">추가 합니다 **GestureRecognizer_Tapped()** 메서드 수에 대 한 응답을 *탭* 사용자 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

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

10. <span data-ttu-id="d7f9f-311">**삭제할** 는 **update ()** 메서드를 차례로 **변경 내용을 저장** Unity를 반환 하기 전에 Visual Studio에서.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="d7f9f-312">9 장-스크립트 참조 설정</span><span class="sxs-lookup"><span data-stu-id="d7f9f-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="d7f9f-313">이 챕터에 배치 해야 합니다 **상호 작용** 스크립트에 **주 카메라**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="d7f9f-314">해당 스크립트는 필요할 수 있는 다른 스크립트를 배치 하는 것을 처리 한 다음 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="d7f9f-315">**스크립트** 폴더에는 *프로젝트 패널*, 스크립트를 끌어 **상호 작용** 에 **주 카메라** 개체, 다음 그림과 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="d7f9f-316">10 장-태그 설정</span><span class="sxs-lookup"><span data-stu-id="d7f9f-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="d7f9f-317">코드를 응시 처리 태그를 사용 하 게 **SignInButton** 개체를 식별 하는 사용자가 상호 작용할에 로그인 하 *Microsoft Graph*합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="d7f9f-318">태그를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="d7f9f-318">To create the Tag:</span></span>

1.  <span data-ttu-id="d7f9f-319">Unity 편집기에서 클릭 합니다 **주 카메라** 에 *계층 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="d7f9f-320">에 *검사기 패널* 클릭 합니다 **MainCamera** *태그* 드롭다운 목록을 열지 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="d7f9f-321">클릭 **태그를 추가 하는 중...**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="d7f9f-322">클릭 합니다 **+** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="d7f9f-323">태그 이름으로 작성할 **SignInButton** 고 저장을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="d7f9f-324">11 장-UWP로 Unity 프로젝트 빌드</span><span class="sxs-lookup"><span data-stu-id="d7f9f-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="d7f9f-325">이 프로젝트의 Unity 섹션에 필요한 모든 항목이 이제 완료 되 면 Unity에서 작성 하는 시간 이므로 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="d7f9f-326">이동할 *빌드 설정* (**파일*>*설정** 빌드).</span><span class="sxs-lookup"><span data-stu-id="d7f9f-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="d7f9f-327">경우에 눈금 **Unity C\# 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="d7f9f-328">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-328">Click **Build**.</span></span> <span data-ttu-id="d7f9f-329">Unity가 시작 됩니다는 **파일 탐색기** 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="d7f9f-330">해당 폴더를 이제 만들고 이름을 **앱**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="d7f9f-331">사용 하 여 다음 합니다 **앱** 폴더를 선택, 클릭 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="d7f9f-332">Unity 프로젝트를 빌드할 예정 된 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="d7f9f-333">한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="d7f9f-334">12-장 HoloLens에 배포</span><span class="sxs-lookup"><span data-stu-id="d7f9f-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="d7f9f-335">HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="d7f9f-336">(배포에 대 한 원격), 여 HoloLens의 IP 주소를 사용 해야 하 고 확인에 HoloLens가 **개발자 모드입니다.**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="d7f9f-337">가상 하드 디스크 파일에 대한 중요 정보를 제공하려면</span><span class="sxs-lookup"><span data-stu-id="d7f9f-337">To do this:</span></span>

    1.  <span data-ttu-id="d7f9f-338">에 HoloLens, 착용 하는 동안 엽니다는 **설정을**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="d7f9f-339">로 이동 **네트워크 및 인터넷** > **Wi-fi** > **고급 옵션**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="d7f9f-340">참고 합니다 **IPv4** 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="d7f9f-341">다음으로 다시 이동할 **설정을**, 한 다음 **업데이트 및 보안** > **개발자를 위한**</span><span class="sxs-lookup"><span data-stu-id="d7f9f-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="d7f9f-342">설정할 **에서 개발자 모드가**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="d7f9f-343">새 Unity 빌드에 이동 (합니다 **앱** 폴더) 사용 하 여 솔루션 파일을 엽니다 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="d7f9f-344">에 **솔루션 구성** 선택 **디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="d7f9f-345">에 **솔루션 플랫폼**를 선택 **x86, 원격 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="d7f9f-346">삽입 하 라는 메시지가 표시 됩니다는 **IP 주소** 원격 장치 (여 HoloLens,이 경우 둔).</span><span class="sxs-lookup"><span data-stu-id="d7f9f-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="d7f9f-347">로 이동 **빌드할** 메뉴를 클릭 **솔루션 배포** 을 사이드 로드에 HoloLens에 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="d7f9f-348">앱에 HoloLens 시작할 준비가에 설치 된 앱 목록에 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="d7f9f-349">Microsoft Graph HoloLens 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="d7f9f-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="d7f9f-350">축 하 읽고 사용자 일정 데이터를 표시 하는 Microsoft Graph를 활용 하는 혼합된 현실 앱 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="d7f9f-351">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="d7f9f-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="d7f9f-352">연습 1</span><span class="sxs-lookup"><span data-stu-id="d7f9f-352">Exercise 1</span></span>

<span data-ttu-id="d7f9f-353">Microsoft Graph를 사용 하 여 사용자에 대 한 다른 정보를 표시 하려면</span><span class="sxs-lookup"><span data-stu-id="d7f9f-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="d7f9f-354">사용자 전자 메일 프로필 사진 / 전화 번호</span><span class="sxs-lookup"><span data-stu-id="d7f9f-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="d7f9f-355">연습 1</span><span class="sxs-lookup"><span data-stu-id="d7f9f-355">Exercise 1</span></span>

<span data-ttu-id="d7f9f-356">Microsoft Graph UI 이동할 음성 제어를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7f9f-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
