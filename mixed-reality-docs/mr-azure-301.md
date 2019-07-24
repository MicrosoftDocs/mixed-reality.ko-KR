---
title: MR 및 Azure 301-언어 번역
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램 내에서 Azure Translator Text API을 구현 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, translator 텍스트, hololens, 몰입 형, vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63554056"
---
>[!NOTE]
><span data-ttu-id="ea1ba-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ea1ba-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ea1ba-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ea1ba-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ea1ba-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ea1ba-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="ea1ba-110">MR 및 Azure 301: 외국어 번역</span><span class="sxs-lookup"><span data-stu-id="ea1ba-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="ea1ba-111">이 과정에서는 Translator Text API와 함께 Azure Cognitive Services를 사용 하 여 혼합 현실 응용 프로그램에 번역 기능을 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![최종 제품](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="ea1ba-113">Translator Text API은 거의 실시간으로 작동 하는 번역 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="ea1ba-114">서비스는 클라우드를 기반으로 하며, REST API 호출을 사용 하 여 앱은 신경망 번역 기술을 사용 하 여 텍스트를 다른 언어로 번역할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="ea1ba-115">자세한 내용은 [Azure Translator Text API 페이지](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="ea1ba-116">이 과정이 완료 되 면 다음을 수행할 수 있는 혼합 현실 응용 프로그램이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="ea1ba-117">사용자는 몰입 형 (VR) 헤드셋 (또는 HoloLens의 기본 제공 마이크)에 연결 된 마이크를 말합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="ea1ba-118">앱이 받아쓰기를 캡처하여 Azure Translator Text API에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="ea1ba-119">번역 결과는 Unity 장면의 간단한 UI 그룹에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="ea1ba-120">이 과정에서는 변환기 서비스에서 Unity 기반 샘플 응용 프로그램으로 결과를 가져오는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="ea1ba-121">빌드할 수 있는 사용자 지정 응용 프로그램에 이러한 개념을 적용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="ea1ba-122">장치 지원</span><span class="sxs-lookup"><span data-stu-id="ea1ba-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ea1ba-123">과정</span><span class="sxs-lookup"><span data-stu-id="ea1ba-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ea1ba-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ea1ba-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ea1ba-125"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="ea1ba-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ea1ba-126">MR 및 Azure 301: 외국어 번역</span><span class="sxs-lookup"><span data-stu-id="ea1ba-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="ea1ba-127">✔️</span><span class="sxs-lookup"><span data-stu-id="ea1ba-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ea1ba-128">✔️</span><span class="sxs-lookup"><span data-stu-id="ea1ba-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ea1ba-129">이 과정에서 주로 Windows Mixed Reality (VR) 헤드셋에 초점을 맞춘 반면,이 과정에서 학습 하는 내용을 Microsoft HoloLens에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="ea1ba-130">과정을 진행할 때 HoloLens를 지원 하기 위해 사용 해야 하는 모든 변경 내용에 대 한 메모를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="ea1ba-131">HoloLens를 사용 하는 경우 음성 캡처 중에 몇 가지 echo를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea1ba-132">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ea1ba-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ea1ba-133">이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ea1ba-134">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="ea1ba-135">[도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="ea1ba-136">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ea1ba-137">모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC</span><span class="sxs-lookup"><span data-stu-id="ea1ba-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ea1ba-138">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="ea1ba-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ea1ba-139">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="ea1ba-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ea1ba-140">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="ea1ba-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ea1ba-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ea1ba-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="ea1ba-142">개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="ea1ba-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="ea1ba-143">기본 제공 마이크가 있는 헤드폰 집합 (헤드셋에 기본 제공 mic 및 스피커가 없는 경우)</span><span class="sxs-lookup"><span data-stu-id="ea1ba-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="ea1ba-144">Azure 설정 및 번역 검색을 위한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="ea1ba-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ea1ba-145">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="ea1ba-145">Before you start</span></span>

- <span data-ttu-id="ea1ba-146">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="ea1ba-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="ea1ba-147">이 자습서의 코드를 사용 하 여 PC에 연결 된 기본 마이크 장치에서 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="ea1ba-148">기본 마이크 장치가 음성 캡처에 사용할 장치로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="ea1ba-149">PC에서 받아쓰기를 사용 하도록 허용 하려면 **설정 > 개인 정보 > 음성, 필기 & 입력** 으로 이동 하 고, **음성 서비스 설정 및 제안 입력**단추를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="ea1ba-150">헤드셋 (또는 기본 제공)에 연결 된 마이크 및 헤드폰을 사용 하는 경우 **설정 > 혼합 현실 > 오디오 및 음성**에서 "헤드셋을 사용할 때 헤드셋 mic로 전환" 옵션이 켜 졌는 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![혼합 현실 설정](images/AzureLabs-Lab1-00-5.png)

   ![마이크 설정](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="ea1ba-153">이 랩에서 모던 헤드셋을 개발 하는 경우 오디오 출력 장치 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="ea1ba-154">이 문제는 unity의 문제 때문에 발생 합니다 .이 문제는 unity (Unity 2018.2)의 이후 버전에서 수정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="ea1ba-155">이 문제는 Unity에서 런타임에 기본 오디오 출력 장치를 변경 하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="ea1ba-156">이 문제를 해결 하려면 위의 단계를 완료 했는지 확인 하 고,이 문제가 자체적으로 표시 되 면 편집기를 닫았다가 다시 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="ea1ba-157">1 장-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="ea1ba-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="ea1ba-158">Azure Translator API를 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="ea1ba-159">[Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ea1ba-160">아직 Azure 계정이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ea1ba-161">교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ea1ba-162">로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 "Translator Text API"를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="ea1ba-163">**Enter 키**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-163">Select **Enter**.</span></span>

    ![새 리소스](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="ea1ba-165">새 단어는 **새** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="ea1ba-166">새 페이지에 *Translator Text API* 서비스에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="ea1ba-167">이 페이지의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Translator Text API 서비스 만들기](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="ea1ba-169">**만들기**를 클릭 하면 다음을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="ea1ba-170">이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="ea1ba-171">적절 한 **구독**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="ea1ba-172">적절 한 **가격 책정 계층** 을 선택 합니다. *Translator Text 서비스*를 처음 만드는 경우 무료 계층 (명명 된 F0)을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="ea1ba-173">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ea1ba-174">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ea1ba-175">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="ea1ba-176">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="ea1ba-177">새 리소스 그룹을 만드는 경우 리소스 그룹의 **위치** 를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ea1ba-178">위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ea1ba-179">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="ea1ba-180">또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="ea1ba-181">**만들기**를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-181">Select **Create**.</span></span>

        ![만들기 단추를 선택 합니다.](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="ea1ba-183">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="ea1ba-184">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Azure 서비스 만들기 알림](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="ea1ba-186">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-186">Click on the notification to explore your new Service instance.</span></span> 

    ![리소스 팝업으로 이동 합니다.](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="ea1ba-188">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="ea1ba-189">새 Translator Text API 서비스 인스턴스로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Translator Text API 서비스 페이지](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="ea1ba-191">이 자습서에서 응용 프로그램은 서비스에 대 한 호출을 수행 해야 하며, 서비스의 구독 키를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="ea1ba-192">*Translator Text* 서비스의 *빠른 시작* 페이지에서 첫 번째 단계로 이동 하 고 *키*를 클릭 한 다음 **키** 를 클릭 합니다 .이를 위해 서비스 탐색 메뉴에 있는 파란색 하이퍼링크 키를 클릭 하 여이를 수행할 수도 있습니다. 키 아이콘으로 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="ea1ba-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="ea1ba-193">이렇게 하면 서비스 *키*가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="ea1ba-194">프로젝트에서 나중에 필요 하므로 표시 된 키 중 하나를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="ea1ba-195">2 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="ea1ba-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="ea1ba-196">혼합 현실 모던 헤드셋을 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="ea1ba-197">이 과정에서는 동작 컨트롤러가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="ea1ba-198">몰입 형 헤드셋을 설정 하는 데 지원이 필요한 경우 [다음 단계를 수행](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality)하세요.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="ea1ba-199">다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정 이며, 따라서 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="ea1ba-200">*Unity* 를 열고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-200">Open *Unity* and click **New**.</span></span> 

    ![새 Unity 프로젝트를 시작 합니다.](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="ea1ba-202">이제 Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="ea1ba-203">**MR_Translation**을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="ea1ba-204">프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="ea1ba-205">위치를 적절 한 *위치* 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ea1ba-206">그런 다음 **프로젝트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-206">Then, click **Create project**.</span></span>

    ![새 Unity 프로젝트에 대 한 세부 정보를 제공 합니다.](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="ea1ba-208">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ea1ba-209">**> 기본 설정 편집** 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ea1ba-210">**외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ea1ba-211">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-211">Close the **Preferences** window.</span></span>

    ![스크립트 편집기 기본 설정을 업데이트 합니다.](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="ea1ba-213">그런 다음 **파일 > 빌드 설정** 으로 이동 하 고 플랫폼 **전환** 단추를 클릭 하 여 플랫폼을 **유니버설 Windows 플랫폼**로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![빌드 설정 창에서 플랫폼을 UWP로 전환 합니다.](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="ea1ba-215">**파일 > 빌드 설정** 으로 이동 하 고 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="ea1ba-216">**대상 장치** 는 **임의의 장치로**설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="ea1ba-217">Microsoft HoloLens의 경우 **대상 장치** 를 *HoloLens*로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="ea1ba-218">**빌드 형식이** **D3D** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="ea1ba-219">**SDK** 가 **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="ea1ba-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="ea1ba-220">**Visual Studio 버전이** **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="ea1ba-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="ea1ba-221">**빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="ea1ba-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="ea1ba-222">장면을 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="ea1ba-223">이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="ea1ba-224">저장 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-224">A save window will appear.</span></span>

            ![열린 장면 추가 단추를 클릭 합니다.](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="ea1ba-226">이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을**로 지정한 다음</span><span class="sxs-lookup"><span data-stu-id="ea1ba-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="ea1ba-228">새로 만든 **장면** 폴더를 연 다음 *파일 이름*: 텍스트 필드에 **MR_TranslationScene**를 입력 하 고 **저장**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![새 장면에 이름을 지정 합니다.](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="ea1ba-230">Unity 프로젝트와 연결 되어 있어야 하므로 *자산* 폴더 내에 unity 장면을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="ea1ba-231">배경 폴더 (및 기타 유사한 폴더)를 만드는 것은 Unity 프로젝트를 구조화 하는 일반적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="ea1ba-232">*빌드 설정*의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="ea1ba-233">*빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![플레이어 설정을 엽니다.](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="ea1ba-235">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="ea1ba-236">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="ea1ba-237">**Scripting Runtime 버전** 은 **안정적** 이어야 합니다 (.net 3.5 해당).</span><span class="sxs-lookup"><span data-stu-id="ea1ba-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="ea1ba-238">**Scripting 백엔드** 는 **.net** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="ea1ba-239">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![다른 설정을 업데이트 합니다.](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="ea1ba-241">**게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="ea1ba-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ea1ba-242">**InternetClient**</span></span>
        2. <span data-ttu-id="ea1ba-243">**마이크로**</span><span class="sxs-lookup"><span data-stu-id="ea1ba-243">**Microphone**</span></span>

            ![게시 설정을 업데이트 하는 중입니다.](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="ea1ba-245">패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X R 설정을 업데이트 합니다.](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="ea1ba-247">**빌드 설정**으로 돌아가서 *Unity C# 프로젝트가* 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="ea1ba-248">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="ea1ba-249">장면 및 프로젝트를 저장 합니다 (**파일 > 장면/파일 저장 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="ea1ba-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="ea1ba-250">3 장-기본 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="ea1ba-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea1ba-251">이 과정의 *Unity 설정* 구성 요소를 건너뛰고 계속 해 서 코드를 계속 사용 하려면 [unitypackage를 다운로드](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)하 여 프로젝트에 [*사용자 지정 패키지로*](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 [5 장](#chapter-5--create-the-results-class)에서 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="ea1ba-252">Unity 프로젝트를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="ea1ba-253">*계층 패널*에서 **주 카메라**라는 개체를 찾을 수 있습니다 .이 개체는 응용 프로그램 "내부"에 있는 경우의 "헤드" 관점을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="ea1ba-254">앞의 Unity 대시보드를 사용 하 여 **기본 카메라 GameObject**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="ea1ba-255">*검사기 패널* (일반적으로 대시보드 내에서 오른쪽에 있음)에는 해당 *GameObject*의 다양 한 구성 요소, 위쪽의 *변환* , *카메라*및 기타 구성 요소가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="ea1ba-256">기본 카메라의 변환을 다시 설정 해야 올바른 위치에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="ea1ba-257">이렇게 하려면 카메라의 *변형* 구성 요소 옆에 있는 **기어** 아이콘을 선택 하 고 **다시 설정**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![기본 카메라 변환을 다시 설정 합니다.](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="ea1ba-259">*변환* 구성 요소는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="ea1ba-260">*위치* 는 **0, 0,** 0으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="ea1ba-261">*회전이* **0, 0, 0** 으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="ea1ba-262">및 *소수 자릿수* 는 **1, 1, 1** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![카메라에 대 한 변환 정보](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="ea1ba-264">그런 다음 **기본 카메라** 개체를 선택 하 고 *검사기 패널*의 맨 아래에 있는 **구성 요소 추가** 단추를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="ea1ba-265">이 단추를 선택 하 고 아래와 같이 **오디오 원본** 이라는 구성 요소에 대 한 *오디오 소스* 를 검색 필드에 입력 하거나 섹션을 탐색 하 여 검색 하 고 선택한 다음 선택 합니다. (또한 enter 키를 누르면 작동 함)</span><span class="sxs-lookup"><span data-stu-id="ea1ba-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="ea1ba-266">아래와 같이 *오디오 원본* 구성 요소가 **기본 카메라**에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![오디오 원본 구성 요소를 추가 합니다.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="ea1ba-268">Microsoft HoloLens의 경우 **기본 카메라**의 **카메라** 구성 요소에 포함 되는 다음도 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="ea1ba-269">**플래그 지우기:** 단색입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="ea1ba-270">**배경** ' Black, Alpha 0 ' – 16 진수 색: #00000000.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="ea1ba-271">4 장-디버그 캔버스 설정</span><span class="sxs-lookup"><span data-stu-id="ea1ba-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="ea1ba-272">변환의 입력 및 출력을 표시 하려면 기본 UI를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="ea1ba-273">이 과정에서는 데이터를 표시 하는 여러 ' Text ' 개체를 포함 하는 Canvas UI 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="ea1ba-274">*계층 패널*의 빈 영역을 마우스 오른쪽 단추로 클릭 하 고 **UI**에서 **캔버스**를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![새 Canvas UI 개체를 추가 합니다.](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="ea1ba-276">Canvas 개체가 선택 된 상태에서 ' Canvas ' 구성 요소 내의 *검사기 패널* 에서 **렌더링 모드** 를 **세계 공간**으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="ea1ba-277">다음으로, *검사기 패널의 Rect 변환*에서 다음 매개 변수를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="ea1ba-278">*POS*    X 0 Z 40 -  </span><span class="sxs-lookup"><span data-stu-id="ea1ba-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="ea1ba-279">*너비* -500</span><span class="sxs-lookup"><span data-stu-id="ea1ba-279">*Width* -    500</span></span>
    3. <span data-ttu-id="ea1ba-280">*높이* -300</span><span class="sxs-lookup"><span data-stu-id="ea1ba-280">*Height* -   300</span></span>
    4. <span data-ttu-id="ea1ba-281">*크기 조정* - **X** 0.13 **Y** 0.13 **Z** 0.13</span><span class="sxs-lookup"><span data-stu-id="ea1ba-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![캔버스의 rect 변환을 업데이트 합니다.](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="ea1ba-283">*계층 패널*의 **UI**아래에서 **캔버스** 를 마우스 오른쪽 단추로 클릭 하 고 **패널**을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="ea1ba-284">이 **패널** 은 장면에 표시 되는 텍스트에 대 한 배경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="ea1ba-285">*계층 패널*의 **패널** 에서 **UI**를 마우스 오른쪽 단추로 클릭 하 고 **텍스트 개체**를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="ea1ba-286">총 4 개의 UI 텍스트 개체를 만들 때까지 동일한 프로세스를 반복 합니다 (힌트: 첫 번째 ' 텍스트 ' 개체가 선택 된 경우 **' ctrl ' + d '** 를 눌러 합계를 4 개까지)를 복제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="ea1ba-287">각 **텍스트 개체**에 대해 선택 하 고 아래 표를 사용 하 여 *검사기 패널*에서 매개 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="ea1ba-288">*Rect Transform* 구성 요소의 경우:</span><span class="sxs-lookup"><span data-stu-id="ea1ba-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="ea1ba-289">이름</span><span class="sxs-lookup"><span data-stu-id="ea1ba-289">Name</span></span>                   | <span data-ttu-id="ea1ba-290">변환 *위치*</span><span class="sxs-lookup"><span data-stu-id="ea1ba-290">Transform - *Position*</span></span>             | <span data-ttu-id="ea1ba-291">너비</span><span class="sxs-lookup"><span data-stu-id="ea1ba-291">Width</span></span>      | <span data-ttu-id="ea1ba-292">높이</span><span class="sxs-lookup"><span data-stu-id="ea1ba-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="ea1ba-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="ea1ba-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="ea1ba-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="ea1ba-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="ea1ba-295">300</span><span class="sxs-lookup"><span data-stu-id="ea1ba-295">300</span></span>        | <span data-ttu-id="ea1ba-296">30</span><span class="sxs-lookup"><span data-stu-id="ea1ba-296">30</span></span>        |
        | <span data-ttu-id="ea1ba-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="ea1ba-297">AzureResponseLabel</span></span>     | <span data-ttu-id="ea1ba-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="ea1ba-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="ea1ba-299">300</span><span class="sxs-lookup"><span data-stu-id="ea1ba-299">300</span></span>        | <span data-ttu-id="ea1ba-300">30</span><span class="sxs-lookup"><span data-stu-id="ea1ba-300">30</span></span>        |
        | <span data-ttu-id="ea1ba-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="ea1ba-301">DictationLabel</span></span>         | <span data-ttu-id="ea1ba-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="ea1ba-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="ea1ba-303">300</span><span class="sxs-lookup"><span data-stu-id="ea1ba-303">300</span></span>        | <span data-ttu-id="ea1ba-304">30</span><span class="sxs-lookup"><span data-stu-id="ea1ba-304">30</span></span>        |
        | <span data-ttu-id="ea1ba-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="ea1ba-305">TranslationResultLabel</span></span> | <span data-ttu-id="ea1ba-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="ea1ba-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="ea1ba-307">300</span><span class="sxs-lookup"><span data-stu-id="ea1ba-307">300</span></span>        | <span data-ttu-id="ea1ba-308">30</span><span class="sxs-lookup"><span data-stu-id="ea1ba-308">30</span></span>        |


    2. <span data-ttu-id="ea1ba-309">**텍스트 (스크립트)** 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="ea1ba-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="ea1ba-310">이름</span><span class="sxs-lookup"><span data-stu-id="ea1ba-310">Name</span></span>                   | <span data-ttu-id="ea1ba-311">텍스트 모드</span><span class="sxs-lookup"><span data-stu-id="ea1ba-311">Text</span></span>               | <span data-ttu-id="ea1ba-312">글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="ea1ba-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="ea1ba-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="ea1ba-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="ea1ba-314">마이크 상태:</span><span class="sxs-lookup"><span data-stu-id="ea1ba-314">Microphone Status:</span></span> | <span data-ttu-id="ea1ba-315">20</span><span class="sxs-lookup"><span data-stu-id="ea1ba-315">20</span></span>           |
        | <span data-ttu-id="ea1ba-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="ea1ba-316">AzureResponseLabel</span></span>     | <span data-ttu-id="ea1ba-317">Azure 웹 응답</span><span class="sxs-lookup"><span data-stu-id="ea1ba-317">Azure Web Response</span></span> | <span data-ttu-id="ea1ba-318">20</span><span class="sxs-lookup"><span data-stu-id="ea1ba-318">20</span></span>           |
        | <span data-ttu-id="ea1ba-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="ea1ba-319">DictationLabel</span></span>         |   <span data-ttu-id="ea1ba-320">앞서 언급 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-320">You just said:</span></span>   | <span data-ttu-id="ea1ba-321">20</span><span class="sxs-lookup"><span data-stu-id="ea1ba-321">20</span></span>           |
        | <span data-ttu-id="ea1ba-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="ea1ba-322">TranslationResultLabel</span></span> |    <span data-ttu-id="ea1ba-323">변환</span><span class="sxs-lookup"><span data-stu-id="ea1ba-323">Translation:</span></span>    | <span data-ttu-id="ea1ba-324">20</span><span class="sxs-lookup"><span data-stu-id="ea1ba-324">20</span></span>           |

        ![UI 레이블에 해당 하는 값을 입력 합니다.](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="ea1ba-326">또한 글꼴 스타일을 **굵게 표시**합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="ea1ba-327">이렇게 하면 텍스트를 더 쉽게 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-327">This will make the text easier to read.</span></span>

        ![굵은 글꼴입니다.](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="ea1ba-329">[5 장](#chapter-5--create-the-results-class)에서 만든 각 *ui 텍스트 개체* 에 대해 새 *자식* **ui 텍스트 개체**를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="ea1ba-330">이러한 자식은 응용 프로그램의 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-330">These children will display the output of the application.</span></span> <span data-ttu-id="ea1ba-331">원하는 부모 (예: *MicrophoneStatusLabel*)를 마우스 오른쪽 단추로 클릭 한 다음 **UI** 를 선택 하 고 **텍스트**를 선택 하 여 *자식* 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="ea1ba-332">이러한 각 자식에 대해 선택 하 고 아래 표를 사용 하 여 검사기 패널에서 매개 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="ea1ba-333">**Rect Transform** 구성 요소의 경우:</span><span class="sxs-lookup"><span data-stu-id="ea1ba-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="ea1ba-334">이름</span><span class="sxs-lookup"><span data-stu-id="ea1ba-334">Name</span></span>                  | <span data-ttu-id="ea1ba-335">변환 *위치*</span><span class="sxs-lookup"><span data-stu-id="ea1ba-335">Transform - *Position*</span></span> | <span data-ttu-id="ea1ba-336">너비</span><span class="sxs-lookup"><span data-stu-id="ea1ba-336">Width</span></span>      | <span data-ttu-id="ea1ba-337">높이</span><span class="sxs-lookup"><span data-stu-id="ea1ba-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="ea1ba-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="ea1ba-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="ea1ba-339">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="ea1ba-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="ea1ba-340">300</span><span class="sxs-lookup"><span data-stu-id="ea1ba-340">300</span></span>        | <span data-ttu-id="ea1ba-341">30</span><span class="sxs-lookup"><span data-stu-id="ea1ba-341">30</span></span>        |
        | <span data-ttu-id="ea1ba-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="ea1ba-342">AzureResponseText</span></span>     | <span data-ttu-id="ea1ba-343">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="ea1ba-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="ea1ba-344">300</span><span class="sxs-lookup"><span data-stu-id="ea1ba-344">300</span></span>        | <span data-ttu-id="ea1ba-345">30</span><span class="sxs-lookup"><span data-stu-id="ea1ba-345">30</span></span>        |
        | <span data-ttu-id="ea1ba-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="ea1ba-346">DictationText</span></span>         | <span data-ttu-id="ea1ba-347">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="ea1ba-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="ea1ba-348">300</span><span class="sxs-lookup"><span data-stu-id="ea1ba-348">300</span></span>        | <span data-ttu-id="ea1ba-349">30</span><span class="sxs-lookup"><span data-stu-id="ea1ba-349">30</span></span>        |
        | <span data-ttu-id="ea1ba-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="ea1ba-350">TranslationResultText</span></span> | <span data-ttu-id="ea1ba-351">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="ea1ba-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="ea1ba-352">300</span><span class="sxs-lookup"><span data-stu-id="ea1ba-352">300</span></span>        | <span data-ttu-id="ea1ba-353">30</span><span class="sxs-lookup"><span data-stu-id="ea1ba-353">30</span></span>        |

    2. <span data-ttu-id="ea1ba-354">**텍스트 (스크립트)** 구성 요소:</span><span class="sxs-lookup"><span data-stu-id="ea1ba-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="ea1ba-355">이름</span><span class="sxs-lookup"><span data-stu-id="ea1ba-355">Name</span></span>                  | <span data-ttu-id="ea1ba-356">텍스트 모드</span><span class="sxs-lookup"><span data-stu-id="ea1ba-356">Text</span></span>          | <span data-ttu-id="ea1ba-357">글꼴 크기</span><span class="sxs-lookup"><span data-stu-id="ea1ba-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="ea1ba-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="ea1ba-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="ea1ba-359">??</span><span class="sxs-lookup"><span data-stu-id="ea1ba-359">??</span></span>       | <span data-ttu-id="ea1ba-360">20</span><span class="sxs-lookup"><span data-stu-id="ea1ba-360">20</span></span>           |
        | <span data-ttu-id="ea1ba-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="ea1ba-361">AzureResponseText</span></span>     |      <span data-ttu-id="ea1ba-362">??</span><span class="sxs-lookup"><span data-stu-id="ea1ba-362">??</span></span>       | <span data-ttu-id="ea1ba-363">20</span><span class="sxs-lookup"><span data-stu-id="ea1ba-363">20</span></span>           |
        | <span data-ttu-id="ea1ba-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="ea1ba-364">DictationText</span></span>         |      <span data-ttu-id="ea1ba-365">??</span><span class="sxs-lookup"><span data-stu-id="ea1ba-365">??</span></span>       | <span data-ttu-id="ea1ba-366">20</span><span class="sxs-lookup"><span data-stu-id="ea1ba-366">20</span></span>           |
        | <span data-ttu-id="ea1ba-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="ea1ba-367">TranslationResultText</span></span> |      <span data-ttu-id="ea1ba-368">??</span><span class="sxs-lookup"><span data-stu-id="ea1ba-368">??</span></span>       | <span data-ttu-id="ea1ba-369">20</span><span class="sxs-lookup"><span data-stu-id="ea1ba-369">20</span></span>           |

9. <span data-ttu-id="ea1ba-370">다음으로 각 텍스트 구성 요소에 대 한 ' 중앙 ' 맞춤 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![텍스트 맞춤.](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="ea1ba-372">**자식 UI 텍스트** 개체를 쉽게 읽을 수 있도록 하려면 *색*을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="ea1ba-373">*색*옆에 있는 막대 (현재 ' 검은색 ')를 클릭 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![UI 텍스트 출력에 해당 하는 값을 입력 합니다.](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="ea1ba-375">그런 다음, 작은 *색* 창에서 *16 진수 색* 을 다음과 같이 변경 합니다. **0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="ea1ba-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![색을 파랑으로 업데이트 합니다.](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="ea1ba-377">**UI** 를 표시 하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="ea1ba-378">*계층 패널*에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-378">In the *Hierarchy Panel*:</span></span>

        ![제공 된 구조체에 계층이 있습니다.](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="ea1ba-380">*장면* 및 *게임 보기*에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-380">In the *Scene* and *Game Views*:</span></span>

        ![장면 및 게임 보기가 동일한 구조에 있어야 합니다.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="ea1ba-382">5 장-결과 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="ea1ba-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="ea1ba-383">만들어야 하는 첫 번째 스크립트는 변환 결과를 확인 하는 방법을 제공 하는 *결과* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="ea1ba-384">클래스는 다음을 저장 하 고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="ea1ba-385">Azure의 응답 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-385">The response result from Azure.</span></span>
- <span data-ttu-id="ea1ba-386">마이크 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-386">The microphone status.</span></span> 
- <span data-ttu-id="ea1ba-387">받아쓰기 (음성 텍스트)의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="ea1ba-388">변환의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-388">The result of the translation.</span></span>

<span data-ttu-id="ea1ba-389">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="ea1ba-389">To create this class:</span></span> 

1.  <span data-ttu-id="ea1ba-390">*프로젝트 패널*을 마우스 오른쪽 단추로 클릭 하 고 **> 폴더를 만듭니다**.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="ea1ba-391">폴더 이름을 **스크립트**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-391">Name the folder **Scripts**.</span></span> 
 
    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab1-31.png)

    ![Scripts 폴더를 엽니다.](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="ea1ba-394">**Scripts** 폴더 만들기를 사용 하 여 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="ea1ba-395">그런 다음 해당 폴더 내에서를 마우스 오른쪽 단추로 클릭 하 고 **> 만들기** 를 선택 하 고  **C# 스크립트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="ea1ba-396">스크립트 *결과*의 이름을로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-396">Name the script *Results*.</span></span> 

    ![첫 번째 스크립트를 만듭니다.](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="ea1ba-398">새 *결과* 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="ea1ba-399">다음 네임 스페이스를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="ea1ba-400">클래스 내에서 다음 변수를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-400">Inside the Class insert the following variables:</span></span>

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

6.  <span data-ttu-id="ea1ba-401">그런 다음, 다시 사용할 수 있는 *()* 메서드를 추가 합니다 .이 메서드는 클래스가 초기화 될 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="ea1ba-402">마지막으로 다양 한 결과 정보를 UI에 출력 하는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

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

8.  <span data-ttu-id="ea1ba-403">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="ea1ba-404">6 장 – *MicrophoneManager* 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="ea1ba-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="ea1ba-405">만들려는 두 번째 클래스는 *MicrophoneManager*입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="ea1ba-406">이 클래스는 다음을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-406">This class is responsible for:</span></span>

- <span data-ttu-id="ea1ba-407">헤드셋 또는 컴퓨터에 연결 된 기록 장치 검색 (기본값)</span><span class="sxs-lookup"><span data-stu-id="ea1ba-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="ea1ba-408">오디오 (음성)를 캡처하고 받아쓰기를 사용 하 여 문자열로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="ea1ba-409">음성이 일시 중지 되 면 받아쓰기를 Translator 클래스에 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="ea1ba-410">원할 경우 음성 캡처를 중지할 수 있는 메서드를 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="ea1ba-411">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="ea1ba-411">To create this class:</span></span> 
1.  <span data-ttu-id="ea1ba-412">**스크립트** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="ea1ba-413">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> C# 스크립트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="ea1ba-414">스크립트 이름을 *MicrophoneManager*로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="ea1ba-415">새 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="ea1ba-416">*MicrophoneManager* 클래스의 맨 위에서 다음과 같이 네임 스페이스를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="ea1ba-417">그런 다음 *MicrophoneManager* 클래스 안에 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

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

6.  <span data-ttu-id="ea1ba-418">이제 해제 *()* 및 *Start ()* 메서드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="ea1ba-419">이러한 작업은 클래스가 초기화 될 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-419">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="ea1ba-420">이 클래스는 사용 하지 않으므로 *Update ()* 메서드를 *삭제할* 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="ea1ba-421">이제 앱에서 음성 캡처를 시작 및 중지 하는 데 사용 하는 메서드를 사용 하 여 곧 빌드할 *변환기* 클래스로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="ea1ba-422">다음 코드를 복사 하 여 *Start ()* 메서드 아래에 붙여 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

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
    > <span data-ttu-id="ea1ba-423">이 응용 프로그램은이 응용 프로그램을 사용 하지 않지만 여기서는 *Stopcapturingaudio ()* 메서드도 제공 했습니다. 응용 프로그램에서 오디오 캡처를 중지 하는 기능을 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="ea1ba-424">이제 음성이 중지 될 때 호출 되는 받아쓰기 처리기를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="ea1ba-425">그런 다음이 메서드는 지시한 텍스트를 *Translator* 클래스로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-425">This method will then pass the dictated text to the *Translator* class.</span></span>

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

10. <span data-ttu-id="ea1ba-426">Unity로 반환 하기 전에 Visual Studio에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="ea1ba-427">이 시점에서 *Unity 편집기 콘솔* 패널에 오류가 표시 됩니다 ("' 번역기 ' 이름 '이 (가) 없습니다 ...").</span><span class="sxs-lookup"><span data-stu-id="ea1ba-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="ea1ba-428">이는 코드에서 다음 챕터에서 만들 *Translator* 클래스를 참조 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="ea1ba-429">7 장 – Azure 및 translator 서비스에 대 한 호출</span><span class="sxs-lookup"><span data-stu-id="ea1ba-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="ea1ba-430">생성 해야 하는 마지막 스크립트는 *Translator* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="ea1ba-431">이 클래스는 다음을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-431">This class is responsible for:</span></span>

-   <span data-ttu-id="ea1ba-432">**인증 토큰**에 대해 Exchange에서 *Azure*를 사용 하 여 앱을 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="ea1ba-433">**인증 토큰** 을 사용 하 여 번역할 텍스트 ( *MicrophoneManager* 클래스에서 수신)를 제출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="ea1ba-434">번역 된 결과를 수신 하 고 UI에서 시각화할 *결과* 클래스에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="ea1ba-435">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="ea1ba-435">To create this Class:</span></span> 
1.  <span data-ttu-id="ea1ba-436">이전에 만든 **스크립트** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="ea1ba-437">**프로젝트 패널**을 마우스 오른쪽 단추로 클릭 하 **> C# 스크립트를 만듭니다**.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="ea1ba-438">스크립트 *변환기*를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="ea1ba-439">새 *변환기* 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="ea1ba-440">파일의 맨 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="ea1ba-441">그런 다음 *Translator* 클래스 내에 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-441">Then add the following variables inside the *Translator* class:</span></span>

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
    > - <span data-ttu-id="ea1ba-442">언어 **열거형** 에 삽입 된 언어는 예제 일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="ea1ba-443">원한다 면 자유롭게 추가할 수 있습니다. [API는 60 개 이상의 언어](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (클링온어 포함)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="ea1ba-444">사용 가능한 언어를 포함 하는 [대화형 페이지는 더 많이](https://www.microsoft.com/translator/business/languages/)있습니다. 페이지는 사이트 언어가 ' en-us '로 설정 된 경우에만 작동 하는 것 처럼 보이지만 Microsoft 사이트는 네이티브 언어로 리디렉션될 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="ea1ba-445">페이지의 맨 아래에 있는 사이트 언어를 변경 하거나 URL을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="ea1ba-446">위의 코드 조각에서 **authorizationkey** 값은 *Azure Translator Text API*에 구독할 때 받은 **키** 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="ea1ba-447">이 내용은 [1 장](#chapter-1--the-azure-portal)에서 설명 했습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="ea1ba-448">이제 해제 *()* 및 *Start ()* 메서드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="ea1ba-449">이 경우 코드는 *토큰*을 가져오기 위해 권한 부여 키를 사용 하 여 *Azure* 에 대 한 호출을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

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
    > <span data-ttu-id="ea1ba-450">토큰은 10 분 후에 만료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="ea1ba-451">앱의 시나리오에 따라 동일한 코 루틴 호출을 여러 번 수행 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="ea1ba-452">토큰을 가져오는 코 루틴는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-452">The coroutine to obtain the Token is the following:</span></span>

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
    > <span data-ttu-id="ea1ba-453">IEnumerator 메서드 **GetTokenCoroutine ()** 의 이름을 편집 하는 경우 위의 코드에서 *StartCoroutine* 및 *StopCoroutine* 호출 문자열 값을 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="ea1ba-454">[Unity 설명서에 따라](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)특정 *코 루틴*을 중지 하려면 string value 메서드를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="ea1ba-455">다음으로, 코 루틴 (바로 아래에 "지원" 스트림 메서드 포함)를 추가 하 여 *MicrophoneManager* 클래스에서 받은 텍스트의 변환을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="ea1ba-456">이 코드는 *Azure Translator Text API*에 보낼 쿼리 문자열을 만든 다음 내부 Unity UnityWebRequest 클래스를 사용 하 여 쿼리 문자열을 사용 하 여 끝점에 대 한 ' Get ' 호출을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="ea1ba-457">결과를 사용 하 여 결과 개체에서 변환을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="ea1ba-458">아래 코드는 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-458">The code below shows the implementation:</span></span>

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

10. <span data-ttu-id="ea1ba-459">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="ea1ba-460">8 장-Unity 장면 구성</span><span class="sxs-lookup"><span data-stu-id="ea1ba-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="ea1ba-461">Unity 편집기로 돌아가서 **Scripts** 폴더의 *Results* *클래스를* 클릭 하 여 *계층 패널*의 **기본 카메라** 개체로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="ea1ba-462">**주 카메라** 를 클릭 하 고 *검사기 패널*을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="ea1ba-463">새로 추가한 *스크립트* 구성 요소에는 빈 값을 갖는 4 개의 필드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="ea1ba-464">다음은 코드의 속성에 대 한 출력 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="ea1ba-465">아래 이미지에 표시 된 것 처럼 적절 한 **텍스트** 개체를 *계층 패널* 에서 4 개의 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![지정 된 값을 사용 하 여 대상 참조를 업데이트 합니다.](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="ea1ba-467">그런 다음 **Scripts** 폴더의 *Translator* 클래스를 클릭 하 여 *계층 패널*의 **기본 카메라** 개체로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="ea1ba-468">그런 다음 **Scripts** 폴더에서 *MicrophoneManager* 클래스를 클릭 하 여 *계층 패널*의 **기본 카메라** 개체로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="ea1ba-469">마지막으로, **주 카메라** 를 클릭 하 고 *검사기 패널*을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="ea1ba-470">끌어 온 스크립트에서 언어를 설정 하는 데 사용할 수 있는 두 개의 드롭다운 상자가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![원하는 번역 언어가 입력 인지 확인 합니다.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="ea1ba-472">9 장-혼합 현실에서 테스트</span><span class="sxs-lookup"><span data-stu-id="ea1ba-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="ea1ba-473">이 시점에서 장면이 제대로 구현 되었는지 테스트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="ea1ba-474">다음을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-474">Ensure that:</span></span>

- <span data-ttu-id="ea1ba-475">[1 장](#chapter-1--the-azure-portal) 에서 설명한 모든 설정이 올바르게 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="ea1ba-476">*결과*, *번역기*및 *MicrophoneManager*스크립트는 **주 카메라** 개체에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="ea1ba-477">*Azure Translator Text API* 서비스 **키** 를 *Translator* 스크립트 내 **authorizationkey** 변수 내에 배치 했습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="ea1ba-478">*기본 카메라 검사기 패널* 의 모든 필드가 제대로 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="ea1ba-479">장면을 실행할 때 마이크가 작동 합니다 (그렇지 않은 경우 연결 된 마이크가 *기본* 장치이 고 [Windows 내에서 올바르게 설정](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)했는지 확인).</span><span class="sxs-lookup"><span data-stu-id="ea1ba-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="ea1ba-480">*Unity 편집기*에서 **재생** 단추를 눌러 몰입 형 헤드셋을 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="ea1ba-481">앱은 연결 된 모던 헤드셋을 통해 작동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="ea1ba-482">Unity 콘솔에 기본 오디오 장치 변경에 대 한 오류가 표시 되 면 장면이 예상 대로 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="ea1ba-483">이는 혼합 현실 포털이이를 포함 하는 헤드셋의 기본 제공 마이크를 처리 하는 방식 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="ea1ba-484">이 오류가 표시 되 면 장면을 중지 하 고 다시 시작 하 고 예상 대로 작동 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="ea1ba-485">10 장 – 로컬 컴퓨터에서 UWP 솔루션 및 테스트용으로 로드 빌드</span><span class="sxs-lookup"><span data-stu-id="ea1ba-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="ea1ba-486">이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었으므로 Unity에서 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="ea1ba-487">**빌드 설정**으로 이동 합니다. **빌드 설정 > 파일 ...**</span><span class="sxs-lookup"><span data-stu-id="ea1ba-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="ea1ba-488">**빌드 설정** 창에서 **빌드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Unity 장면을 빌드합니다.](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="ea1ba-490">아직 없는 경우 tick **Unity C# 프로젝트**입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="ea1ba-491">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-491">Click **Build**.</span></span> <span data-ttu-id="ea1ba-492">Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 *파일 탐색기* 창을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="ea1ba-493">이제 해당 폴더를 만들고 이름을 *App*으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="ea1ba-494">그런 다음 *앱* 폴더를 선택 하 고 **폴더 선택**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="ea1ba-495">Unity는 *응용* 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="ea1ba-496">Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 *파일 탐색기* 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)</span><span class="sxs-lookup"><span data-stu-id="ea1ba-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="ea1ba-497">11 장 – 응용 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="ea1ba-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="ea1ba-498">응용 프로그램을 배포 하려면:</span><span class="sxs-lookup"><span data-stu-id="ea1ba-498">To deploy your application:</span></span>

1.  <span data-ttu-id="ea1ba-499">새 Unity 빌드 ( *앱* 폴더)로 이동 하 여 *Visual Studio*에서 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="ea1ba-500">솔루션 구성에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="ea1ba-501">솔루션 플랫폼에서 **x86**, **로컬 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="ea1ba-502">Microsoft HoloLens의 경우 컴퓨터에 테더 링 된 하지 않도록 *원격 컴퓨터*를 설정 하는 것이 더 쉬울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="ea1ba-503">그러나 다음을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="ea1ba-504">HoloLens의 **IP 주소** 를 알고 있습니다. *설정 > 네트워크 & 인터넷 > Wi-fi > 고급 옵션*에서 찾을 수 있습니다. IPv4는 사용 해야 하는 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="ea1ba-505">*개발자 모드가* **설정**되어 있는지 확인 합니다. *개발자를 위한 업데이트 & 보안 > > 설정*에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="ea1ba-507">**빌드 메뉴로** 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 PC에 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="ea1ba-508">이제 앱이 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="ea1ba-509">앱이 시작 되 면 마이크에 대 한 액세스 권한을 부여 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="ea1ba-510">**예** 단추를 클릭 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="ea1ba-511">이제 번역을 시작할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="ea1ba-512">완성 된 번역 텍스트 API 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="ea1ba-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="ea1ba-513">축 하 합니다. Azure Translation 텍스트 API를 활용 하 여 음성을 번역 된 텍스트로 변환 하는 혼합 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![최종 제품.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="ea1ba-515">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="ea1ba-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="ea1ba-516">연습 1</span><span class="sxs-lookup"><span data-stu-id="ea1ba-516">Exercise 1</span></span>

<span data-ttu-id="ea1ba-517">텍스트 음성 변환 기능을 앱에 추가 하 여 반환 된 텍스트를 말할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="ea1ba-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="ea1ba-518">연습 2</span><span class="sxs-lookup"><span data-stu-id="ea1ba-518">Exercise 2</span></span>

<span data-ttu-id="ea1ba-519">사용자가 앱 자체 내에서 원본 및 출력 언어 (' from ' 및 ' to ')를 변경할 수 있으므로 언어를 변경할 때마다 앱을 다시 빌드할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1ba-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
