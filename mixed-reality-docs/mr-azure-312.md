---
title: MR 및 Azure 312-Bot 통합
description: 만들고 Microsoft Bot Framework v4를 사용 하 여 봇, 배포 하는 방법을 알아보려면이 과정을 완료 하 고 혼합된 현실 응용 프로그램에서 통신 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, 컴퓨터 비전, hololens, vr 몰입도 microsoft bot framework v4, web app 봇, bot framework, microsoft bot
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604982"
---
>[!NOTE]
><span data-ttu-id="dcca0-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="dcca0-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="dcca0-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="dcca0-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="dcca0-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="dcca0-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="dcca0-110">MR 및 Azure 312: 봇 통합</span><span class="sxs-lookup"><span data-stu-id="dcca0-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="dcca0-111">이 과정을 만들고 Microsoft Bot Framework V4를 사용 하는 봇 배포 및 Windows Mixed Reality 응용 프로그램을 통해 통신 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="dcca0-112">합니다 **Microsoft Bot Framework V4** 개발자 도구를 확장 하 고 확장 가능한 봇 빌드를 제공 하도록 설계 Api 집합을 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="dcca0-113">자세한 내용은 참조는 [Microsoft Bot Framework 페이지](https://dev.botframework.com/) 또는 [V4 Git 리포지토리](https://github.com/Microsoft/botbuilder-dotnet/wiki)합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="dcca0-114">이 과정을 완료 한 후 다음을 수행 하는 일을 할 수 있는 Windows Mixed Reality 응용 프로그램을 빌드한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="dcca0-115">사용 하 여는 **탭 제스처** 봇에 사용자 음성에 대 한 수신 대기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="dcca0-116">사용자가 내용이 포함 되어 있었습니다, 봇 응답을 제공 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="dcca0-117">봇 회신 Unity 장면에서 봇, 가까이 배치한 텍스트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="dcca0-118">응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="dcca0-119">이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="dcca0-120">혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="dcca0-121">장치 지원</span><span class="sxs-lookup"><span data-stu-id="dcca0-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="dcca0-122">과정</span><span class="sxs-lookup"><span data-stu-id="dcca0-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="dcca0-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="dcca0-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="dcca0-124"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="dcca0-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="dcca0-125">MR 및 Azure 312: 봇 통합</span><span class="sxs-lookup"><span data-stu-id="dcca0-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="dcca0-126">✔️</span><span class="sxs-lookup"><span data-stu-id="dcca0-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="dcca0-127">✔️</span><span class="sxs-lookup"><span data-stu-id="dcca0-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="dcca0-128">이 과정 HoloLens에 주로 중점을 두고, 하는 동안 Windows Mixed Reality 몰입 형 (VR) 헤드셋을이 과정에서 배운 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="dcca0-129">몰입 형 (VR) 헤드셋에 액세스할 수 있는 카메라 없기 때문에 PC에 연결 하는 외부 카메라를 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="dcca0-130">과정을 따라가려면 정보 몰입 형 (VR) 헤드셋을 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dcca0-131">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="dcca0-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="dcca0-132">이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="dcca0-133">또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 7 월) 작성 시점에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="dcca0-134">내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 나열 된 것 보다 최신 소프트웨어에 맞게 보면 일치 완벽 하 게 됩니다 있지만 문서 아래.</span><span class="sxs-lookup"><span data-stu-id="dcca0-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="dcca0-135">다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="dcca0-136">개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용</span><span class="sxs-lookup"><span data-stu-id="dcca0-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="dcca0-137">Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="dcca0-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="dcca0-138">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="dcca0-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="dcca0-139">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="dcca0-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="dcca0-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="dcca0-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="dcca0-141">A [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md) 하거나 [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여</span><span class="sxs-lookup"><span data-stu-id="dcca0-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="dcca0-142">Azure Bot 검색 및 Azure에 대 한 인터넷 액세스.</span><span class="sxs-lookup"><span data-stu-id="dcca0-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="dcca0-143">자세한 내용은 [이 링크를 따르세요](https://dev.botframework.com/)합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="dcca0-144">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="dcca0-144">Before you start</span></span>

1.  <span data-ttu-id="dcca0-145">이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).</span><span class="sxs-lookup"><span data-stu-id="dcca0-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="dcca0-146">설정 하 고 여 HoloLens를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="dcca0-147">에 HoloLens 등록 설정을 지원 해야 하는 경우 [HoloLens 설치 문서를 참조 하도록](https://docs.microsoft.com/hololens/hololens-setup)합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="dcca0-148">(때로는 도움이 각 사용자에 대 한 이러한 작업을 수행) 새 HoloLens 앱 개발을 시작할 때 보정 및 센서 튜닝을 수행 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="dcca0-149">보정에 대 한 도움말을 따라이 [HoloLens 보정 문서 링크](calibration.md#hololens)합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="dcca0-150">센서 조정에 대 한 도움말을 따라이 [HoloLens 센서 튜닝 문서 링크](sensor-tuning.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="dcca0-151">1 장-봇 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="dcca0-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="dcca0-152">첫 번째 단계 봇을 로컬 ASP.Net Core 웹 응용 프로그램을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="dcca0-153">완료 하 고 테스트 후 Azure 포털에 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="dcca0-154">Visual Studio를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-154">Open Visual Studio.</span></span> <span data-ttu-id="dcca0-155">새 프로젝트를 만듭니다 **ASP NET Core 웹 응용 프로그램** (있습니다 아래 하위 섹션에서는.NET Core) 프로젝트 형식으로 호출 **MyBot**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="dcca0-156">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-156">Click **OK**.</span></span>

2.  <span data-ttu-id="dcca0-157">선택 표시 되는 창의 **빈**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="dcca0-158">또한 대상 설정 되어 있는지 확인 **ASP NET Core 2.0** 인증으로 설정 됩니다 **인증 안 함**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="dcca0-159">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-159">Click **OK**.</span></span>  

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="dcca0-161">솔루션이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-161">The solution will now open.</span></span> <span data-ttu-id="dcca0-162">솔루션을 마우스 오른쪽 단추로 클릭 **Mybot** 에 **솔루션 탐색기** 클릭 **솔루션용 NuGet 패키지 관리**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="dcca0-164">에 **찾아보기** 탭에서 검색할 **Microsoft.Bot.Builder.Integration.AspNet.Core** (했는지 **시험판 포함** 확인).</span><span class="sxs-lookup"><span data-stu-id="dcca0-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="dcca0-165">패키지 버전을 선택 **4.0.1-preview**, 프로젝트 상자 눈금.</span><span class="sxs-lookup"><span data-stu-id="dcca0-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="dcca0-166">클릭 **설치**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-166">Then click on **Install**.</span></span> <span data-ttu-id="dcca0-167">이제에 필요한 라이브러리를 설치 합니다 **Bot Framework v4**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="dcca0-168">NuGet 페이지를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-168">Close the NuGet page.</span></span>

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="dcca0-170">마우스 오른쪽 단추로 클릭 하 *프로젝트*, **MyBot**에서 합니다 **솔루션 탐색기** 을 클릭할 **추가** **|** **클래스**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="dcca0-172">클래스의 이름을 **MyBot** 를 클릭 **추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="dcca0-174">라는 다른 클래스를 만들려면 이전 점이 반복 **ConversationContext**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="dcca0-175">마우스 오른쪽 단추로 클릭 **wwwroot** 에 **솔루션 탐색기** 클릭 **추가** **|** **새항목**.</span><span class="sxs-lookup"><span data-stu-id="dcca0-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="dcca0-176">선택 **HTML 페이지** (알 수 있을 것 하위 섹션에서는 웹에서).</span><span class="sxs-lookup"><span data-stu-id="dcca0-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="dcca0-177">파일 이름을 **default.html**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-177">Name the file **default.html**.</span></span> <span data-ttu-id="dcca0-178">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-178">Click **Add**.</span></span>

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="dcca0-180">클래스의 목록은 개체 / 합니다 **솔루션 탐색기** 아래 이미지와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![봇 응용 프로그램 만들기](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="dcca0-182">두 번 클릭 합니다 **ConversationContext** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="dcca0-183">이 클래스는 봇 대화 컨텍스트를 유지 하기 위해 사용 하는 변수를 보유 하는 일을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="dcca0-184">때문에 이러한 대화 컨텍스트 값은이 클래스의 인스턴스에서 유지 관리의 모든 인스턴스를 **MyBot** 클래스 활동 수신 될 때마다 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="dcca0-185">클래스에 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-185">Add the following code to the class:</span></span>

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. <span data-ttu-id="dcca0-186">두 번 클릭 합니다 **MyBot** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="dcca0-187">이 클래스는 고객 으로부터 받는 모든 활동에 의해 호출 처리기를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="dcca0-188">이 클래스에서 봇와 고객 간의 대화를 빌드하는 데 사용 하는 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="dcca0-189">앞에서 설명한 대로이 클래스의 인스턴스는 활동 수신 될 때마다 초기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="dcca0-190">이 클래스에 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-190">Add the following code to this class:</span></span>

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. <span data-ttu-id="dcca0-191">두 번 클릭 합니다 **시작** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="dcca0-192">이 클래스는 봇을 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-192">This class will initialize the bot.</span></span> <span data-ttu-id="dcca0-193">클래스에 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-193">Add the following code to the class:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. <span data-ttu-id="dcca0-194">엽니다는 **프로그램** 클래스 파일 및 해당 코드를 다음과 같이 같은지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. <span data-ttu-id="dcca0-195">로를 위해 변경 내용을 저장 해야 **파일** > **모두 저장**, Visual Studio의 맨 위에 있는 도구 모음에서.</span><span class="sxs-lookup"><span data-stu-id="dcca0-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="dcca0-196">-2 장 Azure Bot Service 만들기</span><span class="sxs-lookup"><span data-stu-id="dcca0-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="dcca0-197">인스턴스를 게시 해야 하는 코드 봇에 빌드 합니다 *Web App 봇* Azure Portal에서 서비스 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="dcca0-198">이 장에서 만들 azure Bot Service를 구성 하 고 다음 코드를 게시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="dcca0-199">먼저 Azure Portal에 로그인 (https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="dcca0-200">Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="dcca0-201">클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="dcca0-202">일단 로그인 하면 클릭할 **리소스 만들기** 왼쪽 위에서 모서리 및 검색 *Web App 봇*를 클릭 하 고 **Enter**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="dcca0-204">새 페이지에 대 한 설명을 제공 합니다는 *Web App 봇* 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="dcca0-205">선택이 페이지의 왼쪽 아래에 있는 합니다 **만들기** 이 연결 서비스를 만들려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="dcca0-207">클릭 한 후 **만들기**:</span><span class="sxs-lookup"><span data-stu-id="dcca0-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="dcca0-208">원하는 삽입 **이름을** 이 서비스 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="dcca0-209">선택 된 **구독**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="dcca0-210">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="dcca0-211">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="dcca0-212">좋습니다 일반적인 리소스 그룹에서 (예: 이러한 교육 과정) 예: 단일 프로젝트와 연결 된 Azure 서비스를 모두 유지).</span><span class="sxs-lookup"><span data-stu-id="dcca0-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="dcca0-213">추가 하려는 경우 Azure 리소스 그룹에 대 한 [이 링크를 따르세요.](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="dcca0-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="dcca0-214">(새 리소스 그룹을 만들면) 하는 경우 리소스 그룹의 위치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="dcca0-215">위치는 응용 프로그램은 실행할 지역의 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="dcca0-216">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="dcca0-217">선택 된 **가격 책정 계층** 첫 번째 경우, 적절 한 시간 만들기는 *Web App 봇* 서비스, 무료 계층 (F0 라는)를 사용할 수 있어야</span><span class="sxs-lookup"><span data-stu-id="dcca0-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="dcca0-218">**앱 이름** 방금에 남겨둘 수와 동일 합니다 *봇 이름*합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="dcca0-219">유지 된 *Bot 템플릿을* 으로 **기본 (C#)** 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="dcca0-220">*App service 계획/위치* 계정에 대해 자동으로 채워진 었어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="dcca0-221">설정 합니다 **Azure Storage** 봇을 호스트할 사용 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="dcca0-222">없다면 이미, 여기서 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="dcca0-223">이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="dcca0-224">만들기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-224">Click Create.</span></span>
 
        ![Azure Bot Service 만들기](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="dcca0-226">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="dcca0-227">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="dcca0-229">새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="dcca0-231">클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="dcca0-232">새 Azure 서비스에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="dcca0-234">라는 기능을 설치 해야 하는 시점 **직접 회선** 클라이언트 응용 프로그램이이 Bot 서비스와 통신할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="dcca0-235">클릭할 **채널**, 그런 다음는 **추천된 채널 추가** 섹션을 클릭 **구성 직접 회선 채널**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="dcca0-237">이 페이지에서 찾을 수 있습니다 합니다 **비밀 키** 클라이언트 앱 봇으로 인증할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="dcca0-238">클릭 합니다 **표시** 단추 및 프로젝트에서 나중에이 필요 하므로 하나 표시 키의 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="dcca0-240">– 3 장 봇을 Azure Web App 봇 서비스에 게시</span><span class="sxs-lookup"><span data-stu-id="dcca0-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="dcca0-241">이제 서비스 준비 되 면 새로 만든된 웹 앱 봇 서비스에 이전에 작성 하는 봇 코드를 게시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="dcca0-242">봇 솔루션에 변경 될 때마다 Azure 서비스에 봇을 게시 해야 / c o d.</span><span class="sxs-lookup"><span data-stu-id="dcca0-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="dcca0-243">이전에 만든 Visual Studio 솔루션으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="dcca0-244">마우스 오른쪽 단추로 클릭 하 **MyBot** 프로젝트를 합니다 **솔루션 탐색기**, 클릭 **게시**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![봇 Azure Web App 봇 서비스에 게시](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="dcca0-246">에 *게시 대상 선택* 페이지에서 **App Service**, 한 다음 **기존 항목 선택**, 마지막 클릭 **프로필 만들기** (해야 할 수 있습니다 옆에 있는 드롭다운 화살표를 클릭 합니다 *게시* 단추에 표시 되지 않는 경우).</span><span class="sxs-lookup"><span data-stu-id="dcca0-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![봇 Azure Web App 봇 서비스에 게시](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="dcca0-248">하면 로그인 하지 않은 아직 Microsoft 계정으로, 다음 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="dcca0-249">에 **게시** 동일 하 게 설정 해야 하는 것이 보면 페이지 **구독** 에 사용 하는 합니다 *Web App 봇* 서비스 만들기.</span><span class="sxs-lookup"><span data-stu-id="dcca0-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="dcca0-250">설정한 합니다 **보기** 으로 **리소스 그룹** 드롭다운 폴더 구조 목록에서 선택 합니다 **리소스 그룹** 이전에 만든 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="dcca0-251">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-251">Click **OK**.</span></span> 

    ![봇 Azure Web App 봇 서비스에 게시](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="dcca0-253">클릭 합니다 **게시** 단추 및 봇에 게시 될 때까지 기다립니다 (몇 분 정도 걸릴 수 있습니다).</span><span class="sxs-lookup"><span data-stu-id="dcca0-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![봇 Azure Web App 봇 서비스에 게시](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="dcca0-255">4 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="dcca0-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="dcca0-256">다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="dcca0-257">오픈 *Unity* 누릅니다 **새로 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-257">Open *Unity* and click **New**.</span></span> 

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="dcca0-259">이제 Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="dcca0-260">삽입 **Hololens Bot**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="dcca0-261">프로젝트 템플릿은 설정 되어 있는지 확인 **3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="dcca0-262">설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다).</span><span class="sxs-lookup"><span data-stu-id="dcca0-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="dcca0-263">그런 다음 클릭 **프로젝트 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-263">Then, click **Create project**.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="dcca0-265">Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="dcca0-266">로 이동 **편집 > 기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="dcca0-267">변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="dcca0-268">닫기 합니다 **기본 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-268">Close the **Preferences** window.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="dcca0-270">이동한 다음 **파일 > 빌드 설정** 선택한 **유니버설 Windows 플랫폼**를 클릭 합니다 **플랫폼 전환** 선택 항목을 적용 하려면 단추.</span><span class="sxs-lookup"><span data-stu-id="dcca0-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="dcca0-272">여전히 **파일 > 빌드 설정** 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="dcca0-273">**장치를 대상** 로 설정 된 **Hololens**</span><span class="sxs-lookup"><span data-stu-id="dcca0-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="dcca0-274">몰입 형 헤드셋, 설정 **대상 장치** 하 *모든 장치*합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="dcca0-275">**빌드 형식** 로 설정 된 **D3D**</span><span class="sxs-lookup"><span data-stu-id="dcca0-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="dcca0-276">**SDK** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="dcca0-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="dcca0-277">**Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="dcca0-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="dcca0-278">**빌드 및 실행** 로 설정 된 **로컬 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="dcca0-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="dcca0-279">장면 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="dcca0-280">선택 하 여이 작업을 수행할 **열고 장면 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="dcca0-281">창 저장 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-281">A save window will appear.</span></span>
        
            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="dcca0-283">새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Unity 프로젝트 설정](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="dcca0-285">새로 만든 열 **장면** 폴더를 선택한 다음는 *파일 이름*: 텍스트 필드에 입력 **BotScene**, 클릭 **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="dcca0-287">설정에 남아 **빌드 설정**, 지금은 기본값으로 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="dcca0-288">에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한.</span><span class="sxs-lookup"><span data-stu-id="dcca0-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="dcca0-290">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="dcca0-291">에 **기타 설정** 탭:</span><span class="sxs-lookup"><span data-stu-id="dcca0-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="dcca0-292">**스크립팅 런타임 버전** 있어야 **실험적 (NET 4.6 동등)**; 편집기를 다시 시작이를 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="dcca0-293">**백 엔드를 스크립팅** 있어야 **.NET**</span><span class="sxs-lookup"><span data-stu-id="dcca0-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="dcca0-294">**API 호환성 수준** 있어야 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="dcca0-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="dcca0-296">내 합니다 **게시 설정** 탭의 **기능**, 확인:</span><span class="sxs-lookup"><span data-stu-id="dcca0-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="dcca0-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="dcca0-297">**InternetClient**</span></span>
        - <span data-ttu-id="dcca0-298">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="dcca0-298">**Microphone**</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="dcca0-300">패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="dcca0-302">년대 *빌드 설정* _Unity C#_  프로젝트는 더 이상 회색으로;이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="dcca0-303">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="dcca0-304">장면 및 프로젝트 저장 (**파일 > 저장 장면 파일 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="dcca0-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="dcca0-305">5 장-카메라 설정</span><span class="sxs-lookup"><span data-stu-id="dcca0-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dcca0-306">건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드로 바로 계속, 다운로드 자유롭게 [Azure MR-312 Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)을 로프로젝트로가져올[ **사용자 지정 패키지**](https://docs.unity3d.com/Manual/AssetPackages.html)를 선택한 다음에서 계속 [7 장](#chapter-7-–-create-the-botobjects-class)합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-7-–-create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="dcca0-307">에 *계층 패널*를 선택 합니다 **주 카메라**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="dcca0-308">선택한 후에의 모든 구성 요소를 볼 수는 합니다 **주 카메라** 에 *검사기 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="dcca0-309">합니다 **카메라 개체** 이름은 **주 카메라** (맞춤법을 확인 합니다.)</span><span class="sxs-lookup"><span data-stu-id="dcca0-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="dcca0-310">주 카메라 **태그** 으로 설정 되어 있어야 **MainCamera** (맞춤법을 확인 합니다.)</span><span class="sxs-lookup"><span data-stu-id="dcca0-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="dcca0-311">있는지 확인 합니다 **변환 위치** 로 설정 된 **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="dcca0-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="dcca0-312">설정 **플래그 지우기** 하 **단색**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="dcca0-313">설정 된 **백그라운드** 카메라 구성 요소의 색 **검정, 알파 0 (16 진수 코드: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="dcca0-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![카메라 설정](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="dcca0-315">6 장-Newtonsoft 라이브러리 가져오기</span><span class="sxs-lookup"><span data-stu-id="dcca0-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="dcca0-316">봇 서비스에 보내고 받은 개체를 serialize 및 deserialize 하는 데 다운로드 해야 합니다 **Newtonsoft** 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="dcca0-317">찾을 수 있습니다는 [호환 되는 버전 여기 잘못 Unity 폴더 구조를 사용 하 여 이미 구성](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="dcca0-318">Newtonsoft 라이브러리를 프로젝트로 가져오는이 과정을 통해 제공 된 Unity 패키지를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="dcca0-319">추가 된 *.unitypackage* 사용 하 여 Unity에는 **자산** > **패키지 가져오기** > **사용자 지정 패키지** 메뉴 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Newtonsoft 라이브러리 가져오기](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="dcca0-321">에 **Unity 패키지 가져오기** 표시 되는 상자에서 아래에 있는 포함 하 여 모든 것을 확인 **플러그 인** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Newtonsoft 라이브러리 가져오기](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="dcca0-323">클릭 합니다 **가져오기** 프로젝트에 항목을 추가 하려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="dcca0-324">로 이동 합니다 **Newtonsoft** 아래에 폴더 **플러그 인** 프로젝트 보기를 Newtonsoft 플러그 인을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="dcca0-325">선택한 Newtonsoft 플러그 인을 사용 하 여 있는지를 확인 **Any 플랫폼** 는 **unchecked**, 한지 확인 합니다 **WSAPlayer** 이기도 **검사 되지 않은**, 누른 **적용**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="dcca0-326">이 파일이 올바르게 구성 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="dcca0-327">이러한 플러그 인을 표시만 Unity 편집기에서 사용 되도록 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="dcca0-328">Unity에서 프로젝트를 내보낸 후 사용 되는 WSA 폴더에서 다른 집합을 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="dcca0-329">열어야 할 때 다음에 **WSA** 폴더 내에서 합니다 **Newtonsoft** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="dcca0-330">방금 구성한 동일한 파일의 복사본을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="dcca0-331">파일을 선택 하 고 [관리자]에서 확인 하는</span><span class="sxs-lookup"><span data-stu-id="dcca0-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="dcca0-332">**모든 플랫폼** 는 **선택 취소 되어 있음**</span><span class="sxs-lookup"><span data-stu-id="dcca0-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="dcca0-333">**만** **WSAPlayer** 는 **확인**</span><span class="sxs-lookup"><span data-stu-id="dcca0-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="dcca0-334">**처리 하지 않음** 는 **확인**</span><span class="sxs-lookup"><span data-stu-id="dcca0-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="dcca0-335">7 장 –는 BotTag 만들기</span><span class="sxs-lookup"><span data-stu-id="dcca0-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="dcca0-336">새 **태그** 라는 개체 **BotTag**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="dcca0-337">주 카메라 장면에서 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="dcca0-338">태그에 대 한 드롭다운 검사기 창에서 메뉴를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="dcca0-339">클릭할 **태그를 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-339">Click on **Add Tag**.</span></span>

    ![카메라 설정](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="dcca0-341">클릭 합니다 **+** 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-341">Click on the **+** symbol.</span></span> <span data-ttu-id="dcca0-342">새 이름을 **태그** 으로 **BotTag**하십시오 *저장*합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![카메라 설정](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="dcca0-344">**하지** 적용 된 **BotTag** 주 카메라입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="dcca0-345">실수로 수행한 경우이 변경 해야 태그를 주 카메라 *MainCamera*합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="dcca0-346">8 장-BotObjects 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="dcca0-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="dcca0-347">생성 해야 하는 첫 번째 스크립트는 **BotObjects** 동일한 스크립트 내 일련의 다른 클래스 개체에 저장할 수 있도록 만들고 장면에서 다른 스크립트에서 액세스 하는 빈 클래스 클래스.</span><span class="sxs-lookup"><span data-stu-id="dcca0-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="dcca0-348">이 클래스의 생성은 순수 하 게 아키텍처, 이러한 개체는이 과정의 뒷부분에서 만들 봇 스크립트 대신 호스트 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="dcca0-349">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="dcca0-349">To create this class:</span></span> 

1.  <span data-ttu-id="dcca0-350">마우스 오른쪽 단추로 클릭 합니다 *프로젝트 패널*, 한 다음 **만들기 > 폴더**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="dcca0-351">폴더의 이름을 **스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-351">Name the folder **Scripts**.</span></span> 

    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="dcca0-353">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="dcca0-354">해당 폴더를 마우스 오른쪽 단추로 선택 내에서 다음 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="dcca0-355">스크립트 이름을 **BotObjects**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="dcca0-356">새 두 번 클릭 **BotObjects** 스크립트를 사용 하 여 열고 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="dcca0-357">스크립트의 콘텐츠를 삭제 하 고 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-357">Delete the content of the script and replace it with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  <span data-ttu-id="dcca0-358">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="dcca0-359">9 장-GazeInput 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="dcca0-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="dcca0-360">다음 클래스를 만드는 것은 **GazeInput** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="dcca0-361">이 클래스는 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-361">This class is responsible for:</span></span>

- <span data-ttu-id="dcca0-362">커서를 만들기가 나타내는 합니다 *gaze* 플레이어의 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="dcca0-363">선수의 게이즈 발생 하는 개체를 검색 하 고 검색 된 개체에 대 한 참조를 보유 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="dcca0-364">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="dcca0-364">To create this class:</span></span> 

1.  <span data-ttu-id="dcca0-365">로 이동 합니다 **스크립트** 이전에 만든 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="dcca0-366">폴더를 마우스 오른쪽 단추로 클릭 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="dcca0-367">스크립트를 호출할 **GazeInput**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="dcca0-368">새 두 번 클릭 **GazeInput** 스크립트를 사용 하 여 열고 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="dcca0-369">클래스 이름에 바로 위에 다음 줄을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="dcca0-370">다음 내에서 다음 변수를 추가 합니다 **GazeInput** 위의 클래스는 **start ()** 메서드:</span><span class="sxs-lookup"><span data-stu-id="dcca0-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

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

6.  <span data-ttu-id="dcca0-371">에 대 한 코드 **start ()** 메서드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="dcca0-372">이 클래스를 초기화할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-372">This will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="dcca0-373">인스턴스화를 응시 커서를 설정 하는 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  <span data-ttu-id="dcca0-374">주 카메라에서 Raycast 설정 및는 추적할 현재 포커스가 있는 개체는 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

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
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
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
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  <span data-ttu-id="dcca0-375">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="dcca0-376">10 장-Bot 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="dcca0-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="dcca0-377">이제 만들려는 하려는 스크립트를 호출 **Bot**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="dcca0-378">응용 프로그램의 핵심 클래스를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="dcca0-379">Web App 봇 자격 증명</span><span class="sxs-lookup"><span data-stu-id="dcca0-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="dcca0-380">사용자 음성 명령에서 수집 하는 메서드</span><span class="sxs-lookup"><span data-stu-id="dcca0-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="dcca0-381">웹 응용 프로그램 봇을 사용 하 여 대화를 시작 하는 데 필요한 메서드</span><span class="sxs-lookup"><span data-stu-id="dcca0-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="dcca0-382">웹 응용 프로그램 봇을에 메시지를 보내는 데 필요한 메서드</span><span class="sxs-lookup"><span data-stu-id="dcca0-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="dcca0-383">봇 서비스에 메시지를 보내도록 합니다 **SendMessageToBot()** 코 루틴에서 사용자가 보낸 데이터로 Bot Framework에서 인식 하는 개체인 활동을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="dcca0-384">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="dcca0-384">To create this class:</span></span> 

1. <span data-ttu-id="dcca0-385">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="dcca0-386">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="dcca0-387">스크립트 이름을 **Bot**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="dcca0-388">Visual Studio를 사용 하 여 열에 새 스크립트를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="dcca0-389">네임 스페이스의 맨 위에 있는 다음과 같을 수를 업데이트 합니다 **Bot** 클래스:</span><span class="sxs-lookup"><span data-stu-id="dcca0-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="dcca0-390">내부를 **Bot** 클래스에 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-390">Inside the **Bot** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > <span data-ttu-id="dcca0-391">삽입 해야 하 **Bot 비밀 키** 에 **botSecret** 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="dcca0-392">가 기록한 사용자 **Bot 비밀 키** 이 과정의 시작 부분에  **[2 장](#chapter-2---create-the-azure-bot-service), 10 단계**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="dcca0-393">에 대 한 코드 **Awake()** 하 고 **start ()** 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. <span data-ttu-id="dcca0-394">음성 캡처를 시작 및 종료 하는 경우 음성 라이브러리에서 호출 되는 두 명의 처리기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="dcca0-395">합니다 *DictationRecognizer* 말하기 중지할 때 사용자 음성 캡처 자동으로 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. <span data-ttu-id="dcca0-396">다음 처리기는 사용자 음성 입력의 결과 수집 하 고 웹 앱 봇 서비스에 메시지를 보내는 코 루틴을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. <span data-ttu-id="dcca0-397">봇에 사용 하 여 대화를 시작 하려면 다음 코 루틴 일 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="dcca0-398">대화 호출이 완료 되 면 호출을 확인할 수 있습니다 합니다 **SendMessageToCoroutine()** 는 일련의 빈 메시지로 Bot Service를 전송할 수 있도록 활동을 설정 하는 매개 변수를 전달 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="dcca0-399">Bot Service와 관련 된 대화를 시작 하려면 프롬프트에 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. <span data-ttu-id="dcca0-400">Bot Service를 전송할 수 있도록 활동을 빌드한 다음 코 루틴 일 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. <span data-ttu-id="dcca0-401">봇 서비스에 활동을 보낸 후 응답을 요청 하려면 다음 코 루틴 일 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. <span data-ttu-id="dcca0-402">이 클래스에 추가할 마지막 메서드는 장면에서 메시지를 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="dcca0-403">Unity 편집기 콘솔 누락 하는 방법에 대 한 오류가 표시 될 수 있습니다 합니다 **SceneOrganiser** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="dcca0-404">자습서의 뒷부분에 나오는이 클래스를 만들기는이 메시지는 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="dcca0-405">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="dcca0-406">11 장-상호 작용 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="dcca0-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="dcca0-407">클래스를 만드는 것은 이제 라고 **상호 작용**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="dcca0-408">이 클래스는 사용자 로부터 HoloLens 탭 입력 검색할 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="dcca0-409">확인 하는 동안 사용자가 누를 경우는 *Bot* 봇 장면에 개체는 음성 입력을 수신 하도록 준비, 봇 개체는 색을 변경 **빨간색** 음성 입력에 대 한 수신 대기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="dcca0-410">이 클래스에서 상속 된 **GazeInput** 클래스를 참조할 수는 **start ()** 메서드 및 변수를 사용 하 여 표시 되는 클래스에서 **기본**입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="dcca0-411">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="dcca0-411">To create this class:</span></span>

1.  <span data-ttu-id="dcca0-412">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="dcca0-413">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="dcca0-414">스크립트 이름을 **상호 작용**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="dcca0-415">Visual Studio를 사용 하 여 열에 새 스크립트를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="dcca0-416">네임 스페이스 및 클래스 상속의 맨 위에 있는 다음과 같을 수를 업데이트 합니다 **상호 작용** 클래스:</span><span class="sxs-lookup"><span data-stu-id="dcca0-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="dcca0-417">내 합니다 **상호 작용** 클래스에 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="dcca0-418">그런 다음 추가 합니다 **start ()** 메서드:</span><span class="sxs-lookup"><span data-stu-id="dcca0-418">Then add the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="dcca0-419">사용자가 HoloLens 카메라 앞에 탭 제스처를 수행할 때 트리거되는 처리기 추가</span><span class="sxs-lookup"><span data-stu-id="dcca0-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. <span data-ttu-id="dcca0-420">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="dcca0-421">12 장-SceneOrganiser 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="dcca0-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="dcca0-422">이 랩에 필요한 마지막 클래스 라고 **SceneOrganiser**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="dcca0-423">이 클래스는 장면에서 해당 개체를 만들고 주 카메라에 구성 요소 및 스크립트를 추가 하 여 장면 프로그래밍 방식으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="dcca0-424">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="dcca0-424">To create this class:</span></span>

1.  <span data-ttu-id="dcca0-425">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="dcca0-426">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="dcca0-427">스크립트 이름을 **SceneOrganiser**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="dcca0-428">Visual Studio를 사용 하 여 열에 새 스크립트를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="dcca0-429">내 합니다 **SceneOrganiser** 클래스에 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  <span data-ttu-id="dcca0-430">다음 추가 합니다 **Awake()** 하 고 **start ()** 메서드:</span><span class="sxs-lookup"><span data-stu-id="dcca0-430">Then add the **Awake()** and **Start()** methods:</span></span>

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  <span data-ttu-id="dcca0-431">장면에서 봇 개체를 만들고 매개 변수 및 구성 요소 설정에 다음 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  <span data-ttu-id="dcca0-432">봇의 응답을 나타내는 장면에서 UI 개체를 만드는 다음 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  <span data-ttu-id="dcca0-433">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="dcca0-434">Unity 편집기에서 끌어 합니다 **SceneOrganiser** 주 카메라를 Scripts 폴더에서 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="dcca0-435">장면 Organiser 구성 요소 아래 그림과에서 같이 이제 주 카메라 개체에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="dcca0-437">13 장-빌드하기 전에</span><span class="sxs-lookup"><span data-stu-id="dcca0-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="dcca0-438">응용 프로그램의 철저 한 테스트를 수행 하려면 해야 테스트용으로 로드 하 여 HoloLens에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="dcca0-439">를 수행 하기 전에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="dcca0-440">에 언급 된 모든 설정 합니다 [ **4 장** ](#Chapter-4-–-Set-up-the-unity-project) 올바르게 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-440">All the settings mentioned in the [**Chapter 4**](#Chapter-4-–-Set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="dcca0-441">스크립트 **SceneOrganiser** 에 연결할 때 합니다 **주 카메라** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="dcca0-442">에 **Bot** 클래스를 넣었습니다 선택 되어 있는지 확인 합니다에 **봇 비밀 키** 에 **botSecret** 변수.</span><span class="sxs-lookup"><span data-stu-id="dcca0-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="dcca0-443">14 장-빌드 및는 HoloLens에 테스트용으로 로드</span><span class="sxs-lookup"><span data-stu-id="dcca0-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="dcca0-444">이 프로젝트의 Unity 섹션에 필요한 모든 항목이 이제 완료 되 면 Unity에서 작성 하는 시간 이므로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="dcca0-445">이동할 **빌드 설정**, **파일 > 빌드 설정...** .</span><span class="sxs-lookup"><span data-stu-id="dcca0-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="dcca0-446">**빌드 설정** 창에서 클릭 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Unity에서 앱 빌드](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="dcca0-448">경우에 눈금 **Unity C# 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="dcca0-449">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-449">Click **Build**.</span></span> <span data-ttu-id="dcca0-450">Unity가 시작 됩니다는 **파일 탐색기** 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="dcca0-451">해당 폴더를 이제 만들고 이름을 **앱**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="dcca0-452">사용 하 여 다음 합니다 **앱** 폴더를 선택, 클릭 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="dcca0-453">Unity 프로젝트를 빌드할 예정 된 **앱** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="dcca0-454">한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="dcca0-455">HoloLens에 장 15-배포</span><span class="sxs-lookup"><span data-stu-id="dcca0-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="dcca0-456">HoloLens에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="dcca0-457">(배포에 대 한 원격), 여 HoloLens의 IP 주소를 사용 해야 하 고 중인에 HoloLens 되도록 **개발자 모드**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="dcca0-458">가상 하드 디스크 파일에 대한 중요 정보를 제공하려면</span><span class="sxs-lookup"><span data-stu-id="dcca0-458">To do this:</span></span>

    1. <span data-ttu-id="dcca0-459">에 HoloLens, 착용 하는 동안 엽니다는 **설정을**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="dcca0-460">로 **네트워크 및 인터넷 > Wi-fi > 고급 옵션**</span><span class="sxs-lookup"><span data-stu-id="dcca0-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="dcca0-461">참고 합니다 **IPv4** 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="dcca0-462">다음으로 다시 이동할 **설정을**, 다음 **업데이트 및 보안 > 개발자 용**</span><span class="sxs-lookup"><span data-stu-id="dcca0-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="dcca0-463">개발자 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="dcca0-464">새 Unity 빌드에 이동 (합니다 **앱** 폴더) 사용 하 여 솔루션 파일을 엽니다 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="dcca0-465">에 **솔루션 구성** 선택 **디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="dcca0-466">에 **솔루션 플랫폼**를 선택 **x86**를 **원격 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="dcca0-468">로 이동 합니다 **빌드 메뉴** 클릭 **솔루션 배포**, 응용 프로그램에 HoloLens 테스트용으로 로드 하려면.</span><span class="sxs-lookup"><span data-stu-id="dcca0-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="dcca0-469">앱에 HoloLens 시작할 준비가에 설치 된 앱 목록에 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="dcca0-470">몰입 형 헤드셋을 배포 하려면 설정 합니다 **솔루션 플랫폼** 를 *로컬 컴퓨터*, 설정 및를 **구성** 에 *디버그*, 를사용하여*x86* 으로 **플랫폼**합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="dcca0-471">로컬 배포 후 컴퓨터를 사용 하 여는 **빌드 메뉴**을 선택 하면 *솔루션 배포*합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="dcca0-472">16 장-는 HoloLens에서 응용 프로그램을 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="dcca0-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="dcca0-473">응용 프로그램을 시작한 후 사용자 앞에 파란색 구도 봇을 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="dcca0-474">사용 된 **탭 제스처** 대화를 시작 하 여 구를에서 gazing 되는 동안.</span><span class="sxs-lookup"><span data-stu-id="dcca0-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="dcca0-475">대화를 시작 될 때까지 기다립니다 (UI는 메시지가 표시 되는 경우).</span><span class="sxs-lookup"><span data-stu-id="dcca0-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="dcca0-476">봇에서 소개 메시지를 받게 되 면 탭 다시 봇 빨간색 설정 하 고 의견을 듣기를 시작 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="dcca0-477">통신을 중지 하면 응용 프로그램 봇에 메시지를 송신할 후 UI에 표시 되는 응답을 즉시 받습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="dcca0-478">(해야 될 때마다 메시지 발신자를 누릅니다) 봇을 더 많은 메시지를 보낼 프로세스를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="dcca0-479">이 대화 봇 정보 (이름)을 유지할 수는 방법을 보여 줍니다 (예: 누적 되는 항목) 알려진된 정보를 제공 하는 동안.</span><span class="sxs-lookup"><span data-stu-id="dcca0-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="dcca0-480">봇에 몇 가지 질문 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="dcca0-481">완성 된 Web App 봇 (v4) 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="dcca0-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="dcca0-482">축 하의 Azure Web App 봇, Microsoft Bot Framework v4를 활용 하는 혼합된 현실 앱 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![최종 제품](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="dcca0-484">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="dcca0-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="dcca0-485">연습 1</span><span class="sxs-lookup"><span data-stu-id="dcca0-485">Exercise 1</span></span>

<span data-ttu-id="dcca0-486">이 랩에서 대화 구조 매우 기본적인 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="dcca0-487">Microsoft LUIS를 사용 하 여 봇에 자연어 이해 기능.</span><span class="sxs-lookup"><span data-stu-id="dcca0-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="dcca0-488">연습 2</span><span class="sxs-lookup"><span data-stu-id="dcca0-488">Exercise 2</span></span>

<span data-ttu-id="dcca0-489">이 예제에서는 대화를 종료 하 고 새 암호를 다시 시작 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="dcca0-490">봇 기능 완료를 위해 대화에는 클로저를 구현 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="dcca0-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
