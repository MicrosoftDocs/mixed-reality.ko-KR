---
title: MR 및 Azure 302-컴퓨터 비전
description: 이 과정을 완료 하 여 혼합 현실 응용 프로그램에서 Azure Computer Vision를 사용 하 여 제공 된 이미지 내의 시각적 콘텐츠를 인식 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, 아카데미, unity, 자습서, api, 컴퓨터 비전, hololens, 몰입 형, vr
ms.openlocfilehash: 9cc526afdc36b8056afd61948fea5cf98015bb35
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047190"
---
>[!NOTE]
><span data-ttu-id="b4828-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="b4828-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="b4828-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="b4828-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="b4828-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="b4828-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="b4828-110">MR 및 Azure 302: 컴퓨터 비전</span><span class="sxs-lookup"><span data-stu-id="b4828-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="b4828-111">이 과정에서는 혼합 현실 응용 프로그램에서 Azure Computer Vision 기능을 사용 하 여 제공 된 이미지 내의 시각적 콘텐츠를 인식 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="b4828-112">인식 결과는 설명 태그로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="b4828-113">Machine learning 모델을 학습 하지 않고도이 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="b4828-114">구현에서 기계 학습 모델을 학습 해야 하는 경우 [MR 및 Azure 302b](mr-azure-302b.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4828-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![랩 결과](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="b4828-116">Microsoft Computer Vision는 개발자에 게 모든 클라우드에서 고급 알고리즘을 사용 하 여 이미지 처리 및 분석 (반환 정보 포함)을 제공 하도록 설계 된 Api 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="b4828-117">개발자는 이미지 또는 이미지 URL을 업로드 하 고 Microsoft Computer Vision API 알고리즘은 사용자가 선택한 입력에 따라 시각적 콘텐츠를 분석 하 여 이미지의 유형 및 품질을 식별 하 고 사용자 얼굴을 검색 하는 등의 정보를 반환할 수 있습니다. 해당 좌표)를 반환 하 고 이미지를 태그 지정 하거나 범주화 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="b4828-118">자세한 내용은 [Azure Computer Vision API 페이지](https://azure.microsoft.com/services/cognitive-services/computer-vision/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4828-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="b4828-119">이 과정을 완료 하면 다음과 같은 작업을 수행할 수 있는 혼합 현실 HoloLens 응용 프로그램이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="b4828-120">탭 제스처를 사용 하 여 HoloLens 카메라는 이미지를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="b4828-121">이미지가 Azure Computer Vision API 서비스로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="b4828-122">인식 된 개체는 Unity 장면에 배치 된 간단한 UI 그룹에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="b4828-123">응용 프로그램에서 결과를 디자인과 통합 하는 방법을 사용자가 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="b4828-124">이 과정은 Azure 서비스를 Unity 프로젝트와 통합 하는 방법을 배울 수 있도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="b4828-125">이 과정에서 얻은 지식을 사용 하 여 혼합 현실 응용 프로그램을 개선 하는 것은 사용자의 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="b4828-126">장치 지원</span><span class="sxs-lookup"><span data-stu-id="b4828-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="b4828-127">과정</span><span class="sxs-lookup"><span data-stu-id="b4828-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="b4828-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="b4828-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="b4828-129"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="b4828-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="b4828-130">MR 및 Azure 302: 컴퓨터 비전</span><span class="sxs-lookup"><span data-stu-id="b4828-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="b4828-131">✔️</span><span class="sxs-lookup"><span data-stu-id="b4828-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="b4828-132">✔️</span><span class="sxs-lookup"><span data-stu-id="b4828-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="b4828-133">이 과정에서 주로 HoloLens에 초점을 맞춘 반면,이 과정에서 배운 내용을 Windows Mixed Reality 모던 (VR) 헤드셋에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="b4828-134">모던 (VR) 헤드셋은 액세스할 수 있는 카메라를 포함 하지 않으므로 PC에 연결 된 외부 카메라가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="b4828-135">이 과정을 진행 하면서 모던 (VR) 헤드셋을 지원 하기 위해 사용 해야 하는 변경 내용에 대 한 정보를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b4828-136">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b4828-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="b4828-137">이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="b4828-138">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (2018 일 수 있음)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="b4828-139">[도구 설치](install-the-tools.md) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="b4828-140">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="b4828-141">모던 (VR) 헤드셋 개발을 위한 [Windows Mixed Reality와 호환 되](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) 는 개발 PC</span><span class="sxs-lookup"><span data-stu-id="b4828-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="b4828-142">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="b4828-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b4828-143">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="b4828-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b4828-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="b4828-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="b4828-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="b4828-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="b4828-146">개발자 모드가 사용 하도록 설정 된 [Windows Mixed Reality 모던 (VR) 헤드셋](immersive-headset-hardware-details.md) 또는 [Microsoft HoloLens](hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="b4828-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="b4828-147">PC에 연결 된 카메라 (몰입 형 헤드셋 개발용)</span><span class="sxs-lookup"><span data-stu-id="b4828-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="b4828-148">Azure 설정 및 Computer Vision API 검색을 위한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="b4828-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="b4828-149">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="b4828-149">Before you start</span></span>

1.  <span data-ttu-id="b4828-150">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="b4828-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="b4828-151">HoloLens를 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="b4828-152">HoloLens를 설정 하는 데 지원이 필요한 경우 [hololens 설정 문서를 방문](https://docs.microsoft.com/hololens/hololens-setup)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="b4828-153">새 HoloLens 앱 개발을 시작할 때 보정 및 센서 조정을 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음).</span><span class="sxs-lookup"><span data-stu-id="b4828-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="b4828-154">보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에](calibration.md#hololens-2)대 한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4828-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="b4828-155">센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](sensor-tuning.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4828-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="b4828-156">1 장-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="b4828-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="b4828-157">Azure에서 *Computer Vision API* 서비스를 사용 하려면 응용 프로그램에서 사용할 수 있도록 서비스 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="b4828-158">먼저 [Azure Portal](https://portal.azure.com)에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="b4828-159">아직 Azure 계정이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="b4828-160">교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="b4828-161">로그인 되 면 왼쪽 위 모서리에서 **새로 만들기** 를 클릭 하 고 *Computer Vision API*를 검색 한 다음 **Enter 키**를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![Azure에서 새 리소스 만들기](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="b4828-163">새 단어는 **새** 포털에서 **리소스 만들기**로 대체 되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="b4828-164">새 페이지에 *Computer Vision API* 서비스에 대 한 설명이 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="b4828-165">이 페이지의 왼쪽 아래에서 **만들기** 단추를 선택 하 여이 서비스와의 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![컴퓨터 비전 api 서비스 정보](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="b4828-167">**만들기**를 클릭 하면 다음을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="b4828-168">이 서비스 인스턴스의 원하는 **이름을** 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="b4828-169">**구독**을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="b4828-170">적절 한 **가격 책정 계층** 을 선택 합니다. *Computer Vision API* 서비스를 처음 만드는 경우 무료 계층 (명명 된 F0)을 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="b4828-171">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="b4828-172">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="b4828-173">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 랩)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="b4828-174">Azure 리소스 그룹에 대 한 자세한 내용을 보려면 [리소스 그룹 문서를 참조](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)하세요.</span><span class="sxs-lookup"><span data-stu-id="b4828-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="b4828-175">새 리소스 그룹을 만드는 경우 리소스 그룹의 위치를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="b4828-176">위치는 응용 프로그램이 실행 되는 영역에 있는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="b4828-177">일부 Azure 자산은 특정 지역 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="b4828-178">또한이 서비스에 적용 된 사용 약관을 이해 했는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="b4828-179">만들기를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-179">Click Create.</span></span>

        ![서비스 생성 정보](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="b4828-181">**만들기**를 클릭 한 후에는 서비스를 만들 때까지 기다려야 합니다 .이 작업이 몇 분 정도 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="b4828-182">서비스 인스턴스를 만든 후 알림이 포털에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![새 서비스에 대 한 새 알림 확인](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="b4828-184">알림을 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-184">Click on the notification to explore your new Service instance.</span></span> 

    ![리소스로 이동 단추를 선택 합니다.](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="b4828-186">알림에서 **리소스로 이동** 단추를 클릭 하 여 새 서비스 인스턴스를 탐색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="b4828-187">새 Computer Vision API 서비스 인스턴스로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![새 Computer Vision API 서비스](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="b4828-189">이 자습서에서 응용 프로그램은 서비스에 대 한 호출을 수행 해야 하며, 서비스의 구독 키를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="b4828-190">*Computer Vision API* 서비스의 *빠른 시작* 페이지에서 첫 번째 단계로 이동 하 고 *키*를 클릭 한 다음 **키** 를 클릭 합니다 .이를 위해 서비스 탐색 메뉴에 있는 파란색 하이퍼링크 키를 클릭 하 여이를 수행할 수도 있습니다. 키 아이콘으로 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="b4828-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="b4828-191">이렇게 하면 서비스 *키*가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="b4828-192">프로젝트에서 나중에 필요 하므로 표시 된 키 중 하나를 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="b4828-193">*빠른 시작* 페이지로 돌아가 여기에서 끝점을 인출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="b4828-194">사용자는 지역에 따라 다를 수 있습니다 (이 경우 나중에 코드를 변경 해야 하는 경우).</span><span class="sxs-lookup"><span data-stu-id="b4828-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="b4828-195">나중에 사용 하기 위해이 끝점의 복사본을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-195">Take a copy of this endpoint for use later:</span></span>

    ![새 Computer Vision API 서비스](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="b4828-197">다양 한 끝점이 [여기](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)에 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="b4828-198">2 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="b4828-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="b4828-199">다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="b4828-200">*Unity* 를 열고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-200">Open *Unity* and click **New**.</span></span> 

    ![새 Unity 프로젝트를 시작 합니다.](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="b4828-202">이제 Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="b4828-203">**MR_ComputerVision**을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="b4828-204">프로젝트 형식이 **3d**로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="b4828-205">위치를 적절 한 **위치** 에 적절 하 게 설정 합니다. 루트 디렉터리에 가까울수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="b4828-206">그런 다음 **프로젝트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-206">Then, click **Create project**.</span></span>

    ![새 Unity 프로젝트에 대 한 세부 정보를 제공 합니다.](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="b4828-208">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="b4828-209">**> 기본 설정 편집** 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="b4828-210">**외부 스크립트 편집기** 를 **Visual Studio 2017**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="b4828-211">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-211">Close the **Preferences** window.</span></span>

    ![스크립트 편집기 기본 설정을 업데이트 합니다.](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="b4828-213">그런 다음 **파일 > 빌드 설정** 으로 이동 하 고 **유니버설 Windows 플랫폼**을 선택한 후 **플랫폼 전환** 단추를 클릭 하 여 선택 항목을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![빌드 설정 창에서 플랫폼을 UWP로 전환 합니다.](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="b4828-215">아직 **파일 > 빌드 설정을** 사용 하 고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="b4828-216">**대상 장치가** **HoloLens** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="b4828-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="b4828-217">모던 헤드셋의 경우 **대상 장치** 를 *모든 장치로*설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="b4828-218">**빌드 형식이** **D3D** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="b4828-219">**SDK** 가 **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="b4828-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="b4828-220">**Visual Studio 버전이** **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="b4828-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="b4828-221">**빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="b4828-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="b4828-222">장면을 저장 하 고 빌드에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="b4828-223">이렇게 하려면 열려 있는 **장면 추가**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="b4828-224">저장 창이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-224">A save window will appear.</span></span>
        
            ![열린 장면 추가 단추를 클릭 합니다.](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="b4828-226">이에 대 한 새 폴더를 만들고 나중에 장면을 만든 다음 **새 폴더** 단추를 선택 하 여 새 폴더를 만들고 이름을 **장면을**로 지정한 다음</span><span class="sxs-lookup"><span data-stu-id="b4828-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![새 스크립트 폴더 만들기](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="b4828-228">새로 만든 **장면** 폴더를 연 다음 *파일 이름*: 텍스트 필드에 **MR_ComputerVisionScene**를 입력 하 고 **저장**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![새 장면에 이름을 지정 합니다.](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="b4828-230">Unity 프로젝트와 연결 되어 있어야 하므로 *자산* 폴더 내에 unity 장면을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="b4828-231">배경 폴더 (및 기타 유사한 폴더)를 만드는 것은 Unity 프로젝트를 구조화 하는 일반적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="b4828-232">*빌드 설정*의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="b4828-233">*빌드 설정* 창에서 **플레이어 설정** 단추를 클릭 하면 *검사기* 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![플레이어 설정을 엽니다.](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="b4828-235">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="b4828-236">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="b4828-237">**Scripting Runtime 버전** 은 **안정적** 이어야 합니다 (.net 3.5 해당).</span><span class="sxs-lookup"><span data-stu-id="b4828-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="b4828-238">**Scripting 백엔드** 는 **.net** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="b4828-239">**API 호환성 수준은** **.net 4.6** 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![다른 설정을 업데이트 합니다.](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="b4828-241">**게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="b4828-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="b4828-242">**InternetClient**</span></span>
        2. <span data-ttu-id="b4828-243">**웹캠**</span><span class="sxs-lookup"><span data-stu-id="b4828-243">**Webcam**</span></span>

            ![게시 설정을 업데이트 하는 중입니다.](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="b4828-245">패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X R 설정을 업데이트 합니다.](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="b4828-247">*빌드 설정* 으로 돌아가서 _Unity C#_  프로젝트가 더 이상 회색으로 표시 되지 않습니다. 이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="b4828-248">빌드 설정 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="b4828-249">장면 및 프로젝트를 저장 합니다 (**파일 > 장면/파일 저장 > 프로젝트 저장**).</span><span class="sxs-lookup"><span data-stu-id="b4828-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="b4828-250">3 장-기본 카메라 설정</span><span class="sxs-lookup"><span data-stu-id="b4828-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4828-251">이 과정의 *Unity 설정* 구성 요소를 건너뛰고 계속 해 서 코드를 계속 사용 하려면 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)를 다운로드 하 여 프로젝트에 [사용자 지정 패키지로](https://docs.unity3d.com/Manual/AssetPackages.html)가져온 후 [5 장](#chapter-5--create-the-resultslabel-class)에서 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="b4828-252">*계층 패널*에서 **기본 카메라**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="b4828-253">선택한 후에는 *검사기 패널*에서 **주 카메라** 의 모든 구성 요소를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="b4828-254">**카메라 개체** 의 이름을 **주 카메라로** 지정 해야 합니다 (철자 확인).</span><span class="sxs-lookup"><span data-stu-id="b4828-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="b4828-255">기본 카메라 **태그** 는 **maincamera** 로 설정 되어야 합니다 (철자 확인).</span><span class="sxs-lookup"><span data-stu-id="b4828-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="b4828-256">**변환 위치가** **0, 0, 0** 으로 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="b4828-257">**Clear 플래그** 를 **단색** 으로 설정 합니다. 몰입 형 헤드셋의 경우이를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="b4828-258">카메라 구성 요소의 **배경색** 을 **검은색, 알파 0 (16 진수 코드: #00000000)** 으로 설정 합니다 (몰입 형 헤드셋의 경우 무시).</span><span class="sxs-lookup"><span data-stu-id="b4828-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![카메라 구성 요소를 업데이트 합니다.](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="b4828-260">다음으로, **주 카메라**에 연결 된 간단한 "커서" 개체를 만들어야 합니다. 그러면 응용 프로그램을 실행할 때 이미지 분석 출력을 배치 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="b4828-261">이 커서는 카메라 포커스의 중심점을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="b4828-262">커서를 만들려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="b4828-263">*계층 패널*에서 **기본 카메라**를 마우스 오른쪽 단추로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="b4828-264">**3D 개체**에서 **구**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![커서 개체를 선택 합니다.](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="b4828-266">**구의** 이름을 **커서로** 변경 합니다 (커서 개체를 두 번 클릭 하거나 선택한 개체가 있는 ' F2 ' 키보드 단추를 누름). **기본 카메라**의 자식으로 배치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="b4828-267">*계층 패널*에서 **커서**를 마우스 왼쪽 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="b4828-268">커서를 선택 하 고 *검사기 패널*에서 다음 변수를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="b4828-269">*변환 위치* 를 **0, 0, 5** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="b4828-270">*소수 자릿수* 를 **0.02, 0.02, 0.02** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![변환 위치 및 소수 자릿수를 업데이트 합니다.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="b4828-272">4 장-레이블 시스템 설정</span><span class="sxs-lookup"><span data-stu-id="b4828-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="b4828-273">HoloLens 카메라를 사용 하 여 이미지를 캡처한 후 해당 이미지는 분석을 위해 *Azure Computer Vision API* 서비스 인스턴스로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="b4828-274">이 분석의 결과는 **태그**라고 하는 인식 된 개체의 목록이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="b4828-275">레이블 (세계 공간에서 3D 텍스트로)을 사용 하 여 사진이 만들어진 위치에 이러한 태그를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="b4828-276">다음 단계에서는 **Label** 개체를 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="b4828-277">계층 패널에서 아무 곳 이나 마우스 오른쪽 단추로 클릭 하 고 (위치는이 시점에서 중요 하지 않음) **3D 개체**에서 **3d 텍스트**를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="b4828-278">**레이블 텍스트**를 이름으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-278">Name it **LabelText**.</span></span>

    ![3D 텍스트 개체를 만듭니다.](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="b4828-280">*계층 패널*에서 **레이블 텍스트**를 마우스 왼쪽 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="b4828-281">**Labeltext** 를 선택한 상태에서 *검사기 패널*의 다음 변수를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="b4828-282">**위치** 를 **0, 0, 0** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="b4828-283">**소수 자릿수** 를 **0.01, 0.01, 0.01** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="b4828-284">구성 요소 **텍스트 메시**에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="b4828-285">**텍스트**에 있는 모든 텍스트를 "..."로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="b4828-286">**앵커** 를 **중간 가운데로** 설정</span><span class="sxs-lookup"><span data-stu-id="b4828-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="b4828-287">맞춤을 **가운데** **맞춤** 으로 설정</span><span class="sxs-lookup"><span data-stu-id="b4828-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="b4828-288">**탭 크기** 를 **4** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="b4828-289">**글꼴 크기** 를 **50** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="b4828-290">**색** 을 **#FFFFFFFF** 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![텍스트 구성 요소](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="b4828-292">*계층 패널*의 **Labeltext** 를 *프로젝트 패널*내의 *Asset 폴더로*끌어 옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="b4828-293">이렇게 하면 **레이블 텍스트가** Prefab로 설정 되어 코드에서 인스턴스화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![LabelText 개체의 prefab을 만듭니다.](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="b4828-295">열이 표시 되는 장면에 표시 되지 않도록 *계층 패널*에서 **labeltext** 를 삭제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="b4828-296">이제 자산 폴더의 개별 인스턴스에 대해를 호출 하는 prefab 장면 내에서 보관할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="b4828-297">*계층 패널* 의 최종 개체 구조는 아래 이미지에 표시 된 것과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![계층 패널의 최종 구조입니다.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="b4828-299">5 장-ResultsLabel 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b4828-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="b4828-300">만들어야 하는 첫 번째 스크립트는 다음을 담당 하는 *ResultsLabel* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="b4828-301">카메라의 위치를 기준으로 적절 한 세계 공간에 레이블 만들기</span><span class="sxs-lookup"><span data-stu-id="b4828-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="b4828-302">이미지 분석에서 태그를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="b4828-303">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b4828-303">To create this class:</span></span> 

1.  <span data-ttu-id="b4828-304">*프로젝트 패널*을 마우스 오른쪽 단추로 클릭 하 고 **> 폴더를 만듭니다**.</span><span class="sxs-lookup"><span data-stu-id="b4828-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="b4828-305">폴더 이름을 **스크립트**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-305">Name the folder **Scripts**.</span></span> 

    ![스크립트 폴더를 만듭니다.](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="b4828-307">**Scripts** 폴더 만들기를 사용 하 여 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="b4828-308">그런 다음 해당 폴더 내에서를 마우스 오른쪽 단추로 클릭 하 고 **> 만들기** 를 선택 하 고  **C# 스크립트**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="b4828-309">스크립트 이름을 *ResultsLabel*로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="b4828-310">새 *ResultsLabel* 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="b4828-311">클래스 내에서 *ResultsLabel* 클래스에 다음 코드를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  <span data-ttu-id="b4828-312">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="b4828-313">*Unity 편집기*로 돌아가서 **Scripts** 폴더의 *ResultsLabel* 클래스를 클릭 하 여 *계층 패널*의 **기본 카메라** 개체로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="b4828-314">**주 카메라** 를 클릭 하 고 *검사기 패널*을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="b4828-315">방금 카메라 안으로 끌어온 스크립트에서 두 개의 필드가 있습니다. **커서** 및 **레이블 Prefab**.</span><span class="sxs-lookup"><span data-stu-id="b4828-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="b4828-316">아래 이미지에 표시 된 것 처럼 *계층 패널* 에서 커서 라는 개체를 **커서**라는 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="b4828-317">아래 이미지에 표시 된 것 처럼 *프로젝트 패널* 의 *자산 폴더* 에서 **레이블 Prefab**이라는 개체를 끌어 레이블 이름이 지정 된 슬롯으로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![Unity 내에서 참조 대상을 설정 합니다.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="b4828-319">6 장 – ImageCapture 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b4828-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="b4828-320">만들려는 다음 클래스는 *ImageCapture* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="b4828-321">이 클래스는 다음을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-321">This class is responsible for:</span></span>

-   <span data-ttu-id="b4828-322">HoloLens 카메라를 사용 하 여 이미지를 캡처하고 앱 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="b4828-323">사용자 로부터 탭 제스처를 캡처하는 경우</span><span class="sxs-lookup"><span data-stu-id="b4828-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="b4828-324">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b4828-324">To create this class:</span></span> 

1.  <span data-ttu-id="b4828-325">이전에 만든 **스크립트** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="b4828-326">폴더 내부를 마우스 오른쪽 단추로 클릭 하 **> C# 스크립트를 만듭니다**.</span><span class="sxs-lookup"><span data-stu-id="b4828-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="b4828-327">*ImageCapture*스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="b4828-328">새 *ImageCapture* 스크립트를 두 번 클릭 하 여 **Visual Studio**에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="b4828-329">파일의 맨 위에 다음 네임 스페이스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="b4828-330">그런 다음 *ImageCapture* 클래스 내에서 *Start ()* 메서드 위의 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="b4828-331">**TapsCount** 변수는 사용자에 게 캡처된 탭 제스처 수를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="b4828-332">이 숫자는 캡처된 이미지의 이름을 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="b4828-333">이제 *활성 ()* 및 *Start ()* 메서드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="b4828-334">이러한 작업은 클래스가 초기화 될 때 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="b4828-335">탭 제스처가 발생할 때 호출 되는 처리기를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
<span data-ttu-id="b4828-336">*TapHandler ()* 메서드는 사용자 로부터 캡처된 탭의 수를 늘리고 현재 커서 위치를 사용 하 여 새 레이블을 배치할 위치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="b4828-337">그런 다음이 메서드는 *ExecuteImageCaptureAndAnalysis ()* 메서드를 호출 하 여이 응용 프로그램의 핵심 기능을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="b4828-338">이미지를 캡처 및 저장 한 후에는 다음 처리기가 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="b4828-339">프로세스가 성공적으로 실행 되 면 분석을 위해 결과가 아직 생성 중이 *VisionManager* 에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  <span data-ttu-id="b4828-340">그런 다음 응용 프로그램이 이미지 캡처 프로세스를 시작 하 고 이미지를 저장 하는 데 사용 하는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> <span data-ttu-id="b4828-341">이 시점에서 *Unity 편집기 콘솔 패널*에 오류가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="b4828-342">코드는 다음 챕터에서 만들 *VisionManager* 클래스를 참조 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="b4828-343">7 장 – Azure 및 이미지 분석 호출</span><span class="sxs-lookup"><span data-stu-id="b4828-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="b4828-344">생성 해야 하는 마지막 스크립트는 *VisionManager* 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="b4828-345">이 클래스는 다음을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-345">This class is responsible for:</span></span>

-   <span data-ttu-id="b4828-346">캡처된 최신 이미지를 바이트 배열로 로드 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="b4828-347">분석을 위해 바이트 배열을 *Azure Computer Vision API* 서비스 인스턴스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="b4828-348">JSON 문자열로 응답을 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="b4828-349">응답을 deserialize 하 고 결과 태그를 *ResultsLabel* 클래스에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="b4828-350">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="b4828-350">To create this class:</span></span>

1.  <span data-ttu-id="b4828-351">**스크립트** 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="b4828-352">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 하 고 **> C# 스크립트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="b4828-353">스크립트 이름을 *VisionManager*로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="b4828-354">새 스크립트를 두 번 클릭 하 여 Visual Studio에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="b4828-355">*VisionManager* 클래스의 맨 위에서 다음과 같이 네임 스페이스를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="b4828-356">스크립트의 맨 위에 있는 *VisionManager* 클래스 ( *Start ()* 메서드 위의)에서, 이제 Azure에서 deserialize 된 JSON 응답을 나타내는 두 개의 *클래스* 를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="b4828-357">*TagData* 및 *AnalysedObject* 클래스에는 Unity 라이브러리를 사용 하 여 deserialize 할 수 있도록 선언 앞에 *[]* 특성이 추가 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="b4828-358">VisionManager 클래스에서 다음 변수를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-358">In the VisionManager class, you should add the following variables:</span></span>

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > <span data-ttu-id="b4828-359">**Authorizationkey** 변수에 **인증 키** 를 삽입 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="b4828-360">이 과정의 시작 부분에 [1 장](#chapter-1--the-azure-portal)에서 **인증 키** 를 기록 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="b4828-361">**VisionAnalysisEndpoint** 변수는이 예제에서 지정한 것과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="b4828-362">미국 **서 부** 는 미국 서 부 지역에 대해 만든 서비스 인스턴스를 엄격히 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="b4828-363">이를 [끝점 URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)로 업데이트 합니다. 다음과 같은 몇 가지 예가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="b4828-364">유럽 서부:`https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="b4828-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="b4828-365">동남 아시아:`https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="b4828-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="b4828-366">오스트레일리아 동부:`https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="b4828-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="b4828-367">이제 절전 모드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="b4828-368">그런 다음 *ImageCapture* 클래스에 의해 캡처된 이미지의 분석 결과를 얻을 수 있는 코 루틴 (아래 정적 스트림 메서드 포함)를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  <span data-ttu-id="b4828-369">*Unity*로 반환 하기 전에 *Visual Studio* 에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="b4828-370">Unity 편집기로 돌아가서 **Scripts** 폴더에서 *VisionManager* 및 *ImageCapture* 클래스를 클릭 하 여 *계층 패널*의 **기본 카메라** 개체로 끕니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="b4828-371">8 장 – 빌드하기 전</span><span class="sxs-lookup"><span data-stu-id="b4828-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="b4828-372">응용 프로그램에 대 한 철저 한 테스트를 수행 하려면 HoloLens에 테스트용으로 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="b4828-373">이렇게 하려면 먼저 다음을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="b4828-374">[2 장](#chapter-2--set-up-the-unity-project) 에서 설명한 모든 설정이 올바르게 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="b4828-375">모든 스크립트는 **주 카메라** 개체에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="b4828-376">*기본 카메라 검사기 패널* 의 모든 필드가 제대로 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="b4828-377">**Authorizationkey** 변수에 **인증 키** 를 삽입 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="b4828-378">*VisionManager* 스크립트에서 끝점을 확인 하 고 *사용자* 의 지역에 부합 하는지 확인 합니다 .이 문서에서는 기본적으로 *미국 서 부* 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="b4828-379">9 장-UWP 솔루션 빌드 및 응용 프로그램 테스트용으로 로드</span><span class="sxs-lookup"><span data-stu-id="b4828-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="b4828-380">이제이 프로젝트의 Unity 섹션에 필요한 모든 항목이 완료 되었으므로 Unity에서 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="b4828-381">빌드 설정 - **파일 > 빌드 설정** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="b4828-382">*빌드 설정* 창에서 **빌드**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-382">From the *Build Settings* window, click **Build**.</span></span>

    ![Unity에서 앱 빌드](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="b4828-384">아직 없는 경우 tick **Unity C# 프로젝트**입니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="b4828-385">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-385">Click **Build**.</span></span> <span data-ttu-id="b4828-386">Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 *파일 탐색기* 창을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="b4828-387">이제 해당 폴더를 만들고 이름을 *App*으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="b4828-388">그런 다음 *앱* 폴더를 선택 하 고 **폴더 선택**을 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="b4828-389">Unity는 *응용* 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="b4828-390">Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 *파일 탐색기* 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)</span><span class="sxs-lookup"><span data-stu-id="b4828-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="b4828-391">10 장 – HoloLens에 배포</span><span class="sxs-lookup"><span data-stu-id="b4828-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="b4828-392">HoloLens에 배포 하려면:</span><span class="sxs-lookup"><span data-stu-id="b4828-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="b4828-393">HoloLens의 IP 주소 (원격 배포의 경우)가 필요 하 고 HoloLens가 **개발자 모드**에 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="b4828-394">가상 하드 디스크 파일에 대한 중요 정보를 제공하려면</span><span class="sxs-lookup"><span data-stu-id="b4828-394">To do this:</span></span>

    1. <span data-ttu-id="b4828-395">HoloLens를 입고 하는 동안 **설정을**엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="b4828-396">**네트워크 & 인터넷 > wi-fi > 고급 옵션** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="b4828-397">**IPv4** 주소를 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="b4828-398">그런 다음 **설정**으로 다시 이동한 다음 **개발자를 위한 & 보안 >를 업데이트** 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="b4828-399">에서 개발자 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="b4828-400">새 Unity 빌드 ( *앱* 폴더)로 이동 하 여 *Visual Studio*에서 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="b4828-401">솔루션 구성에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="b4828-402">솔루션 플랫폼에서 **x86**, **원격 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Visual Studio에서 솔루션을 배포 합니다.](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="b4828-404">**빌드 메뉴로** 이동 하 여 **솔루션 배포**를 클릭 하 여 응용 프로그램을 HoloLens로 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="b4828-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="b4828-405">이제 앱이 HoloLens에 설치 된 앱 목록에 표시 되어 시작할 준비가 되었습니다!</span><span class="sxs-lookup"><span data-stu-id="b4828-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="b4828-406">모던 헤드셋에 배포 하려면 **솔루션 플랫폼** 을 *로컬 컴퓨터*로 설정 하 고 **구성을** *디버그*로 설정 하 고 *x 86* 을 **플랫폼**으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="b4828-407">그런 다음 **빌드 메뉴**를 사용 하 여 *솔루션 배포*를 선택 하 여 로컬 컴퓨터에 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="b4828-408">완성 된 Computer Vision API 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="b4828-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="b4828-409">축 하 합니다. Azure Computer Vision API를 활용 하 여 실제 개체를 인식 하 고 표시 되는 내용에 대 한 확신을 표시 하는 혼합 현실 앱을 빌드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![랩 결과](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="b4828-411">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="b4828-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="b4828-412">연습 1</span><span class="sxs-lookup"><span data-stu-id="b4828-412">Exercise 1</span></span>

<span data-ttu-id="b4828-413">*Tags* 매개 변수 ( *VisionManager*내에서 사용 되는 *끝점* 내에서 복합적로)를 사용 하는 것 처럼 앱을 확장 하 여 다른 정보를 검색 합니다. [여기](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)에 액세스할 수 있는 다른 매개 변수를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="b4828-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="b4828-414">연습 2</span><span class="sxs-lookup"><span data-stu-id="b4828-414">Exercise 2</span></span>

<span data-ttu-id="b4828-415">반환 된 Azure 데이터를 보다 잘 이해 하 고 읽을 수 있는 방법으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="b4828-416">사용자에 게 사용자에 게 문의 하 고 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4828-416">As though a bot might be speaking to the user.</span></span>
