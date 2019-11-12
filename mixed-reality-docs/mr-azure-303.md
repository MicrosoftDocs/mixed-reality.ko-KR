---
title: MR 및 Azure 303-자연어 이해 (LUIS)
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure LUIS (Language Understanding 인텔리전스 서비스)를 구현 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 언어 이해 인텔리전스 서비스, luis, hololens, 몰입 형, vr
ms.openlocfilehash: 9b3e4f081dc8a054d783246554f904a38f43f26c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926812"
---
>[!NOTE]
><span data-ttu-id="9169f-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9169f-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9169f-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9169f-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9169f-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="9169f-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="9169f-110">MR 및 Azure 303: 자연어 이해 (LUIS)</span><span class="sxs-lookup"><span data-stu-id="9169f-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="9169f-111">이 과정에서는 Language Understanding API와 함께 Azure Cognitive Services를 사용 하 여 혼합 현실 응용 프로그램에 Language Understanding를 통합 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![랩 결과](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="9169f-113">*LUIS (Language Understanding)* 는 응용 프로그램에서 사용자가 원하는 항목을 자신의 단어로 추출 하는 등 사용자 입력에서 의미를 유지할 수 있는 기능을 제공 하는 Microsoft Azure 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="9169f-114">이는 입력 정보를 이해 하 고 학습 한 다음 상세 하 고 관련 된 정보를 사용 하 여 회신할 수 있는 기계 학습을 통해 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="9169f-115">자세한 내용은 [Azure Language Understanding (LUIS) 페이지](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9169f-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="9169f-116">이 과정을 완료 하면 다음과 같은 작업을 수행할 수 있는 혼합 현실 모던 헤드셋 응용 프로그램이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="9169f-117">몰입 형 헤드셋에 연결 된 마이크를 사용 하 여 사용자 입력 음성을 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="9169f-118">캡처된 받아쓰기를 *Azure Language Understanding Intelligent Service* (*LUIS*)로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="9169f-119">LUIS은 전송 정보에서 의미를 추출 하 여 분석 하 고 사용자의 요청 의도를 확인 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="9169f-120">개발에는 사용자가 음성 및/또는 응시를 사용 하 여 장면의 개체 크기와 색을 변경할 수 있는 앱을 만드는 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="9169f-121">동작 컨트롤러의 사용은 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="9169f-122">응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="9169f-123">이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="9169f-124">이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="9169f-125">[12 장](#chapter-12--improving-your-luis-service)에서 설명 하는 LUIS을 여러 번 학습 하도록 준비 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="9169f-126">LUIS을 더 많이 학습 한 경우 더 나은 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="9169f-127">장치 지원</span><span class="sxs-lookup"><span data-stu-id="9169f-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9169f-128">과정</span><span class="sxs-lookup"><span data-stu-id="9169f-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9169f-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9169f-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9169f-130"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="9169f-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="9169f-131">MR 및 Azure 303: 자연어 이해 (LUIS)</span><span class="sxs-lookup"><span data-stu-id="9169f-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="9169f-132">✔️</span><span class="sxs-lookup"><span data-stu-id="9169f-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="9169f-133">✔️</span><span class="sxs-lookup"><span data-stu-id="9169f-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="9169f-134">이 과정에서 주로 Windows Mixed Reality (VR) 헤드셋에 초점을 맞춘 반면,이 과정에서 학습 하는 내용을 Microsoft HoloLens에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="9169f-135">과정을 진행할 때 HoloLens를 지원 하기 위해 사용 해야 하는 모든 변경 내용에 대 한 메모를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="9169f-136">HoloLens를 사용 하는 경우 음성 캡처 중에 몇 가지 echo를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9169f-137">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="9169f-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="9169f-138">이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="9169f-139">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="9169f-140">[도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="9169f-141">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="9169f-142">모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC</span><span class="sxs-lookup"><span data-stu-id="9169f-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="9169f-143">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="9169f-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="9169f-144">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="9169f-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="9169f-145">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="9169f-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="9169f-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="9169f-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="9169f-147">개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="9169f-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="9169f-148">기본 제공 마이크가 있는 헤드폰 집합 (헤드셋에 기본 제공 mic 및 스피커가 없는 경우)</span><span class="sxs-lookup"><span data-stu-id="9169f-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="9169f-149">Azure 설정 및 LUIS 검색을 위한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="9169f-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="9169f-150">시작하기 전 확인 사항</span><span class="sxs-lookup"><span data-stu-id="9169f-150">Before you start</span></span>

1.  <span data-ttu-id="9169f-151">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="9169f-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="9169f-152">컴퓨터에서 받아쓰기를 사용 하도록 허용 하려면 **Windows 설정 > 개인 정보 > 음성, 필기 & 입력** 으로 이동 하 고 단추를 눌러 **음성 서비스를 켜고 제안을 입력**합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="9169f-153">이 자습서의 코드를 사용 하면 컴퓨터에 설정 된 **기본 마이크 장치** 에서 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="9169f-154">기본 마이크 장치가 음성을 캡처하는 데 사용할 것으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="9169f-155">헤드셋에 기본 제공 마이크가 있는 경우 *혼합 현실 포털* 설정에서 *"헤드셋을 착용 할 때 헤드셋 mic로 전환"* 옵션이 켜져 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![모던 헤드셋 설정](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="9169f-157">1 장-Azure Portal 설정</span><span class="sxs-lookup"><span data-stu-id="9169f-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="9169f-158">Azure에서 *Language Understanding* 서비스를 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="9169f-159">[Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="9169f-160">아직 Azure 계정이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="9169f-161">교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="9169f-162">로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 *Language Understanding*를 검색 한 다음 **Enter 키**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![LUIS 리소스 만들기](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="9169f-164">새 단어는 **새** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="9169f-165">오른쪽의 새 페이지는 Language Understanding 서비스에 대 한 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="9169f-166">이 페이지의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![LUIS 서비스 만들기-법적 고 지 사항](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="9169f-168">만들기를 클릭 하면 다음을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="9169f-169">이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="9169f-170">**구독**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="9169f-171">적절 한 **가격 책정 계층** 을 선택 하세요. *LUIS 서비스*를 처음 만드는 경우 무료 계층 (명명 된 F0)을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="9169f-172">이 과정에서는 사용 가능한 할당이 충분 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="9169f-173">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="9169f-174">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="9169f-175">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="9169f-176">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.</span><span class="sxs-lookup"><span data-stu-id="9169f-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="9169f-177">새 리소스 그룹을 만드는 경우 리소스 그룹의 **위치** 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="9169f-178">위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="9169f-179">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="9169f-180">또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="9169f-181">**만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-181">Select **Create**.</span></span>

        ![LUIS 서비스 만들기-사용자 입력](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="9169f-183">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="9169f-184">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![새 Azure 알림 이미지](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="9169f-186">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-186">Click on the notification to explore your new Service instance.</span></span>

    ![리소스 만들기 성공 알림](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="9169f-188">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="9169f-189">새 LUIS 서비스 인스턴스로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![LUIS 키 액세스](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="9169f-191">이 자습서에서 응용 프로그램은 서비스에 대 한 호출을 수행 해야 하며, 서비스의 구독 키를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="9169f-192">*LUIS API* 서비스의 *빠른 시작* 페이지에서 첫 번째 단계로 이동 하 고 키를 클릭 한 다음 *키를 클릭*합니다 .이를 위해 서비스 탐색 메뉴에서 키 아이콘으로 표시 되는 파란색 하이퍼링크 키 **를 클릭 하** 여이를 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="9169f-193">이렇게 하면 서비스 *키*가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="9169f-194">프로젝트에서 나중에 필요 하므로 표시 된 키 중 하나를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="9169f-195">*서비스* 페이지에서 LUIS 앱 내에서 새 서비스를 만드는 데 사용할 웹 페이지로 리디렉션되는 *Language Understanding 포털* 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="9169f-196">2 장-Language Understanding 포털</span><span class="sxs-lookup"><span data-stu-id="9169f-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="9169f-197">이 섹션에서는 LUIS 포털에서 LUIS 앱을 만드는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="9169f-198">이 장 내에서 *엔터티*, *의도*및 *길이 발언* 를 설정 하는 것은 LUIS 서비스를 빌드하는 첫 번째 단계 일 뿐입니다. 더 정확 하 게 만들려면 서비스를 여러 번 다시 학습 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="9169f-199">서비스에 대 한 재 학습은이 과정의 [마지막 장에서](#chapter-12--improving-your-luis-service) 설명 하므로 완료 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="9169f-200">*Language Understanding 포털*에 도달 하면 Azure Portal와 동일한 자격 증명을 사용 하 여 로그인 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![LUIS 로그인 페이지](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="9169f-202">LUIS를 처음 사용 하는 경우 시작 페이지의 아래쪽으로 스크롤하여 **LUIS 앱 만들기** 단추를 찾아 클릭 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![LUIS 앱 만들기 페이지](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="9169f-204">로그인 한 후 **내 앱** (현재 해당 섹션에 있지 않은 경우)을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="9169f-205">그런 다음 **새 앱 만들기**를 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-205">You can then click on **Create new app**.</span></span>

    ![LUIS-내 앱 이미지](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="9169f-207">앱에 *이름을*지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="9169f-208">앱이 영어와 다른 언어를 파악 해야 하는 경우 *문화권* 을 적절 한 언어로 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="9169f-209">여기에서 새 LUIS 앱에 대 한 *설명을* 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS-새 앱 만들기](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="9169f-211">**완료**를 누르면 새 *LUIS* 응용 프로그램의 *빌드* 페이지가 입력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="9169f-212">여기에서 이해할 수 있는 몇 가지 중요 한 개념이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="9169f-213">*의도*는 사용자의 쿼리 다음에 호출 될 메서드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="9169f-214">*의도* 에 하나 이상의 *엔터티가*있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="9169f-215">*엔터티*는 *의도*와 관련 된 정보를 설명 하는 쿼리의 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="9169f-216">*길이 발언*는 개발자가 직접 학습 하는 데 사용 하는 개발자가 제공 하는 쿼리의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="9169f-217">이러한 개념을 완벽 하 게 명확 하 게 이해 하지 못하는 경우이 과정에서이 장을 자세히 설명 하므로 걱정 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="9169f-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="9169f-218">이 과정을 빌드하는 데 필요한 *엔터티* 를 만드는 것부터 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="9169f-219">페이지의 왼쪽에서 *엔터티*를 클릭 한 다음 **새 엔터티 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![새 엔터티 만들기](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="9169f-221">새 엔터티 *색*을 호출 하 고 해당 형식을 *Simple*로 설정한 후 **Done**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![단순 엔터티 색 만들기](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="9169f-223">이 프로세스를 반복 하 여 라는 세 개의 단순 엔터티 (3)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="9169f-224">*업사이징*</span><span class="sxs-lookup"><span data-stu-id="9169f-224">*upsize*</span></span>
    -   <span data-ttu-id="9169f-225">*줄이지*</span><span class="sxs-lookup"><span data-stu-id="9169f-225">*downsize*</span></span>
    -   <span data-ttu-id="9169f-226">*대상을*</span><span class="sxs-lookup"><span data-stu-id="9169f-226">*target*</span></span>

<span data-ttu-id="9169f-227">결과는 아래 이미지와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-227">The result should look like the image below:</span></span>

![엔터티 생성 결과](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="9169f-229">이 시점에서 *의도*만들기를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="9169f-230">**없음** 의도를 삭제 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="9169f-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="9169f-231">페이지의 왼쪽에서 **의도**를 클릭 한 다음 **새 용도 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![새 의도 만들기](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="9169f-233">새 *의도* **changeobjectcolor**를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="9169f-234">이 *의도* 이름은이 과정의 뒷부분에 나오는 코드 내에서 사용 되므로 최상의 결과를 위해 제공 된 대로 정확 하 게이 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="9169f-235">이름을 확인 한 후에는 의도 페이지로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS-의도 페이지](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="9169f-237">5 개 이상의 다른 *길이 발언*를 입력 하 라는 텍스트 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="9169f-238">LUIS는 모든 길이 발언를 소문자로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="9169f-239">맨 위 텍스트 상자에 다음 *Utterance* 을 삽입 합니다 (현재 텍스트 *형식이 5 개 예* 인 경우).</span><span class="sxs-lookup"><span data-stu-id="9169f-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="9169f-240">)를 **입력**하 고 enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="9169f-241">새 *Utterance* 이 아래 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="9169f-242">동일한 프로세스를 수행 하 고 다음 6 개 (6) 길이 발언를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="9169f-243">만든 각 Utterance에 대해 LUIS에서 엔터티로 사용할 단어를 식별 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="9169f-244">이 예제에서는 모든 색을 *색* 엔터티로 레이블과 대상에 대 한 모든 가능한 참조를 *대상* 엔터티로 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="9169f-245">이렇게 하려면 첫 번째 Utterance에서 *실린더* 단어를 클릭 하 고 *대상*을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![Utterance 대상 식별](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="9169f-247">이제 첫 번째 Utterance *빨간색* 이라는 단어를 클릭 하 고 *색*을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![Utterance 엔터티 식별](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="9169f-249">다음 줄에 레이블을 지정 합니다. 여기서 *cube* 는 *대상*이어야 하 고 *black* 은 *색*이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="9169f-250">또한 제공 되는 *' this '* , *' it '* 및 *' this object '* 단어를 사용 하 여 특정 대상 유형을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="9169f-251">모든 길이 발언에 레이블이 붙은 엔터티가 있을 때까지 위의 프로세스를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="9169f-252">도움이 필요 하면 아래 이미지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9169f-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="9169f-253">엔터티로 레이블을 추가할 단어를 선택 하는 경우:</span><span class="sxs-lookup"><span data-stu-id="9169f-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="9169f-254">한 단어에 대해서만 클릭 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-254">For single words just click them.</span></span>
    > - <span data-ttu-id="9169f-255">두 개 이상의 단어 집합의 경우 시작 부분을 클릭 한 다음 집합의 끝 부분을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9169f-256">*토큰 뷰* 토글 단추를 사용 하 여 **엔터티/토큰 뷰**간을 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="9169f-257">결과는 아래 이미지에 표시 된 것과 같이 **엔터티/토큰 뷰**를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![토큰 & 엔터티 보기](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="9169f-259">이 시점에서 페이지의 오른쪽 위에 있는 **학습** 단추를 누르고 작은 라운드 표시기가 녹색으로 전환 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="9169f-260">이는 LUIS가 이러한 의도를 인식할 수 있도록 성공적으로 교육 되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![LUIS 학습](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="9169f-262">실습으로, 엔터티 *대상*, *업사이징*및 *다운 크기*를 사용 하 여 **changeobjectsize**라는 새로운 의도를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="9169f-263">이전 의도와 동일한 프로세스를 수행 하 여 *크기* 변경에 대 한 길이 발언 8 (8)을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. <span data-ttu-id="9169f-264">결과는 아래 이미지에 있는 것과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-264">The result should be like the one in the image below:</span></span>

    ![ChangeObjectSize 토큰/엔터티 설정](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="9169f-266">두 의도, **Changeobjectcolor** 및 **changeobjectcolor**를 모두 만들고 학습 한 후에는 페이지 맨 위에 있는 **게시** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![LUIS 서비스 게시](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="9169f-268">*게시* 페이지에서 LUIS 앱을 마무리 하 고 게시 하 여 코드에서 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="9169f-269">드롭다운을 **프로덕션**으로 *게시를* 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="9169f-270">표준 시간대로 *표준* 시간대를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="9169f-271">**모든 예측 된 의도 점수를 포함**하는 상자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="9169f-272">**프로덕션 슬롯에 게시를**클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-272">Click on **Publish to Production Slot**.</span></span>

        ![게시 설정](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="9169f-274">*리소스 및 키*섹션에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="9169f-275">Azure Portal에서 서비스 인스턴스에 대해 설정한 지역을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="9169f-276">아래 **Starter_Key** 요소를 확인 하 고 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="9169f-277">**키 추가** 를 클릭 하 고 서비스 인스턴스를 만들 때 Azure Portal에서 가져온 *키* 를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="9169f-278">Azure와 LUIS 포털이 동일한 사용자에 게 로그인 하는 경우 *테 넌 트 이름*, *구독 이름*및 사용 하려는 *키* 에 대 한 드롭다운 메뉴가 제공 됩니다 (이전에는 azure portal에서 제공한 것과 동일한 이름을 사용).</span><span class="sxs-lookup"><span data-stu-id="9169f-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="9169f-279">*끝점*아래에서 삽입 한 키에 해당 하는 끝점의 복사본을 만든 후 코드에서 곧 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="9169f-280">3 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="9169f-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="9169f-281">다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="9169f-282">*Unity* 를 열고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-282">Open *Unity* and click **New**.</span></span> 

    ![새 Unity 프로젝트를 시작 합니다.](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="9169f-284">이제 Unity 프로젝트 이름, insert **MR_LUIS**를 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="9169f-285">프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="9169f-286">위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="9169f-287">그런 다음 **프로젝트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-287">Then, click **Create project**.</span></span>

    ![새 Unity 프로젝트에 대 한 세부 정보를 제공 합니다.](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="9169f-289">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="9169f-290">> 기본 설정 편집으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="9169f-291">**외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="9169f-292">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-292">Close the **Preferences** window.</span></span>

    ![스크립트 편집기 기본 설정을 업데이트 합니다.](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="9169f-294">그런 다음 **파일 > 빌드 설정** 으로 이동 하 고 플랫폼 **전환** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼**로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![빌드 설정 창에서 플랫폼을 UWP로 전환 합니다.](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="9169f-296">**파일 > 빌드 설정** 으로 이동 하 고 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="9169f-297">**대상 장치가** **모든 장치로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="9169f-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="9169f-298">Microsoft HoloLens의 경우 **대상 장치** 를 *HoloLens*로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="9169f-299">**빌드 형식이** **D3D** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="9169f-300">**SDK** 가 **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="9169f-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="9169f-301">**Visual Studio 버전이** **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="9169f-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="9169f-302">**빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="9169f-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="9169f-303">장면을 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="9169f-304">이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="9169f-305">저장 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-305">A save window will appear.</span></span>
        
            ![열린 장면 추가 단추를 클릭 합니다.](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="9169f-307">이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을**로 지정한 다음</span><span class="sxs-lookup"><span data-stu-id="9169f-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="9169f-309">새로 만든 **장면** 폴더를 연 다음 *파일 이름*: 텍스트 필드에 **MR_LuisScene**를 입력 하 고 **저장**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![새 장면에 이름을 지정 합니다.](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="9169f-311">*빌드 설정*의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="9169f-312">*빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![플레이어 설정을 엽니다.](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="9169f-314">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="9169f-315">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="9169f-316">**Scripting Runtime 버전** 은 **안정적** 이어야 합니다 (.net 3.5 해당).</span><span class="sxs-lookup"><span data-stu-id="9169f-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="9169f-317">**Scripting 백엔드** 는 **.net** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="9169f-318">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![다른 설정을 업데이트 합니다.](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="9169f-320">**게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="9169f-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="9169f-321">**InternetClient**</span></span>
        2. <span data-ttu-id="9169f-322">**마이크로**</span><span class="sxs-lookup"><span data-stu-id="9169f-322">**Microphone**</span></span>

            ![게시 설정을 업데이트 하는 중입니다.](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="9169f-324">패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X R 설정을 업데이트 합니다.](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="9169f-326">*빌드 설정* 으로 돌아가서 _Unity C#_  프로젝트가 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="9169f-327">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="9169f-328">장면 및 프로젝트를 저장 합니다 (**파일 > 장면/파일 저장 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="9169f-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="9169f-329">4 장-장면 만들기</span><span class="sxs-lookup"><span data-stu-id="9169f-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9169f-330">이 과정의 *Unity 설정* 구성 요소를 건너뛰고 계속 해 서 코드를 계속 사용 하려면 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)를 다운로드 하 여 프로젝트에 [사용자 지정 패키지로](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 [5 장](#chapter-5--create-the-microphonemanager-class)에서 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="9169f-331">*계층 패널*의 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 **3d 개체**아래에서 **평면**을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![평면을 만듭니다.](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="9169f-333">*계층 구조* 내에서 마우스 오른쪽 단추를 클릭 하 여 더 많은 개체를 만들 경우 마지막 개체를 선택한 경우 선택한 개체가 새 개체의 부모가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="9169f-334">계층 구조 내의 빈 공간을 마우스 왼쪽 단추로 클릭 한 다음 마우스 오른쪽 단추를 클릭 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="9169f-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="9169f-335">위의 절차를 반복 하 여 다음 개체를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="9169f-336">*Sphere*</span><span class="sxs-lookup"><span data-stu-id="9169f-336">*Sphere*</span></span>
    2. <span data-ttu-id="9169f-337">*원통형*</span><span class="sxs-lookup"><span data-stu-id="9169f-337">*Cylinder*</span></span>
    3. <span data-ttu-id="9169f-338">*큐브*</span><span class="sxs-lookup"><span data-stu-id="9169f-338">*Cube*</span></span>
    4. <span data-ttu-id="9169f-339">*3D 텍스트*</span><span class="sxs-lookup"><span data-stu-id="9169f-339">*3D Text*</span></span>

4.  <span data-ttu-id="9169f-340">결과 장면 *계층 구조* 는 아래 이미지에 있는 것과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![장면 계층 설정입니다.](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="9169f-342">**기본 카메라** 를 마우스 왼쪽 단추를 클릭 하 여 선택 하 고, *검사기 패널* 에서 모든 구성 요소를 포함 하는 카메라 개체를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="9169f-343">*검사기 패널*의 맨 아래에 있는 **구성 요소 추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![오디오 소스 추가](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="9169f-345">위에 표시 된 것 처럼 *오디오 원본*이라는 구성 요소를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="9169f-346">또한 기본 카메라의 *변형* 구성 요소가 (0, 0, 0)로 설정 되어 있는지 확인 합니다. 카메라의 *변형* 구성 요소 옆에 있는 **기어** 아이콘을 누르고 **다시 설정**을 선택 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="9169f-347">*변환* 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="9169f-348">*Position* 은 **0, 0,** 0으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="9169f-349">*회전* 은 **0, 0, 0**으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="9169f-350">Microsoft HoloLens의 경우 **기본 카메라**의 **카메라** 구성 요소에 포함 된 다음도 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="9169f-351">**플래그 지우기:** 단색입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="9169f-352">**배경** ' Black, Alpha 0 ' – 16 진수 색: #00000000.</span><span class="sxs-lookup"><span data-stu-id="9169f-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="9169f-353">**평면** 을 마우스 왼쪽 단추를 클릭 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="9169f-354">*검사기 패널* 에서 *변형* 구성 요소를 다음 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="9169f-355">변환 *위치*</span><span class="sxs-lookup"><span data-stu-id="9169f-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="9169f-356">**.X**</span><span class="sxs-lookup"><span data-stu-id="9169f-356">**X**</span></span> | <span data-ttu-id="9169f-357">**X.y**</span><span class="sxs-lookup"><span data-stu-id="9169f-357">**Y**</span></span>                  | <span data-ttu-id="9169f-358">**-**</span><span class="sxs-lookup"><span data-stu-id="9169f-358">**Z**</span></span> |
    | <span data-ttu-id="9169f-359">0</span><span class="sxs-lookup"><span data-stu-id="9169f-359">0</span></span>     | <span data-ttu-id="9169f-360">-1</span><span class="sxs-lookup"><span data-stu-id="9169f-360">-1</span></span>                     | <span data-ttu-id="9169f-361">0</span><span class="sxs-lookup"><span data-stu-id="9169f-361">0</span></span>     |


10. <span data-ttu-id="9169f-362">**구를** 마우스 왼쪽 단추를 클릭 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="9169f-363">*검사기 패널* 에서 *변형* 구성 요소를 다음 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="9169f-364">변환 *위치*</span><span class="sxs-lookup"><span data-stu-id="9169f-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="9169f-365">**.X**</span><span class="sxs-lookup"><span data-stu-id="9169f-365">**X**</span></span> | <span data-ttu-id="9169f-366">**X.y**</span><span class="sxs-lookup"><span data-stu-id="9169f-366">**Y**</span></span>                  | <span data-ttu-id="9169f-367">**-**</span><span class="sxs-lookup"><span data-stu-id="9169f-367">**Z**</span></span> |
    | <span data-ttu-id="9169f-368">2</span><span class="sxs-lookup"><span data-stu-id="9169f-368">2</span></span>     | <span data-ttu-id="9169f-369">1</span><span class="sxs-lookup"><span data-stu-id="9169f-369">1</span></span>                      | <span data-ttu-id="9169f-370">2</span><span class="sxs-lookup"><span data-stu-id="9169f-370">2</span></span>     |

11. <span data-ttu-id="9169f-371">**원통** 을 마우스 왼쪽 단추를 클릭 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="9169f-372">*검사기 패널* 에서 *변형* 구성 요소를 다음 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="9169f-373">변환 *위치*</span><span class="sxs-lookup"><span data-stu-id="9169f-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="9169f-374">**.X**</span><span class="sxs-lookup"><span data-stu-id="9169f-374">**X**</span></span> | <span data-ttu-id="9169f-375">**X.y**</span><span class="sxs-lookup"><span data-stu-id="9169f-375">**Y**</span></span>                  | <span data-ttu-id="9169f-376">**-**</span><span class="sxs-lookup"><span data-stu-id="9169f-376">**Z**</span></span> |
    | <span data-ttu-id="9169f-377">-2</span><span class="sxs-lookup"><span data-stu-id="9169f-377">-2</span></span>    | <span data-ttu-id="9169f-378">1</span><span class="sxs-lookup"><span data-stu-id="9169f-378">1</span></span>                      | <span data-ttu-id="9169f-379">2</span><span class="sxs-lookup"><span data-stu-id="9169f-379">2</span></span>     |

12. <span data-ttu-id="9169f-380">**큐브** 를 마우스 왼쪽 단추를 클릭 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="9169f-381">*검사기 패널* 에서 *변형* 구성 요소를 다음 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="9169f-382">변환 *위치*</span><span class="sxs-lookup"><span data-stu-id="9169f-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="9169f-383">변환- *회전*</span><span class="sxs-lookup"><span data-stu-id="9169f-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="9169f-384">**.X**</span><span class="sxs-lookup"><span data-stu-id="9169f-384">**X**</span></span> | <span data-ttu-id="9169f-385">**X.y**</span><span class="sxs-lookup"><span data-stu-id="9169f-385">**Y**</span></span>                   | <span data-ttu-id="9169f-386">**-**</span><span class="sxs-lookup"><span data-stu-id="9169f-386">**Z**</span></span> |  \| | <span data-ttu-id="9169f-387">**.X**</span><span class="sxs-lookup"><span data-stu-id="9169f-387">**X**</span></span> | <span data-ttu-id="9169f-388">**X.y**</span><span class="sxs-lookup"><span data-stu-id="9169f-388">**Y**</span></span>                  | <span data-ttu-id="9169f-389">**-**</span><span class="sxs-lookup"><span data-stu-id="9169f-389">**Z**</span></span> |
    | <span data-ttu-id="9169f-390">0</span><span class="sxs-lookup"><span data-stu-id="9169f-390">0</span></span>     | <span data-ttu-id="9169f-391">1</span><span class="sxs-lookup"><span data-stu-id="9169f-391">1</span></span>                       | <span data-ttu-id="9169f-392">추가를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-392">4</span></span>     |  \| | <span data-ttu-id="9169f-393">45</span><span class="sxs-lookup"><span data-stu-id="9169f-393">45</span></span>    | <span data-ttu-id="9169f-394">45</span><span class="sxs-lookup"><span data-stu-id="9169f-394">45</span></span>                     | <span data-ttu-id="9169f-395">0</span><span class="sxs-lookup"><span data-stu-id="9169f-395">0</span></span>     | 

13. <span data-ttu-id="9169f-396">**새 텍스트** 개체를 마우스 왼쪽 단추를 클릭 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="9169f-397">*검사기 패널* 에서 *변형* 구성 요소를 다음 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="9169f-398">변환 *위치*</span><span class="sxs-lookup"><span data-stu-id="9169f-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="9169f-399">변환- *배율*</span><span class="sxs-lookup"><span data-stu-id="9169f-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="9169f-400">**.X**</span><span class="sxs-lookup"><span data-stu-id="9169f-400">**X**</span></span> | <span data-ttu-id="9169f-401">**X.y**</span><span class="sxs-lookup"><span data-stu-id="9169f-401">**Y**</span></span>                  | <span data-ttu-id="9169f-402">**-**</span><span class="sxs-lookup"><span data-stu-id="9169f-402">**Z**</span></span> |  \| | <span data-ttu-id="9169f-403">**.X**</span><span class="sxs-lookup"><span data-stu-id="9169f-403">**X**</span></span> | <span data-ttu-id="9169f-404">**X.y**</span><span class="sxs-lookup"><span data-stu-id="9169f-404">**Y**</span></span>               | <span data-ttu-id="9169f-405">**-**</span><span class="sxs-lookup"><span data-stu-id="9169f-405">**Z**</span></span> |
    | <span data-ttu-id="9169f-406">-2</span><span class="sxs-lookup"><span data-stu-id="9169f-406">-2</span></span>    | <span data-ttu-id="9169f-407">6</span><span class="sxs-lookup"><span data-stu-id="9169f-407">6</span></span>                      | <span data-ttu-id="9169f-408">9</span><span class="sxs-lookup"><span data-stu-id="9169f-408">9</span></span>     |  \| | <span data-ttu-id="9169f-409">0.1</span><span class="sxs-lookup"><span data-stu-id="9169f-409">0.1</span></span>   | <span data-ttu-id="9169f-410">0.1</span><span class="sxs-lookup"><span data-stu-id="9169f-410">0.1</span></span>                 | <span data-ttu-id="9169f-411">0.1</span><span class="sxs-lookup"><span data-stu-id="9169f-411">0.1</span></span>   | 

14. <span data-ttu-id="9169f-412">**텍스트 메시** 구성 요소의 **글꼴 크기** 를 **50**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="9169f-413">**텍스트 메시** 개체의 *이름을* **받아쓰기 텍스트로**변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![3D 텍스트 개체 만들기](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="9169f-415">이제 계층 구조 패널 구조가 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![장면 뷰의 텍스트 메시](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="9169f-417">최종 장면은 아래 이미지와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-417">The final scene should look like the image below:</span></span>

    ![장면 뷰입니다.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="9169f-419">5 장-MicrophoneManager 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="9169f-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="9169f-420">만들려는 첫 번째 스크립트는 *MicrophoneManager* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="9169f-421">이를 수행 하 고 나면 *Luismanager*, *동작* 클래스 및 마지막으로 *응시* 클래스 (각 챕터에 도달 하는 경우에도 적용 됨)를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="9169f-422">*MicrophoneManager* 클래스는 다음을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="9169f-423">헤드셋 또는 컴퓨터에 연결 된 기록 장치 검색 (기본 항목 중 하나)</span><span class="sxs-lookup"><span data-stu-id="9169f-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="9169f-424">오디오 (음성)를 캡처하고 받아쓰기를 사용 하 여 문자열로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="9169f-425">음성이 일시 중지 되 면 받아쓰기를 *Luismanager* 클래스에 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="9169f-426">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="9169f-426">To create this class:</span></span> 

1.  <span data-ttu-id="9169f-427">*프로젝트 패널*을 마우스 오른쪽 단추로 클릭 하 **> 폴더를 만듭니다**.</span><span class="sxs-lookup"><span data-stu-id="9169f-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="9169f-428">폴더 **스크립트**를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-428">Call the folder **Scripts**.</span></span> 

    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="9169f-430">**Scripts** 폴더를 만든 다음 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="9169f-431">그런 다음 해당 폴더 내에서  **C# > 스크립트 만들기**를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="9169f-432">스크립트 이름을 *MicrophoneManager*로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="9169f-433">*MicrophoneManager* 를 두 번 클릭 하 여 *Visual Studio*에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="9169f-434">파일의 맨 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="9169f-435">그런 다음 *MicrophoneManager* 클래스 안에 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="9169f-436">이제 *활성 ()* 및 *Start ()* 메서드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="9169f-437">이러한 작업은 클래스가 초기화 될 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-437">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  <span data-ttu-id="9169f-438">이제 앱이 음성 캡처를 시작 및 중지 하는 데 사용 하는 메서드를 사용 하 여 곧 빌드 될 *Luismanager* 클래스에 전달 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  <span data-ttu-id="9169f-439">음성이 일시 중지 될 때 호출 되는 *받아쓰기 처리기* 를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="9169f-440">이 메서드는 받아쓰기 텍스트를 *Luismanager* 클래스로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="9169f-441">이 클래스는 사용 하지 않으므로 *Update ()* 메서드를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="9169f-442">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9169f-443">이 시점에서 *Unity 편집기 콘솔 패널*에 오류가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="9169f-444">코드는 다음 챕터에서 만들 *Luismanager* 클래스를 참조 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="9169f-445">6 장 – LUISManager 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="9169f-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="9169f-446">Azure LUIS 서비스에 대 한 호출을 수행 하는 *Luismanager* 클래스를 만들 때입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="9169f-447">이 클래스의 목적은 *MicrophoneManager* 클래스에서 받아쓰기 텍스트를 받고 분석 될 *Azure Language Understanding API* 로 보내는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="9169f-448">이 클래스는 *JSON* 응답을 deserialize 하 고 *동작* 클래스의 적절 한 메서드를 호출 하 여 작업을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="9169f-449">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="9169f-449">To create this class:</span></span> 

1.  <span data-ttu-id="9169f-450">**스크립트** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="9169f-451">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> C# 스크립트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="9169f-452">스크립트 이름을 *Luismanager*로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="9169f-453">스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="9169f-454">파일의 맨 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="9169f-455">먼저 Azure에서 deserialize 된 JSON 응답을 나타내는 동일한 스크립트 파일 ( *Start ()* 메서드 위에 있는)의 *luismanager* **클래스 내에서 세 개의 클래스를** 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  <span data-ttu-id="9169f-456">그런 다음, 다음 변수를 *Luismanager* 클래스 내에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="9169f-457">LUIS 끝점을 지금 (LUIS 포털에서 수행할 수 있도록)에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="9169f-458">이제 해제 *()* 메서드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="9169f-459">이 메서드는 클래스가 초기화 될 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="9169f-460">이제이 응용 프로그램에서 *MicrophoneManager* 클래스 로부터 받은 받아쓰기를 *LUIS*로 보낸 다음 응답을 수신 및 deserialize 하는 데 사용 하는 메서드가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="9169f-461">의도 및 연결 된 엔터티의 값이 확인 되 면 *동작* 클래스의 인스턴스에 전달 되어 의도 된 동작을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. <span data-ttu-id="9169f-462">결과 *AnalysedQuery* 를 읽고 엔터티를 확인 하는 *AnalyseResponseElements ()* 라는 새 메서드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="9169f-463">이러한 엔터티가 결정 되 면 작업에서 사용할 *동작* 클래스의 인스턴스에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="9169f-464">*Start ()* 및 *Update ()* 메서드는이 클래스에서 사용 하지 않으므로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="9169f-465">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="9169f-466">이 시점에서 *Unity 편집기 콘솔 패널*에 몇 가지 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="9169f-467">코드는 다음 챕터에서 만들 *동작* 클래스를 참조 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="9169f-468">7 장 – 동작 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="9169f-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="9169f-469">*동작* 클래스는 *luismanager* 클래스에서 제공 하는 엔터티를 사용 하 여 작업을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="9169f-470">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="9169f-470">To create this class:</span></span> 

1.  <span data-ttu-id="9169f-471">**스크립트** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="9169f-472">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> C# 스크립트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="9169f-473">스크립트 이름을 *동작*로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="9169f-474">스크립트를 두 번 클릭 하 여 *Visual Studio*에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="9169f-475">그런 다음 *동작* 클래스 안에 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="9169f-476">*활성 ()* 메서드 코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="9169f-477">이 메서드는 클래스가 초기화 될 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="9169f-478">다음 메서드는 이전에 만든 *Luismanager* 클래스에서 호출 되어 쿼리의 대상인 개체를 확인 한 다음 적절 한 작업을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  <span data-ttu-id="9169f-479">*Findtarget ()* 메서드를 추가 하 여 현재 의도의 대상인 *gameobject* 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="9169f-480">이 메서드는 엔터티에 명시적 대상이 정의 되어 있지 않은 경우 대상의 기본값을 "gazed"로 *GameObject* 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="9169f-481">*Start ()* 및 *Update ()* 메서드는이 클래스에서 사용 하지 않으므로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="9169f-482">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="9169f-483">8 장-응시 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="9169f-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="9169f-484">이 앱을 완료 하는 데 필요한 마지막 클래스는 *응시* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="9169f-485">이 클래스는 현재 사용자의 시각적 포커스에 있는 *GameObject* 에 대 한 참조를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="9169f-486">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="9169f-486">To create this Class:</span></span> 

1.  <span data-ttu-id="9169f-487">**스크립트** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="9169f-488">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> C# 스크립트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="9169f-489">스크립트 이름을 *응시*로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="9169f-490">스크립트를 두 번 클릭 하 여 *Visual Studio*에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="9169f-491">이 클래스에 대해 다음 코드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-491">Insert the following code for this class:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  <span data-ttu-id="9169f-492">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="9169f-493">9 장-장면 설정 완료</span><span class="sxs-lookup"><span data-stu-id="9169f-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="9169f-494">장면의 설정을 완료 하려면 Scripts 폴더에서 만든 각 스크립트를 *계층 패널*의 **기본 카메라** 개체로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="9169f-495">**주 카메라** 를 선택 하 고 *검사기 패널*에서 연결 된 각 스크립트를 볼 수 있어야 하며, 아직 설정 하지 않은 각 스크립트에 대 한 매개 변수가 있다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![카메라 참조 대상을 설정 합니다.](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="9169f-497">이러한 매개 변수를 올바르게 설정 하려면 다음 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="9169f-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="9169f-498">*MicrophoneManager*:</span><span class="sxs-lookup"><span data-stu-id="9169f-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="9169f-499">*계층 패널*에서 **받아쓰기 텍스트** 개체를 **받아쓰기 텍스트** 매개 변수 값 상자로 끌어옵니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="9169f-500">*계층 패널*에서 *동작*:</span><span class="sxs-lookup"><span data-stu-id="9169f-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="9169f-501">**구** 개체를 *구* 참조 대상 상자로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="9169f-502">**원통을** *원통* 참조 대상 상자로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="9169f-503">**큐브를** *큐브* 참조 대상 상자로 끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="9169f-504">*응시*:</span><span class="sxs-lookup"><span data-stu-id="9169f-504">*Gaze*:</span></span>

        - <span data-ttu-id="9169f-505">*응시 최대 거리* 를 **300** (아직 없는 경우)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="9169f-506">결과는 아래 이미지와 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-506">The result should look like the image below:</span></span>

    ![카메라 참조 대상을 표시 합니다 (이제 설정).](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="9169f-508">10 장-Unity 편집기에서 테스트</span><span class="sxs-lookup"><span data-stu-id="9169f-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="9169f-509">장면 설정이 제대로 구현 되었는지 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="9169f-510">다음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-510">Ensure that:</span></span>

-   <span data-ttu-id="9169f-511">모든 스크립트는 **주 카메라** 개체에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="9169f-512">*기본 카메라 검사기 패널* 의 모든 필드가 제대로 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="9169f-513">*Unity 편집기*에서 **재생** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="9169f-514">앱은 연결 된 모던 헤드셋 내에서 실행 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="9169f-515">다음과 같은 몇 가지 길이 발언 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="9169f-516">Unity 콘솔에 기본 오디오 장치 변경에 대 한 오류가 표시 되 면 장면이 예상 대로 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="9169f-517">이는 혼합 현실 포털이이를 포함 하는 헤드셋의 기본 제공 마이크를 처리 하는 방식 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="9169f-518">이 오류가 표시 되 면 장면을 중지 하 고 다시 시작 하 고 예상 대로 작동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="9169f-519">11 장-UWP 솔루션 빌드 및 테스트용으로 로드</span><span class="sxs-lookup"><span data-stu-id="9169f-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="9169f-520">Unity 편집기에서 응용 프로그램이 작동 하는지 확인 한 후에는 빌드 및 배포할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="9169f-521">빌드:</span><span class="sxs-lookup"><span data-stu-id="9169f-521">To Build:</span></span>

1.  <span data-ttu-id="9169f-522">**파일 > 저장**을 클릭 하 여 현재 장면을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="9169f-523">**파일 > 빌드 설정**으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="9169f-524">**Unity C# 프로젝트** 라는 상자를 표시 합니다 (UWP 프로젝트를 만든 후 코드를 보고 디버깅 하는 데 유용).</span><span class="sxs-lookup"><span data-stu-id="9169f-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="9169f-525">열려 있는 **장면 추가**를 클릭 한 다음 **빌드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![빌드 설정 창](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="9169f-527">솔루션을 빌드하는 데 사용할 폴더를 선택 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="9169f-528">*빌드* 폴더를 만들고 해당 폴더 내에서 원하는 적절 한 이름을 사용 하 여 다른 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="9169f-529">**폴더 선택** 을 클릭 하 여 해당 위치에서 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="9169f-530">빌드 폴더 만들기 ![](images/AzureLabs-Lab3-44.png)
    ![빌드 폴더를 선택](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="9169f-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="9169f-531">Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창을 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="9169f-532">로컬 컴퓨터에 배포 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="9169f-533">*Visual Studio*에서 [이전 챕터](#chapter-10--test-in-the-unity-editor)에서 만든 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="9169f-534">**솔루션 플랫폼**에서 **X86**, **로컬 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="9169f-535">**솔루션 구성** 에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="9169f-536">Microsoft HoloLens의 경우 컴퓨터에 테더 링 된 하지 않도록 *원격 컴퓨터*를 설정 하는 것이 더 쉬울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="9169f-537">그러나 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="9169f-538">HoloLens의 **IP 주소** 를 알고 있습니다. *설정 > 네트워크 & 인터넷 > Wi-fi > 고급 옵션*에서 찾을 수 있습니다. IPv4는 사용 해야 하는 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="9169f-539">**개발자 모드가** **설정**되어 있는지 확인 합니다. *개발자를 위한 업데이트 & 보안 > > 설정*에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![앱 배포](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="9169f-541">**빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 컴퓨터에 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="9169f-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="9169f-542">이제 앱이 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="9169f-543">앱이 시작 되 면 _마이크_에 대 한 액세스 권한을 부여 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="9169f-544">*동작 컨트롤러*또는 *음성 입력*을 사용 하거나 *키보드* 를 사용 하 여 **예** 단추를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="9169f-545">12 장-LUIS 서비스 개선</span><span class="sxs-lookup"><span data-stu-id="9169f-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="9169f-546">이 장은 매우 중요 하며, LUIS 서비스의 정확도를 향상 시키는 데 도움이 되므로 몇 번 반복 해야 할 수 있습니다 .이 작업을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-546">This chapter is incredibly important, and may need to be iterated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="9169f-547">LUIS에서 제공 하는 이해 수준을 개선 하려면 새로운 길이 발언을 캡처하고 LUIS 앱을 다시 학습 하는 데 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="9169f-548">예를 들어 "증가" 및 "업사이징"을 이해 하기 위해 학습 된 LUIS가 있을 수 있지만, 앱에서 "확대"와 같은 단어를 이해 하 고 싶으세요?</span><span class="sxs-lookup"><span data-stu-id="9169f-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="9169f-549">응용 프로그램을 몇 번 사용한 후에는 LUIS에 의해 수집 되며 LUIS 포털에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="9169f-550">이 [링크](https://www.luis.ai/home)를 따라 포털 응용 프로그램으로 이동 하 여 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="9169f-551">MS 자격 증명을 사용 하 여 로그인 하면 *앱 이름을*클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="9169f-552">페이지 왼쪽에서 **endpoint 길이 발언 검토** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![길이 발언 검토](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="9169f-554">혼합 현실 응용 프로그램에 의해 LUIS로 전송 된 길이 발언 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![길이 발언 목록](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="9169f-556">일부 강조 된 *엔터티*를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="9169f-557">강조 표시 된 각 단어를 마우스로 가리키면 각 Utterance를 검토 하 고 올바르게 인식 된 엔터티, 잘못 된 엔터티 및 누락 된 엔터티를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="9169f-558">위의 예에서는 "스피어" 라는 단어가 대상으로 강조 표시 된 것을 발견 했으므로 실수를 수정 해야 합니다 .이 작업은 단어를 마우스로 가리키고 **레이블 제거**를 클릭 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="9169f-559">![확인 길이 발언](images/AzureLabs-Lab3-49.png)
![레이블 이미지 제거](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="9169f-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="9169f-560">완전히 잘못 된 길이 발언를 찾으면 화면 오른쪽에 있는 **삭제** 단추를 사용 하 여 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![잘못 된 길이 발언 삭제](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="9169f-562">또는 LUIS가 Utterance를 올바르게 해석 한 경우 **정렬 된 의도에 추가** 단추를 사용 하 여 해당 이해의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![정렬 된 의도에 추가](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="9169f-564">표시 된 모든 길이 발언를 정렬 한 후 페이지를 다시 로드 하 여 더 많은 사용 가능한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="9169f-565">응용 프로그램 이해를 향상 시키기 위해 가능한 한 많은 횟수로이 프로세스를 반복 하는 것이 매우 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="9169f-566">**즐거운 시간 보내세요!**</span><span class="sxs-lookup"><span data-stu-id="9169f-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="9169f-567">완성 된 LUIS 통합 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="9169f-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="9169f-568">축 하 합니다. Azure Language Understanding Intelligence 서비스를 활용 하 여 사용자에 게 표시 되는 내용을 이해 하 고 해당 정보에 대해 조치를 취하는 혼합 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![랩 결과](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="9169f-570">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="9169f-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="9169f-571">연습 1</span><span class="sxs-lookup"><span data-stu-id="9169f-571">Exercise 1</span></span>

<span data-ttu-id="9169f-572">이 응용 프로그램을 사용 하는 동안 개체를 응시 하 고 색을 변경 하도록 요청 하면이 작업을 수행 하는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="9169f-573">응용 프로그램이 바닥 색을 변경 하는 것을 중지 하는 방법을 알아볼 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="9169f-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="9169f-574">연습 2</span><span class="sxs-lookup"><span data-stu-id="9169f-574">Exercise 2</span></span>

<span data-ttu-id="9169f-575">LUIS 및 앱 기능을 확장 하 여 장면의 개체에 대 한 기능을 추가 해 보세요. 예를 들어 사용자에 게 표시 되는 내용에 따라 응시 적중 지점에서 새 개체를 만든 다음 기존 명령과 함께 현재 장면 개체와 함께 해당 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9169f-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
