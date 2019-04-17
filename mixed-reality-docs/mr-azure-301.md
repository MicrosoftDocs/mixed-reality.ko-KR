---
title: MR 및 Azure 301-언어 번역
description: 혼합된 현실 응용 프로그램에서 Azure Translator Text API를 구현 하는 방법을 알아보려면이 과정을 완료 합니다.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 혼합 현실, academy, unity, 자습서, api, translator 텍스트, hololens, 몰입 형, vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59603609"
---
>[!NOTE]
><span data-ttu-id="65936-104">혼합 현실 Academy 자습서 HoloLens로 설계 되었습니다 (첫 번째 gen) 및 혼합 현실 몰입 형 헤드셋 유의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="65936-105">따라서 해당 장치에 대 한 개발에 대 한 지침 여전히 알아보려는 개발자를 위한이 자습서를 그대로 둘을 고려해 야 하는 것이 생각 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="65936-106">이 자습서는 **_없습니다_** 최신 도구 집합 또는 HoloLens 2에 사용 되는 상호 작용을 사용 하 여 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="65936-107">지원 되는 장치에서 작업을 계속 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="65936-108">새 자습서 시리즈의 나중에 게시는 HoloLens 2에 대 한 개발 하는 방법을 보여주는 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="65936-109">게시 된 경우이 알림은 이러한 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="65936-110">MR 및 Azure 301: 외국어 번역</span><span class="sxs-lookup"><span data-stu-id="65936-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="65936-111">이 과정에서는 번역 기능 Translator Text API를 사용 하 여 Azure Cognitive Services를 사용 하 여 혼합된 현실 응용 프로그램을 추가 하는 방법을 배웁니다.</span><span class="sxs-lookup"><span data-stu-id="65936-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![최종 제품](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="65936-113">Translator Text API는 번역 서비스에서 거의 실시간으로 작동 하는 경우</span><span class="sxs-lookup"><span data-stu-id="65936-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="65936-114">서비스는 클라우드 기반, REST API 호출을 사용 하 여, 앱 수 있으며 다른 언어로 텍스트를 변환 하는 신경망 기계 번역 기술을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="65936-115">자세한 내용은 참조는 [Azure Translator Text API 페이지](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="65936-116">이 과정을 완료 하면 다음을 수행 하는 일을 할 수 있는 혼합된 현실 응용 프로그램을 갖게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="65936-117">사용자가 마이크는 몰입 형 (VR) 헤드셋에 연결 (또는 HoloLens의 내장 마이크)를 말하십시오.</span><span class="sxs-lookup"><span data-stu-id="65936-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="65936-118">앱 받아쓰기 캡처하고 Azure Translator Text API에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="65936-119">변환 결과 Unity 장면에서 간단한 UI 그룹에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="65936-120">이 코스 샘플 Unity 기반 응용 프로그램으로 Translator 서비스에서 결과 가져오는 방법을 배우게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="65936-121">사용자 지정 응용 프로그램을 작성 하려는 경우에 이러한 개념을 적용 하는 것이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="65936-122">장치 지원</span><span class="sxs-lookup"><span data-stu-id="65936-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="65936-123">과정</span><span class="sxs-lookup"><span data-stu-id="65936-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="65936-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="65936-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="65936-125"><a href="immersive-headset-hardware-details.md">몰입 형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="65936-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="65936-126">MR 및 Azure 301: 외국어 번역</span><span class="sxs-lookup"><span data-stu-id="65936-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="65936-127">✔️</span><span class="sxs-lookup"><span data-stu-id="65936-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="65936-128">✔️</span><span class="sxs-lookup"><span data-stu-id="65936-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="65936-129">이 코스는 주로 Windows Mixed Reality 몰입 형 (VR) 헤드셋 주력, Microsoft HoloLens이 과정에서 배운 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="65936-130">과정을 따라가려면 정보 HoloLens를 지원 하기 위해 사용 해야 합니다. 변경 내용에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="65936-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="65936-131">HoloLens를 사용 하는 경우 음성 캡처하는 동안 일부 echo를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65936-132">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="65936-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="65936-133">이 자습서는 Unity 사용 하 여 기본 경험이 있는 개발자 용으로 설계 하 고 C#입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="65936-134">또한 주의 필수 구성 요소 및이 문서에서 작성 된 지침을 나타내는 새로운 테스트 되었으며 (2018 년 5 월) 작성 시점에 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="65936-135">내에서 나열 된 사용 가능한 최신 소프트웨어를 사용 하는 합니다 [도구를 설치](install-the-tools.md) 없습니다 가정이 과정에서 정보를 아래에 나열 된 보다 최신 소프트웨어에서 찾을 수 있는 항목을 일치 완벽 하 게 됩니다 있지만 문서 .</span><span class="sxs-lookup"><span data-stu-id="65936-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="65936-136">다음 하드웨어 및 소프트웨어가이 과정에 대 한 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="65936-137">개발 PC A [Windows Mixed Reality 호환](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 몰입 형 (VR) 헤드셋 개발용</span><span class="sxs-lookup"><span data-stu-id="65936-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="65936-138">Windows 10 Fall Creators Update (또는 이상) 사용 하도록 설정 하는 개발자 모드를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="65936-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="65936-139">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="65936-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="65936-140">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="65936-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="65936-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="65936-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="65936-142">A [Windows Mixed Reality 몰입 형 (VR) 헤드셋](immersive-headset-hardware-details.md) 하거나 [Microsoft HoloLens](hololens-hardware-details.md) 개발자 모드를 설정 하 여</span><span class="sxs-lookup"><span data-stu-id="65936-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="65936-143">(없으면 헤드셋 내장 마이크와 스피커) 내장 마이크를 사용 하 여 헤드폰 집합</span><span class="sxs-lookup"><span data-stu-id="65936-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="65936-144">Azure 설정 및 번역 검색에 대 한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="65936-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="65936-145">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="65936-145">Before you start</span></span>

- <span data-ttu-id="65936-146">이 프로젝트를 구축 하는 문제 발생을 방지 하려면 것이 좋습니다 루트 또는 루트 거의 폴더에이 자습서에 언급 된 프로젝트를 만든 (오래 폴더 경로 빌드 시에는 문제가 발생할 수 있습니다).</span><span class="sxs-lookup"><span data-stu-id="65936-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="65936-147">이 자습서의 코드를 사용 하면 PC에 연결 된 기본 마이크 장치에서 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="65936-148">기본 마이크 장치 음성 캡처를 사용 하려는 장치에 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="65936-149">받아쓰기를 사용 하도록 설정 하려면 PC를 허용 하려면로 이동 **설정 > 개인 정보 > 음성 변환, 잉크 입력 및 입력** 단추를 선택 하 고 **켜기 음성 서비스 및 입력 제안을**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="65936-150">마이크와 연결할 헤드폰 (또는 기본 제공)를 사용 하는 경우, 헤드셋 옵션이 있는지 확인 "내 헤드셋 wear 있습니까 때 헤드셋 마이크 전환"에서 켜져 **설정 > 혼합 현실을 > 오디오 및 음성**.</span><span class="sxs-lookup"><span data-stu-id="65936-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![혼합된 현실 설정](images/AzureLabs-Lab1-00-5.png)

   ![마이크 설정](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="65936-153">이 랩의 몰입 형 헤드셋을 개발 하는 경우 발생할 수 있는 오디오 출력 장치 문제에 유의 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="65936-154">Unity는 unity (Unity 2018.2) 이상 버전에서 수정 되는 문제 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="65936-155">문제는 런타임 시 기본 오디오 출력 장치를 변경 하지 Unity를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="65936-156">해결 방법으로, 위의 단계를 완료 해야 하 고 닫은 다음 다시이 문제가 발생 하는 자체 편집기를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65936-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="65936-157">1 장-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="65936-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="65936-158">Azure의 Translator API를 사용 하려면 응용 프로그램에 사용할 수 있도록 서비스의 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="65936-159">에 로그인 합니다 [Azure Portal](https://portal.azure.com)합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="65936-160">Azure 계정이 아직 없는 경우 새로 만들려면 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="65936-161">클래스 룸 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 새 계정 설정 도움말에 대 한 여력 중 하나를 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="65936-162">일단 로그인 하면 클릭할 **새로 만들기** 위쪽에서 왼쪽 모퉁이 검색 "Translator text API입니다."</span><span class="sxs-lookup"><span data-stu-id="65936-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="65936-163">선택 **입력**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-163">Select **Enter**.</span></span>

    ![새 리소스](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="65936-165">단어 **새로 만들기** 로 대체 되었습니다 **리소스 만들기**, 최신 포털에서입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="65936-166">새 페이지에 대 한 설명을 제공 합니다는 *Translator Text API* 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="65936-167">선택이 페이지의 왼쪽 아래에 있는 합니다 **만들기** 이 연결 서비스를 만들려면 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Translator 텍스트 API 서비스 만들기](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="65936-169">클릭 한 후 **만들기**:</span><span class="sxs-lookup"><span data-stu-id="65936-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="65936-170">원하는 삽입 **이름을** 이 서비스 인스턴스에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="65936-171">적절 한 선택 **구독**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="65936-172">선택 합니다 **가격 책정 계층** 첫 번째 경우, 적절 한 시간 만들기는 *Translator 텍스트 서비스*, 무료 계층 (F0 라는)를 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="65936-173">선택 된 **리소스 그룹** 하거나 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="65936-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="65936-174">리소스 그룹에는 모니터링, 프로 비전, 액세스 제어 및 Azure 자산 모음에 대 한 청구를 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="65936-175">좋습니다 일반적인 리소스 그룹에서 (예: 이러한 labs) 예: 단일 프로젝트와 연결 된 Azure 서비스를 모두 유지).</span><span class="sxs-lookup"><span data-stu-id="65936-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="65936-176">추가 하려는 경우 Azure 리소스 그룹에 대 한 하세요 [리소스 그룹 방문해](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="65936-177">확인 합니다 **위치** (새 리소스 그룹을 만들면) 하는 경우 리소스 그룹에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="65936-178">위치는 응용 프로그램은 실행할 지역의 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="65936-179">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="65936-180">이 서비스에 적용 되는 조건에 이해는 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="65936-181">**만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-181">Select **Create**.</span></span>

        ![만들기 단추를 선택 합니다.](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="65936-183">클릭 한 후 **만들기**만들려는 서비스에 대 한 대기 해야, 1 분이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="65936-184">서비스 인스턴스가 생성 되 면 포털에서 알림이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Azure 서비스 만들기 알림](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="65936-186">새 서비스 인스턴스를 탐색 하려면 알림을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-186">Click on the notification to explore your new Service instance.</span></span> 

    ![리소스 팝업으로 이동 합니다.](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="65936-188">클릭 합니다 **리소스로 이동** 알림에서 새 서비스 인스턴스를 탐색 하는 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="65936-189">새 텍스트 API Translator 서비스 인스턴스로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Translator API 서비스 텍스트 페이지](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="65936-191">이 자습서에서 응용 프로그램 서비스의 구독 키를 사용 하 여 수행 하는 서비스에 대 한 호출을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="65936-192">*빠른 시작* 페이지에 *Translator Text* 서비스를 이동 하 여 첫 번째 단계로 *키 가져오기*를 클릭 하 고 **키** (할 수 있습니다 또한 이렇게 열쇠 아이콘을 가리키는 서비스 탐색 메뉴에 있는 파란색 하이퍼링크 키를 클릭 하 여).</span><span class="sxs-lookup"><span data-stu-id="65936-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="65936-193">이 서비스를 줄이면 *키*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="65936-194">프로젝트에서 나중에이 필요 하므로 표시 된 키 중 하나가 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="65936-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="65936-195">2 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="65936-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="65936-196">설정 하 고 혼합된 현실 몰입 형 헤드셋을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="65936-197">이 과정에 대 한 동작 컨트롤러 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="65936-198">몰입 형 헤드셋 설정만 지원에 필요한 경우 하세요 [이 단계를 따라](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="65936-199">다음 혼합된 현실을 사용 하 여 개발 하는 것에 대 한 일반적인 집합 중인지 이며, 따라서 다른 프로젝트에 대 한 적절 한 템플릿:</span><span class="sxs-lookup"><span data-stu-id="65936-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="65936-200">오픈 *Unity* 누릅니다 **새로 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-200">Open *Unity* and click **New**.</span></span> 

    ![새 Unity 프로젝트를 시작 합니다.](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="65936-202">이제 Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="65936-203">삽입 **MR_Translation**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="65936-204">프로젝트 형식 설정 되어 있는지 확인 **3D**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="65936-205">설정 된 *위치* 적절 한 위치로 (기억에 루트 디렉터리에 가까울수록이 더 좋습니다).</span><span class="sxs-lookup"><span data-stu-id="65936-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="65936-206">그런 다음 클릭 **프로젝트 만들기**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-206">Then, click **Create project**.</span></span>

    ![새 Unity 프로젝트에 대 한 세부 정보를 제공 합니다.](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="65936-208">Unity 열기를 사용 하 여 기본 검사 가치가 **스크립트 편집기** 로 설정 된 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="65936-209">로 이동 **편집 > 기본 설정** 로 이동한 다음 새 창에서 **외부 도구**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="65936-210">변경 **외부 스크립트 편집기** 하 **Visual Studio 2017**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="65936-211">닫기 합니다 **기본 설정** 창입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-211">Close the **Preferences** window.</span></span>

    ![스크립트 편집기 기본 설정을 업데이트 합니다.](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="65936-213">이동한 다음 **파일 > 빌드 설정** 플랫폼 전환 **유니버설 Windows 플랫폼**를 클릭 하 여는 **플랫폼 전환** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![빌드 설정 창, uwp 플랫폼 전환 합니다.](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="65936-215">로 이동 **파일 > 빌드 설정** 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="65936-216">**장치를 대상** 로 설정 된 **모든 장치**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="65936-217">Microsoft HoloLens 설정 **대상 장치** 하 *HoloLens*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="65936-218">**빌드 형식** 로 설정 된 **D3D**</span><span class="sxs-lookup"><span data-stu-id="65936-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="65936-219">**SDK** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="65936-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="65936-220">**Visual Studio 버전** 로 설정 된 **가장 최근에 설치 된**</span><span class="sxs-lookup"><span data-stu-id="65936-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="65936-221">**빌드 및 실행** 로 설정 된 **로컬 컴퓨터**</span><span class="sxs-lookup"><span data-stu-id="65936-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="65936-222">장면 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="65936-223">선택 하 여이 작업을 수행할 **열고 장면 추가**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="65936-224">창 저장 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="65936-224">A save window will appear.</span></span>

            ![추가 백그라운드에서 열기 단추를 클릭](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="65936-226">새 폴더를 만들려면이 고 모든의 미래, 장면에 대 한 다음 선택 합니다 **새 폴더** 새 폴더를 만들려면 단추 이름을 **장면**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="65936-228">새로 만든 열 **장면** 폴더를 선택한 다음는 *파일 이름*: 텍스트 필드에 입력 **MR_TranslationScene**, 키를 누릅니다 **저장**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![새 장면에 이름을 지정 합니다.](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="65936-230">주의 내에서 Unity 장면에 저장 해야 합니다 *자산* 폴더를 Unity 프로젝트와 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="65936-231">백그라운드에서 폴더 (및 다른 유사한 폴더)를 만들기 Unity 프로젝트를 구성 하는 일반적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="65936-232">설정에 남아 *빌드 설정*, 지금은 기본값으로 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="65936-233">에 *빌드 설정* 창을 **플레이어 설정** 단추를 공간에 관련 된 패널이 열립니다이 위치를 *검사기* 위치한.</span><span class="sxs-lookup"><span data-stu-id="65936-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![플레이어 설정 열기](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="65936-235">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="65936-236">에 **기타 설정** 탭:</span><span class="sxs-lookup"><span data-stu-id="65936-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="65936-237">**스크립팅 런타임 버전** 있어야 **안정적인** (.NET 3.5와 같음).</span><span class="sxs-lookup"><span data-stu-id="65936-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="65936-238">**백 엔드를 스크립팅** 있어야 **.NET**</span><span class="sxs-lookup"><span data-stu-id="65936-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="65936-239">**API 호환성 수준** 있어야 **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="65936-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![다른 설정을 업데이트 합니다.](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="65936-241">내 합니다 **게시 설정** 탭의 **기능**, 확인:</span><span class="sxs-lookup"><span data-stu-id="65936-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="65936-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="65936-242">**InternetClient**</span></span>
        2. <span data-ttu-id="65936-243">**Microphone**</span><span class="sxs-lookup"><span data-stu-id="65936-243">**Microphone**</span></span>

            ![게시 설정을 업데이트 합니다.](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="65936-245">패널을 아래쪽의 **xr 하이 설정을** (아래에서 확인할 **게시 설정**), 눈금 **가상 현실 지원**, 있는지는 **Windows Mixed Reality SDK**  추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X R 설정을 업데이트 합니다.](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="65936-247">년대 **빌드 설정**를 *Unity C# 프로젝트* 가 더 이상 회색;이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="65936-248">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="65936-249">장면 및 프로젝트 저장 (**파일 > 저장 장면 파일 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="65936-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="65936-250">3 장-주 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="65936-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="65936-251">건너뛸 하려는 경우는 *Unity 설정* 이 구성 요소, 과정 및 코드에 바로 계속, 자유롭게 [이.unitypackage 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage),으로 프로젝트로 가져올를 [ *사용자 지정 패키지*](https://docs.unity3d.com/Manual/AssetPackages.html)를 선택한 다음에서 계속 [5 장](#chapter-5--create-the-results-class)합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="65936-252">Unity 프로젝트 만들기를 계속 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="65936-253">에 *계층 패널*, 라는 개체를 보면 **주 카메라**, "내부" 응용 프로그램 되 면이 개체에 "head" 관점을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="65936-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="65936-254">사용자 앞에 Unity 대시보드를 선택 합니다 **주 카메라 GameObject**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="65936-255">합니다 *검사기 패널* (일반적으로 대시보드 내에서 오른쪽에 있음)의 다양 한 구성 요소에 표시 됩니다 *GameObject*를 사용 하 여 *변환* 맨 뒤에 *카메라*, 및 기타 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="65936-256">위치가 올바르게 하므로 주 카메라의 변환을 다시 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="65936-257">이 작업을 수행 하려면 선택 합니다 **기어** 카메라의 옆에 있는 아이콘 *변환* 구성 요소 및 선택 **재설정**.</span><span class="sxs-lookup"><span data-stu-id="65936-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![주 카메라 변환을 다시 설정 합니다.](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="65936-259">합니다 *변환* 구성 요소는 다음과 같이 보입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="65936-260">합니다 *위치* 로 설정 된 **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="65936-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="65936-261">*회전* 로 설정 된 **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="65936-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="65936-262">및 *크기 조정* 로 설정 된 **1, 1, 1**</span><span class="sxs-lookup"><span data-stu-id="65936-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![카메라에 대 한 정보를 변환 합니다.](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="65936-264">사용 하 여 다음 합니다 **주 카메라** 선택한 개체를 참조 하십시오는 **구성 요소 추가** 의 맨 아래에 있는 단추를 *검사기 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="65936-265">해당 단추를 선택 하 고 검색 (입력 하거나 *오디오 원본* 섹션을 탐색 하거나 검색 필드에) 라는 구성 요소에 대 한 **오디오 원본** 아래와 같이 선택 (키를 눌러 입력에 또한 작동)입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="65936-266">*오디오 원본* 에 추가할 구성 요소를 **주 카메라**아래 설명 된 대로, 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![오디오 원본 구성 요소를 추가 합니다.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="65936-268">Microsoft HoloLens 대 한 다음을 변경 해야의 일부인 합니다 **카메라** 구성 요소에 **주 카메라**:</span><span class="sxs-lookup"><span data-stu-id="65936-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="65936-269">**플래그를 지웁니다.** 단색입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="65936-270">**백그라운드** ' 검정, 알파 0'-16 진수 색: #00000000 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="65936-271">4 장-설치 디버그 캔버스</span><span class="sxs-lookup"><span data-stu-id="65936-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="65936-272">입력 및 변환의 출력을 표시 하려면 기본 UI를 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="65936-273">이 과정에 대 한 데이터를 표시 하려면 여러 'Text' 개체를 사용 하 여 캔버스 UI 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="65936-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="65936-274">빈 영역을 마우스 오른쪽 단추로 클릭 합니다 *계층 패널*아래에 있는 **UI**, 추가 **캔버스**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![새 캔버스 UI 개체를 추가 합니다.](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="65936-276">선택 된 경우 캔버스 개체를 사용 하 여는 *검사기 패널* ('캔버스' 구성 요소 내)을 변경 **렌더링 모드** 에 **세계 좌표 공간**입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="65936-277">다음으로, 다음 매개 변수를 변경 합니다 *검사기 창의 Rect 변환*:</span><span class="sxs-lookup"><span data-stu-id="65936-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="65936-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="65936-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="65936-279">*Width* -    500</span><span class="sxs-lookup"><span data-stu-id="65936-279">*Width* -    500</span></span>
    3. <span data-ttu-id="65936-280">*높이* -300</span><span class="sxs-lookup"><span data-stu-id="65936-280">*Height* -   300</span></span>
    4. <span data-ttu-id="65936-281">*크기 조정* - **X** 0.13 **Y** 0.13 **Z** 0.13</span><span class="sxs-lookup"><span data-stu-id="65936-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![캔버스에 대 한 rect 변환을 업데이트 합니다.](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="65936-283">마우스 오른쪽 단추로 클릭는 **캔버스** 에 *계층 패널*아래에 있는 **UI**, 추가 **패널**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="65936-284">이렇게 **패널** 텍스트에 장면에 표시 됩니다 하는 경우 배경이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="65936-285">마우스 오른쪽 단추로 클릭는 **패널** 에 *계층 패널*아래에 있는 **UI**, 추가 **텍스트 개체**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="65936-286">총에서 4 개의 UI 텍스트 개체를 만든 때까지 동일한 프로세스를 반복 (힌트: 선택한 첫 번째 'Text' 개체에 있는 경우 단순히 누르면 **Ctrl + 했습니다 '**, 총에서 4 개 생길 때까지 복제할).</span><span class="sxs-lookup"><span data-stu-id="65936-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="65936-287">각각에 대해 **텍스트 개체**선택 하 고 사용 하 여는 아래에서 매개 변수를 설정 하는 테이블의 *검사기 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="65936-288">에 대 한 합니다 *Rect 변환* 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="65936-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="65936-289">이름</span><span class="sxs-lookup"><span data-stu-id="65936-289">Name</span></span>                   | <span data-ttu-id="65936-290">변환- *위치*</span><span class="sxs-lookup"><span data-stu-id="65936-290">Transform - *Position*</span></span>             | <span data-ttu-id="65936-291">너비</span><span class="sxs-lookup"><span data-stu-id="65936-291">Width</span></span>      | <span data-ttu-id="65936-292">높이</span><span class="sxs-lookup"><span data-stu-id="65936-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="65936-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="65936-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="65936-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="65936-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="65936-295">300</span><span class="sxs-lookup"><span data-stu-id="65936-295">300</span></span>        | <span data-ttu-id="65936-296">30</span><span class="sxs-lookup"><span data-stu-id="65936-296">30</span></span>        |
        | <span data-ttu-id="65936-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="65936-297">AzureResponseLabel</span></span>     | <span data-ttu-id="65936-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="65936-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="65936-299">300</span><span class="sxs-lookup"><span data-stu-id="65936-299">300</span></span>        | <span data-ttu-id="65936-300">30</span><span class="sxs-lookup"><span data-stu-id="65936-300">30</span></span>        |
        | <span data-ttu-id="65936-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="65936-301">DictationLabel</span></span>         | <span data-ttu-id="65936-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="65936-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="65936-303">300</span><span class="sxs-lookup"><span data-stu-id="65936-303">300</span></span>        | <span data-ttu-id="65936-304">30</span><span class="sxs-lookup"><span data-stu-id="65936-304">30</span></span>        |
        | <span data-ttu-id="65936-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="65936-305">TranslationResultLabel</span></span> | <span data-ttu-id="65936-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="65936-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="65936-307">300</span><span class="sxs-lookup"><span data-stu-id="65936-307">300</span></span>        | <span data-ttu-id="65936-308">30</span><span class="sxs-lookup"><span data-stu-id="65936-308">30</span></span>        |


    2. <span data-ttu-id="65936-309">에 대 한 합니다 **텍스트 (스크립트)** 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="65936-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="65936-310">이름</span><span class="sxs-lookup"><span data-stu-id="65936-310">Name</span></span>                   | <span data-ttu-id="65936-311">텍스트 모드</span><span class="sxs-lookup"><span data-stu-id="65936-311">Text</span></span>               | <span data-ttu-id="65936-312">글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="65936-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="65936-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="65936-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="65936-314">마이크 상태:</span><span class="sxs-lookup"><span data-stu-id="65936-314">Microphone Status:</span></span> | <span data-ttu-id="65936-315">20</span><span class="sxs-lookup"><span data-stu-id="65936-315">20</span></span>           |
        | <span data-ttu-id="65936-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="65936-316">AzureResponseLabel</span></span>     | <span data-ttu-id="65936-317">Azure 웹 응답</span><span class="sxs-lookup"><span data-stu-id="65936-317">Azure Web Response</span></span> | <span data-ttu-id="65936-318">20</span><span class="sxs-lookup"><span data-stu-id="65936-318">20</span></span>           |
        | <span data-ttu-id="65936-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="65936-319">DictationLabel</span></span>         |   <span data-ttu-id="65936-320">방금 말한:</span><span class="sxs-lookup"><span data-stu-id="65936-320">You just said:</span></span>   | <span data-ttu-id="65936-321">20</span><span class="sxs-lookup"><span data-stu-id="65936-321">20</span></span>           |
        | <span data-ttu-id="65936-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="65936-322">TranslationResultLabel</span></span> |    <span data-ttu-id="65936-323">변환:</span><span class="sxs-lookup"><span data-stu-id="65936-323">Translation:</span></span>    | <span data-ttu-id="65936-324">20</span><span class="sxs-lookup"><span data-stu-id="65936-324">20</span></span>           |

        ![UI 레이블에 대 한 해당 값을 입력 합니다.](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="65936-326">또한, 글꼴 스타일을 확인 **굵게**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="65936-327">이렇게 하면 텍스트를 쉽게 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-327">This will make the text easier to read.</span></span>

        ![굵은 글꼴입니다.](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="65936-329">각 *UI 텍스트 개체* 에서 만든 [5 장](#chapter-5--create-the-results-class)에서 새 *자식* **UI 텍스트 개체**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="65936-330">이러한 자식 응용 프로그램의 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-330">These children will display the output of the application.</span></span> <span data-ttu-id="65936-331">만들 *자식* 의도 한 부모를 마우스 오른쪽 단추로 클릭을 통해 개체 (예: *MicrophoneStatusLabel*)를 선택한 **UI** 를 선택한 **텍스트**.</span><span class="sxs-lookup"><span data-stu-id="65936-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="65936-332">이러한 자식 각각 선택 하 고 사용 하 여는 아래 검사기 창에서 매개 변수를 설정 하는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="65936-333">에 대 한 합니다 **Rect 변환** 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="65936-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="65936-334">이름</span><span class="sxs-lookup"><span data-stu-id="65936-334">Name</span></span>                  | <span data-ttu-id="65936-335">변환- *위치*</span><span class="sxs-lookup"><span data-stu-id="65936-335">Transform - *Position*</span></span> | <span data-ttu-id="65936-336">너비</span><span class="sxs-lookup"><span data-stu-id="65936-336">Width</span></span>      | <span data-ttu-id="65936-337">높이</span><span class="sxs-lookup"><span data-stu-id="65936-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="65936-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="65936-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="65936-339">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="65936-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="65936-340">300</span><span class="sxs-lookup"><span data-stu-id="65936-340">300</span></span>        | <span data-ttu-id="65936-341">30</span><span class="sxs-lookup"><span data-stu-id="65936-341">30</span></span>        |
        | <span data-ttu-id="65936-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="65936-342">AzureResponseText</span></span>     | <span data-ttu-id="65936-343">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="65936-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="65936-344">300</span><span class="sxs-lookup"><span data-stu-id="65936-344">300</span></span>        | <span data-ttu-id="65936-345">30</span><span class="sxs-lookup"><span data-stu-id="65936-345">30</span></span>        |
        | <span data-ttu-id="65936-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="65936-346">DictationText</span></span>         | <span data-ttu-id="65936-347">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="65936-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="65936-348">300</span><span class="sxs-lookup"><span data-stu-id="65936-348">300</span></span>        | <span data-ttu-id="65936-349">30</span><span class="sxs-lookup"><span data-stu-id="65936-349">30</span></span>        |
        | <span data-ttu-id="65936-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="65936-350">TranslationResultText</span></span> | <span data-ttu-id="65936-351">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="65936-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="65936-352">300</span><span class="sxs-lookup"><span data-stu-id="65936-352">300</span></span>        | <span data-ttu-id="65936-353">30</span><span class="sxs-lookup"><span data-stu-id="65936-353">30</span></span>        |

    2. <span data-ttu-id="65936-354">에 대 한 합니다 **텍스트 (스크립트)** 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="65936-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="65936-355">이름</span><span class="sxs-lookup"><span data-stu-id="65936-355">Name</span></span>                  | <span data-ttu-id="65936-356">텍스트 모드</span><span class="sxs-lookup"><span data-stu-id="65936-356">Text</span></span>          | <span data-ttu-id="65936-357">글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="65936-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="65936-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="65936-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="65936-359">??</span><span class="sxs-lookup"><span data-stu-id="65936-359">??</span></span>       | <span data-ttu-id="65936-360">20</span><span class="sxs-lookup"><span data-stu-id="65936-360">20</span></span>           |
        | <span data-ttu-id="65936-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="65936-361">AzureResponseText</span></span>     |      <span data-ttu-id="65936-362">??</span><span class="sxs-lookup"><span data-stu-id="65936-362">??</span></span>       | <span data-ttu-id="65936-363">20</span><span class="sxs-lookup"><span data-stu-id="65936-363">20</span></span>           |
        | <span data-ttu-id="65936-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="65936-364">DictationText</span></span>         |      <span data-ttu-id="65936-365">??</span><span class="sxs-lookup"><span data-stu-id="65936-365">??</span></span>       | <span data-ttu-id="65936-366">20</span><span class="sxs-lookup"><span data-stu-id="65936-366">20</span></span>           |
        | <span data-ttu-id="65936-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="65936-367">TranslationResultText</span></span> |      <span data-ttu-id="65936-368">??</span><span class="sxs-lookup"><span data-stu-id="65936-368">??</span></span>       | <span data-ttu-id="65936-369">20</span><span class="sxs-lookup"><span data-stu-id="65936-369">20</span></span>           |

9. <span data-ttu-id="65936-370">다음으로, 각 텍스트 구성 요소에 대 한 'centre' 맞춤 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![텍스트를 맞춥니다.](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="65936-372">되도록 합니다 **자식 UI 텍스트가** 개체를 쉽게 읽을 수, 변경 해당 *색*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="65936-373">(현재 ' 검은색') 옆에 있는 표시줄에서 클릭 하 여이 작업을 수행할 *Color*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![UI 텍스트 출력에 대 한 값을 해당 입력 합니다.](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="65936-375">그런 다음 새로운 작은, *색* 창에서 변경 합니다 *16 진수 색* 에: **0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="65936-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![색을 파랑으로 업데이트 합니다.](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="65936-377">다음은 하는 방법을 **UI** 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="65936-378">에 *계층 패널*:</span><span class="sxs-lookup"><span data-stu-id="65936-378">In the *Hierarchy Panel*:</span></span>

        ![제공 된 구조 계층 구조를 포함 합니다.](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="65936-380">에 *장면* 하 고 *뷰를 게임*:</span><span class="sxs-lookup"><span data-stu-id="65936-380">In the *Scene* and *Game Views*:</span></span>

        ![장면 및 게임 보기를 동일한 구조에 있습니다.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="65936-382">5 장-결과 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="65936-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="65936-383">생성 해야 하는 첫 번째 스크립트는 *결과* 변환의 결과 확인 하는 방법을 제공 하는 일을 담당 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="65936-384">클래스는 저장 하 고 다음을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="65936-385">Azure에서 응답 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-385">The response result from Azure.</span></span>
- <span data-ttu-id="65936-386">마이크 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-386">The microphone status.</span></span> 
- <span data-ttu-id="65936-387">받아쓰기 (텍스트 음성)의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="65936-388">변환의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-388">The result of the translation.</span></span>

<span data-ttu-id="65936-389">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="65936-389">To create this class:</span></span> 

1.  <span data-ttu-id="65936-390">마우스 오른쪽 단추로 클릭 합니다 *프로젝트 패널*, 한 다음 **만들기 > 폴더**.</span><span class="sxs-lookup"><span data-stu-id="65936-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="65936-391">폴더의 이름을 **스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-391">Name the folder **Scripts**.</span></span> 
 
    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab1-31.png)

    ![스크립트 폴더를 엽니다.](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="65936-394">사용 하 여 합니다 **스크립트** 폴더 만들기, 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65936-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="65936-395">해당 폴더를 마우스 오른쪽 단추로 선택 내에서 다음 **만들기 >** 한 다음  **C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="65936-396">스크립트 이름을 *결과*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-396">Name the script *Results*.</span></span> 

    ![첫 번째 스크립트를 만듭니다.](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="65936-398">두 번 클릭 하 여 새 *결과* 스크립트를 사용 하 여 열고 **Visual Studio**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="65936-399">다음 네임 스페이스를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="65936-400">클래스 내에서 다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-400">Inside the Class insert the following variables:</span></span>

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  <span data-ttu-id="65936-401">추가한 합니다 *Awake()* 메서드는 클래스를 초기화할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="65936-402">마지막으로 UI 다양 한 결과 정보를 출력 하는 일을 담당 하는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  <span data-ttu-id="65936-403">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="65936-404">6 장-만들기 합니다 *MicrophoneManager* 클래스</span><span class="sxs-lookup"><span data-stu-id="65936-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="65936-405">두 번째 클래스를 만드는 것은 *MicrophoneManager*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="65936-406">이 클래스는 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-406">This class is responsible for:</span></span>

- <span data-ttu-id="65936-407">헤드셋 이나 컴퓨터 (중 기본)에 연결 하 여 녹음 장치를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="65936-408">(의견) 오디오를 캡처하고 받아쓰기를 사용 하 여 문자열로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="65936-409">음성, 일시 중지 되 면 변환기 클래스에 받아쓰기를 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="65936-410">원하는 경우에 음성 캡처를 중지할 수 있습니다 하는 메서드를 호스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="65936-411">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="65936-411">To create this class:</span></span> 
1.  <span data-ttu-id="65936-412">두 번 클릭 합니다 **스크립트** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="65936-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="65936-413">마우스 오른쪽 단추로 클릭 합니다 **스크립트** 폴더를 클릭 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="65936-414">스크립트 이름을 *MicrophoneManager*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="65936-415">새 스크립트를 Visual Studio를 사용 하 여 열을 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="65936-416">네임 스페이스의 맨 위에 있는 다음과 같을 수를 업데이트 합니다 *MicrophoneManager* 클래스:</span><span class="sxs-lookup"><span data-stu-id="65936-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="65936-417">그런 다음 내에서 다음 변수를 추가 합니다 *MicrophoneManager* 클래스:</span><span class="sxs-lookup"><span data-stu-id="65936-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  <span data-ttu-id="65936-418">에 대 한 코드를 *Awake()* 하 고 *start ()* 메서드는 이제 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="65936-419">이러한 클래스를 초기화할 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-419">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  <span data-ttu-id="65936-420">할 수 있습니다 *삭제할* 는 *update ()* 이 클래스는 사용 하지 않으므로 메서드.</span><span class="sxs-lookup"><span data-stu-id="65936-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="65936-421">이제 앱을 시작 및 음성 캡처를 중지 하 고 전달 하는 메서드를 *Translator* 곧 빌드하게 되는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="65936-422">다음 코드를 복사 하 고 아래에 붙여 합니다 *start ()* 메서드.</span><span class="sxs-lookup"><span data-stu-id="65936-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > <span data-ttu-id="65936-423">이 응용 프로그램을 만들지 것입니다 하지만 이용 합니다 *StopCapturingAudio()* 메서드도 제공 되어 여기에서 응용 프로그램에서 오디오 캡처를 중지 하는 기능을 구현 하려는 경우.</span><span class="sxs-lookup"><span data-stu-id="65936-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="65936-424">이제 음성을 중지 될 때 호출 되는 받아쓰기 처리기를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="65936-425">이 메서드는 지정 된 텍스트를 전달한 합니다 *Translator* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-425">This method will then pass the dictated text to the *Translator* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. <span data-ttu-id="65936-426">Unity를 반환 하기 전에 Visual Studio에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="65936-427">이 시점에 표시 되는 오류를 확인할 수 있습니다 합니다 *Unity 편집기 콘솔* 패널 ("이름 '변환기'가 없습니다...").</span><span class="sxs-lookup"><span data-stu-id="65936-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="65936-428">코드를 참조 하기 때문에 이것이 합니다 *Translator* 클래스를 만든 다음 장에서 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="65936-429">7 장-Azure 및 translator 서비스 호출</span><span class="sxs-lookup"><span data-stu-id="65936-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="65936-430">만들어야 하는 마지막 스크립트를 *Translator* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="65936-431">이 클래스는 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-431">This class is responsible for:</span></span>

-   <span data-ttu-id="65936-432">응용 프로그램을 인증 *Azure*, exchange에 **인증 토큰**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="65936-433">사용 하 여는 **인증 토큰** 텍스트를 제출 하려면 (에서 받은 *MicrophoneManager* 클래스) 번역할입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="65936-434">변환 된 결과 받고에 전달 된 *결과* UI에 시각화할 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="65936-435">이 클래스 만들려면:</span><span class="sxs-lookup"><span data-stu-id="65936-435">To create this Class:</span></span> 
1.  <span data-ttu-id="65936-436">로 이동 합니다 **스크립트** 이전에 만든 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="65936-437">마우스 오른쪽 단추로 클릭 합니다 **프로젝트 패널**를 **만들기 > C# 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="65936-438">스크립트를 호출할 *Translator*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="65936-439">두 번 클릭 하 여 새 *Translator* 열려는 스크립트 **Visual Studio를 사용 하 여**입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="65936-440">파일의 맨 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="65936-441">그런 다음 내에서 다음 변수를 추가 합니다 *Translator* 클래스:</span><span class="sxs-lookup"><span data-stu-id="65936-441">Then add the following variables inside the *Translator* class:</span></span>

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - <span data-ttu-id="65936-442">언어를 삽입 하는 언어 **enum** 은 예제 일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="65936-443">자유롭게; 하려는 경우 더 추가 합니다 [API는 60 개 이상의 언어를 지원](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (방법 포함).</span><span class="sxs-lookup"><span data-stu-id="65936-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="65936-444">[사용 가능한 언어를 포함 하는 좀 더 대화형 페이지](https://www.microsoft.com/translator/business/languages/), 하지만 페이지가 사이트 언어로 설정 된 경우 작업에 표시 주의 ' en-' (및 네이티브 언어로 가능성이 리디렉션이 Microsoft 사이트).</span><span class="sxs-lookup"><span data-stu-id="65936-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="65936-445">사이트 URL을 변경 하 여 또는 페이지의 맨 아래에 언어를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="65936-446">합니다 **authorizationKey** 위의 코드 조각에서 값 이어야 합니다는 **키** 에 구독할 때 수신 합니다 *Azure Translator Text API*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="65936-447">이 다룬 [1 장](#chapter-1--the-azure-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="65936-448">에 대 한 코드를 *Awake()* 하 고 *start ()* 메서드는 이제 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="65936-449">이 경우 코드는 호출할 *Azure* 권한 부여 키를 사용 하 여를 *토큰*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="65936-450">토큰은 10 분 후 만료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="65936-451">앱에 대 한 시나리오에 따라 여러 번 호출 하는 동일한 코 루틴을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="65936-452">토큰을 가져오려면 코 루틴 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-452">The coroutine to obtain the Token is the following:</span></span>

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > <span data-ttu-id="65936-453">IEnumerator 메서드의 이름을 편집 하는 경우 **GetTokenCoroutine()** 를 업데이트 해야 합니다 *StartCoroutine* 및 *StopCoroutine* 위의 코드에서 문자열 값을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="65936-454">[Unity 설명서에 따라](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), 특정 중지 *코 루틴*, 하는 문자열 값 메서드를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="65936-455">다음으로, 수신한 텍스트 번역을 가져오려면 (메서드로 "지원" stream 바로 아래)는 코 루틴을 추가 합니다 *MicrophoneManager* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="65936-456">이 코드를 보낼 쿼리 문자열을 만듭니다는 *Azure Translator Text API*, 내부 Unity UnityWebRequest 클래스를 사용 하 여 쿼리 문자열을 사용 하 여 끝점에 'Get' 호출을 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="65936-457">결과 변환 결과 개체에서 설정에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="65936-458">아래 코드 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="65936-458">The code below shows the implementation:</span></span>

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. <span data-ttu-id="65936-459">변경 내용을 저장 해야 *Visual Studio* 를 반환 하기 전에 *Unity*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="65936-460">8 장 – Unity 장면 구성</span><span class="sxs-lookup"><span data-stu-id="65936-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="65936-461">다시 Unity 편집기에서 클릭 하 고 끌어서 합니다 *결과* 클래스 *에서* 는 **스크립트** 폴더를 **주 카메라** 개체에는  *계층 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="65936-462">클릭 합니다 **주 카메라** 확인 합니다 *검사기 패널*.</span><span class="sxs-lookup"><span data-stu-id="65936-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="65936-463">내에서 새로 추가 된 점을 확인할 수 있습니다 *스크립트* 구성 요소를 빈 값을 사용 하 여 4 개의 필드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="65936-464">이들은 코드에서 속성에 대 한 출력 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="65936-465">적절 한 끌어 **텍스트** 에서 개체를 *계층 패널* 아래 이미지와 같이 4 개의 해당 슬롯에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![지정 된 값을 사용 하 여 대상 참조를 업데이트 합니다.](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="65936-467">다음을 클릭 하 고 끌어서를 *Translator* 에서 클래스를 **스크립트** 폴더를 **주 카메라** 개체를 *계층 패널*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="65936-468">클릭 한 다음, 끌어서 합니다 *MicrophoneManager* 에서 클래스를 **스크립트** 폴더를 **주 카메라** 개체를 *계층 패널*.</span><span class="sxs-lookup"><span data-stu-id="65936-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="65936-469">마지막으로, 클릭 합니다 **주 카메라** 확인 합니다 *검사기 패널*.</span><span class="sxs-lookup"><span data-stu-id="65936-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="65936-470">끌어 놓은 스크립트에는 두 드롭다운 상자를 사용 하면 언어를 설정 하는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![의도 한 번역 언어는 입력을 확인 합니다.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="65936-472">9 장-혼합된 현실에서 테스트</span><span class="sxs-lookup"><span data-stu-id="65936-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="65936-473">이 시점에서 장면 올바르게 구현 되었는지 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="65936-474">다음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-474">Ensure that:</span></span>

- <span data-ttu-id="65936-475">에 언급 된 모든 설정이 [1 장](#chapter-1--the-azure-portal) 올바르게 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="65936-476">합니다 *결과*, *Translator*, 및 *MicrophoneManager*, 스크립트에 연결 된 합니다 **주 카메라** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="65936-477">배치 했으면 하 *Azure Translator Text API* 서비스 **키** 내 합니다 **authorizationKey** 내에서 변수를 *Translator* 스크립트입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="65936-478">모든 필드를 *주 카메라 검사기 패널* 올바르게 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="65936-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="65936-479">마이크 장면을 실행 하는 경우 작동 (그렇지 않은 경우 연결 된 마이크 인지 확인 합니다 *기본* 장치 및 있다고 [Windows 내에서 올바르게 설정](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span><span class="sxs-lookup"><span data-stu-id="65936-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="65936-480">키를 눌러 몰입 형 헤드셋을 테스트할 수 있습니다 합니다 **재생** 단추를 *Unity 편집기*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="65936-481">앱 연결된 몰입 형 헤드셋을 통해 작동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="65936-482">변경 하는 기본 오디오 장치에 대 한 Unity 콘솔에 오류를 표시 하는 경우 장면 예상 대로 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65936-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="65936-483">혼합된 현실 포털에 있는 헤드셋에 대 한 기본 제공 마이크를 사용 하 여 처리 하는 방식 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="65936-484">이 오류가 표시, 단순히 장면 중지 및 다시 시작 하 고으로 작동 해야 하는 경우 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="65936-485">장 10-UWP 솔루션 및 로컬 컴퓨터에 테스트용으로 로드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="65936-486">이 프로젝트의 Unity 섹션에 필요한 모든 항목이 이제 완료 되 면 Unity에서 작성 하는 시간 이므로 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="65936-487">이동할 **빌드 설정**: **파일 > 빌드 설정...**</span><span class="sxs-lookup"><span data-stu-id="65936-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="65936-488">**빌드 설정** 창에서 클릭 **빌드**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Unity 장면을 빌드하십시오.](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="65936-490">경우에 눈금 **Unity C# 프로젝트**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="65936-491">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-491">Click **Build**.</span></span> <span data-ttu-id="65936-492">Unity가 시작 됩니다는 *파일 탐색기* 창을 만들고 다음에 앱을 빌드하는 폴더를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="65936-493">해당 폴더를 이제 만들고 이름을 *앱*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="65936-494">사용 하 여 다음 합니다 *앱* 폴더 선택 키를 눌러 **폴더 선택**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="65936-495">Unity 프로젝트를 빌드할 예정 된 *앱* 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="65936-496">한 번 Unity (약간의 시간이 걸릴 수 있습니다) 빌드 완료, 열립니다는 *파일 탐색기* 빌드 위치에 있는 창 (작업 표시줄에서 항상 windows에서 위에 나타나지 않을 수 있습니다 있지만 새 추가 대 한 알림을 확인 창)입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="65936-497">11 장-응용 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="65936-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="65936-498">응용 프로그램을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-498">To deploy your application:</span></span>

1.  <span data-ttu-id="65936-499">새 Unity 빌드에 이동 (합니다 *앱* 폴더) 사용 하 여 솔루션 파일을 엽니다 *Visual Studio*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="65936-500">솔루션 구성 선택에서 **디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="65936-501">솔루션 플랫폼에서 선택 **x86**하십시오 **로컬 컴퓨터**합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="65936-502">Microsoft HoloLens 알 수 있습니다 것이 더 쉽게 *원격 컴퓨터*컴퓨터로 테더 링 없습니다 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="65936-503">그러나 또한 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="65936-504">알고는 **IP 주소** 내에서 찾을 수 있는 여 HoloLens의는 *설정 > 네트워크 및 인터넷 > Wi-fi > 고급 옵션*; IPv4는 주소를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="65936-505">확인 *개발자 모드* 됩니다 **에**에; *설정 > 업데이트 및 보안 > 개발자를 위한*합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="65936-507">로 이동 **빌드 메뉴** 를 클릭 **솔루션 배포** 사용자 PC에 응용 프로그램을 테스트용으로 로드 하려면.</span><span class="sxs-lookup"><span data-stu-id="65936-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="65936-508">이제 앱 시작할 준비가 되었습니다. 설치 된 앱 목록에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="65936-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="65936-509">시작 되 면 앱 하 라는 메시지가 나타납니다 마이크에 대 한 액세스 권한을 부여 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="65936-510">클릭 해야 합니다 **예** 단추입니다.</span><span class="sxs-lookup"><span data-stu-id="65936-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="65936-511">번역을 시작할 준비가 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="65936-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="65936-512">완성 된 변환 텍스트 API 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="65936-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="65936-513">축, 음성을 번역 된 텍스트로 변환 하는 Azure 번역 텍스트 API를 활용 하는 혼합된 현실 앱을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![최종 제품입니다.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="65936-515">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="65936-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="65936-516">연습 1</span><span class="sxs-lookup"><span data-stu-id="65936-516">Exercise 1</span></span>

<span data-ttu-id="65936-517">있습니다 텍스트 음성 변환 기능을 추가할 수는 앱에 반환 된 텍스트를 음성으로 변환 되어 있도록?</span><span class="sxs-lookup"><span data-stu-id="65936-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="65936-518">연습 2</span><span class="sxs-lookup"><span data-stu-id="65936-518">Exercise 2</span></span>

<span data-ttu-id="65936-519">사용자가 앱 언어를 변경할 때마다 다시 작성 하지 않아도 되므로 앱 자체 내에서 원본 및 출력 언어 ('from' 및 'to')을 변경할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="65936-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
