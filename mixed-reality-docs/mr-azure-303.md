---
title: MR 및 Azure 303-자연 언어 이해 (LUIS)
description: 혼합된 현실 응용 프로그램에서 Azure Intelligence Service LUIS (Language Understanding)를 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, 언어 인식 인텔리전스 서비스, luis, 몰입 형, hololens, vr
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603073"
---
>[!NOTE]
><span data-ttu-id="74079-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="74079-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="74079-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="74079-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="74079-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="74079-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="74079-110">MR 및 Azure 303: 자연 언어 이해 (LUIS)</span><span class="sxs-lookup"><span data-stu-id="74079-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="74079-111">이 과정에서는 Language Understanding Language Understanding API를 사용 하 여 Azure Cognitive Services를 사용 하 여 혼합된 현실 응용 프로그램을 통합 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="74079-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![랩 결과](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="74079-113">*LUIS (language Understanding)* 는 사용자 수 원하는 고유한 단어 추출 통해 같은 사용자 입력에서 의미를 확인 하는 기능을 사용 하 여 응용 프로그램을 제공 하는 Microsoft Azure 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="74079-114">이해 및 입력된 정보를 학습 하 고, 자세한 관련 정보를 사용 하 여 응답할 수 있는 기계 학습을 통해 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="74079-115">자세한 내용은 참조는 [Azure LUIS (Language Understanding) 페이지](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="74079-116">이 과정을 마치면 다음을 수행 하는 일을 할 수 있는 혼합된 현실 몰입 형 헤드셋 응용 프로그램을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="74079-117">사용자 입력된 음성 변환을, 몰입 형 헤드셋에 연결 된 마이크를 사용 하 여 캡처하십시오.</span><span class="sxs-lookup"><span data-stu-id="74079-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="74079-118">캡처된 받아쓰기를 전송 합니다 *Azure Language Understanding Intelligent Service* (*LUIS*).</span><span class="sxs-lookup"><span data-stu-id="74079-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="74079-119">LUIS 추출은 분석할 수 사용자의 요청 의도 확인 하려고 하며 송신 정보를 통해 의미 있는 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="74079-120">개발은 사용자 음성을 사용 및/또는 gaze 장면에 있는 개체의 색과 크기를 변경 하는 일을 할 수 있는 앱 만들기가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="74079-121">컨트롤러 동작의 사용을 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="74079-122">응용 프로그램에서는 사용자의 몫 디자인을 사용 하 여 결과에서는 통합 하는 방법에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="74079-123">이 과정은 Unity 프로젝트를 사용 하 여 Azure 서비스를 통합 하는 방법을 알려 주기 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="74079-124">혼합된 현실 응용 프로그램을 강화 하기 위해이 과정에서 얻는 지식을 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="74079-125">여러 번 학습 LUIS 준비가 되어에 나와 있는 [12 장](#chapter-12--improving-your-luis-service)합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="74079-126">LUIS의 학습을 수행한 회 더 나은 결과 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="74079-127">장치 지원</span><span class="sxs-lookup"><span data-stu-id="74079-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="74079-128">과정</span><span class="sxs-lookup"><span data-stu-id="74079-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="74079-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="74079-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="74079-130"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="74079-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="74079-131">MR 및 Azure 303: 자연 언어 이해 (LUIS)</span><span class="sxs-lookup"><span data-stu-id="74079-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="74079-132">✔️</span><span class="sxs-lookup"><span data-stu-id="74079-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="74079-133">✔️</span><span class="sxs-lookup"><span data-stu-id="74079-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="74079-134">이 코스는 주로 Windows Mixed Reality 몰입 형 (VR) 헤드셋 주력, Microsoft HoloLens이 과정에서 배운 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="74079-135">과정을 따라가려면 정보 HoloLens를 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="74079-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="74079-136">HoloLens를 사용 하는 경우 음성 캡처하는 동안 일부 echo를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74079-137">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="74079-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="74079-138">이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="74079-139">또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 5 월) 작성 시점에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="74079-140">내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 아래에 나열 된 보다 최신 소프트웨어에서 찾을 수 있는 항목을 일치 완벽 하 게 됩니다 있지만 문서 .</span><span class="sxs-lookup"><span data-stu-id="74079-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="74079-141">다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="74079-142">개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용</span><span class="sxs-lookup"><span data-stu-id="74079-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="74079-143">Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="74079-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="74079-144">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="74079-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="74079-145">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="74079-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="74079-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="74079-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="74079-147">A [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md) 하거나 [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여</span><span class="sxs-lookup"><span data-stu-id="74079-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="74079-148">(없으면 헤드셋 내장 마이크와 스피커) 내장 마이크를 사용 하 여 헤드폰 집합</span><span class="sxs-lookup"><span data-stu-id="74079-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="74079-149">Azure 설정 및 LUIS 검색에 대 한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="74079-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="74079-150">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="74079-150">Before you start</span></span>

1.  <span data-ttu-id="74079-151">이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).</span><span class="sxs-lookup"><span data-stu-id="74079-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="74079-152">받아쓰기를 사용 하도록 설정 하려면 컴퓨터를 허용 하려면로 이동 **Windows 설정 > 개인 정보 > 음성 변환, 잉크 입력 및 입력** 단추를 누르고 **켜기 음성 서비스 및 입력 제안을**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="74079-153">이 자습서의 코드를 사용 하면에서 기록 하는 **마이크 장치 기본** 컴퓨터에서 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="74079-154">기본 마이크 장치 음성 캡처를 사용 하려는 것으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="74079-155">헤드셋 내장 마이크에 있는지 확인 옵션 *"내 헤드셋 wear 있습니까 때 헤드셋 마이크 전환"* 에서 켜져 합니다 *혼합 현실 포털* 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![몰입 형 헤드셋 설정](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="74079-157">1 장-Azure Portal 설정</span><span class="sxs-lookup"><span data-stu-id="74079-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="74079-158">사용 하는 *Language Understanding* 서비스가 Azure에서 응용 프로그램에 사용할 수 있도록 서비스의 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="74079-159">에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="74079-160">Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="74079-161">클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="74079-162">일단 로그인 하면 클릭할 **새로 만들기** 왼쪽 위에서 모서리 및 검색 *Language Understanding*를 클릭 하 고 **Enter**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![LUIS 리소스 만들기](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="74079-164">단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="74079-165">새 페이지를 오른쪽 Language Understanding 서비스에 대 한 설명을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="74079-166">선택이 페이지의 왼쪽 아래에 있는 합니다 **만들기** 단추,이 서비스의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="74079-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![LUIS 서비스 만들기-법적 고 지 사항](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="74079-168">한 번 클릭 하면 만들기:</span><span class="sxs-lookup"><span data-stu-id="74079-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="74079-169">원하는 삽입 **이름을** 이 서비스 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="74079-170">선택 된 **구독**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="74079-171">선택 합니다 **가격 책정 계층** 첫 번째 경우, 적절 한 시간 만들기는 *LUIS 서비스*, 무료 계층 (F0 라는)를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="74079-172">사용 가능한 할당이이 과정에 대 한 충분 한 것 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="74079-173">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="74079-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="74079-174">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="74079-175">것이 좋습니다 (예: 이러한 교육 과정)와 같은 일반적인 리소스 그룹에서 단일 프로젝트와 연결 된 모든 Azure 서비스를 유지).</span><span class="sxs-lookup"><span data-stu-id="74079-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="74079-176">추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="74079-177">확인 합니다 **위치** (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="74079-178">위치는 응용 프로그램은 실행할 지역의 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="74079-179">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="74079-180">이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="74079-181">**만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-181">Select **Create**.</span></span>

        ![LUIS 서비스-사용자 입력 만들기](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="74079-183">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="74079-184">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![새 Azure 알림 이미지](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="74079-186">새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-186">Click on the notification to explore your new Service instance.</span></span>

    ![성공적으로 리소스 만들기 알림](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="74079-188">클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="74079-189">새 LUIS 서비스 인스턴스로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![LUIS 키 액세스](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="74079-191">이 자습서에서 응용 프로그램 서비스의 구독 키를 사용 하 여 수행 하는 서비스에 대 한 호출을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="74079-192">*빠른 시작* 페이지의 프로그램 *LUIS API* 서비스에서 첫 번째 단계로 이동 *키 가져오기*, 클릭 **키** (수도 있습니다 이렇게 키 아이콘으로 표시 하 고 서비스 탐색 메뉴에 있는 파란색 하이퍼링크 키를 클릭 하 여).</span><span class="sxs-lookup"><span data-stu-id="74079-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="74079-193">이 서비스를 줄이면 *키*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="74079-194">프로젝트에서 나중에이 필요 하므로 표시 된 키 중 하나가 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="74079-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="74079-195">에 *서비스* 페이지에서 클릭 *Language Understanding Portal* LUIS 앱 내에서 새 서비스를 만드는 데 사용할 수 있는 웹 페이지로 리디렉션되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="74079-196">2 장-Language Understanding Portal</span><span class="sxs-lookup"><span data-stu-id="74079-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="74079-197">이 섹션에서는 LUIS 포털에서 LUIS 앱을 확인 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="74079-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="74079-198">주의 해당 설정 합니다 *엔터티*를 *의도*, 및 *길이 발언* 이 장에서 LUIS 서비스 구축에 첫 번째 단계:도 해야 재 학습 서비스를 여러 번 하므로 보다 정확 하 게 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="74079-199">에 대해서는 서비스의 재 학습 합니다 [장의 마지막](#chapter-12--improving-your-luis-service) 이 물론 있도록 완료 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="74079-200">에 도달 하면 합니다 *Language Understanding Portal*, 없는 경우 이미 Azure portal로 동일한 자격 증명에 로그인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![LUIS 로그인 페이지](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="74079-202">시작 페이지를 찾아 클릭의 맨 아래로 스크롤하여 해야 LUIS를 사용 하 여 처음으로이 경우는 **만들 LUIS 앱** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![LUIS 앱 페이지 만들기](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="74079-204">일단 로그인 하면 클릭 **My apps** (없는 경우 해당 섹션에서 현재).</span><span class="sxs-lookup"><span data-stu-id="74079-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="74079-205">클릭할 수 있습니다 **새 앱 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-205">You can then click on **Create new app**.</span></span>

    ![LUIS-내 앱 이미지](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="74079-207">앱을 제공 된 *이름*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="74079-208">영어가 아닌 언어를 이해할 수 할 앱을 하는 경우 변경 해야 합니다 *문화권* 적절 한 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="74079-209">여기 추가할 수도 있습니다는 *설명* 새 LUIS 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS-새 앱 만들기](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="74079-211">누르면 **수행**를 입력 합니다 *빌드* 새 페이지 *LUIS* 응용 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="74079-212">여기 이해 하려면 몇 가지 중요 한 개념이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="74079-213">*의도*, 다음 사용자에서는 쿼리에서 호출 되는 메서드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="74079-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="74079-214">*의도* 하나 이상 있을 수 있습니다 *엔터티*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="74079-215">*엔터티*, 관련 된 정보를 설명 하는 쿼리의의 구성 요소인 합니다 *의도*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="74079-216">*길이 발언*, 개발자가 해당 LUIS를 사용 하 여 자체 학습 제공은 쿼리의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="74079-217">이러한 개념은 완벽 하 게 지우기 경우 처럼이 코스 명확 하 게 설명으로이 챕터에 걱정 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="74079-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="74079-218">만들어 시작 합니다 *엔터티* 이 과정을 빌드하는 데 필요한 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="74079-219">페이지의 왼쪽에서 클릭 *엔터티*, 클릭 **새 엔터티 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![새 엔터티 만들기](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="74079-221">새 엔터티를 호출 *색*, 해당 유형을 설정 *단순*를 누릅니다 **수행**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![간단한 엔터티-색 만들기](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="74079-223">엔터티를 만드는 데 3 개의 자세한 간단한 라는이 프로세스를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="74079-224">*upsize*</span><span class="sxs-lookup"><span data-stu-id="74079-224">*upsize*</span></span>
    -   <span data-ttu-id="74079-225">*downsize*</span><span class="sxs-lookup"><span data-stu-id="74079-225">*downsize*</span></span>
    -   <span data-ttu-id="74079-226">*target*</span><span class="sxs-lookup"><span data-stu-id="74079-226">*target*</span></span>

<span data-ttu-id="74079-227">결과 아래 이미지와 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-227">The result should look like the image below:</span></span>

![엔터티 만들기의 결과](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="74079-229">이 시점에서 만들 수 있습니다 *의도*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="74079-230">삭제 하지 마십시오 합니다 **None** 의도 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="74079-231">페이지의 왼쪽에서 클릭 **의도**, 클릭 **새 의도 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![새로운 인 텐트 만들기](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="74079-233">새 호출 *의도* **ChangeObjectColor**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="74079-234">이렇게 *의도* 이름은이 과정의 뒷부분에 나오는 코드 내에서 따라서 최상의 결과 사용이 이름을 제공 하는 대로 정확 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="74079-235">일단 의도 페이지로 리디렉션됩니다 이름을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS-의도 페이지](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="74079-237">5 개 이상의 서로 다른 형식으로 라는 텍스트 상자는 표시 됩니다 *길이 발언*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="74079-238">LUIS는 모든 길이 발언을 소문자로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="74079-239">다음 삽입 *Utterance* 상위 텍스트 상자에서 (텍스트를 사용 하 여 현재 *약 5 예제 입력...*</span><span class="sxs-lookup"><span data-stu-id="74079-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="74079-240">)을 누릅니다 **Enter**:</span><span class="sxs-lookup"><span data-stu-id="74079-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="74079-241">새 *Utterance* 아래 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="74079-242">동일한 프로세스를 다음 다음 6 (6) 길이 발언을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="74079-243">사용자가 만든 각 Utterance, 엔터티로 LUIS 사용 해야 하는 단어 식별 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="74079-244">이 예제의 모든 색으로 레이블을 지정 해야는 *색* 엔터티와 대상으로 가능한 모든 참조는 *대상* 엔터티.</span><span class="sxs-lookup"><span data-stu-id="74079-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="74079-245">이렇게 하려면 단어를 클릭 해 보십시오 *cylinder* 선택한 첫 번째 Utterance *대상*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![Utterance 대상 식별](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="74079-247">이제 이라는 단어를 클릭 *빨간색* 선택한 첫 번째 Utterance *색*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![Utterance 엔터티 식별](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="74079-249">다음 줄을 또한 레이블을 위치 *큐브* 이어야 합니다는 *대상*, 및 *검은색* 이어야 합니다는 *색*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="74079-250">단어를 사용 하 여 또한 *'this'* 를 *'그것'*, 및 *'이 object이 '* 를 제공 하 고, 따라서도 관련 되지 않은 대상 유형을 사용할 수 있어야 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="74079-251">모든 대상이 눈에 띄도록 이라는 레이블이 지정 된 엔터티를 가질 때까지 위에서 설명한 프로세스를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="74079-252">참조는 아래 이미지는 데 도움이 필요한 경우.</span><span class="sxs-lookup"><span data-stu-id="74079-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="74079-253">경우 엔터티로으로 레이블을 단어 선택:</span><span class="sxs-lookup"><span data-stu-id="74079-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="74079-254">단일 단어 바로 대 한 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-254">For single words just click them.</span></span>
    > - <span data-ttu-id="74079-255">두 개 이상의 단어 집합의 경우 시작 부분 및 집합의 끝에 다음을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="74079-256">사용할 수는 *토큰 뷰* 토글 단추 사이 전환할 **엔터티 / 토큰 뷰**!</span><span class="sxs-lookup"><span data-stu-id="74079-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="74079-257">결과 보여 주는 아래 이미지에 표시 된 대로 사용 해야 합니다 **엔터티 / 토큰 뷰**:</span><span class="sxs-lookup"><span data-stu-id="74079-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![토큰 및 엔터티 보기](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="74079-259">이 시점에서 키를 눌러 합니다 **학습** 페이지의 오른쪽 위에 있는 단추 및 녹색으로 바뀌도록 하는 데이 작은 round 표시기에 대 한 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="74079-260">LUIS이이 의도 인식할 성공적으로 학습 되었으면 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="74079-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![LUIS 학습](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="74079-262">연습으로 라는 새 의도 만들기 **ChangeObjectSize**, 엔터티를 사용 하 여 *대상*에 *업사이징*, 및 *줄이지*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="74079-263">다음 8 (8) 표현에 대 한 삽입 이전 의도 동일한 프로세스를 수행 *크기* 변경:</span><span class="sxs-lookup"><span data-stu-id="74079-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

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

23. <span data-ttu-id="74079-264">결과 아래 그림과에서 같은 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-264">The result should be like the one in the image below:</span></span>

    ![ChangeObjectSize 토큰을 설정 / 엔터티](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="74079-266">두 의도 한 번 **ChangeObjectColor** 및 **ChangeObjectSize**, 만든 및 클릭을 학습 합니다 **게시** 페이지 위쪽 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![LUIS 서비스 게시](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="74079-268">에 *게시* 페이지 완료 되며 코드에서 액세스할 수 있도록 LUIS 앱을 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="74079-269">드롭다운을 내놓은 *에 게시* 으로 **프로덕션**.</span><span class="sxs-lookup"><span data-stu-id="74079-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="74079-270">설정 된 *표준 시간대* 표준 시간대로 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="74079-271">확인란 **Include 모든 의도 점수를 예측**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="74079-272">클릭할 **프로덕션 슬롯에 게시**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-272">Click on **Publish to Production Slot**.</span></span>

        ![게시 설정](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="74079-274">단원의 *자원과 키*:</span><span class="sxs-lookup"><span data-stu-id="74079-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="74079-275">Azure Portal에서 서비스 인스턴스에 대해 설정 하는 지역을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="74079-276">알 수 있습니다는 **Starter_Key** 요소 아래에 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="74079-277">클릭할 **키 추가** 삽입 합니다 *키* 서비스 인스턴스를 만들 때 Azure Portal에서 가져온입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="74079-278">Azure 및 LUIS 포털은 동일한 사용자에 로그인 하는 경우 제공 됩니다에 대 한 드롭다운 메뉴가 *테 넌 트 이름*를 *구독 이름*, 및 *키* (사용 하려는 Azure Portal에서 이전에 제공 된 동일한 이름을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="74079-279">아래 *끝점*, 키에 해당 하는 끝점의 복사본 삽입 한, 곧 코드에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="74079-280">3 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="74079-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="74079-281">다음은 일반적인 등록 혼합된 현실 등을 사용 하 여 개발 하는 것에 대 한와 따라서 다른 프로젝트에 대 한 좋은 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="74079-282">오픈 *Unity* 누릅니다 **새로 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-282">Open *Unity* and click **New**.</span></span> 

    ![새 Unity 프로젝트를 시작 합니다.](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="74079-284">Unity 프로젝트 이름을 제공 해야 이제 삽입 **MR_LUIS**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="74079-285">프로젝트 형식 설정 되어 있는지 확인 **3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="74079-286">설정 된 **위치** 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다).</span><span class="sxs-lookup"><span data-stu-id="74079-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="74079-287">그런 다음 클릭 **프로젝트 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-287">Then, click **Create project**.</span></span>

    ![새 Unity 프로젝트에 대 한 세부 정보를 제공 합니다.](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="74079-289">Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="74079-290">편집으로 이동 > 기본 설정으로 이동한 다음 새 창에서 **외부 도구**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="74079-291">변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="74079-292">닫기 합니다 **기본 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-292">Close the **Preferences** window.</span></span>

    ![스크립트 편집기 기본 설정을 업데이트 합니다.](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="74079-294">이동한 다음 **파일 > 빌드 설정** 플랫폼 전환 **유니버설 Windows 플랫폼**를 클릭 하 여는 **플랫폼 전환** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![빌드 설정 창, uwp 플랫폼 전환 합니다.](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="74079-296">로 이동 **파일 > 빌드 설정** 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="74079-297">**장치를 대상** 로 설정 된 **모든 장치**</span><span class="sxs-lookup"><span data-stu-id="74079-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="74079-298">Microsoft HoloLens 설정 **대상 장치** 하 *HoloLens*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="74079-299">**빌드 형식** 로 설정 된 **D3D**</span><span class="sxs-lookup"><span data-stu-id="74079-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="74079-300">**SDK** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="74079-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="74079-301">**Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="74079-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="74079-302">**빌드 및 실행** 로 설정 된 **로컬 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="74079-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="74079-303">장면 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="74079-304">선택 하 여이 작업을 수행할 **열고 장면 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="74079-305">창 저장 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="74079-305">A save window will appear.</span></span>
        
            ![추가 백그라운드에서 열기 단추를 클릭](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="74079-307">새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="74079-309">새로 만든 열 **장면** 폴더를 선택한 다음는 *파일 이름*: 텍스트 필드에 입력 **MR_LuisScene**, 키를 누릅니다 **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![새 장면에 이름을 지정 합니다.](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="74079-311">설정에 남아 *빌드 설정*, 지금은 기본값으로 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="74079-312">에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한.</span><span class="sxs-lookup"><span data-stu-id="74079-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![플레이어 설정 열기](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="74079-314">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="74079-315">에 **기타 설정** 탭:</span><span class="sxs-lookup"><span data-stu-id="74079-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="74079-316">**스크립팅 런타임 버전** 있어야 **안정적인** (.NET 3.5와 같음).</span><span class="sxs-lookup"><span data-stu-id="74079-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="74079-317">**백 엔드를 스크립팅** 있어야 **.NET**</span><span class="sxs-lookup"><span data-stu-id="74079-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="74079-318">**API 호환성 수준** 있어야 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="74079-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![다른 설정을 업데이트 합니다.](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="74079-320">내 합니다 **게시 설정** 탭의 **기능**, 확인:</span><span class="sxs-lookup"><span data-stu-id="74079-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="74079-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="74079-321">**InternetClient**</span></span>
        2. <span data-ttu-id="74079-322">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="74079-322">**Microphone**</span></span>

            ![게시 설정을 업데이트 합니다.](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="74079-324">패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X R 설정을 업데이트 합니다.](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="74079-326">년대 *빌드 설정* _Unity C#_  프로젝트는 더 이상 회색으로;이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="74079-327">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="74079-328">장면 및 프로젝트 저장 (**파일 > 저장 장면 파일 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="74079-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="74079-329">4 장-장면 만들기</span><span class="sxs-lookup"><span data-stu-id="74079-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74079-330">건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드로 바로 계속, 다운로드 자유롭게 [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage),으로 프로젝트로 가져올는 [사용자 지정 패키지 ](https://docs.unity3d.com/Manual/AssetPackages.html)를 계속 진행 한 다음 [5 장](#chapter-5--create-the-microphonemanager-class)합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="74079-331">빈 영역을 마우스 오른쪽 단추로 클릭 합니다 *계층 패널*아래에 있는 **3D 개체**, 추가 **평면**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![평면을 만듭니다.](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="74079-333">주의 내에서 마우스 오른쪽 단추로 때 합니다 *계층* 다시 선택한 마지막 개체에도 있는 경우 개체를 더 만들려면 선택한 개체 부모가 될 새 개체의 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="74079-334">빈 공간을 계층 내에서 마우스 왼쪽 단추로 클릭 하 고 마우스 오른쪽 단추로 클릭 한 다음이 문제를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="74079-335">다음 개체를 추가 하려면 위의 절차를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="74079-336">*구*</span><span class="sxs-lookup"><span data-stu-id="74079-336">*Sphere*</span></span>
    2. <span data-ttu-id="74079-337">*원기둥*</span><span class="sxs-lookup"><span data-stu-id="74079-337">*Cylinder*</span></span>
    3. <span data-ttu-id="74079-338">*Cube*</span><span class="sxs-lookup"><span data-stu-id="74079-338">*Cube*</span></span>
    4. <span data-ttu-id="74079-339">*3D 텍스트*</span><span class="sxs-lookup"><span data-stu-id="74079-339">*3D Text*</span></span>

4.  <span data-ttu-id="74079-340">결과 장면 *계층* 아래 이미지 처럼 보여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![장면 계층 설치 합니다.](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="74079-342">마우스 왼쪽 단추로 클릭 합니다 **주 카메라** 살펴볼 것을 선택 하려면를 *검사기 패널* 모든 카메라 개체 표시 됩니다는 해당 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="74079-343">클릭 합니다 **구성 요소 추가** 맨 아래쪽에 있는 단추를 *검사기 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![오디오 소스 추가](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="74079-345">라는 구성 요소에 대 한 검색 *오디오 원본*위와 같이 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="74079-346">되었는지도 확인 합니다 *변환* 주 카메라의 구성 요소 (0,0,0)으로 설정 되 면이 키를 눌러 가능 합니다 **기어** 카메라의 옆에 있는 아이콘 *변환* 구성 요소 선택 하 고 **재설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="74079-347">합니다 *변환* 구성 요소는 다음과 같이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="74079-348">*위치* 로 설정 된 **0, 0, 0**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="74079-349">*회전* 로 설정 된 **0, 0, 0**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="74079-350">Microsoft HoloLens 대 한 다음을 변경 해야의 일부인 합니다 **카메라** 에 있는 구성 요소에 **주 카메라**:</span><span class="sxs-lookup"><span data-stu-id="74079-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="74079-351">**플래그를 지웁니다.** 단색입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="74079-352">**백그라운드** ' 검정, 알파 0'-16 진수 색: #00000000 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="74079-353">마우스 왼쪽 단추로 클릭 합니다 **평면** 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="74079-354">에 *검사기 패널* 설정 된 *변환* 다음 값을 사용 하 여 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="74079-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="74079-355">변환- *위치*</span><span class="sxs-lookup"><span data-stu-id="74079-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="74079-356">**X**</span><span class="sxs-lookup"><span data-stu-id="74079-356">**X**</span></span> | <span data-ttu-id="74079-357">**Y**</span><span class="sxs-lookup"><span data-stu-id="74079-357">**Y**</span></span>                  | <span data-ttu-id="74079-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="74079-358">**Z**</span></span> |
    | <span data-ttu-id="74079-359">0</span><span class="sxs-lookup"><span data-stu-id="74079-359">0</span></span>     | <span data-ttu-id="74079-360">-1</span><span class="sxs-lookup"><span data-stu-id="74079-360">-1</span></span>                     | <span data-ttu-id="74079-361">0</span><span class="sxs-lookup"><span data-stu-id="74079-361">0</span></span>     |


10. <span data-ttu-id="74079-362">마우스 왼쪽 단추로 클릭 합니다 **구체** 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="74079-363">에 *검사기 패널* 설정 된 *변환* 다음 값을 사용 하 여 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="74079-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="74079-364">변환- *위치*</span><span class="sxs-lookup"><span data-stu-id="74079-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="74079-365">**X**</span><span class="sxs-lookup"><span data-stu-id="74079-365">**X**</span></span> | <span data-ttu-id="74079-366">**Y**</span><span class="sxs-lookup"><span data-stu-id="74079-366">**Y**</span></span>                  | <span data-ttu-id="74079-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="74079-367">**Z**</span></span> |
    | <span data-ttu-id="74079-368">2</span><span class="sxs-lookup"><span data-stu-id="74079-368">2</span></span>     | <span data-ttu-id="74079-369">1</span><span class="sxs-lookup"><span data-stu-id="74079-369">1</span></span>                      | <span data-ttu-id="74079-370">2</span><span class="sxs-lookup"><span data-stu-id="74079-370">2</span></span>     |

11. <span data-ttu-id="74079-371">마우스 왼쪽 단추로 클릭 합니다 **Cylinder** 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="74079-372">에 *검사기 패널* 설정 된 *변환* 다음 값을 사용 하 여 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="74079-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="74079-373">변환- *위치*</span><span class="sxs-lookup"><span data-stu-id="74079-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="74079-374">**X**</span><span class="sxs-lookup"><span data-stu-id="74079-374">**X**</span></span> | <span data-ttu-id="74079-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="74079-375">**Y**</span></span>                  | <span data-ttu-id="74079-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="74079-376">**Z**</span></span> |
    | <span data-ttu-id="74079-377">-2</span><span class="sxs-lookup"><span data-stu-id="74079-377">-2</span></span>    | <span data-ttu-id="74079-378">1</span><span class="sxs-lookup"><span data-stu-id="74079-378">1</span></span>                      | <span data-ttu-id="74079-379">2</span><span class="sxs-lookup"><span data-stu-id="74079-379">2</span></span>     |

12. <span data-ttu-id="74079-380">마우스 왼쪽 단추로 클릭 합니다 **큐브** 하 여 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="74079-381">에 *검사기 패널* 설정 된 *변환* 다음 값을 사용 하 여 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="74079-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="74079-382">변환- *위치*</span><span class="sxs-lookup"><span data-stu-id="74079-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="74079-383">변환- *회전*</span><span class="sxs-lookup"><span data-stu-id="74079-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="74079-384">**X**</span><span class="sxs-lookup"><span data-stu-id="74079-384">**X**</span></span> | <span data-ttu-id="74079-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="74079-385">**Y**</span></span>                   | <span data-ttu-id="74079-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="74079-386">**Z**</span></span> |  \| | <span data-ttu-id="74079-387">**X**</span><span class="sxs-lookup"><span data-stu-id="74079-387">**X**</span></span> | <span data-ttu-id="74079-388">**Y**</span><span class="sxs-lookup"><span data-stu-id="74079-388">**Y**</span></span>                  | <span data-ttu-id="74079-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="74079-389">**Z**</span></span> |
    | <span data-ttu-id="74079-390">0</span><span class="sxs-lookup"><span data-stu-id="74079-390">0</span></span>     | <span data-ttu-id="74079-391">1</span><span class="sxs-lookup"><span data-stu-id="74079-391">1</span></span>                       | <span data-ttu-id="74079-392">4</span><span class="sxs-lookup"><span data-stu-id="74079-392">4</span></span>     |  \| | <span data-ttu-id="74079-393">45</span><span class="sxs-lookup"><span data-stu-id="74079-393">45</span></span>    | <span data-ttu-id="74079-394">45</span><span class="sxs-lookup"><span data-stu-id="74079-394">45</span></span>                     | <span data-ttu-id="74079-395">0</span><span class="sxs-lookup"><span data-stu-id="74079-395">0</span></span>     | 

13. <span data-ttu-id="74079-396">마우스 왼쪽 단추로 클릭 합니다 **새 텍스트** 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="74079-397">에 *검사기 패널* 설정 된 *변환* 다음 값을 사용 하 여 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="74079-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="74079-398">변환- *위치*</span><span class="sxs-lookup"><span data-stu-id="74079-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="74079-399">변환- *확장*</span><span class="sxs-lookup"><span data-stu-id="74079-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="74079-400">**X**</span><span class="sxs-lookup"><span data-stu-id="74079-400">**X**</span></span> | <span data-ttu-id="74079-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="74079-401">**Y**</span></span>                  | <span data-ttu-id="74079-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="74079-402">**Z**</span></span> |  \| | <span data-ttu-id="74079-403">**X**</span><span class="sxs-lookup"><span data-stu-id="74079-403">**X**</span></span> | <span data-ttu-id="74079-404">**Y**</span><span class="sxs-lookup"><span data-stu-id="74079-404">**Y**</span></span>               | <span data-ttu-id="74079-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="74079-405">**Z**</span></span> |
    | <span data-ttu-id="74079-406">-2</span><span class="sxs-lookup"><span data-stu-id="74079-406">-2</span></span>    | <span data-ttu-id="74079-407">6</span><span class="sxs-lookup"><span data-stu-id="74079-407">6</span></span>                      | <span data-ttu-id="74079-408">9</span><span class="sxs-lookup"><span data-stu-id="74079-408">9</span></span>     |  \| | <span data-ttu-id="74079-409">0.1</span><span class="sxs-lookup"><span data-stu-id="74079-409">0.1</span></span>   | <span data-ttu-id="74079-410">0.1</span><span class="sxs-lookup"><span data-stu-id="74079-410">0.1</span></span>                 | <span data-ttu-id="74079-411">0.1</span><span class="sxs-lookup"><span data-stu-id="74079-411">0.1</span></span>   | 

14. <span data-ttu-id="74079-412">변경 **글꼴 크기** 에 **텍스트 메시** 구성 요소를 **50**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="74079-413">변경 된 *이름* 의 **텍스트 메시** 개체를 **받아쓰기 텍스트**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![3D 텍스트 개체 만들기](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="74079-415">이제 계층 패널 구조에 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![장면 뷰에서 텍스트 메시](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="74079-417">최종 장면 아래 이미지와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-417">The final scene should look like the image below:</span></span>

    ![장면 뷰입니다.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="74079-419">5 장-MicrophoneManager 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="74079-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="74079-420">첫 번째 스크립트를 만드는 것은 *MicrophoneManager* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="74079-421">다음에 만듭니다는 *LuisManager*의 *행동* 클래스 및 마지막으로 *Gaze* 클래스 (자유롭게도 설명 하지만 이러한 이제 모든 만들기 연결할 각 장).</span><span class="sxs-lookup"><span data-stu-id="74079-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="74079-422">합니다 *MicrophoneManager* 클래스는 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="74079-423">헤드셋 이나 컴퓨터 (중 하나는 기본)에 연결 하 여 녹음 장치를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="74079-424">(의견) 오디오를 캡처하고 받아쓰기를 사용 하 여 문자열로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="74079-425">음성, 일시 중지 되 면 받아쓰기를 제출 합니다 *LuisManager* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="74079-426">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="74079-426">To create this class:</span></span> 

1.  <span data-ttu-id="74079-427">마우스 오른쪽 단추로 클릭 합니다 *프로젝트 패널*를 **만들기 > 폴더**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="74079-428">폴더를 호출 **스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-428">Call the folder **Scripts**.</span></span> 

    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="74079-430">사용 하 여 합니다 **스크립트** 가 만든 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="74079-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="74079-431">그런 다음, 해당 폴더 내에서 마우스 오른쪽 단추로 클릭 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="74079-432">스크립트 이름을 *MicrophoneManager*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="74079-433">두 번 클릭 *MicrophoneManager* 사용 하 여 열려는 *Visual Studio*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="74079-434">파일의 맨 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="74079-435">그런 다음 내에서 다음 변수를 추가 합니다 *MicrophoneManager* 클래스:</span><span class="sxs-lookup"><span data-stu-id="74079-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="74079-436">에 대 한 코드 *Awake()* 하 고 *start ()* 메서드는 이제 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="74079-437">이러한 클래스를 초기화할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-437">These will be called when the class initializes:</span></span>

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
 
7.  <span data-ttu-id="74079-438">이제 앱을 시작 및 음성 캡처를 중지 하 고 전달 하는 메서드를 *LuisManager* 곧 빌드하게 되는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

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

8.  <span data-ttu-id="74079-439">추가 된 *받아쓰기 처리기* 음성을 놓을 때 호출 되는 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="74079-440">이 메서드는 받아쓰기 텍스트를 전달 합니다 *LuisManager* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

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
    > <span data-ttu-id="74079-441">삭제 합니다 *update ()* 메서드가이 클래스는 사용 하지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="74079-442">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="74079-443">이 시점에 표시 되는 오류를 확인할 수 있습니다 합니다 *Unity 편집기 콘솔 패널이*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="74079-444">코드를 참조 하기 때문에 이것이 합니다 *LuisManager* 만든 다음 장에서 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="74079-445">6 장-LUISManager 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="74079-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="74079-446">만들기 위한 시간이 합니다 *LuisManager* Azure LUIS 서비스를 호출 하 게 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="74079-447">이 클래스의 목적은 받아쓰기 텍스트를 수신 하는 것을 *MicrophoneManager* 클래스 및 보낼 합니다 *Azure Language Understanding API* 분석할 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="74079-448">이 클래스를 역직렬화 하는 *JSON* 응답의 적절 한 메서드를 호출 합니다 *동작도* 클래스는 작업을 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="74079-449">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="74079-449">To create this class:</span></span> 

1.  <span data-ttu-id="74079-450">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="74079-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="74079-451">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="74079-452">스크립트 이름을 *LuisManager*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="74079-453">스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="74079-454">파일의 맨 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="74079-455">세 가지 클래스를 만들어 시작 합니다 **내** 는 *LuisManager* 클래스 (동일한 스크립트 파일에서 위의 *start ()* 메서드)를 나타내는 deserialize 된 형식 Azure에서 JSON 응답입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

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

6.  <span data-ttu-id="74079-456">다음으로 내에서 다음 변수를 추가 합니다 *LuisManager* 클래스:</span><span class="sxs-lookup"><span data-stu-id="74079-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="74079-457">해야에서 LUIS 끝점을 이제 배치 (있음 LUIS 포털에서 해야) 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="74079-458">에 대 한 코드를 *Awake()* 메서드는 이제 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="74079-459">이 메서드는 클래스를 초기화할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="74079-460">이제이 응용 프로그램에서 받은 받아쓰기를 사용 하 여 메서드를 *MicrophoneManager* 클래스를 *LUIS*, 다음 받고 응답을 역직렬화 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="74079-461">인스턴스에 전달 되는 의도 및 연결 된 엔터티 값 결정 되 면 합니다 *동작도* 의도 한 동작을 트리거하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

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
 
11. <span data-ttu-id="74079-462">이라는 새 메서드를 만듭니다 *AnalyseResponseElements()* 결과이 읽힙니다 *AnalysedQuery* 엔터티를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="74079-463">전달 인스턴스의 됩니다 해당 엔터티 확인 되 면 합니다 *동작도* 작업에서 사용 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

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

            // Depending on the topmost recognised intent, read the entities name
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
    > <span data-ttu-id="74079-464">삭제 합니다 *start ()* 하 고 *update ()* 메서드가이 클래스에서 사용 하지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="74079-465">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="74079-466">이 시점에 표시 되는 몇 가지 오류를 확인할 수 있습니다 합니다 *Unity 편집기 콘솔 패널이*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="74079-467">코드를 참조 하기 때문에 이것이 합니다 *행동* 다음 장에서 만들려는 클래스.</span><span class="sxs-lookup"><span data-stu-id="74079-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="74079-468">7 장-동작도 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="74079-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="74079-469">합니다 *동작도* 클래스에서 제공 하는 엔터티를 사용 하 여 작업을 트리거할 합니다 *LuisManager* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="74079-470">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="74079-470">To create this class:</span></span> 

1.  <span data-ttu-id="74079-471">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="74079-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="74079-472">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="74079-473">스크립트 이름을 *동작도*입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="74079-474">사용 하 여 열고 스크립트를 두 번 클릭 *Visual Studio*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="74079-475">그런 다음 내에서 다음 변수를 추가 합니다 *동작도* 클래스:</span><span class="sxs-lookup"><span data-stu-id="74079-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="74079-476">추가 된 *Awake()* 메서드 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="74079-477">이 메서드는 클래스를 초기화할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="74079-478">다음 메서드 호출을 *LuisManager* 클래스 (이전에 만든) 인지 쿼리의 대상 개체를 적절 한 조치를 트리거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

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
 
7.  <span data-ttu-id="74079-479">추가 합니다 *FindTarget()* 결정 하기 위해 메서드를 *Gameobject* 현재 의도의 대상입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="74079-480">이 메서드는 대상의 기본값은 *GameObject* 되 "gazed" 명시적 대상이 없습니다. 엔터티에 정의 된 경우.</span><span class="sxs-lookup"><span data-stu-id="74079-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
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
    > <span data-ttu-id="74079-481">삭제 합니다 *start ()* 하 고 *update ()* 메서드가이 클래스에서 사용 하지 것입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="74079-482">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="74079-483">8 장 – 게이즈 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="74079-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="74079-484">마지막으로 클래스는이 앱을 완료 해야 합니다 *Gaze* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="74079-485">이 클래스에 대 한 참조를 업데이트 합니다 *GameObject* 현재 사용자의 visual 포커스가 있는 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="74079-486">이 클래스 만들려면:</span><span class="sxs-lookup"><span data-stu-id="74079-486">To create this Class:</span></span> 

1.  <span data-ttu-id="74079-487">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="74079-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="74079-488">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="74079-489">스크립트 이름을 *Gaze*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="74079-490">사용 하 여 열고 스크립트를 두 번 클릭 *Visual Studio*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="74079-491">이 클래스에 다음 코드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-491">Insert the following code for this class:</span></span>

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
 
5.  <span data-ttu-id="74079-492">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="74079-493">9 장-장면 설치 완료</span><span class="sxs-lookup"><span data-stu-id="74079-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="74079-494">장면의 설치를 완료 하려면 끌어 Scripts 폴더에서 만든 각 스크립트를 **주 카메라** 개체를 *계층 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="74079-495">선택 합니다 **주 카메라** 확인 합니다 *검사기 패널*, 연결 상태는 각 스크립트를 확인할 수 있어야 하 고 아직 설정 된 각 스크립트에 매개 변수가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![카메라 참조 대상을 설정 합니다.](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="74079-497">이러한 매개 변수를 올바르게 설정 하려면 다음이 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="74079-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="74079-498">*MicrophoneManager*:</span><span class="sxs-lookup"><span data-stu-id="74079-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="74079-499">*계층 패널*, 끌어를 **받아쓰기 텍스트** 개체를 **받아쓰기 텍스트** 매개 변수 값 상자.</span><span class="sxs-lookup"><span data-stu-id="74079-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="74079-500">*행동*에서 *계층 패널*:</span><span class="sxs-lookup"><span data-stu-id="74079-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="74079-501">끌어서를 **구체** 개체를 *구체* 참조 대상 상자.</span><span class="sxs-lookup"><span data-stu-id="74079-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="74079-502">끌어서 합니다 **Cylinder** 에 *원기둥* 참조 대상 상자입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="74079-503">끌기 합니다 **큐브** 에 *큐브* 참조 대상 상자입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="74079-504">*Gaze*:</span><span class="sxs-lookup"><span data-stu-id="74079-504">*Gaze*:</span></span>

        - <span data-ttu-id="74079-505">설정 합니다 *Gaze 최대 거리* 하 **300** (아직 없는) 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="74079-506">결과 아래 이미지와 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-506">The result should look like the image below:</span></span>

    ![이제 설정 카메라 참조 대상을 표시 합니다.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="74079-508">10 장-Unity 편집기에서 테스트</span><span class="sxs-lookup"><span data-stu-id="74079-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="74079-509">장면 설정을 제대로 구현 하는 테스트입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="74079-510">다음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-510">Ensure that:</span></span>

-   <span data-ttu-id="74079-511">에 연결 된 모든 스크립트를 **주 카메라** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="74079-512">모든 필드를 *주 카메라 검사기 패널* 올바르게 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="74079-513">키를 눌러 합니다 **재생** 단추를 *Unity 편집기*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="74079-514">앱을 연결된 하는 몰입 형 헤드셋 내에서 실행 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="74079-515">와 같은 몇 가지 길이 발언을 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="74079-516">변경 하는 기본 오디오 장치에 대 한 Unity 콘솔에 오류를 표시 하는 경우 장면 예상 대로 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="74079-517">혼합된 현실 포털에 있는 헤드셋에 대 한 기본 제공 마이크를 사용 하 여 처리 하는 방식 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="74079-518">이 오류가 표시, 단순히 장면 중지 및 다시 시작 하 고으로 작동 해야 하는 경우 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="74079-519">11 장-빌드 및 UWP 솔루션 테스트용으로 로드</span><span class="sxs-lookup"><span data-stu-id="74079-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="74079-520">Unity 편집기에서 응용 프로그램 작동 하는지 확인 한 후를 빌드하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="74079-521">빌드:</span><span class="sxs-lookup"><span data-stu-id="74079-521">To Build:</span></span>

1.  <span data-ttu-id="74079-522">클릭 하 여 현재 장면 저장 **파일 > 저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="74079-523">로 이동 **파일 > 빌드 설정**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="74079-524">라는 상자를 눈금 **Unity C# 프로젝트** (표시 및 UWP 프로젝트에서 생성 되 면 코드를 디버깅 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="74079-525">클릭할 **열려 장면 추가**, 클릭 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![빌드 설정 창](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="74079-527">솔루션을 빌드 하려는 폴더를 선택 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="74079-528">만들기는 *빌드* 폴더 및 해당 폴더 내에서 원하는 적절 한 이름을 다른 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="74079-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="74079-529">클릭 **폴더 선택** 해당 위치에서 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="74079-530">![빌드 폴더를 만듭니다](images/AzureLabs-Lab3-44.png)
    ![선택 빌드 폴더](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="74079-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="74079-531">한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 **파일 탐색기** 빌드 위치는 창입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="74079-532">로컬 컴퓨터에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="74079-533">*Visual Studio*에서 만든 솔루션 파일을 엽니다 합니다 [이전 장](#chapter-10--test-in-the-unity-editor)합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="74079-534">에 **솔루션 플랫폼**를 선택 **x86**를 **로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="74079-535">에 **솔루션 구성** 선택 **디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="74079-536">Microsoft HoloLens 알 수 있습니다 것이 더 쉽게 *원격 컴퓨터*컴퓨터로 테더 링 없습니다 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="74079-537">그러나 또한 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="74079-538">알고는 **IP 주소** 내에서 찾을 수 있는 여 HoloLens의는 *설정 > 네트워크 및 인터넷 > Wi-fi > 고급 옵션*; IPv4는 주소를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="74079-539">확인 **개발자 모드** 됩니다 **에**에; *설정 > 업데이트 및 보안 > 개발자를 위한*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![앱 배포](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="74079-541">로 이동 합니다 **빌드 메뉴** 를 클릭 **솔루션 배포** 컴퓨터에 응용 프로그램을 테스트용으로 로드 하려면.</span><span class="sxs-lookup"><span data-stu-id="74079-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="74079-542">앱 시작 될 준비가 되었습니다. 설치 된 앱 목록에 나타나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="74079-543">시작 되 면 앱 하 라는 메시지가 나타납니다에 대 한 액세스 권한을 부여 합니다 _마이크_합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="74079-544">사용 하 여는 *동작 컨트롤러*, 또는 *음성 입력*, 또는 *키보드* 를 눌러 합니다 **예** 단추.</span><span class="sxs-lookup"><span data-stu-id="74079-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="74079-545">12 장-LUIS 서비스 개선</span><span class="sxs-lookup"><span data-stu-id="74079-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="74079-546">이 장에서 것이 매우 중요 하 고 LUIS 서비스의 정확도 높이 데 도움이 되는 대로 여러 번 시 interated 되도록 해야 할 수 있습니다:이 완료 하면 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-546">This chapter is incredibly important, and may need to be interated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="74079-547">LUIS를 제공한 이해가 수준 향상을 위해 새 길이 발언을 캡처하고 사용 하 여 LUIS 앱을 다시 학습 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="74079-548">예를 들어 LUIS "Increase" 이해 하 고 "업사이징" 교육 받은 수 있지만 "확대"와 같은 단어 이해 하기 위해 앱 있습니다 원하지?</span><span class="sxs-lookup"><span data-stu-id="74079-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="74079-549">응용 프로그램을 몇 번 사용 하면 LUIS에서 수집 된 및 LUIS 포털에서 사용할 수 있는 말씀 하 신 모든 것이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="74079-550">이 포털 응용 프로그램으로 이동 [링크](https://www.luis.ai/home), 하 고 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="74079-551">MS 자격 증명으로 로그인 되 면 클릭 하면 *앱 이름*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="74079-552">클릭 합니다 **끝점 길이 발언 검토** 페이지의 왼쪽에 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![검토 길이 발언](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="74079-554">응용 프로그램에 혼합된 현실에서 LUIS를 보낸 대상이 눈에 띄도록 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74079-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![목록 길이 발언](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="74079-556">강조 표시 된 일부 알 수 있습니다 *엔터티*합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="74079-557">강조 표시 된 각 단어를 마우스로 각 Utterance를 검토 하 고 및 엔터티는 누락 된 엔터티 인식 된 올바르게 잘못 된 엔터티는 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="74079-558">위의 예제에서 찾을 수는 단어 "창"가 강조 표시 되었습니다 대상으로 하므로 마우스로 단어를 마우스로 클릭 하 여 수행 하는 실수를 수정 하는 데 필요한 것 **레이블 제거**합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="74079-559">![확인 길이 발언](images/AzureLabs-Lab3-49.png)
![레이블 이미지 제거](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="74079-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="74079-560">완전히 잘못 된 길이 발언을 발견할 경우 삭제할 수 있습니다를 사용 하는 **삭제** 화면 오른쪽의 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![잘못 된 길이 발언 삭제](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="74079-562">LUIS를 Utterance를 올바르게 해석에 생각 하는 경우 사용 하 여 이해를 확인할 수 있습니다 또는 합니다 **정렬 의도 추가** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="74079-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![정렬 된 의도 추가](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="74079-564">표시 된 모든 길이 발언을 정렬 한 후 해 사용할 수 있는 경우 자세히 보려면 페이지를 다시 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="74079-565">것이 매우 중요 응용 프로그램 이해를 향상 시킬 수 만큼이 단계를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="74079-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="74079-566">**즐거운 시간 보내세요!**</span><span class="sxs-lookup"><span data-stu-id="74079-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="74079-567">완성 된 LUIS 통합 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="74079-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="74079-568">축 하 Azure 언어 인식 인텔리전스 서비스는 사용자의 표시를 이해 하 고 해당 정보에는 act를 활용 하는 혼합된 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![랩 결과](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="74079-570">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="74079-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="74079-571">연습 1</span><span class="sxs-lookup"><span data-stu-id="74079-571">Exercise 1</span></span>

<span data-ttu-id="74079-572">이 응용 프로그램을 사용 하는 동안는 Floor 개체 응시 하 게 요청 하 여 해당 색을 변경 하는 경우이 수행을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74079-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="74079-573">Floor 색 변경에서 응용 프로그램을 중지 하는 방법에 대해 작업할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="74079-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="74079-574">연습 2</span><span class="sxs-lookup"><span data-stu-id="74079-574">Exercise 2</span></span>

<span data-ttu-id="74079-575">확장 된 LUIS 및 앱 기능 장면;에서 개체에 대 한 추가 기능을 추가 해 보십시오. 예를 들어 게이즈 사용자에 따라 적중된 지점을 라는 및 그런 다음 기존 명령을 사용 하 여 현재 장면 개체와 함께 해당 개체를 사용할 수 있는 새 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="74079-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
