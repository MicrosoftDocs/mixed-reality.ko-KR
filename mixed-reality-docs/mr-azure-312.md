---
title: MR 및 Azure 312-봇 통합
description: 이 과정을 완료 하 여 Microsoft 봇 Framework v4를 사용 하는 bot을 만들어 배포 하 고 혼합 현실 응용 프로그램에서 통신 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 컴퓨터 비전, hololens, 모던, vr, microsoft 봇 framework v4, 웹 앱 봇, 봇 프레임 워크, microsoft 봇
ms.openlocfilehash: dc428f01a8333bf812fe03c59a46b7a2fa20df83
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438489"
---
>[!NOTE]
><span data-ttu-id="0cdbd-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0cdbd-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0cdbd-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0cdbd-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0cdbd-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0cdbd-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="0cdbd-110">MR 및 Azure 312: 봇 통합</span><span class="sxs-lookup"><span data-stu-id="0cdbd-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="0cdbd-111">이 과정에서는 Microsoft 봇 Framework V4를 사용 하 여 봇을 만들어 배포 하 고 Windows Mixed Reality 응용 프로그램을 통해 통신 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="0cdbd-112">**Microsoft Bot Framework V4** 는 개발자에 게 확장 가능 하 고 확장 가능한 봇 응용 프로그램을 빌드할 수 있는 도구를 제공 하도록 설계 된 api 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="0cdbd-113">자세한 내용은 [Microsoft 봇 Framework 페이지](https://dev.botframework.com/) 또는 [V4 Git 리포지토리](https://github.com/Microsoft/botbuilder-dotnet/wiki)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="0cdbd-114">이 과정을 완료 한 후 다음을 수행할 수 있는 Windows Mixed Reality 응용 프로그램을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="0cdbd-115">**탭 제스처** 를 사용 하 여 사용자 의견을 수신 하는 봇을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="0cdbd-116">사용자가 무언가를 말하면 봇은 응답을 제공 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="0cdbd-117">Unity 장면에서 봇 근처에 있는 텍스트로 인공 지능 회신을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="0cdbd-118">응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="0cdbd-119">이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="0cdbd-120">이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="0cdbd-121">장치 지원</span><span class="sxs-lookup"><span data-stu-id="0cdbd-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0cdbd-122">과정</span><span class="sxs-lookup"><span data-stu-id="0cdbd-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0cdbd-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0cdbd-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0cdbd-124"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="0cdbd-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="0cdbd-125">MR 및 Azure 312: 봇 통합</span><span class="sxs-lookup"><span data-stu-id="0cdbd-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="0cdbd-126">✔️</span><span class="sxs-lookup"><span data-stu-id="0cdbd-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="0cdbd-127">✔️</span><span class="sxs-lookup"><span data-stu-id="0cdbd-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="0cdbd-128">이 과정에서 주로 HoloLens에 초점을 맞춘 반면,이 과정에서 배운 내용을 Windows Mixed Reality 모던 (VR) 헤드셋에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="0cdbd-129">모던 (VR) 헤드셋은 액세스할 수 있는 카메라를 포함 하지 않으므로 PC에 연결 된 외부 카메라가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="0cdbd-130">이 과정을 진행 하면서 모던 (VR) 헤드셋을 지원 하기 위해 사용 해야 하는 변경 내용에 대 한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0cdbd-131">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="0cdbd-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="0cdbd-132">이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="0cdbd-133">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (7 월 2018)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="0cdbd-134">[도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="0cdbd-135">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="0cdbd-136">모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC</span><span class="sxs-lookup"><span data-stu-id="0cdbd-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="0cdbd-137">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="0cdbd-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0cdbd-138">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="0cdbd-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0cdbd-139">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="0cdbd-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0cdbd-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0cdbd-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="0cdbd-141">개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="0cdbd-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="0cdbd-142">Azure 및 Azure Bot 검색을 위한 인터넷 액세스.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="0cdbd-143">자세한 내용은 [다음 링크](https://dev.botframework.com/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="0cdbd-144">시작하기 전 확인 사항</span><span class="sxs-lookup"><span data-stu-id="0cdbd-144">Before you start</span></span>

1.  <span data-ttu-id="0cdbd-145">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="0cdbd-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="0cdbd-146">HoloLens를 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="0cdbd-147">HoloLens를 설정 하는 데 지원이 필요한 경우 [hololens 설정 문서를 방문](https://docs.microsoft.com/hololens/hololens-setup)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="0cdbd-148">새 HoloLens 앱 개발을 시작할 때 보정 및 센서 조정을 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음).</span><span class="sxs-lookup"><span data-stu-id="0cdbd-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="0cdbd-149">보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에](calibration.md#hololens-2)대 한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="0cdbd-150">센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](sensor-tuning.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="0cdbd-151">1 장-Bot 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="0cdbd-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="0cdbd-152">첫 번째 단계는 bot을 로컬 ASP.Net Core 웹 응용 프로그램으로 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="0cdbd-153">이를 완료 하 고 테스트 한 후에는 Azure Portal에 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="0cdbd-154">Visual Studio를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-154">Open Visual Studio.</span></span> <span data-ttu-id="0cdbd-155">새 프로젝트를 만들고, 프로젝트 형식으로 **ASP NET Core 웹 응용 프로그램** 을 선택 하 고 (하위 섹션 .net core 아래에서 찾을 수 있습니다.) **mybot**를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="0cdbd-156">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-156">Click **OK**.</span></span>

2.  <span data-ttu-id="0cdbd-157">표시 되는 창에서 **비어 있음**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="0cdbd-158">또한 대상이 **ASP NET Core 2.0** 로 설정 되 고 인증이 **인증 없음**으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="0cdbd-159">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-159">Click **OK**.</span></span>  

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="0cdbd-161">이제 솔루션이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-161">The solution will now open.</span></span> <span data-ttu-id="0cdbd-162">**솔루션 탐색기** 에서 솔루션 **mybot** 을 마우스 오른쪽 단추로 클릭 하 고 **솔루션용 NuGet 패키지 관리**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="0cdbd-164">**찾아보기** 탭에서 **Microsoft** . m a. a. m a. i.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="0cdbd-165">패키지 버전 **4.0.1-미리 보기**를 선택 하 고 프로젝트 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="0cdbd-166">그런 다음 **설치**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-166">Then click on **Install**.</span></span> <span data-ttu-id="0cdbd-167">이제 **Bot Framework v4**에 필요한 라이브러리를 설치 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="0cdbd-168">NuGet 페이지를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-168">Close the NuGet page.</span></span>

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="0cdbd-170">**솔루션 탐색기** 에서 *프로젝트* **mybot**을 마우스 오른쪽 단추로 클릭 하 고 **|** **클래스** **추가** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="0cdbd-172">클래스 이름을 **Mybot** 로 설정 하 고 **추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="0cdbd-174">이전 지점을 반복 하 여 **ConversationContext**라는 다른 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="0cdbd-175">**솔루션 탐색기** 에서 **wwwroot** 를 마우스 오른쪽 단추로 클릭 하 고 **|** **새 항목** **추가** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="0cdbd-176">**HTML 페이지** 를 선택 합니다 .이 페이지는 하위 섹션 웹에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="0cdbd-177">파일 이름을 **html.actionlink**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-177">Name the file **default.html**.</span></span> <span data-ttu-id="0cdbd-178">**추가**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-178">Click **Add**.</span></span>

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="0cdbd-180">**솔루션 탐색기** 의 클래스/개체 목록은 아래 이미지와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![Bot 응용 프로그램 만들기](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="0cdbd-182">**ConversationContext** 클래스를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="0cdbd-183">이 클래스는 봇에서 대화의 컨텍스트를 유지 하는 데 사용 하는 변수를 보유 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="0cdbd-184">이러한 대화 컨텍스트 값은이 클래스의 인스턴스에서 유지 관리 됩니다. **Mybot** 클래스의 인스턴스는 활동이 수신 될 때마다 새로 고쳐집니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="0cdbd-185">클래스에 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-185">Add the following code to the class:</span></span>

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

11. <span data-ttu-id="0cdbd-186">**Mybot** 클래스를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="0cdbd-187">이 클래스는 고객의 들어오는 활동에 의해 호출 되는 처리기를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="0cdbd-188">이 클래스에서는 봇과 고객 간에 대화를 빌드하는 데 사용 되는 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="0cdbd-189">앞에서 설명한 것 처럼이 클래스의 인스턴스는 활동이 수신 될 때마다 초기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="0cdbd-190">이 클래스에 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-190">Add the following code to this class:</span></span>

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

12. <span data-ttu-id="0cdbd-191">**Startup** 클래스를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="0cdbd-192">이 클래스는 bot를 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-192">This class will initialize the bot.</span></span> <span data-ttu-id="0cdbd-193">클래스에 다음 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-193">Add the following code to the class:</span></span>

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

13. <span data-ttu-id="0cdbd-194">**프로그램** 클래스 파일을 열고 코드의 코드가 다음과 같은지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

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

14. <span data-ttu-id="0cdbd-195">변경 내용을 저장 하려면 Visual Studio 맨 위에 있는 도구 모음에서 **파일** > **모두 저장**으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="0cdbd-196">2 장-Azure Bot Service 만들기</span><span class="sxs-lookup"><span data-stu-id="0cdbd-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="0cdbd-197">이제 bot에 대 한 코드를 빌드 했으므로 Azure Portal에서 *웹 앱 봇* 서비스의 인스턴스에 게시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="0cdbd-198">이 장에서는 Azure에서 봇 서비스를 만들고 구성 하는 방법을 보여 주고 코드를 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="0cdbd-199">먼저 Azure Portal (https://portal.azure.com) 에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="0cdbd-200">아직 Azure 계정이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="0cdbd-201">교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="0cdbd-202">로그인 되 면 왼쪽 위 모서리에서 **리소스 만들기** 를 클릭 하 고 *웹 앱 봇*을 검색 한 다음 **Enter 키**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="0cdbd-204">새 페이지에는 *웹 앱 봇* 서비스에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="0cdbd-205">이 페이지의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="0cdbd-207">**만들기**를 클릭 하면 다음을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="0cdbd-208">이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="0cdbd-209">**구독**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="0cdbd-210">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="0cdbd-211">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0cdbd-212">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="0cdbd-213">Azure 리소스 그룹에 대 한 자세한 내용은 [다음 링크](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="0cdbd-214">새 리소스 그룹을 만드는 경우 리소스 그룹의 위치를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="0cdbd-215">위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="0cdbd-216">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="0cdbd-217">적절 한 **가격 책정 계층** 을 선택 합니다. *웹 앱 봇* 서비스를 처음 만드는 경우 무료 계층 (명명 된 F0)을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="0cdbd-218">**앱 이름은** *봇 이름과*동일 하 게 남겨둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="0cdbd-219">*Bot 템플릿을* **Basic (C#)** 으로 그대로 둡니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="0cdbd-220">계정에 대해 *App service 계획/위치* 를 자동으로 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="0cdbd-221">Bot을 호스트 하는 데 사용할 **Azure Storage** 를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="0cdbd-222">아직 없는 경우 여기에서 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="0cdbd-223">또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="0cdbd-224">만들기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-224">Click Create.</span></span>
 
        ![Azure Bot Service 만들기](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="0cdbd-226">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="0cdbd-227">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="0cdbd-229">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="0cdbd-231">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="0cdbd-232">새 Azure 서비스 인스턴스로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="0cdbd-234">이 시점에서 클라이언트 응용 프로그램이이 Bot 서비스와 통신할 수 있도록 **Direct Line** 이라는 기능을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="0cdbd-235">**채널**을 클릭 한 다음, **추천 채널 추가** 섹션에서 **직접 선 채널 구성**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="0cdbd-237">이 페이지에서는 클라이언트 앱에서 봇으로 인증할 수 있는 **비밀 키** 를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="0cdbd-238">**표시** 단추를 클릭 하 고, 프로젝트에서 나중에 필요 하므로 표시 된 키 중 하나를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="0cdbd-240">3 장 – Azure 웹 앱 봇 서비스에 봇 게시</span><span class="sxs-lookup"><span data-stu-id="0cdbd-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="0cdbd-241">이제 서비스가 준비 되었으므로 새로 만든 웹 앱 봇 서비스에 이전에 빌드한 봇 코드를 게시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="0cdbd-242">Bot 솔루션/코드를 변경할 때마다 Azure 서비스에 봇을 게시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="0cdbd-243">이전에 만든 Visual Studio 솔루션으로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="0cdbd-244">**솔루션 탐색기**에서 **mybot** 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **게시**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![Azure 웹 앱 봇 서비스에 봇 게시](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="0cdbd-246">*게시 대상 선택* 페이지에서 **App Service**를 클릭 한 다음 기존 프로필 만들기를 **선택**합니다. 마지막으로 **프로필 만들기** 를 클릭 합니다 (표시 되지 않는 경우 *게시* 단추와 함께 드롭다운 화살표를 클릭 해야 할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="0cdbd-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![Azure 웹 앱 봇 서비스에 봇 게시](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="0cdbd-248">Microsoft 계정에 아직 로그인 하지 않은 경우 여기에서 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="0cdbd-249">**게시** 페이지에서 *웹 앱 봇* 서비스 생성에 사용한 것과 동일한 **구독** 을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="0cdbd-250">그런 다음 **보기** 를 **리소스 그룹** 으로 설정 하 고 드롭다운 폴더 구조에서 이전에 만든 **리소스 그룹** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="0cdbd-251">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-251">Click **OK**.</span></span> 

    ![Azure 웹 앱 봇 서비스에 봇 게시](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="0cdbd-253">이제 **게시** 단추를 클릭 하 고 봇이 게시 될 때까지 기다립니다 (몇 분 정도 걸릴 수 있음).</span><span class="sxs-lookup"><span data-stu-id="0cdbd-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![Azure 웹 앱 봇 서비스에 봇 게시](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="0cdbd-255">4 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="0cdbd-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="0cdbd-256">다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="0cdbd-257">*Unity* 를 열고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-257">Open *Unity* and click **New**.</span></span> 

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="0cdbd-259">이제 Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="0cdbd-260">**HoloLens 봇**을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-260">Insert **HoloLens Bot**.</span></span> <span data-ttu-id="0cdbd-261">프로젝트 템플릿이 **3d**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="0cdbd-262">위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="0cdbd-263">그런 다음 **프로젝트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-263">Then, click **Create project**.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="0cdbd-265">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="0cdbd-266">**> 기본 설정 편집** 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="0cdbd-267">**외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="0cdbd-268">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-268">Close the **Preferences** window.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="0cdbd-270">그런 다음 **파일 > 빌드 설정** 으로 이동 하 고 **유니버설 Windows 플랫폼**을 선택한 후 **플랫폼 전환** 단추를 클릭 하 여 선택 항목을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="0cdbd-272">아직 **파일 > 빌드 설정을** 사용 하 고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="0cdbd-273">**대상 장치가** **HoloLens** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="0cdbd-273">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="0cdbd-274">모던 헤드셋의 경우 **대상 장치** 를 *모든 장치로*설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="0cdbd-275">**빌드 형식이** **D3D** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="0cdbd-276">**SDK** 가 **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="0cdbd-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="0cdbd-277">**Visual Studio 버전이** **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="0cdbd-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="0cdbd-278">**빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="0cdbd-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="0cdbd-279">장면을 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="0cdbd-280">이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="0cdbd-281">저장 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-281">A save window will appear.</span></span>
        
            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="0cdbd-283">이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을**로 지정한 다음</span><span class="sxs-lookup"><span data-stu-id="0cdbd-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Unity 프로젝트 설정](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="0cdbd-285">새로 만든 **장면** 폴더를 연 다음 *파일 이름*: 텍스트 필드에 **BotScene**를 입력 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="0cdbd-287">**빌드 설정**의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="0cdbd-288">*빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Unity 프로젝트 설정](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="0cdbd-290">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="0cdbd-291">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="0cdbd-292">**Scripting Runtime 버전** 은 **실험적 (NET 4.6 동급)** 이어야 합니다. 이를 변경 하려면 편집기를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="0cdbd-293">**Scripting 백엔드** 는 **.net** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="0cdbd-294">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="0cdbd-296">**게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="0cdbd-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="0cdbd-297">**InternetClient**</span></span>
        - <span data-ttu-id="0cdbd-298">**마이크로**</span><span class="sxs-lookup"><span data-stu-id="0cdbd-298">**Microphone**</span></span>

            ![Unity 프로젝트 설정](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="0cdbd-300">패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Unity 프로젝트 설정](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="0cdbd-302">*빌드 설정* 으로 돌아가서 _Unity C#_  프로젝트가 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="0cdbd-303">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="0cdbd-304">장면 및 프로젝트를 저장 합니다 (**파일 > 장면/파일 저장 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="0cdbd-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="0cdbd-305">5 장-카메라 설정</span><span class="sxs-lookup"><span data-stu-id="0cdbd-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0cdbd-306">이 과정의 *Unity 설정* 구성 요소를 건너뛰고 계속 해 서 코드를 계속 사용 하려면 [312이 unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)를 다운로드 하 고 프로젝트에 [**사용자 지정 패키지로**](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 다음을 [계속 진행 합니다. 7 장](#chapter-8--create-the-botobjects-class).</span><span class="sxs-lookup"><span data-stu-id="0cdbd-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-8--create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="0cdbd-307">*계층 패널*에서 **기본 카메라**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="0cdbd-308">선택한 후에는 *검사기 패널*에서 **주 카메라** 의 모든 구성 요소를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="0cdbd-309">**카메라 개체** 의 이름을 **주 카메라로** 지정 해야 합니다 (철자 확인).</span><span class="sxs-lookup"><span data-stu-id="0cdbd-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="0cdbd-310">기본 카메라 **태그** 는 **maincamera** 로 설정 되어야 합니다 (철자 확인).</span><span class="sxs-lookup"><span data-stu-id="0cdbd-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="0cdbd-311">**변환 위치가** **0, 0, 0** 으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="0cdbd-312">**Clear Flags** 를 **Solid 색**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="0cdbd-313">카메라 구성 요소의 **배경색** 을 **검은색, 알파 0 (16 진수 코드: #00000000)** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![카메라 설정](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="0cdbd-315">6 장 – Newtonsoft.json 라이브러리 가져오기</span><span class="sxs-lookup"><span data-stu-id="0cdbd-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="0cdbd-316">받아서 봇 서비스로 전송 되는 개체를 deserialize 하 고 serialize 할 수 있도록 **newtonsoft.json** 라이브러리를 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="0cdbd-317">[여기에서 올바른 Unity 폴더 구조를 사용 하 여 이미 구성 된 호환 버전](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="0cdbd-318">Newtonsoft.json 라이브러리를 프로젝트로 가져오려면이 과정에서 제공 되는 Unity 패키지를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="0cdbd-319"> >  > **패키지 가져오기** **사용자 지정 패키지** 메뉴 옵션의 **자산** 을 사용 하 여 *unitypackage* 을 Unity에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Newtonsoft.json 라이브러리 가져오기](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="0cdbd-321">표시 되는 **Unity 패키지 가져오기** 상자에서 **플러그 인** 을 포함 하 여 모든 항목을 선택 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Newtonsoft.json 라이브러리 가져오기](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="0cdbd-323">**가져오기** 단추를 클릭 하 여 프로젝트에 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="0cdbd-324">프로젝트 뷰에서 **플러그** 인의 **newtonsoft.json** 폴더로 이동 하 고 newtonsoft.json 플러그 인을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="0cdbd-325">Newtonsoft.json 플러그 인을 선택한 상태에서 **모든 플랫폼이** 선택 **취소**되어 있는지 확인 한 다음 **WSAPlayer** 도 **선택 취소**되어 있는지 확인 하 고 **적용**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="0cdbd-326">이는 파일이 올바르게 구성 되었는지 확인 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="0cdbd-327">이러한 플러그 인을 표시 하면 Unity 편집기 에서만 사용 하도록 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="0cdbd-328">WSA 폴더에는 프로젝트를 Unity에서 내보낸 후에 사용 되는 다른 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="0cdbd-329">다음으로 **newtonsoft.json** 폴더 내에서 **WSA** 폴더를 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="0cdbd-330">방금 구성한 파일의 복사본이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="0cdbd-331">파일을 선택 하 고 검사기에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="0cdbd-332">**모든 플랫폼이** **선택 취소** 되어 있음</span><span class="sxs-lookup"><span data-stu-id="0cdbd-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="0cdbd-333">**WSAPlayer** 만 **선택** 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="0cdbd-334">**Dont 프로세스** 를 **선택 했습니다** .</span><span class="sxs-lookup"><span data-stu-id="0cdbd-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="0cdbd-335">7 장-BotTag 만들기</span><span class="sxs-lookup"><span data-stu-id="0cdbd-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="0cdbd-336">**BotTag**라는 새 **Tag** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="0cdbd-337">장면에서 주 카메라를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="0cdbd-338">검사기 패널에서 태그 드롭다운 메뉴를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="0cdbd-339">**태그 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-339">Click on **Add Tag**.</span></span>

    ![카메라 설정](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="0cdbd-341">**+** 기호를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-341">Click on the **+** symbol.</span></span> <span data-ttu-id="0cdbd-342">새 **태그** 의 이름을 **BotTag**, *Save*로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![카메라 설정](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="0cdbd-344">**BotTag** 를 기본 카메라에 적용 **하지 마십시오** .</span><span class="sxs-lookup"><span data-stu-id="0cdbd-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="0cdbd-345">실수로이 작업을 수행한 경우 주 카메라 태그를 *Maincamera*로 다시 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="0cdbd-346">8 장 – BotObjects 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="0cdbd-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="0cdbd-347">만들어야 하는 첫 번째 스크립트는 **BotObjects** 클래스입니다 .이 클래스는 일련의 다른 클래스 개체를 동일한 스크립트 내에 저장 하 고 장면의 다른 스크립트에서 액세스할 수 있도록 만들어지는 빈 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="0cdbd-348">이 클래스를 만드는 것은 전적으로 아키텍처를 선택 하는 것입니다. 이러한 개체는이 과정의 뒷부분에서 만들 Bot 스크립트에서 호스팅될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="0cdbd-349">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="0cdbd-349">To create this class:</span></span> 

1.  <span data-ttu-id="0cdbd-350">*프로젝트 패널*을 마우스 오른쪽 단추로 클릭 하 고 **> 폴더를 만듭니다**.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="0cdbd-351">폴더 이름을 **스크립트**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-351">Name the folder **Scripts**.</span></span> 

    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="0cdbd-353">**Scripts** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="0cdbd-354">그런 다음 해당 폴더 내에서를 마우스 오른쪽 단추로 클릭 하 고  **C# > 스크립트 만들기**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="0cdbd-355">스크립트 이름을 **BotObjects**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="0cdbd-356">새 **BotObjects** 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="0cdbd-357">스크립트의 내용을 삭제 하 고 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-357">Delete the content of the script and replace it with the following code:</span></span>

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

6.  <span data-ttu-id="0cdbd-358">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="0cdbd-359">9 장 – GazeInput 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="0cdbd-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="0cdbd-360">만들려는 다음 클래스는 **GazeInput** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="0cdbd-361">이 클래스는 다음을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-361">This class is responsible for:</span></span>

- <span data-ttu-id="0cdbd-362">플레이어의 *응시* 를 나타내는 커서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="0cdbd-363">플레이어를 응시 하 고 검색 된 개체에 대 한 참조를 보유 하는 개체를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="0cdbd-364">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="0cdbd-364">To create this class:</span></span> 

1.  <span data-ttu-id="0cdbd-365">이전에 만든 **스크립트** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="0cdbd-366">폴더 내부를 마우스 오른쪽 단추로 클릭 하 **> C# 스크립트를 만듭니다**.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="0cdbd-367">**GazeInput**스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="0cdbd-368">새 **GazeInput** 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="0cdbd-369">클래스 이름 바로 위에 다음 줄을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="0cdbd-370">그런 다음 **GazeInput** 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="0cdbd-371">**Start ()** 메서드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="0cdbd-372">클래스가 초기화 될 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-372">This will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="0cdbd-373">응시 커서를 인스턴스화하고 설정 하는 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

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

8.  <span data-ttu-id="0cdbd-374">기본 카메라에서 Raycast를 설정 하 고 현재 포커스가 있는 개체를 추적 하는 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

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
 
9.  <span data-ttu-id="0cdbd-375">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="0cdbd-376">10 장 – Bot 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="0cdbd-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="0cdbd-377">지금 만들려는 스크립트를 **봇**이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="0cdbd-378">이 클래스는 응용 프로그램의 핵심 클래스 이며 다음을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="0cdbd-379">웹 앱 봇 자격 증명</span><span class="sxs-lookup"><span data-stu-id="0cdbd-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="0cdbd-380">사용자 음성 명령을 수집 하는 메서드</span><span class="sxs-lookup"><span data-stu-id="0cdbd-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="0cdbd-381">웹 앱 봇에서 대화를 시작 하는 데 필요한 방법</span><span class="sxs-lookup"><span data-stu-id="0cdbd-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="0cdbd-382">웹 앱 봇에 메시지를 보내는 데 필요한 방법</span><span class="sxs-lookup"><span data-stu-id="0cdbd-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="0cdbd-383">Bot Service로 메시지를 보내기 위해 **SendMessageToBot ()** 코 루틴는 사용자가 보낸 데이터로 bot Framework에서 인식 하는 개체인 활동을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="0cdbd-384">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="0cdbd-384">To create this class:</span></span> 

1. <span data-ttu-id="0cdbd-385">**Scripts** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="0cdbd-386">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> C# 스크립트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="0cdbd-387">스크립트의 이름을 **Bot**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="0cdbd-388">새 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="0cdbd-389">**Bot** 클래스의 위쪽에서 다음과 같이 네임 스페이스를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="0cdbd-390">**Bot** 클래스 내에서 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-390">Inside the **Bot** class add the following variables:</span></span>

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
    > <span data-ttu-id="0cdbd-391">**BotSecret** 변수에 **봇 비밀 키** 를 삽입 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="0cdbd-392">이 과정의 시작 부분에 있는  **[2 장](#chapter-2---create-the-azure-bot-service), 10 단계**에서 **봇 비밀 키** 를 적어 두는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="0cdbd-393">이제 해제 **()** 및 **Start ()** 에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

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

8. <span data-ttu-id="0cdbd-394">음성 캡처가 시작 되 고 끝날 때 음성 라이브러리에서 호출 하는 두 처리기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="0cdbd-395">*DictationRecognizer* 사용자가 말하기를 중지 하면 자동으로 사용자 음성 캡처가 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

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

1. <span data-ttu-id="0cdbd-396">다음 처리기는 사용자 음성 입력의 결과를 수집 하 고 웹 앱 봇 서비스에 메시지를 전송 하는 것을 담당 하는 코 루틴을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

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

10. <span data-ttu-id="0cdbd-397">다음 코 루틴는 Bot를 사용 하 여 대화를 시작 하기 위해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="0cdbd-398">대화 호출이 완료 되 면 활동을 **SendMessageToCoroutine ()** 를 호출 하는 일련의 매개 변수를 전달 하 여 해당 활동을 빈 메시지로 전달 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="0cdbd-399">이 작업은 봇 서비스에 대화를 시작 하 라는 메시지를 표시 하기 위해 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

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

11. <span data-ttu-id="0cdbd-400">다음 코 루틴는 Bot 서비스로 보낼 활동을 빌드하기 위해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

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

12. <span data-ttu-id="0cdbd-401">다음 코 루틴는 작업을 Bot Service로 보낸 후 응답을 요청 하기 위해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

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

13. <span data-ttu-id="0cdbd-402">이 클래스에 추가할 마지막 메서드는 장면에 메시지를 표시 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

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
    > <span data-ttu-id="0cdbd-403">Unity 편집기 콘솔에 **SceneOrganiser** 클래스 누락에 대 한 오류가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="0cdbd-404">자습서의 뒷부분에서이 클래스를 만들 때이 메시지는 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="0cdbd-405">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="0cdbd-406">11 장-상호 작용 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="0cdbd-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="0cdbd-407">지금 만들 클래스를 **상호 작용**이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="0cdbd-408">이 클래스는 사용자의 HoloLens 탭 입력을 검색 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="0cdbd-409">장면에서 *봇* 개체를 확인 하는 동안 사용자를 누르면 봇이 음성 입력을 수신할 준비가 되 면 봇 개체가 색을 **빨강** 으로 변경 하 고 음성 입력 수신 대기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="0cdbd-410">이 클래스는 **GazeInput** 클래스에서 상속 하므로 **base**를 사용 하는 것으로 표시 된 해당 클래스에서 **Start ()** 메서드 및 변수를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="0cdbd-411">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="0cdbd-411">To create this class:</span></span>

1.  <span data-ttu-id="0cdbd-412">**Scripts** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="0cdbd-413">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> C# 스크립트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="0cdbd-414">스크립트 **상호 작용**의 이름을로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="0cdbd-415">새 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="0cdbd-416">**상호 작용** 클래스의 위쪽에서 네임 스페이스와 클래스 상속을 다음과 같이 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="0cdbd-417">**상호 작용** 클래스 내에서 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="0cdbd-418">그런 다음 **Start ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-418">Then add the **Start()** method:</span></span>

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

7.  <span data-ttu-id="0cdbd-419">사용자가 HoloLens 카메라 앞에서 탭 제스처를 수행할 때 트리거되는 처리기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

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

8. <span data-ttu-id="0cdbd-420">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="0cdbd-421">12 장 – SceneOrganiser 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="0cdbd-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="0cdbd-422">이 랩에서 필요한 마지막 클래스를 **SceneOrganiser**라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="0cdbd-423">이 클래스는 기본 카메라에 구성 요소 및 스크립트를 추가 하 고 장면에 적절 한 개체를 만들어 프로그래밍 방식으로 장면을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="0cdbd-424">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="0cdbd-424">To create this class:</span></span>

1.  <span data-ttu-id="0cdbd-425">**Scripts** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="0cdbd-426">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> C# 스크립트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="0cdbd-427">스크립트 이름을 **SceneOrganiser**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="0cdbd-428">새 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="0cdbd-429">**SceneOrganiser** 클래스 내에서 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

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

6.  <span data-ttu-id="0cdbd-430">그런 다음, no **()** 및 **Start ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-430">Then add the **Awake()** and **Start()** methods:</span></span>

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

7.  <span data-ttu-id="0cdbd-431">장면에서 봇 개체를 만들고 매개 변수 및 구성 요소를 설정 하는 다음 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

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

7.  <span data-ttu-id="0cdbd-432">다음 메서드를 추가 하 여 화면에 UI 개체를 만들고 봇의 응답을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

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

8.  <span data-ttu-id="0cdbd-433">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="0cdbd-434">Unity 편집기에서 **SceneOrganiser** 스크립트를 Scripts 폴더에서 주 카메라로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="0cdbd-435">이제 아래 이미지에 표시 된 것 처럼 장면 Organiser 구성 요소가 기본 카메라 개체에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Azure Bot Service 만들기](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="0cdbd-437">13 장 – 빌드하기 전</span><span class="sxs-lookup"><span data-stu-id="0cdbd-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="0cdbd-438">응용 프로그램에 대 한 철저 한 테스트를 수행 하려면 HoloLens에 테스트용으로 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="0cdbd-439">이렇게 하려면 먼저 다음을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="0cdbd-440">[**4 장**](#chapter-4--set-up-the-unity-project) 에서 설명한 모든 설정이 올바르게 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-440">All the settings mentioned in the [**Chapter 4**](#chapter-4--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="0cdbd-441">**SceneOrganiser** 스크립트는 **주 카메라** 개체에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="0cdbd-442">**Bot** 클래스에서 **봇 비밀 키** 를 **botSecret** 변수에 삽입 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="0cdbd-443">14 장 – 테스트용으로 로드에 빌드 및</span><span class="sxs-lookup"><span data-stu-id="0cdbd-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="0cdbd-444">이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었으므로 Unity에서 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="0cdbd-445">**빌드 설정**, **파일 > 빌드 설정**으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="0cdbd-446">**빌드 설정** 창에서 **빌드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Unity에서 앱 빌드](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="0cdbd-448">아직 없는 경우 tick **Unity C# 프로젝트**입니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="0cdbd-449">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-449">Click **Build**.</span></span> <span data-ttu-id="0cdbd-450">Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 **파일 탐색기** 창을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="0cdbd-451">이제 해당 폴더를 만들고 이름을 **App**으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="0cdbd-452">그런 다음 **앱** 폴더를 선택 하 고 **폴더 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="0cdbd-453">Unity는 **응용** 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="0cdbd-454">Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)</span><span class="sxs-lookup"><span data-stu-id="0cdbd-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="0cdbd-455">15 장 – HoloLens에 배포</span><span class="sxs-lookup"><span data-stu-id="0cdbd-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="0cdbd-456">HoloLens에 배포 하려면:</span><span class="sxs-lookup"><span data-stu-id="0cdbd-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="0cdbd-457">HoloLens의 IP 주소 (원격 배포의 경우)가 필요 하 고 HoloLens가 **개발자 모드**에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="0cdbd-458">이렇게 하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-458">To do this:</span></span>

    1. <span data-ttu-id="0cdbd-459">HoloLens를 입고 하는 동안 **설정을**엽니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="0cdbd-460">**네트워크 & 인터넷 > wi-fi > 고급 옵션** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="0cdbd-461">**IPv4** 주소를 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="0cdbd-462">그런 다음 **설정**으로 다시 이동한 다음 **개발자를 위한 & 보안 >를 업데이트** 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="0cdbd-463">에서 개발자 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="0cdbd-464">새 Unity 빌드 ( **앱** 폴더)로 이동 하 여 **Visual Studio**에서 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="0cdbd-465">**솔루션 구성** 에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="0cdbd-466">**솔루션 플랫폼**에서 **X86**, **원격 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="0cdbd-468">**빌드 메뉴로** 이동 하 여 **솔루션 배포**를 클릭 하 여 응용 프로그램을 HoloLens로 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="0cdbd-469">이제 앱이 HoloLens에 설치 된 앱 목록에 표시 되어 시작할 준비가 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="0cdbd-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="0cdbd-470">모던 헤드셋에 배포 하려면 **솔루션 플랫폼** 을 *로컬 컴퓨터*로 설정 하 고 **구성을** *디버그*로 설정 하 고 *x 86* 을 **플랫폼**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="0cdbd-471">그런 다음 **빌드 메뉴**를 사용 하 여 *솔루션 배포*를 선택 하 여 로컬 컴퓨터에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="0cdbd-472">16 장-HoloLens에서 응용 프로그램 사용</span><span class="sxs-lookup"><span data-stu-id="0cdbd-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="0cdbd-473">응용 프로그램을 시작 하면 그 앞에 파란색 구로 봇이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="0cdbd-474">구에 gazing 하는 동안 **탭 제스처** 를 사용 하 여 대화를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="0cdbd-475">대화가 시작 될 때까지 기다립니다 (UI가 발생 하면 메시지 표시).</span><span class="sxs-lookup"><span data-stu-id="0cdbd-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="0cdbd-476">봇에서 소개 메시지를 받은 후 봇에서 다시 탭 하 여 빨간색으로 바뀌고 음성 듣기를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="0cdbd-477">통신을 중지 하면 응용 프로그램이 봇으로 메시지를 보내고 UI에 표시 되는 응답을 즉시 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="0cdbd-478">프로세스를 반복 하 여 봇에 더 많은 메시지를 보냅니다 (메시지를 send 할 때마다 탭 해야).</span><span class="sxs-lookup"><span data-stu-id="0cdbd-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="0cdbd-479">이 대화에서는 봇이 정보 (사용자 이름)를 유지할 수 있는 방법을 보여 주며, 알려진 정보 (예: 보충 항목)도 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="0cdbd-480">Bot 질문:</span><span class="sxs-lookup"><span data-stu-id="0cdbd-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="0cdbd-481">완료 된 웹 앱 봇 (v4) 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="0cdbd-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="0cdbd-482">축 하 합니다. Azure 웹 앱 봇, Microsoft 봇 Framework v4를 활용 하는 혼합 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![최종 제품](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="0cdbd-484">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="0cdbd-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="0cdbd-485">연습 1</span><span class="sxs-lookup"><span data-stu-id="0cdbd-485">Exercise 1</span></span>

<span data-ttu-id="0cdbd-486">이 랩에서 대화 구조는 매우 기본적인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="0cdbd-487">Microsoft LUIS를 사용 하 여 인공 자연어 이해 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="0cdbd-488">연습 2</span><span class="sxs-lookup"><span data-stu-id="0cdbd-488">Exercise 2</span></span>

<span data-ttu-id="0cdbd-489">이 예제에서는 대화를 종료 하 고 새 대화를 다시 시작 하는 것을 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="0cdbd-490">Bot 기능을 완전 하 게 만들려면 대화에 대 한 클로저를 구현 해 보세요.</span><span class="sxs-lookup"><span data-stu-id="0cdbd-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
