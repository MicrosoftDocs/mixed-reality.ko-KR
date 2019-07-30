---
title: MR 및 Azure 310-개체 검색
description: 이 과정을 완료 하 여 machine learning 모델을 학습 한 다음, 학습 된 모델을 사용 하 여 혼합 현실 응용 프로그램 내에서 실제 세계의 유사한 개체와 해당 위치를 인식 하는 방법을 알아보세요.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, 사용자 지정 비전, 개체 검색, 혼합 현실, 아카데미, unity, 자습서, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63544417"
---
>[!NOTE]
><span data-ttu-id="8713f-104">혼합 현실 아카데미 자습서는 HoloLens (첫 번째 gen) 및 혼합 현실 모던 헤드셋을 염두에 두면 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="8713f-105">따라서 이러한 장치에 대 한 개발에 대 한 지침을 계속 찾고 있는 개발자를 위해 이러한 자습서를 그대로 두는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="8713f-106">이러한 자습서는 HoloLens 2에 사용 되는 최신 도구 집합 또는 상호 작용으로 업데이트 **_되지_** 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="8713f-107">지원 되는 장치에서 작업을 계속 하기 위해 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="8713f-108">향후에는 HoloLens 2를 개발 하는 방법을 보여 주는 새 자습서 시리즈를 게시할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="8713f-109">이 알림은 게시 될 때 해당 자습서에 대 한 링크를 사용 하 여 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="8713f-110">Mr 및 Azure 310: 개체 검색</span><span class="sxs-lookup"><span data-stu-id="8713f-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="8713f-111">이 과정에서는 혼합 현실 응용 프로그램에서 Azure Custom Vision "개체 검색" 기능을 사용 하 여 제공 된 이미지 내에서 사용자 지정 시각적 콘텐츠와 해당 공간 위치를 인식 하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="8713f-112">이 서비스를 사용 하면 개체 이미지를 사용 하 여 기계 학습 모델을 학습 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="8713f-113">Microsoft HoloLens의 카메라 캡처 또는 카메라를 사용 하 여 (VR 용 PC에 연결) 헤드셋에서 제공 하는 것 처럼 학습 된 모델을 사용 하 여 실제 세계에서 유사한 개체를 인식 하 고 해당 위치를 대략적으로 파악할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![과정 결과](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="8713f-115">**Azure Custom Vision, 개체 검색** 은 개발자가 사용자 지정 이미지 분류자를 빌드할 수 있게 해 주는 Microsoft 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="8713f-116">이러한 분류자는 이미지 자체 내에서 **상자 경계** 를 제공 하 여 새 이미지 내에서 개체를 검색 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="8713f-117">이 서비스는 간단 하 고 사용 하기 쉬운 온라인 포털을 제공 하 여이 프로세스를 간소화 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="8713f-118">자세한 내용은 다음 링크를 방문 하세요.</span><span class="sxs-lookup"><span data-stu-id="8713f-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="8713f-119">Azure Custom Vision 페이지</span><span class="sxs-lookup"><span data-stu-id="8713f-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="8713f-120">제한 및 할당량</span><span class="sxs-lookup"><span data-stu-id="8713f-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="8713f-121">이 과정이 완료 되 면 다음을 수행할 수 있는 혼합 현실 응용 프로그램이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="8713f-122">사용자가 Azure Custom Vision Service, 개체 검색을 사용 하 여 학습 한 개체를 *응시* 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="8713f-123">사용자는 *탭* 제스처를 사용 하 여 원하는 항목의 이미지를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="8713f-124">앱이 Azure Custom Vision Service에 이미지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="8713f-125">인식 결과를 전 세계 공간 텍스트로 표시 하는 서비스의 회신이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="8713f-126">이는 인식 되는 개체의 세계 위치를 이해 하 고 이미지에서 검색 된 *태그* 를 사용 하 여 레이블 텍스트를 제공 하는 방법으로 Microsoft HoloLens의 공간 추적을 활용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="8713f-127">또한이 과정에서는 이미지 내에서 *경계 상자* 를 설정 하 여 이미지를 수동으로 업로드 하 고, 태그를 만들고, 서비스를 학습 하 여 다양 한 개체 (제공 된 예제에서 컵)를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="8713f-128">앱을 만들고 사용한 후 개발자는 Azure Custom Vision Service으로 다시 이동 하 고, 서비스에서 수행 하는 예측을 식별 하 고, 서비스가 누락 되었는지 여부를 확인 합니다. *경계 상자*조정).</span><span class="sxs-lookup"><span data-stu-id="8713f-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="8713f-129">그런 다음 서비스를 다시 학습 하 여 실제 개체를 인식할 가능성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="8713f-130">이 과정에서는 Azure Custom Vision Service, 개체 검색에서 결과를 Unity 기반 샘플 응용 프로그램으로 가져오는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="8713f-131">빌드할 수 있는 사용자 지정 응용 프로그램에 이러한 개념을 적용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="8713f-132">장치 지원</span><span class="sxs-lookup"><span data-stu-id="8713f-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="8713f-133">과정</span><span class="sxs-lookup"><span data-stu-id="8713f-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="8713f-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="8713f-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="8713f-135"><a href="immersive-headset-hardware-details.md">몰입형 헤드셋</a></span><span class="sxs-lookup"><span data-stu-id="8713f-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="8713f-136">MR 및 Azure 310: 개체 검색</span><span class="sxs-lookup"><span data-stu-id="8713f-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="8713f-137">✔️</span><span class="sxs-lookup"><span data-stu-id="8713f-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="8713f-138">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="8713f-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="8713f-139">이 자습서는 Unity 및 C#에 대 한 기본 경험이 있는 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="8713f-140">또한이 문서에서 사전 요구 사항 및 작성 된 지침은 작성 시 테스트 되 고 확인 된 내용 (7 월 2018)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="8713f-141">[도구 설치](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) 문서에 나와 있는 것 처럼 최신 소프트웨어를 무료로 사용할 수 있지만,이 과정의 정보가 아래 나열 된 것 보다 최신 소프트웨어에서 찾을 수 있는 것으로 간주 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="8713f-142">이 과정에는 다음 하드웨어 및 소프트웨어를 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="8713f-143">개발 PC</span><span class="sxs-lookup"><span data-stu-id="8713f-143">A development PC</span></span>
- [<span data-ttu-id="8713f-144">개발자 모드를 사용 하는 Windows 10이 하 버전의 작성자 업데이트 (또는 이상)</span><span class="sxs-lookup"><span data-stu-id="8713f-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="8713f-145">최신 Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="8713f-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="8713f-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="8713f-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="8713f-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="8713f-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="8713f-148">개발자 모드를 사용 하는 [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)</span><span class="sxs-lookup"><span data-stu-id="8713f-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="8713f-149">Azure 설정 및 Custom Vision Service 검색을 위한 인터넷 액세스</span><span class="sxs-lookup"><span data-stu-id="8713f-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="8713f-150">Custom Vision에서 인식할 수 있는 각 개체에 대해 15 개 이상의 이미지가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="8713f-151">원할 경우이 과정에서 이미 제공 된 이미지 ( [일련의 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="8713f-152">시작하기 전 주의 사항</span><span class="sxs-lookup"><span data-stu-id="8713f-152">Before you start</span></span>

1.  <span data-ttu-id="8713f-153">이 프로젝트를 빌드하는 데 문제가 발생 하지 않도록 하려면 루트 또는 루트 폴더에이 자습서에서 언급 한 프로젝트를 만드는 것이 좋습니다. (긴 폴더 경로는 빌드 시에 문제를 일으킬 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="8713f-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="8713f-154">HoloLens를 설정 하 고 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="8713f-155">HoloLens를 설정 하는 데 지원이 필요한 경우 [hololens 설정 문서를 방문](https://docs.microsoft.com/hololens/hololens-setup)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="8713f-156">새 HoloLens 앱 개발을 시작할 때 보정 및 센서 조정을 수행 하는 것이 좋습니다 (경우에 따라 각 사용자에 대해 해당 작업을 수행 하는 데 도움이 될 수 있음).</span><span class="sxs-lookup"><span data-stu-id="8713f-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="8713f-157">보정에 대 한 도움말을 보려면 [HoloLens 보정 문서에](calibration.md#hololens)대 한 다음 링크를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8713f-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="8713f-158">센서 조정에 대 한 도움말을 보려면 [HoloLens 센서 조정 문서에 대 한 링크를](sensor-tuning.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8713f-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="8713f-159">1 장-Custom Vision 포털</span><span class="sxs-lookup"><span data-stu-id="8713f-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="8713f-160">**Azure Custom Vision Service**을 사용 하려면 응용 프로그램에서 사용할 수 있도록 인스턴스를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="8713f-161">[ **Custom Vision Service** 기본 페이지로](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="8713f-162">**시작**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="8713f-163">Custom Vision 포털에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="8713f-164">아직 Azure 계정이 없는 경우 새로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="8713f-165">교실 또는 랩 상황에서이 자습서를 수행 하는 경우 강사 또는 proctors 중 하나에 문의 하 여 새 계정을 설정 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="8713f-166">처음으로 로그인 한 후에는 *서비스 사용 약관* 패널이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="8713f-167">확인란을 클릭 하 여 *약관에 동의*합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="8713f-168">그런 다음 **동의 함**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="8713f-169">조건에 동의한 경우 이제 *내 프로젝트* 섹션에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="8713f-170">**새 프로젝트**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="8713f-171">탭이 오른쪽에 표시 되 고 프로젝트의 일부 필드를 지정 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="8713f-172">프로젝트 이름을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="8713f-173">프로젝트에 대 한 설명을 삽입 합니다 (**선택 사항**).</span><span class="sxs-lookup"><span data-stu-id="8713f-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="8713f-174">리소스 그룹을 선택 하거나 새 **리소스 그룹** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="8713f-175">리소스 그룹은 Azure 자산의 컬렉션에 대 한 청구를 모니터링 하 고, 액세스를 제어 하 고, 프로 비전 하 고, 관리 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="8713f-176">단일 프로젝트와 연결 된 모든 Azure 서비스 (예: 이러한 과정)를 공용 리소스 그룹에 유지 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="8713f-177">[Azure 리소스 그룹에 대 한 자세한 내용을 보려면 관련 문서를 탐색](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) 하세요.</span><span class="sxs-lookup"><span data-stu-id="8713f-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="8713f-178">**프로젝트 형식을** **개체 검색 (미리 보기)** 으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="8713f-179">작업이 완료 되 면 **프로젝트 만들기**를 클릭 하면 Custom Vision Service 프로젝트 페이지로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="8713f-180">2 장-Custom Vision 프로젝트 학습</span><span class="sxs-lookup"><span data-stu-id="8713f-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="8713f-181">Custom Vision 포털에서 기본 목표는 이미지의 특정 개체를 인식할 수 있도록 프로젝트를 학습 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="8713f-182">응용 프로그램에서 인식 하는 각 개체에 대해 최소 15 개의 이미지가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="8713f-183">이 과정에서 제공 되는 이미지 ([일련의 cup](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip))를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="8713f-184">Custom Vision 프로젝트를 학습 하려면:</span><span class="sxs-lookup"><span data-stu-id="8713f-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="8713f-185">**태그 옆**에 있는 **단추를클릭+** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="8713f-186">에 이미지를 연결 하는 데 사용 되는 태그의 **이름을** 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="8713f-187">이 예제에서는 cup 이미지를 사용 하 여 인식 하므로이 **컵**의 태그 이름을 지정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="8713f-188">완료 되 면 **저장** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="8713f-189">**태그가** 추가 된 것을 확인할 수 있습니다 (표시 되기 위해 페이지를 다시 로드 해야 할 수 있음).</span><span class="sxs-lookup"><span data-stu-id="8713f-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="8713f-190">페이지의 가운데에 있는 **이미지 추가** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="8713f-191">**로컬 파일 찾아보기**를 클릭 하 고, 한 개체에 대해 업로드할 이미지를 찾은 다음 최소 15 (15)입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="8713f-192">한 번에 여러 이미지를 선택 하 여 업로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="8713f-193">프로젝트를 학습 하려는 모든 이미지를 선택 했으면 **파일 업로드** 를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="8713f-194">파일이 업로드 되기 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-194">The files will begin uploading.</span></span> <span data-ttu-id="8713f-195">업로드를 확인 한 후 **완료**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="8713f-196">이 시점에서 이미지는 업로드 되지만 태그가 지정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="8713f-197">이미지에 태그를 사용 하려면 마우스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="8713f-198">이미지를 마우스로 가리키면 선택 항목 강조 표시를 통해 개체 주위에 선택 영역을 자동으로 그리면 도움을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="8713f-199">정확 하지 않은 경우 직접 그릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="8713f-200">마우스 왼쪽 단추를 누르고 선택 영역을 끌어 개체를 포함 하 여이를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="8713f-201">이미지 내에서 개체를 선택 하 고 나 서 작은 프롬프트가 표시 되 면 *지역 태그를 추가*하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="8713f-202">위의 예제에서 이전에 만든 태그 (' 컵 ')를 선택 하거나 태그를 더 추가 하는 경우에 해당 태그를 입력 하 고 **+ (더하기)** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="8713f-203">다음 이미지에 태그를 표시 하려면 블레이드의 오른쪽에 있는 화살표를 클릭 하거나 블레이드의 오른쪽 위 모퉁이에 있는 **X** 를 클릭 하 여 태그 블레이드를 닫은 후 다음 이미지를 클릭 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="8713f-204">다음 이미지가 준비 되 면 동일한 절차를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="8713f-205">모든 이미지에 태그를 지정 하기 전까지 업로드 한 모든 이미지에 대해이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="8713f-206">아래 이미지와 같이 동일한 이미지에서 여러 개체를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="8713f-207">태그를 모두 지정 했으면 화면 왼쪽에 있는 **태그가 지정** 된 단추를 클릭 하 여 태그가 지정 된 이미지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="8713f-208">이제 서비스를 학습할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-208">You are now ready to train your Service.</span></span> <span data-ttu-id="8713f-209">**학습** 단추를 클릭 하면 첫 번째 학습 반복이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="8713f-210">빌드된 후에는 **기본** 및 **예측 URL**이라는 두 개의 단추를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="8713f-211">먼저 **기본 설정** 을 클릭 한 다음 **예측 URL**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="8713f-212">이에서 제공 하는 끝점은 기본값으로 표시 된 *반복* 에 대해 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="8713f-213">따라서 나중에 새 *반복* 을 만들고 기본값으로 업데이트할 경우에는 코드를 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="8713f-214">**예측 URL**을 클릭 하면 *메모장*을 열고, 코드에서 나중에 필요할 때 검색할 수 있도록 **url** ( **예측 엔드포인트**라고도 함) 및 **서비스 예측 키**를 복사 하 여 붙여넣습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="8713f-215">3 장-Unity 프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="8713f-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="8713f-216">다음은 혼합 현실를 사용 하 여 개발 하기 위한 일반적인 설정으로, 다른 프로젝트에 적합 한 템플릿입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="8713f-217">**Unity** 를 열고 **새로 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="8713f-218">이제 Unity 프로젝트 이름을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="8713f-219">**CustomVisionObjDetection**을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="8713f-220">프로젝트 형식이 **3d**로 설정 되었는지 확인 하 고 위치를 적절 한 **위치** 에 적절 하 게 설정 합니다 (루트 디렉터리와 더 잘 됨).</span><span class="sxs-lookup"><span data-stu-id="8713f-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="8713f-221">그런 다음 **프로젝트 만들기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="8713f-222">Unity를 연 상태에서 기본 **스크립트 편집기** 가 **Visual Studio**로 설정 되어 있는지 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="8713f-223">\**기본 설정* *편집* > \* 으로 이동한 다음 새 창에서 **외부 도구**로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="8713f-224">**외부 스크립트 편집기** 를 **Visual Studio**로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="8713f-225">**기본 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="8713f-226">그런 다음 **파일 > 빌드 설정** 으로 이동 하 고 **플랫폼** 을 *유니버설 Windows 플랫폼*로 전환한 다음, **플랫폼 전환** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="8713f-227">동일한 **빌드 설정** 창에서 다음이 설정 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="8713f-228">**대상 장치가** **HoloLens** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="8713f-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="8713f-229">**빌드 형식이** **D3D** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="8713f-230">**SDK** 가 **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="8713f-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="8713f-231">**Visual Studio 버전이** **최신 설치** 로 설정 됨</span><span class="sxs-lookup"><span data-stu-id="8713f-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="8713f-232">**빌드 및 실행** 이 **로컬 컴퓨터로** 설정 됨</span><span class="sxs-lookup"><span data-stu-id="8713f-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="8713f-233">**빌드 설정**의 나머지 설정은 지금은 기본값으로 남겨 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="8713f-234">동일한 **빌드 설정** 창에서 **플레이어 설정** 단추를 클릭 하면 **검사기** 가 있는 공간에서 관련 패널이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="8713f-235">이 패널에서 몇 가지 설정을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="8713f-236">**기타 설정** 탭에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="8713f-237">**Scripting Runtime 버전** 은 **실험적** (.net 4.6 이와 동일) 이어야 하며,이 경우 편집기를 다시 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="8713f-238">**Scripting 백엔드** 는 **.net**이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="8713f-239">**API 호환성 수준은** **.net 4.6**이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="8713f-240">**게시 설정** 탭의 **기능**아래에서 다음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="8713f-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="8713f-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="8713f-242">**웹캠**</span><span class="sxs-lookup"><span data-stu-id="8713f-242">**Webcam**</span></span>

        3. <span data-ttu-id="8713f-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="8713f-243">**SpatialPerception**</span></span>

            <span data-ttu-id="8713f-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="8713f-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="8713f-245">패널의 아래쪽에서 **XR 설정** ( **게시 설정**아래에 있음), **지원 되는 틱 가상 현실**, **Windows Mixed reality SDK** 가 추가 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="8713f-246">**빌드 설정**으로 돌아가서 *\# Unity C 프로젝트가* 더 이상 회색으로 표시 되지 않습니다 .이 옆의 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="8713f-247">**빌드 설정** 창을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="8713f-248">**편집기**에서**프로젝트 설정** > 편집 > **그래픽**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="8713f-249">**검사기 패널** 에서 *그래픽 설정이* 열립니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="8713f-250">**항상 셰이더 포함**이라는 배열이 표시 될 때까지 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="8713f-251">**크기** 변수를 1 씩 늘려서 슬롯을 추가 합니다 .이 예제에서는 8 이므로 9로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="8713f-252">새 슬롯은 아래와 같이 배열의 마지막 위치에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="8713f-253">슬롯에서 슬롯 옆의 작은 대상 원을 클릭 하 여 셰이더 목록을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="8713f-254">**레거시 셰이더/투명/확산** 셰이더를 찾아 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="8713f-255">4 장-CustomVisionObjDetection Unity 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="8713f-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="8713f-256">이 과정에서는 **310. unitypackage**라는 Unity 자산 패키지가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="8713f-257">잠깐만 전체 장면을 포함 하 여 Unity에서 지원 되는 모든 개체를 **unitypackage** 파일로 패키지 하 고 다른 프로젝트에서 내보내거나 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="8713f-258">서로 다른 **Unity 프로젝트**간에 자산을 이동 하는 가장 안전 하 고 가장 효율적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="8713f-259">[여기에서 다운로드 해야 하는 Azure-MR-310 패키지](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="8713f-260">앞의 Unity 대시보드를 사용 하 여 화면 위쪽의 메뉴에서 **자산** 을 클릭 하 고 **패키지 가져오기 > 사용자 지정 패키지**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="8713f-261">파일 선택기를 사용 하 여 **310. unitypackage** 패키지를 선택 하 고 **열기**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="8713f-262">이 자산의 구성 요소 목록이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="8713f-263">**가져오기** 단추를 클릭 하 여 가져오기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="8713f-264">가져오기가 완료 되 면 패키지의 폴더가 **자산** 폴더에 추가 된 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="8713f-265">이러한 종류의 폴더 구조는 Unity 프로젝트에 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="8713f-266">**재질** 폴더는 **응시 커서**에서 사용 하는 자료를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="8713f-267">**플러그 인** 폴더는 코드에서 서비스 웹 응답을 deserialize 하는 데 사용 하는 newtonsoft.json DLL을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="8713f-268">폴더 및 하위 폴더에 포함 된 두 가지 다른 버전은 Unity 편집기와 UWP 빌드 모두에서 라이브러리를 사용 하 고 작성할 수 있도록 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="8713f-269">**Prefabs** 폴더에는 장면에 포함 된 Prefabs이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="8713f-270">이러한 작업은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-270">Those are:</span></span>

        1.  <span data-ttu-id="8713f-271">응용 프로그램에서 사용 되는 **GazeCursor**입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="8713f-272">는 SpatialMapping prefab와 함께 작동 하 여 물리적 개체의 맨 위에 장면에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="8713f-273">**레이블**-필요할 때 장면에 개체 태그를 표시 하는 데 사용 되는 UI 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="8713f-274">**SpatialMapping**는 응용 프로그램에서 Microsoft HoloLens의 공간 추적을 사용 하 여 가상 맵 만들기를 사용할 수 있도록 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="8713f-275">이 과정의 미리 작성 된 장면을 현재 포함 하는 **장면** 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="8713f-276">**프로젝트 패널**에서 **장면** 폴더를 열고 **ObjDetectionScene**를 두 번 클릭 하 여이 과정에 사용할 장면을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="8713f-277">**코드는 포함 되지 않으며**,이 과정을 수행 하 여 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="8713f-278">5 장-CustomVisionAnalyser 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="8713f-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="8713f-279">이 시점에서 일부 코드를 작성할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="8713f-280">**CustomVisionAnalyser** 클래스로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="8713f-281">아래에 표시 된 코드에서 수행 된 **Custom Vision Service**호출은 **Custom Vision REST API**를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="8713f-282">이를 사용 하 여이 API를 구현 하 고 사용 하는 방법을 확인할 수 있습니다 (사용자가 직접 비슷한 항목을 구현 하는 방법을 이해 하는 데 유용).</span><span class="sxs-lookup"><span data-stu-id="8713f-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="8713f-283">Microsoft는 서비스를 호출 하는 데 사용할 수 있는 **CUSTOM VISION SDK** 를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="8713f-284">자세한 내용은 [CUSTOM VISION SDK 문서](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8713f-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="8713f-285">이 클래스는 다음을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-285">This class is responsible for:</span></span>

- <span data-ttu-id="8713f-286">캡처된 최신 이미지를 바이트 배열로 로드 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="8713f-287">분석을 위해 바이트 배열을 Azure **Custom Vision Service** 인스턴스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="8713f-288">JSON 문자열로 응답을 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="8713f-289">응답을 deserialize 하 고 결과 **예측** 을 **SceneOrganiser** 클래스에 전달 하 여 응답이 표시 되는 방법을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="8713f-290">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="8713f-290">To create this class:</span></span>

1.  <span data-ttu-id="8713f-291">**프로젝트 패널**에 있는 **자산 폴더**를 마우스 오른쪽 단추로 클릭 한 다음**폴더** **만들기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="8713f-292">폴더 **스크립트**를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="8713f-293">새로 만든 폴더를 두 번 클릭 하 여 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="8713f-294">폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음,**C\# 스크립트** **만들기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="8713f-295">스크립트 이름을 **CustomVisionAnalyser로 합니다.**</span><span class="sxs-lookup"><span data-stu-id="8713f-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="8713f-296">새 **CustomVisionAnalyser** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="8713f-297">파일의 위쪽에서 참조 되는 다음 네임 스페이스가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="8713f-298">**CustomVisionAnalyser** 클래스에서 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="8713f-299">**서비스 예측 키** 를 **predictionKey** 변수에 삽입 하 고 **예측 끝점** 을 **predictionEndpoint** 변수에 삽입 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="8713f-300">위의 [2 장, 14 단계에서 메모장](#chapter-2---training-your-custom-vision-project)에 복사 했습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="8713f-301">이제 initialize **()** 에 대 한 코드를 추가 하 여 인스턴스 변수를 초기화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="8713f-302">코 루틴 (아래의 static **GetImageAsByteArray ()** 메서드 사용)를 추가 합니다. 그러면 **ImageCapture** 클래스에서 캡처한 이미지의 분석 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8713f-303">**AnalyseImageCapture** 코 루틴에는 아직 만들지 않은 **SceneOrganiser** 클래스에 대 한 호출이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="8713f-304">따라서 **해당 줄을 현재 주석으로 처리**합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-304">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. <span data-ttu-id="8713f-305">**Start ()** 및 **Update ()** 메서드를 사용 하지 않으므로 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="8713f-306">**Unity**로 반환 하기 전에 **Visual Studio**에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8713f-307">앞에서 설명한 것 처럼 오류가 발생 한 것 처럼 보일 수 있는 코드에 대해 걱정 하지 마세요. 추가 클래스를 곧 제공 하면이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="8713f-308">6 장-CustomVisionObjects 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="8713f-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="8713f-309">지금 만들 클래스는 **CustomVisionObjects** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="8713f-310">이 스크립트에는 다른 클래스에서 Custom Vision Service에 대 한 호출을 serialize 및 deserialize 하는 데 사용 하는 여러 개체가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="8713f-311">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="8713f-311">To create this class:</span></span>

1.  <span data-ttu-id="8713f-312">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **\# C 스크립트** **만들기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="8713f-313">CustomVisionObjects 스크립트를 호출 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="8713f-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="8713f-314">새 **CustomVisionObjects** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="8713f-315">파일의 위쪽에서 참조 되는 다음 네임 스페이스가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="8713f-316">**CustomVisionObjects** 클래스 내에서 **Start ()** 및 **Update ()** 메서드를 삭제 합니다 .이 클래스는 이제 비어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="8713f-317">다음 명령을 신중 하 게 수행 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="8713f-318">**CustomVisionObjects** 클래스 내에 새 클래스 선언을 배치 하면 **AnalysisRootObject** 및 **BoundingBox** 가 없다는 것을 나타내는 [10 장](#chapter-10---create-the-imagecapture-class)에서 컴파일 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="8713f-319">**CustomVisionObjects** 클래스 *외부* 에 다음 클래스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="8713f-320">이러한 개체는 **newtonsoft.json** 라이브러리에서 응답 데이터를 serialize 및 deserialize 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  <span data-ttu-id="8713f-321">**Unity**로 반환 하기 전에 **Visual Studio**에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="8713f-322">7 장-SpatialMapping 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="8713f-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="8713f-323">이 클래스는 가상 개체와 실제 개체 간의 충돌을 검색할 수 있도록 장면에 **공간 매핑 Collider** 를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="8713f-324">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="8713f-324">To create this class:</span></span>

1.  <span data-ttu-id="8713f-325">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **\# C 스크립트** **만들기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="8713f-326">SpatialMapping 스크립트를 호출 **합니다.**</span><span class="sxs-lookup"><span data-stu-id="8713f-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="8713f-327">새 **SpatialMapping** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="8713f-328">**SpatialMapping** 클래스 위에 참조 된 다음 네임 스페이스가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="8713f-329">그런 다음 **SpatialMapping** 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  <span data-ttu-id="8713f-330">절전 모드 **()** 를 추가 하 고 **Start ()** 를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-330">Add the **Awake()** and **Start()**:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  <span data-ttu-id="8713f-331">**Update ()** 메서드를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="8713f-332">**Unity**로 반환 하기 전에 **Visual Studio**에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="8713f-333">8 장-GazeCursor 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="8713f-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="8713f-334">이 클래스는 이전 장에서 만든 **SpatialMappingCollider**을 사용 하 여 실제 공간에서 올바른 위치에 커서를 설정 하는 작업을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="8713f-335">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="8713f-335">To create this class:</span></span>

1.  <span data-ttu-id="8713f-336">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **\# C 스크립트** **만들기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="8713f-337">**GazeCursor** 스크립트를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="8713f-338">새 **GazeCursor** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="8713f-339">**GazeCursor** 클래스 위에 참조 된 다음 네임 스페이스가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="8713f-340">그런 다음 **GazeCursor** 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="8713f-341">**Start ()** 메서드를 다음 코드로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-341">Update the **Start()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  <span data-ttu-id="8713f-342">**Update ()** 메서드를 다음 코드로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-342">Update the **Update()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="8713f-343">**SceneOrganiser** 클래스를 찾을 수 없다는 오류에 대해 걱정 하지 마세요. 다음 챕터에서 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="8713f-344">**Unity**로 반환 하기 전에 **Visual Studio**에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="8713f-345">9 장-SceneOrganiser 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="8713f-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="8713f-346">이 클래스는 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-346">This class will:</span></span>

-   <span data-ttu-id="8713f-347">적절 한 구성 요소를 연결 하 여 *기본 카메라* 를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="8713f-348">개체가 검색 되 면 실제 환경에서 해당 위치를 계산 하 고 적절 한 **태그 이름을**사용 하 여 **태그 레이블을** 근처에 배치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="8713f-349">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="8713f-349">To create this class:</span></span>

1.  <span data-ttu-id="8713f-350">**Scripts** 폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음 **\# C 스크립트** **만들기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="8713f-351">스크립트 이름을 **SceneOrganiser**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="8713f-352">새 **SceneOrganiser** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="8713f-353">**SceneOrganiser** 클래스 위에 참조 된 다음 네임 스페이스가 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="8713f-354">그런 다음 **SceneOrganiser** 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  <span data-ttu-id="8713f-355">**Start ()** 및 **Update ()** 메서드를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="8713f-356">변수 아래에서 해제 **()** 메서드를 추가 합니다 .이 메서드는 클래스를 초기화 하 고 장면을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  <span data-ttu-id="8713f-357">**PlaceAnalysisLabel ()** 메서드를 추가 합니다 .이 메서드는 장면 (이 시점에서 사용자에 게 보이지 않음)의 레이블을 *인스턴스화합니다* .</span><span class="sxs-lookup"><span data-stu-id="8713f-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="8713f-358">또한 이미지가 배치 되는 4 개 (보이지 않음)를 배치 하 고 실제 세계와 겹칩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="8713f-359">분석 후 서비스에서 검색 된 상자 좌표가이 쿼드로 다시 추적 되어 실제 세계에 있는 개체의 대략적인 위치를 결정 하기 때문에이는 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  <span data-ttu-id="8713f-360">**FinaliseLabel ()** 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="8713f-361">이 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-361">It is responsible for:</span></span>

    *   <span data-ttu-id="8713f-362">신뢰 수준이 가장 높은 예측의 *태그로* *레이블* 텍스트를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="8713f-363">이전에 배치 하 고 장면에 레이블을 배치 하 여 쿼드 개체의 *경계 상자* 계산 호출</span><span class="sxs-lookup"><span data-stu-id="8713f-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="8713f-364">실제 세계의 개체와 충돌 하는 *경계 상자*를 향해 Raycast를 사용 하 여 레이블 깊이를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="8713f-365">사용자가 다른 이미지를 캡처할 수 있도록 캡처 프로세스를 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-365">Resetting the capture process to allow the user to capture another image.</span></span>

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  <span data-ttu-id="8713f-366">**CalculateBoundingBoxPosition ()** 메서드를 추가 합니다 .이 메서드는 서비스에서 검색 된 *경계 상자* 좌표를 변환 하 고 쿼드에 비례하여 다시 만드는 데 필요한 계산을 여러 개 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. <span data-ttu-id="8713f-367">**Unity**로 반환 하기 전에 **Visual Studio**에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8713f-368">계속 하기 전에 **CustomVisionAnalyser** 클래스를 열고 **AnalyseLastImageCaptured ()** 메서드 내에서 다음 줄의 *주석 처리를 제거* 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> <span data-ttu-id="8713f-369">**ImageCapture** 클래스 ' 찾을 수 없음 ' 메시지에 대해 걱정 하지 마세요. 다음 장에서 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="8713f-370">10 장-ImageCapture 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="8713f-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="8713f-371">만들려는 다음 클래스는 **ImageCapture** 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="8713f-372">이 클래스는 다음을 담당 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-372">This class is responsible for:</span></span>

*   <span data-ttu-id="8713f-373">HoloLens 카메라를 사용 하 여 이미지를 캡처하고 *앱* 폴더에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="8713f-374">사용자 로부터 *탭* 제스처를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="8713f-375">이 클래스를 만들려면:</span><span class="sxs-lookup"><span data-stu-id="8713f-375">To create this class:</span></span>

1.  <span data-ttu-id="8713f-376">이전에 만든 **스크립트** 폴더로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="8713f-377">폴더 내부를 마우스 오른쪽 단추로 클릭 한 다음,**C\# 스크립트** **만들기** > 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="8713f-378">스크립트 이름을 **ImageCapture**로 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="8713f-379">새 **ImageCapture** 스크립트를 두 번 클릭 하 여 **Visual Studio** 에서 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="8713f-380">파일의 맨 위에 있는 네임 스페이스를 다음으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="8713f-381">그런 다음 **ImageCapture** 클래스 내에서 **Start ()** 메서드 위의 다음 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="8713f-382">이제 **활성 ()** 및 **Start ()** 메서드에 대 한 코드를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="8713f-383">탭 제스처가 발생할 때 호출 되는 처리기를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="8713f-384">커서가 **녹색이**면 카메라에서 이미지를 사용할 수 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="8713f-385">커서가 **빨간색**이면 카메라가 사용 중임을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="8713f-386">응용 프로그램이 이미지 캡처 프로세스를 시작 하 고 이미지를 저장 하는 데 사용 하는 메서드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  <span data-ttu-id="8713f-387">사진이 캡처되고 분석 준비가 될 때 호출 되는 처리기를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="8713f-388">그런 다음 결과가 분석을 위해 **CustomVisionAnalyser** 에 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="8713f-389">**Unity**로 반환 하기 전에 **Visual Studio**에서 변경 내용을 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="8713f-390">11 장-장면에서 스크립트 설정</span><span class="sxs-lookup"><span data-stu-id="8713f-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="8713f-391">이 프로젝트에 필요한 모든 코드를 작성 했으므로 이제는 장면에서 스크립트를 설정 하 고 prefabs에서 제대로 동작 하도록 하는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="8713f-392">**Unity 편집기**내의 **계층 패널**에서 **주 카메라**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="8713f-393">**검사기 패널**에서 **주 카메라** 를 선택 하 고 **구성 요소 추가**를 클릭 한 다음 **SceneOrganiser** 스크립트를 검색 하 고 두 번 클릭 하 여 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="8713f-394">에 표시 된 것 처럼 **프로젝트 패널**에서 **Prefabs 폴더**를 열고 Prefab **label** 을 *기본 카메라*에 방금 추가한 **SceneOrganiser** 스크립트의 *레이블* 빈 참조 대상 입력 영역으로 끌어 옵니다. 아래 이미지:</span><span class="sxs-lookup"><span data-stu-id="8713f-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="8713f-395">**계층 패널**에서 **기본 카메라**의 **GazeCursor** 자식을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="8713f-396">**검사기 패널**에서 **GazeCursor** 가 선택 된 상태에서 **구성 요소 추가**를 클릭 한 다음 **GazeCursor** 스크립트를 검색 하 고 두 번 클릭 하 여 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="8713f-397">**계층 패널**에서 **기본 카메라**의 **SpatialMapping** 자식을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="8713f-398">**검사기 패널**에서 **SpatialMapping** 가 선택 된 상태에서 **구성 요소 추가**를 클릭 한 다음 **SpatialMapping** 스크립트를 검색 하 고 두 번 클릭 하 여 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="8713f-399">설정 하지 않은 나머지 스크립트는 런타임 중에 **SceneOrganiser** 스크립트의 코드에 의해 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="8713f-400">12 장-빌드하기 전</span><span class="sxs-lookup"><span data-stu-id="8713f-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="8713f-401">응용 프로그램에 대 한 철저 한 테스트를 수행 하려면 Microsoft HoloLens로 테스트용으로 로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="8713f-402">이렇게 하려면 먼저 다음을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="8713f-403">[3 장](#chapter-3---set-up-the-unity-project) 에서 설명한 모든 설정이 올바르게 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="8713f-404">**SceneOrganiser** 스크립트는 **주 카메라** 개체에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="8713f-405">**GazeCursor** 스크립트는 **GazeCursor** 개체에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="8713f-406">**SpatialMapping** 스크립트는 **SpatialMapping** 개체에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="8713f-407">[5 장](#chapter-5---create-the-customvisionanalyser-class), 6 단계:</span><span class="sxs-lookup"><span data-stu-id="8713f-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="8713f-408">**PredictionKey** 변수에 **서비스 예측 키** 를 삽입 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="8713f-409">**예측 끝점** 을 **predictionEndpoint** 클래스에 삽입 했습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="8713f-410">13 장-UWP 솔루션 빌드 및 응용 프로그램 테스트용으로 로드</span><span class="sxs-lookup"><span data-stu-id="8713f-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="8713f-411">이제 Microsoft HoloLens에 배포할 수 있는 UWP 솔루션으로 응용 프로그램을 빌드할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="8713f-412">빌드 프로세스를 시작 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-412">To begin the build process:</span></span>

1.  <span data-ttu-id="8713f-413">**파일 > 빌드 설정**으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="8713f-414">Tick **Unity C\# 프로젝트**.</span><span class="sxs-lookup"><span data-stu-id="8713f-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="8713f-415">열려 있는 **장면 추가**를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="8713f-416">이렇게 하면 현재 열려 있는 장면이 빌드에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="8713f-417">**빌드**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-417">Click **Build**.</span></span> <span data-ttu-id="8713f-418">Unity는 응용 프로그램을 빌드할 폴더를 만들고 선택 해야 하는 *파일 탐색기* 창을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="8713f-419">이제 해당 폴더를 만들고 이름을 **App**으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="8713f-420">그런 다음 **앱** 폴더를 선택 하 고 **폴더 선택**을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="8713f-421">Unity는 **응용** 프로그램 폴더에 대 한 프로젝트 빌드를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="8713f-422">Unity가 빌드를 완료 하면 (시간이 걸릴 수 있음) 빌드 위치에서 **파일 탐색기** 창이 열립니다. (작업 표시줄은 항상 창 위에 표시 되는 것은 아니지만 새 창 추가를 알려 줍니다.)</span><span class="sxs-lookup"><span data-stu-id="8713f-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="8713f-423">Microsoft HoloLens에 배포 하려면 해당 장치의 IP 주소가 필요 하며 (원격 배포의 경우) **개발자 모드가** 설정 되어 있는지도 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="8713f-424">가상 하드 디스크 파일에 대한 중요 정보를 제공하려면</span><span class="sxs-lookup"><span data-stu-id="8713f-424">To do this:</span></span>

    1.  <span data-ttu-id="8713f-425">HoloLens를 입고 하는 동안 **설정을**엽니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="8713f-426">**네트워크 & 인터넷** > **wi-fi** > **고급 옵션** 으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="8713f-427">**IPv4** 주소를 적어둡니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="8713f-428">그런 다음 **설정**으로 다시 이동한 다음**개발자** 를 위한 **& 보안** > 을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="8713f-429">에서 **개발자 모드** *를*설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="8713f-430">새 Unity 빌드 ( **앱** 폴더)로 이동 하 여 **Visual Studio**에서 솔루션 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="8713f-431">솔루션 구성에서 **디버그**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="8713f-432">솔루션 플랫폼에서 **x86, 원격 컴퓨터**를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="8713f-433">원격 장치의 **IP 주소** (이 경우에는 기록한 Microsoft HoloLens)를 삽입 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="8713f-434">**빌드** 메뉴로 이동 하 여 **솔루션 배포** 를 클릭 하 여 응용 프로그램을 HoloLens로 테스트용으로 로드.</span><span class="sxs-lookup"><span data-stu-id="8713f-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="8713f-435">이제 앱이 Microsoft HoloLens의 설치 된 앱 목록에 표시 되어 시작 될 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="8713f-436">응용 프로그램을 사용 하려면:</span><span class="sxs-lookup"><span data-stu-id="8713f-436">To use the application:</span></span>

* <span data-ttu-id="8713f-437">**Azure Custom Vision Service 및 개체 검색**을 사용 하 여 학습 하 고 **탭 제스처**를 사용 하 여 개체를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="8713f-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="8713f-438">개체가 성공적으로 검색 되 면 세계 공백 *레이블 텍스트가* 태그 이름과 함께 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8713f-439">사진을 캡처하여 서비스로 보낼 때마다 서비스 페이지로 돌아가서 새로 캡처한 이미지를 사용 하 여 서비스를 다시 학습 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="8713f-440">처음에는 *경계 상자* 를 수정 하 여 보다 정확 하 고 서비스를 다시 학습 하는 것도 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="8713f-441">Microsoft HoloLens 센서 및/또는 Unity의 SpatialTrackingComponent가 실제 개체를 기준으로 적절 한 colliders를 배치 하지 못할 때 배치 된 레이블 텍스트가 개체 근처에 나타나지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="8713f-442">해당 하는 경우 다른 화면에서 응용 프로그램을 사용 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8713f-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="8713f-443">Custom Vision, 개체 검색 응용 프로그램</span><span class="sxs-lookup"><span data-stu-id="8713f-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="8713f-444">축 하 합니다. Azure Custom Vision, 개체 검색 API를 활용 하는 혼합 현실 앱을 빌드하여 이미지에서 개체를 인식 한 다음 3D 공간에서 해당 개체에 대 한 대략적인 위치를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="8713f-445">보너스 연습</span><span class="sxs-lookup"><span data-stu-id="8713f-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="8713f-446">연습 1</span><span class="sxs-lookup"><span data-stu-id="8713f-446">Exercise 1</span></span>

<span data-ttu-id="8713f-447">텍스트 레이블에를 추가 하 여 반투명 큐브를 사용 하 여 3D *경계 상자*에 실제 개체를 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="8713f-448">연습 2</span><span class="sxs-lookup"><span data-stu-id="8713f-448">Exercise 2</span></span>

<span data-ttu-id="8713f-449">Custom Vision Service를 학습 하 여 더 많은 개체를 인식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="8713f-450">연습 3</span><span class="sxs-lookup"><span data-stu-id="8713f-450">Exercise 3</span></span>

<span data-ttu-id="8713f-451">개체가 인식 될 때 소리를 재생 합니다.</span><span class="sxs-lookup"><span data-stu-id="8713f-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="8713f-452">연습 4</span><span class="sxs-lookup"><span data-stu-id="8713f-452">Exercise 4</span></span>

<span data-ttu-id="8713f-453">API를 사용 하 여 응용 프로그램이 분석 하는 것과 동일한 이미지를 사용 하 여 서비스를 다시 학습 하므로 서비스를 보다 정확 하 게 만들 수 있습니다 (예측 및 학습을 동시에 수행).</span><span class="sxs-lookup"><span data-stu-id="8713f-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
